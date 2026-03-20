# Baroque Oil Painting Serverless

This repository is the Baroque oil painting RunPod ComfyUI project derived from the serverless template.

The repo now carries project-specific workflow, custom node, and model manifests for two related workflows:

- portrait workflow
- pet workflow

## Start Here

Read these in order:

1. `QUICK_START.md`
2. `SOP_RUNBOOK.md`
3. `PITFALLS.md`
4. `MANUAL_CHECKLIST.md`
5. `scripts/README.md`
6. `AGENTS.md`

## Current Project Inputs

- `project-config/custom-nodes.txt`
- `project-config/model-manifest.txt`
- `project-config/model-truth.md`
- `project-config/dependency-notes.md`
- `project-inputs/workflow-api.json`
- `project-inputs/workflow-pet-api.json`
- `project-inputs/workflow-portrait-api.json`
- `project-inputs/test-payload-minimal.json`
- `project-inputs/test-payload-with-image.json`
- `.runpod/hub.json`

`project-inputs/workflow-api.json` currently mirrors the pet workflow as the default entry.

## Current Verified Runtime

The currently verified image for the Baroque project is:

- `ultimatech/runpod-comfyui-serverless-oilpainting:v0.1.5`

This image includes:

- newer RunPod ComfyUI base image
- `transformers` pinned to `<5`
- extra runtime packages required during real endpoint debugging:
  - `opencv-contrib-python`
  - `pyOpenSSL`

## Stable Runtime Layer

- `handler.py`
- `src/start.sh`
- `Dockerfile`
- `scripts/download-models-to-volume.sh`
- `scripts/install-custom-nodes.sh`

Change these only when there is a real deployment issue to solve.

## Repository Layout

```text
runpod-comfyui-serverless-oilpainting/
  .runpod/
  project-config/
  project-inputs/
  scripts/
  src/
  templates/serverless-project/
  tests/
  Dockerfile
  docker-compose.yml
  handler.py
  README.md
  QUICK_START.md
  SOP_SIMPLE.md
  SOP_RUNBOOK.md
  PITFALLS.md
  MANUAL_CHECKLIST.md
  DELIVERY_CHECKLIST.md
  AGENTS.md
```

## Working Rules

- Keep workflow-specific logic in the workflow JSON before touching `handler.py`.
- Install custom nodes into the image.
- Put models on a Network Volume.
- Keep workflow model names aligned with the Hugging Face filenames in `project-config/model-manifest.txt`.
- Use `project-config/model-truth.md` when auditing model identity or changing download sources.

## Hugging Face Auth

Some models return `401` until both conditions are met:

- you accepted the model license on Hugging Face
- you exported `HF_TOKEN` inside the temporary pod shell

Example:

```bash
export HF_TOKEN=hf_xxx_your_token_here
bash scripts/download-models-to-volume.sh /workspace project-config/model-manifest.txt /tmp/download-models-failed.txt
```

For a single protected file:

```bash
curl -L --fail \
  -H "Authorization: Bearer ${HF_TOKEN}" \
  -o /workspace/models/unet/flux-2-klein-9b.safetensors \
  "https://huggingface.co/black-forest-labs/FLUX.2-klein-9B/resolve/main/flux-2-klein-9b.safetensors"
```

## Request Contract

Use RunPod input shaped like:

```json
{
  "input": {
    "workflow": {},
    "images": []
  }
}
```

`images` is optional.

## Response Contract

Read generated media from `output.images[]`.

Each item contains:

- `filename`
- `type`
- `data`

For base64 responses, `data` may already include a data URI prefix.
