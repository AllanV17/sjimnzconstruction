# SJIMNZ Construction

Static Astro + TypeScript site. Home includes the navbar, hero, introduction, services, selected work, company introduction, final estimate CTA and footer.

## Local development

Requires Node.js 22.23.4+ (Node 24 supported) and npm 9.6.5+.

```sh
npm install
npm run dev
npm run build
npm run preview
```

The build outputs `dist/`. About, Services and Contact links intentionally target future routes (`/about/`, `/services/`, `/contact/`); those pages do not exist yet.

Development and preview serve the site at `http://localhost:4321/sjimnzconstruction/`. Use the address printed by Astro if that port is busy.

## GitHub Pages development deployment

The workflow in `.github/workflows/deploy.yml` deploys pushes to `main` and can also be run manually. It uses the [official Astro deployment action](https://docs.astro.build/en/guides/deploy/github/), with Node 24 and npm detected from `package-lock.json`.

The repository is [AllanV17/sjimnzconstruction](https://github.com/AllanV17/sjimnzconstruction). `astro.config.mjs` sets `site` to `https://allanv17.github.io` and `base` to `/sjimnzconstruction`, giving the expected publication URL [https://allanv17.github.io/sjimnzconstruction/](https://allanv17.github.io/sjimnzconstruction/). Internal links, images and font preload use Astro's `BASE_URL`; Vite prefixes the font URLs in the stylesheet during the build. Development and preview use the same base path as production.

First publication:

1. Git is initialized locally on `main`, with `origin` pointing to `https://github.com/AllanV17/sjimnzconstruction.git`. The remote was verified empty; there are no local commits yet.
2. In the repository, select **Settings → Pages → Build and deployment → Source → GitHub Actions**.
3. Run `git add .`, `git diff --cached --stat`, `git commit -m "Configure Astro GitHub Pages deployment"`, then `git push -u origin main`. Authenticate using GitHub Credential Manager for HTTPS if Git prompts; never put tokens in source files or the remote URL. If Git requests an author identity, configure your own name and email for this repository before committing.
4. Wait for **Deploy to GitHub Pages** to succeed. The `github-pages` environment shows the published URL.

Keep `package-lock.json` committed. Dependencies, generated output, `.env` files and local editor settings are ignored. Only Home currently exists; About, Services and Contact will still return 404 until those pages are implemented.

## Visual reference and assets

- [Figma reference](https://www.figma.com/design/fmWXkYn5oN9KKf4nukXSyK/Tiki-Hostal?node-id=232-1679): desktop hero `232:1680`, mobile hero `232:1883`.
- Photographs, brand marks and icons in `public/images/` were exported from those frames. The hero uses the same conceptual kitchen image on desktop and mobile, with a vertical crop and a darker overlay on mobile.
- Inter and IBM Plex Mono are served locally as Latin WOFF2 fonts. Their SIL Open Font License files are in `public/fonts/`.

## Commercial sources

The new Home sections use photographs from the company's existing website, downloaded locally without altering the originals:

- `projects/kitchen.jpeg`: [Kitchen-4.jpeg](https://www.sjimnzconstruction.com/wp-content/uploads/2019/06/Kitchen-4.jpeg).
- `projects/kitchen-detail.jpeg`: [Kitchen-7-1.jpeg](https://www.sjimnzconstruction.com/wp-content/uploads/2019/06/Kitchen-7-1.jpeg).
- `projects/bathroom.jpeg`: [bathrooms-1.jpeg](https://www.sjimnzconstruction.com/wp-content/uploads/2019/06/bathrooms-1.jpeg).
- `projects/drywall.jpeg`: [drywall-sjmnzconstruction.jpeg](https://www.sjimnzconstruction.com/wp-content/uploads/2019/05/drywall-sjmnzconstruction.jpeg).
- `projects/staircase.jpg`: [staircase-Sjimnzconstruction.jpg](https://www.sjimnzconstruction.com/wp-content/uploads/2019/06/staircase-Sjimnzconstruction.jpg).

Sergio J. Jimenez's CEO / Manager title is published on the [existing About page](https://www.sjimnzconstruction.com/about/). The phone, email, address and license number PA147397 are published on the [existing Home page](https://www.sjimnzconstruction.com/). The license number is reproduced as published, without asserting its current registration status. No project locations, dates, testimonials or additional credentials have been added.

## Quick verification

- Build with `npm run build`.
- Check desktop at 1440 px and mobile at 390 px and 320 px, including image loading and horizontal overflow.
- On mobile, focus the hamburger control (accessible name: Main menu) and press Enter to open and close it; check all four navigation links and the phone link inside the menu.
- Confirm the phone points to `tel:+12158003372` and the estimate button to `/contact/`.
