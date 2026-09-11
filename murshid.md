# Murshid | مرشد

**Product and engineering brief**

[Moath Hajaj](https://github.com/moathhajaj) ·
[Request a walkthrough](mailto:moath@murshid.me?subject=Murshid%20product%20walkthrough)

## Product purpose

Murshid is an Arabic-English mobile product connecting short-form learning
with mentorship, communities, events, and opportunity discovery. Its initial
audience is university students and people early in their careers in Qatar.

The product hypothesis is that connecting discovery to practical actions
will help people make progress: find guidance, join an event, or pursue an
opportunity. A controlled pilot is needed to test that hypothesis.

**Stage: MVP under active development and testing, before public launch.**
Catalog content includes demonstrations; it is not evidence of customers,
partnerships, or revenue.

## What a product review can cover

- **Discovery:** short-form content, saved resources, and opportunity details.
- **Guidance:** mentor profiles, availability, booking, and session preparation.
- **Participation:** communities, event registration, and access passes.
- **Operations:** a separate console for review, moderation, curation, and
  operator access management.

These are implemented areas of the MVP. Native media and payment integrations
still need separate provider and device validation; real-money payments
remain disabled pending end-to-end checks.

## Engineering decisions

| Decision | Practical purpose | Review boundary |
|---|---|---|
| React Native / Expo mobile app and a separate Next.js console | Keep the learner experience and operator workflows focused on their different tasks. | Browser previews do not validate native SDK behavior. |
| Feature modules own data access behind public interfaces | Keep routes thin and reduce dependencies between product areas. | Shared changes still need checks across their consumers. |
| Both applications consume generated database types | Keep their TypeScript contracts aligned with the schema after regeneration. | Types do not replace runtime validation or authorization. |
| Server-side operator role checks | Re-check access when an operation is requested, including after role removal. | Unit tests mock the backend; hosted authorization needs separate verification. |
| English-Arabic dictionary parity tests | Catch missing translation keys in either shared dictionary. | This does not assess translation quality, screen-local copy, or RTL layouts on devices. |

The backend uses Supabase Postgres, Auth, Storage, and Edge Functions.
Database policies and server-side checks form the authorization boundary.

## Selected local evidence

Recorded **11 September 2026** against the private implementation. These are
focused checks performed for this brief, not a complete release assessment
or an independent security audit.

| Check | Recorded result | Scope |
|---|---|---|
| Repository health | 17 checks passed | Workspace structure, feature inventory, dependency boundaries, and repository consistency. |
| Booking helpers and currency formatting | 30 tests passed | Price and time calculations, client-side overlap checks, and formatting cases. |
| Operator access helpers | 10 tests passed | Missing sessions, denied or removed roles, lookup failures, and repeated access checks with mocked backend responses. |
| Translation dictionary parity | 5 tests passed | Shared English-Arabic key alignment and dictionary consistency checks. |

The source and test suites are private. Passing these checks does not
establish service delivery, real-user outcomes, or production readiness.

## Next validation milestones

1. Validate the app and Arabic/English layouts on physical iOS and Android devices.
2. Complete provider-dependent media and payment checks before enabling them
   for public use.
3. Run a controlled pilot to evaluate the product hypothesis with real participants.

For a product walkthrough or a discussion of the implementation, contact
**[moath@murshid.me](mailto:moath@murshid.me)**.
