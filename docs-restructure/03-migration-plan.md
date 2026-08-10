# jaksam-docs, Phase 3: Migration Plan

Internal planning document, not part of the published site. Builds on `01-audit.md` and `02-information-architecture.md` (both approved 2026-08-10). Covers what happens to every existing page, expressed as bulk rules for the ~330 pages that follow a repeating pattern, plus an explicit table for the pages the audit flagged individually.

---

## Bulk rules (default action for the ~330 pattern-following pages)

Rather than listing all 352 pages one by one, these rules cover the repeating structures found in every product during the audit. Anything not covered by a bulk rule appears in the exceptions table below.

| Page pattern | Action | Tab (after) | URL change? | Redirect needed? |
|---|---|---|---|---|
| `<product>/home.md` | **Keep**, content-level rewrite in Phase 4 to normalize richness (audit: Confusing Content #3) | Main | No | No |
| `<product>/installation.md` | **Keep**, content-level rewrite in Phase 4 to add Requirements/Verification and unify Tabs+Steps structure (audit: Missing Content #2/#4, Confusing Content #4) | Main | No | No |
| `<product>/faq.md` (10 products that already have one) | **Keep** as-is | Main | No | No |
| `<product>/client/**`, `<product>/server/**` (all export/event reference pages, all "root" index pages) | **Move**, tab reassignment only, from the single existing tab into the new API tab. No file move, no content change. | Main → API | **No** (tabs don't affect file path/URL) | No |
| `<product>/modules.md` (Jobs, Drugs, Doors, Shops Creator) | **Move** to API tab (audit: Confusing Content #5, developer task, was in a beginner nav slot) | Main → API | No | No |
| `jobs-creator/replacing-default-scripts-names.md`, `replacing-default-events-names.md`, `qbcore-jobs-injection.md` | **Move** to API tab (developer/integration tasks) | Main → API | No | No |
| Other top-level "how-to"/guide pages that are genuinely server-owner tasks (`how-to-give-keys-with-car-command`, `fix-hotwiring-bought-car`, `lock-unlock-vehicle`, `how-to-use-custom-sprites`, `change-doors-icon`, `admin-bypass-lock`, `how-to-edit-minigames`, `how-to-use-images-for-items`, `how-to-enable-discord-features`, `commands-usage`, `external-deferrals`, `optimization`) | **Keep** in Main, regrouped under a "Guides" sub-group per product (cosmetic nav grouping only) | Main | No | No |
| General group pages (`how-to-update-the-scripts`, `common-faq`, `licensing`, `nexus-terms`) | **Keep** as-is | Main | No | No |

**Net effect:** the beginner/developer split from Phase 2 is achieved for the vast majority of the site purely by re-grouping `docs.json`, no bulk file moves, no bulk redirects. This is deliberately the lowest-risk way to execute the largest structural change in the plan.

---

## Exceptions table (pages the audit flagged individually)

| Page | Current location | Action | New location | Tab | Redirect |
|---|---|---|---|---|---|
| `untitled-page-2.mdx` | repo root, `/untitled-page-2` | **Move + Rename** (content is Jobs Creator's harvest-item-harvested event, misplaced since the GitBook migration) | `jobs-creator/server/harvest/item-harvested.mdx` | API | `/untitled-page-2` → `/jobs-creator/server/harvest/item-harvested` |
| `untitled-page-3.mdx` | repo root, `/untitled-page-3` | **Move + Rename** (content is Jobs Creator's shop-item-bought event) | `jobs-creator/server/shop/item-bought.mdx` | API | `/untitled-page-3` → `/jobs-creator/server/shop/item-bought` |
| `fivem-escrow-system-errors/failed-to-verify-protected-resource.md` | General group | **Move + rename** (revised during execution: the page is a full 245-line guide with its own Steps/nested Accordions/internal anchors, too large to fold into a single Troubleshooting accordion item without breaking its structure and internal links; kept as its own page, relocated next to the other General pages instead) + added one cross-link from Troubleshooting pointing to it | `jaksams-scripts/escrow-errors.md` | Main | `/fivem-escrow-system-errors/failed-to-verify-protected-resource` → `/jaksams-scripts/escrow-errors` |
| `index.mdx` | root | **Rewrite**, add a product-catalog `<CardGroup>` linking all 16 products' Main-tab Home pages (audit: Navigation Problems #1). Structural addition only, links to pages that already exist. | same | Main | No (same URL) |
| `jaksam-inventory/home.md` | Inventory | **Rewrite**, fix the three broken/inconsistent internal links (audit: Confusing Content #2): dedupe the Installation/Configuration cards, correct the framework anchor paths to include the `/jaksam-inventory` prefix, replace the dead `/backwards-compatibility` link with the correct in-page anchor. | same | Main | No |
| `jaksam-inventory/functions/client.md`, `functions/shared.md`, `functions/server.md`, `events/server.md`, `hooks.md` | Inventory, `Functions/`+`Events/`+standalone | **Move now** (tab only) into API. **Split later** in Phase 4 into one page per export/event/hook, matching the 1-page-per-export convention used by all other 15 products (audit: Technical Gaps #3), this is a content-restructuring task (splitting existing prose into the standard template), not new information. | `jaksam-inventory/functions/client/<export-name>.md` etc. (exact slugs decided when the split happens in Phase 4) | API | Yes, once split, old page → its group's new landing/index page |
| Products missing `faq.md` (revised count during execution, cross-checked directly against `docs.json`: Billing UI, Luxury Clothes Theft, Races Creator, Farming Creator, Missions Creator, Dealerships Creator, Shops Creator, Jaksam Inventory, 8 products, not the 6 estimated in the audit) |, | **Create** new placeholder page, frontmatter + a single `[TODO: INFORMATION NEEDED]` note, no fabricated Q&A (audit: Missing Content #5) | `<product>/faq.md` | Main | No (net-new page) |
| Developer Overview |, | **Create** new page: reference-page conventions (Side/Parameters/Return/Errors/Notes) + links to every product's API section (per Phase 2 decision #2) | `developers/overview.mdx` (exact slug TBD, kept shallow per URL rules) | API | No (net-new page) |
| Requirements + Verification content in each `installation.md` |, | **Rewrite in place** during Phase 4, product by product, Requirements pulled from each product's existing Start Order Example (not invented); Verification added **only** where the current doc already implies a way to check success. Where it doesn't, marked `[TODO: INFORMATION NEEDED]` instead of invented. | same file | Main | No |
| Configuration as a separate page |, | **Decided live, per product, during Phase 4**, not pre-committed here. Default is "stays a section inside Installation." A product only gets a standalone Configuration page if, once its actual Installation content is being rewritten, there turns out to be enough distinct config material to justify the split (Jaksam Inventory, with its Backwards Compatibility + Import sections, is the most likely candidate, to be confirmed when that page is rewritten, not assumed now). | varies | Main | Only if split happens |

---

## Archive (`hidden: true`) candidates

**None identified yet.** The audit did not surface any page that is confirmed unused, obsolete, or safe to remove outright, the near-identical installation boilerplate and reference-page templates found during the audit are intentional patterns, not redundant content (see `01-audit.md`, Duplicate Content). 

The `hidden: true` Archive mechanism from Phase 2 stays available for Phase 4: if rewriting a product turns up something that turns out to be genuinely dead (e.g. a page superseded by another that wasn't obvious from the nav tree alone), it goes into an Archive group at that point rather than being deleted immediately or silently kept live. This section will be filled in as (if) that happens.

**Purpose/lifecycle (confirmed 2026-08-10):** Archive is a **temporary staging step for stakeholder sign-off**, not a permanent home. Anything that lands here is content flagged as "no longer needed", kept out of nav/search/sitemap but still present on disk so it can be reviewed (by the user's boss) before anything is destroyed. Once reviewed and confirmed, the expected end state is **full deletion** of that content, not indefinite archival. Track anything sitting in Archive as an open item until it's actually deleted.

---

## Consolidated `docs.json` redirects to add

```json
"redirects": [
  { "source": "/untitled-page-2", "destination": "/jobs-creator/server/harvest/item-harvested" },
  { "source": "/untitled-page-3", "destination": "/jobs-creator/server/shop/item-bought" },
  { "source": "/fivem-escrow-system-errors/failed-to-verify-protected-resource", "destination": "/jaksams-scripts/escrow-errors" }
]
```

This list also still needs the **pre-existing GitBook→Mintlify redirects** identified as the top priority in `seo-ux-dx-strategy.md` (old `documentation.jaksam-scripts.com/...` paths), those are tracked there, not duplicated here; both lists end up in the same `docs.json` `redirects` array when implemented.

---

## Inventory split: completed 2026-08-10

The Jaksam Inventory reference split (53 functions across Client/Shared/Server + 3 events + 6 hook events) is done, in its own focused pass as agreed with the user. Actual scope discovered while reading the source in full: 22 client functions, 4 shared, 27 server, 3 server events, and a hooks system with its own `registerHook`/`unregisterHook`/`unregisterResourceHooks` API plus 6 hookable event types, larger than the earlier "Split later" note anticipated.

Structure used:
- `jaksam-inventory/functions/client/<export-name>.md` (22 pages) + `client/index.md` (function list)
- `jaksam-inventory/functions/shared/<export-name>.md` (4 pages) + `shared/index.md`
- `jaksam-inventory/functions/server/<export-name>.md` (27 pages) + `server/index.md`
- `jaksam-inventory/events/server/<event-name>.md` (3 pages) + `events/server/index.md`
- `jaksam-inventory/hooks/<hook-event-name>.md` (6 pages, payload + matching examples) + `hooks/index.md` (kept as the landing page for the registerHook/unregisterHook API, Options Parameter, and Hook Behavior, since those are cross-cutting across all 6 hook types, splitting them per-event would have duplicated or fragmented that shared context)

No redirects were needed for this split: Mintlify renders `<folder>/index.md` at the folder's own path, so `jaksam-inventory/functions/client/index.md` still resolves to `/jaksam-inventory/functions/client`, identical to the old flat file's URL. The new leaf pages (one per export/event/hook) are net-new URLs with no prior canonical location, so nothing to redirect there either.

One undocumented parameter was found and flagged rather than guessed: `getItemFromSlot` (server) accepts a third `returnRaw` argument in its signature that the source material never explains, marked `[TODO: INFORMATION NEEDED]` on that page. One hook (`onItemRemoved`) has a documented payload but no worked example in the source, also marked TODO rather than invented.

Full site validated after this split: 422 unique pages referenced in `docs.json`, all resolve to real files, zero orphaned files, zero duplicate nav entries.

## Sequencing for Phase 4

1. `docs.json` nav restructure: create the "API" tab, apply all bulk **Move** rules + the exceptions table's tab assignments. This alone (no file edits) already delivers the beginner/developer split.
2. File-level moves: `untitled-page-2/3` rename+relocate, escrow-error merge into Troubleshooting, add the three redirects.
3. Content rewrites: `index.mdx` product catalog, `jaksam-inventory/home.md` link fixes, per-product Installation Requirements/Verification pass, missing-FAQ placeholders, new Developer Overview page.
4. Jaksam Inventory reference split (largest single content-restructuring task, do last since it's the most involved and benefits from the conventions already having been written for the Developer Overview page in step 3).

Ready to move into Phase 4 on your go-ahead, or flag if any action above should change first.
