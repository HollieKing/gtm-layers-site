# GTM Layers — Deploy

Three steps. Ten minutes. The first deploy uses a `vercel.app` staging URL — private (blocked from search engines, blocked from being framed/embedded), shareable with advisors.

---

## 1 · Generate the OG image (~60 seconds, one-time)

The site references `/og-image.png` for social previews. To create it:

1. Open `og.html` in any browser (just double-click the file).
2. Open DevTools — **Cmd + Option + I** on Mac, **F12** on Windows.
3. Toggle the device toolbar — **Cmd + Shift + M**. Set viewport to **1200 × 630**.
4. Open the command menu — **Cmd + Shift + P**. Type *"Capture full size screenshot"* and run it.
5. Save the downloaded image as **`og-image.png`** in this `/site` folder, next to `index.html`.

That's it. The card is rendered server-side every time someone shares the URL on LinkedIn, Slack, Twitter, etc.

---

## 2 · Deploy to Vercel (~5 minutes)

### Option A — Vercel CLI (fastest, one command)

```
npm install -g vercel
cd "/Users/hollie/Documents/Claude/Projects/AI GTM/site"
vercel
```

Answer the prompts with defaults. Vercel will give you a URL like `gtmlayers-abc123.vercel.app`.

### Option B — Drag-and-drop (no terminal)

1. Sign in at [vercel.com](https://vercel.com) (GitHub / email — both free).
2. Click **Add New → Project**.
3. Click **"Continue with no Git provider"** (or "Browse all templates" → "Other").
4. Drag the entire `/site` folder into the upload area.
5. Click **Deploy**.

You'll get a `*.vercel.app` URL within ~30 seconds.

---

## 3 · Share the URL

The staging URL is locked down two ways:

- `<meta name="robots" content="noindex,nofollow">` in `index.html` — search engines ignore it.
- `robots.txt` — blocks compliant crawlers from the entire site.

Safe to share by direct link with advisors, partners, and trusted readers for feedback.

---

## Going production (later — when ready)

When the brand is ready to launch publicly:

| # | Step | Where |
|---|------|-------|
| 1 | Domain ✓ acquired | `gtmlayers.com` registered at Cloudflare. |
| 2 | Add domain to Vercel | Project → Settings → Domains → Add `gtmlayers.com`. Follow DNS prompts (Cloudflare-to-Vercel is automatic if both managed by Cloudflare, otherwise ~5 min). |
| 3 | Remove `noindex` meta tag | `index.html` line ~14 — delete `<meta name="robots" content="noindex,nofollow">`. |
| 4 | Update `robots.txt` | Replace `Disallow: /` with `Allow: /`. |
| 5 | Set up email | Google Workspace or Fastmail on `gtmlayers.com`. Create `brief@gtmlayers.com`. |
| 6 | Wire the mailto | Already set to `mailto:brief@gtmlayers.com` in `index.html` — confirms automatically once email exists. |
| 7 | Add real proof | Add the case study section back when you have one authorized engagement to anonymize. Add real client/press logos only when authentic. |
| 8 | Add analytics | Plausible or Fathom — privacy-respecting, ~5 minutes to integrate. |
| 9 | Add privacy policy + terms | Required if collecting email or any data. Use a generator (Termly, Iubenda) or a lawyer for the founder-grade version. |
| 10 | Confirm legal entity in footer | Currently reads `© 2026 · GTM LAYERS` — update to the registered entity when incorporated. |

---

## File map

```
/site/
├── index.html       — the homepage
├── favicon.svg      — wordmark glyph as favicon
├── og.html          — OG image generator (utility — open and screenshot)
├── og-image.png     — generated social card (you create in step 1)
├── vercel.json      — security headers, clean URLs
├── robots.txt       — crawler block (staging)
└── DEPLOY.md        — this file
```

---

## What's been intentionally stripped from the staging build

- The case study section (38% / 2.4× / −47% stats and the anonymized CEO quote). Removed because they were illustrative, not real. Add back when you have a genuine, authorized engagement.
- "INDEX LIVE" framing on the hero pill. Softened to "METHODOLOGY V1.0".
- The "N = 412 COMPANIES" claim on the Index board. Replaced with "REV 09 · 9 DIMENSIONS".
- The minute-by-minute live timestamp ticker on the Index. Replaced with a static "REV 09 · MAY 2026" + "ANNUAL PUBLICATION FORTHCOMING" footer.
- The legal entity suffix in the footer ("LTD."). Re-add once incorporated.

The Index methodology, dimension scores, deltas, and composite are kept — they're a faithful preview of what the methodology produces, not a false claim about a live dataset.
