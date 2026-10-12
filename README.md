# CoreForge

**Build Smarter. Game Harder. Create Without Limits.**

CoreForge is a static HTML and CSS prototype of a PC components marketplace and intelligent PC builder, designed for Bangladesh with BDT (৳) pricing. It joins shopping, component comparison, build configuration, budget planning and workload-based performance analysis into one coherent experience.

> **Status: visual prototype.** There is no JavaScript and no backend. All products, prices, stock, specifications and builds are clearly labeled **sample data**. Features that need logic or live data are shown as interface designs and labeled as prototypes.

---

## 1. Project goals

The site is built to answer six questions:

1. What PC components can I buy, and how much do they cost?
2. Which component is better for my needs?
3. Are all the components in my build compatible?
4. What is the best PC I can build within my budget?
5. What games can I play, and what performance can I expect?
6. How well will my PC handle editing, design, programming, streaming, rendering and productivity software?

**Audience:** gamers, PC enthusiasts, video editors, content creators, programmers, designers, students and workstation users.

## 2. Constraints

| Area | Rule |
|---|---|
| Markup | HTML5, semantic elements |
| Styling | External CSS only, shared design system |
| JavaScript | Not used in this implementation |
| Frameworks | None (no Bootstrap, Tailwind, React, Vue) |
| Backend | None |
| Responsive | Desktop, tablet, mobile (360, 390, 768, 1024, 1440 px targets) |
| Accessibility | WCAG-informed: semantic headings, labeled forms, visible focus, reduced-motion support |
| Currency | BDT with South Asian digit grouping (for example ৳1,05,000) |

## 3. How to open it

1. Unzip the project.
2. Double-click `index.html`, **or** from the project folder run:

   ```
   python3 -m http.server 8000
   ```

   then visit http://localhost:8000.

Space Grotesk and Inter load from Google Fonts when you are online. Offline, system fonts are used.

## 4. Project structure

```
coreforge/
├── index.html                  Homepage
├── pages/                      Supporting pages
│   ├── components.html         Category hub
│   ├── search.html             Placeholder (needs JS/backend)
│   ├── saved-builds.html       Placeholder
│   ├── compare-list.html       Placeholder
│   ├── wishlist.html           Placeholder
│   ├── account.html            Placeholder
│   ├── about.html
│   ├── contact.html
│   ├── privacy.html            Template text, not legal advice
│   ├── terms.html              Template text, not legal advice
│   └── methodology.html        Data and benchmark rules
├── products/                   12 category listings + 36 product detail pages
│   ├── cpu.html, gpu.html, motherboard.html, ram.html, storage.html,
│   │   psu.html, case.html, cooler.html, fans.html, monitors.html,
│   │   peripherals.html, prebuilt.html
│   └── <product-id>.html       e.g. r5-5600.html, rtx-4060.html
├── builds/
│   ├── builder.html            PC Builder (static example)
│   ├── budget.html             Build by Budget
│   ├── popular.html            Six example builds
│   └── compare-builds.html     Two-build comparison
├── compare/
│   ├── index.html              Comparison hub
│   └── cpu, gpu, ram, ssd, motherboard, psu .html
├── performance/
│   ├── gaming.html             Gaming performance analyzer
│   └── creator.html            Creator and productivity analyzer
├── guides/
│   ├── index.html
│   ├── choose-a-psu.html
│   ├── cpu-sockets.html
│   └── vram-explained.html
├── css/
│   ├── global.css              Tokens, typography, buttons, tables, forms
│   ├── header.css              Utility bar, navigation, dropdowns, mobile menu
│   ├── footer.css
│   ├── home.css                Hero, tools, product cards, builds, brands
│   ├── products.css            Listings, filters, product detail
│   ├── builder.css             Builder slots, summary, budget tabs
│   ├── comparison.css          Comparison tables and verdicts
│   ├── performance.css         Analyzer dashboard, gauges, rating grid
│   └── responsive.css          Cross-page responsive refinements
├── assets/
│   ├── images/                 hero-build.svg and ph-<category>.svg placeholders
│   ├── logos/                  Empty: add licensed brand logos here
│   └── icons/                  Empty
├── tools/
│   ├── data.py                 Sample catalogue, builds and budget examples
│   └── gen.py                  Page generator (see section 11)
└── README.md
```

## 5. Design system

**Direction:** dark-first, data-rich, restrained. Layered charcoal surfaces, thin borders, small corner radius (4 px), a single lime accent for actions and positive states, teal for secondary actions and data. No neon gradients, glassmorphism or decorative glow.

**Color tokens** (defined in `css/global.css`)

| Token | Value | Use |
|---|---|---|
| `--bg` | `#0B0D10` | Page background |
| `--surface` | `#13171C` | Panels, cards |
| `--surface-2` | `#1A2027` | Table heads, inputs |
| `--border` | `#2A323C` | Borders, dividers |
| `--text` | `#F3F5F7` | Primary text |
| `--muted` | `#9AA5B1` | Secondary text |
| `--lime` | `#B6F36A` | Primary actions, selection, positive |
| `--teal` | `#5DD6C0` | Secondary actions, data |
| `--warn` | `#F4B860` | Unknown or sample status |
| `--err` | `#FF6B6B` | Genuine incompatibility or error |

**Typography:** Space Grotesk for headings and prominent numbers; Inter for body, navigation, forms, tables and specifications. System fallbacks are provided. Prices and specs use tabular numerals.

**Reusable patterns:** `.btn` (primary, teal, small), `.chip` (ok, warn, err, sample), `.notice`, `.panel`, `.table-scroll`, `.pcard` (product card), `.prow` (listing row), `.slot` (builder slot), `.verdict`, `.gauge`.

**Signature element:** a blueprint-style hero schematic of a motherboard, memory and GPU on a faint grid, kept as the one memorable visual with everything else quiet.

## 6. Pages in detail

### Homepage (`index.html`)
Hero ("Your Next PC Starts Here."), four quick-start tools, featured components (CPU, GPU, motherboard, RAM, SSD, PSU), six popular builds, trending games table, creator and productivity workloads, price trends and deals, hardware brand strip, guides, final call to action and footer.

### Components (`products/`)
Each category page has a filter sidebar (collapsible groups matched to that category), a sort control, and product rows with image, brand and model, sample BDT price, stock status, key specs, a compare checkbox, **View details** and **Add to build**. Each product has a detail page with a full specification table.

### Compare (`compare/`)
Side-by-side tables for CPU, GPU, RAM, SSD, motherboard and PSU. Rows that differ are tinted and tagged, the price difference is shown, and recommendations are split by workload. No universal winner is declared.

### PC Builder (`builds/builder.html`)
Ten slots (CPU, cooler, motherboard, RAM, GPU, storage, PSU, case, fans, optional monitor and peripherals) with Replace and Remove controls, and a build summary showing total, example budget, remaining budget, estimated power and recommended PSU. The compatibility panel separates **Verified** from **Unknown** and states plainly that the build is **not verified as compatible** while any required data is missing.

### Build by Budget (`builds/budget.html`)
Custom budget field, nine intended-use options, six preferences, and example builds for ৳30,000, 40,000, 50,000, 60,000, 80,000, 100,000 and 150,000+. Each shows a component cost table, remaining budget and trade-offs. The page also lists the eight steps a real recommendation engine would follow.

### Popular builds and build comparison
Six example builds (budget gaming, 1080p competitive, 1440p gaming, video editing, programming, streaming and content creation) built from catalogue items, and a two-build comparison covering cost, parts, estimated power and upgrade potential.

### Performance (`performance/`)
- **Gaming:** input panel (CPU, GPU, RAM, game, resolution, preset, upscaling), result gauges that show "Not available" until verified data exists, a record format for future benchmark data, and a game library grouped into competitive shooters, battle royale, AAA, racing, simulation and strategy.
- **Creator:** rating label definitions (Basic, Comfortable, Strong, High-performance), a matrix of 13 applications against seven hardware factors, common limitations (VRAM, RAM, codec support), and the rating methodology.

### Guides (`guides/`)
Three original explainers (power supplies, CPU sockets, VRAM) and a note that reviews are published only after real testing.

## 7. Navigation

Main: Components (dropdown of all 12 categories), PC Builder, Compare, Build by Budget, Performance (dropdown), Guides & Reviews.
Utility: Search, Saved Builds, Compare List, Wishlist, Account, Currency: BDT.
**Build My PC** is the most prominent action.
The mobile menu and dropdowns work with CSS only (checkbox toggle, `:hover` and `:focus-within`).

## 8. Working features

- Responsive layouts and a shared header and footer on every page
- CSS-only mobile menu and dropdowns
- Every navigation link resolves to a real page (checked by script)
- Budget example switcher (CSS radio technique)
- Collapsible filter groups
- Horizontally scrollable tables and brand strip, with no page-level horizontal overflow
- Skip link, visible focus styles, labeled form controls
- Reduced-motion support

## 9. Prototype-only features

These require JavaScript and/or a backend and are **not operational**. Each is labeled in the interface.

| Feature | What is needed |
|---|---|
| Search | Index plus JS or server search |
| Filtering and sorting | JS or server-side queries |
| Compare list, wishlist, saved builds | Storage (localStorage or database) |
| Accounts and sign-in | Backend authentication |
| Adding and removing builder parts, live totals | JS state |
| Automatic compatibility checks | Rules engine with complete spec data |
| Budget recommendation engine | Optimizer plus compatibility rules |
| FPS and workload estimates | Verified benchmark database |
| Export build summary | JS or server rendering |
| Contact form | Form endpoint |

## 10. Data integrity rules

The prototype never fabricates:

- Live prices, stock, retailer discounts or price history
- Hardware specifications presented as verified
- Official product images
- FPS benchmarks or creator-app scores
- Compatibility results (unknown stays "Unknown")
- User reviews, ratings or manufacturer warranties

How this shows up in the interface:

- Prices carry a **Sample price** chip; stock reads "(sample)"
- Benchmarks read **Benchmark data unavailable**
- Missing specs read **Not listed** or **Not in sample data**
- Ratings read "no verified reviews"
- Brand tiles are text only; no logos are bundled and no partnership is implied
- Product images are placeholder illustrations

Please verify every specification against manufacturer data sheets before using any value outside the prototype.

## 11. Regenerating pages

The HTML is generated from one catalogue so pages stay consistent. To change products, prices or builds:

1. Edit `tools/data.py` (products, `POP` popular builds, `BUD` budget examples).
2. Edit `tools/gen.py` for layout or copy.
3. From the `tools/` folder run `python3 gen.py`. It rewrites the HTML pages and placeholder SVGs in the project root.

The CSS files are hand-written and are not touched by the generator.

**Data record shape** (see `data.py`): `id`, `cat`, `brand`, `model`, `price` (BDT integer), `stock`, `specs` (ordered label/value pairs) and `keys` (specs shown on cards). The same shape maps directly to a database table or API response.

## 12. Responsive and accessibility notes

- Single-column product listings and stacked panels on mobile; comparison and data tables scroll inside their own containers
- Touch targets are at least 44 px for primary controls
- One `h1` per page with an ordered heading hierarchy; descriptive page titles and meta descriptions
- Informative alt text on images; decorative marks are hidden from assistive technology
- Status is never conveyed by color alone (chips carry text)
- Add canonical URLs once a real domain is configured

## 13. Roadmap

1. **Data layer:** move the catalogue to JSON or a database using the record shape above; add compatibility fields (GPU length, case clearance, cooler height, M.2 slots, connector requirements, BIOS support).
2. **JavaScript layer:** filters and sorting, compare list, builder state and live totals, localStorage saved builds, compatibility rules engine, build export.
3. **Backend:** Bangladesh retailer price and stock feeds, warranty data, accounts, wishlist and saved builds sync.
4. **Benchmarks:** ingest verified results with game version, drivers, settings, hardware and source, then enable the FPS analyzer and labeled estimates.
5. **Optimizer:** implement the eight-step budget recommendation using the rules engine, with alternatives and explanations.
6. **Creator analyzer:** per-application scoring from verified benchmarks using the documented methodology.
7. **Polish:** licensed product photography and brand logos, self-hosted fonts, canonical URLs, full accessibility and cross-browser audit, reviewed privacy policy and terms.

## 14. Credits and notices

Brand and product names belong to their respective owners and appear for illustration only. Privacy and Terms pages are placeholder templates, not legal advice.
