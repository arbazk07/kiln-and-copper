# Kiln & Copper 🔥

A one-page marketing site for **Kiln & Copper**, a fictional wood-fired, downtown restaurant. Built as a single self-contained HTML file — no build step, no dependencies, no backend.

**Demo site — built for preview purposes.**

## Features

- Animated hero with a live `<canvas>` ember/fire effect
- Custom cursor (desktop only; falls back to the system cursor on mobile)
- Scroll-triggered reveal animations via `IntersectionObserver`
- Sections: hero, story, menu, gallery, testimonials, reservations
- Reservation form (front-end only — see [Reservation form](#reservation-form) below)
- Sticky "Book a Table" CTA
- Responsive layout, mobile nav menu
- Fonts: [Fraunces](https://fonts.google.com/specimen/Fraunces), [Work Sans](https://fonts.google.com/specimen/Work+Sans), [Space Mono](https://fonts.google.com/specimen/Space+Mono), loaded from Google Fonts
- Images loaded from Unsplash via hotlinked URLs

## Tech stack

Plain HTML, CSS, and vanilla JavaScript. Everything lives in `ember-and-salt.html` — one file, no npm packages, no framework.

## Local preview

Since there's no build process, you can just open the file directly:

```bash
open ember-and-salt.html
```

Or serve it locally (recommended, so relative paths and fonts behave the same as in production):

```bash
npx serve .
```

## Deploying to Vercel

This is a static file, so deployment needs no configuration:

1. Push this repo to GitHub.
2. In Vercel, click **Add New → Project** and import the repo.
3. Framework preset: **Other** (or leave as detected).
4. Leave the build command empty and set the output directory to `.`
5. Deploy.

If you want `/` to load the page automatically, either rename the file to `index.html`, or add a `vercel.json` rewrite:

```json
{
  "rewrites": [{ "source": "/", "destination": "/ember-and-salt.html" }]
}
```

## Reservation form

The **Reserve a table** form calls a `handleReserve(event)` JS function on submit. It currently only runs client-side logic (e.g. preventing default submission / showing a confirmation state) — **it does not send data anywhere**. Before using this in production you'll want to wire it up to a real backend, for example:

- A serverless function (Vercel Functions / API routes)
- A form service like Formspree, Basin, or Getform
- A reservations platform (OpenTable, Resy, Tock, etc.)

## Customizing

All copy, prices, hours, and contact info are hardcoded directly in the HTML — search for the relevant `<section id="...">` block to edit:

| Section | id |
|---|---|
| Hero | `.hero` |
| Story | `#story` |
| Menu | `#menu` |
| Gallery | `#gallery` |
| Testimonials | `#testimonials` |
| Reservations | `#reserve` |

Colors and design tokens are defined as CSS custom properties at the top of the `<style>` block (`--void`, `--linen`, `--gold`, `--copper`, `--wine`, etc.).

## License

Add a license of your choice, or mark this repo private if it's just for internal preview/demo use.
