# cryptoler.net

The front page of cryptoler.net: one static page linking to each project on its own subdomain.

| Project | Address | Hosted on |
|---|---|---|
| Nobody's Meadow | https://meadow.cryptoler.net | GitHub Pages, repo `askel-dev/aeon-garden` |
| Noctiluca | https://noctiluca.cryptoler.net | GitHub Pages, repo `askel-dev/NOCTILUCA` |
| The Eye | https://eye.cryptoler.net | Vercel, repo `askel-dev/the-eye` (data and logins in Supabase) |
| Ödemark | https://odemark.cryptoler.net | Oracle Cloud server with Caddy, repo `askel-dev/odemark` |

This page is a Vercel project of its own, holding `cryptoler.net` and `www.cryptoler.net`.
Pushing to `main` deploys it. There is no build step: `index.html`, `favicon.svg` and `assets/`.

The domain's DNS lives in Vercel (Namecheap only holds the registration). Vercel answers for every
subdomain by default, so a project hosted elsewhere needs its own record there: `odemark` is an A record
to the Oracle server, `meadow` and `noctiluca` CNAMEs to `askel-dev.github.io`.

Each card's cover is its project's own first screen in miniature: the meadow's share picture,
Noctiluca's splash over the live flock (captured from the page, prompt hidden), The Eye's login lockup (`assets/eye.svg`, its logo fixed to black), Ödemark's front page. To add a
project, copy a `.app` card and give it a colour of its own in `:root`.

Preview locally: `python3 -m http.server 8790`, then http://localhost:8790.
