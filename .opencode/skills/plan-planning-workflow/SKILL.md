---
name: plan-planning-workflow
description: Workflow operativo (stile programmatore). Chiarimenti minimi, task breakdown, raccomandazioni e guida all’implementazione (con snippet mirati) coerente con i vincoli del repo.
license: MIT
compatibility: opencode
metadata:
  audience: agents
  workflow: plan
---

## What I do

- Traduco una richiesta in un flusso operativo da sviluppatore: task piccoli, ordine di lavoro, dipendenze, rischi e checklist.
- Fornisco suggerimenti implementativi e snippet mirati (scheletri, firme, pseudo-codice) senza produrre patch complete non richieste.
- Tengo separate: fatti, assunti, decisioni, next steps.

## When to use me

- Quando la richiesta è vaga e serve un set minimo di chiarimenti *prima di scrivere codice*.
- Quando devi pianificare l’implementazione di una feature/refactor e vuoi un output “da programmatore” (task, note, warning, checklist).

## Workflow

1) **Chiarimenti minimi (se necessari)** (3–7 domande, un solo batch):
   - obiettivo e “definition of done”
   - vincoli (tempo, scope, compatibilità, UX)
   - dati/stato (API, mock, shape, persistenza)
   - priorità e rischi principali
2) **Vincoli del repo (sempre)**:
   - richiama i vincoli rilevanti da `AGENTS.md` (TS6, `noUnusedLocals/Parameters`, assenza test, ecc.)
   - evidenzia cosa può rompere build/lint e come evitarlo
3) **Task breakdown** (stile ticket):
   - 5–15 task piccoli, ciascuno con: obiettivo, output atteso, dipendenze, stima grossolana, “done criteria”
   - separa: UI / state / data / routing / accessibilità / refactor / docs
4) **Sequenza di implementazione**:
   - ordine consigliato (minimizza rework), punti di integrazione, rollback plan se serve
5) **Suggerimenti di codice (mirati)**:
   - snippet/scheletri per i punti critici (component boundaries, hook signature, types, data flow)
   - indica file/aree probabili (“es. `src/...`”) senza inventare file nuovi se non necessari
6) **Raccomandazioni & avvertenze**:
   - performance, a11y, error handling, edge cases, migrazioni
   - “gotcha” specifici del repo (import type-only, niente codice morto, ecc.)
7) **Checklist finale**:
   - controlli rapidi per non rompere build/lint (tipi, unused, naming, consistenza)

## Guardrails

- Non applicare modifiche al repository se non richiesto esplicitamente: lo fa **Build**.
- Snippet sì, patch complete no (salvo richiesta).
- Se i dati non sono verificabili, dichiaralo esplicitamente.
- Evita output YAML.

## Output

- Context (1–3 bullet)
- Assunzioni + vincoli del repo (bullet)
- Task breakdown (lista numerata di task)
- Sequenza consigliata (bullet)
- Snippet/scheletri (solo dove servono)
- Raccomandazioni & avvertenze
- Checklist finale
