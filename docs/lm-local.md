# LM Local

LM Local is a native iPhone/iPad app for running local language and vision models with MLX. I am using it to explore the parts of an AI app that change when the model, files and chat history live on the device.

## What Is Built

- SwiftUI app with a chat surface, model menu, settings, personalization panel and conversation history.
- MLX-backed model loading through `MLXLMCommon`, `MLXLLM` and `MLXVLM`.
- Local model catalog stored in XML and parsed into app models.
- Download/cancel/delete flows for model files, with storage summary and per-model status.
- Compatibility filtering by iOS version, RAM and recommended device class.
- Text and image attachments, camera import, image cache and a fallback prompt for image-only messages.

The current catalog has 10 models: Qwen 3.5, Gemma, Gemma Vision, Qwen Vision and SmolVLM entries. Three of them support vision. The app shows incompatible models instead of hiding them, because that makes hardware limits easier to understand.

## Model Browser

The model browser is the core of the project. Each model carries the details that matter on mobile: quantization, context size, file size, minimum RAM, minimum OS, Hugging Face id, revision, backend type, default generation settings and notes. A 0.8B model for an older iPhone and a 9B model for an iPad Pro should not be presented as if they were the same choice.

## Status

Private alpha. The recent work has been around the model catalog and compatibility simulation. The next practical questions are performance, memory pressure, download reliability and whether the chat UX stays pleasant once real local inference latency is involved.
