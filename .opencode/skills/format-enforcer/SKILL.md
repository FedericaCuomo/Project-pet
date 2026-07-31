---
name: format-enforcer
description: Verifica che agenti e skill rispettino il formato Markdown OpenCode.
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: ai-assistant
---

## What I do

- Controllo frontmatter, campi obbligatori e struttura del corpo.
- Verifico che i prompt descrivano comportamento e che le skill descrivano operatività.
- Evidenzio errori di formato, campi mancanti e confusione tra agent e skill.

## When to use me

- Quando devi validare o correggere file agent/skill.
- Quando sospetti che una configurazione non rispetti lo standard OpenCode.

## Workflow

1. Verifica frontmatter YAML.
2. Verifica sezioni obbligatorie del corpo.
3. Elenca errori e correzioni minime.

## Output

- Errori trovati
- Correzioni suggerite
- Patch sintetica
