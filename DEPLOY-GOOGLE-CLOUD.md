# Hosting the Lovable site on Google Cloud

Lovable produces a Vite + React single-page app. On Google Cloud, the right home for that is
**Firebase Hosting** (Firebase is Google Cloud's web-app layer; the project shows up in the Cloud
console). It is free at portfolio traffic levels, gives you a global CDN and automatic HTTPS, and
custom domains take one DNS change. Cloud Run and Cloud Storage are covered at the end for
completeness; neither is a better fit for a static portfolio.

## 0. Get the code out of Lovable (5 min)

1. In Lovable: project → **Settings → GitHub → Connect** and create the repo (name it
   `portfolio`, keep it private — it's a code repo, the site itself is public).
2. Clone it locally:
   ```bash
   git clone git@github.com:<your-github-user>/portfolio.git
   cd portfolio
   npm install
   npm run build        # produces dist/
   ```
   If `npm run build` fails, fix it in Lovable first ("the production build fails with: <error>").
3. Put your headshot at `public/headshot.jpg` and commit.

## 1. Create the Google Cloud / Firebase project (5 min)

1. Go to https://console.firebase.google.com → **Add project** → name it `jeff-rolling-portfolio`.
   Google Analytics: off (you can add it later). This also creates a Google Cloud project of the
   same name; no billing account is required for the Spark (free) plan.
2. In the project, open **Build → Hosting → Get started** just to enable it. You can close the
   wizard; the CLI does the rest.

## 2. Deploy from your laptop (10 min)

```bash
npm install -g firebase-tools
firebase login                      # opens the browser; use the Google account that owns the project
firebase init hosting
```
Answer the prompts:
- Use an existing project → `jeff-rolling-portfolio`
- Public directory → `dist`
- Configure as a single-page app (rewrite all URLs to /index.html)? → **Yes** (required, or
  `/work/checkout-reliability` returns 404 on refresh)
- Set up automatic builds and deploys with GitHub? → **No** for now (step 4 does it properly)
- Overwrite dist/index.html? → **No**

Then:
```bash
npm run build
firebase deploy --only hosting
```
The output ends with `Hosting URL: https://jeff-rolling-portfolio.web.app`. Open it on your phone
and click every route.

## 3. Custom domain (15 min, then up to 24 h for DNS)

1. Firebase console → **Hosting → Add custom domain** → enter `jeffrolling.com` (or whichever you
   own; if you don't own one yet, Google Domains is gone — buy at Cloudflare or Namecheap, ~€10/yr).
2. Firebase shows a TXT record to prove ownership, then A records (or a CNAME for `www`). Add them
   at your registrar. Tick "redirect www → apex" in Firebase.
3. Wait. SSL is issued automatically once DNS propagates; status turns to **Connected**.
4. Put the final URL on your resume, LinkedIn (Contact info → Website, and the Featured section),
   and in the experience library in the ProductManagement repo under Fast Facts → Portfolio.

## 4. Auto-deploy on every push (10 min, optional but worth it)

So that editing in Lovable → "push to GitHub" → live site, with no laptop step:
```bash
firebase init hosting:github
```
- Repo → `<your-github-user>/portfolio`
- Set up the workflow to run a build script before every deploy? → **Yes** → `npm ci && npm run build`
- Deploy to live channel on merge? → **Yes** → branch `main`

This writes `.github/workflows/firebase-hosting-merge.yml` and stores a service-account secret
in the GitHub repo. Commit and push; check the Actions tab for a green run. From now on every
Lovable push to `main` goes live in ~2 minutes, and pull requests get a preview URL.

## 5. Cost

Firebase Hosting Spark plan: 10 GB storage, 360 MB/day transfer, free. A portfolio uses a
fraction of that. No billing account needed unless you add other Firebase products.

## Alternatives on Google Cloud (and why not)

- **Cloud Run** — containerize `dist/` behind nginx, `gcloud run deploy --source .`, then
  **Domain mappings** for the custom domain. Scales to zero, so it's near-free, but you're
  maintaining a Dockerfile and nginx config to serve five static pages. Use it only if you later
  add a backend.
- **Cloud Storage static website** — a bucket named after your domain with `index.html` set as the
  main page. Serves plain HTTP only; HTTPS requires an external HTTPS load balancer, which costs
  roughly $18/month before traffic. Not worth it for this.
- **Lovable's own hosting** — the Publish button plus a custom domain works fine and is the
  zero-maintenance option if you decide Google Cloud isn't worth the extra step.

## Before it goes live — checklist

- [ ] Every route works on refresh (SPA rewrite in step 2).
- [ ] Headshot loads; JR fallback never shows in production.
- [ ] No phone number anywhere on the site.
- [ ] Numbers match the experience library in the ProductManagement repo (39%, 9.4%, 49 → <30 days, 64.5 → 15.3, 76 clients, 8,000+ travelers, €1.8M, 20 → 37).
- [ ] Lighthouse mobile score ≥ 90 (Chrome DevTools → Lighthouse). Fraunces + Source Sans 3 + Plex Mono is three font files; if performance dips, drop Plex Mono and use the system monospace stack.
- [ ] `robots` not blocking; page titles set (follow-up prompt 3 in `LOVABLE-PROMPT.md`).
