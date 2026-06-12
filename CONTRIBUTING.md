# Contribuire a Sententia

Grazie per l'interesse. Leggi questo documento prima di aprire una PR significativa.

## Struttura del repository

```
sententia/           Il plugin Claude Desktop: agenti, comandi, skill, hook, .mcp.json
├── agents/          16 agenti (YAML frontmatter: name, description, model, tools)
├── commands/        15 comandi slash
├── skills/          12 skill (SKILL.md per directory)
├── hooks/           Hook Cowork Desktop (privacy)
├── scripts/         privacy-check.js e il suo file di test
└── mcp-servers/     Server MCP locale (ollama STDIO)

docs/                Documentazione tecnica e design
templates/           Template Word compatibili
```

I server MCP remoti (dati giuridici) sono ospitati da terze parti pubbliche:
- `mcp.opencaselaw.ch` — [OpenCaseLaw](https://opencaselaw.ch)
- `mcp.bettercallclaude.ch` — [BetterCallClaude](https://github.com/fedec65/BetterCallClaudeMCP)

Per modificare il comportamento dei server MCP, apri una PR nei rispettivi repository upstream.

## Prerequisiti

- Node.js 20 o 22.
- Per lavoro sul privacy hook: niente di extra — `privacy-check.js` usa solo la libreria standard Node.
- Per il server Ollama: un daemon Ollama locale.

## Branching

Tutti i cambiamenti vanno in branch off `main`:

- `fix/<nome>` — bug fix
- `feat/<nome>` — nuova funzionalità
- `docs/<nome>` — solo documentazione
- `chore/<nome>` — dipendenze, tooling

## Stile dei commit

```
feat(draft): add document generation agent with footnote citations

Implements the core /sententia:draft pipeline: research → write → footnotes.
Citations follow BGE/DTF format with Erwägung number and page (BCC standard).
```

- Prima riga ≤ 72 caratteri, `<tipo>(<scope>): verbo imperativo`.
- Il corpo spiega il perché, non solo il diff.

## Checklist PR

Prima di aprire una PR:

- [ ] `npm run package` funziona localmente.
- [ ] `node sententia/scripts/privacy-check.test.js` è verde se hai toccato il privacy hook.
- [ ] CI verde su GitHub.
- [ ] Nessun segreto, `.env`, o `settings.json` committato.

## Regole tecniche importanti

- **Gli agenti devono dichiarare `model:`** — usa `opus` per coordinamento, `haiku` per formattazione meccanica, `sonnet` per tutto il resto.
- **Gli agenti che lanciano sub-agenti devono listare `Task` come tool.**
- **Non usare `${user_config.*}` dentro i campi `url:` di `.mcp.json`** — Cowork Desktop rifiuta il templating URL durante la validazione upload. Usa `${user_config.*}` solo in `env:`, `args:`, e `headers:`.

## Test del privacy hook

```bash
cd sententia
node scripts/privacy-check.test.js
```

## Domande

Apri una discussione su GitHub o contatta il maintainer via Issues.
Per problemi di sicurezza vedi [`SECURITY.md`](./SECURITY.md).
