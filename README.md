# LinkedIn Company Scraper: Size & Industry, No Cookies

Python client for **[LinkedIn Company Scraper: Size & Industry, No Cookies](https://apify.com/themineworks/linkedin-company-details)** — scrape LinkedIn company pages: size, industry, details — no cookies.

> ⚡ No login, no cookies, no ban risk · runs in the cloud on [Apify](https://apify.com/themineworks/linkedin-company-details)
>
> 💸 From **$5.0 per 1,000 results** (volume discounts on paid Apify plans). You are only charged for delivered results — empty searches and failed pages are never billed.

## Quick start

```bash
pip install apify-client
python3 linkedin_company_scraper.py --token YOUR_APIFY_TOKEN --company-urls "https://www.linkedin.com/company/openai"
```
### Node.js

```bash
npm install apify-client
node linkedin_company_scraper.mjs --token YOUR_APIFY_TOKEN --token YOUR_APIFY_TOKEN --company-urls "https://www.linkedin.com/company/openai"
```


Get a free API token: [console.apify.com/sign-up](https://console.apify.com/sign-up) — then find it under **Settings → API & Integrations**.

## Options

| Flag | Type | Description |
|---|---|---|
| `--token` | string | Apify API token (or `APIFY_TOKEN` env var) |
| `--out` | string | Output basename — writes `results.json` + `results.csv` |
| `--company-urls` | array | List of LinkedIn company page URLs to scrape (e.g. https://www.linkedin.com/company/openai |
| `--max-results` | integer | Maximum number of companies to scrape. Capped at 200. |

Flags map 1:1 to the actor's input schema — full reference and a live output sample on the [Store listing](https://apify.com/themineworks/linkedin-company-details).

## Output

One row per result, saved as both JSON and CSV with every field the actor returns. Preview the exact fields on the [listing's output tab](https://apify.com/themineworks/linkedin-company-details).

## Why this actor

- **HTTP-native** — fast, stable, no headless-browser overhead
- **No account risk** — never asks for your login or cookies
- **Fair billing** — pay per delivered result only

MIT © [The Mine Works](https://apify.com/themineworks) — part of a 69-scraper suite trusted by 450+ developers.
