**Title:** Add event-detail parsing utilities

**Description:** Add utilities to extract detailed information from an event page: banner/logo URLs, long description (HTML sanitized), agenda items, whenDate/whenTime and tags.

**Details:**
- Provide functions such as `get_event_details(url)`, `extract_agenda(html)`, `get_banner_url(html_or_doc)`.
- Return structured objects with clear types and error handling.

**Acceptance criteria:**
- Unit-tested functions that parse representative sample HTML and return structured objects.
- Clear error handling for missing fields and malformed HTML.

**Labels:** enhancement, tooling, tests
