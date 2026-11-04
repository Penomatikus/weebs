# weebs product spec

How weebs behaves, in the language of [GLOSSARY.md](../GLOSSARY.md). The reasons behind the bigger decisions live in [docs/adr/](adr/). This is a living document: change it when behaviour changes.

weebs is a non-commercial hobby project for a small group of friends: no ads, no tracking, no revenue.

## Accounts and sign-in

- Users sign in with email and password.
- Signing up is only possible through an Invite Link.

## Search and adding Titles

- Search queries the primary Catalogue (Kitsu) live. Nothing is copied into weebs until a Title is added to an Entry.
- Results show one entry per Title: Kitsu returns one hit per Season, and weebs groups them into their Title.
- Selecting a result opens the Title's page, which lists its Seasons and its Related Titles (Movies, specials, OVAs).
- From that page a Group or User adds to their Entry by choosing:
  - **All**: every Season plus every Related Title (each Related Title gets its own Entry);
  - **All seasons**: every Season, no Related Titles;
  - individual Seasons;
  - individual Related Titles. There is no "all movies" option.
- Choosing Seasons of a Title that already has an Entry adds them to that Entry rather than creating a new one (e.g. adding *Dandadan* Season 2 first and Season 1 later gives one *Dandadan* Entry).
- "All" and "All seasons" are one-off selections, not subscriptions: Seasons that appear later are not added automatically.

## Building Titles from the Catalogue

When a Title is first added to an Entry, weebs loads it from Kitsu, fills gaps (mainly Episode titles) from TMDB, and saves its own copy. Kitsu lists one entry per season and links them with typed relations; weebs assembles a Title from them as follows:

- Follow the sequel/prequel relations from the selected entry to find the Title's main chain.
- A **Season** is an episodic entry on that chain: format TV, TV_SHORT or ONA. Separately listed parts of a split season (e.g. *Attack on Titan* Final Season Part 1 and Part 2) are separate Seasons.
- Recaps and recuts (summary and alternative relations) are ignored. Where the chain forks between a Movie and a recut of it (e.g. *Mugen Train*), follow the Movie and drop the recut.
- Movies, specials and OVAs connected to the chain become **Related Titles**: a one-episode special is treated as a Movie, a multi-episode OVA as a Title with a single Season.
- Episodes are numbered from 1 within their Season. When neither source has an Episode's title, it is shown by number (E1, E2, ...).
- Filling gaps from TMDB means mapping Kitsu's Seasons onto TMDB's differently split seasons (e.g. *Frieren* Season 2 Episode 1 is TMDB S1 E29).

## Refresh

- An automatic Refresh runs weekly for every Title in an Entry, regardless of when it was last refreshed.
- Any User with an Entry for the Title can ask for a Refresh. If the last Refresh (manual or automatic) was less than 6 hours ago, weebs doesn't call the Catalogue and tells the User nothing new is out yet.
- Every Refresh records when it ran.
- A Refresh only adds Episodes and Seasons and updates details. It never removes an Episode someone has Watched or scored; changes it can't reconcile are left as they were and flagged.

## Notifications

- When a Refresh finds new Episodes or Seasons, everyone with an Entry for that Title that isn't Dropped is notified.
- Inside a Group, news about its Group Entries' Titles (e.g. new *One Piece* Episodes) is shown in an info box.
- Channels:
  - in-app: always on;
  - email: opt-in per User;
  - push: opt-in per User, only when weebs is installed as a web app on iPhone or Android.

## Watching and scoring

- Once a User has ticked the last Episode of a Season, a **Finish** button appears; Finishing unlocks their Season Scores.
- Peeking at hidden Scores shows a spoiler warning first, saying it may spoil the experience; the User can hide the Scores again afterwards.

## Attribution

- The app shows the TMDB logo and the notice "This application uses TMDB and the TMDB APIs but is not endorsed, certified, or otherwise approved by TMDB", as TMDB's terms require (see [ADR-0003](adr/0003-kitsu-primary-tmdb-secondary-catalogue.md)).
- If TMDB watch-provider data is ever shown, it is credited to JustWatch.
