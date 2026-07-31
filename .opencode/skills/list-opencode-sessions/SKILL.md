---
name: list-opencode-sessions
description: Mostra l’elenco delle sessioni Opencode locali attive e consente la selezione di una sessione.
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: ai-assistant
---

## What I do

- Esegue `opencode session list`.
- Presenta una checklist con `sessionID`, titolo/descrizione e timestamp.
- Chiede all’utente di selezionare **una sola** sessione (rispondendo con la `sessionID`).

## When to use me

- Quando devi recuperare evidenza da una sessione Opencode diversa dalla chat corrente.

## Workflow

### 1) Enumerazione sessioni

1. Esegui `opencode session list`.
2. Presenta all’utente una checklist del tipo:
   - `[ ] <sessionID> — <Title/descrizione> (Updated: <timestamp>)`

### 2) Selezione

1. Chiedi all’utente di selezionare **una sola** sessione (rispondendo con la `sessionID` scelta).
2. Salva `selectedSessionID`.

## Guardrails

- Non basarti su chat corrente per i fatti: questa skill serve solo a scegliere la sessione.
- Non proporre modifiche a file.

## Output

- `selectedSessionID`
