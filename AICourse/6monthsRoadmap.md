6-Month AI Learning Roadmap (Basics → Advanced, Python-Ready)

Assumes: you already know Python. Each month = ~4 weeks, ~6-8 hrs/week. Adjust pace as needed.


Month 1: Foundations — How AI Actually Works

Week 1: Basics of AI


What AI, ML, Deep Learning, and Generative AI actually mean (and how they relate)
Types of AI: narrow vs general, supervised/unsupervised/reinforcement learning
Key vocabulary: model, weights, parameters, training vs inference, tokens
Resource: Google's "AI for Everyone" (Andrew Ng, Coursera) or fast.ai "Practical Deep Learning"


Week 2: How Neural Networks Work (Conceptually)


Neurons, layers, activation functions — no heavy math required
What "training" a model means: loss functions, gradient descent, backpropagation (conceptual, not derivations)
Resource: 3Blue1Brown's Neural Networks video series (YouTube) — best visual explanation available


Week 3: How LLMs Work in the Background


Tokenization, embeddings, the Transformer architecture (attention mechanism, at a conceptual level)
Pretraining vs fine-tuning vs RLHF
Context windows, temperature, top-p, why models "hallucinate"
Resource: "The Illustrated Transformer" (Jay Alammar's blog), Anthropic's "Interpretability" blog posts


Week 4: The AI Ecosystem Today


Major model providers: Anthropic (Claude), OpenAI, Google (Gemini), open-source (Llama, Mistral, Qwen)
API vs chat interface vs local models
Project: Write a 1-page summary comparing 3 models' strengths/use cases (this cements the mental model)



Month 2: Prompt Engineering

Week 1: Core Prompting Principles


Being clear, specific, and giving context
Role prompting (system prompts), few-shot vs zero-shot examples
Resource: Anthropic's Prompt Engineering docs


Week 2: Advanced Prompting Techniques


Chain-of-thought prompting, step-by-step reasoning requests
XML tags / structured output requests, output formatting control
Prompt chaining (breaking a task into sequential prompts)


Week 3: Prompting for Different Tasks


Prompting for code generation, summarization, classification, extraction
Guardrails: reducing hallucination, asking the model to cite sources or admit uncertainty
Project: Build a "prompt library" — 10 reusable, well-tested prompt templates for common tasks


Week 4: Evaluating & Iterating on Prompts


How to A/B test prompts, measure quality, and version them
Intro to prompt evaluation tools (Promptfoo, LangSmith evals)
Project: Take one weak prompt and iterate it through 5 versions, documenting improvements



Month 3: Setting Up AI for Real Use (No Building From Scratch)

Week 1: Using AI APIs


Getting API keys, making your first API call (Anthropic API, OpenAI API)
Understanding pricing, rate limits, context length, streaming responses
Resource: Anthropic API docs


Week 2: Environment & Tooling Setup


Setting up a Python project with .env files, virtual environments, SDKs (anthropic, openai packages)
Using Jupyter notebooks vs scripts for experimentation
Local model setup basics (Ollama, LM Studio) for running open models locally — no training required


Week 3: Generative AI Beyond Text


Image generation basics (concepts behind diffusion models — not building one)
Setting up tools like Stable Diffusion (via API/local), voice/audio AI tools (ElevenLabs, Whisper)
Understanding multimodal models (text+image input)


Week 4: Multi-Purpose AI Setup


Designing one setup that serves multiple use cases: chatbot, summarizer, code assistant, content generator
Using system prompts + config files to switch "modes" without rebuilding
Project: Build a single Python script/notebook that can do 3 different tasks (summarize, translate, generate ideas) using the same API setup with different configs



Month 4: Retrieval, Memory & Grounding AI

(This bridges "using AI" to "building agents" — most real agents need this)

Week 1: Retrieval-Augmented Generation (RAG) Concepts


Why RAG exists: giving models access to your own data
Embeddings and vector databases (Pinecone, Chroma, Weaviate — conceptual + hands-on with Chroma, it's free/local)


Week 2: Building a Simple RAG Pipeline


Chunking documents, creating embeddings, storing and querying a vector DB
Connecting retrieval results back into a prompt
Resource: LlamaIndex or LangChain's RAG quickstart docs


Week 3: Memory for AI Applications


Short-term (conversation) memory vs long-term (persistent) memory
Simple memory patterns: summarization memory, key-value memory stores


Week 4: Project — Personal Knowledge Assistant


Project: Build a small RAG app that answers questions from a folder of your own documents (PDFs/notes)



Month 5: Building Your First Agents

Week 1: What Makes AI "Agentic"


Difference between a chatbot and an agent: reasoning loops, planning, tool use, autonomy
The ReAct pattern (Reason + Act), agent loops: observe → think → act → observe


Week 2: Tool Use / Function Calling


How models call external tools (function calling / tool use in Claude & OpenAI APIs)
Giving your agent tools: web search, calculator, file access, custom Python functions
Resource: Anthropic Tool Use docs


Week 3: Creating Your First Agent


Building a single-purpose agent from scratch using just the API + a loop (no framework) — this teaches you what frameworks do under the hood
Project: Build an agent that can search the web and answer questions with citations, using your own control loop


Week 4: Introduction to Agent Frameworks


Overview of the current landscape (as of 2026):

LangGraph — best for complex, stateful, production-grade workflows (steepest learning curve, most control)
CrewAI — best for role-based multi-agent teams, easiest to start with
Claude Agent SDK — best for Anthropic-native agents with sub-agent spawning
OpenAI Agents SDK — lightweight, good for OpenAI-native prototyping
Microsoft Agent Framework — merged successor to Semantic Kernel + AutoGen, best for enterprise/.NET stacks
LlamaIndex Workflows — best when your agent is RAG-first



Project: Rebuild your Month 5 Week 3 agent using CrewAI or LangGraph and compare the experience



Month 6: Agentic AI at Scale + Capstone

Week 1: Multi-Agent Systems


Patterns: supervisor/worker agents, role-based crews, hierarchical delegation
Handling agent-to-agent communication and shared state
Pick one framework from Month 5 and go deep (LangGraph or CrewAI recommended for beginners)


Week 2: Connecting Agents to Real Tools (MCP & Integrations)


Model Context Protocol (MCP) — the emerging standard for connecting AI to external tools/data sources
Linking agents to real services: Google Drive, Slack, GitHub, databases, custom APIs
Resource: MCP documentation


Week 3: Production Concerns


Error handling, retries, timeouts, cost control, observability/logging (LangSmith, Helicone)
Guardrails: approval steps before risky actions, rate limiting, avoiding infinite loops
Basic security: prompt injection awareness, sandboxing tool access


Week 4: Capstone Project


Build a complete multi-tool agentic system, for example:

A research agent that searches the web, reads documents (RAG), summarizes findings, and drafts a report
A personal ops agent connected to your calendar/email/task tool via MCP



Document it, deploy it (even locally via a simple script or Streamlit UI), and present it as a portfolio piece



Quick Reference: Tool Links to Bookmark

PurposeToolPrompting/API docshttps://docs.claude.comPrompt evaluationPromptfoo, LangSmithVector DB (free/local)ChromaRAG frameworkLlamaIndex, LangChainAgent framework (production)LangGraphAgent framework (beginner-friendly)CrewAILocal model runnerOllamaTool/data connectionsModel Context Protocol (MCP)ObservabilityLangSmith, Helicone


How to Use This Roadmap


Each month builds on the last — don't skip to agents before Month 3-4's setup fundamentals.
Every "Project" is non-negotiable — reading about prompting won't teach it, writing prompts will.
Frameworks change fast; the concepts (loops, tool use, memory, retrieval) are stable and worth mastering before you commit to one framework.