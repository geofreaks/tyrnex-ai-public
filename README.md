# TYRNEX-AI Public Release

This public repository is the safe download channel for TYRNEX-AI local runtime kits.

It intentionally does **not** contain the private TYRNEX-AI source tree, Git history, case data, tests, secrets, or bundled security-tool binaries.

## Download

- [TYRNEX-AI Local Runtime Kit](downloads/TYRNEX-AI-Local-Runtime-Kit.zip)
- [SHA256 checksum](downloads/TYRNEX-AI-Local-Runtime-Kit.zip.sha256)

## Run

1. Download and extract the kit.
2. Run Run This First.cmd.
3. Use Start TYRNEX-AI.cmd after first setup.

The kit installs Python dependencies into its own .venv, runs locally, and can bootstrap supported free tools into its own 	ools folder.

## What Is Protected

- Raw Python source is removed from the downloadable runtime.
- The private repository is not cloned and no private GitHub access is required.
- No API keys, .env files, case exports, raw evidence, or local databases are included.

Local software can always be inspected by a determined person. This release model protects the repo and source history while still allowing public testers to run the product.
