# aws-ai-bridge — Grok Communication Channel

This public repository is the dedicated communication bridge between Grok (and other AIs) and my Ubuntu server.

### How It Works

- Reading: Grok uses the AI Bridge web server (Cloudflared tunnel)
- Writing: Grok force-pushes to branch `wiz-inbox` using the wiz-write convention

### Wiz-Write Convention (Grok must follow exactly)

For every file:

1. Push these two files to `wiz-inbox`:
   - `payload-NAME.b64` → only base64 content
   - `payload-NAME.meta` → exactly these 3 lines:

target=/full/path/on/server
mode=644
append=false

2. (Optional) Add `wiz.sh` with human readable steps.

### Local command

```bash
wiz-write payload-NAME
