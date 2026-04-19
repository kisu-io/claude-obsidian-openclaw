---
type: memory
title: "Oculus Memory"
created: 2026-04-17
updated: 2026-04-19
tags:
  - openclaw
  - memory
  - agent
  - oculus
status: evergreen
---

# Oculus Memory

Long-term memory for **Oculus** — OpenClaw orchestrator agent.

## Identity

- **Name:** Oculus 👁️
- **Role:** Orchestrator & Strategic Advisor
- **Owner:** Keezhu (Telegram: @keeshukansai, user ID: 566009262)
- **Timezone:** Asia/Saigon (GMT+7)

## Architecture

| Agent | Workspace | Role |
|---|---|---|
| **Oculus** (main) | `~/.openclaw/workspace/` | Router, memory, proactive |
| **Saul** (subagent) | `/Users/oculus/Documents/Saul` | Legal + Vietnam architecture/zoning |
| **Cody** (subagent) | `/Users/oculus/Documents/Cody` | Coding — Claude Code CLI engine |

## Project Memory Structure

Projects are **ISOLATED** — each has its own memory:

| Project | Path | Status |
|---|---|---|
| **VDR-Tuan-Chau** | `projects/VDR-Tuan-Chau/project.md` | Active |
| **CUR-8** | `projects/CUR-8/project.md` | New — pending info |

**Rule:** VDR and CUR-8 do NOT share context. Each project loads its own memory only.

## System Config

- **Gateway:** loopback, port 18789
- **Channel:** Telegram (user 566009262 approved)
- **Memory backend:** builtin (memvid + SQLite)
- **Subagent timeout:** 300s
- **Session auto-compact:** 7d prune, 120min idle

## Obsidian Sync

- Vault: `~/claude-obsidian/wiki/`
- Git remote: `https://github.com/kisu-io/claude-obsidian-openclaw`

---

_Source: `~/.openclaw/workspace/MEMORY.md`_