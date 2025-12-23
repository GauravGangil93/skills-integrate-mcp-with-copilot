**Title:** Add certificate verification endpoints

**Description:** Implement certificate verification by code using Firebase (or another data store) to retrieve certificate metadata and validation status.

**Details:**
- Validate input code and return certificate owner, issue date and verification status.

**Acceptance criteria:**
- `GET /certificates/verify?code=<CODE>` returns `200` with certificate data or `404` if not found.
- Input validation and rate-limiting to prevent abuse.

**Labels:** enhancement, backend, security
