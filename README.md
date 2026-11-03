# Mind Garden – Brain Games

Static, no-build web app (English / 简体中文). Progress is saved in the browser's localStorage.

```
public/   index.html, i18n.js, sw.js, manifest.webmanifest, icon.svg, _headers
wrangler.jsonc   Cloudflare config (Workers Static Assets)
```

## 1. Test locally
```bash
npm install
npm run dev          # http://localhost:8787
```

## 2. Push to GitHub
```bash
git init -b main
git add .
git commit -m "Mind Garden: bilingual, mobile-friendly, PWA"
# create an empty repo on github.com (no README), then:
git remote add origin https://github.com/<you>/mind-garden.git
git push -u origin main
```

## 3. Host on Cloudflare (auto-deploy on every push)
1. Cloudflare dashboard → **Workers & Pages** → **Create** → **Import a repository** (Workers Builds).
2. Authorise GitHub, pick `mind-garden`, branch `main`.
3. Build command: *(leave empty)*. Deploy command: `npx wrangler deploy`. Root directory: `/`.
4. **Save and Deploy** → live at `https://mind-garden.<your-subdomain>.workers.dev`.
5. Custom domain: Worker → **Settings → Domains & Routes → Add → Custom domain**.

Dashboard labels change occasionally; the key facts are: repo root, no build command, deploy = `npx wrangler deploy`.

**Manual alternative:** `npx wrangler login && npm run deploy`.

## Updating
Edit files in `public/`, commit, push. When you change cached files, bump `V` in `public/sw.js` so phones pick up the update.
