# SOP Runbook

## Inputs You Need

- API-exported workflow JSON
- reference input files or image URLs
- model download sources
- custom node repositories or registry names
- expected output format

## Real Operating Model

This SOP is semi-automated:

- workflow extraction can produce draft dependency lists
- custom-node repos still need human confirmation
- model names exported from third-party workflow platforms may be dirty or misleading
- final delivery should prefer manually verified links and your own Hugging Face mirror when needed

Treat node repo grouping as higher risk than model-link cleanup, because repo mistakes force image rebuilds.

## Required Checks Before Build

- run `scripts/verify-project-readiness.sh`
- confirm every required node is in `project-config/custom-nodes.txt`
- confirm every required model is in `project-config/model-manifest.txt` or explicitly marked as preloaded
- confirm the custom-node list is repo-level correct, not only node-level complete
- confirm LoRA links are stable enough for delivery or mirrored to your own Hugging Face repo

## Recommended Model Workflow

1. extract workflow dependencies into a draft
2. keep the workflow name as `workflow_ref`
3. manually verify the true model source
4. mirror unstable LoRA files to your own Hugging Face repo
5. put the final mirrored link into `project-config/model-manifest.txt`

## Required Checks Before Endpoint Creation

- confirm the temporary pod and endpoint use the same Network Volume
- confirm the actual mount path in the temporary pod
- confirm the volume contains the expected model files
- confirm mirrored LoRA files are reachable from their final Hugging Face URLs

## Required Checks After Endpoint Creation

- confirm startup logs show the detected models root
- confirm a known-good payload returns media in `output.images[]`
- confirm large outputs use S3 if base64 is too large
