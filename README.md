---
license: apache-2.0
library_name: onnxruntime
tags:
- image-to-image
- image-inpainting
- onnx
- lama
---

# Carousel Fit / 차곡 — LaMa FP32

Public, byte-identical mirror of Carve Photos' LaMa FP32 ONNX model for local
photo background extension. This repository contains only the model and notices;
no user photos, app source, or generated user images are published here.

Original LaMa: Copyright [2021] Samsung Research, Apache License 2.0.
Original project: https://github.com/advimman/lama
ONNX conversion: https://github.com/Carve-Photos/lama
Upstream model: https://huggingface.co/Carve/LaMa-ONNX
Upstream file: `lama_fp32.onnx`, file commit `a3ee2fca54baebec351b8fa7786154ffa7555aa6`.
The upstream model card declares Apache-2.0; LICENSE-LAMA.txt and LAMA-NOTICE.txt
retain the license and attribution. No endorsement is implied.

## Integrity

- File: `lama-fp32-1faef5301d78.onnx`
- Size: 208,044,816 bytes
- SHA-256: `1faef5301d78db7dda502fe59966957ec4b79dd64e16f03ed96913c7a4eb68d6`
- Weights/graph unmodified; only the local filename is content-addressed.

GitHub release mirror: https://github.com/neureps/carousel-fit-models/releases/tag/lama-v1
Hugging Face mirror: https://huggingface.co/neureps/carousel-fit-models

## Runtime contract and limitations

ONNX Runtime 1.24.2 CPU. Input `image`: float32 RGB `[1,3,512,512]` in 0–1;
`mask`: float32 `[1,1,512,512]`, 1 generates and 0 preserves. Output RGB values
are in 0–255. The app symmetrically pads a ratio-preserving working canvas,
crops the result back, and restores original photo pixels. Post-processing is
separate from the model and does not modify these weights.

Model download requires explicit consent, with an additional non-Wi-Fi data
confirmation. After downloading and validating SHA-256, processing stays offline.
The model is not bundled with the app. High memory usage can cause failure or OS
termination on some phones; availability is not a guarantee of device performance.
Generated backgrounds can contain artifacts and should be reviewed before saving.
