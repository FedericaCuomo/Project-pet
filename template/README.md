---
title: ZampaInRete — Template HTML/CSS
summary: Template statici HTML/CSS per demo navigabile (frontend pubblico + dashboard admin).

tags: [zampainrete, ui, template]

depends: []

related:
  - ../INDEX.md
  - ../strategy/mvpAndScope.md

status: in_progress
updated: 2026-07-22
---

# Summary

- Base per demo/MVP: pagine statiche senza dipendenze JS (eccetto toggle sidebar).
- Struttura: home, liste (adozioni/smarrimenti/ritrovamenti), dettagli, form, pagina “chi siamo”, contatti.
- Area admin: dashboard KPI, gestione annunci, utenti, impostazioni.
- UI: palette verde/blu + neutrali; badge stati; layout responsive con navbar sticky.
- Uso: aprire `index.html` (pubblico) e `admin/index.html` (admin) in browser.
- Asset: immagini demo da Unsplash via URL (da sostituire).

---

# Details

# ZampaInRete — Template HTML/CSS

Template statici pronti per essere usati come base della demo/MVP.

## Struttura

```
template/
├── index.html                       # Home pubblica
├── css/
│   ├── style.css                    # Design system frontend (verde + blu)
│   └── admin.css                    # Design system admin dashboard
├── pages/                           # Pagine frontend
│   ├── adozioni.html                # Listing adozioni + filtri
│   ├── smarrimenti.html             # Listing animali smarriti
│   ├── ritrovamenti.html            # Listing animali ritrovati
│   ├── dettaglio-adozione.html      # Scheda singolo animale
│   ├── dettaglio-smarrimento.html   # Scheda annuncio smarrimento
│   ├── pubblica.html                # Form pubblicazione annuncio
│   ├── contatti.html                # Form contatti
│   └── chi-siamo.html               # Pagina chi siamo
└── admin/                           # Dashboard amministratore
    ├── index.html                   # Dashboard con KPI + tabella
    ├── annunci.html                 # Tabella gestione annunci
    ├── annuncio-nuovo.html          # Form creazione annuncio
    ├── utenti.html                  # Tabella utenti
    └── impostazioni.html            # Form impostazioni
```

## Palette

- **Verde** `#10b981 → #047857` — natura, adozioni, conferme
- **Blu** `#3b82f6 → #1d4ed8` — fiducia, ritrovamenti, link
- **Inchiostro** `#0f172a → #64748b` — testi, neutrali
- **Rosso** `#ef4444` — smarrimenti, allerta

## Caratteristiche

### Frontend
- Navbar sticky con blur, menu hamburger su mobile
- Hero con gradient e statistiche
- Card animali con badge, tag e griglia responsive (4/2/1 col)
- Filtri (input + select) per le liste
- Pagine di dettaglio con galleria + dati strutturati
- Form pubblicazione e contatti
- Footer con 4 colonne

### Admin
- **Sidebar a destra** (come richiesto), comprimibile su mobile
- Topbar con search e azioni rapide
- 4 stat card con trend
- Tabelle complete con thumb, badge stato, azioni
- Form completi con upload area
- Sistema di badge: success / blue / warn / danger / gray
- Bottoni: primary, blue, outline, danger, ghost, sm

## Uso

Apri `index.html` nel browser per la parte pubblica, `admin/index.html` per la dashboard. Tutto è puro HTML + CSS, nessuna dipendenza JS (eccetto un piccolo `onclick` per toggle sidebar mobile).

Font caricati da Google Fonts: **Inter** (testo) + **Poppins** (titoli).

Le immagini di esempio sono caricate da Unsplash via URL — sostituiscile con le tue.
