# StudyPetal Premium Supabase Project

StudyPetal is a premium animated study productivity app built with Vite, React, Framer Motion, Supabase Auth, and Supabase Postgres.

## What Is Included

- Supabase authentication with login and signup
- Persistent user sessions
- Protected dashboard routes
- Supabase database integration
- Row level security policies
- Screen time entries
- Pomodoro sessions
- Study planner tasks
- Analytics event storage
- CRUD functionality for planner and screen time data
- Toast notifications
- Loading and error states
- Premium animated landing page
- Framer Motion page transitions
- Animated dashboard cards
- Glowing productivity widgets
- Weekly focus chart
- Subject allocation rings
- Glassmorphism cards
- Gradients and hover effects
- Netlify production build setup

## Project Structure

```text
.
├── app.js
├── index.html
├── styles.css
├── package.json
├── package-lock.json
├── vite.config.js
├── netlify.toml
├── README.md
├── .env.example
├── config.example.js
├── scripts/
│   ├── create-config.mjs
│   └── verify-supabase.mjs
└── supabase/
    └── schema.sql
```

## Local Setup

Install dependencies:

```bash
npm install
```

Create `.env` in the project root:

```bash
VITE_SUPABASE_URL=https://your-project-ref.supabase.co
VITE_SUPABASE_ANON_KEY=your-public-anon-key
```

Run locally:

```bash
npm run dev
```

Build for production:

```bash
npm run build
```

Run syntax checks:

```bash
npm run check
```

## Supabase Setup

1. Create a Supabase project.
2. Open the Supabase SQL editor.
3. Run `supabase/schema.sql`.
4. In Supabase Authentication settings, add your local and deployed URLs to allowed redirect URLs.
5. Copy your project URL and anon key into `.env` and Netlify environment variables.

## Database Tables

The app uses these Supabase tables:

- `profiles`
- `screen_time_entries`
- `pomodoro_sessions`
- `study_planner_tasks`
- `analytics_events`

All user-owned data is protected by row level security and scoped to `auth.uid()`.

## Netlify Deployment

Set these environment variables in Netlify:

```bash
VITE_SUPABASE_URL=https://your-project-ref.supabase.co
VITE_SUPABASE_ANON_KEY=your-public-anon-key
```

Netlify configuration:

```toml
[build]
  command = "npm run build"
  publish = "dist"
```

The app uses static hosting with Vite and Supabase as the backend.

## Verification Notes

Verified locally:

- Production build passes with `npm run build`
- Syntax checks pass with `npm run check`
- Built app loads with no browser console errors
- Protected dashboard route redirects to login when signed out
- Supabase table endpoints and anonymous RLS were verified

Full authenticated CRUD verification requires a confirmed Supabase user session. If email confirmation is enabled, confirm a test user before running:

```bash
node scripts/verify-supabase.mjs
```

## Main Files

- `app.js`: React app, Supabase logic, Framer Motion transitions, dashboard widgets, CRUD handlers
- `styles.css`: premium dashboard styling, glassmorphism, gradients, charts, glow effects
- `supabase/schema.sql`: Postgres schema, indexes, triggers, and RLS policies
- `netlify.toml`: Netlify build and redirect setup
- `vite.config.js`: Vite build configuration
- `scripts/verify-supabase.mjs`: Supabase verification utility

## Current Status

The project is production-ready for Netlify once Supabase environment variables are configured and the SQL schema has been applied.
