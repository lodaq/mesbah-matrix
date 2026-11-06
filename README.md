# Mesbah Matrix

![Status: Under development](https://img.shields.io/badge/status-under_development-orange)

A customizable personal dashboard for productivity, learning, and daily routines. Arrange draggable, resizable widgets and open dedicated tools for tasks, focus, calendars, bookmarks, drawing, and inspiration.

[Source](https://github.com/lodaq/mesbah-matrix)

The previous deployment at `https://mesbah-matrix.vercel.app` returned HTTP 500 on 2026-11-06. No working public website is currently advertised.

## Features

- A configurable grid with widget placement, resizing, locking, and removal.
- Tasks, Kanban, calendar, focus timer, and an Eisenhower Matrix.
- A drawing canvas and Portalio bookmark workspace.
- Quran, Azkar, daily reminders, quotes, and media widgets.
- Account integration through Kinde and data services backed by Firebase.

This project is under development. Some routes and integrations depend on configured external services; the presence of a tool in the interface does not establish production readiness.

## Stack

Next.js 16, React 19, TypeScript, Tailwind CSS, shadcn/Radix UI, Zustand, Firebase, Kinde, and react-grid-layout.

## Run locally

Use Node.js 20.9 or newer and pnpm.

```sh
git clone https://github.com/lodaq/mesbah-matrix.git
cd mesbah-matrix
pnpm install
pnpm dev
```

Open http://localhost:3000. Configure your own Firebase project in an untracked `.env.local`:

```env
NEXT_PUBLIC_FIREBASE_API_KEY=
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=
NEXT_PUBLIC_FIREBASE_PROJECT_ID=
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=
NEXT_PUBLIC_FIREBASE_APP_ID=
NEXT_PUBLIC_FIREBASE_MEASUREMENT_ID=
NEXT_PUBLIC_QUOTES_API=
```

Account routes also need Kinde configuration for the local app: `KINDE_CLIENT_ID`, `KINDE_CLIENT_SECRET`, `KINDE_ISSUER_URL`, `KINDE_SITE_URL`, `KINDE_POST_LOGOUT_REDIRECT_URL`, and `KINDE_POST_LOGIN_REDIRECT_URL`. Register matching callback URLs with Kinde. Set only public client configuration in `NEXT_PUBLIC_*`; never expose server secrets through those variables.

## Development

```sh
pnpm check
pnpm exec tsc --noEmit
pnpm build
pnpm start
```

- `app/_components/`: dashboard grid and widgets.
- `app/`: tool routes, layouts, and account integration.
- `lib/`: Firebase setup, data access, and shared behavior.
- `components/`: reusable interface components.

Environment files and local account data are not source assets and must stay out of commits.

## Known verification blockers

As checked on 2026-11-06, TypeScript 7 rejects the existing `baseUrl` compiler option, and `pnpm check` reports existing lint/format findings. These need resolution before a clean release build can be claimed.
