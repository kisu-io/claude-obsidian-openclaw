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
---

# Oculus Memory

Long-term memory for the **Oculus** agent (OpenClaw orchestrator, running on Keezhu's macOS).

> This note is synced from OpenClaw's `MEMORY.md` — do not edit directly here.

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

## Key Files

- OpenClaw MEMORY.md: `~/.openclaw/workspace/MEMORY.md`
- Saul system prompt: `~/.openclaw/agents/saul/agent/system-prompt.md`
- Saul project memory: `/Users/oculus/Documents/Saul/memory/vdr-tuan-chau.md`

## Known Projects

### Jen Tuan Chau / Caye Sereno
- Ultra-luxury villa resort, Đảo Tuần Châu, Hạ Long
- 18 villas, 15,828 m², completed 2015
- Corporate: Công ty TNHH Jen Tuan Chau — MST 5701599302
- Ownership: 49% Đào Ngọc Co. / 51% Jen Capital Vietnam (Chiaphua Group, Hong Kong)
- Leadership: Chủ tịch Đào Thùy Phương Thảo, TGĐ Huỳnh Quang Thuận
- Legal: Investment cert + ĐKKD amended 5×, land certs Bi 462036 + Bi 462037
- Key risks: UNESCO buffer zone, planning status unclear, PCCC docs missing
- Full details: `/Users/oculus/Documents/Saul/memory/vdr-tuan-chau.md`

## System Config

- **Gateway:** loopback, port 18789, auth token set
- **Telegram:** connected (user 566009262 approved)
- **Memory backend:** builtin (memvid + SQLite)
- **Memvid:** `~/.openclaw/memvid/main.mv2`
- **Memory SQLite:** `~/.openclaw/memory/main.sqlite` + `oculus.sqlite`
- **Daily notes:** `memory/YYYY-MM-DD.md` in workspace

## Obsidian Link

Sync anchor: `[[MEMORY]]` ↔ `~/.openclaw/workspace/MEMORY.md`

Last synced: 2026-04-17

---
_This is a mirror of the OpenClaw MEMORY.md — source of truth lives at `~/.openclaw/workspace/MEMORY.md`_