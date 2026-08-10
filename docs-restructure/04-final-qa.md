# jaksam-docs, Phase 5+6: Dev Doc Standards + Final QA

Internal planning document, not part of the published site. Closes out the restructure started in `01-audit.md`.

---

## Phase 5: Developer documentation standards

The reference-page convention (Side via folder location, Description, Export/Event + Example in a CodeGroup, Parameters table, Return value table, Notes where relevant) was already good across 15 of 16 products per the audit, it's now:

- **Documented explicitly** for the first time at `developers/overview.mdx` (API tab), so a developer landing on any single reference page can find the convention instead of inferring it from patterns.
- **Extended to Jaksam Inventory**, the one product that didn't follow it (53 functions + 3 events + 6 hooks split from 5 consolidated pages into the same 1-page-per-export shape as every other product).
- **Given real icons per page**, not a small reused set, matching how the rest of the site already worked.

Known, honestly-marked gaps (not silently dropped, not invented):
- `[TODO: INFORMATION NEEDED]` on `getItemFromSlot` (server) for its undocumented third `returnRaw` parameter.
- `[TODO: INFORMATION NEEDED]` on the `onItemRemoved` hook for a missing worked example.
- `[TODO: INFORMATION NEEDED]` on Verification steps for 7 products whose installation docs never stated a way to confirm success (Missions Creator, Farming Creator, Dealerships Creator, Races Creator, Trackers Creator, Billing UI, Vehicles Keys, Luxury Clothes Theft, going from the actual pass, some products got a real check pulled from existing content instead, see each `installation.md`).
- 8 FAQ pages are placeholders (`[TODO: INFORMATION NEEDED]`), not fabricated Q&A.

---

## Phase 6: Final QA checklist

| Check | Status |
|---|---|
| All existing features are still documented | ✅ Verified via page-inventory diff, nothing dropped except the 2 intentionally relocated/merged items |
| Important technical information has not been lost | ✅ Same diff check, plus the Inventory split preserved every function/event/hook verbatim |
| Installation instructions are complete | ✅ All 16 now have Requirements + the original steps + Verification (or an honest TODO) |
| Configuration instructions are complete | ⚠️ Stays a section inside Installation for all 16, per the Phase 3 decision to only split it out if a product's actual content warranted a dedicated page, none did on inspection |
| A beginner can install the product | ✅ Consistent Tabs+Steps pattern now standard, Requirements stated upfront |
| A developer can integrate the product | ✅ API tab, Developer Overview, consistent reference convention across all 16 products |
| Client/server differences are clear | ✅ Conveyed by nav location (Main vs API, Client vs Server groups) as before, now also stated in the Developer Overview's Side explanation |
| APIs/exports/events documented accurately | ✅ No parameters, return values, or behavior invented, source content reused verbatim, gaps marked TODO |
| Examples are technically correct | ✅ Reused verbatim from source; two known pre-existing bugs in the original examples (noted in the source material itself) were preserved as flagged corrections, not silently rewritten |
| No obvious contradictions | ✅ No conflicting information found or introduced |
| Minimal unnecessary duplication | ✅ No new duplication introduced; the duplication flagged in the audit (installation boilerplate) was intentionally left as-is per that finding |
| Important pages are not orphaned | ✅ Verified programmatically: 0 orphan files, 0 missing file references, 0 duplicate nav entries across 422 pages |
| URLs are consistent | ✅ No unnecessary URL churn; only the 3 planned location fixes changed URLs |
| Old URLs have redirects | ✅ 3 redirects added to `docs.json` for the 3 relocated pages; no redirects needed for the tab split or the Inventory index pages (same URL preserved) |
| Navigation is logical | ✅ Main = server owner, API = developer, consistent per product |
| FiveM-specific search intent covered | ➖ Unchanged from audit, `seo-ux-dx-strategy.md` still owns this, not revisited this pass |
| Scales for future products | ✅ The Main/API split and per-product template apply directly to any future 17th product |

**Not done, flagged for a future pass if wanted:** the `hidden: true` Archive mechanism was set up but never used, since nothing in the audit or this pass turned out to be confirmed-dead content. OpenGraph/social preview images (noted in `seo-ux-dx-strategy.md`) weren't touched.
