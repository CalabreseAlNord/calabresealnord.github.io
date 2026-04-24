# calabresealnord.github.io — Aurora Merenda Portfolio

Sito personale di **Aurora Merenda**, fotografa e content creator (Reggio Emilia / Milano).
Deploy automatico su GitHub Pages → dominio `merendaurora.com`.

## Struttura

```
/                   → sito v1 (produzione attuale, Nicepage)
  index.html        → homepage v1
  ca.html           → redirect a /files/artistic-curriculum.pdf
  portfolio.html    → redirect a /files/creative-portfolio.pdf
  files/            → PDF (CV artistico, portfolio, preventivi) + video hero
  images/           → loghi brand (1-9.png), foto profilo, favicon
  fonts/            → web fonts v1

v2/                 → sito v2 (redesign in corso, custom CSS/JS puro)
  index.html        → homepage v2 — file principale da modificare
  ca.html           → redirect a v2/files/artistic-curriculum.pdf
  portfolio.html    → redirect a v2/files/creative-portfolio.pdf
  files/            → PDF aggiornati (CV, portfolio, preventivi)
  media/
    images/         → 12 foto portfolio (1).JPG–(12).jpg
    reels/          → 6 video verticali (.MOV/.mp4/.mov)
    video/          → 4 copertine video orizzontali (.JPG/.jpg/.png)
    aurora-profilo.jpg → foto sfondo sezione "Chi sono"
  mockup/idea.html  → mockup originale di riferimento (non modificare)
```

## Regole per agenti AI

- **Il file da modificare è `v2/index.html`**. È un singolo file HTML self-contained (CSS e JS inline). Non usare framework, bundler o dipendenze esterne oltre a quelle già presenti (Google Fonts, Elfsight).
- **Non toccare `v2/mockup/idea.html`** — è il reference design originale.
- **Non modificare la v1** (root) salvo istruzioni esplicite. La v1 è in produzione.
- I path relativi in `v2/index.html` puntano a `../files/` e `../images/` per risorse condivise con la v1, e a `media/` per risorse v2-specifiche.
- **GTM**: ID `GTM-55VBKSZ` già configurato, non rimuoverlo.
- **Elfsight widget**: `elfsight-app-c5f99342-024c-488a-8471-1c928c35ce55` — feed Instagram live, lasciare invariato.

## Sezioni di v2/index.html

| Sezione | ID | Note |
|---|---|---|
| Hero video | `#hero` | Video `../files/previewsito-2.mp4`, autoplay muted loop |
| Chi sono | `#about` | Sfondo `media/aurora-profilo.jpg`, 2 pulsanti download CV+Portfolio |
| Fotografia | `#foto` | 12 immagini, griglia masonry 3 col, aspect-ratio 2/3 crop center |
| Video & Reels | `#video-section` | 6 reels verticali (mp4 locale) + 4 video YouTube (popup) |
| Instagram | `#instagram` | Elfsight widget |
| Brand | `#brands` | Marquee infinito, loghi `../images/1-9.png` |
| Contatti | `#contact` | Email, telefono, Instagram |
| Servizi | `#services` | Griglia 3×2, titolo + descrizione sempre visibili |

## Contatti nel sito

- Email: `merendaurora@gmail.com`
- Telefono: `(+39) 366 328 7202`
- Instagram: `@auroraamerenda`
- Posizioni: Reggio Emilia · Milano · Trasferte

## Video YouTube

| Titolo | URL |
|---|---|
| Giorni – Mullah | https://youtu.be/Res8fQ_agt8 |
| Vita Cinema – Swat | https://youtu.be/9PmAgCfUwYY |
| Ferrari | https://youtu.be/S5vfZ3n4jyY |
| Technogym Commercial | https://youtu.be/kjFnBLUpGos |

## Pattern JS ricorrenti

- **Popup video/reel**: `openPopup(card)` / `openReelPopup(item)` — leggono `data-src` e `data-title`
- **Chiusura universale**: ESC e click-outside chiudono sia popup video che lightbox foto
- **Scroll reveal**: IntersectionObserver su `.reveal` e `.reveal-scale`
- **Nav**: appare solo quando `#hero` non è visibile (IntersectionObserver)

## Deploy

Push su `main` → GitHub Actions deploya automaticamente su GitHub Pages.
Nessun build step — file statici serviti direttamente.
