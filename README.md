# श्री गुरु जम्भेश्वर शब्दवाणी — PWA Book Reader

A Progressive Web App (PWA) for reading the 120 Shabad of Shri Guru Jambheshwar.  
Hosted as a static site on GitHub Pages with full offline support.

## Features

- 📖 Browse all 120 chapters from the home screen
- 🔖 Bookmark any chapter (one bookmark at a time) — saved in localStorage
- ⬅️ ➡️ Navigate between chapters via sticky bottom nav
- 📴 Full offline support via Service Worker — JSON is cached on first load
- 📱 Installable as a PWA on iOS, Android, and desktop
- 🌙 Dark theme with gold accents

## Files

```
/
├── index.html        ← Main app (single-file SPA)
├── manifest.json     ← PWA manifest
├── sw.js             ← Service Worker (caching + offline)
├── icons/
│   ├── icon-192.png  ← PWA icon
│   └── icon-512.png  ← PWA icon
└── README.md
```

## Deploy to GitHub Pages

### Option 1: New repo (recommended)

1. Create a new GitHub repo (e.g. `shabad-vani`)
2. Upload all files from this folder to the repo root
3. Go to **Settings → Pages → Source** → select `main` branch, root `/`
4. Your app will be live at: `https://<your-username>.github.io/shabad-vani/`

### Option 2: GitHub CLI

```bash
gh repo create shabad-vani --public
git init
git add .
git commit -m "feat: initial PWA book reader"
git remote add origin https://github.com/<username>/shabad-vani.git
git push -u origin main
# Then enable GitHub Pages in Settings
```

### Option 3: Existing repo subfolder

If deploying to a subfolder (e.g. `/books/shabad-vani/`), update `manifest.json`:
```json
"start_url": "./index.html"
```
And in `sw.js`, update `STATIC_ASSETS` paths accordingly.

## Data Source

Content is fetched from:  
`https://raw.githubusercontent.com/poonia/my-db/main/app-db.json`

The Service Worker caches this JSON on first load so subsequent visits work offline.

## Customization

- **Colors**: Edit CSS variables in `:root {}` inside `index.html`
- **Font**: Noto Serif Devanagari is loaded from Google Fonts (cached after first load)
- **Data**: Update `DB_URL` in the `<script>` section to point to a different JSON source
