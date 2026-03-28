# 🛒 ScontOne — Blog Hugo per Recensioni Amazon

Un blog moderno, responsive e dark-themed costruito con Hugo per recensioni e consigli sui prodotti Amazon.

---

## 🚀 Avvio rapido

### Prerequisiti
- **Hugo Extended** v0.120.0 o superiore
  - macOS: `brew install hugo`
  - Windows: `choco install hugo-extended` o [scarica da GitHub](https://github.com/gohugoio/hugo/releases)
  - Linux: `snap install hugo` oppure scarica il binario da GitHub

### Avvio del server di sviluppo

```bash
cd scontone
hugo server -D
```

Il sito sarà disponibile su **http://localhost:1313**

### Build per produzione

```bash
hugo --minify
```

I file saranno generati nella cartella `public/`.

---

## 📁 Struttura del progetto

```
amazblog/
├── hugo.toml              # Configurazione principale
├── assets/
│   └── css/
│       └── main.css       # Tutti gli stili
├── layouts/
│   ├── _default/
│   │   ├── baseof.html    # Layout base HTML
│   │   ├── list.html      # Pagine lista (categorie)
│   │   └── single.html    # Singola recensione
│   ├── partials/
│   │   ├── header.html    # Header con nav
│   │   ├── footer.html    # Footer
│   │   └── post-card.html # Card articolo
│   └── index.html         # Homepage
├── content/
│   ├── tecnologia/
│   │   ├── _index.md
│   │   ├── smartphone/
│   │   ├── tablet/
│   │   ├── laptop/
│   │   └── audio/
│   ├── cucina/
│   │   ├── _index.md
│   │   ├── friggitrici-ad-aria/
│   │   ├── macchine-caffe/
│   │   ├── tostapane/
│   │   └── robot-cucina/
│   ├── casa/
│   │   ├── aspirapolvere/
│   │   ├── domotica/
│   │   └── illuminazione/
│   ├── bellezza/
│   └── sport/
└── archetypes/
    └── default.md         # Template nuovo articolo
```

---

## ✍️ Creare una nuova recensione

```bash
# Crea un nuovo articolo in una sottocategoria
hugo new tecnologia/smartphone/samsung-galaxy-s25-recensione.md
hugo new cucina/macchine-caffe/nespresso-vertuo-recensione.md
```

### Frontmatter completo (parametri disponibili)

```yaml
---
title: "Nome Prodotto: Recensione Completa"
date: 2025-01-01
draft: false                    # true = non pubblicato
featured: false                 # true = appare in evidenza homepage

# Prodotto
category: "Smartphone"          # categoria visualizzata
icon: "📱"                      # emoji per placeholder immagine
brand: "Samsung"
product_name: "Samsung Galaxy S25"
image: "/images/galaxy-s25.jpg" # path immagine (opzionale)

# Rating
rating: 4.5                     # voto da 1 a 5
reviews: 1234                   # numero recensioni Amazon

# Prezzo
price: "€899"
price_old: "€999"               # prezzo barrato
discount: 10                    # % sconto
amazon_url: "https://amzn.to/xxx"

# Badge
best_buy: false                 # badge BEST BUY
top_pick: true                  # badge TOP PICK

# Meta
read_time: 6                    # minuti lettura
author: "Nome Autore"
tags: ["samsung", "android"]
description: "Meta description per SEO"

# Score dettagliati (per barre di valutazione)
scores:
  Design: 5
  Fotocamera: 4
  Performance: 5
  Batteria: 4
  Prezzo/Qualità: 4

# Pro e contro
pros:
  - "Punto di forza 1"
  - "Punto di forza 2"
cons:
  - "Limite 1"
  - "Limite 2"
---
```

---

## 🎨 Personalizzazione

### Colori (in `assets/css/main.css`)

```css
:root {
  --accent: #ff6b35;    /* Colore principale (arancione) */
  --gold: #ffd166;      /* Stelle e punteggi */
  --green: #06d6a0;     /* Prezzi */
  --bg: #0a0a0f;        /* Sfondo principale */
}
```

### Aggiungere una nuova categoria

1. Crea la cartella e il file indice:
```bash
mkdir -p content/gaming
echo '---
title: "Gaming"
description: "Recensioni di console, periferiche e giochi."
icon: "🎮"
color: "#7c3aed"
---' > content/gaming/_index.md
```

2. Aggiungi al menu in `hugo.toml`:
```toml
[[menu.main]]
  name = "Gaming"
  url = "/gaming/"
  weight = 7
```

3. Aggiungi la card nella homepage (`layouts/index.html`).

---

## 📦 Deploy

### Netlify (raccomandato)
1. Pusha il repository su GitHub
2. Connetti il repo a Netlify
3. Build command: `hugo --minify`
4. Publish directory: `public`

### GitHub Pages
Aggiungi `.github/workflows/hugo.yml` con l'action ufficiale Hugo.

---

## 💡 Consigli SEO

- Usa descrizioni uniche nel frontmatter di ogni articolo
- Includi parole chiave nel titolo e nella URL (slug del file)
- Aggiungi immagini con alt text descrittivi
- Pubblica regolarmente per migliorare il posizionamento

---

## ⚖️ Affiliate Disclaimer

Ricorda di aggiornare il disclaimer affiliazione in `hugo.toml`:
```toml
[params]
  affiliateDisclaimer = "Il tuo testo disclaimer qui..."
```

---

*Made with ❤️ using Hugo*
