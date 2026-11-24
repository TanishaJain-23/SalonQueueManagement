# Prompts Used / Project Build Log

The following are the project prompts adapted from the Salon Queue Management guide. If you use Antigravity or Codex to continue building, append every prompt you actually send, in order, including failed attempts.

1. Read AGENTS.md and all files in docs/. Summarise the salon queue app in eight bullets and identify unclear rules. Do not write code yet.
2. Implement Step 1 only: set up React + Vite + TypeScript + Tailwind, Express backend, SQLite and Socket.IO. Create modular folders, concurrent local development scripts and a backend health endpoint. Verify frontend and backend locally.
3. Build only Home and Join Queue from docs/02-screens.md. Add realistic services and barbers, phone validation, 3-service limit, live price/duration summary and responsive charcoal/gold styling.
4. Implement My Status, sequential daily tokens, queue persistence, estimated wait and Waiting-only cancellation.
5. Build Reception Dashboard with walk-ins and barber-preference-aware Call next.
6. Build Barber View with Available/On break, Start and Done actions. Add the Waiting Area TV with live token updates.
7. Build Owner Settings: service add/edit availability, online queue open/close and daily summary.
8. Implement every rule in docs/03-flows-rules.md. Validate status transitions on the backend, persist data and broadcast updates with Socket.IO.
9. Audit every checklist item. Run frontend production build, test backend edge cases and report PASS/FAIL with evidence. Fix reproducible defects only.
10. Prepare deployment, remove localhost-only assumptions, configure environment variables, add the working live URL at the top of README.md and document staff access.

## Important
This file records the planned prompts for the starter implementation. Replace or supplement this list with the exact prompts you personally submit to your coding agent, as your guide requires every prompt actually used.
