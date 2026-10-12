# CoreForge (static HTML/CSS prototype)

Build Smarter. Game Harder. Create Without Limits.
PC components marketplace and intelligent PC builder prototype for Bangladesh (BDT). No JavaScript, no frameworks.

## Open locally
Double-click `index.html`, or run `python3 -m http.server` in this folder and visit http://localhost:8000.
Fonts (Space Grotesk, Inter) load from Google Fonts when online; system fallbacks are used offline.

## Structure
index.html, pages/, products/ (12 category pages + one detail page per sample product), builds/ (builder, budget, popular, compare-builds), compare/, performance/ (gaming, creator), guides/, css/, assets/.

## Working features (pure HTML/CSS)
- Responsive layout, shared header/footer, CSS-only mobile menu and Components/Performance dropdowns
- All navigation links resolve to real pages
- Budget tabs on Build by Budget (CSS radio technique)
- Collapsible filter groups, scrollable tables and brand strip
- Static comparison tables with highlighted difference rows
- Reduced-motion support, skip link, visible focus states

## Prototype only (needs JavaScript and/or a backend)
Search, filtering and sorting, compare list, wishlist, saved builds, accounts, adding/removing parts in the builder, live totals, automatic compatibility checks, budget recommendation engine, FPS and workload analysis, build export, contact form.

## Data integrity
All products, prices, stock and specs are SAMPLE data labeled in the UI. No FPS benchmarks, reviews, discounts or warranties are invented; those fields show "Benchmark data unavailable" or "Not listed". Images are placeholder SVGs; brand tiles are text only. Add licensed photos and logos to `assets/`.

## Roadmap
1. Move products, compatibility rules, prices, benchmarks and retailers into JSON or a database using the same field names as `data.py`-style records.
2. Add JavaScript: filters/sort, compare list, builder state, compatibility rules engine, localStorage saved builds.
3. Add a backend/API: retailer price feeds (BDT), stock, accounts, verified benchmark ingestion with source and test conditions.
4. Implement the budget optimizer against the compatibility rules, then the FPS and creator analyzers from verified data.
5. Self-host fonts, add canonical URLs, run an accessibility audit.
