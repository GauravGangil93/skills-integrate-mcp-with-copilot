**Title:** Add Firebase-backed team endpoints

**Description:** Add endpoints to serve team member data (lead, senior, junior) using Firebase Realtime Database or Firestore.

**Details:**
- Provide configuration (env vars or config file) for Firebase credentials.
- Endpoints should return member objects with `name`, `position`, `image`, and social links.

**Acceptance criteria:**
- `GET /team/lead`, `GET /team/senior`, `GET /team/junior` respond with JSON.
- Include example config and README notes for setting Firebase credentials locally.

**Labels:** backend, integration
