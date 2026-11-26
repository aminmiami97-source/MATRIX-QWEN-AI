# MATRIX QWEN AI

A browser-based AI chat interface powered by **Qwen2.5-0.5B-Instruct** and [Transformers.js](https://huggingface.co/docs/transformers.js).

## Features

- Runs Qwen directly in the browser — no inference API key or backend required.
- Uses the ONNX model from [onnx-community/Qwen2.5-0.5B-Instruct](https://huggingface.co/onnx-community/Qwen2.5-0.5B-Instruct).
- Attempts WebGPU first and falls back to WebAssembly (WASM) if WebGPU initialization fails.
- Quantized model loading with q4 weights.
- Browser-cached model files and locally stored chat history.
- Responsive interface for desktop and mobile.

## Run locally

Serve this repository with a local static web server because the app uses JavaScript modules. For example, run:

    python -m http.server 8000

Then open http://localhost:8000.

## GitHub Pages deployment

1. Open Settings → Pages in this repository.
2. Under Build and deployment, select GitHub Actions as the source.
3. The workflow in .github/workflows/deploy.yml deploys the static site when changes are pushed to main.
4. After the first successful workflow run, the Pages URL will appear in the repository's Pages settings.

## First launch

The model weights are not bundled in this repository. On the first launch, the browser downloads model files from Hugging Face. This can take time and use substantial memory and bandwidth. Keep the tab open while it loads. Later visits may reuse the browser cache.

WebGPU availability depends on the browser, operating system, and GPU. The app attempts a WASM fallback when WebGPU fails, but performance may be slower on devices without suitable acceleration.

## Privacy

Chat messages are sent to the model running in your browser and chat history is stored in that browser's localStorage. The model files are downloaded from Hugging Face. This project does not send prompts to a MATRIX-hosted inference server.

## Model and library

- Model: [onnx-community/Qwen2.5-0.5B-Instruct](https://huggingface.co/onnx-community/Qwen2.5-0.5B-Instruct)
- Runtime: [Transformers.js](https://github.com/huggingface/transformers.js)
