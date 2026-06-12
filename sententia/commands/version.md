---
description: "Mostra la versione di Sententia, i componenti installati e lo stato dei server MCP"
---

# Sententia — Versione e Stato

Quando questo comando viene invocato, mostra il report di stato qui sotto. Verifica la disponibilità dei server MCP tentando di usare i loro tool. Aggiorna gli indicatori di stato di conseguenza.

## Report di stato

Mostra il seguente blocco formattato:

```
═══════════════════════════════════════════════════
  SENTENTIA — Plugin di generazione documenti legali
═══════════════════════════════════════════════════
  Versione:   1.0.0
  Formato:    Claude Code Plugin (Cowork Desktop)
  Repository: github.com/sententiaki/Sententia-plugin
  Licenza:    AGPL-3.0
═══════════════════════════════════════════════════

  COMANDI
  -------
  [x] draft          - Genera documento su template (pipeline Sententia)
  [x] legal          - Gateway intelligente
  [x] research       - Ricerca BGE/ATF/DTF
  [x] strategy       - Strategia processuale
  [x] adversarial    - Analisi avversariale
  [x] legal-5step    - Pipeline 5 fasi
  [x] briefing       - Briefing strutturato
  [x] doc-analyze    - Analisi documenti
  [x] validate       - Validazione citazioni
  [x] cite           - Formattazione citazioni
  [x] translate      - Traduzione legale DE/FR/IT/EN
  [x] summarize      - Sintesi output
  [x] refine         - Affinamento query
  [x] cantonal       - Diritto cantonale
  [x] federal        - Diritto federale
  [x] precedent      - Catene di precedenti
  [x] privacy        - Modalità privacy
  [x] version        - Questo report
  [x] help           - Guida comandi

  AGENTI (21)
  -----------
  Sententia:
  [x] doc-reviewer      - Review indipendente documenti generati

  Da BetterCallClaude:
  [x] researcher      [x] strategist     [x] drafter
  [x] citation        [x] compliance     [x] data-protection
  [x] risk            [x] procedure      [x] translator
  [x] fiscal          [x] corporate      [x] cantonal
  [x] realestate      [x] advocate       [x] adversary
  [x] judicial        [x] briefing       [x] orchestrator
  [x] summarizer      [x] prompt-engineer

  SKILL (12)
  ----------
  [x] swiss-legal-research     [x] swiss-legal-drafting
  [x] swiss-legal-strategy     [x] swiss-citation-formats
  [x] swiss-document-analysis  [x] privacy-routing
  [x] swiss-legal-translation  [x] adversarial-analysis
  [x] compliance-frameworks    [x] data-protection-law
  [x] legal-intake             [x] legal-5step-framework

  SERVER MCP (9)
  --------------
  [ ] swiss-caselaw     - 974K+ decisioni, 8M citazioni  (SSE)
  [ ] entscheidsuche    - Ricerca sentenze svizzere       (HTTP)
  [ ] bge-search        - Ricerca BGE/ATF/DTF             (HTTP)
  [ ] legal-citations   - Verifica citazioni              (HTTP)
  [ ] fedlex-sparql     - Legislazione federale           (HTTP)
  [ ] onlinekommentar   - Commentari dottrinali           (HTTP)
  [ ] legal-persona     - Strategia e drafting            (HTTP)
  [ ] tas-jurisprudence - Arbitrato CAS/TAS               (HTTP)
  [ ] ollama            - Privacy locale                  (Local)

  Esegui /sententia:privacy per la modalità privacy attiva.

  LINGUE
  ------
  [x] Italiano (IT)   - CO, CC, CP, DTF
  [x] Tedesco (DE)    - OR, ZGB, StGB, BGE
  [x] Francese (FR)   - CO, CC, CP, ATF
  [x] Inglese (EN)    - Terminologia svizzera

  GIURISDIZIONI
  -------------
  [x] Diritto federale
  [x] Tutti i 26 cantoni svizzeri
  [x] Cantone di default: TI

═══════════════════════════════════════════════════
  github.com/sententiaki/Sententia-plugin
═══════════════════════════════════════════════════
```

Per ogni server MCP, verifica la disponibilità:
- Se i tool rispondono, segna `[x]` (attivo)
- Se non disponibili, segna `[ ]` (non raggiungibile)

## Query utente

$ARGUMENTS
