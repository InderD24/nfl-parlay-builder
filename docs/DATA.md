# Free data plan

Provider documentation was researched October 6, 2026. Authenticated coverage has not been tested; recheck terms, limits, and available markets before integration.

## Primary sources

- [The Odds API](https://the-odds-api.com/): free plan documented at 500 credits/month; use upcoming NFL moneylines from one sportsbook. Historical odds are paid.
- [API documentation](https://the-odds-api.com/liveapi/guides/v4/): quota depends on markets and regions; do not equate every call with one credit.
- [Terms](https://the-odds-api.com/terms-and-conditions.html): analytical use and internal storage are permitted; do not publish a raw odds feed/archive.
- [nflverse](https://github.com/nflverse/nflverse-data): historical schedules, results, team/player stats; preserve dataset-specific attribution/license requirements.
- [nflreadpy](https://nflreadpy.nflverse.com/): Python access.
- [Games CSV](https://raw.githubusercontent.com/nflverse/nfldata/master/data/games.csv): includes historical moneyline columns, with missing values and provenance/timing limitations.

## Alternatives

- [SportsGameOdds](https://sportsgameodds.com/pricing): documented free tier of 2,500 objects/month and 10-minute updates; investigate optional NFL props and exact usage terms.
- [API-NFL](https://www.api-football.com/news/post/how-to-get-started-with-api-nfl-the-complete-beginners-guide): documented 100 free requests/day; pre-match odds coverage and refreshes must be checked.
- [BALLDONTLIE NFL](https://nfl.balldontlie.io/): odds and props were paid-tier endpoints; do not depend on a temporary trial.

## Engineering requirements

Keep keys server-side. Use a shared cache, quota monitoring, and a bounded refresh schedule. Store provider and retrieval timestamps, event mappings, feature cutoffs, and model versions. Never commit keys or raw odds archives. Save prospective snapshots: historical summary odds do not establish what was available days before kickoff.
