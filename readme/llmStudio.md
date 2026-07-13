# LM Studio setup on your local machine

## 1. Install LM Studio
- Download and install LM Studio from the official website.
- Open the app after installation.

## 2. Download a model for coding
- In LM Studio, open the left menu and go to Model Search.
- Search for a coding-friendly model such as Qwen, DeepSeek, or Code Llama.
- If the model is not visible in LM Studio, search for it on Hugging Face.
- Choose a quantized version if needed and click Use this Model.
- Select LM Studio as the destination.
- Once the model is downloaded, open the chat window and select the model.

> Tip: Models labeled as MOE (Mixture of Experts) can be strong options for coding tasks.

## 3. Start the local API server
- LM Studio will expose a local API endpoint, usually at:
  - http://127.0.0.1:1234
- Keep this running while using it from VS Code.

## 4. Enable Agentic AI for code assistance in VS Code
- Install the Continue extension in VS Code.
- Open Continue and configure a new model provider.
- Choose an OpenAI-compatible provider.
- Set the base URL to:
  - http://127.0.0.1:1234/v1
- Set the model name to the same model you loaded in LM Studio.
- Use any placeholder value for the API key, such as:
  - lmstudio
- Enable chat/agent mode and autocomplete if available.
- Restart VS Code and test it by asking for code explanations, completions, or editing help.

## 5. Quick usage flow
- Load your model in LM Studio.
- Keep the local server running.
- Use Continue in VS Code to get AI help for coding tasks.
