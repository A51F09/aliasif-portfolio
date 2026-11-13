# Deferred / Removed Content

Things taken off the live site temporarily, kept here verbatim so they're trivial to paste back in. Nothing is lost — just off the page for now while the site gets hosted quickly.

---

## Removed 2026-11-06 — "Read Paper (PDF)" link (Quantum Chip Research card)

Removed because the paper isn't written yet. To restore: drop the finished PDF in this folder (suggested name `quantum_paper.pdf`), then add this link back into the `card-links` div of the quantum research card (in the Research section of `index.html`), right before the GitHub Repo link:

```html
<a href="quantum_paper.pdf" target="_blank" rel="noopener noreferrer">Read Paper (PDF) →</a>
```

---

## Restored 2026-11-13 — Projects section

The Projects section (noted below as removed on 2026-11-06) is back, now with real ATHLTC content: full description, real tech stack badges, a link to athltc.app, and a status line. Only the 4 screenshot slots are still open (Image Placeholders 1-4) — drop in `athltc_1.png` through `athltc_4.png` (or however many you have) and swap each `img-placeholder` div for a real `<img class="zoomable" data-group="athltc" ...>` tag, same pattern used elsewhere on the site (see the README's "Adding images" section). The old generic "second project" card was dropped rather than restored — add a new card manually if/when there's a second project to show.

---

## Removed 2026-11-07 — Resume section + nav link

Removed temporarily to ship version 1. To restore:

1. Add this link back into the nav, as the last item (after "Gallery"):

   ```html
   <a href="#resume">Resume</a>
   ```

2. Add this whole section back into `index.html`, right before the closing `</main>` tag:

```html
  <section id="resume">
    <div class="wrap">
      <h2>Resume</h2>
      <a class="resume-btn" href="Ali_Asif_Resume.pdf" download>
        <svg viewBox="0 0 16 16" width="18" height="18" fill="currentColor" aria-hidden="true"><path d="M8 11.5 4 7.5l1.06-1.06L7.25 8.6V1h1.5v7.6l2.19-2.16L12 7.5 8 11.5zM2 13.5h12V15H2v-1.5z"/></svg>
        Download Resume
      </a>
      <p class="placeholder" style="margin-top:12px;">[PLACEHOLDER - Upload resume as Ali_Asif_Resume.pdf in this directory]</p>
    </div>
  </section>
```

The `.resume-btn` CSS rule is still in `index.html` (untouched), so the button will look right as soon as the markup is back.
