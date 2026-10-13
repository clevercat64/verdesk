<p align="center">
  <img src="./docs/logo.png" alt="Verdesk" width="120" height="120" />
</p>

<h1 align="center">Verdesk</h1>

[![Latest release](https://img.shields.io/github/v/release/clevercat64/verdesk?style=flat-square&color=28E08C)](https://github.com/clevercat64/verdesk/releases/latest)
[![Platform](https://img.shields.io/badge/Windows-10%20%7C%2011-blue?style=flat-square)](#install)

**The modulated vision and control layer for AI agents.** Verdesk is a local MCP server for Windows that hands AI agents *deltas* — not full screenshots — together with plain text and UI Automation. Result: **89–93% fewer vision tokens** on a typical session, with no loss of control.

→ Landing: **[verdesk.app](https://verdesk.app)**
→ EULA: [LICENSE](./LICENSE)
→ Skill for Claude Code: [clevercat64/verdesk-skill](https://github.com/clevercat64/verdesk-skill)

---

## Install

1. Grab the latest setup from **[Releases](https://github.com/clevercat64/verdesk/releases/latest)** (`Verdesk_x.y.z_x64-setup.exe`, ~226 MB — bundles WebView2 offline so it works on stripped Windows installs too).
2. Run it. Windows SmartScreen may warn (not code-signed yet) — *More info* → *Run anyway*.
3. Verdesk lives in your tray. First run opens a short welcome window.

Verify the download (optional, recommended):

```powershell
Get-FileHash Verdesk_x.y.z_x64-setup.exe -Algorithm SHA256
```

Compare against `SHA256SUMS.txt` on the same Release.

---

## Connect Claude Code (Local mode)

Verdesk runs an MCP server on loopback. Add it to your client:

```bash
claude mcp add --transport http verdesk http://127.0.0.1:47802/mcp
```

That's it — your AI agent now has `look`, `capture`, `act_uia`, `read_text`, profiles and the rest.

For **LAN** (same network) and **WAN** (over the internet via SSH tunnel or Tailscale), see *Settings → Connection*. Both require a **Pro** license.

---

## Pro features

| | Free | Pro ($2.90/month) |
|---|:---:|:---:|
| Modulated vision pipeline (deltas, hashing, buffer, history) | ✓ | ✓ |
| All base tools (`look`, `capture`, `act_uia`, `run_command`, profiles, …) | ✓ | ✓ |
| Local-mode MCP server | ✓ | ✓ |
| Macros: record a task once, replay it | — | ✓ |
| Saved buttons and objects (found by how they look) | — | ✓ |
| Automatic drafts of what your AI does | — | ✓ |
| Remote access (LAN / WAN) | — | ✓ |
| Commercial use | — | ✓ (1 developer · up to 2 devices) |

→ **[Buy Pro](https://pay.verdesk.app)** — $2.90/month subscription. Pay online, receive your license by email, paste it in *Settings → License*. One license works on up to 2 computers.

---

## Compatibility

- Windows 10 / 11 (x64)
- Works with **Claude Code**, **GPT** (any MCP-compatible client) and **local models**
- No usage telemetry · No account required · Single executable
- What does leave your PC: the sign-up report when you finish the first-run welcome (your `email`, a random `machine_id` made on this PC, the `app_version` and your tier, Free or Pro; never your license key), sent to a script run by the project owner; license checks with `pay.verdesk.app` if you have a paid license; checks for new releases on GitHub; and a report only if you or your agent choose to send one. The exact fields are listed in [SECURITY.md](./.github/SECURITY.md).

---

## Reporting bugs

Open an issue with: Verdesk version (*Settings → Home*), Windows version, mode (Local/LAN/WAN) and steps to reproduce.

Security vulnerabilities: see [SECURITY.md](./.github/SECURITY.md).

---

## License

Verdesk is **proprietary, source-available only for the prebuilt binaries** distributed here. The full EULA is in [LICENSE](./LICENSE).

© clever.cat — Camilo Brossard · `support@clever.cat`
