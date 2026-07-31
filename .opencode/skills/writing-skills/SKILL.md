---
name: writing-skills
description: Generatore di skeleton per nuove skill (SKILL.md) conforme OpenCode. Fornisce una guida standard per creare lo skeleton di una skill, ispirata alle best practice di OpenCode.
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: ai-assistant
---

## Posizione dei file
OpenCode cerca SKILL.md nelle seguenti posizioni:
- .opencode/skills/<name>/SKILL.md

## Frontmatter
Ogni SKILL.md deve iniziare con frontmatter YAML. I campi riconosciuti sono:
- name (obbligatorio)
- description (obbligatorio)
- license (opzionale)
- compatibility (opzionale)
- metadata (opzionale, mappa)
I campi non riconosciuti vengono ignorati.

## Validazione nomi
name deve:
- essere lungo 1-64 caratteri
- essere alfanumerico minuscolo con separatori '-' singoli
- non iniziare o finire con '-'
- non contenere '--'
- corrispondere al nome della directory contenente SKILL.md

Regex equivalente:
```
^[a-z0-9]+(-[a-z0-9]+)*$
```

## Regole di lunghezza
description deve essere lunga 1-1024 caratteri.

## What I do
- Genero uno skeleton per una nuova skill (SKILL.md) basato su input: name (nome della skill), type (SKILL|PLAN|BUILD, opzionale, default SKILL), target_path (percorso di output, default: .opencode/skills).
- Genero la struttura di base per la nuova skill nel percorso di output: <target_path>/<name>/, in conformità con le linee guida OpenCode.
- Verifico che i skeleton generati rispettino i vincoli OpenCode (front matter, sezioni, formato).

## When to use me
- Usa quando devi generare rapidamente lo skeleton di una nuova skill senza scrivere manualmente la strutturazione.
- Usa quando vuoi avere una guida standardizzata per iniziare una nuova skill.

## Workflow

1. Input check
   - Controllo che name sia fornito; default per type = SKILL; default target_path = .opencode/skills
2. Skeleton generation
   - Crea directory <target_path>/<name>/ e genera SKILL.md nel percorso di output (con frontmatter coerente)
3. Conformità e patch plan
   - Verifica con format-enforcer; se necessario, genera patch plan per le modifiche

## Guardrails
- Non cambiare la logica di OpenCode; generare solo skeleton strutturali.
- Mantenere front matter e sezioni in formato Markdown OpenCode valido.
- Se incontra ambiguità, sollevare domande e non applicare patch.

## Output
- File generati nel path di output: <target_path>/<name>/ con SKILL.md
- Output di controllo: path verificati, file creati, eventuali domande per chiarimenti

## Esempio
Esempio di configurazione per scrivere uno skeleton:
```
---
name: example-skill
description: Esempio di skeleton per una nuova skill
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: github
---
```
