# Keep a server-side copy of Catalogue data

weebs stores its own copy of the Title and Episode details it shows (name, episode count, Episode titles where available, cover art, related Titles and streaming links) in the deployed application's database, taken when a Title is first added to an Entry and refreshed weekly or when a User asks for it (at most once every 6 hours), rather than fetching them from the Catalogue on every view. Group lists must load quickly and keep working when the Catalogue is down or rate-limiting us, and every member of a Group must see the same data; the cost is that details for airing Titles (e.g. episode count) can go stale until the next refresh.

## Considered Options

- **Fetch live on every view**: always fresh, but the app breaks whenever the Catalogue does, and many Group members viewing at once multiplies API calls.
- **Store only the Catalogue ID and cache on demand**: similar to the chosen option but makes the first view of every Title slow and the cache's freshness implicit.
