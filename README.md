# Resolvd — Frontend

React Native / Expo app. The backend API is already deployed — nothing to run server-side.

## Setup

```bash
npm install
cp .env.example .env
npm start
```

A QR code appears. Open **Expo Go** on your phone, scan it, the app loads on your device.

Phone and computer must be on the same Wi-Fi network. If that doesn't work, run `npm start -- --tunnel` instead.

Login with the credentials sent to you separately.

## Layout

```
app/          # Screens (expo-router)
  (auth)/     # Login screens
  (app)/      # Main app screens
components/   # Reusable UI
theme/        # Colors, spacing, typography
assets/       # Icons, splash
lib/          # API client, auth, data layer — don't touch
```

## Scripts

- `npm start` — dev server
- `npm run typecheck` — TypeScript check
- `npm run ios` — iOS Simulator build (macOS + Xcode required)

## Workflow

Work on a branch, push, open a PR on GitHub — or push to `main` directly if you prefer.

```bash
git checkout -b theme/whatever
# make changes
git add -A
git commit -m "describe the change"
git push
```

## Troubleshooting

**"EXPO_PUBLIC_API_URL is not set"** → you haven't created `.env`. Run `cp .env.example .env` and restart.

**Login fails** → check with Joakim that the test account is still valid.
