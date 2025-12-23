# Proposed Issues to Add GDSC-like Features

This file contains draft GitHub issues to add features inspired by the GDSC-PHCET Android app.

---

## 1. Add event-scraping endpoint
- **Description:** Implement a server-side endpoint that scrapes event pages (e.g. gdsc.community.dev) and returns structured event data (upcoming/past lists).
- **Acceptance criteria:** Endpoint `/scrape/events` (or similar) accepts a source URL and returns JSON with events including title, date/time, type, image, url and tags. Include rate-limiting/timeout handling.
- **Labels:** enhancement, backend

---

## 2. Add event-detail parsing utilities
- **Description:** Add a utilities module to parse event detail pages and extract banner/logo URLs, long/short descriptions, agenda items and tags.
- **Acceptance criteria:** Functions `get_event_banner(url)`, `get_event_details(url)`, `extract_agenda(html)` with unit tests that parse representative HTML snippets.
- **Labels:** enhancement, tooling, tests

---

## 3. Add Firebase-backed team endpoints
- **Description:** Add endpoints to serve team data (lead, senior, junior members) backed by Firebase Realtime Database or Firestore.
- **Acceptance criteria:** Endpoints `/team/lead`, `/team/senior`, `/team/junior` return JSON with social links and images; include configuration for Firebase credentials.
- **Labels:** backend, integration

---

## 4. Add certificate verification endpoints
- **Description:** Implement certificate verification lookup by code using Firebase as the source of truth.
- **Acceptance criteria:** Endpoint `/certificates/verify?code=...` returns certificate metadata or 404; validate inputs and handle errors.
- **Labels:** enhancement, backend, security

---

## 5. Add sharing/export endpoint
- **Description:** Add an endpoint to export event details as an image (or structured payload) suitable for sharing; can be implemented as server-side render or an export helper.
- **Acceptance criteria:** POST `/events/{id}/export` returns an image or a link to a generated share image; document limitations (size, format).
- **Labels:** enhancement, api

---

## 6. Add tests for scraping/parsing logic
- **Description:** Add unit tests (pytest) for the event scraping and parsing utilities to ensure HTML parsing works and to prevent regressions.
- **Acceptance criteria:** Tests cover core parsing functions and run via `pytest`; include sample HTML fixtures.
- **Labels:** tests

---

## 7. Add integration: scrape-on-demand + periodic updater
- **Description:** Wire the scraping endpoint into the API so it can be run on-demand and add an optional periodic updater (cron / background task) to refresh events.
- **Acceptance criteria:** Background job or scheduled task updates an internal store or cache; include a toggle to enable/disable.
- **Labels:** enhancement, ops

---

If you want these created as real GitHub Issues instead of a drafted file, I can create them directly in the repository when you confirm. For now this file serves as the canonical list and can be edited before issue creation.
