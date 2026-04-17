---
type: meta
title: "Lint Report 2026-04-16"
created: 2026-04-16
updated: 2026-04-16
tags: [meta, lint]
status: developing
---

# Lint Report: 2026-04-16

## Summary
- Pages scanned: 27
- Issues found: 37
- Auto-fixed: 9
- Needs review: 28

---

## 1. Orphan Pages
No true orphan pages found. All content pages have at least 1 inbound link.

---

## 2. Dead Links (22 issues)

### Canvas/file links (3)
- [[Wiki Map]]: referenced in [[hot]], [[getting-started]], [[index]] — file exists as `Wiki Map.canvas` but wikilink resolves to `.md`. **Obsidian resolves this correctly** but it shows as dead in text search. Low priority.
- [[AI Marketing Hub Cover Images Canvas]]: referenced in [[overview]] — does not exist. Suggest: create or remove link.
- [[claude-obsidian-presentation]]: referenced in [[overview]] — canvas exists at `canvases/claude-obsidian-presentation.canvas`. Obsidian should resolve. Low priority.

### Path-style wikilinks (3)
- [[concepts/_index]]: referenced in [[dashboard]], [[index]], [[LLM Wiki Pattern]] — Obsidian resolves `_index` without path prefix. These work but are non-standard.
- [[entities/_index]]: referenced in [[index]], [[concepts/_index]], [[sources/_index]]
- [[sources/_index]]: referenced in [[log]], [[index]], [[concepts/_index]]

### Heading anchor links (13)
These all link to `cherry-picks#N. Feature Name`. They work **only if the heading text matches exactly**. Verify headings in [[cherry-picks]]:
- [[cherry-picks#1. URL Ingestion in /wiki-ingest]] — from [[kepano-obsidian-skills]]
- [[cherry-picks#2. Auto-Commit PostToolUse Hook]] — from [[ballred-obsidian-claude-pkm]]
- [[cherry-picks#3. defuddle Web Cleaning Skill]] — from [[kepano-obsidian-skills]]
- [[cherry-picks#4. Delta Tracking Manifest]] — from [[Ar9av-obsidian-wiki]]
- [[cherry-picks#5. Multi-Depth Query Modes]] — from [[rvk7895-llm-knowledge-bases]]
- [[cherry-picks#6. /wiki-ingest Vision Support]] — from [[Ar9av-obsidian-wiki]]
- [[cherry-picks#7. /adopt — Import Existing Vault]] — from [[ballred-obsidian-claude-pkm]]
- [[cherry-picks#8. Productivity Wrapper (Daily/Weekly Reviews)]] — from [[ballred-obsidian-claude-pkm]]
- [[cherry-picks#9. Multi-Agent Compatibility]] — from [[Ar9av-obsidian-wiki]], [[kepano-obsidian-skills]]
- [[cherry-picks#9. Multi-Agent Compatibility (Cursor, Windsurf, Codex)]] — from [[Ar9av-obsidian-wiki]]
- [[cherry-picks#10. Marp Presentation Output]] — from [[rvk7895-llm-knowledge-bases]]
- [[cherry-picks#11. obsidian-memory-mcp Integration]] — from [[Nexus-claudesidian-mcp]]
- [[cherry-picks#12. obsidian-bases Skill (from kepano)]] — from [[kepano-obsidian-skills]]
- [[cherry-picks#13. Schema-Emergent Vault Mode]] — from [[Ar9av-obsidian-wiki]]

### Other (3)
- [[dashboard.base]]: referenced in [[dashboard]] — `.base` files are not `.md`; Obsidian resolves these natively. Low priority.
- [[wikilinks]]: referenced in [[cherry-picks]] — page does not exist. Suggest: remove link or create stub.

---

## 3. Stale Claims
No contradictions detected between pages. Vault is young (1 source ingested).

---

## 4. Missing Pages
- **wikilinks**: mentioned in [[cherry-picks]] but no page exists. Low priority — likely a generic term, not a concept page.

---

## 5. Missing Cross-References
No significant unlinked mentions found. Cross-linking is thorough.

---

## 6. Frontmatter Gaps (8 pages)

| Page | Missing Fields |
|------|---------------|
| concepts/_index | created |
| entities/_index | created |
| sources/_index | created |
| getting-started | created |
| hot | created |
| index | created |
| log | created |
| dashboard | created |

All 8 pages are missing `created` date only.

---

## 7. Empty Sections (18 instances)

### Structural placeholders (expected)
- concepts/_index: "Add new concepts here..."
- entities/_index: "Add new entities here..."
- sources/_index: "Add new sources here..."

### Content gaps
- **Wiki vs RAG**: entire page is an empty heading
- **Hot Cache**: "Recent Context" section empty
- **cherry-picks**: Tier 1, Tier 2, Tier 3, Tier 4 sections all empty (headings only)
- **Ar9av-obsidian-wiki**: "Key Innovations" empty
- **Claudian-YishenTu**: "Key Features" empty
- **ballred-obsidian-claude-pkm**: "Key Innovations" empty
- **rvk7895-llm-knowledge-bases**: "Key Innovations" empty
- **getting-started**: "Three-Step Quick Start" empty
- **claude-obsidian-v1.2.0-release-session**: 3 empty sections
- **full-audit-and-system-setup-session**: 1 empty section

---

## 8. Stale Index Entries
Index is accurate. All 26 pages listed in [[index]] exist and link correctly. Page count in index says 26 but actual count is 27 (minor drift).

---

## Recommendations

### Quick fixes (safe to auto-fix)
1. Add `created: 2026-04-07` to the 8 pages missing it
2. Remove `[[wikilinks]]` link in cherry-picks or convert to plain text
3. Update page count in index from 26 to 27

### Needs review
4. **[[Wiki vs RAG]]** is effectively empty — flesh out or mark as seed
5. **cherry-picks** tier sections are empty headings — add content or remove tiers
6. Entity pages missing "Key Innovations"/"Key Features" content — fill or mark seed
7. **[[AI Marketing Hub Cover Images Canvas]]** link in overview points to nothing — remove or create
8. Cherry-picks heading anchors — verify headings match exactly (Obsidian is case/character sensitive on anchors)
