# Project Config

Keep per-project dependencies here.

## Files

- `custom-nodes.txt`: custom node sources
- `model-manifest.txt`: model download list for volume preparation
- `model-truth.md`: human-verified model identity and source notes
- `dependency-notes.md`: merged workflow dependency summary
- `env.example`: environment variable template for project notes

Do not hardcode project-specific dependencies directly into `Dockerfile` unless there is no practical alternative.
