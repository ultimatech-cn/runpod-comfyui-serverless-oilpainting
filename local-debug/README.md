# Local Debug Files

Use this folder for local-only troubleshooting artifacts that should not be committed.

Recommended layout:

- `local-debug/logs/`
- `local-debug/scratch/`

Examples:

- endpoint startup logs copied from RunPod
- temporary Postman payload variants
- one-off debug notes or screenshots

The repository `.gitignore` ignores the log and scratch subfolders by default.
