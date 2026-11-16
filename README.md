# cryptoler.net

The front page of cryptoler.net is a static directory of projects.

| Project | Address | Hosted on |
|---|---|---|
| nibblet | https://nibblet.cryptoler.net | Vercel, repo `askel-dev/long-shot` |
| Nobody's Meadow | https://meadow.cryptoler.net | GitHub Pages, repo `askel-dev/aeon-garden` |
| Noctiluca | https://boids.cryptoler.net | GitHub Pages, repo `askel-dev/NOCTILUCA` |
| ingenium | https://github.com/askel-dev/ingenium | Native Rust project on GitHub |
| The Eye | https://eye.cryptoler.net | Vercel, repo `askel-dev/the-eye` (data and logins in Supabase) |

This page is a Vercel project of its own, holding `cryptoler.net` and `www.cryptoler.net`.
Pushing to `main` deploys the static files without a build step.

Vercel redirects the apex domain to `https://www.cryptoler.net/`. That URL is the homepage canonical
and the only entry in `sitemap.xml`. The project subdomains have independent deployments.
Keep the homepage cards and the project summaries in `llms.txt` in sync when updating the directory.

The domain's DNS lives in Vercel (Namecheap only holds the registration). Vercel answers for every
subdomain by default, so a project hosted elsewhere needs its own record there: `odemark` is an A record
to the Oracle server, `meadow` and `boids` CNAMEs to `askel-dev.github.io`.

The covers show the meadow's share picture, nibblet's planned title screen (the wordmark over the
morning scene, `?h=9.5&x=-90`, as in long-shot's `artifacts/brand-study/round-2-bobber.html`),
Noctiluca's splash over the live flock, an in-engine forest capture from ingenium, and The Eye's
login lockup (`assets/eye.svg`, its logo fixed to black). To add a project, copy an `.app` card
and give it a colour of its own in `:root`.

The link preview is `og.jpg`, drawn from `tools/og.html` (the five covers, three over two). After changing a card,
redraw it and bump the `?v=` on `og:image` and `twitter:image` in `index.html`:

    "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars \
      --window-size=1200,630 --virtual-time-budget=4000 --screenshot=og.png tools/og.html
    sips -s format jpeg -s formatOptions 88 og.png --out og.jpg && rm og.png

`tools/` and this README aren't deployed (`.vercelignore`).

Preview locally: `python3 -m http.server 8790`, then http://localhost:8790.
