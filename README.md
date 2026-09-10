# Jason's Wood Refinishing — Website

A static (no backend) marketing website: plain HTML, CSS, and a little JS.

## Folder structure

```
index.html        Home
services.html      Services detail
gallery.html       Before / after gallery
about.html         About page
contact.html       Contact page + quote form
thank-you.html     Shown after a successful form submission
css/style.css      One shared stylesheet for the whole site
js/script.js       Mobile nav toggle + small helpers
images/placeholders/placeholder.svg   Generic stand-in graphic used everywhere a real photo is needed
robots.txt, sitemap.xml               Basic SEO files
```

There's no build step — just open the `.html` files in a browser, or serve
the folder with any static host (see **Deploying** below).

## 1. Finish setting up the contact form (Formspree)

The contact form on `contact.html` is wired to **Formspree**, a free
service that emails form submissions without needing your own server.

1. Go to https://formspree.io and sign up using `vanassejason@gmail.com`.
2. Create a new form. Set the notification email to `vanassejason@gmail.com`.
3. Formspree will give you a form endpoint like `https://formspree.io/f/abcdwxyz`.
4. Open `contact.html`, find this line near the top of the `<form>`:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```
   and replace `YOUR_FORM_ID` with your real ID.
5. Publish the site, submit one test message from the live form — Formspree
   requires a one-time confirmation click on the first submission before it
   starts forwarding emails.

That's it — no API keys, no JS SDK, no server required.

## 2. Add real photos

Everywhere you see `images/placeholders/placeholder.svg` in the code, it's
a stand-in graphic (a labeled "PHOTO PLACEHOLDER" box) marking a spot for a
real photo. To swap one in:

1. Add your photo to an `images/` subfolder (e.g. create `images/gallery/`,
   `images/hero/`, etc. — organize however makes sense to you).
2. Update the `src="..."` attribute on that `<img>` tag to point to your
   new file.
3. Update the `alt="..."` text to describe the *real* photo (each one
   currently has a placeholder description ending in
   "— PLACEHOLDER, replace with real photo").

The homepage hero background is the one exception — it's a CSS gradient,
not an `<img>`. To use a real photo there instead, see the comment inside
`css/style.css` under `.hero`.

Search the project for the word `PLACEHOLDER` (or `TODO`) to find every
spot that's expecting real content later — every code editor's
"Find in Files" (Ctrl+Shift+F in VS Code) will list them all at once.

## 3. Other things to review before going fully live

- **Services list** — the site currently lists: Furniture Refinishing,
  Cabinet Refinishing, Deck Restoration, Antique Restoration, Custom
  Staining & Finishing, and Wood Repair. Confirm this matches what Jason
  actually offers and adjust wording on `index.html` and `services.html`.
- **About page bio** — `about.html` has a generic placeholder story/bio.
  Replace it with Jason's real background and years of experience.
- **Service area** — confirm which surrounding cities/towns to list
  (Cape Coral, Estero, Bonita Springs, etc.) in `about.html`.
- **Google Map embed** — `contact.html` has a placeholder box where a real
  Google Maps embed can go. Instructions are in a comment right above it.
- **Domain & sitemap** — once you have a real domain, replace
  `YOUR-DOMAIN-HERE.com` in `robots.txt` and `sitemap.xml`.
- **Gallery photos** — `gallery.html` has 6 sample before/after slots, all
  placeholders. Duplicate/remove `.ba-card` blocks as needed once you have
  real project photos.

## Deploying

This is a plain static site, so any of these work well and are free for a
site this size:

- **Netlify** — drag-and-drop the whole `D:\Jason` folder at
  https://app.netlify.com/drop
- **GitHub Pages** — push this folder to a GitHub repo and enable Pages
  in the repo settings.
- **Vercel** — similar drag-and-drop / Git-based deploy flow.

All of them give you a free `.netlify.app` / `.vercel.app` / `.github.io`
URL immediately, and let you attach a custom domain (e.g.
`jasonswoodrefinishing.com`) later.

## Making future edits

- Colors, fonts, and spacing are controlled by CSS variables at the top of
  `css/style.css` (the `:root { ... }` block) — change a value there and
  it updates the whole site.
- The header and footer are duplicated at the top/bottom of every page
  (there's no shared-template system since this is plain HTML). If you
  change the nav links, phone number, or footer contact info, update it
  in all 6 HTML files. Comments in each file mark where these sections
  start and end.
