# ThoughtLink Landing

Static landing page for `thoughtlink.ai` and `thoughtlink.co`. Intentionally a placeholder — activates the domains and reserves the brand mark.

## Stack

- Plain HTML / CSS, no framework
- Hosted on Cloudflare Pages

## Local preview

Just open `index.html` in a browser. No build step.

```sh
# or with a simple local server
npx serve .
```

## Deploy

`thoughtlink.ai` is the canonical domain. `thoughtlink.co` 301-redirects to it.

1. Push this repo to GitHub.
2. Cloudflare Dashboard → Workers & Pages → Create → Pages → Connect to Git → pick this repo. Build settings: framework "None", no build command, output directory `/`.
3. Custom domains → add **`thoughtlink.ai` only** (this is the canonical).
4. For `thoughtlink.co` (brand protection / typo catcher):
   - DNS → add an `A` record `@` → `192.0.2.1` with Proxied (orange cloud) on.
   - Rules → Redirect Rules → create a 301 rule: hostname equals `thoughtlink.co` → static redirect to `https://thoughtlink.ai`, preserve path + query.

## Edit

Edit `index.html` (markup) and `style.css` (visuals). That's it.

## Social share card (OG image)

The OG / Twitter Card metadata points to `/og-image.png` (1200×630). The design source is `og-image.svg`; `og-image.png` is the rendered output committed alongside it (Twitter/Facebook/LinkedIn don't accept SVG).

To regenerate the PNG after editing the SVG:

```sh
npx --yes @resvg/resvg-js-cli og-image.svg og-image.png
```

## Future

When the page needs to grow beyond a single static screen (blog, framework spec, etc.), upgrade to Astro or Next without touching the domain setup.
