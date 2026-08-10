# jaksam-docs, Phase 1: Documentation Audit

Internal planning document, not part of the published site (not referenced in `docs.json` nav). Produced before any restructuring/rewriting, per the FiveM Documentation Restructure brief.

**Scope note:** This repository contains documentation only, no product source code (Lua/JS) is present to cross-check exports, events, or parameters against an implementation. Per the brief's rule #20, the existing documentation is treated as source of truth throughout this audit. Findings are based on a full read of `docs.json` (complete navigation tree, 352 pages across 16 products) plus targeted sampling of representative pages in each category (home, installation, FAQ, client reference, server reference, general/global pages) across ~10 of the 16 products, chosen to cover every structural pattern in the repo. Findings described as "pattern" were confirmed in 3+ products; findings scoped to one product are labeled as such.

---

## Current Documentation Map

Top-level nav has one **General** group (global, cross-product pages) and **16 product groups**, each following a mostly-similar internal shape:

```
General
├── how-to-update-the-scripts
├── troubleshooting
├── common-faq
├── licensing
├── nexus-terms
└── failed-to-verify-protected-resource   (fivem-escrow-system-errors/, see Navigation Problems)

<Product> (×16: Jaksam Inventory, Jobs Creator, Drugs Creator, Doors Creator,
           Missions Creator, Blips Creator, Farming Creator, Shops Creator,
           Robberies Creator, Vehicles Keys, Dealerships Creator, Races Creator,
           Trackers Creator, Easy Allowlist, Billing UI, Luxury Clothes Theft)
├── home                       (root page for the group)
├── installation
├── faq                        (10 of 16 products only, see Missing Content)
├── modules / other top-level guides (varies per product)
├── Client/                    (nested groups → 1 export or event per page)
│   └── <feature>/<page>.md
└── Server/
    └── <feature>/<page>.md
```

Exceptions to this shape:
- **Jaksam Inventory** does not use Client/Server-with-nested-feature-groups. It uses `Functions/` (client, shared, server, one long page each listing multiple exports) + `Events/` (server) + a standalone `hooks.md` page. This is the only product organized this way. See Technical Gaps.
- **Easy Allowlist** has no Client group at all (Discord/allowlist product, server-only), which is correct for what it does, not an inconsistency.
- Two files exist at the **repository root** with no product namespace: `untitled-page-2.mdx`, `untitled-page-3.mdx`. Both contain real reference content but were never renamed/moved after the GitBook→Mintlify migration. See Confusing Content.

Full page-by-page tree is in `docs.json:39-936` (already read in full for this audit), not reproduced here line-by-line since it's the authoritative source.

---

## Duplicate Content

1. **Installation boilerplate**, near word-for-word across most products:
   - The FileZilla/WinSCP warning block.
   - The closing line "You are ready to go! Enjoy the script 😁"
   - This was already flagged in `seo-ux-dx-strategy.md` as acceptable UX repetition with low SEO risk (short blocks). Confirmed still valid, no action needed here beyond what that note already recommends.

2. **Per-product reference pages that are structurally identical templates with only the product/item name changed**, e.g. `replace-default-notifications`, `replace-default-help-notifications`, `replace-default-police-alert`, present in nearly every "Creator" product with the same shape (disable-default event + example). This is the intended DX pattern (1 export/event = 1 page), not a bug. Flagged only because Phase 4 should consider a shared template/snippet to keep these consistent when rewriting, not because they should be merged.

3. **`common-faq.md` vs. per-product `faq.md`** are complementary, not duplicate, common-faq covers cross-product issues (crashes, ESX nil errors, refunds), product FAQs cover product-specific behavior. No contradiction found in sampled pages, but see Missing Content, 6 products have no FAQ at all, so this split isn't applied consistently.

---

## Missing Content

1. **No product overview / catalog page.** `index.mdx` (the root/homepage) does not list or link to any of the 16 products. A visitor arriving at the domain root cannot discover what exists without already knowing a URL or using search. (Also flagged in `seo-ux-dx-strategy.md` §2, confirmed still unresolved.)

2. **No explicit "Requirements/Dependencies" section** on any sampled installation page. Dependencies (`oxmysql`, `ox_lib`, framework version) are only inferable from reading the `server.cfg` "Start Order Example" code block, never stated as a plain-language prerequisite list before the steps begin. This breaks the brief's requested progression (`Requirements → Download → Installation → ...`) at the first step.

3. **No "Configuration" as a distinct concept anywhere sampled.** Config is either folded into the Installation page (Jaksam Inventory), pushed into an in-game admin menu with no documented settings reference (Doors Creator: "configure from `/doorscreator`", no page documents what's configurable there), or absent. No product has a page answering "what do I configure and what does each option do" outside of a fully manual `server.cfg`/`config.lua` walkthrough.

4. **No "Verification" step.** None of the sampled installation guides tell the server owner how to confirm the install worked (e.g., a command to run, a UI element to check, an expected console line). This is one of the 8 explicit questions the brief requires beginner guides to answer, and it's currently unanswered everywhere sampled.

5. **FAQ coverage is inconsistent.** Per `docs.json`, only 10 of 16 products have a `faq.md` (Jobs Creator, Drugs Creator, Doors Creator, Easy Allowlist, Trackers Creator, Vehicles Keys, Blips Creator, Robberies Creator + the two General ones). Missing entirely: Billing UI, Luxury Clothes Theft, Races Creator, Farming Creator, Missions Creator, Dealerships Creator, and Jaksam Inventory (which instead has no FAQ page of any kind).

6. **No developer-facing landing page per product** (e.g., an "API/Reference overview" page one level above Client/Server that explains side, auth/permission model, and general conventions once instead of implicitly through folder structure). Currently a developer's only entry point is the Client or Server sidebar group itself.

7. **No "Errors" documentation anywhere sampled.** Every reference page sampled (`add-weapon-to-armory`, `duty-status-toggled`, `get-queue-count`, the two untitled pages) documents the happy path only, no failure modes (invalid ID, offline player, missing permission). The brief's reference convention explicitly asks for an Errors field; currently it doesn't exist as a pattern at all, so this must be filled with `[TODO: INFORMATION NEEDED]` per page during Phase 4, never invented.

---

## Confusing Content

1. **`untitled-page-2.mdx` and `untitled-page-3.mdx`** sit at the repository root with meaningless filenames despite containing real, on-topic content ("Item harvested" for Jobs Creator's Harvest module, "Item bought" for its Shop module). They render at `/untitled-page-2` and `/untitled-page-3`, flat, non-descriptive URLs completely disconnected from their actual location in the nav (`jobs-creator/server/harvest/` and `jobs-creator/server/shop/`). Clear migration leftover.

2. **Broken/inconsistent internal links on `jaksam-inventory/home.md`:**
   - The "Installation" and "Configuration" cards both link to the exact same target (`/jaksam-inventory/installation`), "Configuration" doesn't actually lead anywhere distinct because no separate configuration page exists (see Missing Content #3).
   - Framework anchor links are inconsistent: some use the full path (`/jaksam-inventory/installation#esx-1107`), others use a path missing the product prefix (`/installation#esx-1107`, `/installation#qbcore`, `/installation#qbx`), the latter resolve to the wrong page (root install page, not `jaksam-inventory`'s), if one exists at all.
   - A card links to `/backwards-compatibility` as if it were a standalone route; it's actually just an `## Backwards Compatibility` heading inside `jaksam-inventory/installation.md`, so the link target doesn't exist as written.

3. **Home-page quality is wildly inconsistent across products with no product-tier justification.** `jaksam-inventory/home.md` is a full hub page (Quick Start tabs per framework, framework-support cards, documentation cards). `jobs-creator/home.md`, arguably the second-most complex product in the repo, judging by its reference-page count, is two links (forum thread + Tebex store) and nothing else: no description of what the product does, no links to Installation/FAQ/Modules, no framework info. The good pattern already exists in the repo; it's just not applied consistently.

4. **Installation page structure differs per product for no apparent product-specific reason:**
   - Jaksam Inventory: `<Tabs>` per framework + plain numbered lists.
   - Jobs Creator: `<Tabs>` per framework + `<Steps>` component (clearest of the three sampled).
   - Doors Creator: `<Steps>` only, no framework branching at all, even though other products treat ESX vs. QBCore as materially different install paths.
   A server owner who's installed one jaksam product has to re-learn the doc pattern for the next one.

5. **"Modules" pages mix beginner and developer content in a beginner-tier nav slot.** `jobs-creator/modules.md` (and the equivalent in Drugs/Doors/Shops Creator) sits at the same top-level nav position as Installation and FAQ, but its actual content ("how to create a custom module", editing Lua files in `_modules/`, matching event names of a third-party script) is a developer/integrator task, not a server-owner task. This directly cuts against the brief's Goal #4 (separate beginner vs. developer content).

6. **Likely duplicate-sounding page titles within the same product**, based on the URL/slug pattern in `docs.json` (not yet content-verified): Jobs Creator has `client/buyable-vehicles/vehicle-spawned`, `client/garage-owned/vehicle-spawned`, and `client/temporary-garage/vehicle-spawned` as three separate pages, if their `title` frontmatter is just "Vehicle spawned" in each (as the slug suggests and as seen in other sampled pages, where title generally matches slug literally), they'd be indistinguishable in search results or browser tabs without the surrounding breadcrumb. **Flagged as needs-verification in Phase 2/3, not confirmed.**

---

## Technical Gaps

1. **No explicit "Side" (client/server) label in the page body.** Side is only conveyed by which nav group/folder the page lives in. The brief's reference convention wants Side as a stated field; right now a page viewed in isolation (e.g. shared via direct link, or indexed by Google) doesn't say whether it's client or server.

2. **No "Errors" or "Notes/Limitations" sections exist as a pattern anywhere** (see Missing Content #7). Every sampled reference page stops after Parameters/Return value.

3. **Jaksam Inventory's reference format is a structurally different convention from every other product**, despite being (arguably) the flagship product:
   - Multiple exports documented on one long page (`functions/client.md`) instead of one export per page.
   - Return values written as inline prose (`**Returns:** totalAmount (number), ...`) instead of the Markdown table convention used everywhere else (`add-weapon-to-armory.md`, `duty-status-toggled.md`, etc.).
   - Uses Mintlify `<ParamField>` components for parameters instead of the Markdown table used by every "Creator" product.
   This means the same underlying information (name, type, description, required-or-not) is presented in two incompatible visual/structural systems depending on which product a developer happens to be reading, with no technical reason found for the difference (both are exports documentation).

4. **No version/compatibility markers on individual reference pages.** `jobs-creator/updating-script-from-old-versions.md` implies breaking changes exist across script versions, but no reference page states which version it documents, so a developer can't tell if a page is current for their installed version.

---

## SEO Opportunities

`seo-ux-dx-strategy.md` (already in the repo) covers this ground in detail, redirects before merge, homepage as product catalog, duplicate `title: "Installation"` across 16 pages, cross-linking related products, OG tags. Treat that document as the SEO section of this audit; not repeating it here. Two additions from the IA angle specifically:

1. **No per-product "developer landing" page** means there's no single URL that could rank for intent like "jobs creator fivem exports" or "jaksam inventory api", that content only exists split across many deep, narrow reference pages with no aggregating parent that targets the broader query.
2. **No practical task-oriented guide pages separate from raw reference.** E.g., "how to replace the default notifications in Jobs Creator" currently *is* the reference page (`client/notifications/replace-default-notifications`), there's no separate, more narrative guide version of the same task. Per the brief's SEO goal #6, the reference page and a practical guide are meant to be two different pages serving two different search intents; right now only the reference version exists.

---

## Navigation Problems

1. **Root `index.mdx` doesn't link to any product**, the single biggest discoverability gap in the whole site (already covered above and in the SEO note).

2. **`untitled-page-2` / `untitled-page-3`**, covered above, also a navigation problem since their URLs give the visitor no indication of what product/feature they belong to.

3. **The "General" nav group mixes truly global pages (update guide, troubleshooting, common FAQ, licensing, Nexus terms) with one single-product page that doesn't belong there:** `fivem-escrow-system-errors/failed-to-verify-protected-resource`. This is a FiveM-platform-level escrow error, not something specific to any jaksam product, but it's filed as if it were a general jaksam doc rather than its own thing or folded into the general Troubleshooting page.

4. **No "related pages" / "see also" links observed on any sampled reference page.** The only way to get from a deep reference page back to its product's home, or sideways to a related export, is the sidebar, there's no in-content cross-linking at the leaf level.

5. **Nested category names repeat across Client and Server for the same product** (e.g. Jobs Creator has "Buyable Vehicles" under both Client and Server, each with their own sub-pages), not a bug, since client/server behavior genuinely differs, but combined with finding Confusing Content #6 (possible duplicate titles), this could make in-site search results hard to tell apart without opening them.

---

## Summary for Phase 2

The strongest, highest-leverage findings to carry into the IA proposal:

- Beginner and developer content are **not currently separated** anywhere (Modules pages, home-page inconsistency, no dev landing page), this is the brief's Goal #4 and is currently unmet almost everywhere.
- The **reference-page convention is good and should be preserved and extended**, not replaced, except for Jaksam Inventory, which needs to be brought into the same 1-page-per-export pattern used by the other 15 products.
- The **beginner installation flow is incomplete** at both ends: no stated requirements before it starts, no verification step at the end.
- **Two concrete cleanup items** (untitled pages, jaksam-inventory/home.md broken links) can be fixed with no IA change at all and don't need to wait for Phase 3/4.
