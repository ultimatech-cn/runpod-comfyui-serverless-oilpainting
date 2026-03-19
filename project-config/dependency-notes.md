# Baroque Merged Dependencies

## Custom Node Repos

Final merged repo count: `10`

| Repo | Covered nodes |
| --- | --- |
| `https://github.com/IuvenisSapiens/ComfyUI_Qwen3-VL-Instruct` | `Qwen3_VQA` |
| `https://github.com/ronn1xG/comfyui-upscale-by-model` | `UpscaleImageByUsingModel` |
| `https://github.com/chflame163/ComfyUI_LayerStyle` | `LayerUtility: PurgeVRAM V2`, `LayerUtility: ImageScaleByAspectRatio V2` |
| `https://github.com/cubiq/ComfyUI_essentials` | `GetImageSize+` |
| `https://github.com/kijai/ComfyUI-KJNodes` | `ColorMatch`, `JoinStrings` |
| `https://github.com/logtd/ComfyUI-Fluxtapoz` | `FluxDeGuidance`, `FluxForwardODESampler`, `FluxReverseODESampler`, `InFluxModelSamplingPred`, `OutFluxModelSamplingPred` |
| `https://github.com/princepainter/Comfyui-PainterFluxImageEdit` | `PainterFluxImageEdit` |
| `https://github.com/rgthree/rgthree-comfy` | `Any Switch (rgthree)` |
| `https://github.com/shadowcz007/comfyui-mixlab-nodes` | `SaveImageAndMetadata_` |
| `https://github.com/yolain/ComfyUI-Easy-Use` | `easy cleanGpuUsed`, `easy showAnything` |

## Official Nodes

These were confirmed as official/built-in for the current scope and are not part of the Docker repo list:

- `CFGNorm`
- `DisableNoise`
- `FlipSigmas`
- `FluxKontextImageScale`
- `ModelSamplingAuraFlow`
- `PrimitiveString`
- `TextEncodeQwenImageEditPlus`

## Merged Model Baseline

Unique model count: `18`

Important note:

- This list is only the merged workflow baseline.
- It is not the final truth for delivery links.
- Final URLs should prefer manually verified sources and your own Hugging Face mirror when needed.

| Workflow ref | Type | Notes |
| --- | --- | --- |
| `4xNomos8kSCHAT-L.pth` | `upscale_model` | pet |
| `ae.safetensors` | `vae` | pet, normalized from old workflow ref `ae.sft` |
| `art-texture-painting-v1.safetensors` | `lora` | pet, normalized to Hugging Face mirror filename |
| `FireRed-Image-Edit-1.1-transformer.safetensors` | `unet` | pet |
| `flux1-dev-fp8.safetensors` | `unet` | pet, normalized from old workflow ref `flux1-dev.sft` |
| `Qwen-Image-Edit-F2P.safetensors` | `lora` | portrait |
| `Qwen-Image-Lightning-4steps-V2.0.safetensors` | `lora` | pet |
| `Qwen-Rapid-AIO-NSFW-v18.safetensors` | `checkpoint` | portrait |
| `Qwen3-VL-4B-Instruct` | `other` | Hugging Face repo dependency, preload recommended |
| `clip_l.safetensors` | `clip` | pet |
| `flux-2-klein-9b-nvfp4.safetensors` | `unet` | portrait |
| `flux2-vae.safetensors` | `vae` | portrait |
| `impressionist-k9_2.safetensors` | `lora` | portrait, manually resolved from page title |
| `qwen_2.5_vl_7b_fp8_scaled.safetensors` | `clip` | shared |
| `qwen_3_8b.safetensors` | `clip` | portrait |
| `qwen_image_vae.safetensors` | `vae` | pet |
| `t5xxl_fp8_e4m3fn.safetensors` | `clip` | pet |
| `flux-oilpainting-v1-3.safetensors` | `lora` | pet, normalized to Hugging Face mirror filename |

## Recommended Next Step

1. Use [custom-nodes.txt](E:\Program Files\runpod-comfyui-serverless-oilpainting\project-config\custom-nodes.txt) as the repo install baseline.
2. Use [model-truth.md](E:\Program Files\runpod-comfyui-serverless-oilpainting\project-config\model-truth.md) as the model truth reference.
3. Keep workflow model names aligned with the filenames in [model-manifest.txt](E:\Program Files\runpod-comfyui-serverless-oilpainting\project-config\model-manifest.txt).
