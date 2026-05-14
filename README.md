# AWS AI Bridge

This repo acts as a **bridge** between Grok (via native GitHub connector) and the ai-bridge running on my AWS server.

## How it works
- Grok edits files in this repo
- ai-bridge pulls the changes and writes them to the local filesystem
- (Later: push changes back from server to GitHub)

## Folder structure
- `bridge/` → files that will be synced to AWS
