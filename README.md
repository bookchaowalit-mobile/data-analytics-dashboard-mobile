# Analytics Dashboard — Mobile

## Template copy

This repo is one of the name-substituted Expo SDK 53 / Expo Router template
copies in the `bookchaowalit-mobile` org. The canonical template is
[`bookchaowalit-mobile/community-hub-mobile`](https://github.com/bookchaowalit-mobile/community-hub-mobile).
Consolidating or archiving this copy is pending owner decision D5 (BD-033); see
`repository-catalog/portfolio/MOBILE-CONSOLIDATION-2026-10.md` in solo-empire.
This copy keeps its own code and its own copy of the CI workflow (no shared package).

React Native mobile app (Expo) for **Analytics Dashboard**.

Part of [Chaowalit Greepoke](https://bookchaowalit.com)'s 101 Portfolio Projects.

## Tech Stack

- **Framework:** Expo SDK 53 + Expo Router
- **Language:** TypeScript
- **Navigation:** Expo Router (file-based)
- **UI:** React Native + Ionicons

## Features

- **Dashboard** (home tab): KPI cards for visitors, sign-ups, revenue and
  conversion rate over the last 7/14/30 days, each with the change versus the
  previous period of the same length.
- **Daily trend chart**: bar chart per metric for the selected range.
- Uses deterministic sample data (`lib/analytics.ts`); connecting a real
  analytics API is on the backlog.

## Getting Started

```bash
npm ci
npx expo start
```

## Validation

```bash
npm run validate   # expo lint + tsc --noEmit + vitest
npx expo export --platform android --output-dir dist   # bundle smoke check
```

Pure logic lives in `lib/` and is unit-tested with Vitest (`lib/*.test.ts`).
CI (`.github/workflows/ci.yml`) calls the shared
`bookchaowalit/platform-ci-workflows` v1.1.1 (pinned by SHA): `npm ci`, lint,
typecheck, `vitest run`, then the Android JS bundle export, plus the security
scans (gitleaks, Semgrep, OSV-Scanner, Trivy). Nothing is masked. Reviewed
scanner exceptions, each with a reason and expiry, are in `osv-scanner.toml`
and `.trivyignore`. EAS / Expo cloud builds are not run in CI: they need the
owner's Expo account (`EXPO_TOKEN`), so they stay a manual owner step.

## Build

```bash
# Android
npx eas build --platform android --profile preview

# iOS
npx eas build --platform ios --profile preview
```

## Related

- **Frontend:** [bookchaowalit-website/analytics-dashboard-frontend](https://github.com/bookchaowalit-website/analytics-dashboard-frontend)
- **Portfolio:** [bookchaowalit.com](https://bookchaowalit.com)

## License

MIT
