============================================================
aws-ai-bridge — Grok Communication Channel
============================================================

This public repository is the dedicated bridge between Grok and 
the Ubuntu server (sarahkarn@ip-172-31-40-204).

Current location: /home/sarahkarn/aws-ai-bridge

=== WIZ-WRITE PROTOCOL (Final & Simple) ===

How Grok sends files to the server:

1. Grok pushes two files to branch `wiz-inbox`:
   - payload-NAME.b64     ← base64 content only
   - payload-NAME.meta    ← exactly 3 lines

2. You run on server:
   wiz-write payload-NAME

=== META FILE FORMAT (payload-NAME.meta) ===
target=/full/path/on/server/filename.txt
mode=644
append=false

=== EXAMPLE USAGE ===
wiz-write payload-grokwiztest

=== CURRENT FILES ===
(payload-test.b64 and payload-test.meta are already here for testing)

Last updated: May 17 2026
