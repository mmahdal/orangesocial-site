# orangesocial.app

Corporate website of Orange Social Limited. Static site on GitHub Pages.

**Status:** placeholder ("under construction"), crawling blocked via `robots.txt` and `noindex`. Remove both at launch.

## Structure

- `public/` – everything that is published
- `.github/workflows/pages.yml` – deploys `public/` on every push to `main`

Internal documents (prompts, runbooks, proposals) are **not** in this repo. They live in `~/Documents/Orange Social/docs-internal/`.

## Preview locally

```sh
python3 -m http.server 8000 --directory public
# open http://localhost:8000
```

## Deploy

Push to `main`. GitHub Actions publishes within a minute or two.

## Domains and DNS (GoDaddy)

`orangesocial.app` (custom domain set in repo Settings → Pages, HTTPS enforced):

| Type | Name | Value |
|---|---|---|
| A | @ | 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153 |
| AAAA | @ | 2606:50c0:8000::153, 2606:50c0:8001::153, 2606:50c0:8002::153, 2606:50c0:8003::153 |
| CNAME | www | mmahdal.github.io |
| TXT | _github-pages-challenge-mmahdal | domain verification (GitHub account settings → Pages) |

Mail records (MX, SPF, DKIM, DMARC) for Google Workspace sit alongside these; see the email runbook.

`orangesocialapp.com`: GoDaddy domain forwarding, 301 to `https://orangesocial.app` (covers `www`). Mail lock-down records (null MX, `v=spf1 -all`, DMARC reject) stay in place.
