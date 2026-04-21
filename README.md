# Resolvd — Frontend

React Native / Expo app. Backend is already deployed.

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

## Layout

```
app/          Screens (expo-router)
  (auth)/     Login
  (app)/      Main app tabs
components/   Reusable UI
theme/        Colors, spacing, typography
assets/       Icons, splash
lib/          API client, auth — don't touch
```

**Touch:** `theme/`, `components/`, `app/`, `assets/`
**Don't touch:** `lib/`, `package.json`, `app.json`, `metro.config.js`, `tsconfig.json`

If you want to add something that needs data (e.g. a new list of things from the backend), ping Joakim first.

---

## Scripts

- `npm start` — dev server
- `npm run typecheck` — TypeScript check

---

## Troubleshooting

**`EXPO_PUBLIC_API_URL is not set`** → run `cp .env.example .env` and restart.

**Can't scan QR / app won't load** → same Wi-Fi; otherwise `npm start -- --tunnel`.

**Login fails** → ping Joakim for a fresh test account.
