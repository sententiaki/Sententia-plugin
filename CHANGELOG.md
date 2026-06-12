# Changelog

## [1.0.0] - 2026-06-12

### Primo rilascio

- Fork di [BetterCallClaude](https://github.com/fedec65/bettercallclaude) v4.8.3 di Federico Cesconi.
- Rebranding completo: cartella `sententia/`, plugin.json, marketplace.json, README.
- Aggiunto campo `template_path` — percorso del template Word di carta intestata dello studio.
- Aggiunto campo `output_folder` — cartella di destinazione dei documenti generati.
- Lingua default impostata su `IT`, cantone default su `TI`.
- Rimosso campo `api_token` (non necessario per il servizio pubblico).
- Tutti i 9 server MCP originali mantenuti (swiss-caselaw, entscheidsuche, bge-search, fedlex-sparql, legal-citations, onlinekommentar, legal-persona, tas-jurisprudence, ollama).
- 20 agenti di ricerca BCC mantenuti integralmente.

### Da fare nella prossima versione

- Agente `/sententia:draft` — generazione documento su template con note a piè di pagina.
- Agente reviewer — controllo indipendente delle fonti citate.
- Comando `/sententia:help` aggiornato per Sententia.
- Template Word di esempio per carta intestata.

---

Il formato segue [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
