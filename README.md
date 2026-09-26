# Nitrotick — company website

Static company website for **Nitrotick — Verifiable Execution Infrastructure**, published with GitHub Pages.

- 100% HTML + CSS. No JavaScript, no build step, no frameworks.
- All graphics are inline or file-based **SVG**. PNG files exist only where platforms require raster images (social preview cards, Apple touch icon, PWA icons).
- No external fonts, trackers or third-party requests (GDPR-friendly and fast).
- Contact goes through LinkedIn messages, so the site has no contact form.

## Structure

```
/
├── index.html                        Home — platform, trust tiers, architecture, comparison, FAQ
├── federation/index.html             Nitrotick Federation (cross-institution execution)
├── digital-product-passport/index.html  Verifiable Digital Asset Platform / DPP (EN + MK summary)
├── ai-governance/index.html          Governed AI execution (AI agents as bounded actors)
├── blockchain-alternative/index.html Enterprise blockchain alternative (comparison, FAQ)
├── compliance/index.html             NIS2, DORA, EU AI Act, GDPR, eIDAS 2.0, ESPR
├── 404.html                          GitHub Pages not-found page
├── css/styles.css                    Complete design system (tokens, layout, components)
├── assets/img/
│   ├── logo.svg / logo-mark.svg      Brand logo (full / mark only)
│   ├── og-image.svg → og-image.png   Social preview card source and 1200×630 render
│   ├── logo-512.png                  Organization logo for structured data
│   └── icon-192.png / icon-512.png   Web manifest icons
├── favicon.svg, favicon-32.png, apple-touch-icon.png
├── site.webmanifest
├── robots.txt, sitemap.xml
└── .nojekyll                         Serve files as-is (skip Jekyll processing)
```

## SEO

Every page includes:

- a unique `<title>`, meta description and canonical URL
- Open Graph and Twitter Card metadata with a 1200×630 PNG preview
- JSON-LD structured data: `Organization`, `Person` (founder), `WebSite`, `WebPage`, `SoftwareApplication`, `FAQPage` (home), and `Service` + `BreadcrumbList` (sub-pages)
- semantic HTML5 landmarks, a single `h1`, accessible SVG (`role="img"`, `<title>`, `<desc>`)

`robots.txt` and `sitemap.xml` point to `https://nitrotick.com/`.

## Deployment (GitHub Pages)

1. **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main`, folder = `/ (root)`.
2. **Custom domain**: enter `nitrotick.com` and save. GitHub then commits a `CNAME` file. Enable **Enforce HTTPS** once the certificate is issued.
3. DNS at your registrar:
   - Apex `nitrotick.com`: `A` records → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` (optionally `AAAA` → `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`)
   - `www`: `CNAME` → `<github-username>.github.io`
4. After the site is live, submit `https://nitrotick.com/sitemap.xml` in Google Search Console and Bing Webmaster Tools.

If you use a different domain, replace `https://nitrotick.com` in all `*.html` files, `robots.txt` and `sitemap.xml`.

Page links use relative paths, so the site also works at `https://<user>.github.io/<repo>/` before the domain is connected. The only exception is `404.html`, which needs root-absolute paths because GitHub Pages serves it for any URL.

## Updating the social preview image

Edit `assets/img/og-image.svg`, then export it to `og-image.png` at 1200×630. Any SVG-to-PNG tool works, such as Inkscape or a headless browser screenshot.

## Local preview

```bash
npx serve .      # or: python3 -m http.server 8080
```

© 2026 Nitrotick. All rights reserved.
