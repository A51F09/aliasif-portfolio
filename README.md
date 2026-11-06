# aliasif.dev

Portfolio site for Ali Asif. Single static page (`index.html`), no build step, no dependencies to install.

**Note:** some sections (like Projects) are temporarily removed to get the site hosted quickly. See [DEFERRED.md](DEFERRED.md) for everything that's been taken out and exactly how to put it back.

## 1. Filling in your content

Every placeholder is numbered so you can reference it directly (e.g. "fill in Placeholder 8" or "here's the file for Image Placeholder 3"). There are two kinds:

- **`[PLACEHOLDER N - ...]`** — text: bios, descriptions, dates, links, tech-stack badges, captions. Currently numbered 2, 16–23 (lower numbers are already filled in and won't show as brackets anymore — gaps are expected).
- **`[IMAGE PLACEHOLDER N - ...]`** — a photo/screenshot/poster slot shown as a dashed box. Currently numbered 3–8, separately from the text ones (1 and 2 are already filled).

1. Open `index.html` in any text editor.
2. Press **Ctrl+F** and search for `PLACEHOLDER` to jump through every spot that needs real content, or just look for the placeholder number you're working on.
3. Replace the bracketed text with your own copy. You can also remove `class="placeholder"` from that element if you want normal (non-italic, non-gray) styling right away.

### Adding images

1. Drop your image files directly in this folder (next to `index.html`), or in the `images/` folder — either works, just keep the path consistent. Prefer `.png` or `.jpg` over `.webp` for anything important — more universally supported.
2. Find the matching `<div class="img-placeholder">...</div>` block (labeled `IMAGE PLACEHOLDER N`) in `index.html` and replace it with a real `<img>` tag. Add `class="zoomable"` so clicking the image opens it full-size in an in-page lightbox (not a new tab):

   ```html
   <img class="zoomable" src="images/poster_cu.png" alt="CU Boulder EMG research poster" loading="lazy">
   ```

   The lightbox itself (markup, CSS, and a small vanilla-JS script) is already wired up at the bottom of `index.html` — any `<img class="zoomable">` anywhere on the page gets the click-to-enlarge behavior automatically, no extra setup needed per image.

   To make a **scrollable mini-gallery** out of several images (like the CU Boulder research card has), give each image the same `data-group="some-name"` attribute. The lightbox will then show prev/next arrows and a counter so visitors can page through that whole set without closing it:

   ```html
   <p class="poster-gallery-label">Gallery</p>
   <div class="poster-gallery">
     <img class="zoomable" data-group="my-group" src="images/photo1.png" alt="..." loading="lazy">
     <img class="zoomable" data-group="my-group" src="images/photo2.png" alt="..." loading="lazy">
   </div>
   ```

   The `poster-gallery` wrapper makes the row horizontally scrollable with its own thumbnails; the `data-group` value just needs to match across the images you want grouped together (the quantum research card doesn't use this yet — it's still a single image).

3. What each image placeholder is for:
   - **Image Placeholder 1** (already filled) — CU Boulder research poster
   - **Image Placeholder 2** (already filled) — ACC quantum research poster
   - **Image Placeholder 3–8** — the six Gallery photos (any filenames you like)
   - The Resume section is currently removed (see [DEFERRED.md](DEFERRED.md)) — once it's back, `Ali_Asif_Resume.pdf` will be linked as text there, not an image box.

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
├── Ali_Asif_Resume.pdf   # add this once the Resume section is restored (see DEFERRED.md)
├── DEFERRED.md           # content temporarily removed from the site, kept verbatim for later
└── README.md            # this file
```
