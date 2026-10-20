# Isoline — notes for AI coding agents

One HTML file: markup, inline CSS and inline scripts; GSAP with ScrollTrigger and SplitText, Lenis smooth scroll, all from jsDelivr. No build step, no framework.

## Files
Work from the files: a page read through a link comes back as a summary, and a page rebuilt from it would differ.
```bash
curl -LO https://raw.githubusercontent.com/8bsite/coworking-website-template/main/index.html
curl -LO https://raw.githubusercontent.com/8bsite/coworking-website-template/main/AGENTS.md
curl -LO https://raw.githubusercontent.com/8bsite/coworking-website-template/main/LICENSE
curl -LO https://raw.githubusercontent.com/8bsite/coworking-website-template/main/CREDITS.md
```
In Windows PowerShell type `curl.exe`. Publish `index.html` with LICENSE and CREDITS.md; this file, README.md and `previews/` are not part of the site.

## Do not break
- Keep it one file unless the user asks otherwise; no framework or bundler for copy, colour or photo changes.
- Keep the ids and the `data-8b-section` / `data-8b-motion` attributes. Each section has its styles in `<style data-8b-part="section:<id>">` and its animation, if any, in `<script data-8b-part="scene:<id>">`.
- The scripts find these classes and attributes; when you change a section's markup, keep them or update the script:
  - `section-script:navigation`: `.nav__menu` `.nav__close` `.nav__overlay`
  - `section-script:visit`: `.visit__form` `.visit__status` `data-sent` `data-missing`
  - `scene:opening-fall`: `.opening__stage` `.opening__well` `.m-well__band` `.opening__figure-move` `.opening__second` `data-line` `.opening__copy`
  - `scene:depths-lower`: `.depths__wall` `.depths__item` `.depths__hang` `.m-print` `.m-well__band`
  - `scene:day-dial`: `.day__well` `.day__list` `.day__row` `.m-well__band`
  - `scene:rules-dig`: `.rules__stage` `.rules__row`
  - `scene:evenings-surface`: `.evenings__row` `.evenings__date`
  - `scene:plans-deepen`: `.plan__well` `.m-well__band`
- Colours, fonts, radii and shadows are CSS variables in the `:root` block (`data-8b-part="tokens"`); change them there and keep body text at 4.5:1 contrast or more.
- Animations run only when the visitor allows motion (`prefers-reduced-motion: no-preference`); the page must stay readable without them.
- A display line with `style="--len:N"` is sized to fill its width: N is its number of characters, spaces included (`Isoline` → 7).
- Keep the header comment and `<meta name="generator">`. Keep the "Design: 8B" footer link unless the site owner asks to remove it.

## Replace before publishing
- Everything marked `data-8b-placeholder` (og-image, favicon, phone, email, form); remove the attribute once the real value is in. With no real value: no preview image — delete the `og:image` tag and set `twitter:card` to `summary`; no phone, email or address — remove that link or row.
- Book a day (nav) and Book a day pass (opening): link to #plans now; point them to your booking or day-pass URL (or keep #plans).
- Plan buttons (Book a day, Become a member, Ask about a carrel): link to #visit now; point them to the booking, checkout or membership sign-up URL of each plan.
- Save a seat on each evening talk: link to #visit now; point them to the RSVP or ticket URL of each event.
- **The form sends nothing.** `section-script:visit` checks the fields and shows a thank-you message without sending. Pick one:
  - Formspree: set `action="https://formspree.io/f/<id>"` on the form; in the script, before the thank-you message, `await fetch(form.action, { method: 'POST', body: new FormData(form), headers: { Accept: 'application/json' } })` and show it only if the response is ok.
  - Netlify Forms (site on Netlify): add `name="contact" data-netlify="true"` and `<input type="hidden" name="form-name" value="contact">`; send with `fetch('/', { method: 'POST', headers: { 'Content-Type': 'application/x-www-form-urlencoded' }, body: new URLSearchParams(new FormData(form)) })`.
  - No form service: remove the `<form>` together with the script that handles it (it would fail without the form) and keep the email link.
- Invented demo facts (ask the user for the real ones; do not make up prices, dates or addresses):
  - Address "14 Wren Yard, Leeds LS2 7EW" (visit, the map label, footer) and the company name "Isoline Workrooms Ltd." (footer): invented, the postcode may be real.
  - Phone +44 113 000 0000 and email hello@isoline.example (visit, footer "Email us").
  - Opening hours: weekdays 7:30 to 21:00, residents every day (visit, footer), and the whole daily schedule 7:30, 9:00, 10:30, 13:30, 15:00, 18:30, 21:00 with booths held for three hours (the day).
  - Prices in euros although the address is in the UK: Day pass €24 a day, Member €190 a month, Resident €340 a month, and what each includes: levels, roof lunch, bookable a week ahead, two booth blocks a week, Thursday evenings, own carrel, a key seven days, a locker (plans).
  - Capacity and building: three floors, a roof open "from spring to the first frost", forty seats at two oak tables, twenty-two carrels and six sealed booths, lockers on the landing (rooms, depths, rules), "two hundred members" (members).
  - People and quotes: Ines Varga, Maren Holt, Teodor Lund, Arun Desai with jobs, quotes and details ("Booth four", "two winters", "At eighty-one", "leave at four") (members, evenings, made); also Pell Okafor and Lise Brandt (made).
  - Works listed as finished in the building: The Salt Year, Small Hours (eight tracks), Where the Fox Sleeps, Tidewater Grotesk (four weights), The Collected Letters of R. Anand, Soil Memory (made).
  - Events: talks on 16 Oct, 23 Oct, 30 Oct and 6 Nov, Thursdays at 18:30, twenty-minute talks, with titles, speakers and places (evenings, and "on Thursdays" in the day).
  - Service promises: a tour "in fifteen minutes" (visit) and "We will write within a day" (the data-sent message on .visit__status).
  - Copyright year 2026 (footer).
- `<title>`, the meta description and the og tags; photos (Unsplash, see CREDITS.md) when the user has their own.

## Notes
- The colour fields, posters, dial, rules well and contour map are SVG and CSS, not images: the three depth colours (orange, blue, violet) come from the :root colour variables, so recolour them there.
- Person photos are printed with multiply onto the fields: use photos on a white or very light ground, or the background will show as a box.
- Without JavaScript the phone menu button cannot open the overlay; the links stay reachable in the opening and the footer.
- The map in visit is a drawing, not a real map: add a link to your map service if visitors need directions.
- Faces that overlap the middle of a colour field take its tint (photos are printed with multiply).

## Common edits
- Rebrand: search the old name (`Isoline`) in any letter case and replace every match; change the favicon letter and colours in `<link rel="icon">`.
- Photos: replace `src` and delete `srcset` and `sizes` (they list Unsplash sizes), keep `width`/`height` to the new photo's ratio, update `alt` and CREDITS.md.
- Remove a section: delete its markup, its `section:<id>` and `scene-style:<id>` styles, its `scene:<id>` and `section-script:<id>` scripts, and links to `#<id>`.
- Native scroll instead of smooth scroll: delete the Lenis block in `page-init` and the Lenis `<script>` tag.

## Check and publish
- Open the page at 375 and 1440 px, with reduced motion on, with the console open.
- Search `data-8b-placeholder` and the old name: nothing should be left but class names.
