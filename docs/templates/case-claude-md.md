<!--
  BetterCallClaude — Case CLAUDE.md Template
  ============================================
  Copy this file to your case directory as CLAUDE.md, then fill in the
  [REPLACE: ...] placeholders. Claude reads it automatically on startup.
  Tutorial: docs/tutorials/employment-case-walkthrough.md
-->

# [REPLACE: Matter Title — e.g., Keller v. TechCorp AG, Wrongful Termination]

## Case Profile

| Field | Value |
|-------|-------|
| Internal reference | [REPLACE: Firm file number] |
| Jurisdiction | [REPLACE: Federal / Cantonal / Multi-jurisdictional] |
| Canton | [REPLACE: Two-letter code (ZH, BE, GE, …) or "Federal"] |
| Primary domains | [REPLACE: One or more — litigation, corporate, fiscal, compliance, data-protection, real-estate, procedure, drafting, research, cantonal] |
| Language | [REPLACE: DE / FR / IT / EN] |
| Streitwert / Value in dispute | [REPLACE: CHF amount or "non-monetary"] |
| Procedural posture | [REPLACE: Pre-litigation / Pending / Appeal / Advisory] |

### Parties

| Role | Name / Description |
|------|--------------------|
| Client | [REPLACE: Client name and role — Kläger/Beklagter / demandeur/défendeur / attore/convenuto] |
| Opposing party | [REPLACE: Opposing party and role] |
| Other parties | [REPLACE: Third parties, intervenors, or "none"] |

Always use the jurisdiction and language specified above when producing any output for this matter.

---

## Privacy and Confidentiality

| Setting | Value |
|---------|-------|
| Privacy mode | [REPLACE: strict / balanced / cloud] |
| Privilege detection | [REPLACE: enabled / disabled] |

<!--
  Privacy modes (from BetterCallClaude privacy-routing skill):
  - strict:   All content treated as CONFIDENTIAL minimum. Local processing only.
  - balanced: Auto-detect privacy level via pattern matching (default).
  - cloud:    Cloud processing for PUBLIC and CONFIDENTIAL; local only for PRIVILEGED.
-->

This matter is subject to Anwaltsgeheimnis (Art. 321 StGB). Never include client names or identifying details in queries sent to external APIs. Anonymize all case facts before any external processing.

---

## Key Dates and Deadlines

| Date | Event | Status |
|------|-------|--------|
| [REPLACE: YYYY-MM-DD] | Mandate start | Active |
| [REPLACE: YYYY-MM-DD] | Key incident (e.g., termination, breach) | — |
| [REPLACE: YYYY-MM-DD] | Filing deadline (Klagefrist) | Pending |
| [REPLACE: YYYY-MM-DD] | Limitation period (Verjaehrung) | Pending |
| [REPLACE: YYYY-MM-DD] | Court hearing | Scheduled |

Flag any deadline within 30 days. Always check limitation periods when discussing the case timeline.

---

## Legal Issues and Statutory Framework

### Key Questions (Fragestellungen)

1. [REPLACE: Primary legal question]
2. [REPLACE: Secondary legal question]
3. [REPLACE: Additional question or delete this line]

### Applicable Statutes

| Provision | Description |
|-----------|-------------|
| [REPLACE: e.g., Art. 335c OR] | [REPLACE: Short description — e.g., Notice periods for employment contracts] |
| [REPLACE: e.g., Art. 336 OR] | [REPLACE: Short description] |
| [REPLACE: e.g., Art. 336a OR] | [REPLACE: Short description] |

### Known Precedents

| Citation | Relevance |
|----------|-----------|
| [REPLACE: e.g., BGE 136 III 513] | [REPLACE: Short note — e.g., Leading case on wrongful termination criteria] |
| [REPLACE: Citation or delete row] | [REPLACE: Short note] |

Start research from these statutes and precedents. Search beyond them but treat them as the baseline. Verify all citations via the legal-citations MCP server.

---

## Workflow Preferences

| Setting | Value |
|---------|-------|
| Briefing depth | [REPLACE: quick / standard / deep] |
| Summary length | [REPLACE: short / medium / long] |
| Auto-briefing threshold | [REPLACE: Complexity score 1-10 — default 7] |
| Checkpoint behavior | [REPLACE: pause-at-each / pause-at-major / no-pause] |
| Default workflow template | [REPLACE: full-litigation / due-diligence / contract-lifecycle / regulatory-assessment / none] |

### Quality Requirements

- Verify all citations before inclusion in any deliverable.
- Use formal legal register (Gutachtenstil: Obersatz, Untersatz, Schluss).
- Distinguish mandatory law (zwingendes Recht) from dispositive provisions.
- Include the professional disclaimer on every substantive output.
- Express risks as probabilities and CHF amounts where possible.

---

## Deliverables

Check the items this matter requires. When the user gives broad instructions like "prepare the case", consult this checklist and propose a workflow that produces the checked items.

- [ ] Research memo (Rechtsgutachten)
- [ ] Strategy assessment with risk matrix
- [ ] Adversarial analysis (advocate / adversary / judicial)
- [ ] Court submission (Klageschrift / Klageantwort / Berufung)
- [ ] Contract draft or review
- [ ] Settlement calculation (Vergleichsberechnung)
- [ ] Compliance assessment
- [ ] Translation (specify target language)

## Professional Disclaimer

All outputs produced for this matter require review and validation by a qualified Swiss lawyer before use. They do not constitute legal advice. The lawyer retains full professional responsibility for all work products.

## Briefing State

<!-- Auto-populated by /bettercallclaude:briefing sessions. Do not edit manually. -->
When resuming in a new conversation, check this section first. If a briefing ID is present, load the corresponding state before beginning new analysis.
