# Publishing on GitHub Pages

This folder is set up so it can be published as a **GitHub Pages** site (Jekyll).

## What was changed for GitHub Pages

- **Links** — All internal links use `.html` (e.g. `practice-plan.html`) so they work after Jekyll builds the site.
- **index.md** — Serves as the site’s landing page (becomes the root URL).
- **overview.md** — Same content as README; built as **overview.html**. The index links here because Jekyll/GitHub Pages often don't build README.md as a page (README.html would 404).
- **_config.yml** — Jekyll config so each page gets a clean URL like `phase-01-foundation.html`.

## How to publish

1. Put the **contents** of this Trumpet folder in the **root** of a GitHub repo (or in a branch’s root).
2. In the repo: **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to the branch that contains the files (e.g. `main`).
4. Save. The site will be at `https://<username>.github.io/<repo-name>/` (or your custom domain).

## If the site is in a subpath

If the site URL is something like `https://username.github.io/trumpet-practice/`, add this to `_config.yml`:

```yaml
baseurl: /trumpet-practice
```

Then internal links would need to use that base path. With the repo at root (e.g. a repo named `trumpet-practice` used for Pages), the default baseurl is empty and the current links work as-is.

## Custom domain: trumpet.west.best

You can serve this site at **trumpet.west.best** once GitHub Pages is working. No changes to this repo are required—the site is already set up to work at the root of any domain.

### 1. Configure the custom domain in GitHub

1. In your repo go to **Settings → Pages**.
2. Under **Custom domain**, type: `trumpet.west.best`
3. Click **Save**.
4. If offered, turn on **Enforce HTTPS** (after DNS is set up and the certificate is ready).

### 2. Configure DNS for west.best

Wherever **west.best** is managed (e.g. Cloudflare, Namecheap, Google Domains, your registrar), add **one** of these:

**Option A — CNAME (recommended for a subdomain)**  
- **Type:** `CNAME`  
- **Name / Host:** `trumpet` (or `trumpet.west.best` if the provider asks for the full subdomain)  
- **Target / Value:** `YOUR-GITHUB-USERNAME.github.io`  
  - Use your actual GitHub username. Some providers want a trailing dot: `YOUR-GITHUB-USERNAME.github.io.`

**Option B — A records (if the provider doesn't support CNAME for subdomains)**  
Point `trumpet.west.best` to GitHub's IPs (see [GitHub's custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)); CNAME is usually simpler for a subdomain.

### 3. Wait for DNS and HTTPS

- DNS can take from a few minutes up to 24–48 hours to propagate.
- In **Settings → Pages**, GitHub will show when the custom domain is verified.
- After that, GitHub will issue an HTTPS certificate; **Enforce HTTPS** will then work and the site will be available at `https://trumpet.west.best`.

### 4. No baseurl change

Because the site is at the **root** of `trumpet.west.best` (e.g. `https://trumpet.west.best/`, `https://trumpet.west.best/practice-plan.html`), you do **not** need to set `baseurl` in `_config.yml`. All existing links will work as-is.

---

## Viewing on GitHub (before or without Pages)

When you open the repo on GitHub, you’re viewing the raw `.md` files. Links point to `.html` pages, which only exist after the site is built. So:

- **On the published site** — All links work.
- **On GitHub’s file view** — Clicking a link may open a 404 until the site is published; use the **Preview** or the published URL to navigate.
