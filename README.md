# Salon Queue Management System

**Live demo:** Not deployed yet — add the public URL here after deployment and testing.

## Project overview
A mobile-first salon queue management web application. Customers can join the queue, receive a daily token and follow their service status. Reception staff manage waiting customers, barbers update service progress, a waiting-area display shows turns, and the owner manages services and online queue availability.

## Main screens
- `/` — Home
- `/join` — Join Queue
- `/status/:id` — Customer status
- `/reception` — Reception dashboard
- `/barber` — Barber view
- `/display` — Waiting-area display
- `/admin` — Owner settings

## Technology
React, TypeScript, Vite, Tailwind CSS, Express, SQLite and Socket.IO.

## Run locally (Windows PowerShell)
Use a supported Node.js LTS release (Node.js 22 LTS is recommended for the native `better-sqlite3` dependency).

1. Install Node.js LTS.
2. Open this folder in VS Code.
3. In the terminal, run `npm.cmd install`.
4. Start the app with `npm.cmd run dev`.
5. Open `http://localhost:5173`.
6. Backend health endpoint: `http://localhost:4000/api/health`.

If PowerShell blocks `npm`, use `npm.cmd` as shown. Do not upload `node_modules/` to GitHub.

## Repository contents
- `src/` — React user interface
- `server/` — Express API and SQLite data layer
- `docs/` — Project brief, screen descriptions, and queue rules
- `AGENTS.md` — Instructions for AI coding agents
- `prompts.md` — Prompt log / development prompts
- `DEPLOYMENT.md` — Hosting instructions
- `SUBMISSION_REPORT.pdf` — Project submission report

## Important implementation notes
This is a lab MVP starter and must be tested before being described as production-ready. Staff routes do not currently have authentication. Estimated wait times are approximate. SMS/WhatsApp, online payments, future appointments and multi-branch support are outside the stated scope. SQLite deployment needs persistent storage configured on the hosting provider.

## Before final submission
1. Run the app locally and test the checklist in `docs/03-flows-rules.md`.
2. Fix any failed checks and record actual results.
3. Deploy frontend/backend and replace the Live demo line with the tested public URL.
4. Record a short demo showing the customer-to-staff flow.
5. Add your name, student ID, course details and actual demo link to the report if your instructor requires them.
