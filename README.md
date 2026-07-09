# AGVC Website — agvcfunds.com

Static site. No build step. Hosted on Cloudflare Pages.

---

## Deploy Instructions

### Step 1 — Replace files in GitHub repo

```bash
# Clone your existing repo
git clone https://github.com/s7jcqc27x7-dev/agvcfunds.github.io.git
cd agvcfunds.github.io

# Wipe old Netlify/React build files (keep .git)
find . -not -path './.git*' -not -name '.' -delete

# Copy new site files into this folder:
# index.html, __forms.html, netlify.toml → root
# All images → /images/
```

Then drop in your images (see list below), and push:

```bash
git add -A
git commit -m "Rebuild: AGVC v2 — static site"
git push origin main
```

---

### Step 2 — Connect to Cloudflare Pages (free)

1. Go to https://dash.cloudflare.com → **Pages** → **Create a project**
2. Choose **Connect to Git** → select GitHub → pick `agvcfunds.github.io`
3. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave blank)*
   - **Build output directory:** `/` or `.`
4. Click **Save and Deploy**

Cloudflare will deploy in ~30 seconds. Every `git push` auto-deploys.

---

### Step 3 — Connect agvcfunds.com domain

Since your domain is already on Cloudflare DNS, this is automatic:

1. In your Cloudflare Pages project → **Custom domains** → **Set up a custom domain**
2. Type `agvcfunds.com` → Cloudflare auto-creates the DNS record
3. Also add `www.agvcfunds.com` if you want www to redirect

SSL is provisioned automatically. Done.

---

### Step 4 — Remove old Netlify DNS (if applicable)

If agvcfunds.com was previously pointing to Netlify, go to:
Cloudflare DNS → delete any A or CNAME records pointing to `*.netlify.app`

---

## Images — place in /images/ folder

Copy these from your local images folder, keeping exact filenames:

| File | Used in |
|---|---|
| `agvc-logo-white.png` | Nav logo + browser favicon |
| `agvc-logo-black.png` | (available, unused — keep for later) |
| `map-asia-hub.png` | Hero background + Presence section |
| `justin-tso.jpg` | Team spotlight |
| `aaisha-bhuiyan.jpg` | Advisor card |
| `doug-nissinoff.jpg` | Advisor card |
| `donny-siu.jpg` | Advisor card |
| `rima-patel.jpg` | Advisor card |
| `elena-liapounova.jpeg` | Advisor card |
| `sergei-petukhov.jpeg` | Advisor card |
| `eric-verdin.jpeg` | Advisor card |
| `editorial-scmp.png` | Service panel logo strip |
| `editorial-nature.png` | Service panel logo strip |
| `editorial-tvm.png` | Service panel logo strip |
| `editorial-worldbank.png` | Service panel logo strip |

All images have graceful fallbacks — missing images won't break the site.

---

## Updating advisor titles/bios

Open `index.html` and search for `id="advisors"`.
Each advisor card has three fields to update:
- `adv-name` — full name
- `adv-title` — title / role
- `adv-org` — organisation

---

## Updating service content

Each service is a tab panel in `index.html`:
- `id="s1"` — Business Landing
- `id="s2"` — CDMO & Manufacturing
- `id="s3"` — Capital Markets
- `id="s4"` — Venture Building

---

## File structure

```
/
├── index.html          ← Entire site
├── __forms.html        ← Keep for Netlify form fallback (harmless)
├── netlify.toml        ← Can delete if not using Netlify
├── images/             ← Drop all images here
└── README.md
```

---

## Contact form note

The form uses `data-netlify="true"` which only works on Netlify.
On Cloudflare Pages, replace with one of:
- **Formspree** (free tier: 50 submissions/month) — https://formspree.io
- **Web3Forms** (free, unlimited) — https://web3forms.com ← recommended

To use Web3Forms:
1. Get a free access key at web3forms.com
2. In index.html, find `<form name="contact"` and replace with:
   `<form action="https://api.web3forms.com/submit" method="POST">`
3. Add inside the form: `<input type="hidden" name="access_key" value="YOUR_KEY">`
4. Remove `data-netlify="true"` and `netlify-honeypot` attributes

