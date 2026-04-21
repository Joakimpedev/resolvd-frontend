# AI setup instructions

You are an AI coding assistant helping a non-technical user set up this Expo app. Do every step yourself. Only ask the user when you truly cannot proceed.

## 1. Install prerequisites if missing

Check each. Install if missing.

- **Node.js 20+** (`node --version`):
  - Windows: `winget install OpenJS.NodeJS.LTS`
  - Mac with Homebrew: `brew install node`
  - Neither available: direct the user to download the LTS installer from nodejs.org, wait for them.
- **Git** (`git --version`):
  - Windows: `winget install Git.Git`
  - Mac: usually pre-installed; otherwise `brew install git`

## 2. Install project dependencies

```
npm install
```

## 3. Create .env

If `.env` does not exist, copy from `.env.example`:

- Unix / Git Bash: `cp .env.example .env`
- Windows CMD / PowerShell: `copy .env.example .env`

## 4. Start the dev server

```
npm start
```

## 5. Tell the user

When the QR code appears, say exactly:

> Setup is done. Install **Expo Go** on your phone from the App Store or Play Store if you haven't yet, then scan the QR code above with Expo Go. Log in with the credentials Joakim sent you.

---

## Rules for making changes later

When the user asks you to modify this app:

### Allowed

- Edit files only in: `theme/`, `components/`, `app/`, `assets/`
- Changes: colors, spacing, typography, component styling, screen layouts, icon/splash swaps

### Forbidden

- Do not edit: `lib/`, `package.json`, `package-lock.json`, `.npmrc`, `app.json`, `eas.json`, `metro.config.js`, `tsconfig.json`, `.env*`, `index.ts`, `expo-env.d.ts`
- Do not add new `fetch()` calls, API endpoints, data types/models, or npm packages
- Do not create new screens that load new kinds of data from the backend
- Do not sweep through unrelated files "improving" them

### Context you need to know

The backend is a **separate repo you cannot see**. `lib/api.ts` calls endpoints implemented in that other repo. If fetch calls reference endpoints whose implementation isn't visible here — that's expected. Do not try to "fix" them, regenerate types, or stub missing code.

### If a task needs backend work

Stop. Tell the user: "This needs a change in the backend repo. Joakim has to do that first." Do not invent endpoints, new data models, or mock responses.

See `CLAUDE.md` for the full rule list.

---

## Pushing changes to GitHub

When the user says they want to save / send / push their changes, run:

```
git add -A
git commit -m "short description of the change"
git push
```

If `git push` fails with an authentication error:

- If the user is in Cursor or VS Code: tell them to open the Source Control panel and sign in with GitHub — the editor handles auth
- Otherwise: install GitHub CLI and authenticate
  - Windows: `winget install GitHub.cli` then `gh auth login`
  - Mac: `brew install gh` then `gh auth login`

After that, retry `git push`.
