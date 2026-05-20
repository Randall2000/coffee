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
- Journal is a single main flow:
  1. trend summary (hidden when bean filter active)
  2. search + sort
  3. recent bean rail (hidden when bean filter active)
  4. filtered recent log list

## Journal Bean Filtering — Sub-page Navigation Pattern
- Tapping a bean chip on the rail triggers **sub-page navigation**, NOT in-place filtering.
- When `selectedJournalBeans.length > 0`:
  - Page title changes from "沖煮日誌" (with BookOpen icon) to a `← [bean name]` back button
  - If multiple beans selected: title shows `← X 種豆子`
  - Subtitle changes from static hint text to `找到 N 筆紀錄`
  - Bean rail is hidden (user is already inside the filtered view)
  - Trend stats section is hidden
  - Search bar and sort dropdown remain visible
  - Clicking the title/back button calls `setSelectedJournalBeans([])` to return to full view
- This pattern was chosen to prevent the "lost in filter" UX problem.
  - Do NOT revert to in-place filter with a small "清除" button — that caused the original confusion.
  - Do NOT add a separate filter chips row below the search bar — the header back button is the exit.

## Journal Bean Filtering — State
- `selectedJournalBeans`: multi-select bean filters
- `journalBeanSheetOpen`: journal-only bean filter sheet
- `journalBeanSearch`: search input inside journal bean sheet
- Filtering behavior: multi-select, OR logic, logs shown if they match any selected bean
- `更多豆子` opens a dedicated journal bean filter bottom sheet (separate from the brew-config bean sheet)

## Important UX Decisions
- Do not reuse brew configuration bean selection UX for journal filtering.
- Recent bean rail is only a shortcut for quick single-bean drill-down.
- Full multi-bean filtering should happen in the journal-specific sheet (`journalBeanSheetOpen`).
- The "sub-page navigation" pattern is intentional — users understand ← as "go back", not "clear filter".

## Pre-Brew Confirmation Page — Quick Adjust Panel
- Triggered by: `showAdjust` state, toggled via 快速調整 button below the Start Brew button
- Current adjustable items:
  - **粉量** (coffee grams): stepper, range 10–40g
  - **水溫** (water temp): stepper, range 70–100°C
- Removed items:
  - **烘焙度** was removed. Roast level is only set via the bean selection sheet, not inline adjustment.

## Bottom Sheets on Pre-Brew Page
- **豆子 sheet** (`beanSheetOpen`): select or add/edit beans. When no beans exist and user opens new-bean form, a 取消 button closes the sheet. When beans exist, 返回選擇 navigates back to the list.
- **濾杯 sheet** (`dripperSheetOpen`): has × close button in header.
- **磨豆機 sheet** (`grinderSheetOpen`): has × close button in header.
- **手沖法 sheet** (`recipeSheetOpen`): has × close button in header.

## Bilingual Support (EN / 中)

The app supports full English/Chinese switching via a toggle in the header.

### Architecture
- `lang` state: `'zh'` (default) or `'en'`, persisted in `localStorage` (`barista_flow_lang`)
- `t(key, ...args)` helper inside `BaristaFlow` — looks up `TRANSLATIONS[key][lang]`
- `TRANSLATIONS` constant at the top of `<script>`: 191+ keys covering all visible UI strings
- `document.documentElement.lang` updates to `'zh-Hant'` or `'en'` on every toggle
- `RadarChart` component: receives `lang` prop and uses a local `tl()` helper for axis labels
- `getRelativeDate(ts, lang)` — second param controls locale for relative date display
- `formatRoastDate(dateString, lang)` — uses `'zh-TW'` or `'en-US'` locale

### Static Data i18n
Static data constants that are displayed in the UI have bilingual fields:
- **`RECIPES`**: each recipe has `nameEn` and `descriptionEn`; each step has `nameEn` and `descEn`
- **`ROAST_LEVELS`**: labels translated via `t('roast.' + id)` at render sites (keys: `roast.light`, `roast.medium`, `roast.dark`)
- **`FLOW_OPTIONS`**: translated via `t('flow.' + id)` at render sites (keys: `flow.fast`, `flow.good`, `flow.clog`)
- **`SENSORY_ATTRIBUTES`**: translated via `tl('sensory.' + key)` inside `RadarChart`

### Important Rules
- Storage sentinel value `'未命名咖啡豆'` is stored as-is; **only display uses `t('bean.unnamed')`**
- `beanName !== '未命名咖啡豆'` comparisons must keep the fixed Chinese string (not `t()`)
- Log entries store Chinese recipe/step names (as typed at save time) — display fallback is fine

## Recent Changes
- Removed delete button from journal cards.
- Refocused journal around trends and filtered recents.
- Simplified filter area and changed bean shortcuts to a horizontal rail.
- Added multi-select journal bean filtering.
- Added dedicated journal bean filter sheet for `更多豆子`.
- Added × close button to dripper / grinder / recipe sheets.
- Added cancel/back exit to bean sheet when no beans exist.
- Removed 烘焙度 from quick adjust panel (pre-brew confirmation page).
- **Journal bean filter changed to sub-page navigation**: clicking a bean now changes the header to `← [bean name]` with a back button, instead of in-place silent filter.
- **Added EN/中 language toggle**: full bilingual support across all views; system font stays (intentional).

## Notes For Future Agents
- If you update journal filtering UX, also update this file.
- If you update the quick adjust panel items, also update this file.
- Keep interactions aligned with mobile thumb-friendly usage.
- The journal page header is dynamic: it shows "沖煮日誌" normally, and `← [bean]` when filtered. Do not change this without understanding the sub-page navigation design decision above.
- If you add new UI strings, add keys to `TRANSLATIONS` with both `zh` and `en` values.
- If you add new recipe steps or RECIPES entries, add `nameEn` and `descEn` to every step.
