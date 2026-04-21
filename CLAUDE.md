# Rules for AI coding tools

This file is read automatically by Claude Code, Cursor, and similar tools. Follow these rules.

## What this repo is

React Native / Expo frontend. The backend lives in a **separate repo** you cannot see. `lib/api.ts` calls endpoints defined in that backend — their implementation is not in this repo. **This is expected. Do not try to regenerate, stub, or "fix" missing types or endpoints.**

## Allowed work

Only edits inside these folders:

- `theme/` — colors, spacing, typography, icons
- `components/` — styling and layout
- `app/` — layouts of existing screens
- `assets/` — icon / splash images

## Forbidden

- Do not edit `lib/` (API client, auth, queries). Even if something looks unused or simplifiable.
- Do not edit `package.json`, `package-lock.json`, `.npmrc`, `app.json`, `eas.json`, `metro.config.js`, `tsconfig.json`, `index.ts`, `expo-env.d.ts`, `.env*`.
- Do not add new `fetch()` calls, new API endpoints, new data types/models, or new screens that load new kinds of data from the backend.
- Do not install, add, or bump npm packages.
- Do not sweep across unrelated files "improving" things. Stay within the specific task.

## If a task can't be done within scope

Stop and say so. Do not expand scope, invent new endpoints, mock out data, or assume new backend work will happen. Backend changes are Joakim's job, not yours.

## If in doubt

Refuse to proceed and ask. Always better to ask than to modify forbidden files.
