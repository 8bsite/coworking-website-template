# Free HTML coworking website template with GSAP scroll animations — Isoline

**Website for a coworking space or members' workspace, with day passes and memberships: a free HTML template in one file, with GSAP scroll animations, no build step, MIT license. Made by [8B](https://8b.com/), the AI website builder.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE) ![one HTML file: no build](https://img.shields.io/badge/one%20HTML%20file-no%20build-orange) ![GSAP: ScrollTrigger](https://img.shields.io/badge/GSAP-ScrollTrigger-88ce02)

**[Live demo](https://8bsite.github.io/coworking-website-template/)** · **[Use this template](https://github.com/new?template_name=coworking-website-template&template_owner=8bsite)** · **[Download ZIP](https://github.com/8bsite/coworking-website-template/archive/refs/heads/main.zip)**

<a href="https://8bsite.github.io/coworking-website-template/"><img src="previews/desktop.png" alt="Isoline, a free HTML template: first screen on a desktop" width="76.1%"></a> <a href="https://8bsite.github.io/coworking-website-template/"><img src="previews/phone.png" alt="Isoline, a free HTML template: first screen on a phone" width="21.9%"></a>

<p align="center"><a href="https://8bsite.github.io/coworking-website-template/"><img src="previews/scroll.gif" alt="Isoline, a free HTML template: scrolling through the first sections on a desktop" width="40%"></a><br><sub>Scroll animation</sub></p>

A one-page site for an invented members' workspace in Leeds with three floors, from a talkative roof down to silent study carrels. Big colour fields of nested stepped bands, like contour lines, mark each floor's depth in orange, blue and violet; on the first scroll you fall into the blue field, prints drop on their wires and the bands fill and open as you read on.

Good for: coworking space or shared office; quiet study space, library or writers' room; members' club with day passes and memberships; any venue with floors, zones or levels to explain. Free for personal and commercial use (MIT), made by [8B](https://8b.com/).

## Quick start

Pick one:

- **With an AI coding agent** (Claude Code, Codex, Cursor, Windsurf…). Download the files into your project (in Windows PowerShell type `curl.exe`):
  ```bash
  curl -LO https://raw.githubusercontent.com/8bsite/coworking-website-template/main/index.html
  curl -LO https://raw.githubusercontent.com/8bsite/coworking-website-template/main/AGENTS.md
  curl -LO https://raw.githubusercontent.com/8bsite/coworking-website-template/main/LICENSE
  curl -LO https://raw.githubusercontent.com/8bsite/coworking-website-template/main/CREDITS.md
  ```
  Then give your agent this prompt:
  ```text
  Read AGENTS.md, then edit index.html. Use this template as the base for a site for <your coworking space or workspace: name, city, floors or zones, opening hours, prices, events, how to book>. Keep the layout, the motion and the single-file format; replace the brand name, copy, photos, prices, dates, member names, links and contacts, and recolour it through the CSS variables if needed.
  ```
  Give the agent the downloaded file, not a link: an agent reads a link as a summary and would rebuild a different page.
- **No code.** Download the ZIP, unzip it, replace the contacts and texts in `index.html`, put `index.html` into an empty folder and drag that folder onto [Netlify Drop](https://app.netlify.com/drop). The page is online in a minute.
- **On GitHub.** Click **[Use this template](https://github.com/new?template_name=coworking-website-template&template_owner=8bsite)** to get your own copy, then **Settings → Pages → Deploy from a branch → main**. Your site appears at `https://<you>.github.io/<repo>/`.

## What's on the page

- **Navigation** — top bar: wordmark, section links, Book a day button; phone menu overlay
- **Work at your own depth.** — two screens: headline over a huge colour field with a figure on its edge, then a statement and three anchors on the field's colour
- **Three depths. Pick one each morning.** — three hanging posters, one per zone or level, each with its own colour field, photo and caption (demo: the three floors)
- **The building has a day of its own.** — daily schedule beside a sticky colour dial (demo: a weekday from 7:30 to 21:00)
- **Rooms, in order of descent.** — list of rooms indented by level, each with a small hanging photo
- **Three rules, posted at the stairs.** — three short house rules inside a V-shaped cross-section of bands
- **Who works down here.** — four members with photo, name, job and a quote, each under a small colour field
- **Surfacing, on Thursday evenings.** — list of upcoming events with date, time, title, speaker, place and a Save a seat link (demo: Thursday talks)
- **Finished at depth.** — table of works members finished, each with a small stepped colour swatch
- **How deep a membership goes.** — three pricing plans as colour fields whose band count shows how much each includes
- **Come down for a day.** — contact: address, hours, phone, email, a drawn contour map and a tour request form (placeholders)
- **Footer** — tagline with address, links, wordmark, copyright and the Design: 8B credit, hours line

## Before you publish

- Replace everything marked `data-8b-placeholder` (social preview image, favicon, phone, email, form) and the invented demo facts — prices, dates, address. [AGENTS.md](AGENTS.md) lists them.
- The contact form does not send anything yet: connect it to a form service (Formspree, Netlify Forms) or remove it; [AGENTS.md](AGENTS.md) shows both.

## Customize

- **Colours and fonts**: CSS variables in the `:root` block at the top of `<head>`.
- **Text**: edit it in place. A big display line with `style="--len:N"` fills its width: set N to its new number of characters.
- **Photos**: replace `src`, delete `srcset` and `sizes` (they list Unsplash sizes) and update the `alt` texts.
- **Animations**: each section's animation is one `<script data-8b-part="scene:<id>">` block at the end of the file. For native scroll, delete the Lenis block in `page-init`.

## For developers

- **Stack.** HTML and CSS (custom properties, cascade layers) with GSAP 3.13.0, ScrollTrigger, SplitText, Lenis 1.3.27 from jsDelivr. No build step, no framework, no npm. 153 KB.
- **Layout of the file.** `<head>`: CSS variables, shared classes, then one style block per section. Then the markup, one element per section with a one-line comment above it. End of `<body>`: small behaviour scripts, the libraries, smooth scroll (`page-init`), the effects, one animation script per section.
- **Browsers.** Chrome and Edge 111+, Safari 16.2+, Firefox 113+ (it uses color-mix(), cascade layers).
- **Accessibility.** Motion runs only when the visitor's system allows it; with "reduce motion" the page is complete and still. Every photo has alt text.
- **External requests.** fonts.gstatic.com, images.unsplash.com, cdn.jsdelivr.net. No analytics, no cookies. To self-host everything (offline use, or Google Fonts and GDPR in the EU), download those files and change the URLs.
- **Licences of the parts.** GSAP is free, commercial use included, under its own standard licence (not MIT); Lenis is MIT; fonts are SIL OFL; photos are under the Unsplash License. See [CREDITS.md](CREDITS.md).

## FAQ

**Can I use it for a client or a commercial site?** Yes. The code is MIT: use it, change it, sell the site you build with it.

**Do I have to keep the "Design: 8B" link?** No. It is welcome, not required.

**Can I use it in React, Next.js, Astro or Vue?** Yes. Move each section's markup and style block into a component and run its animation script in `useGSAP()` (React) or `onMounted` (Vue); start Lenis once. Or keep it as a separate static landing page next to your app (`example.com` for the landing, `app.example.com` for the app).

**Why doesn't the contact form send?** It is a demo. Connect it to Formspree, Netlify Forms or your backend; AGENTS.md has the steps.

**Where are the photos from?** Unsplash; they load from Unsplash's servers. Replace them with your own when you can.

## More free templates

[More 8B templates on GitHub](https://github.com/8bsite) · [8b.com](https://8b.com/)

## License

The template code is MIT licensed — see [LICENSE](LICENSE). Photos, fonts and libraries keep their own licences — see [CREDITS.md](CREDITS.md).
