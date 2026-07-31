---
name: export-opencode-session
description: Esporta una sessione Opencode (per `sessionID`) e prepara una evidence base dall’export.
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: ai-assistant
---

## What I do

- Esegue `opencode export <sessionID>`.
- Mantiene l’export come sorgente di verità per l’analisi successiva.
- Estrae una **evidence base** tramite euristiche (candidato anomalia + risposta assistant immediatamente associata), senza ancora chiedere expected vs actual.

## When to use me

- Quando l’evidenza utile vive in una sessione Opencode e hai già un `sessionID` selezionato.

## Workflow

### 1) Export sessione

1. Richiedi `sessionID` (se manca, chiedi all’utente).
2. Esegui `opencode export <sessionID>`.
3. Mantieni l’output come `exportText` (sorgente di verità).

### 2) Estrazione evidence base (euristica)

1. Identifica l’ultimo messaggio con `role=user` nell’export come candidato per `userAnomalyTextCandidate`.
2. Identifica la risposta `role=assistant` immediatamente precedente o successiva nel transcript come candidato `assistantResponseTextCandidate`.
3. Se l’euristica non è univoca, seleziona la coppia “più vicina temporalmente” e segnala l’incertezza nell’output.

## Guardrails

- Non interpretare policy/regole: questa skill prepara solo evidence dall’export.
- Non proporre patch o modifiche a file.

## Output

- `selectedSessionID`
- `exportText`
- `userAnomalyTextCandidate`
- `assistantResponseTextCandidate`
