---
name: policy-discussion
description: Analizza conflitti o lacune nelle policy del repository e propone correzioni.
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: review
---

## What I do

- Diagnostico perché una regola risulta ambigua, in conflitto o non coerente con quanto dichiarato.
- Confronto `AGENTS.md`, prompt e skill per trovare conflitti, ambiguità, assenze o sovrapposizioni.
- Propongo patch limitate a `AGENTS.md` o `.opencode/config/` quando serve.

## When to use me

- Quando rilevi una discrepanza tra policy dichiarata e implementazione/documentazione nei file (AGENTS.md, prompt, skill).
- Quando bisogna discutere o rifinire regole del repository per ridurre ambiguità o conflitti.

## Workflow

1. Raccogli le fonti principali.
2. Identifica conflitto, buco di policy o sovrapposizione.
3. Formula una correzione minima e motivata.

## Output

- Sintesi delle fonti principali
- Problema di policy individuato
- Patch proposta
- Impatto e richiesta di conferma
