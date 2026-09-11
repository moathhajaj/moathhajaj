# Murshid: engineering brief

[Product & investor overview](https://github.com/moathhajaj/moathhajaj/blob/main/murshid.md) ·
[Founder profile](https://github.com/moathhajaj) ·
[Discuss the implementation](mailto:moath@murshid.me?subject=Murshid%20technical%20walkthrough)

Murshid is a pre-launch Arabic-English mobile MVP with a separate operator
console. This brief summarizes the implementation and selected local
evidence without publishing application source code.

## Architecture and decisions

| Decision | Practical purpose | Review boundary |
|---|---|---|
| React Native / Expo mobile app and a separate Next.js console | Keep learner and operator workflows focused on their different tasks. | Browser previews do not validate native SDK behavior. |
| Feature modules own data access behind public interfaces | Keep routes thin and reduce dependencies between product areas. | Shared changes still need checks across their consumers. |
| Both applications consume generated database types | Keep TypeScript contracts aligned with the schema after regeneration. | Types do not replace runtime validation or authorization. |
| Server-side operator role checks | Re-check access when an operation is requested, including after role removal. | Unit tests mock the backend; hosted authorization needs separate verification. |
| English-Arabic dictionary parity tests | Catch missing translation keys in either shared dictionary. | This does not assess translation quality, screen-local copy, or RTL layouts on devices. |

The backend uses Supabase Postgres, Auth, Storage, and Edge Functions.
Database policies and server-side checks form the authorization boundary.

Implemented areas include learning and opportunity discovery, mentor
profiles and booking, session preparation, communities, event registration,
and operator review, moderation, curation, and access management.

## Selected local evidence

Recorded **11 September 2026** against the private implementation. These
focused checks are not a complete release assessment or an independent
security audit.

| Check | Recorded result | Scope |
|---|---|---|
| Repository health | 17 checks passed | Workspace structure, feature inventory, dependency boundaries, and repository consistency. |
| Booking helpers and currency formatting | 30 tests passed | Price and time calculations, client-side overlap checks, and formatting cases. |
| Operator access helpers | 10 tests passed | Missing sessions, denied or removed roles, lookup failures, and repeated access checks with mocked backend responses. |
| Translation dictionary parity | 5 tests passed | Shared English-Arabic key alignment and dictionary consistency checks. |

The source and test suites are private. Passing these checks does not
establish service delivery, real-user outcomes, or production readiness.

## Validation still ahead

- Physical iOS and Android device testing, including Arabic/English layouts.
- Provider-dependent native media and payment checks. Real-money payments
  remain disabled pending end-to-end validation.
- Hosted authorization checks and the complete release verification contract.
- A controlled pilot with real participants to evaluate the product hypothesis.

Demo catalog content is used in testing; it is not customer traction.

For a walkthrough of the implementation and its validation priorities,
contact **[moath@murshid.me](mailto:moath@murshid.me?subject=Murshid%20technical%20walkthrough)**.
