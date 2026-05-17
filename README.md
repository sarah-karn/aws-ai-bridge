cd /home/sarahkarn/aws-ai-bridge

# 1. Switch to main and pull latest
git checkout main
git pull origin main

# 2. Remove old stuff
rm -rf bridge/ 2>/dev/null || true

# 3. Create **clean** README.md
cat > README.md << 'EOD'
# aws-ai-bridge — Grok Communication Channel

This public repository is the **dedicated communication bridge** between Grok (and other AIs) and my Ubuntu server (`sarahkarn`).

### How It Works

- **Reading files** — Grok uses the AI Bridge web server (Cloudflared tunnel).
- **Writing changes** — Grok force-pushes to the `wiz-inbox` branch using the **wiz-write convention**.

---

### Wiz-Write Convention (Grok must follow exactly)

For every file Grok wants to create or edit:

1. Force-push **two files** to branch `wiz-inbox`:
   - `payload-NAME.b64` — contains **only** the base64-encoded content
   - `payload-NAME.meta` — plain text with exactly these lines:

example meta file:

target=/full/path/on/server
mode=644
append=false



2. Optionally include a `wiz.sh` with human-readable `# do:` steps.

### Local Command (on server)

```bash
wiz-write payload-NAME



