---
name: common-prompt-skill-optimizer
description: Ottimizza prompt e skill in `common/` rendendoli più essenziali e concisi senza cambiare la logica.
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: ai-assistant
---

## What I do

- Ricevo una lista di file in `common/` da ottimizzare (prompt/skill OpenCode).
- Riduco ridondanze e ambiguità mantenendo il significato: meno caratteri, stessa intenzione e vincoli.
- Verifico che la separazione tra **Prompt** (ruolo/obiettivi/formato output) e **Skill** (operatività/workflow/controlli) rimanga coerente.

## When to use me

- Quando devi rifinire contenuti in `common/` (testo e struttura) senza cambiare la logica.
- Quando, dopo un confronto progetto→common, la logica è equivalente ma il contenuto deve essere reso più conciso.

## Workflow

1. **Input check**
   - Richiedi `targetPaths` se mancante.
   - Verifica che ogni path sia dentro `common/`.

2. **Per-file analisi**
   - Identifica se il file è un **prompt (agent)** o una **skill** (in base a struttura/heading).
   - Rileva ripetizioni, formulazioni ridondanti, parti non informative e boilerplate eccessivo.
   - Controlla coerenza con la separazione Prompt/Skill.

3. **Riscrittura vincolata**
   - Accorcia: elimina sinonimi ripetuti e frasi di contorno.
   - Mantieni vincoli, formato output atteso e intenzione.
   - Se trovi logica operativa inserita nel prompt che dovrebbe stare in una skill, **non** spostare automaticamente: registra una domanda di split.

4. **Decisioni su ambiguità**
   - Se non riesci a garantire che il significato non cambi, non proporre la patch per quel file e aggiungi una domanda.

5. **Patch plan**
   - Produce una proposta per file con motivazione e lista di modifiche (Added/Edited/Deleted se utile).

## Guardrails

- Non cambiare la logica, i vincoli e l’intento.
- Non degradare il formato OpenCode (frontmatter e sezioni).
- Se non sei certo: proponi domande e lascia invariato il file.

## Output

- `filesToOptimize`: elenco file.
- `openQuestions`: domande/decisioni necessarie.
- `patch plan` (solo proposte): elenco per file con:
  - `path`
  - `summary` delle modifiche
  - `reason`
