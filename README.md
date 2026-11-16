# 🎓 SLIIT CA & GPA Calculator

A lightweight, responsive web app designed for SLIIT undergraduates. Track your Continuous Assessment (CA) marks, find out exactly what you need on the final exam to reach your target grade, and calculate your overall GPA - all in one place.

🌐 **Live site:** [sliitca.tharu.site](https://sliitca.tharu.site)

> **💡 Important Note:** Always verify assessment weights and grading rules against your latest official module outline or the SLIIT student handbook, as module structures can change between academic years.

---

## ✨ Features

- **Smart CA Calculations** - Enter the marks you've obtained for each CA component. The app automatically calculates your remaining final-exam weight and shows the exact final exam mark needed to secure every possible grade boundary.
- **Preset Modules** - Jump right in with pre-configured computing modules sorted by academic year and semester, featuring accurate assessment breakdowns.
- **Custom Modules** - Taking a module that isn't on the list? Create your own custom modules with any number of assessment components and custom weights.
- **GPA Calculator** - Calculate your semester or overall GPA in seconds. Enter module names, credits, and grades (A+, A, A-, etc.) to instantly see your Total GPA and Credits.
- **Dashboard Overview** - Get a clear view of all your ongoing modules, current CA performance, and completion status in one clean interface.
- **Privacy-First & Offline Ready** - No accounts, no logins, and no databases. Everything (including theme preferences and entered marks) is saved securely in your browser's local storage.
- **Themes** - Choose between Light, Dark, or System themes.
- **Fully Responsive** - Optimized for desktop, tablet, and mobile devices.

---

## 💻 Tech Stack

- **Frontend:** HTML, CSS, Vanilla JavaScript
- Everything runs on the client-side.

---

## 📂 Project Structure

```text
sliit-ca-calculator/
├── public/
│   └── index.html          
├── wrangler.jsonc         
├── README.md
└── .gitignore
```

## 🚀 Run Locally

Clone the repository:

```bash
git clone https://github.com/TharuPinsara/sliit-ca-calculator.git
cd sliit-ca-calculator
```

Open `public/index.html` in your favorite browser.  
(Alternatively, use a local static server like VS Code Live Server or `npx serve public` for hot-reloading).

## ☁️ Deploy to Cloudflare Workers

### 1. Configure `wrangler.jsonc`

```json
{
  "$schema": "./node_modules/wrangler/config-schema.json",
  "name": "sliit-ca-calculator",
  "compatibility_date": "2026-11-16",
  "assets": {
    "directory": "./public"
  }
}
```

(Update the `compatibility_date` to today's date if you are deploying later).

### 2. Deploy from your machine (Optional)

```bash
npm install -D wrangler
npx wrangler login
npx wrangler deploy
```

### 3. Automatic Deployments via GitHub (Recommended)

1. Push your local repository to GitHub.
2. Go to your Cloudflare Dashboard - Workers & Pages - Create application.
3. Connect your GitHub account and select this repository.
4. Configure the build settings:
   - **Worker name:** `sliit-ca-calculator`
   - **Production branch:** `main`
   - **Root directory:** `/`
   - **Build command:** (leave empty)
   - **Deploy command:** `npx wrangler deploy`
5. Click Deploy. Subsequent pushes to your `main` branch will now trigger new deployments automatically.

### 4. Adding a Custom Domain

1. Open your newly deployed Worker in the Cloudflare Dashboard.
2. Navigate to Settings - Domains & Routes (or Custom Domains).
3. Click Add Custom Domain and enter your personal domain.
4. Complete any DNS / nameserver steps Cloudflare requests.
5. Wait a few minutes for the TLS certificate to issue, and your site is live.

## 🔄 Updating the App

Making changes is easy since the entire app lives in one file:

1. Edit the code in `public/index.html`.
2. Test your changes locally.
3. Commit and push to GitHub:

```bash
git add .
git commit -m "Update CA calculator layout"
git push
```

(Cloudflare will automatically catch the push and redeploy your site in seconds).

## 🔒 Data & Privacy

We respect your data. All data - including your CA marks, custom modules, GPA inputs, and theme preferences - is stored only in your browser via `localStorage`. Absolutely nothing is tracked or sent to any external servers.

