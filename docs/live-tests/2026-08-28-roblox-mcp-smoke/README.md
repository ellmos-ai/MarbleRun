# Roblox Studio MCP smoke test — 2026-08-28

This host-local smoke test proves the complete non-destructive path:

1. Roblox Studio MCP initialized with protocol `2025-03-26`.
2. `list_roblox_studios` returned the open `server.rbxl` session.
3. `screen_capture` returned an image and the helper persisted it as
   `studio-edit-view.jpg`.
4. Open Compute captured the exact visible Studio window as
   `open-compute-studio-window.png`.
5. `get_console_output` completed without an error.
6. Process readback found no wrapper or `StudioMCP` orphan after disconnect.

The installed Studio update had left `%LOCALAPPDATA%\Roblox\mcp.bat` pointing
to a removed version directory. The public wrapper now resolves the newest
installed `StudioMCP.exe` when that generated BAT is stale. Studio's own
"Studio als MCP-Server aktivieren" switch also had to be toggled once after the
update before the open session appeared.

See `capture-receipt.json` for the image hash and `list-result-after-toggle.json`
for the raw, base64-free studio discovery receipt.
