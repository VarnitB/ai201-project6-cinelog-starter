# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end — how you used AI tools during this project -->

## Comment 1 — Rename
**What I did:** Renamed `save_to_watchlist()` to `add_to_watchlist()` in `services/watchlist_service.py` to follow the collection service's `verb_to_noun` naming convention. I searched the repository for call sites and updated the import and function call in `routes/watchlist/watchlist.py`.
**How I verified:** Searched the full repository to confirm there were no remaining uses of `save_to_watchlist`, then ran `pytest tests/ -v` to verify the existing test suite still passed.

## Comment 2 — Deduplication
**What I did:** Added an `AlreadyInWatchlistError` and an existing-entry check to `add_to_watchlist()`. After confirming the film exists, the service now queries for the same `user_id` and `film_id` and raises the new error instead of inserting a duplicate. This follows the pattern used by `add_to_collection()` while preserving its existing `FilmNotFoundError` behavior.
**How I verified:** Compared the validation order and duplicate-query pattern with `add_to_collection()`, confirmed the duplicate check runs before creating or committing a new entry, and ran `pytest tests/ -v` to verify the existing suite still passed.

## Comment 3 — Missing test
**What I did:**
**How I verified:**

## Comment 4 — Default visibility
**My position:**
**Reasoning:**
**Tradeoff acknowledged:**

## Comment 5 — Sort order
**My position:**
**Reasoning:**
**Engagement with reviewer's point:**

## Comment 6 — Rebase
**What conflicted:**
**How I resolved it:**
**How I verified no conflict remains:**

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->
