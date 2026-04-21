# Resolvd — Frontend

React Native / Expo app. Backend is a **separate repo** (not in here) and is already deployed.

---

## First-time setup

```bash
git clone https://github.com/Joakimpedev/resolvd-frontend.git
cd resolvd-frontend
npm install
cp .env.example .env
npm start
```

A QR code appears in the terminal. Open **Expo Go** on your phone and scan it. Log in with the credentials sent to you separately.

Phone and computer must be on the same Wi-Fi. If that fails, run `npm start -- --tunnel` instead.

---

## Making changes

```bash
git pull                              # get latest
# edit files
git add -A
git commit -m "describe what changed"
git push
```

That's it — pushes directly to `main`.

---

## Scope

### Touch freely

- `theme/` — colors, spacing, typography, icons
- `components/` — styling and layout of reusable UI
- `app/` — layouts of existing screens
- `assets/` — icons, splash

### Don't touch

- `lib/` — API client, auth, data queries. It works; leave it alone.
- `package.json`, `package-lock.json` — don't add or bump dependencies
- `app.json`, `eas.json`, `metro.config.js`, `tsconfig.json` — build config
- `.env`, `.env.example`, `.npmrc` — environment and install config
- `index.ts`, `expo-env.d.ts` — entry points

### Don't create

- **New API calls** (`fetch`, new `api(...)` calls) — the set of endpoints is fixed
- **New data types or models** (e.g. `Notification`, `Comment`) — these would need matching backend work
- **New screens that load new kinds of data from the backend** — tweaking layout on existing screens is fine
- **New npm packages** — use what's already installed

### If you want something outside this scope

Ping Joakim. Describe what you want and what data it needs. Don't improvise — a new screen that needs a new endpoint is a backend change first, frontend change second.

---

## For AI coding assistants (Claude Code, Cursor, etc.)

If an AI is helping edit this repo, it needs to know:

- **The backend is not in this repo.** The API client in `lib/` calls endpoints defined in a separate backend repo that you cannot see. If fetch calls reference endpoints whose implementation isn't visible here, that's expected. **Do not try to "fix" or regenerate them.**
- **Do not add new fetch calls, new API endpoints, new data models, or new dependencies.** The scope of allowed work is listed under "Scope" above.
- **Do not modify `lib/`**, even if something looks simplifiable or unused.
- **Do not modify `package.json`, build config, or environment files.**
- **Stay within the task you were asked to do.** Don't sweep through unrelated files "improving" them.

If the requested change can't be done within the Touch Freely scope, stop and say so — don't expand scope.

---

## Scripts

- `npm start` — dev server
- `npm run typecheck` — TypeScript check

---

## Troubleshooting

**`EXPO_PUBLIC_API_URL is not set`** → run `cp .env.example .env` and restart.

**Can't scan QR / app won't load** → same Wi-Fi; otherwise `npm start -- --tunnel`.

**Login fails** → ping Joakim for a fresh test account.
