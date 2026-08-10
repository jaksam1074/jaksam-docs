# jaksam-docs, Phase 2: Proposed Information Architecture

Internal planning document, not part of the published site. Builds directly on `01-audit.md`. Not yet approved, this is the proposal to review before Phase 3 (migration plan) starts.

---

## Core decision: two top-level tabs, not more

The current site already uses Mintlify's `tabs` navigation concept (`docs.json` → `navigation.languages[0].tabs`), currently with a single tab, "Main". Per direct instruction, we keep the tab count minimal:

- **Main**, existing tab, becomes the server-owner/beginner surface.
- **API**, new tab, becomes the developer surface.

No third tab (no separate "Guides" or "Reference" tab), Guides live inside Main, Reference lives inside API.

**Why this is low-risk:** a Mintlify tab is a navigation grouping only, it does not change a page's file path or rendered URL. Moving a page from the "Main" tab's tree to the "API" tab's tree in `docs.json` does not require moving the file or adding a redirect. This means the beginner/developer split (the single biggest gap from the audit) can be executed almost entirely as a `docs.json` re-grouping, not a file-by-file migration. It also means Confusing Content #5 from the audit (Modules pages mixing beginner/developer content in a beginner nav slot) is resolved simply by which tab a page's group is listed under.

---

## Tab 1: "Main", Server Owners & Administrators

**Who:** non-technical to semi-technical server owners going from "I bought this" to "it's working."
**Why it exists:** every page here must be answerable without reading API docs, per the brief's Goal #2/#4.

### General (unchanged group, stays cross-product)
- Home (existing `index.mdx`), **gets a product catalog added** (CardGroup linking to all 16 products' Main-tab home pages), fixing the audit's #1 navigation problem. Structural addition only (links to existing pages), no new factual content.
- How to update
- Troubleshooting, **absorbs** `fivem-escrow-system-errors/failed-to-verify-protected-resource` as an additional accordion entry instead of it sitting as an unrelated standalone nav item (audit: Navigation Problems #3).
- Common FAQ
- Licensing
- Nexus Terms

### Per product (×16), Main tab
Same shape for every product, so a server owner learns the pattern once:

- **Home**, product overview, always in the richer style already used by `jaksam-inventory/home.md` (Quick Start, what it does, links to Installation/Guides/FAQ), applied consistently instead of the thin two-link version currently on Jobs Creator and others (audit: Confusing Content #3).
- **Installation**, rewritten to follow one consistent structure across all 16 products (audit: Confusing Content #4), and to close the two structural gaps from the audit:
  - Add a short **Requirements** block before step 1 (framework version, `oxmysql`/`ox_lib`, other resource dependencies), pulled from what's already implied in each product's existing Start Order Example, not invented.
  - Add a **Verification** step at the end (e.g., run a command / open a menu / expected result), **only where the existing docs already state how to check it worked**; where they don't, mark `[TODO: INFORMATION NEEDED]` rather than inventing a check.
  - Framework branching (`<Tabs>` + `<Steps>`) becomes the standard pattern for every product that has framework-specific steps, matching what Jobs Creator already does best.
- **Configuration**, only split out as its own page where a product actually has enough distinct config content to warrant it (e.g. Jaksam Inventory's backwards-compatibility settings); otherwise stays a clearly-labeled section inside Installation. Decided per-product in Phase 3, not blanket-applied.
- **Guides**, existing task-oriented pages that are genuinely server-owner-facing, e.g. `how-to-give-keys-with-car-command`, `fix-hotwiring-bought-car`, `lock-unlock-vehicle`, `how-to-use-custom-sprites`, `change-doors-icon`, `admin-bypass-lock`, `how-to-edit-minigames`, `how-to-use-images-for-items`, `how-to-enable-discord-features`, `commands-usage`, `external-deferrals`. Grouped under one "Guides" sub-group per product instead of sitting loose at the product's top level.
- **FAQ**, every product gets this slot even if currently empty; the 6 products without one (Billing UI, Luxury Clothes Theft, Races Creator, Farming Creator, Missions Creator, Dealerships Creator) get a placeholder page marked `[TODO: INFORMATION NEEDED]`, not a fabricated FAQ.

**Explicitly NOT in Main:** anything about exports, events, parameters, return values, or editing `_modules`/integration Lua files. Those move to API.

---

## Tab 2: "API", Developers

**Who:** people integrating with or extending a jaksam product, reading/writing Lua, wiring up external scripts.
**Why it exists:** per the brief's Goal #4, a developer shouldn't have to wade through install guides to find an export.

### General (new, minimal)
- **Developer Overview** (new landing page for the API tab), explains the conventions used across every reference page (Side, Parameters, Return value, Errors, Notes, see `03-migration-plan.md`/Phase 5 for the exact template), and links out to each product's API section. This is the API tab's equivalent fix to the Main tab's homepage product-catalog problem, otherwise clicking "API" has no obvious landing content. Purely structural/navigational (links + convention explanation), no invented technical claims.

### Per product (×16), API tab
- **Client**, unchanged structure (existing nested feature groups: Notifications, Actions, Duty, etc.), moved as-is from its current nav position into the API tab.
- **Server**, same, unchanged structure, moved as-is.
- **Advanced/Integration** pages that are really developer tasks, relocated here from where they currently sit at the product's beginner-tier top level (audit: Confusing Content #5):
  - `jobs-creator/modules.md`, `drugs-creator/modules.md`, `doors-creator/modules.md`, `shops-creator/modules.md`
  - `jobs-creator/replacing-default-scripts-names.md`, `jobs-creator/replacing-default-events-names.md`, `jobs-creator/qbcore-jobs-injection.md`
- **Jaksam Inventory exception:** `Functions/` (client, shared, server), `Events/`, and `hooks.md` move into the API tab as-is for now. Restructuring them into the same 1-export-per-page convention as the other 15 products is a Phase 4 rewrite task (audit: Technical Gaps #3), not an IA/placement change, the content moves tabs first, gets restructured internally later.

**Explicitly NOT in API:** installation steps, FAQ, anything phrased as "how do I turn this on as a server owner."

---

## URL structure

**Decision: no URL changes driven by the tab split itself.** Since tabs are a `docs.json`-only construct, every existing page keeps its current path/URL when it moves from Main's tree to API's tree (or vice versa for Modules pages). This satisfies the brief's "avoid unnecessary URL changes" rule and means **no redirects are needed for the tab reorganization**.

URL changes are still needed, but only for the small set of items with an actual location problem, identified in the audit:
- `untitled-page-2.mdx` → `jobs-creator/server/harvest/item-harvested.mdx` (new URL, needs redirect)
- `untitled-page-3.mdx` → `jobs-creator/server/shop/item-bought.mdx` (new URL, needs redirect)
- `fivem-escrow-system-errors/failed-to-verify-protected-resource.md` → folded into `jaksams-scripts/troubleshooting.mdx` as an accordion section (needs redirect from old URL)
- Any new pages (Developer Overview, missing FAQ placeholders) are net-new URLs, not moves, no redirect needed, nothing to preserve.

Full old→new mapping with redirect entries is Phase 3's job, not repeated here.

---

## Cross-linking rules going forward

- Every product's Main-tab **Home** links to that product's API-tab landing (Client/Server groups) for anyone who turns out to be a developer despite starting on Main.
- Every product's API-tab **Client/Server root pages** link back to that product's Main-tab Home (so a developer landing directly via search isn't stranded without install/context info).
- Troubleshooting (Main, General) gets a link from each product's Installation page's closing section, so install-time problems have one obvious next step.
- The new **Developer Overview** page (API, General) is the one place that explains the reference-page convention once, so individual reference pages don't need to repeat it.

---

## Summary table

| Nav location | Tab | Audience | Contains |
|---|---|---|---|
| General | Main | Server owner | Home/catalog, update, troubleshooting, common FAQ, licensing, Nexus terms |
| `<product>` → Home/Installation/Configuration/Guides/FAQ | Main | Server owner | Everything needed to install + use without reading code |
| General → Developer Overview | API | Developer | Reference conventions + links to every product's API section |
| `<product>` → Client/Server | API | Developer | Exports, events, parameters, return values (unchanged structure) |
| `<product>` → Modules/advanced integration | API | Developer | Custom module creation, script/event renaming, framework injection |

---

## Mintlify mechanisms to use (confirmed against official docs.json schema + docs, not assumed)

- **`redirects`** (`docs.json`, array of `{source, destination}`), for every page whose URL actually changes (moved/renamed/merged into another page). Preserves any existing ranking/backlinks on the old URL. Already the #1 priority item in `seo-ux-dx-strategy.md`; this restructure adds a handful more entries to that same list (see Phase 3).
- **`hidden: true`** (valid on groups, tabs, and individual pages in `docs.json`), the mechanism for the "Archive/unused pages" request. By default a hidden group is excluded from the rendered sidebar **and** from search/sitemap/llms.txt (confirmed: the opt-in `searchable: true` is what would keep a hidden page indexed, we deliberately do *not* set it here). Plan: one `hidden: true` group per relevant tab (e.g. "Archive" under Main, "Archive" under API) collecting pages we've moved out of active use during Phase 3/4 but haven't confirmed safe to delete yet. File stays on disk, nothing is destroyed, nothing leaks into Google. This group gets reviewed and emptied (deleted for real, or given a proper redirect) by the end of Phase 4, it's a staging area, not a permanent home.
- **`tag`** (badge on nav entries, e.g. the green "Update" pills already visible on the live site), used sparingly for real signals only (e.g. temporarily marking pages that were substantially restructured this pass), not as decoration.
- **Changelog/Roadmap**, Mintlify has no dedicated blog/changelog page type, but supports the pattern via a normal page using the `<Update>` component (this is how Mintlify's own docs site does it), reachable via a persistent `anchors` entry (like the existing Discord/Store links) rather than a third tab. **Not being built now**, noted for later per the "2 tabs for now" decision below.

## Decisions (confirmed 2026-08-10)

1. **Configuration: decided per product**, not blanket-applied, folded into Installation unless a product has enough distinct config content to earn its own page (e.g. Jaksam Inventory). Exact call per product happens in Phase 3.
2. **Developer Overview page: approved**, new, purely structural (conventions + links to existing content), no invented technical facts.
3. **Tab count: stays at 2 (Main/API) for now.** A future Changelog does not need a third tab if/when it happens, it would use the `anchors` mechanism above instead. No roadmap planned.
4. **Unused-page handling: `hidden: true` Archive groups**, not deletion, per the mechanism above, files preserved for review, kept out of nav/search/sitemap.
5. **URL changes get real `redirects`**, not just archival, hiding a page and creating a new one at a different URL without a redirect would forfeit any existing SEO equity on the old URL.

Phase 3 (migration plan) is next: the full per-page table (keep/move/rename/merge/split/archive) with exact `docs.json` redirect entries and the Archive-group contents.
