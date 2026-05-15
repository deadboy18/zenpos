# ZenPOS

> Single-page spa & wellness POS dashboard — multi-branch, multi-currency, trilingual (EN / BM / 中文), light & dark themes. Pure HTML/CSS/JS, no build step.

ZenPOS is a self-contained front-end demo for managing a multi-branch spa / wellness operation: floor view, workers, rooms, services, collections, transactions, GHL card terminal, and bookings — all in a single HTML file.

---

## ✨ Features

- 🏢 **Multi-branch** — switch between branches from the sidebar, each with its own status, city, rooms, and contacts
- 👤 **Workers, rooms & services** — track availability and assignment per branch
- 💰 **Collections & transactions** — log payments and view history
- 💳 **GHL terminal view** — card-machine workflow page
- 📅 **Booking page** — reservation handling
- 🌐 **Trilingual UI** — English, Bahasa Malaysia, 中文 (Chinese)
- 💵 **Multi-currency** — MYR (Touch 'n Go, GrabPay, Boost, ShopeePay, DuitNow, Maybank MAE), USD (Apple Pay, Venmo), and more
- 🌓 **Light & dark themes** — persisted across sessions
- ⏱ **Live timers** — active session countdowns visible from the topbar
- 🚨 **Emergency alert** — one-tap broadcast to all branches and management
- 📱 **WhatsApp / Telegram quick contact** per branch
- 🔒 **Standard / Full mode toggle** — switch between two brand presentations

---

## 🛠 Tech stack

- **HTML5 / CSS3 / vanilla JavaScript** — no framework, no bundler, no npm
- **Google Fonts** — Plus Jakarta Sans (loaded from CDN)
- **CSS custom properties** — theming via `:root` and `[data-theme="dark"]` variables

Everything lives in one file. Open it in a browser and it runs.

---

## 🚀 Quick start (local)

```bash
git clone https://github.com/<your-username>/zenpos.git
cd zenpos
# just open it
open index.html         # macOS
xdg-open index.html     # Linux
start index.html        # Windows
```

> **Note:** rename `zenpos-system.html` → `index.html` so static hosts serve it as the default page.

---

## 🌐 Deployment

### Option A — Cloudflare Pages (recommended for private repos, free)

1. Push this repo to GitHub (private is fine).
2. Go to **Cloudflare Dashboard → Workers & Pages → Create → Pages → Connect to Git**.
3. Authorize the Cloudflare GitHub app and pick this repo.
4. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/`
5. Deploy. You'll get a `https://zenpos.pages.dev` URL within ~30 seconds.
6. (Optional) Add a custom domain under the project's **Custom domains** tab.

Cloudflare Pages works with private GitHub repos on the free plan, which is why this is the easier path here.

### Option B — GitHub Pages

> ⚠️ GitHub Pages on a **private** repo requires GitHub Pro, Team, or Enterprise. Public repos work on the free plan.

1. Make sure your entry file is named `index.html` (in the repo root, or in a `/docs` folder).
2. Repo → **Settings → Pages**.
3. **Source:** Deploy from a branch.
4. **Branch:** `main` / `root` (or `main` / `docs`).
5. Save. Your site goes live at `https://<your-username>.github.io/zenpos/` in a minute or two.

### Option C — Any static host

The file is fully static. It will also run on Netlify, Vercel, Surge, S3 + CloudFront, or even a USB stick. No server, no database.

---

## 🎨 Customization

Most things you'd want to tweak live near the top of the `<script>` block:

| What to change           | Where to look                                      |
| ------------------------ | -------------------------------------------------- |
| Brand names              | `brandName` / `brandNameFull` in the `i18n` object |
| Branches (name, city)    | `BRANCHES` array                                   |
| Currencies & payments    | `CURRENCIES` object, payment-method arrays         |
| Colors / theme           | `:root` and `[data-theme="dark"]` CSS variables    |
| Default language / theme | initial `state` object                             |

State is held in-memory; persistence (localStorage or a backend) is left as an exercise.

---

## 🔑 Hidden shortcuts

A couple of codes baked into the app:

| Code         | Where to type it          | What it does                                                                   |
| ------------ | ------------------------- | ------------------------------------------------------------------------------ |
| `6969`       | Anywhere (key buffer)     | Toggles between **Standard** (Zen Wellness Spa) and **Full** (Paradise Lounge) modes |
| `1234`       | Emergency alert prompt    | Confirms / clears an active emergency alert (typing `CONFIRM` works too)       |

> ⚠️ These are demo defaults living in plain JS. If you ever wire this up to a real environment, change them — and ideally move the emergency clear to a real auth check instead of a hardcoded PIN. Look for the `keyBuffer.includes('6969')` line (~579) and the `val==='1234'` check (~1377) in the source.

---

## 🗂 Project structure

```
zenpos/
├── index.html      # the whole app
└── README.md
```

That's it.

---

## 📄 License

Private / unlicensed. All rights reserved by the repo owner. Add a `LICENSE` file if you ever decide to open-source it (MIT is a sensible default for a UI demo).
