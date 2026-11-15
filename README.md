# SLIIT CA Calculator

A lightweight, responsive web app that helps SLIIT students track continuous assessment (CA) marks and quickly see what final examination mark they need to reach a target grade.

**Live site:** [sliitca.tharu.site](https://sliitca.tharu.site)

> **Important:** Always verify assessment weights and grading rules against the latest official module outline / SLIIT handbook. Module structures can change between academic years.

## Features

- **Preset modules** – Computing modules organised by academic year and semester with realistic assessment breakdowns
- **Custom modules** – Create your own modules with any number of assessment components
- **Smart calculations**
  - Enter obtained marks for each CA component
  - Automatic calculation of remaining final-exam weight
  - Instantly see the final mark required for every grade (A+, A, A-, …)
- **Dashboard** – Overview of all modules you have entered marks for
- **Local persistence** – Theme preference and entered marks are saved in the browser (localStorage)
- **Theme support** – Light / Dark / System
- **Fully responsive** – Works well on desktop, tablet and mobile

## Tech stack

- HTML, CSS, Vanilla JavaScript
- Hosted on **Cloudflare Workers Static Assets**

No backend or database is required. Everything runs client-side.

## Project structure

```text
sliit-ca-calculator/
├── public/
│   └── index.html          # The entire application
├── wrangler.jsonc
├── README.md
└── .gitignore
```

## Run locally

1. Clone the repository:

```bash
git clone https://github.com/TharuPinsara/sliit-ca-calculator.git
cd sliit-ca-calculator
```

2. Open `public/index.html` in a browser  
   **or** use a local static server (e.g. VS Code Live Server, `npx serve public`, etc.).

## Deploy to Cloudflare Workers

### 1. `wrangler.jsonc`

```jsonc
{
  "$schema": "./node_modules/wrangler/config-schema.json",
  "name": "sliit-ca-calculator",
  "compatibility_date": "2026-11-16",
  "assets": {
    "directory": "./public"
  }
}
```

Update the `compatibility_date` if you deploy later.

### 2. Deploy from your machine (optional)

```bash
npm install -D wrangler
npx wrangler login
npx wrangler deploy
```

### 3. Automatic deployments via GitHub

1. Push the repo to GitHub.
2. In the Cloudflare Dashboard → **Workers & Pages** → **Create application**.
3. Connect the GitHub repository.
4. Configure:
   - Worker name: `sliit-ca-calculator`
   - Production branch: `main`
   - Root directory: `/`
   - Build command: *(leave empty)*
   - Deploy command: `npx wrangler deploy`
5. Deploy.

Subsequent pushes to the production branch will trigger new deployments automatically.

## Custom domain

### Domain ownership note

A subdomain must belong to a domain you control:

- If you own **`tharu.site`**, the correct hostname is **`sliitca.tharu.site`**.
- **`sliitca.tharu.shop`** belongs to **`tharu.shop`** and requires ownership of that domain as well.

### Adding the custom domain

1. Open the Worker in the Cloudflare Dashboard.
2. Go to **Settings** → **Domains & Routes** (or **Custom Domains**).
3. Click **Add Custom Domain** and enter the hostname you control (e.g. `sliitca.tharu.site`).
4. Complete any DNS / nameserver steps Cloudflare requests.
5. Wait for the TLS certificate to be issued, then test the HTTPS URL.

## Updating the app

1. Edit `public/index.html`.
2. Test locally.
3. Commit and push:

```bash
git add .
git commit -m "Update CA calculator"
git push
```

Cloudflare will redeploy automatically if Git integration is enabled.

## Data & privacy

All data (marks, custom modules, theme preference) is stored only in the user’s browser via `localStorage`. Nothing is sent to any server.

## License

Add a license of your choice before allowing others to reuse or redistribute the project. If no license is present, do not assume the repository is free to reuse.
