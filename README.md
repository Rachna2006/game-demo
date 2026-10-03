# My Simple Game

A simple browser game built with HTML, CSS, and JavaScript, deployed on [Render](https://render.com).

**Live demo:** `https://your-game-name.onrender.com` *(update after deploying)*

---

## Project Structure

```
my-game/
├── index.html      # Entry point (must be in the root folder)
├── style.css       # Game styling
├── script.js       # Game logic
├── assets/         # Images, sounds, etc. (optional)
└── README.md
```

---

## Run Locally

No build step is needed. Either:

- Double-click `index.html` to open it in your browser, **or**
- Serve it locally (recommended):

```bash
# Python
python -m http.server 8000

# or Node
npx serve .
```

Then open `http://localhost:8000`.

---

## Deploy on Render (Static Site)

This is the easiest option and is free for static sites.

### 1. Push your code to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

### 2. Create the site on Render

1. Sign in at [dashboard.render.com](https://dashboard.render.com) and connect your GitHub account.
2. Click **New +** → **Static Site**.
3. Select your game's repository.
4. Fill in the settings:

| Setting            | Value                              |
| ------------------ | ---------------------------------- |
| **Name**           | `your-game-name`                   |
| **Branch**         | `main`                             |
| **Build Command**  | *(leave blank)*                    |
| **Publish Directory** | `.` (or the folder containing `index.html`) |

5. Click **Create Static Site**.

Render will deploy your game and give you a public `onrender.com` URL.

### 3. Updating the game

Every `git push` to `main` triggers an automatic redeploy.

---

## Alternative: Deploy as a Web Service (Node.js)

Use this only if your game needs a backend (multiplayer, leaderboard, etc.).

**Requirements:** a `package.json` with a start script, for example:

```json
{
  "name": "my-game",
  "version": "1.0.0",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.19.2"
  }
}
```

And a `server.js` that serves your files and uses Render's port:

```js
const express = require("express");
const app = express();
const PORT = process.env.PORT || 3000;

app.use(express.static(__dirname));
app.listen(PORT, () => console.log(`Running on port ${PORT}`));
```

**Render settings:**

| Setting           | Value           |
| ----------------- | --------------- |
| **Environment**   | Node            |
| **Build Command** | `npm install`   |
| **Start Command** | `npm start`     |

Note: free web services spin down after inactivity, so the first load may take around 30–60 seconds.

---

## Troubleshooting

- **Blank page / 404:** make sure `index.html` is in the Publish Directory and the filename is lowercase.
- **Images or scripts not loading:** use relative paths (`./assets/hero.png`), and remember paths are case-sensitive on Render.
- **Deploy failed:** check the **Logs** tab in the Render dashboard.

---

## License

MIT — feel free to use and modify.
