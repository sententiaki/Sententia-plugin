---
description: "Sententia document pipeline: generates any Swiss legal document (lettera, diffida, parere, ricorso, contratto, atto) on the studio letterhead template with footnote citations, then runs an independent review agent to verify all legal sources. Final Word document is saved and opened automatically."
---

Sei invocato tramite `/sententia:draft`. Esegui la pipeline di generazione documenti Sententia in tre fasi sequenziali.

## Pipeline

### Fase 1 — Generazione (agente: sententia-doc-generator)

Lancia l'agente `sententia-doc-generator` con la richiesta dell'utente.

L'agente:
- Identifica il tipo di documento e i dati disponibili
- Ricerca le basi legali e la giurisprudenza rilevante tramite i server MCP
- Redige il documento completo con note a piè di pagina numerate
- Lascia `[segnaposto]` per i dati mancanti
- Inserisce il contenuto nel template di carta intestata configurato

Attendi che l'agente completi il documento prima di procedere.

### Fase 2 — Review indipendente (agente: sententia-doc-reviewer)

Lancia l'agente `sententia-doc-reviewer` passandogli il percorso del documento generato.

L'agente:
- Verifica ogni citazione DTF/BGE in modo indipendente (considerando + pagina + pertinenza)
- Controlla ogni articolo di legge
- Identifica lacune nelle basi legali
- Applica le correzioni direttamente al file
- Produce un report di review strutturato

Attendi il completamento della review.

### Fase 3 — Consegna

1. Apri il documento corretto in Word (usando `mcp__Word__By_Anthropic___open_document` o `Bash open`).
2. Mostra in chat il **report di review** completo dell'agente reviewer.
3. Elenca i `[segnaposto]` rimasti da compilare manualmente.
4. Mostra il percorso del file salvato.

## Formato output in chat

```
✅ DOCUMENTO GENERATO E VERIFICATO

File: [percorso completo]
Tipo: [tipo documento]
Destinatario: [nome o segnaposto]

REVIEW: [stato — APPROVATO / APPROVATO CON CORREZIONI / RICHIEDE REVISIONE MANUALE]
[report review sintetico]

SEGNAPOSTO DA COMPILARE:
• [elenco segnaposto rimasti]

Il documento è aperto in Word.
```

## Scope del plugin

Usa esclusivamente gli agenti, le skill e i server MCP di Sententia per tutto il lavoro legale. Non delegare a skill o agenti esterni. Le operazioni su file (.docx, apertura Word) sono esenti.

## Configurazione richiesta

Se `template_path` non è impostato nelle impostazioni del plugin, chiedi all'utente il percorso del template prima di procedere:

> "Per generare il documento ho bisogno del percorso del tuo template Word di carta intestata. Puoi trovarlo in Finder e trascinarlo qui, oppure andare nelle impostazioni del plugin e impostare il campo 'Letterhead template path'."

$ARGUMENTS
