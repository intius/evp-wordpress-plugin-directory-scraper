# WordPress Plugin Directory Scraper & Unofficial API (Python, Node.js, MCP)

[Run WordPress Plugin Directory Scraper on Apify](https://apify.com/evpp/wordpress-plugin-directory) to export WordPress Plugin Directory data as clean JSON, CSV, Excel, or an API feed. This repository is a developer quick-start kit with working Python and Node.js clients, an MCP configuration, a real sample dataset, and an n8n automation template.

[![Run on Apify](https://img.shields.io/badge/Run%20on-Apify-orange)](https://apify.com/evpp/wordpress-plugin-directory)

[Open the documentation and crawlable sample explorer](https://intius.github.io/evp-labs-data-extractors/actors/wordpress-plugin-directory/) for quick inputs, integration links, real sample rows, and ready-made task examples.

## Why use this WordPress Plugin Directory scraper?

- Export WordPress Plugin Directory data without building or maintaining a custom scraper
- Get flat, schema documented JSON ready for analytics, lead generation, market research, and AI agents
- Run manually, on a schedule, through the Apify API, or through MCP compatible AI tools
- Use the included 25+ row sample dataset to prototype before running the live Actor

Built for WordPress agencies, hosting companies, plugin competitors, security researchers, lead-gen selling services to 60k+ plugin developers.

## Quick start on Apify

Open [https://apify.com/evpp/wordpress-plugin-directory](https://apify.com/evpp/wordpress-plugin-directory) and use this input:

```json
{
  "searchTerm": "seo",
  "maxItems": 15
}
```

## Python

```bash
pip install -r requirements.txt
export APIFY_TOKEN=your_apify_token
python python/run.py
```

On Windows PowerShell, use `$env:APIFY_TOKEN="your_apify_token"` instead of `export`.

## Node.js

```bash
npm install
export APIFY_TOKEN=your_apify_token
node node/run.mjs
```

## MCP and AI agents

Add the hosted Apify MCP server from `mcp-config.json` to your MCP client:

```json
{
  "mcpServers": {
    "apify": {
      "type": "http",
      "url": "https://mcp.apify.com/?tools=evpp/wordpress-plugin-directory"
    }
  }
}
```

Then ask your agent to run `evpp/wordpress-plugin-directory`, inspect the output schema, or export the latest dataset. The direct MCP URL is `https://mcp.apify.com/?tools=evpp/wordpress-plugin-directory`.

## n8n automation

Import `n8n-workflow.json` into n8n, select your Apify credential, replace the webhook placeholder, and activate the schedule. The workflow runs the Actor every morning and posts fresh dataset items to your webhook.

## Output schema

| Field | Type | Description |
|---|---|---|
| `name` | string | Plugin display name |
| `slug` | string | Plugin slug in the WordPress.org directory |
| `url` | string | Public URL of the plugin page on WordPress.org |
| `version` | string | Current plugin version |
| `author` | string | Plugin author display name (HTML stripped) |
| `authorUrl` | string | Author profile URL on WordPress.org |
| `rating` | integer | Community rating on a 0-100 scale |
| `ratingStars` | number | Community rating on a 0.0-5.0 star scale |
| `numRatings` | integer | Total number of submitted ratings |
| `activeInstalls` | integer | Reported number of active WordPress installations |
| `downloaded` | integer | Lifetime download count |
| `supportThreads` | integer | Number of support threads opened in the last two months |
| `supportThreadsResolved` | integer | Number of those support threads marked resolved |
| `requiresWp` | string | Minimum required WordPress version |
| `testedUpTo` | string | Highest WordPress version the plugin is tested against |
| `requiresPhp` | string | Minimum required PHP version |
| `lastUpdated` | string | When the plugin was last updated, as reported by the API |
| `added` | string | Date the plugin was added to the directory |
| `homepage` | string | Plugin homepage URL declared by the author |
| `downloadLink` | string | Direct ZIP download URL of the current version |
| `tags` | string[] | Tag slugs assigned to the plugin |
| `description` | string | Short plugin description, plain text trimmed to ~300 characters |

## Real sample output

The first sanitized row from the included sample dataset:

```json
{
  "name": "Rank Math SEO – AI SEO Tools to Dominate SEO Rankings",
  "slug": "seo-by-rank-math",
  "url": "https://wordpress.org/plugins/seo-by-rank-math/",
  "version": "1.0.282",
  "author": "Rank Math SEO",
  "authorUrl": "https://profiles.wordpress.org/rankmath/",
  "rating": 96,
  "ratingStars": 4.8,
  "numRatings": 7530,
  "activeInstalls": 4000000,
  "downloaded": 204392168,
  "supportThreads": 41,
  "supportThreadsResolved": 34,
  "requiresWp": "6.7",
  "testedUpTo": "7.1.5",
  "requiresPhp": "7.4",
  "lastUpdated": "2026-11-10 10:58am GMT",
  "added": "2018-11-19",
  "homepage": "https://rankmath.com/",
  "downloadLink": "https://downloads.wordpress.org/plugin/seo-by-rank-math.1.0.282.zip",
  "tags": [
    "google-search-console",
    "redirection",
    "schema",
    "seo",
    "xml-sitemap"
  ],
  "description": "Grow your organic traffic and AI visibility with powerful SEO tools, XML sitemaps, Schema automation, and built-in AI SEO, all in one place."
}
```

## Files in this kit

| File | Purpose |
|---|---|
| `python/run.py` | Working Python Apify API example |
| `node/run.mjs` | Working Node.js Apify API example |
| `mcp-config.json` | MCP server configuration for AI agents |
| `sample-output.json` | First five sanitized sample rows |
| `dataset-snapshot.csv` | 25+ row evaluation snapshot |
| `DATASET_CARD.md` | Dataset documentation and provenance |
| `n8n-workflow.json` | Scheduled n8n automation template |

## Fresh data

This repository contains a static evaluation sample. For current data, run the live Actor: https://apify.com/evpp/wordpress-plugin-directory

## Responsible use

The Actor reads public data from `wordpress.org`. Review the source site's terms and applicable privacy rules before production use.
