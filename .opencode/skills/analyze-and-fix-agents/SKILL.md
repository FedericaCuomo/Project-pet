---
name: analyze-and-fix-agents
description: Analizza incoerenze tra documentazione (AGENTS.md, prompt, skill) e propone correzioni mirate.
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: ai-assistant
---

## What I do

- Individuo incoerenze tra regole dichiarate e contenuti effettivi in `AGENTS.md`, prompt e skill.
- Traccio l’origine delle regole in `AGENTS.md`, prompt o skill.
- Spiego se il problema dipende da ambiguità, conflitti, duplicazioni, assenze o separazione prompt/skill non corretta.
- Preparo una patch minima sui file di documentazione (es. `AGENTS.md` o i markdown di agenti/skill) quando serve.

In particolare, per i file agente in `.opencode/agents/` controllo anche coerenza di **frontmatter** (campi ammessi e `temperature` coerente con lo scopo).

## When to use me

- Quando trovi incoerenze tra le regole e la loro espressione in prompt/skill.
- Quando una regola sembra duplicata, in conflitto o mancante.
- Quando serve correggere/ottimizzare il testo di prompt e skill per ripristinare la separazione tra ruolo (prompt) e operatività (skill).

## Workflow

1. Raccogli le fonti rilevanti (AGENTS.md, prompt e skill) e i relativi estratti.
2. Identifica regola/i coinvolta/e, file e sezione.
3. Determina la causa probabile (ambiguità, conflitto, duplicazione, assenza, separazione scorretta).
4. Proponi la correzione minima necessaria, mantenendo significato e vincoli.

### Standard agent frontmatter (repo)

Se l’incoerenza riguarda un agente, verifica anche:

- frontmatter minimale: `description`, `mode`, `temperature` (più eventuale `permission` se già usato nel repo)
- **niente `model` di default** (solo su richiesta)
- euristica `temperature`:
  - `0.1` analisi / code review / QA / auditing
  - `0.2` pianificazione / decisioni / strutturazione
  - `0.3-0.4` task generali di sviluppo
  - `0.6-0.8` brainstorming / esplorazione creativa

## Output

- Regola coinvolta
- Fonte e posizione
- Estratti rilevanti
- Causa probabile
- Soluzione proposta
- Patch sintetica (`Added` / `Edited` / `Deleted`) se necessaria
