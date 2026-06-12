# Security Policy

## Versioni supportate

Le fix di sicurezza sono applicate all'ultima release su `main`.

| Versione | Stato |
|---|---|
| 1.0.x | Supportata |

## Segnalare una vulnerabilità

Non aprire una issue pubblica su GitHub per una vulnerabilità sospetta.

Usa:
1. **GitHub Security Advisories** — [form di segnalazione privata](https://github.com/sententiaki/Sententia-plugin/security/advisories/new).
2. **Issues GitHub** con label `security` per problemi a bassa criticità.

Includi nella segnalazione:
- Il componente coinvolto (plugin manifest, privacy hook, un server MCP).
- La versione testata.
- Steps di riproduzione: prompt, tool call, input, transcript di rete.
- Impatto osservato: dati usciti dalla macchina, bypass di conferma, agente forzato a un tool non dichiarato.
- La tua valutazione di severità.

## SLA (best effort)

| Severità | Prima risposta | Target fix |
|---|---|---|
| Critica | 48h | 7 giorni |
| Alta | 5 giorni | 30 giorni |
| Media | 10 giorni | Prossima minor |
| Bassa | 15 giorni | In batch |

"Critica" significa: esfiltrazione di contenuto privilegiato (violazione dell'Anwaltsgeheimnis), remote code execution in un server MCP, o bypass di autenticazione.

## Scope

In scope:
- Plugin manifest, hook, agenti, comandi, skill in `sententia/`.
- Il server MCP locale Ollama bundled in `sententia/mcp-servers/ollama/`.

Out of scope:
- Claude Desktop — segnala ad [Anthropic](https://www.anthropic.com/security).
- Le Anthropic API — segnala ad [Anthropic](https://www.anthropic.com/security).
- I server MCP pubblici (`mcp.opencaselaw.ch`, `mcp.bettercallclaude.ch`): segnala ai rispettivi progetti upstream.
- Le fonti giuridiche pubbliche interrogate dal plugin (`entscheidsuche.ch`, `fedlex.admin.ch`, ecc.).

## Non-problemi noti

- **Il hook `pre-tool-use` usa regex, non ML.** È una scelta progettuale documentata. Il hook riduce la fuoriuscita accidentale; non è una garanzia assoluta.
- **Il seed data `data/bettercallclaude.db`** contiene riferimenti giuridici pubblici, nessun PII.
