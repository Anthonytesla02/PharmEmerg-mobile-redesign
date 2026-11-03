# PharmEmerg

Mobile-first pharmacy emergency and trauma training simulator, adapted from https://github.com/Anthonytesla02/med-triage.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm --filter @workspace/pharm-emerg run dev` — run the PharmEmerg web app
- `pnpm --filter @workspace/pharm-emerg run typecheck` — typecheck the web app
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspace, React, Vite, TypeScript, and Tailwind CSS
- Case content, evaluation, and profile progression currently run client-side and persist in localStorage

## Where things live

- `artifacts/pharm-emerg/` — the runnable PharmEmerg web app.
- `artifacts/pharm-emerg/src/components/` — challenge, simulation, debrief, learning, profile, and patient UI.
- `artifacts/pharm-emerg/src/data/` — case library, treatment supplies, drug monographs, and STG references.
- `artifacts/pharm-emerg/src/game/rules.ts` — case evaluation, scoring, progression, and badges.
- `artifacts/pharm-emerg/src/types/clinical.ts` — clinical case, action, result, and profile types.

## Architecture decisions

- The app is a mobile-first web app, not a native mobile app.
- Keep clinical scoring and case evaluation separate from presentation changes.

## Product

- Learners can practice emergency cases, apply treatments, escalate to EMS, review a scored debrief, study STGs and medication monographs, and track progression.
- The active case must keep direct access to Patient, Treatments, and Action Log available on mobile without requiring a scroll back to the top.
- Main mobile navigation should keep Challenge, Learning, and Profile one tap away.

## User preferences

- Make substantial, professional design improvements across the full app, with mobile-first navigation, tabs, collapsible sections, and loading skeletons.

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
