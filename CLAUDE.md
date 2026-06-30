# calabresealnord.github.io — Aurora Merenda Portfolio

Sito personale di **Aurora Merenda**, fotografa e content creator specializzata in fotografia concerti/musica (Reggio Emilia / Milano).
Deploy automatico su GitHub Pages → dominio `merendaurora.com`.

## Struttura

```
/
  index.html          → homepage (unico file da modificare — CSS e JS inline)
  ca.html             → redirect a /files/artistic-curriculum.pdf
  portfolio.html      → redirect a /files/creative-portfolio.pdf
  robots.txt          → crawler config + Sitemap pointer
  sitemap.xml         → sitemap homepage per GSC
  CNAME               → merendaurora.com
  files/              → PDF (CV artistico, portfolio, preventivi) + video hero (previewsito-2.mp4)
  images/             → loghi brand (1-9.png), favicon.jpg
  media/
    aurora-profilo.jpg        → foto sfondo sezione "Chi sono"
    images/                   → foto portfolio (foto-01–16.jpg, tutti JPEG compressi)
    reels/copertine/          → copertine reels (tutti .jpg): alfa, ernia, frah-quintale,
                                giorni, juli, michele-bravi, olly, sayf, vita-cinema
    video/                    → thumbnail video orizzontali (tutti .jpg)
    hero/                     → video hero (intro.mp4, intro-orizzontale.mp4)
```

**Nota:** La directory `v2/` non esiste più. Il sito è interamente alla root.

## Regole per agenti AI

- **Il file da modificare è `index.html`** (root). È un singolo file HTML self-contained (CSS e JS inline). Non usare framework, bundler o dipendenze esterne oltre a quelle già presenti (Google Fonts, Elfsight).
- **Tutte le immagini sono JPEG** — non aggiungere PNG. Comprimere con sips a max q=82, dimensione max 1600px sul lato lungo per foto portfolio, 800px per thumbnail.
- **GTM**: ID `GTM-55VBKSZ` già configurato, non rimuoverlo.
- **Elfsight widget**: `elfsight-app-c5f99342-024c-488a-8471-1c928c35ce55` — feed Instagram live, lasciare invariato.
- **SEO**: canonical, sitemap, JSON-LD Person schema già presenti — non rimuovere.

## Sezioni di index.html

| Sezione | ID | Note |
|---|---|---|
| Hero video | `#hero` | Video `files/previewsito-2.mp4`, autoplay muted loop |
| Chi sono | `#about` | Sfondo `media/aurora-profilo.jpg`, 2 pulsanti download CV+Portfolio |
| Fotografia | `#foto` | 12 immagini, griglia masonry 3 col, aspect-ratio 2/3 crop center |
| Video & Reels | `#video-section` | 7 reels (YouTube Shorts popup) + 4 video YouTube (popup) |
| Instagram | `#instagram` | Elfsight widget |
| Brand | `#brands` | Marquee infinito, loghi `images/1-9.png` |
| Contatti | `#contact` | Email, telefono, Instagram |
| Servizi | `#services` | Griglia 3×2, `<h3>` per nomi servizi |

## Contatti nel sito

- Email: `merendaurora@gmail.com`
- Telefono: `(+39) 366 328 7202`
- Instagram: `@roradirector` (handle corretto — `@auroraamerenda` era outdated)
- YouTube: `@merendaurora`
- Posizioni: Reggio Emilia · Milano · Trasferte

## Reels verticali (YouTube Shorts)

| Label | YouTube Short URL | Copertina |
|---|---|---|
| Tedua | https://youtube.com/shorts/uom7lDjILl0 | YouTube auto-thumb |
| Alfa | https://youtube.com/shorts/IhaH6q6mq5k | `media/reels/copertine/alfa.jpg` |
| Vita Cinema | https://youtube.com/shorts/jw16tSAme_8 | `media/reels/copertine/vita-cinema.jpg` |
| Frah Quintale | https://youtube.com/shorts/diWv0JEB76s | `media/reels/copertine/frah-quintale.jpg` |
| Juli | https://youtube.com/shorts/tYfptpAuWNE | `media/reels/copertine/juli.jpg` |
| Gabry Ponte | https://youtube.com/shorts/HMvfWbhFbrE | `media/reels/copertine/gabry-ponte.jpg` |
| Sayf | https://youtube.com/shorts/nEoKef34q3Y | `media/reels/copertine/sayf.jpg` |

Copertine disponibili ma non ancora in uso (mancano URL Shorts): `ernia.jpg`, `michele-bravi.jpg`, `olly.jpg`

## Video YouTube (popup orizzontali)

| Titolo | URL | Thumbnail |
|---|---|---|
| Giorni – Mullah | https://youtu.be/Res8fQ_agt8 | `media/video/video-thumb-giorni.jpg` |
| Vita Cinema – Swat | https://youtu.be/9PmAgCfUwYY | `media/video/video-thumb-vita-cinema.jpg` |
| Ferrari | https://youtu.be/S5vfZ3n4jyY | `media/video/video-thumb-ferrari.jpg` |
| Technogym Commercial | https://youtu.be/kjFnBLUpGos | `media/video/video-thumb-technogym.jpg` |

## JSON-LD Person schema (SEO/GEO)

Presente in `<head>` prima di `</head>`. Include:
- `name`, `alternateName: "roradirector"`, `jobTitle`, `description` con nomi artisti
- `knowsAbout`: fotografia concerti, videomaking, content creation, ecc.
- `interactionStatistic`: 3474 follower Instagram
- `sameAs`: Instagram + YouTube
- Non rimuovere o modificare senza motivo SEO esplicito.

## Pattern JS ricorrenti

- **Popup video/reel**: `openPopup(card)` / `openReelPopup(item)` — leggono `data-src` e `data-title`
- **Chiusura universale**: ESC e click-outside chiudono sia popup video che lightbox foto
- **Scroll reveal**: IntersectionObserver su `.reveal` e `.reveal-scale`
- **Nav**: appare solo quando `#hero` non è visibile (IntersectionObserver)

## Deploy

Push su `main` → GitHub Pages deploya automaticamente.
Nessun build step — file statici serviti direttamente.

**Dopo ogni deploy con modifiche SEO:** GSC → URL Inspection → richiesta indicizzazione manuale.
