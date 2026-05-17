============================================================
          aws-ai-bridge — Grok Communication Channel
============================================================

This public repository is the dedicated GitHub communication bridge 
between Grok (and other AIs) and my Ubuntu server.

HOW IT WORKS
------------
- Reading files  → Grok uses the AI Bridge web server (Cloudflared tunnel)
- Writing files  → Grok force-pushes to branch "wiz-inbox" using the 
                  wiz-write convention

WIZ-WRITE CONVENTION (Grok must follow exactly)
------------------------------------------------
For every file Grok wants to create or edit:

1. Push these TWO files to branch "wiz-inbox":
   - payload-NAME.b64     → contains ONLY the base64-encoded content
   - payload-NAME.meta    → plain text with exactly these 3 lines:

     target=/full/path/on/server
     mode=644
     append=false          # change to true if appending

2. Optionally include a wiz.sh file with human-readable steps.

LOCAL COMMAND (run on the server)
---------------------------------
wiz-write payload-NAME

Examples:
   wiz-write payload-auth-handler
   wiz-write payload-config

STANDARD PROMPT TO GIVE GROK
----------------------------
Use repo sarah-karn/aws-ai-bridge as the communication channel. 
Force-push to branch wiz-inbox using the wiz-write convention 
(payload-xxx.b64 + payload-xxx.meta).

Last updated: 2026-05-17
============================================================
