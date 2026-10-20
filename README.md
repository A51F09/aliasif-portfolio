# aliasif.dev

Portfolio site for Ali Asif. Single static page (`index.html`), no build step, no dependencies to install.

## 1. Filling in your content

Every placeholder is numbered so you can reference it directly (e.g. "fill in Placeholder 8" or "here's the file for Image Placeholder 3"). There are two kinds:

- **`[PLACEHOLDER N - ...]`** — text: bios, descriptions, dates, links, tech-stack badges, captions. Numbered 1–35, in the order they appear on the page.
- **`[IMAGE PLACEHOLDER N - ...]`** — a photo/screenshot/poster slot shown as a dashed box. Numbered 1–11, separately from the text ones.

1. Open `index.html` in any text editor.
2. Press **Ctrl+F** and search for `PLACEHOLDER` to jump through every spot that needs real content, or just look for the placeholder number you're working on.
3. Replace the bracketed text with your own copy. You can also remove `class="placeholder"` from that element if you want normal (non-italic, non-gray) styling right away.

### Adding images

1. Drop your image files directly in this folder (next to `index.html`), or in the `images/` folder — either works, just keep the path consistent.
2. Find the matching `<div class="img-placeholder">...</div>` block (labeled `IMAGE PLACEHOLDER N`) in `index.html` and replace it with a real `<img>`, wrapped in a link to the same file so visitors can click it open full-size in a new tab:

   ```html
   <a href="images/poster_cu.png" target="_blank" rel="noopener noreferrer" aria-label="Open full-size image in a new tab">
     <img src="images/poster_cu.png" alt="CU Boulder EMG research poster" loading="lazy" style="border-radius:10px;border:1px solid var(--color-border);cursor:zoom-in;">
   </a>
   ```

3. What each image placeholder is for:
   - **Image Placeholder 1** — `poster_cu.png`, CU Boulder research poster
   - **Image Placeholder 2** — `poster_quantum.png`, ACC quantum research poster
   - **Image Placeholder 3 / 4** — `athltc_1.png`, `athltc_2.png`, ATHLTC app screenshots
   - **Image Placeholder 5** — second project's screenshot
   - **Image Placeholder 6–11** — the six Gallery photos (any filenames you like)
   - `quantum_paper.pdf` and `Ali_Asif_Resume.pdf` are linked as text (Placeholder 6 and Placeholder 34), not image boxes — just drop the files in and the links will work once named correctly.

### Showing/hiding the second project card

The second project card (`id="project-card-b"` in the Projects section) is visible by default. To hide it until you're ready, add the class `project-hidden` to its `<article>` tag:

```html
<article class="card project-hidden" id="project-card-b">
```

To show it again, remove that class.

## 2. Previewing locally

Just double-click `index.html` to open it in your browser — no server required. (Opening it directly as a file:// URL works fine here since there's no JS that needs a server.)

## 3. Deploying to GitHub Pages

1. **Create a GitHub repository.** Go to [github.com/new](https://github.com/new) and create a repo (any name works, e.g. `aliasif-portfolio`). It can be public or private — GitHub Pages works with both on a free account as long as the repo itself is public (Pages publishing from a private repo requires GitHub Pro).
2. **Push this folder to it:**

   ```bash
   git init
   git add .
   git commit -m "Initial portfolio site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```

3. **Enable Pages:** In the repo, go to **Settings → Pages**. Under "Build and deployment", set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
4. GitHub will build and publish the site at `https://<your-username>.github.io/<your-repo>/`. It can take a minute or two the first time.

## 4. Connecting your custom domain (aliasif.dev)

You already own the domain. Two things need to happen: GitHub needs to know about the domain, and your domain registrar's DNS needs to point at GitHub.

### A. Tell GitHub about the domain

1. In the repo, go to **Settings → Pages**.
2. Under "Custom domain", enter `aliasif.dev` and click **Save**. GitHub will commit a `CNAME` file containing `aliasif.dev` to your repo root automatically (this repo already includes one, so this step just confirms it in the UI).
3. Leave this tab open — you'll come back to check "DNS check successful" after step B.

### B. Point your domain's DNS at GitHub Pages

Log in to whichever registrar you bought the domain from (Porkbun, Namecheap, GoDaddy, etc. — the steps are the same idea everywhere, just in a different-looking dashboard). Find the **DNS records** or **DNS management** page for `aliasif.dev`.

You're setting up the **apex/root domain** (`aliasif.dev`, no `www`). Add these four **A records**, all with host/name left blank (or `@`):

| Type | Host | Value           |
|------|------|-----------------|
| A    | @    | 185.199.108.153 |
| A    | @    | 185.199.109.153 |
| A    | @    | 185.199.110.153 |
| A    | @    | 185.199.111.153 |

If you also want `www.aliasif.dev` to work and redirect to the apex domain, add one more record:

| Type  | Host | Value                       |
|-------|------|------------------------------|
| CNAME | www  | `<your-username>.github.io` |

**On Porkbun specifically:** go to your domain's **DNS** tab, delete any existing `A` or `ALIAS`/`CNAME` records on the root/`@` host that conflict, then add the records above one at a time using "Add Record".

### C. Wait and verify

- DNS changes can take anywhere from a few minutes to ~24 hours to propagate.
- Back in GitHub's **Settings → Pages**, you should eventually see "DNS check successful" next to your custom domain.
- Once it does, check **Enforce HTTPS** so visitors get `https://aliasif.dev` with a valid certificate (GitHub issues this automatically via Let's Encrypt — can take a few more minutes after DNS verifies).
- Visit `https://aliasif.dev` to confirm.

### Troubleshooting

- If GitHub says the DNS check failed, double check the four A record IPs are entered exactly and that there isn't a leftover "parked domain" A record from your registrar still pointing elsewhere.
- Some registrars don't allow a `CNAME` on `www` alongside other `www` records — remove conflicting ones first.
- You can confirm propagation from your own machine with:

  ```bash
  nslookup aliasif.dev
  ```

  It should eventually return the four `185.199.10x.153` addresses.

## File structure

```
aliasif-portfolio/
├── index.html          # the entire site
├── CNAME                # tells GitHub Pages the custom domain
├── images/              # put your images/screenshots/posters here (optional location)
├── Ali_Asif_Resume.pdf   # add this yourself — linked from the Resume section
└── README.md            # this file
```
