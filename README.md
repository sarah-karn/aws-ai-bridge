# aws-ai-bridge — Grok Communication Channel

This public repository is the dedicated GitHub communication bridge between Grok (and other AIs) and my Ubuntu server.

### How It Works

- **Reading**: Grok uses the live AI Bridge web server (Cloudflared tunnel).
- **Writing changes**: Grok force-pushes to the `wiz-inbox` branch using the wiz-write convention.

---

### Wiz-Write Convention (Grok must follow exactly)

For every file Grok wants to create or modify:

1. Grok force-pushes **two files** to branch `wiz-inbox`:

   - `payload-NAME.b64` — contains ONLY the base64-encoded file content
   - `payload-NAME.meta` — plain text file containing exactly:

     target=/full/path/on/server
     mode=644
     append=false     # or true

2. Optionally include a `wiz.sh` file with human-readable steps using `# do:` lines.

### Local Commands (run on the server)

```bash
# Write / update a file (most common)
wiz-write payload-NAME

# Examples:
wiz-write payload-auth-handler
wiz-write payload-config
