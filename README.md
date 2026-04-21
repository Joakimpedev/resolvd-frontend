# Resolvd — Frontend

React Native / Expo app for Resolvd. Connects to a hosted backend API — you do not need to run anything server-side locally.

## Setup

### 1. Prerequisites

- **Node.js** 20 or newer
- **Expo Go** installed on your phone (App Store / Play Store)
- Your phone and computer on the same Wi-Fi network

### 2. Install and configure

```bash
npm install
cp .env.example .env
```

The `.env` file points the app at the hosted backend. Don't change the URL.

### 3. Run

```bash
npm start
```

A QR code appears in the terminal. Open **Expo Go** on your phone and scan it. The app loads on your device.

### 4. Log in

Use the test account credentials you've been given (ask Marius if you don't have them yet).

## Project layout

```
app/            # Screens (expo-router file-based routing)
  (auth)/       # Login screens
  (app)/        # Main app screens — after login
  _layout.tsx   # Root layout
  index.tsx     # Entry redirect

components/     # Reusable UI components
theme/          # Colors, spacing, typography tokens
  tokens.ts
  typography.ts
  icons.ts

assets/         # Icon, splash
lib/            # API client, auth, React Query setup — DO NOT EDIT (see CONTRIBUTING.md)
```

## Scripts

- `npm start` — run the dev server, scan with Expo Go
- `npm run typecheck` — check types with TypeScript
- `npm run ios` — build a dev client for iOS Simulator (requires Xcode, macOS only — not needed for normal work)

## Troubleshooting

**QR code won't scan / app won't load**
Make sure your phone and computer are on the same Wi-Fi network. If still stuck, in the terminal press `s` to switch to Expo Go mode, or run `npm start -- --tunnel` to use a tunnel connection.

**"EXPO_PUBLIC_API_URL is not set"**
You haven't created `.env`. Run `cp .env.example .env` and restart `npm start`.

**Login fails**
Check that the API URL in `.env` still matches `.env.example`. If credentials are wrong, ask Marius for the current test account.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for what's in-scope for this repo and how to propose changes.
