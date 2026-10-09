# Expo Starter

A small Expo (React Native) starter with NativeWind, Drizzle ORM + SQLite, Zustand and [react-native-reusables](https://github.com/mrzachnugent/react-native-reusables) UI components. It runs on iOS, Android and web.

<!-- screenshot here: iOS light/dark side by side -->

## Stack

| Area | Library |
| --- | --- |
| Framework | Expo SDK 52, React Native 0.76 (New Architecture enabled), Expo Router 4 (typed routes) |
| Styling | NativeWind v4 + Tailwind CSS, `class-variance-authority`, `tailwind-merge` |
| UI | react-native-reusables components built on `@rn-primitives` (Avatar, Button, Card, Progress, Text, Tooltip), Lucide icons |
| Local data | `expo-sqlite` + Drizzle ORM, with migrations run on startup |
| State | Zustand |
| Tooling | TypeScript, ESLint (expo + tailwindcss plugins), Prettier (sorted imports + tailwind class sorting) |

## Features

- Light/dark mode, saved in AsyncStorage. On Android the navigation bar follows the theme.
- On startup, `hooks/useInitializeApp.ts` runs the Drizzle migrations, restores the theme, and hides the splash screen once both are done.
- `db/client.ts` keeps a single Drizzle client. `db/schema.ts` has an example `users_table`.

## Project structure

```
app/          Expo Router routes (_layout, index, +not-found)
components/   ThemeToggle + ui/ primitives
db/           Drizzle schema, client, generated migrations
hooks/        useInitializeApp
lib/          color scheme, icons, utils, Android nav bar helper
```

## Getting started

```bash
bun install        # bun.lockb is committed; npm/pnpm also work
bun run ios        # or: android / web
```

Other scripts: `lint`, `lint:fix`, `clean`.

### Database migrations

After you change `db/schema.ts`, generate a new migration with drizzle-kit (see `drizzle.config.ts`):

```bash
npx drizzle-kit generate
```

## Notes

- The bundle identifiers in `app.json` are still placeholders (`com.anonymous.starterbase`). Change them before you build.
- There are no tests yet.

## Credits

The UI components and base template come from [react-native-reusables](https://github.com/mrzachnugent/react-native-reusables).
