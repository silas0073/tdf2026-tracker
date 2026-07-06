# Tour de France 2026 — Route & Results Tracker

A single-page static site tracking the 2026 Tour de France: all 21 stages,
stage results as they're confirmed, and the four jersey classifications
(yellow, green, polka dot, white).

No build step, no dependencies — it's one `index.html` file.

## Run locally

Just open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8080
# then visit http://localhost:8080
```

## Deploy: GitHub → Netlify (continuous deployment)

1. **Create a GitHub repo** (replace `YOUR_USERNAME`):
   ```bash
   cd tdf2026-tracker
   git branch -m main
   git remote add origin https://github.com/YOUR_USERNAME/tdf2026-tracker.git
   git push -u origin main
   ```
   (If the repo doesn't exist yet, create it first at github.com/new, or with
   the GitHub CLI: `gh repo create tdf2026-tracker --public --source=. --push`.)

2. **Connect it to Netlify:**
   - Go to [app.netlify.com](https://app.netlify.com) → **Add new site** → **Import an existing project**
   - Choose **GitHub**, authorize Netlify, and select the `tdf2026-tracker` repo
   - Build settings are already set in `netlify.toml` (publish directory `.`, no build command) — Netlify will detect them automatically
   - Click **Deploy site**

From then on, every push to `main` redeploys the site automatically.

## Updating results

Stage results and jersey standings live in the `stages` and `gcStandings`
arrays near the top of the `<script>` block in `index.html`. Update those
after each stage and push — Netlify will pick up the change.
