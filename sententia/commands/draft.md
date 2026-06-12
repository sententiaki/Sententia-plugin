---
description: "Sententia document pipeline: drafts any Swiss legal document (lettera, diffida, parere, ricorso, contratto) with footnote citations, runs an independent review loop on the text until approved, then inserts the final text into the studio Word template and presents the file."
---

Sei invocato tramite `/sententia:draft`. Esegui la pipeline Sententia.

## Regola fondamentale — nessuna domanda preliminare

**Non chiedere nulla prima di iniziare. Non presentare form. Inizia a redigere immediatamente.**

Tutti i dati mancanti vengono lasciati come `[segnaposto]` — l'avvocato li compila in Word dopo. Non usare `present_intake_form`. Non attivare `legal-intake` in modalità briefing.

---

## Pipeline

### Fase 1 — Drafter: testo pronto per Word

Usa l'agente `swiss-legal-drafter` per produrre il testo completo del documento.

Il testo prodotto deve essere già nel formato finale da inserire in Word:
- Titolo generato dinamicamente in base alla richiesta
- Corpo completo con tutti i paragrafi
- **Note a piè di pagina numerate** (¹ ² ³ …) — non citazioni inline
- Formato note: `¹ DTF 136 III 261, consid. 3.2, p. 265; art. 102 cpv. 1 CO.`
- `[segnaposto]` per ogni dato mancante (indirizzo, nome completo, importo, data, ecc.)
- Data del giorno in formato `Lugano, GG mese AAAA`

Output: **testo puro** (non un file Word — quello viene creato solo dopo l'approvazione del review).

---

### Fase 2 — Reviewer: valutazione del testo

Passa il testo all'agente `sententia-doc-reviewer` per la valutazione.

Il reviewer lavora **sul testo**, non su un file Word. Valuta:
- Correttezza di ogni citazione DTF/BGE (numero, considerando, pagina, pertinenza)
- Correttezza degli articoli di legge citati
- Lacune nelle basi legali
- Eventuali consigli migliorativi

Il reviewer produce una delle tre risposte:
- **OK** — il testo è approvato, nessuna correzione necessaria
- **CORREZIONI** — lista precisa di cosa correggere, con le versioni corrette già pronte
- **REVISIONE MANUALE** — problema che richiede valutazione dell'avvocato

---

### Fase 3 — Loop di correzione (se necessario)

Se il reviewer risponde **CORREZIONI**:
1. Passa le correzioni al drafter
2. Il drafter aggiorna il testo applicando le correzioni indicate
3. Torna alla Fase 2 — il reviewer rivaluta il testo aggiornato
4. Ripeti finché il reviewer risponde **OK** o **REVISIONE MANUALE**

Massimo 3 iterazioni. Se dopo 3 cicli ci sono ancora problemi, procedi comunque segnalando le correzioni non risolte all'avvocato.

---

### Fase 4 — Inserimento nel template Word (solo dopo OK del reviewer)

Solo quando il reviewer ha approvato il testo, crea il file Word **senza fare domande**:

1. Leggi `template_path` dalle impostazioni del plugin.
   - Se impostato: apri il template con `mcp__Word__By_Anthropic___open_document`.
   - Se non impostato: crea un documento nuovo con `mcp__Word__By_Anthropic___create_document`. **Non chiedere nulla, procedi direttamente.**
2. Inserisci il testo nel documento usando `mcp__Word__By_Anthropic___insert_text` o `mcp__Word__By_Anthropic___replace_text`:
   - Data
   - Titolo/Oggetto
   - Corpo del documento con note a piè di pagina
3. Leggi `output_folder` dalle impostazioni. Se non impostato, salva sul Desktop: `~/Desktop/`.
4. Salva con `mcp__Word__By_Anthropic___save_document` con nome: `[TipoDocumento]-[NomeDestinatario]-[YYYY-MM-DD].docx`

---

### Fase 5 — Presentazione

1. Apri il file in Word.
2. Mostra in chat:

```
✅ DOCUMENTO PRONTO

File: [percorso]
Review: [APPROVATO / APPROVATO CON CORREZIONI / nota correzioni non risolte]

SEGNAPOSTO DA COMPILARE:
• [lista segnaposto rimasti]

Il documento è aperto in Word.
```

$ARGUMENTS
