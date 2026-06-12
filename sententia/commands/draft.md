---
description: "Sententia document pipeline: uses the swiss-legal-drafter agent to research and draft any Swiss legal document (lettera, diffida, parere, ricorso, contratto), then inserts the result into the studio letterhead template with numbered footnote citations, runs the sententia-doc-reviewer to verify all sources, and opens the final Word file."
---

Sei invocato tramite `/sententia:draft`. Esegui la pipeline di generazione documenti Sententia.

## Pipeline

### Fase 1 — Redazione legale

Usa l'agente `swiss-legal-drafter` per generare il contenuto del documento.

Istruzioni aggiuntive rispetto al comportamento standard del drafter:
- Le fonti (DTF/BGE, articoli di legge, commentari) devono essere formattate come **note a piè di pagina numerate** (¹ ² ³ …), non inline nel testo.
- Formato note: `¹ DTF 136 III 261, consid. 3.2, p. 265; art. 712a cpv. 1 CC.`
- Ogni dato mancante (indirizzo, importo, data, ecc.) deve essere lasciato come `[segnaposto]` visibile.
- Il titolo del documento è generato dinamicamente in base alla richiesta — non è fisso.
- Output: testo completo del documento (non un file — il template viene applicato nel passo successivo).

### Fase 2 — Inserimento nel template Word

Prendi il testo prodotto dal drafter e inseriscilo nel template di carta intestata.

1. Leggi il percorso del template da `template_path` nelle impostazioni del plugin.
   - Se non impostato, chiedi: *"Per generare il documento ho bisogno del percorso del tuo template Word. Puoi impostarlo nelle impostazioni del plugin ('Letterhead template path') oppure dirmi dove si trova."*
2. Usa lo skill `anthropic-skills:docx` per aprire il template e inserire:
   - Data nella posizione data
   - Titolo/Oggetto nella posizione oggetto
   - Corpo del documento
   - Note a piè di pagina come vere note Word
3. Salva il file nella cartella `output_folder` con nome descrittivo:
   - Formato: `[TipoDocumento]-[NomeDestinatario]-[YYYY-MM-DD].docx`
   - Esempio: `Diffida-Rossi-2026-06-12.docx`

### Fase 3 — Review indipendente

Lancia l'agente `sententia-doc-reviewer` passandogli il percorso del file generato.

L'agente verifica ogni citazione in modo indipendente e corregge eventuali errori.

### Fase 4 — Consegna

1. Apri il documento corretto in Word.
2. Mostra in chat il report di review.
3. Elenca i `[segnaposto]` da compilare.

## Output in chat

```
✅ DOCUMENTO GENERATO E VERIFICATO

File: [percorso]
Tipo: [tipo documento]

REVIEW: [APPROVATO / APPROVATO CON CORREZIONI / RICHIEDE REVISIONE MANUALE]
[report sintetico]

SEGNAPOSTO DA COMPILARE:
• [lista segnaposto]

Il documento è aperto in Word.
```

$ARGUMENTS
