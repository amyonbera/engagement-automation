# Amy Engagement Automation

Amy operates automated systems that structure community participation data into leaderboard outputs, progress signals and reporting flows.

This repository documents the public-safe architecture of those systems.

These systems support the leaderboards, participation tracking and community engagement outputs that users see on Amy's platform.

The goal is to surface useful community participation, make contribution visible and support fairer reward and progress systems.

## What this system does

Amy's engagement automation pipeline processes community participation signals through several stages:

1. **Curated activity sources** — structured inputs from selected public channels and community-submitted links.
2. **Activity qualification** — capture and structuring of public engagement signals such as posts, comments and interactions.
3. **Quality controls** — deduplication, spam filtering, handle repair and rolling time windows to support fairer outputs.
4. **Structured scoring** — caps, weighting and quality adjustments so outputs reflect structured participation rather than raw volume.
5. **Leaderboard construction** — deterministic ranking with public and internal review layers.
6. **Automated publishing** — outputs delivered to structured destinations for display, review and downstream use.
7. **Daily run reporting** — each run produces a summary of what was collected, processed, published, skipped or failed.

## How this connects to the Amy platform

- [**platform-overview**](https://github.com/amyonbera/platform-overview) explains why Amy tracks community participation.
- [**rewards-framework**](https://github.com/amyonbera/rewards-framework) explains what points, badges and progress mean for users.
- [**data-flows**](https://github.com/amyonbera/data-flows) covers how leaderboard data is historically archived and reported.
- [**platform-technology**](https://github.com/amyonbera/platform-technology) covers the integration and data-boundary principles behind systems like this one.

## Design choices

### Separate collection from judgement

Raw activity capture is separated from structured scoring. The system does not publish raw engagement counts directly; it passes data through quality controls before outputs are built.

### Rolling windows, not lifetime accumulation

Leaderboard outputs are based on defined time windows rather than unbounded historical totals. This keeps outputs current and reduces the advantage of older activity.

### Public outputs, internal review

Each run produces public-facing outputs and fuller internal review layers. Public outputs are designed to be clean and understandable. Internal outputs support deeper analysis and quality checking.

### Run-level observability

Daily runs produce structured summaries covering collection volumes, processing outcomes, publishing results and detected issues. The system is designed to be reviewable, not invisible.

## What is not public

This repository documents system architecture and design patterns. It does not contain:

- private application code or credentials
- exact scoring formulae, cap tables or multiplier bands
- scraper mechanics or timing parameters
- internal file paths, sheet IDs or service account details
- wallet-level data or user-identifiable records
- anti-spam rules in sufficient detail to allow gaming

## Repository purpose

This repository documents Amy's public-safe engagement automation architecture for participation tracking, leaderboard flows, quality controls, publishing and run reporting. It does not contain private application code, credentials, internal infrastructure details or sensitive user data.
