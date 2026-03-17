# LinkShort — Vercel Frontend Deployment

## What is in this folder

| File/Folder | Purpose |
|-------------|---------|
| `index.html` | Main HTML entry point |
| `assets/` | All JavaScript and CSS (built and minified) |
| `images/` | Logo and background images |
| `favicon.svg` | Site favicon |
| `vercel.json` | Vercel routing config for single-page app |

---

## Prerequisite

You must have already deployed the backend to Railway and have your Railway URL ready.
Example: `https://linkshort-backend-production.railway.app`

---

## Environment Variables (set this in Vercel)

| Variable | Value | Required |
|----------|-------|----------|
| `VITE_API_BASE_URL` | Your Railway backend URL (no trailing slash) | YES |

Example value: `https://linkshort-backend-production.railway.app`

This is the only setting that connects the frontend to the backend.

---

## Step-by-Step Deployment

### 1. Create a GitHub Repository

- Go to github.com → New repository → name it `linkshort-frontend`
- Upload everything in this folder into the repo:
  - `index.html`
  - `assets/` folder
  - `images/` folder
  - `favicon.svg`
  - `opengraph.jpg`
  - `vercel.json`

### 2. Deploy to Vercel

1. Go to [vercel.com](https://vercel.com) and sign in
2. Click **Add New** → **Project**
3. Import your `linkshort-frontend` repo
4. Vercel will auto-detect the settings — **do not change anything**
5. Before clicking Deploy, scroll down to **Environment Variables**

### 3. Add the Environment Variable

- Name: `VITE_API_BASE_URL`
- Value: paste your full Railway URL

  Example: `https://linkshort-backend-production.railway.app`

- Click **Add**

### 4. Deploy

- Click **Deploy**
- Wait 1–2 minutes for the build to complete
- Your site is live at `https://your-project.vercel.app`

---

## Important Notes

- The `vercel.json` file handles client-side routing — all page refreshes will work correctly
- If you ever rebuild the frontend (after changing source code), copy the new `assets/` folder and `index.html` into this folder and redeploy
- The backend (Railway) and frontend (Vercel) are completely separate — each can be redeployed independently

---

## Testing the Connection

1. Open your Vercel URL
2. Try to log in with username `admin` and password `admin123`
3. If login works, the frontend and backend are connected correctly

If login fails, check:
- The `VITE_API_BASE_URL` is set correctly in Vercel (no trailing slash)
- The Railway server is running (check the health endpoint: `your-railway-url/api/health`)
