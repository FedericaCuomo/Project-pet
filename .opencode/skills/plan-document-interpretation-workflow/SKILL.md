---
name: plan-document-interpretation-workflow
description: Interpreta documenti esistenti (brief/README/note/mock/screenshot) e produce insight, requisiti impliciti, rischi, opzioni e next steps per un progetto front-end (Vite + React + TypeScript), senza applicare modifiche.
license: MIT
compatibility: opencode
metadata:
  audience: agents
  workflow: plan
---

## What I do

- Interpreto documenti esistenti e li trasformo in una lettura “da programmatore”: requisiti, non-funzionali, edge case, rischi.
- Separo sempre: **fatti** (citabili), **assunti**, **decisioni** (da prendere/validare).
- Produco opzioni con raccomandazione e un backlog iniziale (task piccoli) pronto per passare a Build.

## When to use me

- Quando l’utente chiede di valutare/interpretare documenti esistenti (brief/spec/README/mockup).
- Quando serve allineare scope, criteri di accettazione e priorità prima di scrivere codice.

## Workflow

1) **Source of truth & obiettivo**
   - Quali documenti sono autorevoli?
   - Qual è il risultato atteso (decisione, backlog, architettura, UX)?
2) **Estrazione**
   - Requisiti funzionali (user flow)
   - Requisiti non funzionali (perf, a11y, SEO se rilevante)
   - Stati UI (loading/empty/error) e edge case
3) **Gap analysis**
   - Ambiguità e contraddizioni
   - Dati mancanti (shape, persistenza, API/mock)
4) **Opzioni**
   - 2–3 approcci (trade-off chiari)
   - Raccomandazione motivata
5) **Next steps operativi**
   - Task breakdown con done criteria
   - Checklist di verifica manuale (il repo non ha test runner)

## Guardrails

- Non inventare contenuti: se un requisito non è nel documento, marcarlo come **assunto** o domanda.
- Non applicare modifiche al repository (niente patch/commit): solo analisi e piano.
- Evita output YAML.

## Output

- Context (documenti analizzati + scope)
- Fatti / Assunti / Decisioni
- Requisiti (funzionali + non-funzionali)
- Rischi / Ambiguità / Domande minime (solo bloccanti)
- Opzioni + Raccomandazione
- Next steps (task breakdown + checklist manuale)
