**Title:** Integration: on-demand scrape + periodic updater

**Description:** Wire the scraping endpoint into the API so events can be fetched on-demand and add an optional background updater (cron, APScheduler, or worker) to refresh event data periodically.

**Details:**
- The updater should be toggleable and safe to run in development mode.

**Acceptance criteria:**
- `POST /scrape/events/refresh` triggers a refresh job (or returns job queued) and updates an internal cache/store.
- Provide instructions for enabling scheduled runs (system cron, GitHub Actions schedule, or APScheduler) and a config toggle.

**Labels:** enhancement, ops
