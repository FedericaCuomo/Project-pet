---
name: prompt-optimizer
description: Ottimizza AGENTS.md, prompt e skill riducendo ridondanze e ambiguità.
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: ai-assistant
---

## What I do

- Comprimo prompt e skill senza alterarne il significato.
- Riduco duplicazioni tra `AGENTS.md`, prompt e skill.
- Ripristino una separazione netta tra regole globali, comportamento agente e workflow operativi.
- Quando nel contenuto compaiono sezioni di test (o esempi di test/output), le riscrivo in forma più breve e concisa mantenendo copertura e intenzione.

## When to use me

- Quando devi rifattorizzare configurazioni verbose o incoerenti.
- Quando vuoi spostare una regola nella sua fonte autorevole.

## Workflow

1. Verifica che il perimetro sia quello supportato dall’agente: aggiorno **solo** `AGENTS.md` (root), `opencode.json` (root) e i file in **`.opencode/agents/`** e **`.opencode/skills/`**.
2. Mappa regole e duplicazioni tra `AGENTS.md`, prompt degli agenti e contenuti delle skill nello stesso perimetro.
3. Scegli per ogni regola una sola fonte autorevole.
4. Riscrivi in forma più corta, chiara e mantenibile senza cambiare significato.
5. Verifica che nulla di operativo resti nei prompt se deve vivere in una skill.
6. Se stai toccando file in `.opencode/agents/`, normalizza anche il **frontmatter** secondo lo standard del repo (vedi Guardrails).

## Guardrails

- Non eliminare vincoli distinti solo per accorciare il testo.
- Non cambiare il significato delle regole.
- Segnala quando `AGENTS.md` contiene workflow troppo specifici.

### Standard agent frontmatter (repo)

Quando modifichi/ottimizzi un agente in `.opencode/agents/*.md`, il frontmatter deve restare minimale:

```yaml
---
description: "..."
mode: primary|subagent|all
temperature: <valore>
---
```

- **Non impostare `model` di default** (inseriscilo solo su richiesta esplicita).
- `temperature` va ponderata sullo scopo:
  - `0.1` analisi / code review / QA / auditing
  - `0.2` pianificazione / decisioni / strutturazione
  - `0.3-0.4` task generali di sviluppo
  - `0.6-0.8` brainstorming / esplorazione creativa

## Output

- Problemi individuati
- Migliorie proposte
- Patch sintetica (`Added` / `Edited` / `Deleted`)

- *(Includi anche: perimetro confermato e breve motivazione delle riscritture)*
