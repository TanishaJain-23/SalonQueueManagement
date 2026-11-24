# AGENTS.md — Salon Queue Management

Salon queue web app: customers join from their phone, follow a live token, reception manages the line, barbers serve guests and the TV shows current turns.

## Read first
- docs/01-brief.md — scope and exclusions
- docs/02-screens.md — screen layouts and behaviour
- docs/03-flows-rules.md — queue rules and test checklist

## Stack
React + Vite + TypeScript + Tailwind CSS; Express + SQLite + Socket.IO.
Run locally with `npm install` then `npm run dev`.
Frontend: http://localhost:5173. API: http://localhost:4000/api/health.

## Working rules
- Build one screen or feature per task; preserve unrelated working screens.
- Mobile-first, charcoal #171717 and gold #D4A017.
- Keep queue rules in backend validation; do not trust frontend-only checks.
- Broadcast state changes with Socket.IO.
- Do not build features in the Don't build list.
- After each task, list changed files and how to test.
- Never claim a test passed unless it was actually run.
- Add the deployed live URL at the top of README.md once deployment succeeds.
