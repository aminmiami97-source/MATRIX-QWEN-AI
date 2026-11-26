# MATRIX QWEN AI

A browser-based AI chat interface powered by **Qwen2.5-0.5B-Instruct** and [WebLLM](https://github.com/mlc-ai/web-llm).

## Features

- Runs Qwen directly in the browser — no inference API key or MATRIX backend required.
- Uses the instruction-tuned Qwen2.5 0.5B model in MLC 4-bit format.
- Approximate model repository size: **290 MB** for the model package.
- Uses WebGPU for local inference and hardware acceleration.
- Full-screen model loading screen with live progress, error details, retry, and a ready state.
- Browser caching so a later visit may reuse downloaded model files.
- Responsive interface for desktop and mobile.
- Chat history stored locally in the browser.

## First launch

On the first launch, press **Load Qwen**. The browser downloads the model files from Hugging Face and initializes WebGPU. This is approximately 290 MB before any additional browser/runtime overhead. Keep the tab open while it loads. Later visits may reuse the browser cache.

**WebGPU is required.** This smaller MLC build does not use the old ONNX/WASM fallback. If WebGPU is unavailable or disabled, the app will show an error instead of downloading a larger compatibility model. Use an up-to-date browser and a device with WebGPU support.

## Run locally

Serve this repository with a local static web server because the app uses JavaScript modules. For example:

    python -m http.server 8000

Then open http://localhost:8000.

## GitHub Pages deployment

1. Open Settings → Pages in this repository.
2. Under Build and deployment, select GitHub Actions as the source.
3. The workflow in .github/workflows/deploy.yml deploys the static site when changes are pushed to main.
4. After a successful workflow run, open the Pages URL shown in the repository's Pages settings.

## Privacy

Chat messages are sent to the model running in your browser and chat history is stored in that browser's localStorage. Model files are downloaded from Hugging Face. This project does not send prompts to a MATRIX-hosted inference server.

## Model and runtime

- Model: [mlc-ai/Qwen2.5-0.5B-Instruct-q4f16_1-MLC](https://huggingface.co/mlc-ai/Qwen2.5-0.5B-Instruct-q4f16_1-MLC)
- Runtime: [MLC WebLLM](https://github.com/mlc-ai/web-llm)
- Model license: Apache 2.0 (see the upstream model repository)
