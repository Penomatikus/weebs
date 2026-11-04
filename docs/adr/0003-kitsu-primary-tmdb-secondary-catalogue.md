# Kitsu as the primary Catalogue, TMDB to fill gaps

weebs searches and builds Titles from Kitsu, and fills gaps in Kitsu's data (mainly Episode titles) from TMDB. Kitsu lists one entry per Season with typed sequel and summary relations and direct streaming links, which matches weebs' Title → Season → Episode model as-is; TMDB has complete Episode data and clear API terms, but its seasons are hand-made (merged cours, arc splits) and don't line up with ours.

weebs is a non-commercial hobby project for a small group of friends (no ads, no tracking, no revenue), which is what makes both sources usable at all. Kitsu publishes no API terms ("available upon request") and gives no stability guarantee for its API; we accept that risk without asking for written terms. TMDB requires attribution (logo and "uses TMDB and the TMDB APIs but is not endorsed…" notice) and forbids caching for more than 6 months, which the weekly refresh satisfies.

## Considered Options

- **AniList**: same per-season shape as Kitsu, but its terms forbid using the API for data storage and in anime list or tracker services.
- **TMDB alone**: clearest terms and best Episode data, but adopting it would mean redefining a Season as whatever TMDB calls one (e.g. Frieren S1 and S2 merged).

## Consequences

- Filling gaps means mapping Kitsu's per-Season Episodes onto TMDB's differently split seasons (Frieren S2 E1 is TMDB S1 E29).
- The rules for building Titles from Kitsu's entries are in [docs/spec.md](../spec.md#building-titles-from-the-catalogue); they are expected to change as more edge cases turn up.
