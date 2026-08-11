# jaksam-docs — German (de) locale: continuation notes

Internal planning document, not part of the published site. Read this first in a fresh session before continuing the German translation.

**Status as of 2026-08-11:** Main tab (server-owner content) is fully translated, including all Guides sub-pages. The **API tab** now exists in German with 7 products fully translated: Jaksam Inventory (63 pages), Blips Creator (2), Luxury Clothes Theft (2), Races Creator (7), Farming Creator (8), Trackers Creator (8), Robberies Creator (12) — 102 API pages total. ~9 more products remain untranslated in the API tab (~210+ pages), the largest being Jobs Creator (66) and Drugs Creator (40).

---

## What's already done (don't redo)

- `docs.json` → `navigation.languages` has a `"de"` entry with one tab, `"tab": "Start"`.
- Under it: a `"Allgemein"` group (General) + one group per product (16), each with `root` pointing to `de/<product>/home`, `pages: [installation, faq]`, and (for the 12 products that have one in English) an `"Anleitungen"` sub-group mirroring the English `"Guides"` sub-group, same icons.
- `de/` folder mirrors English structure for: `index.mdx`, `jaksams-scripts/{how-to-update-the-scripts,troubleshooting,common-faq,nexus-terms,escrow-errors}`, every product's `home.md` + `installation.md` + `faq.md`, and all 26 Guides pages (8 Jaksam Inventory + 18 across the other 11 products that have them). 80 German files total.
- `jaksams-scripts/licensing.md` was deliberately skipped (long CC legal license text, `hidden: true`, not in active nav, low value to translate).
- Every German home page's Documentation CardGroup now has the full card set: Installation, Anleitungen (where applicable), FAQ, Entwickler-Referenz. The Entwickler-Referenz card intentionally still points to the **English** API page (e.g. `/jobs-creator/client`, `/jaksam-inventory/functions/client`) since that content isn't translated yet — don't "fix" these to a German URL until the API tab translation actually exists at that path.
- Full validation before every commit (see the PowerShell snippet at the bottom of this file) confirmed 0 missing files, 0 orphans, 0 duplicate nav entries across all languages combined.

## What's NOT done

### 1. ~~Guides sub-pages~~ — DONE as of 2026-08-11, see above.

### 1b. ~~Jaksam Inventory API section~~ — DONE as of 2026-08-11 (branch `de-locale-inventory-api`)

All 62 reference pages (22 client + 4 shared + 27 server functions, 3 server events, 6 hooks) plus the `jaksam-inventory/guides/commands.md` page (referenced from inside the API tab's Inventory group, not the Main tab) are translated under `de/jaksam-inventory/{functions,events,hooks}/...`. `docs.json`'s German `navigation.languages[].tabs[]` now has a second tab, `"tab": "API"`, containing one group so far: `"Inventory"`, mirroring the English API tab's structure exactly with `de/`-prefixed paths. All internal cross-links between these pages use the `/de/...` prefix (this was missed on the first pass for the hooks pages — double-check new pages for bare `/jaksam-inventory/...` links before committing, `grep -n '](/' -r de/<product> | grep -v '(/de/'` catches it, ignoring `/images/...` asset paths which are correctly unprefixed).

### 1c. ~~Blips Creator, Luxury Clothes Theft, Races Creator, Farming Creator~~ — DONE as of 2026-08-11 (branch `de-locale-small-products`)

Translated the 4 smallest remaining API products (19 pages total) in one pass, picked specifically because they were the cheapest way to make more products fully bilingual:

- **Blips Creator** (2 pages): 1 Client index + `open-menu-manually`
- **Luxury Clothes Theft** (2 pages): 1 Client index + `replace-default-notifications`
- **Races Creator** (7 pages): Client index, `replace-default-police-alert`, nested Notifications group (index + 2 pages), Server index, `police-alerted`
- **Farming Creator** (8 pages): Client index + 4 pages, Server index + 2 pages

Each product's German `docs.json` API-tab group was added as a sibling to `"Inventory"` under the `"de"` language's `"API"` tab, mirroring the English group/icon structure exactly with `de/`-prefixed paths. Each product's German `home.md` "Entwickler-Referenz" card was updated from the English fallback URL to the new German one (e.g. `/de/blips-creator/client`) — this is the pattern to repeat for every future product once its API section is translated (grep `Entwickler-Referenz` in the product's `de/<product>/home.md`).

### 1d. ~~Trackers Creator~~ — DONE as of 2026-08-11 (branch `de-locale-trackers`)

8 pages: Client index + 3 pages (notifications, panic button pressed, manually start panic button), Server index + 3 pages (panic button pressed, player lost signal, player set new private frequency). Also fixed a pre-existing bug found in passing: `de/trackers-creator/faq.md` linked to the **English** `optimization` guide page (`/trackers-creator/optimization`) even though the German translation already existed at that path — this was a leftover from the earlier Main-tab Guides pass, not something this session introduced. Worth spot-checking other already-translated products' FAQ/home pages for the same kind of stale English link now that more API sections exist.

### 1e. ~~Robberies Creator~~ — DONE as of 2026-08-11 (branch `de-locale-robberies`)

12 pages: `modules.md` (a top-level advanced-integration page, not under Client/Server — same pattern as `jobs-creator/modules.md`), Client index + `progress-bar` + `replace-default-police-alert` + nested Notifications group (index + 2 pages), Server index + 4 pages (heist-started, heist-finished, police-alerted, step-completed). This product leans heavily on its "Modules" system instead of raw event/export docs for progress bar, dispatch, and TextUI — several pages are short and just point to `/de/robberies-creator/modules` instead of documenting an export directly; that's faithful to the English source, not a shortcut taken here.

### 2. API tab (developer reference) — ~210+ pages remaining across ~9 products

Not started in German for: Jobs Creator (66), Drugs Creator (40), Vehicles Keys (36), Doors Creator (20), Shops Creator (18), Missions Creator (15), Billing UI (13), Dealerships Creator (13), Easy Allowlist (12). This is everything else currently under the English `"API"` tab in `docs.json`:

- Per-product `Client`/`Server` export & event pages
- `developers/overview.mdx` (the conventions page) — the German API tab currently has no `"General"` group/overview page at all; add one (mirroring English) when translating it, or when it becomes the first page a user hits
- The `Modules`/advanced-integration pages (`jobs-creator/modules.md` etc.)

**Recommendation:** keep working smallest-to-largest (see page counts above) to maximize the number of fully-bilingual products per session; Easy Allowlist (12) is the natural next pick. Jobs Creator (66) is the largest and should be its own dedicated multi-session effort near the end, same way the original restructure was phased (audit → plan → execute).

**Mechanical approach that already worked well for Main tab:**
1. Read the English source file(s) (don't re-derive content, translate what's there — see [[feedback_jaksam_docs_no_new_info]], no new facts, ever).
2. Keep code blocks, export/event signatures, parameter names, file paths, and command names **untranslated** (they're literal identifiers, not language).
3. Translate: titles, descriptions, prose, table cell descriptions, Note/Warning/Info box text.
4. Give every new page its own specific icon (reuse the same icon as the English equivalent page — don't invent a new one, don't default to a generic set, see the icon-convention lesson in [[project_jaksam_docs_migration]]).
5. Build the German `docs.json` nav block by mirroring the English API tab's structure exactly, with `de/` prefixed paths.
6. **Validate before every commit** — this repo has 400+ pages, mistakes are easy to miss by eye. Use a PowerShell pass (see the ones used throughout this session, in the conversation history / git log) that walks `docs.json`, collects every referenced page path, and checks: (a) every referenced path has a matching file, (b) every file under `de/` is referenced somewhere, (c) no duplicate nav entries. Don't skip this — it caught 2 real bugs during the Main-tab pass.
7. Commit on a new branch (e.g. `de-locale-api-tab`), stage files **by name**, never `git add -A` (see the `seo-ux-dx-strategy.md` incident in [[project_jaksam_docs_migration]] — there's a stray untracked planning file at repo root that must never get swept into a commit).
8. Push, give the user the compare link (no `gh` CLI on this machine): `https://github.com/jaksam1074/jaksam-docs/compare/master...ofcshiro:jaksam-docs:<branch-name>`.

### 3. Tags/icons on new German pages

Reuse the same `tag`/`icon` frontmatter values as the English source page where the English page has them (e.g. `jaksam-inventory/how-to-update.md` has `tag: "Update"` — its German translation should too, once translated). Don't invent new tags; see [[project_jaksam_docs_migration]] for the "tag" mechanism (page frontmatter only, never `docs.json`, and only used topically/for genuinely new-or-replaced pages).

---

## Quick sanity check to run first in a new session

```powershell
$j = Get-Content -Raw docs.json | ConvertFrom-Json
# confirm which German API-tab groups exist already — if more products were
# added in a prior session, they'll show up here (should show "Inventory" only,
# as of 2026-08-11)
($j.navigation.languages | Where-Object { $_.language -eq "de" }).tabs |
  Where-Object { $_.tab -eq "API" } |
  Select-Object -ExpandProperty groups | Select-Object -ExpandProperty group
```

If this still only shows `Inventory`, nothing has changed since this note was written and the plan above is accurate.
