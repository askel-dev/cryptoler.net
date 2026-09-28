# cryptoler.net

The front page of cryptoler.net: one static page linking to each project on its own subdomain.

| Project | Address | Hosted on |
|---|---|---|
| Nobody's Meadow | https://meadow.cryptoler.net | GitHub Pages, repo `askel-dev/aeon-garden` |
| Noctiluca | https://boids.cryptoler.net | GitHub Pages, repo `askel-dev/NOCTILUCA` |
| The Eye | https://eye.cryptoler.net | Vercel, repo `askel-dev/the-eye` (data and logins in Supabase) |
| Ödemark | https://odemark.cryptoler.net | Oracle Cloud server with Caddy, repo `askel-dev/odemark` |

This page is a Vercel project of its own, holding `cryptoler.net` and `www.cryptoler.net`.
Pushing to `main` deploys it. There is no build step: `index.html`, `favicon.svg` and `assets/`.

The domain's DNS lives in Vercel (Namecheap only holds the registration). Vercel answers for every
subdomain by default, so a project hosted elsewhere needs its own record there: `odemark` is an A record
to the Oracle server, `meadow` and `boids` CNAMEs to `askel-dev.github.io`.

Each card's cover is its project's own first screen in miniature: the meadow's share picture,
Noctiluca's splash over the live flock (captured from the page, prompt hidden), The Eye's login lockup (`assets/eye.svg`, its logo fixed to black), Ödemark's front page. To add a
project, copy a `.app` card and give it a colour of its own in `:root`.

The link preview is `og.jpg`, drawn from `tools/og.html` (the four covers two by two). After changing a card,
redraw it and bump the `?v=` on `og:image` and `twitter:image` in `index.html`:

    "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars \
      --window-size=1200,630 --virtual-time-budget=4000 --screenshot=og.png tools/og.html
    sips -s format jpeg -s formatOptions 88 og.png --out og.jpg && rm og.png

`tools/` and this README aren't deployed (`.vercelignore`).

Preview locally: `python3 -m http.server 8790`, then http://localhost:8790.
