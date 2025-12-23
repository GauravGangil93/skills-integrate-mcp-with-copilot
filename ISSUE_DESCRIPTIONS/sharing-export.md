**Title:** Add sharing/export endpoint

**Description:** Add an endpoint to export event details as a shareable image or provide a structured payload for client-side rendering.

**Details:**
- Server-side rendering can use a headless renderer or image-generation library, or provide JSON optimized for client export.

**Acceptance criteria:**
- `POST /events/{id}/export` returns `image/png` or JSON with a URL to the generated image.
- Document limits (image size, TTL) and required inputs.

**Labels:** enhancement, api
