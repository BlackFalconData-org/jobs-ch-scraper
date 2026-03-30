# Jobs.ch Scraper

Extract structured data from [jobs.ch](https://jobs.ch) — Switzerland's leading job board. Full job descriptions, direct apply URLs, and workload percentage filters.

**[Jobs.ch Scraper on Apify →](https://apify.com/blackfalcondata/jobs-ch-scraper)**

---

## Key features

**Search with filters** — Search by keyword and location. Filter by country, employment type, and more.

**Detail enrichment** — Fetch full job descriptions, employer profiles, and direct apply URLs for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

---

## Use cases

**Data pipeline automation**
Integrate with your ETL pipeline to collect structured job listings from jobs.ch on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor job listings, track trends, and analyze market dynamics with structured, deduplicated data from jobs.ch.

---

## Quick start

```json
{
  "query": "software engineer",
  "maxResults": 50,
  "includeDetails": true
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Job search keywords. |
| `country` | enum | `"CH"` | Which market to search. |
| `location` | string | — | City or region to search in (e.g. Zurich, Bern, Basel). |
| `employmentType` | enum | `""` | Filter by employment type. |
| `maxResults` | integer | `25` | Maximum total results (0 = unlimited). |
| `includeDetails` | boolean | `true` | Fetch full job details. |
| `descriptionMaxLength` | integer | `0` | Truncate description to N chars. 0 = no truncation. |
| `compact` | boolean | `false` | Core fields only (for AI-agent/MCP workflows). |
| `incrementalMode` | boolean | `false` | Compare against previous run state. |
| `stateKey` | string | — | Stable identifier for tracked universe. |

---

## FAQ

**How many results can I get?**
The number depends on your search query and available listings. Use `maxResults` to control output size — set to `0` for unlimited.

**What data fields are included?**
32 fields per listing: title, company, location, employment type, workload percentage, description, apply URL, publication dates, skills, language requirements, categories, and more.

**Is it legal to scrape jobs.ch?**
This actor only accesses publicly visible information. Web scraping of public data is generally legal, but always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

**Can I filter by employment type?**
Yes. Use the `employmentType` parameter to filter by Permanent, Temporary, Freelance, Internship, Apprenticeship, or Supplementary income.

**How much does it cost?**
Pay-per-event: $0.01 per run start + $0.002 per result. Incremental runs only charge for new/changed results.

---

## Known limitations

- Results are limited to what jobs.ch returns for a given search query — very broad queries may not return all listings.
- Contact information (email, phone) is not available — jobs.ch does not expose this data publicly.
- Salary data is not provided by jobs.ch listings.
- Language skills and categories are returned as codes/paths, not human-readable labels.
- The actor requires a search keyword — browsing all listings without a query is not supported.

---

## Related products by Black Falcon Data

- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 03*
