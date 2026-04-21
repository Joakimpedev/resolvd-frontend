# AI setup instructions

You are an AI coding assistant (Claude Code, Cursor agent, or similar) helping a non-technical user get the Resolvd frontend app running on their computer. The user has just opened you in a terminal or editor, probably in an empty folder. **You do every step below. Do not ask the user to run commands — run them yourself. Only ask the user when you truly cannot proceed (e.g. an installer prompts for a password you can't provide).**

The repo you are setting up is: **https://github.com/Joakimpedev/resolvd-frontend**

---

## 1. Ensure prerequisites are installed

Check each. Install silently if missing.

### Node.js 20+

Run `node --version`. If missing or older than 20:

- **Windows:** `winget install OpenJS.NodeJS.LTS`
- **macOS (Homebrew):** `brew install node`
- **Linux (Ubuntu/Debian):** `sudo apt-get install -y nodejs npm`
- If none of the above work, tell the user to download and install Node.js LTS from https://nodejs.org/, then wait for them to confirm.

### Git

Run `git --version`. If missing:

- **Windows:** `winget install Git.Git`
- **macOS:** usually pre-installed; otherwise `brew install git`
- **Linux:** `sudo apt-get install -y git`

---

## 2. Get the repo

Check if the current folder is already the `resolvd-frontend` repo (look for a `package.json` whose `name` is `resolvd-frontend`).

**If it is:** skip to step 3.

**If it isn't:** clone the repo into the current folder.

```
git clone https://github.com/Joakimpedev/resolvd-frontend.git
cd resolvd-frontend
```

If `git clone` fails because the folder already contains `resolvd-frontend/`, just `cd resolvd-frontend`.

All subsequent steps run inside the `resolvd-frontend` folder.

---

## 3. Install project dependencies

```
npm install
```

Wait for it to complete. This can take a few minutes on first run.

---

## 4. Create the `.env` file

If `.env` does not exist, copy from `.env.example`:

- **Unix / macOS / Git Bash:** `cp .env.example .env`
- **Windows CMD:** `copy .env.example .env`
- **Windows PowerShell:** `Copy-Item .env.example .env`

---

## 5. Start the dev server

```
npm start
```

This prints a QR code in the terminal.

---

## 6. Tell the user

Say exactly this:

> Setup complete. If you don't have **Expo Go** on your phone yet, install it from the App Store or Play Store. Then open Expo Go and scan the QR code above. The app will load. Log in with the credentials Joakim sent you.

Wait for the user to confirm it's working. If they hit an error, help them resolve it.

---

## Rules for making changes (read this before editing any code)

When the user asks you to modify this app later, obey these rules.

### Files you may edit

- `theme/` — colors, spacing, typography, icons
- `components/` — styling and layout of reusable UI
- `app/` — layouts of existing screens
- `assets/` — icons, splash

### Files you must NOT edit

- `lib/` (API client, auth, data queries)
- `package.json`, `package-lock.json`, `.npmrc`
- `app.json`, `eas.json`, `metro.config.js`, `tsconfig.json`
- `.env`, `.env.example`
- `index.ts`, `expo-env.d.ts`

### Things you must NOT do

- Add new `fetch()` calls or API endpoints
- Add new data types, models, or interfaces for data from the backend
- Add new screens that load new kinds of data from the backend
- Add, remove, or bump npm packages
- Sweep through unrelated files "improving" them — stay narrow to the specific task

### Important context

The backend is a **separate repo you cannot see**. `lib/api.ts` calls endpoints implemented in that other repo. If fetch calls reference endpoints whose implementation isn't visible here, that is expected — do not try to "fix," regenerate, or stub them.

### When a task needs backend work

Stop. Tell the user:

> This change needs backend work (a new endpoint, a new data field, etc.). Joakim has to build that in the backend repo first. Can you describe what you need so I can pass it on?

Do not invent endpoints, mock data, or scaffolding for work that hasn't been done.

See also `CLAUDE.md` for the rule list in condensed form.

---

## Pushing changes to GitHub

When the user says "save this," "send this to Joakim," "push this," or similar, run:

```
git add -A
git commit -m "short description of the change"
git push
```

If `git push` fails with an authentication error:

- **Cursor / VS Code users:** tell them to open the Source Control sidebar and sign in with GitHub — the editor handles the rest.
- **Terminal-only:** install GitHub CLI and authenticate
  - Windows: `winget install GitHub.cli` then `gh auth login`
  - macOS: `brew install gh` then `gh auth login`
  - Linux: follow https://github.com/cli/cli/blob/trunk/docs/install_linux.md
  - Choose HTTPS, log in via browser, then retry `git push`

If the push is refused with "permission denied" even after auth, the user isn't a collaborator yet. Tell them:

> You don't have push access yet. Reply to Joakim with your GitHub username — he'll add you as a collaborator, then you can push.
