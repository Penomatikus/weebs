# weebs

A tracker for groups of friends who watch anime together: what they've committed to watch, which Episodes each person has seen, and how they rate it.

## Language

### People

**User**:
A person with an account in weebs. People can only sign up through an Invite Link. A User who deletes their account becomes a former Member of every Group; their Scores stay, shown as a Deleted User, and everything else of theirs is removed.
_Avoid_: Account, viewer

**Group**:
A set of Users who commit to watching Titles together. A User can belong to any number of Groups. A Group has no owner or admin: any Member can create Invite Links to it, nobody can be removed, and Members only leave of their own accord. When the last Member leaves, the Group is deleted.
_Avoid_: Party, club, team, circle, Owner, admin

**Member**:
A User who belongs to a given Group. A User who has left it is a former Member; if they rejoin, they pick up their earlier Watched Episodes, Finished Seasons and Scores.
_Avoid_: Participant, viewer

**Invite Link**:
A single-use link, valid for one week, that any User can create. It lets one person either sign up, or join a given Group (signing up first if needed); accepting one is the only way to join a Group.
_Avoid_: Invitation, invite code, referral

### Catalogue

**Title**:
A whole anime, made up of one or more Seasons, or a Movie. weebs assembles a Title from the Catalogue's separate per-season listings. Its Related Titles are listed under it but are never part of it.
_Avoid_: Anime, show, series, media, work, franchise

**Season**:
One run of a Title's Episodes that the Catalogue lists as a single series entry; each separately listed part of a split season is its own Season. Long-running shows the Catalogue lists only once are a single Season.
_Avoid_: Cour, part, arc

**Related Title**:
A Movie, special or OVA that the Catalogue connects to a Title, such as a film set between two Seasons. It is a Title in its own right with its own Entries. A one-episode special counts as a Movie; a multi-episode OVA is a Title with a single Season.
_Avoid_: Spin-off, extra, side story

**Movie**:
A Title that has no Seasons or Episodes; it is watched in one go.
_Avoid_: Film

**Episode**:
One instalment of a Season, numbered from 1 within that Season. It is known by its title when the Catalogue has one, otherwise by its number (E1, E2, ...).
_Avoid_: Chapter, part

**Catalogue**:
The external sources of truth for Seasons, Movies and their details (name, episode count, Episode titles where available, cover art, Related Titles, streaming links): a primary source, with gaps filled from a secondary one. weebs keeps its own copy of a Title only once it is in an Entry, and never edits the sources.
_Avoid_: Database, source, provider

**Refresh**:
weebs checking the Catalogue for new Episodes and Seasons of a Title and updating its copy. It happens weekly, and any User can ask for one, at most once every 6 hours. Everyone with an Entry for the Title that isn't Dropped is notified of anything new. A Refresh never removes an Episode someone has Watched or scored.
_Avoid_: Sync, update, check

### Tracking

**Entry**:
A commitment to watch some or all Seasons of one Title: either a Group Entry or a Personal Entry. Seasons added later join the same Entry; a Season can be taken out again while nobody has ticked or scored anything in it. A Group or User has at most one Entry per Title.
_Avoid_: List item, watchlist item, tracking

**Group Entry**:
An Entry belonging to a Group. Its Status, Checkpoints and Watch Date are shared by all the Group's Members. It can only be deleted while in Planning; after that it can only be Dropped.
_Avoid_: Shared entry, group list item

**Personal Entry**:
An Entry belonging to a single User. It is visible to everyone who shares a Group with them, unless they mark it Private. A User gets one automatically the first time they tick an Episode in a Group Entry for a Title they have no Personal Entry for.
_Avoid_: Solo entry, own entry, private entry

**Status**:
Where an Entry stands: one of Planning, Watching, Completed, Paused or Dropped. It only ever changes by hand. A Group Entry has one Status for the whole Group; Dropped means the Group has agreed to stop watching. A Dropped Entry stays and can be picked up again at any time.
_Avoid_: State, On Hold

**Watched**:
A User has Watched an Episode (or Movie) of an Entry once they've ticked it off. It is recorded per Entry, so watching Episode 3 in one Group doesn't mark it Watched in another; it does also mark it Watched in that User's Personal Entry for the Title, adding the Season to it if needed.
_Avoid_: Seen, done, progress

**Finished**:
A User has Finished a Season of an Entry once they have Watched all its Episodes and confirmed they are done with it. Only then can they give Season Scores. Finishing in a Group Entry also Finishes the Season in that User's Personal Entry, and unticking an Episode afterwards doesn't undo it.
_Avoid_: Complete, done

**Score**:
A whole number from 1 to 10 that a User gives to one Category of a Season or Episode within an Entry. Scores are optional and belong to that Entry only. In a Group Entry, a Score can no longer be changed once other Members can see it.
_Avoid_: Rating, vote, review

**Average Score**:
The mean of the Scores that a Group's Members gave to one Category of a Season or Episode within an Entry. Members who gave no Score are left out; Scores from former Members still count.
_Avoid_: Group score, overall score

**Title Average**:
The figure a Title gets in one Season Category: for a User, the mean of their Season Scores; for a Group, the mean of each Season's Average Score, skipping Seasons with no Scores. It is never a Score itself and only uses Scores that are revealed.
_Avoid_: Title score, overall rating

**Checkpoint**:
A Group's agreement to have Watched an Entry up to a given Episode of a given Season by a given date and time, when they meet to discuss it. It can only name an Episode the Catalogue already lists. An Entry has at most one upcoming Checkpoint, which any Member can set, move or delete. Only Group Entries for Titles that aren't Movies have Checkpoints.
_Avoid_: Deadline, meetup, milestone

**Watch Date**:
The date a Group plans to watch a Movie together; any Member can set, move or clear it. It is for information only and reveals nothing.
_Avoid_: Checkpoint, screening

**Hidden Scores**:
A per-Entry setting, on by default for Group Entries, that keeps Members' Scores hidden from each other until they are revealed. It can only be changed while the Entry is in Planning. A passed Checkpoint reveals every Member's Episode Scores up to and including its Episode, plus the Season Scores of any Season whose last Episode it covers; a Score given for an already-revealed Episode is visible straight away. Revealed Scores can no longer be changed. Movies never have Hidden Scores, because a Group watches them together.
_Avoid_: Blind scoring, secret scores

**Peek**:
A single Member choosing, after a spoiler warning, to see the other Members' hidden Scores in a Group Entry; they can hide them again. A Peek reveals nothing to anyone else and locks no Scores.
_Avoid_: Reveal, unhide

**Season Category**:
One of the fixed aspects a Season is scored on: Overall, Soundtrack, Art Style. A Title is never scored directly; its figures are derived from its Seasons' Scores.
_Avoid_: Criterion, dimension

**Episode Category**:
One of the fixed aspects an Episode is scored on: Humor, Thrilling, Emotional, Fighting. A Movie is scored on both the Season and the Episode Categories.
_Avoid_: Criterion, dimension, tag
