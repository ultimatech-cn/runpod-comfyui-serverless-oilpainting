# Baroque Model Truth

This file is the source of truth for the Baroque project model list.

Use it when rebuilding or auditing [model-manifest.txt](E:\Program Files\runpod-comfyui-serverless-oilpainting\project-config\model-manifest.txt).

Rules:

- `workflow_ref` is the reference used by the workflow after normalization.
- `resolved_name` is the human-verified model identity.
- `final_url` should prefer your own Hugging Face mirror when available.
- Normalize dirty or legacy workflow names to the hosted filename before freezing the repo.

## Models

| workflow_ref | resolved_name | type | target_path_hint | final_url | status | notes |
| --- | --- | --- | --- | --- | --- | --- |
| `Qwen-Rapid-AIO-NSFW-v18.safetensors` | `Qwen-Rapid-AIO-NSFW-v18.safetensors` | `checkpoint` | `checkpoints/Qwen` | `https://huggingface.co/Phr00t/Qwen-Image-Edit-Rapid-AIO/resolve/main/v18/Qwen-Rapid-AIO-NSFW-v18.safetensors` | verified | portrait |
| `qwen_2.5_vl_7b_fp8_scaled.safetensors` | `qwen_2.5_vl_7b_fp8_scaled.safetensors` | `clip` | `clip` | `https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/resolve/main/split_files/text_encoders/qwen_2.5_vl_7b_fp8_scaled.safetensors` | verified | shared |
| `qwen_3_8b.safetensors` | `qwen_3_8b.safetensors` | `clip` | `clip` | `https://huggingface.co/Comfy-Org/vae-text-encorder-for-flux-klein-9b/resolve/main/split_files/text_encoders/qwen_3_8b.safetensors` | verified | portrait, user-selected pairing with original 9B |
| `clip_l.safetensors` | `clip_l.safetensors` | `clip` | `clip` | `https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors` | verified | pet |
| `t5xxl_fp8_e4m3fn.safetensors` | `t5xxl_fp8_e4m3fn.safetensors` | `clip` | `clip` | `https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp8_e4m3fn.safetensors` | verified | pet |
| `Qwen-Image-Edit-F2P.safetensors` | `edit_0928_lora_step40000.safetensors` | `lora` | `loras/Qwen` | `https://huggingface.co/DiffSynth-Studio/Qwen-Image-Edit-F2P/resolve/main/edit_0928_lora_step40000.safetensors` | verified | workflow ref and source filename differ |
| `Qwen-Image-Lightning-4steps-V2.0.safetensors` | `Qwen-Image-Lightning-4steps-V2.0.safetensors` | `lora` | `loras/Qwen` | `https://huggingface.co/lightx2v/Qwen-Image-Lightning/resolve/main/Qwen-Image-Lightning-4steps-V2.0.safetensors` | verified | pet |
| `art-texture-painting-v1.safetensors` | `art-texture-painting-v1.safetensors` | `lora` | `loras/Flux` | `https://huggingface.co/datasets/Robin9527/LoRA/resolve/main/Flux/art-texture-painting-v1.safetensors` | mirrored | pet, normalized to mirror filename |
| `flux-oilpainting-v1-3.safetensors` | `flux-oilpainting-v1-3.safetensors` | `lora` | `loras/Flux` | `https://huggingface.co/datasets/Robin9527/LoRA/resolve/main/Flux/flux-oilpainting-v1-3.safetensors` | mirrored | pet, normalized to mirror filename |
| `impressionist-k9_2.safetensors` | `impressionist-k9_2.safetensors` | `lora` | `loras/Flux2-Klein` | `https://huggingface.co/datasets/Robin9527/LoRA/resolve/main/Flux2-Klein/impressionist-k9_2.safetensors` | mirrored | portrait, original source was Civitai |
| `flux-2-klein-9b.safetensors` | `flux-2-klein-9b.safetensors` | `unet` | `unet` | `https://huggingface.co/black-forest-labs/FLUX.2-klein-9B/resolve/main/flux-2-klein-9b.safetensors` | verified | portrait, switched to original release |
| `FireRed-Image-Edit-1.1-transformer.safetensors` | `FireRed-Image-Edit-1.1-transformer.safetensors` | `unet` | `unet` | `https://huggingface.co/FireRedTeam/FireRed-Image-Edit-1.1-ComfyUI/resolve/main/FireRed-Image-Edit-1.1-transformer.safetensors` | verified | pet |
| `flux1-dev-fp8.safetensors` | `flux1-dev-fp8.safetensors` | `unet` | `unet` | `https://huggingface.co/Kijai/flux-fp8/resolve/main/flux1-dev-fp8.safetensors` | verified | pet, normalized from old workflow ref `flux1-dev.sft` |
| `flux2-vae.safetensors` | `flux2-vae.safetensors` | `vae` | `vae` | `https://huggingface.co/Comfy-Org/flux2-dev/resolve/main/split_files/vae/flux2-vae.safetensors` | verified | portrait |
| `ae.safetensors` | `ae.safetensors` | `vae` | `vae` | `https://huggingface.co/black-forest-labs/FLUX.1-schnell/resolve/main/ae.safetensors` | verified | pet, normalized from old workflow ref `ae.sft` |
| `qwen_image_vae.safetensors` | `qwen_image_vae.safetensors` | `vae` | `vae` | `https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/resolve/main/split_files/vae/qwen_image_vae.safetensors` | verified | pet |
| `4xNomos8kSCHAT-L.pth` | `4xNomos8kSCHAT-L.pth` | `upscale_model` | `upscale_models` | `https://huggingface.co/FelipeMurguia/4xNomos8kSCHAT-L/resolve/b7d4549997b0d4856412c8200b31878122e82776/4xNomos8kSCHAT-L.pth` | verified | pet |
| `Qwen3-VL-4B-Instruct` | `Qwen/Qwen3-VL-4B-Instruct` | `huggingface_repo` | `prompt_generator/Qwen3-VL-4B-Instruct` | `https://huggingface.co/Qwen/Qwen3-VL-4B-Instruct/tree/main` | verified | now included in `model-manifest.txt` as `hf_snapshot` |

## Notes

- `Flux` and `Flux2-Klein` are intentionally separated.
- The three mirrored LoRA files are now hosted under your dataset repo and should be treated as the canonical workflow filenames:
  - `Flux/art-texture-painting-v1.safetensors`
  - `Flux/flux-oilpainting-v1-3.safetensors`
  - `Flux2-Klein/impressionist-k9_2.safetensors`
- Normalize workflow model names to the Hugging Face hosted filenames when the original workflow used dirty or legacy names.
