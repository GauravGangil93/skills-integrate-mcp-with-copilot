**Title:** Add event-scraping endpoint

**Description:** Implement a server endpoint that scrapes event listing pages (e.g. gdsc.community.dev) and returns structured JSON for upcoming and past events.

**Details:**
- Endpoint should accept a source URL (or use a configured source).
- Fetch HTML with a timeout and parse event items.
- Return array of events with: `title`, `dateTime`, `type` (past/upcoming), `image`, `url`, `tags`, `shortDesc`.

**Acceptance criteria:**
- `GET /scrape/events?source=<url>` returns JSON within 10s and handles network errors.
- Responses include pagination/limits to avoid huge payloads.
- Basic rate-limiting and timeout handling implemented.

**Labels:** enhancement, backend
