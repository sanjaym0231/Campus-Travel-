# Detour — Campus Travel & Rental Hub

A multi-page static website for college students to discover Himachal hill-station trips and rental vehicles — structured like a real travel platform (home, explore with filters, colleges, areas, rentals, login/register, contact), built with plain HTML/CSS/JS so it's ready to push straight to GitHub Pages.

## Pages

| Page | What it does |
|---|---|
| `index.html` | Home — search bar, trips by college, trips by area, trending routes, trip-type mosaic, rental teaser |
| `explore.html` | Full trip listing with live filters (type, budget, duration, comfort, departure area) |
| `colleges.html` | Browse by campus (LPU, DAV University, GNDU, Chandigarh University, Punjabi University) |
| `areas.html` | Browse by departure city (Jalandhar, Amritsar, Chandigarh, Ludhiana, Pathankot) |
| `rentals.html` | Rental fleet (Brezza, Ertiga, Swift, Baleno, Innova Crysta, Scorpio-N) with a type filter |
| `login.html` / `register.html` | Static auth forms (front-end only — see note below) |
| `contact.html` | Enquiry / booking form, pre-filled when you arrive from a "View package" or "Reserve" button |

## Structure

```
detour-site/
├── index.html
├── explore.html
├── colleges.html
├── areas.html
├── rentals.html
├── login.html
├── register.html
├── contact.html
├── css/
│   └── style.css
├── js/
│   └── script.js
└── README.md
```

No build step, no npm install. Fonts load from Google Fonts via CDN; every illustration is inline SVG or a CSS gradient, so there are no image assets to manage.

## Run it locally

```bash
cd detour-site
python3 -m http.server 8000
# visit http://localhost:8000
```

## Upload to GitHub

```bash
cd detour-site
git init
git add .
git commit -m "Initial commit: Detour campus travel & rental hub"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

Then in the repo: **Settings → Pages** → Source: `main` branch, `/ (root)` folder → Save. Live in a minute or two at `https://<your-username>.github.io/<your-repo>/`.

## What's real vs. what's a demo

This is a front-end-only project — there's no server or database behind it, same as any static GitHub Pages site:

- **Explore filters** are fully working — real client-side filtering over the trip data in `js/script.js`, with the results grid, count, and empty state all updating live.
- **Search bar, mosaic tiles, and "View package" / "Reserve" buttons** carry your choice into `explore.html` or `contact.html` via URL parameters, so the destination pre-fills.
- **Login and Register forms** validate on the front end and show a message on submit, but don't create real accounts. To make them real, connect them to an auth provider (Firebase Auth, Supabase, Auth0) or your own backend API.
- **The contact/booking form** shows a confirmation message locally but doesn't send anywhere yet. Wire it to a form service (Formspree, Getform) or a serverless function when you're ready to receive real enquiries.

## Customizing

- **Colors, fonts, spacing:** CSS custom properties at the top of `css/style.css` (`:root`).
- **Trip or rental data:** each card is plain HTML in its page — duplicate an `<article class="card...">` block and edit the text, tag, price, and `data-*` filter attributes (on `explore.html` cards) to match.
- **Colleges / areas:** edit the `.entity-card` blocks in `colleges.html` / `areas.html`.

## License

Free to use and modify for coursework or personal projects.
