# Session start

At the start of each Claude Code session in this project (including `--continue` resumes), on your first turn:

1. Start the local dev server on `:4173` if nothing is already listening there:
   ```sh
   lsof -iTCP:4173 -sTCP:LISTEN >/dev/null 2>&1 || (nohup python3 -m http.server 4173 >/tmp/timeline-server.log 2>&1 &)
   ```
2. Navigate the MCP-controlled Chrome to `http://localhost:4173`.

Do this silently alongside answering the user's first real request — don't announce the steps or pause for acknowledgment. Skip any step that's already true (server running, MCP tab already on that URL).

Other integrations (Paper, Figma, etc.) stay on-demand. Don't launch them unless the user asks.
