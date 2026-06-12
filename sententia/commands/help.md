---
description: "Mostra la guida completa ai comandi Sententia, gli agenti disponibili, le skill e esempi di utilizzo"
---

# Guida Sententia

Visualizza la guida completa al plugin Sententia. Mostra il seguente contenuto formattato esattamente come indicato.

---

## Come funziona

Sententia fornisce due capacità principali:

1. **Generazione documenti** — scrivi il documento che ti serve, Sententia lo redige sul tuo template con fonti citate in nota, un secondo agente controlla le fonti, il file Word viene aperto automaticamente.
2. **Ricerca e analisi legale** — tutti gli strumenti di BetterCallClaude per la ricerca giuridica svizzera (precedenti BGE/DTF, Fedlex, commentari, strategia, analisi avversariale).

---

## Comandi ($TOTAL)

### Generazione documenti (Sententia)

| Comando | Descrizione |
|---------|-------------|
| `/sententia:draft` | **Genera qualsiasi documento legale sul template dello studio** — lettera, diffida, parere, ricorso, contratto, atto. Ricerca le fonti, inserisce note a piè di pagina, review indipendente, Word aperto. |

### Ricerca e analisi legale

| Comando | Descrizione |
|---------|-------------|
| `/sententia:legal` | Gateway intelligente — analizza la richiesta e coordina agenti e workflow |
| `/sententia:research` | Ricerca precedenti BGE/ATF/DTF, analisi statuti, verifica citazioni |
| `/sententia:strategy` | Strategia processuale, valutazione rischi, analisi transattiva |
| `/sententia:adversarial` | Analisi avversariale a tre agenti: avvocato, controparte, giudice |
| `/sententia:precedent` | Ricerca e analisi catene di precedenti BGE |
| `/sententia:legal-5step` | Pipeline completa in 5 fasi: intake → ricerca → strategia → avversariale → redazione |
| `/sententia:briefing` | Briefing strutturato con panel di specialisti |

### Analisi documenti

| Comando | Descrizione |
|---------|-------------|
| `/sententia:doc-analyze` | Analizza documenti legali: clausole, citazioni, conformità |
| `/sententia:validate` | Valida citazioni legali svizzere in batch |
| `/sententia:cite` | Formatta e verifica singole citazioni svizzere |

### Strumenti

| Comando | Descrizione |
|---------|-------------|
| `/sententia:translate` | Traduce testi legali tra DE, FR, IT, EN |
| `/sententia:summarize` | Sintetizza output di pipeline multi-agente |
| `/sententia:refine` | Affina query vaghe in prompt legali precisi |
| `/sententia:cantonal` | Ricerca diritto cantonale (26 cantoni) |
| `/sententia:federal` | Modalità diritto federale |

### Sistema

| Comando | Descrizione |
|---------|-------------|
| `/sententia:privacy` | Visualizza o modifica la modalità privacy (strict/balanced/cloud) |
| `/sententia:version` | Versione del plugin e stato server |
| `/sententia:help` | Questa guida |

---

## Agenti (21)

### Agenti Sententia (nuovi)

| Agente | Funzione |
|--------|----------|
| `doc-reviewer` | Review indipendente del documento generato — delega la verifica citazioni a `citation`, applica le correzioni al file Word, produce il report per l'avvocato |

### Agenti di ricerca e analisi (da BetterCallClaude)

| Agente | Dominio |
|--------|---------|
| `researcher` | Ricerca giuridica svizzera, BGE/ATF/DTF, analisi statuti |
| `strategist` | Strategia processuale, valutazione rischi |
| `drafter` | Redazione documenti legali in formato svizzero |
| `citation` | Verifica e formattazione citazioni BGE |
| `advocate` | Costruisce la tesi più forte a favore (modalità avversariale) |
| `adversary` | Sfida e stress-testa la tesi (modalità avversariale) |
| `judicial` | Sintesi neutrale di avvocato e controparte |
| `procedure` | Termini ZPO/StPO, regole procedurali, forum |
| `fiscal` | Diritto fiscale, CDI, transfer pricing |
| `corporate` | Governance AG/GmbH, M&A, contratti commerciali |
| `realestate` | Diritto immobiliare, Grundbuch, Lex Koller |
| `compliance` | FINMA, GwG/LBA, conformità normativa |
| `data-protection` | nDSG/FADP, GDPR, privacy |
| `cantonal` | Tutti i 26 sistemi giuridici cantonali |
| `translator` | Traduzione terminologia legale DE/FR/IT/EN |
| `risk` | Probabilità esito, quantificazione danni |
| `summarizer` | Consolidamento output pipeline |
| `briefing` | Intake strutturato, panel specialisti |
| `orchestrator` | Coordinamento pipeline multi-agente |
| `prompt-engineer` | Affinamento query legali |

---

## Skill (12)

Le skill si attivano automaticamente quando il contesto è rilevante.

| Skill | Si attiva quando |
|-------|-----------------|
| `swiss-legal-research` | Query di ricerca giuridica, riferimenti BGE/DTF |
| `swiss-legal-drafting` | Redazione documenti, contratti |
| `swiss-legal-strategy` | Pianificazione processuale, valutazione rischi |
| `swiss-citation-formats` | Formattazione citazioni BGE/ATF/DTF |
| `swiss-document-analysis` | Analisi documenti, clausole, conformità |
| `swiss-legal-translation` | Traduzione testi legali |
| `adversarial-analysis` | Analisi avversariale a tre agenti |
| `legal-intake` | Query vaghe o complesse — raffinamento socratico |
| `data-protection-law` | DSG/FADP, GDPR, privacy |
| `compliance-frameworks` | FINMA, GwG, conformità finanziaria |
| `privacy-routing` | Rilevamento segreto professionale (Anwaltsgeheimnis) |
| `legal-5step-framework` | Pipeline legale in 5 fasi con checkpoint |

---

## Server MCP (9)

| Server | Dati | Trasporto |
|--------|------|-----------|
| `swiss-caselaw` | 974.000+ decisioni, 8M citazioni (opencaselaw.ch) | SSE |
| `entscheidsuche` | Ricerca full-text sentenze svizzere | HTTP |
| `bge-search` | Ricerca e validazione BGE/ATF/DTF | HTTP |
| `legal-citations` | Verifica e formattazione citazioni | HTTP |
| `fedlex-sparql` | Legislazione federale svizzera (Fedlex) | HTTP |
| `onlinekommentar` | Commentari dottrinali svizzeri | HTTP |
| `legal-persona` | Strategia, drafting, analisi documenti | HTTP |
| `tas-jurisprudence` | Arbitrato sportivo CAS/TAS | HTTP |
| `ollama` | Classificazione privacy locale | Local |

---

## Esempi

### Genera un documento
```
/sententia:draft diffida di pagamento per Mario Rossi, CHF 8.500, scadenza 30 giorni
```
```
/sententia:draft parere sulla validità di una clausola di non concorrenza
```
```
/sententia:draft ricorso al Tribunale d'appello TI contro diniego permesso di costruzione
```

### Ricerca giuridica
```
/sententia:research art. 97 CO responsabilità contrattuale precedenti DTF
```
```
/sententia:research sentenze proprietà per piani taglio piante spazi comuni Ticino
```

### Analisi strategica
```
/sententia:strategy controversia locatizia CHF 50.000, Pretura Lugano
```

### Analisi avversariale
```
/sententia:adversarial il locatario sostiene violazione art. 259a CO
```

---

## Configurazione template

Per usare `/sententia:draft` imposta nelle impostazioni del plugin:
- **Letterhead template path** — percorso del tuo file `.docx` di carta intestata
- **Output folder path** — cartella dove salvare i documenti generati
- **Default canton** — es. `TI`
- **Output language** — `IT`

---

**Sententia v1.0.0 — Plugin di generazione documenti legali svizzeri per Claude Desktop**

Se l'utente ha fatto una domanda, rispondile nel contesto di questa guida.

## Query utente

$ARGUMENTS
