# Product requirements

Status: draft based on the team's October 6, 2026 PRD discussion.

## User and value

Casual NFL bettors choose a target payout and compare explainable combinations. Target odds are a payout preference; estimated hit probability is shown separately.

## Required behavior

1. List upcoming NFL games with available, timestamped moneylines.
2. Accept target American odds, maximum 2–4 legs, and an optional locked pick.
3. Generate cross-game combinations from one configured sportsbook, with at most one leg per game.
4. Filter to an initial ±10% tolerance in decimal odds.
5. Rank by estimated joint hit probability, then target proximity, then fewer legs.
6. Return up to three unique suggestions, or explain why none satisfy the constraints.
7. Show leg prices, estimated combined payout, probability method, timestamps, and assumptions.
8. Exclude started games and stale/unavailable prices.

## Probability approach

Normalize opposing implied probabilities to obtain a market baseline. Evaluate a simple historical model and a blend using chronological validation. Use the market baseline if the blend does not improve held-out probability quality. Cross-game multiplication is an independence approximation. NFL ties, voids, and settlement conventions require an explicit policy before probability or return claims are published.

## Optional scope

Player props require verified free coverage, paired over/under prices at the same line, reliable player matching, and separate validation. Same-game parlays and bet placement are excluded.

## Acceptance criteria

- Every suggestion obeys leg count, distinct-game, sportsbook, and locked-pick constraints.
- Results inside the tolerance are ranked correctly.
- Missing results and data failures have clear explanations.
- Probability provenance and odds freshness are visible.
- Quota exhaustion does not silently serve stale recommendations.
- Saved snapshots reproduce results.

## Open decisions

- Exact sportsbook and audience geography.
- Confirmation of suggestions-only output; sportsbook links remain optional.
- Settlement policy and freshness thresholds.
- Frontend stack and workstream ownership.

## Workstreams

Data ingestion and snapshots; model and calibration; constrained optimizer; UI and user evaluation.
