# Android Agent System — Master Reference

A production-grade multi-agent system for building Android apps with Kotlin, Jetpack Compose, MVVM, Clean Architecture, and Koin.

---

## Agent Pipeline

```
User Request
     │
     ▼
┌────────────────────┐
│  00 · Orchestrator │  ← Start here. Always.
└─────────┬──────────┘
          │  decomposes + dispatches
    ┌─────▼──────┐
    │ 01 · ARCH  │  Module design, interfaces, data flow, file tree skeleton
    └─────┬──────┘
          │  blueprint
    ┌─────▼──────┐
    │ 03 · SEC   │  Threat model, required security controls (pre-code)
    └─────┬──────┘
          │  clearance + controls
    ┌─────▼──────┐
    │ 02 · CODE  │  Full Kotlin implementation (all files, complete)
    └──┬──────┬──┘
       │      │
  ┌────▼──┐ ┌─▼──────┐
  │04·PERF│ │05·TEST │  Run in parallel against CODE output
  └────┬──┘ └─┬──────┘
       │      │
    ┌──▼──────▼──┐
    │ 06 · REVIEW│  Final gate — approve or block
    └────────────┘
```

---

## Agents

| File | Agent | When to Invoke |
|---|---|---|
| `00-android-orchestrator.md` | Orchestrator | Every request — entry point |
| `01-architecture-agent.md` | Architecture | New features, refactors, new modules |
| `02-code-generator-agent.md` | Code Generator | Any implementation task |
| `03-security-agent.md` | Security | Pre-code (threat model) + post-code (audit) |
| `04-performance-agent.md` | Performance | After code is written |
| `05-test-agent.md` | Test | After code is written |
| `06-code-review-agent.md` | Code Review | Final gate before merge |
| `07-android-coder-agent.md` | Coder (standalone) | Solo tasks without full pipeline |

---

## Canonical Tech Stack

| Concern | Technology | Notes |
|---|---|---|
| Language | Kotlin (latest stable) | No Java |
| UI | Jetpack Compose + Material 3 | No XML layouts |
| Architecture | MVVM + Clean Architecture | |
| DI | Koin 3.x | No Hilt |
| Async | Coroutines + Flow | No RxJava |
| Navigation | Compose Navigation (type-safe) | `@Serializable` route objects |
| Networking | Retrofit 2 + OkHttp 4 + kotlinx.serialization | No Gson |
| Local DB | Room (KSP) | |
| Images | Coil 3 | |
| Build | Kotlin DSL + `libs.versions.toml` | |
| Testing | JUnit5 + MockK + Turbine + Compose Test | |

---

## Module Structure (canonical)

```
:app
:feature:[name]
:domain
:data
:core:ui
:core:common
:core:network
:core:database
```

**Dependency rules:**
- `:feature` → `:domain`, `:core:ui`, `:core:common`
- `:data` → `:domain`, `:core:network`, `:core:database`, `:core:common`
- `:domain` → nothing (pure Kotlin)
- `:core:*` → `:core:common` only (no cross-core circular deps)
- `:feature:A` never imports `:feature:B`

---

## Data Flow (unidirectional)

```
Composable
  onIntent(FeatureIntent) ──► ViewModel
                                └── UseCase
                                      └── Repository (interface in :domain)
                                            └── [RepositoryImpl in :data]
                                                  ├── ApiService → Remote DTO → mapper → Domain
                                                  └── Room DAO → Entity → mapper → Domain

ViewModel.uiState: StateFlow<UiState>  ◄── collected in Composable
ViewModel.uiEvent: SharedFlow<UiEvent> ◄── LaunchedEffect in Composable
```

---

## Non-Negotiables (every agent enforces these)

1. No `!!` — safe calls or explicit handling only
2. No Android imports in `:domain`
3. No raw throws past repository boundary — always `Result<T>`
4. No mutable public state in ViewModels
5. No business logic in Composables
6. No feature-to-feature direct imports
7. No hardcoded secrets anywhere
8. No `GlobalScope`
9. No XML layouts
10. `collectAsStateWithLifecycle()` — not `collectAsState()` — in all Composables
