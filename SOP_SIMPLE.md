# SOP Simple

1. Collect the client workflow, sample inputs, model sources, and custom node sources.
2. Fill `templates/serverless-project/00_project-intake.md`.
3. Extract a draft dependency list, then manually verify node repos and real model sources.
4. Mirror unstable LoRA files to your own Hugging Face repo when needed.
5. Update `project-config/custom-nodes.txt` and `project-config/model-manifest.txt`.
6. Manually verify shared Python dependencies required by custom nodes, especially `transformers`, `huggingface_hub`, `accelerate`, `opencv-python`, and `opencv-contrib-python`.
7. Run `scripts/verify-project-readiness.sh`.
8. Build the image locally.
9. Mount the target volume in a temporary pod and run `scripts/download-models-to-volume.sh`.
10. Verify the volume with `scripts/verify-volume-models.sh`.
11. Create the endpoint and mount the same volume.
12. Test with at least one minimal payload and one representative payload.
13. If local workflow works but RunPod fails, check in this order: model file identity, custom-node Python dependencies, then ComfyUI core version.
14. Deliver the endpoint with request and output examples.
