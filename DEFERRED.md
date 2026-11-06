# Deferred / Removed Content

Things taken off the live site temporarily, kept here verbatim so they're trivial to paste back in. Nothing is lost — just off the page for now while the site gets hosted quickly.

---

## Removed 2026-11-06 — "Read Paper (PDF)" link (Quantum Chip Research card)

Removed because the paper isn't written yet. To restore: drop the finished PDF in this folder (suggested name `quantum_paper.pdf`), then add this link back into the `card-links` div of the quantum research card (in the Research section of `index.html`), right before the GitHub Repo link:

```html
<a href="quantum_paper.pdf" target="_blank" rel="noopener noreferrer">Read Paper (PDF) →</a>
```

---

## Removed 2026-11-06 — Projects section (ATHLTC + second project card)

Removed temporarily to get the site live faster. To restore:

1. Add this link back into the nav, between "Research" and "Experience":

   ```html
   <a href="#projects">Projects</a>
   ```

2. Add this whole section back into `index.html`, between the closing `</section>` of `id="research"` and the opening `<section id="experience">`:

```html
  <section id="projects">
    <div class="wrap">
      <h2>Projects</h2>
      <div class="card-grid">

        <article class="card">
          <h3>ATHLTC</h3>
          <p class="card-role">Co-founder &amp; Lead Developer</p>
          <p class="placeholder">[PLACEHOLDER - 2-3 sentences about the fitness app. Suggested talking points: progressive overload tracking, Ramadan Fasting mode, AI integration via API, social features, team of three developers]</p>
          <div class="badges">
            <span class="badge placeholder">[PLACEHOLDER - tech stack, e.g. React Native]</span>
            <span class="badge placeholder">[PLACEHOLDER]</span>
            <span class="badge placeholder">[PLACEHOLDER]</span>
          </div>
          <div class="screenshot-row">
            <div class="img-placeholder" role="img" aria-label="Image placeholder: ATHLTC screenshot 1">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" aria-hidden="true"><rect x="3" y="5" width="18" height="14" rx="2"/><circle cx="8.5" cy="10.5" r="1.5"/><path d="M21 15l-5-5-4 4-2-2-5 5"/></svg>
              [IMAGE PLACEHOLDER - athltc_1.png]
            </div>
            <div class="img-placeholder" role="img" aria-label="Image placeholder: ATHLTC screenshot 2">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" aria-hidden="true"><rect x="3" y="5" width="18" height="14" rx="2"/><circle cx="8.5" cy="10.5" r="1.5"/><path d="M21 15l-5-5-4 4-2-2-5 5"/></svg>
              [IMAGE PLACEHOLDER - athltc_2.png]
            </div>
          </div>
          <div class="card-links">
            <a href="[PLACEHOLDER - Add repo URL]" target="_blank" rel="noopener noreferrer">GitHub Repo →</a>
          </div>
        </article>

        <article class="card" id="project-card-b">
          <h3 class="placeholder">[PLACEHOLDER - Add another project title, e.g. AI Daytrading Bot, personal CLI tool, etc.]</h3>
          <p class="card-role placeholder">[PLACEHOLDER - role]</p>
          <p class="placeholder">[PLACEHOLDER - 2-3 sentences]</p>
          <div class="badges">
            <span class="badge placeholder">[PLACEHOLDER - tech stack]</span>
          </div>
          <div class="img-placeholder" role="img" aria-label="Image placeholder: second project screenshot">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" aria-hidden="true"><rect x="3" y="5" width="18" height="14" rx="2"/><circle cx="8.5" cy="10.5" r="1.5"/><path d="M21 15l-5-5-4 4-2-2-5 5"/></svg>
            [IMAGE PLACEHOLDER]
          </div>
          <div class="card-links">
            <a href="[PLACEHOLDER]" target="_blank" rel="noopener noreferrer">GitHub Repo →</a>
          </div>
        </article>

      </div>
    </div>
  </section>
```

Note: when this comes back, every placeholder in it will need fresh numbers (whatever comes next after the current highest number in `index.html` at the time), and the rest of the page's placeholder numbers won't need to change — only newly-reintroduced ones get added at the end, same approach as filling in any other placeholder.

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
