---
name: analyze-wrong-response-from-session-export
description: Analizza una risposta sbagliata usando il transcript esportato da una sessione Opencode selezionata.
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: ai-assistant
---

## What I do

- Gestisco un routing in 2 fasi:
  - se serve, scelgo la sessione con `list-opencode-sessions`
  - se serve, recupero l’export con `export-opencode-session`
- Con l’evidence recuperata chiedo (se manca) expected vs actual dell’anomalia.
- Avvio il flow di analisi e proposta patch usando le skill esistenti (diagnosi prompt/skill, separazione prompt vs operatività della skill, correzioni minime) basandomi **solo** sull’export.

## When to use me

- Quando l’utente segnala una risposta sbagliata ma l’evidenza utile vive in una sessione Opencode diversa dalla chat corrente.

## Workflow

### 1) Routing: acquisizione sessionID

1. Se **nel contesto** hai già `sessionID` selezionato (es. l’utente lo fornisce), usa quello come `selectedSessionID`.
2. Altrimenti, delega `list-opencode-sessions` e ottieni `selectedSessionID`.

### 2) Routing: acquisizione export + evidence base

1. Se l’utente fornisce già `exportText` e/o `userAnomalyText`/`assistantResponseText`, usa quelli come sorgente di verità.
2. Altrimenti delega `export-opencode-session` con `selectedSessionID` e ottieni:
   - `exportText`
   - `userAnomalyTextCandidate`
   - `assistantResponseTextCandidate`

### 3) Richiesta expected vs actual (solo se manca)

Se l’utente non ha già specificato cosa era sbagliato e qual era l’atteso:
1. Usa la evidence base recuperata (coppia `userAnomalyTextCandidate` + `assistantResponseTextCandidate`) come riferimento.
2. Chiedi all’utente di descrivere l’anomalia in termini di **expected vs actual** e a cosa si riferisce nella risposta dell’export.

### 4) Preparazione evidence bundle

Prepara e usa internamente:
- `selectedSessionID`
- `userAnomalyText` (da `exportText` o input utente)
- `assistantResponseText` (da `exportText` o input utente)
- `expectedVsActual` (da richiesta utente, se necessario)
- eventuali vincoli/output richiesti che risultano dal contesto del repository (es. regole in AGENTS.md/prompt/skill pertinenti, nel perimetro consentito)

### 5) Analisi e patch plan (flow “solito”)

Con l’evidence bundle sopra:
1. Diagnosi: individua quale regola (prompt vs skill) sembra aver causato la deviazione.
2. Deleghe (in ordine indicativo, solo quando servono):
   - `analyze-and-fix-agents` per incoerenze documentazione/prompt/skill
   - `prompt-optimizer` per ottimizzare prompt/skill mantenendo separazione prompt/operatività
   - `format-enforcer` per verifiche di formato
   - `policy-discussion` se emergono gap di policy/regole
   - `config-guard` se la patch tocca configurazioni sensibili
3. Proponi una patch minima con:
   - file e sezione
   - cosa cambia e perché
   - azioni successive (se serve conferma prima di applicare)

## Guardrails

- Basare tutta l’analisi **solo** su quanto recuperato via `opencode export` (ignora la chat corrente come sorgente di verità per i fatti).
- Non leggere/valutare o proporre modifiche fuori dal perimetro:
  - `.opencode/config/agents/` (inclusi `plan.md` e `build.md`)
  - `.opencode/config/skills/`
  - `AGENTS.md`.
- Preferisci correzioni minime e compatibili con l’assetto attuale.
- Output operativo: “Patch plan” e domande solo quando necessario; evita modifiche automatiche.

## Output

- `selectedSessionID`
- estratti dell’evidence bundle (userAnomalyText + assistantResponseText)
- expected vs actual (se forniti dall’utente)
- diagnosi (quale regola prompt/skill non sembra rispettata)
- patch plan minima con file e sezione
