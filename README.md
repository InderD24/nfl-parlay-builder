# NFL Parlay Builder

A team datathon project for casual NFL bettors: choose target combined odds, a maximum of 2–4 legs, and an optional locked pick; compare cross-game parlays ranked by estimated hit probability.

## Problem we are solving

Casual NFL bettors can see a parlay's potential payout but have difficulty comparing combinations with similar odds and understanding how each added leg changes the chance of winning. We aim to make that probability–payout tradeoff explicit and generate explainable combinations near the user's chosen target odds.

## Datasets and APIs

Our planned historical source is [nflverse](https://github.com/nflverse/nflverse-data), including [NFL schedules and results](https://raw.githubusercontent.com/nflverse/nfldata/master/data/games.csv), team statistics, and optional player statistics. We will use completed games to build pre-game features and evaluate models chronologically.

Our planned upcoming-odds source is [The Odds API](https://the-odds-api.com/), using its free tier for NFL moneylines from one sportsbook. We will store timestamped snapshots internally and use a shared cache to respect the quota. [SportsGameOdds](https://sportsgameodds.com/pricing) is an alternative under evaluation for optional player props.

These sources have been researched; authenticated API coverage and dataset quality have not yet been verified. No data has been ingested yet. Raw odds feeds and credentials will not be published in this repository. See [the data plan](docs/DATA.md) for limitations and source links.

## Current progress

Completed: product framing, data-source research, MVP requirements, and team repository structure. Planned next: validate free API coverage, ingest NFL historical results, implement a market-probability baseline, and generate constrained 2–4-leg combinations.

## Modeling and evaluation

We will compare a margin-adjusted market baseline with a simple historical model and a validated blend. Suggestions maximize estimated hit probability near the target payout. We will report held-out calibration and probability accuracy; profitable betting performance is a hypothesis, not an established result. Cross-game probability multiplication is an independence approximation, and NFL tie/void settlement requires an explicit policy.

## Scope

- Required: pre-match moneylines, one sportsbook, one leg per game, target-odds tolerance, up to three suggestions.
- Optional: player props after data coverage and model validation.
- Suggestions only; no automatic bet placement.
- Combined payouts are estimates until confirmed by the sportsbook.

## Team starting points

See [product requirements](docs/PRD.md), [data plan](docs/DATA.md), and [contributing](CONTRIBUTING.md).

## Project layout

- `src/`: future ingestion, modeling, optimization, and application code.
- `tests/`: future validation of constraints and calculations.
- `notebooks/`: exploratory research; keep credentials and raw provider data out of Git.
- `docs/`: requirements and data decisions.

This repository is a planning scaffold. No model or application has been implemented yet.
