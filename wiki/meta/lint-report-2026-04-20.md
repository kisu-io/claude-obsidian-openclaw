---
type: meta
title: "Lint Report 2026-04-20"
created: 2026-04-20
updated: 2026-04-20
tags: [meta, lint]
status: developing
---

# Lint Report: 2026-04-20

## Summary

- Pages scanned: 34
- Issues found: 41 (6 critical, 18 warnings, 17 suggestions)
- New since 2026-04-16: 7 pages added (MEMORY.md, agents/Cody/agent.md, agents/Saul/agent.md, projects/CUR-8/project.md, projects/VDR-Tuan-Chau/project.md, projects/VDR-Tuan-Chau/maps/quang-ninh-planning-maps.md, meta/lint-report-2026-04-16.md)
- Comparison to prior report: several prior issues resolved, several new issues introduced by new pages

---

## Regressions vs 2026-04-16

The following issues are new since the last lint pass (introduced by the 7 new pages):

- 6 new pages with missing or incomplete frontmatter (all 7 new pages lack required fields)
- 3 new orphan pages (agent pages and project pages not linked from index)
- 1 new dead link (Saul/agent.md links to [[VDR Tuan Chau]] which does not exist as a wikilink target)
- index.md page count still stale (was 27 on 2026-04-16, now shows 27 but actual count is 34)
- sources/_index.md "Transcripts" section remains empty (not fixed since prior report)

## Improvements vs 2026-04-16

- [[Wiki vs RAG]] is no longer empty: full comparison table and verdict now present. Prior report flagged it as "effectively empty". Resolved.
- [[Hot Cache]] (concept page) "Recent Context" section: the concept page is substantive. Prior report confusion was between hot.md (the cache file itself) and concepts/Hot Cache.md (the concept page). Both are now populated.
- The heading anchor links to [[cherry-picks#N. Feature Name]] are now verified: the cherry-picks page headings match exactly (e.g. "### 1. URL Ingestion in /wiki-ingest"). The anchor links from entity pages are correct.

---

## Critical (must fix)

### C-1. Dead link: [[VDR Tuan Chau]] in agents/Saul/agent.md

- **Affected page:** [[agents/Saul/agent.md]]
- **Problem:** Line "[[VDR Tuan Chau]]" in the Known Projects section. The actual file is at `projects/VDR-Tuan-Chau/project.md`. Obsidian resolves by filename stem, so the wikilink would need to be [[VDR-Tuan-Chau]] or use a display alias `[[VDR-Tuan-Chau|VDR Tuan Chau]]`. As written, "VDR Tuan Chau" (with spaces) does not match the file stem "VDR-Tuan-Chau" (with hyphens) and will not resolve in strict mode.
- **Suggested fix:** Change to `[[VDR-Tuan-Chau|VDR Tuan Chau]]` or rename the project file to `VDR Tuan Chau.md`.

### C-2. Dead link: [[claude-obsidian-v1.4-release-session]] in hot.md

- **Affected page:** [[hot]]
- **Problem:** hot.md references `[[claude-obsidian-v1.4-release-session]]` in its related frontmatter and in body text. The actual file is `wiki/meta/claude-obsidian-v1.4-release-session.md`. The stem `claude-obsidian-v1.4-release-session` includes a dot, which Obsidian handles inconsistently. However, the file does exist and Obsidian should resolve it. Flag as low-risk but verify in Obsidian graph view.
- **Suggested fix:** Verify the link resolves in Obsidian. If not, rename the file to remove the dot: `claude-obsidian-v14-release-session.md`.

### C-3. Stale index: page count and missing entries

- **Affected page:** [[index]]
- **Problem (a):** Header reads "Total pages: 27" but 34 markdown files now exist in the vault. The count has not been updated since 2026-04-16.
- **Problem (b):** Seven pages added since the last index update are not listed: MEMORY.md, agents/Cody/agent.md, agents/Saul/agent.md, projects/CUR-8/project.md, projects/VDR-Tuan-Chau/project.md, projects/VDR-Tuan-Chau/maps/quang-ninh-planning-maps.md, meta/lint-report-2026-04-16.md.
- **Suggested fix:** Update header count to 34. Add an "Agents" section, a "Projects" section, and a "Meta" subsection for lint reports. Link all 7 missing pages.

### C-4. Dead link: [[dashboard]] referenced throughout but dashboard.md has no equivalent wikilink target for "dashboard"

- **Affected pages:** [[index]], [[overview]], [[hot]], [[getting-started]], [[log]], [[dashboard]] itself
- **Problem:** The file is `wiki/meta/dashboard.md`. The wikilink `[[dashboard]]` works only if Obsidian can find a file with stem "dashboard". The file is inside `wiki/meta/`, not `wiki/`. Obsidian uses global search so this likely resolves, but it is fragile. If another file named "dashboard" exists elsewhere the link breaks. More critically, [[dashboard.base]] referenced inside dashboard.md does not exist as a tracked markdown file (it is a .base file, not .md).
- **Suggested fix:** Confirm [[dashboard]] resolves correctly in Obsidian. Add a note that [[dashboard.base]] is an Obsidian Bases file (non-markdown) and will not appear in link graphs.

### C-5. Missing frontmatter on all 3 project pages and 2 agent pages

- **Affected pages:** projects/CUR-8/project.md, projects/VDR-Tuan-Chau/project.md, projects/VDR-Tuan-Chau/maps/quang-ninh-planning-maps.md, agents/Cody/agent.md, agents/Saul/agent.md
- **Problem:** All five files have no YAML frontmatter block whatsoever. Required fields per wiki convention: `type`, `status`, `created`, `updated`, `tags`. Without frontmatter, Dataview/Bases queries cannot include these pages, and the lint skill cannot categorize them.
- **Suggested fix:** Add frontmatter to each. Suggested values:
  - CUR-8/project.md: type: project, status: seed, created: 2026-04-19, updated: 2026-04-19, tags: [project, cur-8]
  - VDR-Tuan-Chau/project.md: type: project, status: developing, created: 2026-04-17, updated: 2026-04-17, tags: [project, vdr, tuan-chau, vietnam]
  - quang-ninh-planning-maps.md: type: reference, status: developing, created: 2026-04-17, updated: 2026-04-17, tags: [project, vdr, maps, planning, vietnam]
  - Cody/agent.md: type: agent, status: evergreen, created: 2026-04-17, updated: 2026-04-17, tags: [agent, cody, openclaw]
  - Saul/agent.md: type: agent, status: evergreen, created: 2026-04-17, updated: 2026-04-17, tags: [agent, saul, openclaw, legal, vietnam]

### C-6. Missing frontmatter on MEMORY.md (incomplete)

- **Affected page:** [[MEMORY]]
- **Problem:** MEMORY.md has frontmatter but is missing `tags` (it uses tags inline but the array uses hyphens correctly) — wait, it does have tags. Re-check: MEMORY.md has type, title, created, updated, tags, status. All required fields present. This is not a critical issue. Downgrade: see W-1 for a related warning.

---

## Warnings (should fix)

### W-1. MEMORY.md is an orphan: not linked from index or any content page

- **Affected page:** [[MEMORY]]
- **Problem:** MEMORY.md exists at `wiki/MEMORY.md` but is not referenced from index.md, overview.md, hot.md, or any other page. It is a live operational document (updated 2026-04-19) with no inbound wikilinks.
- **Suggested fix:** Add a "System" or "Memory" section to index.md linking [[MEMORY]]. Or add a related link from hot.md since both are operational context files.

### W-2. agents/Cody/agent.md is an orphan

- **Affected page:** [[agents/Cody/agent.md]]
- **Problem:** Not linked from index.md or any other page. The MEMORY.md lists Cody in an architecture table (plain text, no wikilink).
- **Suggested fix:** Add an "Agents" section to index.md. Add a wikilink to Cody in MEMORY.md's Architecture table.

### W-3. agents/Saul/agent.md is an orphan (and has broken link)

- **Affected page:** [[agents/Saul/agent.md]]
- **Problem:** Not linked from index.md or any other page. MEMORY.md lists Saul in plain text without a wikilink. Also see C-1 for the broken [[VDR Tuan Chau]] link within this page.
- **Suggested fix:** Same as W-2: add to index.md Agents section, add wikilink in MEMORY.md.

### W-4. projects/CUR-8/project.md is an orphan

- **Affected page:** [[projects/CUR-8/project.md]]
- **Problem:** Not linked from index.md or any other page. MEMORY.md mentions CUR-8 in a table with plain text path reference, not a wikilink.
- **Suggested fix:** Add a "Projects" section to index.md. Convert the MEMORY.md table entry to a wikilink.

### W-5. projects/VDR-Tuan-Chau/project.md is an orphan

- **Affected page:** [[projects/VDR-Tuan-Chau/project.md]]
- **Problem:** Not linked from index.md. Saul/agent.md has a broken wikilink [[VDR Tuan Chau]] that does not resolve correctly (see C-1). No valid inbound link exists.
- **Suggested fix:** Add to index.md Projects section. Fix the link in Saul/agent.md.

### W-6. projects/VDR-Tuan-Chau/maps/quang-ninh-planning-maps.md is an orphan

- **Affected page:** quang-ninh-planning-maps.md
- **Problem:** No other page links to it. Not in index. Not referenced from VDR-Tuan-Chau/project.md (which has no wikilinks at all).
- **Suggested fix:** Add a "Maps" or "Related" section to VDR-Tuan-Chau/project.md linking this file. Add to index.md Projects section.

### W-7. meta/lint-report-2026-04-16.md is an orphan

- **Affected page:** lint-report-2026-04-16.md
- **Problem:** No other page links to the prior lint report. Not listed in index.md.
- **Suggested fix:** Add a "Lint Reports" subsection to index.md (or the meta section) listing past reports.

### W-8. index.md "Last updated" header is stale (2026-04-16, sources: 2)

- **Affected page:** [[index]]
- **Problem:** Header says "Last updated: 2026-04-16 | Total pages: 27 | Sources ingested: 2". Today is 2026-04-20. 7 new pages exist. The header is stale in all three values.
- **Suggested fix:** Update to: "Last updated: 2026-04-20 | Total pages: 34 | Sources ingested: 2"

### W-9. index.md "Domains" section is empty

- **Affected page:** [[index]]
- **Problem:** The Domains section contains only an HTML comment `<!-- Add domain entries here after scaffold -->`. It has been empty since creation (2026-04-07). This is a heading with no content.
- **Suggested fix:** Either remove the section until domains exist, or add a stub entry explaining the domain pattern is not yet in use.

### W-10. sources/_index.md "Transcripts" section is empty

- **Affected page:** [[sources/_index]]
- **Problem:** The Transcripts subsection under Sources Index has no entries. It has been empty since creation (flagged in prior lint report). The one actual source (claude-obsidian-ecosystem-research) is categorized as research/web, not transcript, so there may be no transcript sources yet.
- **Suggested fix:** If no transcripts exist, remove the heading or replace with a comment. If transcript sources exist elsewhere, add the links.

### W-11. entities/_index.md Organizations and Products sections are empty placeholders

- **Affected page:** [[entities/_index]]
- **Problem:** The Organizations section contains only an HTML comment. Products & Tools section also. Seven entity pages exist in entities/ covering repos/tools/people, but only one (Andrej Karpathy) is listed under People. All six repo entities are unlisted in the entities index.
- **Suggested fix:** Add the 6 repo entities to the Products & Tools section. This is a significant gap in the entities index.

### W-12. CUR-8/project.md is a near-empty seed with no useful content

- **Affected page:** projects/CUR-8/project.md
- **Problem:** Contains only placeholder text ("TBD", "chờ Keezhu cung cấp"). Status is implicitly seed. File was last updated 2026-04-19 (within 30 days, so not stale by the 30-day rule), but it has zero informational content. It is a stub that was created prematurely.
- **Suggested fix:** Either mark explicitly as status: seed and add a [[gap]] callout, or leave until real project info is received. At minimum add frontmatter (see C-5).

### W-13. VDR-Tuan-Chau/project.md uses emoji in body text

- **Affected page:** projects/VDR-Tuan-Chau/project.md
- **Problem:** Body text uses emoji flags (🔴 🟡) as status indicators in the Key Risks section. This is inconsistent with the wiki writing style (declarative prose, no emoji as content markers). The wiki style guide (inferred from the em-dash scrub and style notes in hot.md) values clean plain text.
- **Suggested fix:** Replace emoji with text labels: [HIGH RISK], [MEDIUM RISK], or use a `> [!gap]` callout pattern for risks.

### W-14. quang-ninh-planning-maps.md uses emoji throughout as section markers

- **Affected page:** quang-ninh-planning-maps.md
- **Problem:** Section headers and body use emoji extensively (📥, 📍, 🗺️, ⚠️, 🔗, 📌). Inconsistent with the rest of the wiki's plain-text style, which explicitly discourages emoji in the hot.md style preferences. Also uses `#tag` inline at the bottom instead of frontmatter tags.
- **Suggested fix:** Remove emoji from headers. Convert `_tags: #planning #quang-ninh...` at the bottom to proper frontmatter tags field. (See also C-5 for the missing frontmatter block entirely.)

### W-15. overview.md Current State section is stale

- **Affected page:** [[overview]]
- **Problem:** States "Sources ingested: 2 / Wiki pages: 26 / Last activity: 2026-04-08 (v1.4.1 shipped)". Actual count is now 34 pages, and last activity was 2026-04-19 (new project/agent pages added). The overview is 12 days out of date.
- **Suggested fix:** Update page count and last activity date. Consider linking to MEMORY.md from overview since that file contains more current system state.

### W-16. log.md has a malformed entry (broken paragraph)

- **Affected page:** [[log]]
- **Problem:** Lines 53-55 show a dangling log entry with no date header:
  ```
  - Source: `.raw/` (first ingest)
  - Pages updated: [[index]], [[log]], [[hot]], [[overview]]
  - Key insight: The wiki pattern turns ephemeral AI chat...
  ```
  This appears to be a fragment of the first ingest entry that was accidentally separated from its `## [YYYY-MM-DD]` header. It appears between the v1.2.0 session entry and the vault setup entry with no parent heading.
- **Suggested fix:** Restore the missing `## [2026-04-07] ingest | First Source` heading above these bullet points.

### W-17. "Stale seed" check: How does the LLM Wiki pattern work.md (status: developing, 13+ days old)

- **Affected page:** [[How does the LLM Wiki pattern work]]
- **Problem:** Status is `developing`, not `seed`, so this does not trigger the 30-day seed rule. However, the question was created 2026-04-07 and last updated 2026-04-07 — 13 days without update. The answer is present and marked `answer_quality: definitive`. The status probably should be `mature` or `evergreen` rather than `developing` since the answer is complete.
- **Suggested fix:** Update status from `developing` to `mature`. Update `updated` field to today.

### W-18. overview.md status: developing with no recent update

- **Affected page:** [[overview]]
- **Problem:** Status is `developing`, created and last updated 2026-04-07. It is 13 days old at `developing` status. The "Current Seed Content" and "Current State" sections contain stale data (page count wrong, activity date wrong). The `sources:` frontmatter field is empty (value is blank after the key).
- **Suggested fix:** Fix the stale data (see W-15). Add actual source references to the `sources:` frontmatter field (e.g., `[[claude-obsidian-ecosystem-research]]`). Consider promoting to `evergreen` if the overview is meant to be a stable navigation page.

---

## Suggestions (worth considering)

### S-1. Oculus / OpenClaw system has no concept page

- **Problem:** MEMORY.md, Cody/agent.md, and Saul/agent.md all describe the OpenClaw multi-agent system and Oculus orchestrator, but there is no concept page for these. "OpenClaw", "Oculus", and the agent architecture are mentioned across 3 pages without a dedicated page.
- **Suggested fix:** Create `concepts/OpenClaw.md` or `entities/Oculus.md` covering the orchestrator architecture, agent roster, and system config.

### S-2. "VDR Tuan Chau" / "Jen Tuan Chau" / "Caye Sereno" are multiple names for the same project with no disambiguation

- **Problem:** The project is called "VDR Tuan Chau" in MEMORY.md and the file path, "Jen Tuan Chau / Caye Sereno" in project.md's H2 heading, and "Lâm Ngọc villa zone" in the maps file. Three names, no canonical page or redirect.
- **Suggested fix:** Add an `aliases:` frontmatter field to VDR-Tuan-Chau/project.md with all three names, and note the canonical name in the opening line.

### S-3. Linus Kepano is mentioned by name in kepano-obsidian-skills.md but has no entity page

- **Affected page:** [[kepano-obsidian-skills]]
- **Problem:** "Linus Kepano — creator of Obsidian + Minimal theme" is mentioned as significant (he validates the Agent Skills format, he is the creator of Obsidian itself), but there is no entity page for him. He is mentioned in one page only.
- **Suggested fix:** Create `entities/Linus Kepano.md` if he is expected to be referenced in future ingests. Low priority since he appears in only one page currently.

### S-4. "ekadetov/llm-wiki" is mentioned in cherry-picks as a source but has no entity page

- **Affected page:** [[cherry-picks]]
- **Problem:** cherry-picks.md mentions "ekadetov/llm-wiki" as the source for URL Ingestion (#1) and Auto-Commit (#2), and "rvk7895/llm-knowledge-bases, ekadetov/llm-wiki" as sources for Marp Output (#10). No entity page exists for ekadetov/llm-wiki. It appears in 3 feature entries.
- **Suggested fix:** Create `entities/ekadetov-llm-wiki.md` entity stub. This repo influenced multiple cherry-picks and would fit the existing entity pattern.

### S-5. "infio-copilot" appears in the ecosystem comparison but has no entity page

- **Affected page:** [[claude-obsidian-ecosystem]]
- **Problem:** infio-copilot appears in the Native Obsidian Plugins comparison table with substantive data (semantic search, workspaces, ~300 stars). No entity page exists for it.
- **Suggested fix:** Create `entities/infio-copilot.md` if future research on native plugins is expected. Currently single-page mention.

### S-6. "Weizhena" attribution in rvk7895-llm-knowledge-bases.md is unlinked

- **Affected page:** [[rvk7895-llm-knowledge-bases]]
- **Problem:** Attribution line reads "Built on Karpathy pattern + Weizhena's Deep Research skills adapted for the research pipeline." Weizhena is mentioned nowhere else and has no entity page.
- **Suggested fix:** If Weizhena's Deep Research is a relevant tool in the ecosystem, create a stub entity or add a plain-text citation URL. If not significant enough for its own page, convert to a footnote.

### S-7. cherry-picks.md lacks source wikilinks for several repos mentioned in feature descriptions

- **Affected page:** [[cherry-picks]]
- **Problem:** Feature descriptions mention repos without wikilinks: "ekadetov/llm-wiki" (features #1, #2, #10), "heyitsnoah/claudesidian" (feature #7), "YuNaga224/obsidian-memory-mcp" (feature #11). The entity pages for these do not exist. Currently these are plain text, not wikilinks.
- **Suggested fix:** Either create entity stubs for these repos and add wikilinks, or add a note that they are unresolved external references.

### S-8. hot.md references [[claude-obsidian-v1.4-release-session]] but this is a meta page not in the main index flow

- **Affected page:** [[hot]]
- **Problem:** The related field in hot.md frontmatter links to [[claude-obsidian-v1.4-release-session]]. This file is in wiki/meta/ and is reachable. However, hot.md is supposed to be a ~500-word session context file (per concept definition), but the current version is 70 lines and contains style preferences, repo locations, and install commands. The file has drifted toward a persistent notes document rather than a pure session context cache.
- **Suggested fix:** Consider splitting hot.md into: (1) the ephemeral recent-context summary (what the concept page describes) and (2) a `wiki/meta/style-preferences.md` or updating MEMORY.md with the permanent style rules and repo locations.

### S-9. concepts/_index.md has a duplicate related entry

- **Affected page:** [[concepts/_index]]
- **Problem:** The frontmatter `related:` field lists `[[LLM Wiki Pattern]]` and `[[Hot Cache]]` twice each (lines 16-17 duplicate lines 20-21).
- **Suggested fix:** Remove the duplicate entries.

### S-10. Andrej Karpathy entity page: "claude-obsidian plugin" mention is not wikilinked

- **Affected page:** [[Andrej Karpathy]]
- **Problem:** The Connections section mentions "claude-obsidian plugin — this repo is a production implementation of his pattern" as plain text. No wikilink is possible since there is no entity page for the plugin itself, but this is a gap in the cross-reference graph.
- **Suggested fix:** Either create a minimal `entities/claude-obsidian-plugin.md` entity page, or add a wikilink to overview.md which describes the plugin.

### S-11. writing-style check: several pages use future tense or hedging language

- **Affected pages:** cherry-picks.md, CUR-8/project.md
- **Problem:** The wiki style convention (inferred from the LLM Wiki Pattern skill and declarative-present-tense guidance) calls for declarative present tense. cherry-picks.md uses future tense extensively ("should ship", "could be a separate plugin", "needs the adapter files"). CUR-8/project.md uses "(TBD)" throughout.
- **Suggested fix:** For cherry-picks, this is a planning document and future tense may be appropriate given the type:concept classification. Consider adding type: backlog or type: planning to distinguish from factual concept pages. For CUR-8, mark explicitly as status: seed and add a `> [!gap] Project details pending` callout.

### S-12. No cross-reference from VDR-Tuan-Chau/project.md to quang-ninh-planning-maps.md

- **Affected pages:** projects/VDR-Tuan-Chau/project.md, quang-ninh-planning-maps.md
- **Problem:** The project file does not link to the maps file. A reader looking at the project would not discover the planning maps page. The maps page does not link back to the project file either.
- **Suggested fix:** Add a "Related Files" or "Maps" section to VDR-Tuan-Chau/project.md linking the maps page. Add a back-link in the maps file.

### S-13. No page for the OpenClaw system architecture that MEMORY.md describes

- **Problem:** MEMORY.md describes a non-trivial architecture (gateway, Telegram channel, memory backend, subagent timeout, session config). This is operational configuration, not a wiki concept page. There is currently no separation between the live system state (MEMORY.md) and a stable architecture reference.
- **Suggested fix:** Consider creating `concepts/OpenClaw Architecture.md` as a stable reference, and keeping MEMORY.md as the live operational state that changes frequently.

### S-14. log.md references "sources/_index" as a related page but sources/_index.md is nearly empty

- **Problem:** The related field in log.md points to [[sources/_index]]. The sources index has only one heading ("Transcripts") with no entries and comment placeholders for Articles and Papers. The actual source (claude-obsidian-ecosystem-research) is not listed in sources/_index at all.
- **Suggested fix:** Add [[claude-obsidian-ecosystem-research]] to the Articles section of sources/_index.md. This was flagged in the prior report as a structural placeholder issue.

### S-15. "delta tracking", "URL ingestion", "auto-commit", "vision ingest" are mentioned across multiple pages but may now be shipped (v1.1) while cherry-picks.md still marks them as gaps

- **Affected pages:** [[cherry-picks]], [[claude-obsidian-ecosystem]], [[hot]]
- **Problem:** hot.md and the v1.4 release session note that delta tracking, URL ingestion, and auto-commit shipped in v1.1. The cherry-picks.md still frames all 13 items as a future backlog. The feature matrix in claude-obsidian-ecosystem.md still shows delta tracking (❌) and URL ingestion (❌) for claude-obsidian, which contradicts the v1.4 release session.
- **Suggested fix:** This is a stale claim. Update claude-obsidian-ecosystem.md to reflect v1.1 features shipped (delta tracking ✅, URL ingestion ✅, vision ingest ✅, auto-commit ✅, multi-depth query ✅). Add a `> [!stale]` callout noting the matrix was accurate at 2026-04-08 and reflects pre-v1.1 state. Update cherry-picks.md to mark Tier 1 and most of Tier 2 as "shipped in v1.1".

### S-16. cherry-picks.md has the wrong type classification

- **Affected page:** [[cherry-picks]]
- **Problem:** Frontmatter sets `type: concept`. This page is a product backlog / planning document, not a concept. The concept/entity/comparison taxonomy is meaningful and this misclassification causes it to appear in concept queries mixed with factual knowledge pages.
- **Suggested fix:** Change type to `backlog` or `planning`. Update index.md entry to reflect this.

### S-17. No inbound link to the lint-report-2026-04-16.md from any non-meta page

- **Affected page:** meta/lint-report-2026-04-16.md
- **Problem:** Same issue as W-7. The prior lint report has no inbound links. If lint reports are meant to be navigable artifacts, they need to be linked from index.md.
- **Suggested fix:** Add a "Lint History" subsection to index.md listing past lint reports in reverse chronological order.

---

## Appendix: Frontmatter Compliance Table

| Page | type | status | created | updated | tags | Result |
|------|------|--------|---------|---------|------|--------|
| index.md | meta | evergreen | 2026-04-07 | 2026-04-07 | yes | PASS (updated stale) |
| MEMORY.md | memory | evergreen | 2026-04-17 | 2026-04-19 | yes | PASS |
| hot.md | meta | evergreen | 2026-04-07 | 2026-04-08 | yes | PASS |
| getting-started.md | meta | evergreen | 2026-04-07 | 2026-04-07 | yes | PASS |
| overview.md | overview | developing | 2026-04-07 | 2026-04-07 | yes | WARN: sources field empty |
| log.md | meta | evergreen | 2026-04-07 | 2026-04-08 | yes | PASS |
| dashboard.md | meta | evergreen | 2026-04-07 | 2026-04-08 | yes | PASS |
| concepts/_index.md | meta | evergreen | 2026-04-07 | 2026-04-07 | yes | PASS (duplicate related) |
| entities/_index.md | meta | evergreen | 2026-04-07 | 2026-04-07 | yes | PASS (6 entities unlisted) |
| sources/_index.md | meta | evergreen | 2026-04-07 | 2026-04-07 | yes | PASS (source missing) |
| LLM Wiki Pattern.md | concept | mature | 2026-04-07 | 2026-04-07 | yes | PASS |
| Hot Cache.md | concept | mature | 2026-04-07 | 2026-04-07 | yes | PASS |
| Compounding Knowledge.md | concept | mature | 2026-04-07 | 2026-04-07 | yes | PASS |
| cherry-picks.md | concept | current | 2026-04-08 | 2026-04-08 | yes | WARN: wrong type |
| Andrej Karpathy.md | entity | mature | 2026-04-07 | 2026-04-07 | yes | PASS |
| Ar9av-obsidian-wiki.md | entity | current | 2026-04-08 | 2026-04-08 | yes | PASS |
| Nexus-claudesidian-mcp.md | entity | current | 2026-04-08 | 2026-04-08 | yes | PASS |
| ballred-obsidian-claude-pkm.md | entity | current | 2026-04-08 | 2026-04-08 | yes | PASS |
| rvk7895-llm-knowledge-bases.md | entity | current | 2026-04-08 | 2026-04-08 | yes | PASS |
| kepano-obsidian-skills.md | entity | current | 2026-04-08 | 2026-04-08 | yes | PASS |
| Claudian-YishenTu.md | entity | current | 2026-04-08 | 2026-04-08 | yes | PASS |
| Wiki vs RAG.md | comparison | mature | 2026-04-07 | 2026-04-07 | yes | PASS |
| claude-obsidian-ecosystem.md | comparison | current | 2026-04-08 | 2026-04-08 | yes | PASS (stale data — S-15) |
| How does the LLM Wiki pattern work.md | question | developing | 2026-04-07 | 2026-04-07 | yes | WARN: status should be mature |
| claude-obsidian-ecosystem-research.md | source | current | 2026-04-08 | 2026-04-08 | yes | PASS |
| claude-obsidian-v1.2.0-release-session.md | session | evergreen | 2026-04-07 | 2026-04-07 | yes | PASS |
| claude-obsidian-v1.4-release-session.md | session | evergreen | 2026-04-08 | 2026-04-08 | yes | PASS |
| full-audit-and-system-setup-session.md | session | evergreen | 2026-04-07 | 2026-04-07 | yes | PASS |
| lint-report-2026-04-16.md | meta | developing | 2026-04-16 | 2026-04-16 | yes | PASS |
| agents/Cody/agent.md | MISSING | MISSING | MISSING | MISSING | MISSING | CRITICAL |
| agents/Saul/agent.md | MISSING | MISSING | MISSING | MISSING | MISSING | CRITICAL |
| projects/CUR-8/project.md | MISSING | MISSING | MISSING | MISSING | MISSING | CRITICAL |
| projects/VDR-Tuan-Chau/project.md | MISSING | MISSING | MISSING | MISSING | MISSING | CRITICAL |
| projects/VDR-Tuan-Chau/maps/quang-ninh-planning-maps.md | MISSING | MISSING | MISSING | MISSING | MISSING | CRITICAL |
