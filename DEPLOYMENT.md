# Deployment Guide — step by step

## Recommended architecture
Deploy the React frontend to Vercel and the Express + Socket.IO API to Render. The API needs a persistent disk for its SQLite database. You must create the accounts, connect GitHub and press Deploy yourself; this project package cannot create services inside your accounts.

## A. Push the project to GitHub
1. Create a GitHub account or sign in.
2. Create a new **Public** repository named `salon-queue-management`.
3. Do not add a README from GitHub (this folder already has one).
4. Extract the ZIP file.
5. Open the extracted folder in VS Code.
6. Open Terminal and run:

```bash
git init
git add .
git commit -m "Initial salon queue project"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/salon-queue-management.git
git push -u origin main
```

7. Replace `YOUR-USERNAME` with your actual GitHub username. Your repository URL will be `https://github.com/YOUR-USERNAME/salon-queue-management`.

## B. Deploy the backend on Render
1. Push the repository first.
2. Sign in at https://render.com and choose **New → Web Service**.
3. Connect GitHub and select `salon-queue-management`.
4. Configure:
   - Runtime: Node
   - Build command: `npm install && npm run build:server`
   - Start command: `node dist-server/index.js`
   - Add environment variable `CLIENT_URL` with your eventual Vercel URL (you can temporarily use `*` only during initial testing; replace it with your exact site origin).
   - Add environment variable `DATABASE_FILE=/var/data/salon.sqlite`
5. In Render's service settings, add a persistent disk:
   - Mount path: `/var/data`
   - Size: choose an available plan.
6. Deploy and wait for the service to become Live.
7. Copy the Render URL, for example `https://your-api.onrender.com`.
8. Test `https://your-api.onrender.com/api/health`. It should return JSON with `ok: true`.

## C. Deploy the frontend on Vercel
1. Sign in at https://vercel.com.
2. Choose **Add New → Project**, import the same GitHub repository.
3. Framework preset: Vite.
4. Build command: `npm run build`.
5. Output directory: `dist`.
6. Add environment variable:
   - Name: `VITE_API_URL`
   - Value: your Render API origin, e.g. `https://your-api.onrender.com` (no trailing slash).
7. Deploy.
8. Copy the Vercel URL, e.g. `https://salon-queue-management-yourname.vercel.app`.

## D. Connect both deployments
1. Return to Render → Environment.
2. Set `CLIENT_URL` to the exact Vercel origin (no trailing slash), e.g. `https://salon-queue-management-yourname.vercel.app`.
3. Save changes and redeploy/restart the Render service.
4. In Vercel, redeploy the frontend if you changed its environment variable.
5. Open the Vercel website on your phone. Test joining a queue.
6. Open Reception, Barber View and TV Display in separate browser tabs. Confirm updates arrive without refresh.
7. Refresh the customer status page and check that the entry remains.

## E. Update README live link
At the top of `README.md`, replace:
`**Live demo:** PENDING — deploy the project and replace this line with your working public URL.`
with:
`**Live demo:** https://YOUR-ACTUAL-VERCEL-URL`
Commit and push the change:

```bash
git add README.md
git commit -m "Add deployed live demo URL"
git push
```

## F. Final submission checklist
- [ ] Public GitHub repository opens without login.
- [ ] Live demo opens on a phone.
- [ ] README's live URL is the first line after the title.
- [ ] API health endpoint responds.
- [ ] Customer can join and receive a token.
- [ ] Reception can call a customer.
- [ ] Barber can start and complete service.
- [ ] TV display updates.
- [ ] Owner can disable a service and close the queue.
- [ ] Test the app in two or more browser windows.
- [ ] Record a 3-minute demo video.
- [ ] Complete the reflection in `SUBMISSION_REPORT.pdf` and replace generic observations with your own real testing evidence.

## Troubleshooting
- Vercel page blank: check build logs and `VITE_API_URL`.
- API CORS error: ensure Render `CLIENT_URL` exactly matches the Vercel origin.
- Refresh route returns 404: confirm Vercel is using Vite defaults and the deployment contains `index.html`.
- Database resets: check that the Render persistent disk is mounted at `/var/data` and `DATABASE_FILE` points inside it.
- Socket events do not arrive: check the API URL, Render logs and browser console. The frontend and backend must both be online.
