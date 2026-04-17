---
type: memory
title: "Oculus Memory"
created: 2026-04-17
updated: 2026-04-17
tags:
  - openclaw
  - memory
  - agent
  - oculus
status: evergreen
related:
  - "[[index]]"
  - "[[overview]]"
  - "[[agents/Saul/agent]]"
  - "[[agents/Cody/agent]]"
  - "[[projects/VDR-Tuan-Chau/project]]"
---

# Oculus Memory

Long-term memory for the **Oculus** agent (OpenClaw orchestrator, running on Keezhu's macOS).

## Identity

- **Name:** Oculus 👁️
- **Role:** Orchestrator — coordinates tasks, memory, agents
- **Owner:** Keezhu (Telegram: @keeshukansai, user ID: 566009262)
- **Timezone:** Asia/Saigon (GMT+7)
- **Model stack:** minimax-m2.7:cloud + fallbacks (kimi-k2.5, glm-5.1, qwen3.5)

## Architecture

| Agent | Workspace | Role |
|---|---|---|
| **Oculus** (main) | `~/.openclaw/workspace/` | Router, memory, proactive |
| **Saul** (subagent) | `/Users/oculus/Documents/Saul` | Legal + Vietnam architecture/zoning |
| **Cody** (subagent) | `/Users/oculus/Documents/Cody` | Coding — Claude Code CLI engine |

## Skills Installed

| Skill | Purpose |
|---|---|
| `humanizer` | AI text humanization |
| `vietnamese` | Natural Vietnamese writing |
| `github` | GitHub integration |
| `weather` | Weather forecasts |
| `summarize-pro` | Content summarization |
| `openclaw-skill-vetter` | Pre-install security review |
| `self-improving-agent` | Proactive self-reflection |
| `openclaw-claude-code` | Claude Code CLI integration (Cody's engine) |

## Known Projects

### [[projects/VDR-Tuan-Chau/project]]
- Jen Tuan Chau / Caye Sereno — Ultra-luxury villa resort, Hạ Long
- 18 villas, 15,828 m², completed 2015
- Key risks: UNESCO buffer zone, planning unclear, PCCC docs missing
- Managed by: [[agents/Saul/agent]]

## System Config

- **Gateway:** loopback, port 18789
- **Telegram:** user 566009262 approved, groups allowed
- **Subagent timeout:** 300s
- **Memory backend:** builtin (memvid + SQLite)

## Obsidian Structure

- `agents/Saul/` — Saul's notes
- `agents/Cody/` — Cody's notes
- `projects/VDR-Tuan-Chau/` — Project wiki

## Learned Preferences

- Keezhu prefers direct, no-fluff communication
- Uses `trash` > `rm` for safety
- Always confirm before external actions

---

_Source: `~/.openclaw/workspace/MEMORY.md`_
_Last synced: 2026-04-17_