# AI Agent Sync

## Project
- Repo: `Randall2000/coffee`
- Local path: `/tmp/coffee-fix`
- Main UI file: `index.html`
- App type: single-file React app embedded in `index.html`

## Current Product Direction
- Primary brew flow stays mobile-first and fast.
- Journal page prioritizes:
  1. rating trend review
  2. comparing beans through filtering

## Journal UX State
- Journal no longer uses `timeline / byBean` dual-mode navigation.
- Journal is now a single main flow:
  1. trend summary
  2. search + sort
  3. recent bean rail
  4. filtered recent log list

## Journal Bean Filtering
- State:
  - `selectedJournalBeans`: multi-select bean filters
  - `journalBeanSheetOpen`: journal-only bean filter sheet
  - `journalBeanSearch`: search input inside journal bean sheet
- Filtering behavior:
  - multi-select
  - OR logic
  - logs are shown if they match any selected bean
- UX behavior:
  - clear filter action lives inside the journal tool card, not header
  - recent beans appear as a horizontal rail
  - `更多豆子` opens a dedicated journal bean filter bottom sheet
  - this sheet is separate from the brew-config bean sheet

## Important UX Decisions
- Do not reuse brew configuration bean selection UX for journal filtering.
- For many beans:
  - recent bean rail is only a shortcut
  - full bean filtering should happen in the journal-specific sheet
- Avoid page states where users get trapped in a filtered sub-view with no visible exit.

## Recent Changes
- Removed delete button from journal cards.
- Refocused journal around trends and filtered recents.
- Simplified filter area and changed bean shortcuts to a horizontal rail.
- Added multi-select journal bean filtering.
- Added dedicated journal bean filter sheet for `更多豆子`.

## Notes For Future Agents
- If you update journal filtering UX, also update this file.
- Keep interactions aligned with mobile thumb-friendly usage.
- Prefer local, contextual actions over header-level actions for list filters.
