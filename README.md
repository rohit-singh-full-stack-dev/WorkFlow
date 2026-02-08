# WorkFlow — Staff Tracking & Attendance Management

A **production-ready** staff tracking and attendance platform built for teams that need real-time location visibility, automated attendance, and role-based management—without expensive enterprise solutions.

## Why WorkFlow?

- **Live location tracking** — See where your team is during work hours, with 2-minute interval updates and automatic start/stop on check-in/out.
- **Attendance built-in** — GPS-verified check-in/check-out, automatic working hours, and same-day edits for managers.
- **Clear roles** — Staff (check-in only), Managers (team view + edits), Admin (full control, reports, settings).
- **One codebase, multiple surfaces** — Mobile app for field staff, web dashboard for managers and admins.

Ideal for field teams, operations, and small-to-mid businesses that need accountability and visibility without complex setup.


## What’s Included

| Area | Description |
|------|-------------|
| **Mobile app (Expo)** | Staff check-in/out, background location tracking, team view for managers, history, profile. |
| **Admin dashboard (Next.js)** | Staff & device management, attendance, live map, reports, settings. Responsive for desktop and tablet. |
| **Backend (Supabase)** | Auth (OTP), PostgreSQL, Row Level Security (RLS), realtime. Migrations for profiles, attendance, location logs, teams. |


## Tech Stack

| Layer | Technologies |
|-------|--------------|
| **Mobile** | Expo (React Native), Expo Router, NativeWind (Tailwind), React Native Maps, Supabase client |
| **Admin** | Next.js 16, React 19, Tailwind CSS, Radix UI, Recharts, Supabase, Google Maps |
| **Backend** | Supabase (Auth, Postgres, RLS, Realtime) |


## Features

- **OTP login** — Phone-based auth, no passwords.
- **GPS check-in/out** — Time and location captured; working hours calculated automatically.
- **Background location** — Updates every 2 minutes during work hours; stops after check-out.
- **Role-based access** — Staff / Manager / Admin with appropriate data and UI.
- **Live map** — Managers see team locations; admins see full picture.
- **Day-level routes** — View a staff member’s path for a selected date (polyline on map).
- **Reports & export** — Attendance and analytics from the admin dashboard.
- **Data retention** — Configurable retention (e.g. 30-day location logs) via migrations.


## Project Structure

```
WorkFlow/
├── app/                    # Expo app (staff + manager mobile flows)
│   ├── (manager)/          # Manager: team, map, member detail, day map
│   ├── auth/               # Login, signup
│   ├── history.tsx
│   ├── profile.tsx
│   └── ...
├── admin/                  # Next.js admin dashboard
│   └── src/app/            # Attendance, devices, map, reports, settings, staff
├── components/              # Shared UI (auth, cards, etc.)
├── lib/                    # Auth context, Supabase client, location service
├── hooks/                  # Location tracking, theme
├── supabase/migrations/    # Schema and RPCs (profiles, attendance, location_logs, teams)
└── assets/
```


## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn
- Supabase project (for auth and database)
- For mobile: Android Studio (Android) / Xcode (iOS simulator)

### 1. Install dependencies

```bash
# Mobile app
npm install

# Admin dashboard (optional, for web admin)
cd admin && npm install
```

### 2. Configure environment

Add your Supabase URL and anon key (e.g. in `.env` or app config) for both the Expo app and the admin dashboard.

### 3. Run the app

```bash
# Start Expo (mobile + web)
npm start
# Then: press 'a' for Android, 'w' for web, or scan QR with Expo Go

# Admin dashboard (separate terminal)
cd admin && npm run dev
```

### 4. Database

Apply migrations in `supabase/migrations/` to your Supabase project (via Supabase CLI or Dashboard SQL editor).

## Build & Deploy

- **Android:** `npm run build:android:preview` or `build:android:production` (EAS Build).
- **Admin:** `cd admin && npm run build && npm run start` (or deploy to Vercel/Node host).

## Security & Compliance

- **Row Level Security (RLS)** — All access controlled in Postgres by role (staff/manager/admin).
- **Tracking only during work** — Location is sent only after check-in and stops at check-out.
- **Transparent use** — Designed for internal use with clear policies; tracking limited to work hours.

## Summary

WorkFlow is a complete, production-oriented solution for staff tracking and attendance: mobile app for the field, web dashboard for management, and Supabase for scalable auth and data—suitable for portfolios and client demos on Upwork.

For detailed product and implementation notes, see [PROJECT_CONTEXT.md](./PROJECT_CONTEXT.md).
