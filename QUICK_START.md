# Quick Start

## 1. Edit Project Config

Update these files first:

- `project-config/custom-nodes.txt`
- `project-config/model-manifest.txt`
- `project-inputs/workflow-api.json`
- `.runpod/hub.json`

Before you lock the model manifest:

- separate `workflow_ref` from the final verified source
- manually verify custom-node repos at repo level, not only by node count
- mirror unstable LoRA files to your own Hugging Face repo when needed

## 2. Run the Readiness Check

```bash
bash scripts/verify-project-readiness.sh \
  project-inputs/workflow-api.json \
  project-config/custom-nodes.txt \
  project-config/model-manifest.txt
```

Fix every reported issue before building.

## 3. Build Locally

```powershell
docker build --platform linux/amd64 -t runpod-comfyui-serverless-template:local .
```

## 4. Start the Local Stack

```powershell
docker-compose up
```

Endpoints:

- Worker API: <http://localhost:8000/docs>
- ComfyUI: <http://localhost:8188>

## 5. Download Models to the Mounted Volume

Use verified links here. Do not blindly trust workflow-exported model names.

If Hugging Face returns `401`, the repo or file usually requires:

- accepted model license on the Hugging Face web page
- a valid `HF_TOKEN` in the pod shell

Set the token before downloading:

```bash
export HF_TOKEN=hf_xxx_your_token_here
```

Single protected file example:

```bash
curl -L --fail \
  -H "Authorization: Bearer ${HF_TOKEN}" \
  -o /workspace/models/unet/flux-2-klein-9b.safetensors \
  "https://huggingface.co/black-forest-labs/FLUX.2-klein-9B/resolve/main/flux-2-klein-9b.safetensors"
```

The project download script also reads `HF_TOKEN` automatically.

If your temporary pod mounts the Network Volume at `/runpod-volume`:

```bash
bash scripts/download-models-to-volume.sh /runpod-volume project-config/model-manifest.txt /tmp/download-models-failed.txt
```

If your temporary pod exposes the same volume at `/workspace`:

```bash
bash scripts/download-models-to-volume.sh /workspace project-config/model-manifest.txt /tmp/download-models-failed.txt
```

The third argument may also be a directory such as `/tmp/`.

## 6. Verify the Volume Before Creating the Endpoint

```bash
bash scripts/verify-volume-models.sh /runpod-volume
bash scripts/verify-volume-models.sh /workspace
```

Use the path that exists in the temporary pod.

## 7. Test the Handler Contract

Minimal payload:

```json
{
  "input": {
    "workflow": {}
  }
}
```

Real payloads should usually include a full API-exported workflow and optional `images`.

## 8. Delivery Reality

This template assumes a semi-automated workflow:

- extraction tools generate drafts
- humans verify repo grouping and model truth
- final delivery uses stable mirrored links when required
