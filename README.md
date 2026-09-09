# Digital Dependencies — Workshop Website

International Workshop at the University of Bonn
**Digital Dependencies from an International Perspective: On the Way to Global Digital Sovereignty**
21–22 October 2026

Built with [Hugo](https://gohugo.io). The design is a custom theme built
directly into this project — there is **no external theme to download**, so
setup is simpler than a standard Hugo site.

## Setup

1. Make sure Hugo Extended is installed (you already did this:
   `winget install Hugo.Hugo.Extended`).
2. Open PowerShell in this folder.
3. Preview the site locally:
   ```
   hugo server
   ```
   Then open http://localhost:1313 in your browser. That's it — no
   `git init`, no submodules needed.

## Editing content

All page content lives in `content/` as Markdown (`.md`) files. Open them in
any text editor and replace the `[bracketed placeholders]` with real content.

- `content/_index.md` is NOT used for text — the homepage text lives in the
  template `layouts/index.html` (edit the paragraphs there).
- `content/keynotes/_index.md` — Keynotes & Speakers
- `content/programme/_index.md` — Programme (see below)
- `content/venue/_index.md` — Venue & Directions (Google Maps embed)
- `content/registration/_index.md` — Registration (Google Form embed)
- `content/team/_index.md` — Organisers
- `content/contact/_index.md` — Contact

### Editing the programme

The schedule is data-driven. Open `content/programme/_index.md` — the whole
timetable sits in the front matter (the part between the `---` lines) as a
list of `days`, each with `items`. Each session item looks like this:

```yaml
- time: "14:00 – 15:30"
  kind: "Panel I"
  title: "How to Measure Digital Dependence"
  people:
    - "Yen-Chi Lu, University of Bonn"
    - "Prof. Dr. Maximilian Mayer, University of Bonn"
  moderation: "Moderation: Nathalie Brandmayr, Vodafone Institute"
```

A coffee/lunch break is just:

```yaml
- time: "15:30 – 16:00"
  type: "break"
  label: "Coffee break"
```

Add `highlight: true` to a session to accent its title (used for keynotes
and the public panel). To mark something unconfirmed, wrap it like this
inside any text: `<span class='tbc'>(tbc)</span>`.

## Changing the look

- Colours, fonts, and spacing are all defined at the top of
  `assets/css/main.css` in the `:root { ... }` block. Change a hex value
  there and it updates everywhere.
- The logos in the header/footer are in `static/images/logos/`. To resize
  the header logos, edit the `.logo-strip img` height in `assets/css/main.css`.
- The homepage hero text is in `layouts/index.html`.

## Site settings

Global settings (title, dates, menu, contact email) are in `hugo.yaml`.

## Publishing (free, via GitHub Pages)

1. Create a free GitHub account and a new repository.
2. Push this project to it:
   ```
   git init
   git add .
   git commit -m "Initial workshop site"
   git branch -M main
   git remote add origin https://github.com/YOUR-NAME/YOUR-REPO.git
   git push -u origin main
   ```
3. In the repo on GitHub: Settings → Pages → "Build and deployment" →
   Source → **GitHub Actions**. GitHub will suggest a Hugo workflow —
   accept it. Every push then rebuilds and republishes the site
   automatically.

## Adding a custom domain later (optional)

Once you have a domain (e.g. a `.org` or a University of Bonn subdomain),
add a file named `CNAME` (no extension) inside the `static/` folder
containing just your domain, then point the domain's DNS to GitHub Pages.
See GitHub's custom-domain documentation for the exact DNS records.

## Before going live — checklist

- [ ] Replace the Google Form link on the Registration page
- [ ] Confirm the Google Maps embed on the Venue page
- [ ] Fill in the main venue building/room once known
- [ ] Check and complete the Organisers list and roles
- [ ] Update the contact email (currently workshop@uni-bonn.de)
- [ ] Set the real `baseURL` in hugo.yaml before publishing
