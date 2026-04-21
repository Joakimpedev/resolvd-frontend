# Contributing

This repo is the **frontend** of Resolvd. The backend (API, database, admin panel) lives in a separate repo you don't have access to. That's deliberate — it keeps the scope of this project tight and avoids accidentally breaking data.

## What's in scope

You can freely change:

- **`theme/`** — colors, spacing, typography, icons. Most visual work happens here.
- **`components/`** — styles, layout, visual structure of reusable components.
- **`app/`** — screen layouts, visual structure of screens.
- **`assets/`** — icons, splash screens, fonts (ask before swapping brand assets).

If you want to add a new reusable visual component, go for it — put it in `components/`.

## What's out of scope

Please **don't** touch:

- **`lib/`** — API client, auth, React Query setup, config. This is the data layer. Changes here likely need backend changes too.
- **`package.json`** dependencies — ask before adding or bumping packages.
- **`app.json`, `eas.json`, `metro.config.js`, `tsconfig.json`** — build and project config.
- **Network calls** — don't add new `fetch()` or API calls. If a screen needs data that isn't already wired up, that's a backend conversation (see below).

## If you want to add something that needs data

Open an issue describing what you want to add and what data it needs. Example:

> I want to add a "Featured articles" carousel on the home screen. It needs an endpoint that returns the 5 most recent featured articles with title, thumbnail, and short description.

We'll discuss, build the backend piece if it makes sense, then you build the frontend against the new endpoint. Backend leads, frontend follows.

## Workflow

1. Create a branch for your change: `git checkout -b theme/adjust-colors`
2. Make your changes
3. Run `npm run typecheck` — must pass
4. Test in Expo Go on a real device
5. Commit and push
6. Open a PR. Describe **what** changed and **why** (screenshots welcome for visual changes)

## Testing

No automated tests yet — verification is manual via Expo Go. Before opening a PR:

- Log in with the test account
- Walk through the main flows (login → home → detail screens)
- Check at least one iOS device and, if possible, one Android
- Confirm nothing is visibly broken

## Questions

Ask in our shared channel — don't guess. Especially on anything touching `lib/` or data.
