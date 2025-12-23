# Proposed Issues to Add GDSC-like Features

Draft issues to add server-side and integration features inspired by the GDSC-PHCET Android app. Edit any entry before I create real GitHub Issues.

---

## 1. Add event-scraping endpoint
- Description: Implement a server endpoint that scrapes event listing pages (e.g. gdsc.community.dev) and returns structured JSON for upcoming and past events.
- Details: Endpoint should accept a source URL (or use a configured source), fetch HTML with a timeout, parse event items and return an array of events with fields: `title`, `dateTime`, `type` (past/upcoming), `image`, `url`, `tags`, `shortDesc`.
- Acceptance criteria:
  - `GET /scrape/events?source=<url>` returns JSON with events within 10s; handles network errors and invalid input.
  - Responses include reasonable pagination or limits to avoid very large payloads.
  - Implement basic rate-limiting and timeout handling.
- Labels: `enhancement`, `backend`

---

## 2. Add event-detail parsing utilities
- Description: Add a utilities module to extract detailed information from an event page: banner/logo URLs, long description (HTML sanitized), agenda items, whenDate/whenTime and tags.
- Details: Provide small, testable functions such as `get_event_details(url)`, `extract_agenda(html)`, and `get_banner_url(html_or_doc)` with clear return types.
- Acceptance criteria:
  - Unit-tested functions that parse representative sample HTML and return structured objects.
  - Clear error handling for missing fields and malformed HTML.
- Labels: `enhancement`, `tooling`, `tests`

---

## 3. Add Firebase-backed team endpoints
- Description: Add endpoints to serve team member data (lead, senior, junior) using Firebase Realtime Database or Firestore as the source.
- Details: Provide configuration (env vars or config file) for Firebase credentials; endpoints return member objects with `name`, `position`, `image`, and social links.
- Acceptance criteria:
  - Endpoints: `GET /team/lead`, `GET /team/senior`, `GET /team/junior` respond with JSON.
  - Include an example config and README notes for setting Firebase credentials locally.
- Labels: `backend`, `integration`

---

## 4. Add certificate verification endpoints
- Description: Implement certificate verification by code using Firebase (or another data store) to retrieve certificate metadata and validation status.
- Details: Validate the input code, return certificate owner, issue date and verification status.
- Acceptance criteria:
  - `GET /certificates/verify?code=<CODE>` returns `200` with certificate data or `404` if not found.
  - Input validation and rate-limiting to prevent abuse.
- Labels: `enhancement`, `backend`, `security`

---

## 5. Add sharing/export endpoint
- Description: Add an endpoint to export event details as a shareable image or provide a structured payload for client-side rendering.
- Details: Server-side rendering can use a headless renderer or image-generation library; alternatively provide a JSON payload optimized for client export.
- Acceptance criteria:
  - `POST /events/{id}/export` returns `image/png` or a JSON object with a URL to the generated image.
  - Document limits (image size, TTL) and required inputs.
- Labels: `enhancement`, `api`

---

## 6. Add tests for scraping/parsing logic
- Description: Add unit tests (pytest) and HTML fixtures for the scraping and parsing utilities to prevent regressions.
- Acceptance criteria:
  - Tests run with `pytest` and cover key parsing functions with representative fixtures.
  - Include a small CI job example (optional) to run tests on PRs.
- Labels: `tests`

---

## 7. Integration: on-demand scrape + periodic updater
- Description: Wire the scraping endpoint into the API so events can be fetched on-demand and add an optional background updater (cron, APScheduler, or worker) to refresh event data periodically.
- Details: The updater should be toggleable and safe to run in development mode.
- Acceptance criteria:
  - `POST /scrape/events/refresh` triggers a refresh job (or returns job queued) and updates an internal cache/store.
  - Provide instructions for enabling scheduled runs (system cron, GitHub Actions schedule, or APScheduler) and a config toggle.
- Labels: `enhancement`, `ops`

---

Next steps: review and edit any entry you want changed. When you're ready I can create these as real GitHub Issues in the repository.
