# LinkedIn Company Scraper: No Login B2B Data

Scrape LinkedIn company pages without login: company name, tagline, industry, employee count range, headquarters, founding year, website URL, follower count, about text, and specialties. Supply a list of LinkedIn company URLs.

**Run it on Apify:** [apify.com/themineworks/linkedin-company-details](https://apify.com/themineworks/linkedin-company-details)
**Docs, FAQ and pricing:** [themineworks.com/actors/linkedin-company-details](https://themineworks.com/actors/linkedin-company-details/)

**Price:** $3.50 per 1,000 companies on Apify's free plan, down to $2.10 on higher plans, plus a $0.005 start fee per run. Failed and empty results are never charged.

## What it returns

* Employee count, industry, and founding year
* Website, HQ location, and follower count
* About text and specialties list
* Bulk input: list of LinkedIn company URLs
* No login or cookies required

## Quick start

You need a free [Apify account](https://console.apify.com/sign-up) and its API token (Settings, API & Integrations).

### Python

```bash
pip install apify-client
```

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("themineworks/linkedin-company-details").call(run_input={
    "companyUrls": [
        "https://www.linkedin.com/company/openai"
    ],
    "maxResults": 3
})

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

### Node.js

```bash
npm install apify-client
```

```javascript
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_APIFY_TOKEN' });
const run = await client.actor('themineworks/linkedin-company-details').call({
    "companyUrls": [
        "https://www.linkedin.com/company/openai"
    ],
    "maxResults": 3
});
const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(items);
```

### cURL

One request that runs the actor and returns the results in the response (for runs under 5 minutes):

```bash
curl -X POST "https://api.apify.com/v2/acts/themineworks~linkedin-company-details/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"companyUrls": ["https://www.linkedin.com/company/openai"], "maxResults": 3}'
```

### Command line

This repo includes ready-made clients that save results to JSON and CSV:

```bash
python3 linkedin_company_scraper.py --token YOUR_APIFY_TOKEN --company-urls "https://www.linkedin.com/company/openai" --max-results "3"
node linkedin_company_scraper.mjs --token YOUR_APIFY_TOKEN --company-urls "https://www.linkedin.com/company/openai" --max-results "3"
```

## Input

| Field | Type | Default | Description |
|---|---|---|---|
| `companyUrls` | array |  | List of LinkedIn company page URLs to scrape (for example https://www.linkedin.com/company/openai) |
| `maxResults` | integer | `10` | Maximum number of companies to scrape |

## Output

One row per result, as JSON, CSV, Excel or through the API.

| Field | Type | Description |
|---|---|---|
| `company_url` | string | Canonical LinkedIn company page URL |
| `name` | string | Company name |
| `tagline` | string | Short tagline or description under the company name |
| `industry` | string | Industry category |
| `company_size` | string | Employee count range (for example '201-500 employees') |
| `headquarters` | string | Headquarters location |
| `founded` | string | Year the company was founded |
| `website` | string | Company website URL |
| `followers` | string | Follower count |
| `about` | string | About / description text |
| `specialties` | array | List of company specialties |
| `scraped_at` | string | ISO timestamp when this record was scraped |

## Use it from an AI agent

The actor works as a tool in Claude, Cursor or any MCP client through Apify's MCP server:

```
https://mcp.apify.com/?tools=themineworks/linkedin-company-details
```

## FAQ

### What do I pass in?

A list of LinkedIn company URLs. Each one returns a single structured company record.

### Is a LinkedIn login needed?

No. It reads the publicly visible company page, so no account, cookie or Sales Navigator seat is involved.

### What fields come back?

Company name, tagline, industry, employee count range, headquarters, founding year, website URL, follower count, the about text and the specialties list.

### Is the employee count exact?

No. LinkedIn publishes a band rather than a number, such as 201 to 500, and the actor returns that band as shown rather than inventing a midpoint.

### Can I run a whole account list at once?

Yes. Input is a bulk list, which is the usual way it gets used for firmographic enrichment of a CRM export.

### How fast is a bulk run?

It reads one public page per company with no browser, so a few hundred companies finish in minutes rather than hours.

### What if a company page has been removed?

The row comes back marked rather than silently dropped, so a list can be reconciled against the input without guessing which URLs failed.

### How much does the LinkedIn Company Scraper cost?

$3.50 per 1,000 companies on Apify's free plan, down to $2.10 on higher plans, plus a $0.005 start fee per run. Failed and empty results are never charged. You can cap what a single run may spend with the maximum cost setting on Apify.

### Can I export the results to CSV or Excel?

Yes. Every run saves to an Apify dataset you can download as JSON, CSV, Excel or XML, or read through the API. The Python and Node clients in this repo also write the results to local files.

### Can I run it on a schedule?

Yes. Save your input as a task on Apify and attach a schedule, or call the API from your own cron job. Scheduled runs are billed the same way as manual ones.

## Related scrapers

* [B2B Leads Finder](https://themineworks.com/actors/b2b-leads-finder/): Business emails and LinkedIn profiles for target companies
* [Zillow Rental Listings Scraper](https://themineworks.com/actors/zillow-rental-listings/): Scrape Zillow for-rent listings by city or zip. $1 per 1,000 results
* [Google Maps Leads Scraper](https://themineworks.com/actors/maps-leads/): Verified B2B leads from Google Maps. Pay only for emails that pass MX check

Part of [The Mine Works](https://themineworks.com/): 151 pay-per-result scrapers with no login and no browser setup on your side.

## License

MIT © The Mine Works
