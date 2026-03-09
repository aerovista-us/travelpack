## Travel pack page updates – March 2026

- **HTML files**: `travel pack - latest.html` → consolidated into `index.html`

- **What changed**
  - Swapped the four SVG product placeholders in the “Product visual slots” section for real photos:
    - `Anker 737.jpg`
    - `UGREEN 20K.jpg`
    - `INIU 10K.jpg`
    - `EPICKA Universal Travel Adapter.jpg`
  - Added a product photo for the backup drive:
    - `SAMSUNG T7 Shield 1TB.jpg` in the “Backup Storage” product card.
  - Updated product copy so key specs match current official pages (capacity, wattage, ports) while avoiding hard-coded prices that will go stale.
  - Tightened duplicated “gear recap” text into shorter quick-reference cards, keeping the Summit teaching tone but making it easier to skim.
  - Slightly refined the `.diagram` CSS so real photos scale cleanly inside cards on different screen sizes.
  - Promoted `index.html` to the canonical, Italy-focused travel-pack page with the same content and visuals.

- **How to use this page now**
  - Treat the SVG diagrams as teaching aids and the photo slots as concrete product examples you can swap over time.
  - When you change hardware recommendations in the future, update:
    - The relevant product card text and links.
    - The associated JPG in the same folder (or point the `<img>` tag at a new file).

## Italy-specific refinements – March 2026

- **Italy-only assumptions**
  - Trip is scoped to Italy, so plug guidance and examples now emphasize Euro-style sockets (Types C/E/F) and slim adapters that fit recessed outlets.
  - Pack-tier guidance leans deliberately into the **Balanced** setup: 20K–24K main bank + 10K day bank + 65W charger + SSD.

- **What changed**
  - Updated hero chips and plug-adapter teaching cards to call out Italy plugs explicitly and recommend a slim EU adapter instead of heavy multi-region blocks.
  - Added back several SVG teaching diagrams from the earlier `travel pack.html`, including:
    - Power flow map (wall → charger → main bank → laptop/phone/SSD).
    - Battery legality / Wh comfort zone.
    - ONE Plan voice vs data decision diagram (cleaned labels for easier reading).
    - Plug map (now annotated so Type C/E/F are clearly “enough for Italy” and Type G is framed as future UK/Ireland use).
    - Connectivity fallback ladder (T‑Mobile → eSIM → local SIM).
  - Strengthened cable and adapter copy so a non‑technical reader understands:
    - Which cables to bring (100W USB‑C + Lightning).
    - Where to use them (hotel vs transit vs city walks).
    - How the Balanced tier maps to the final recommended stack.

## Index.html UI/UX refinements – March 2026

- **Information architecture**
  - Added an **“On this page”** mini table of contents linking to gear, connectivity, diagrams, product picks, pack tiers, and final stack.
  - Added stable `id` anchors to major sections so you can deep-link directly into specific teaching blocks.

- **Typography and readability**
  - Increased space above section headings and normalized spacing around cards and grids for easier scanning.
  - Broke several dense paragraphs into “If you remember one thing…” lead sentences plus short bullet lists for non‑technical readers.

- **Diagrams and teaching aids**
  - Added short captions under the weight-conscious pack and daily routine SVGs explaining when to use each diagram.
  - Clarified plug guidance text so Italy’s C/E/F plug family is explicitly tied to the plug map diagram.

- **Balanced + Italy emphasis**
  - Updated hero chips, fast-read blocks, and the pack tiers table copy so the page clearly assumes an **Italy-only, Balanced** setup.
  - Labeled the Anker 737 and INIU 10K product blurbs as “Balanced main bank” and “Balanced day bank” for quick orientation.

- **Checklists and final stack**
  - Added two quick-reference checklists near the bottom: a **night-before move-day** checklist and an **airport security** checklist.
  - Expanded the “Recommended final stack” section with a one-line “short answer” summary that explicitly calls out the Balanced Italy setup.

## Europe Travel Companion – SVG upgrades – March 2026

- **HTML file**: `europe-travel-companion.html`

- **New SVG components**
  - **Trip phase ribbon (Overview tab)**: inline SVG under `Trip snapshot` that shows whether you are *before*, *during*, or *after* the trip. Driven by `tripStart`/`tripEnd` via `getTripPhase()` and updated in `renderOverview()` using `updateTripPhaseSvg(phase)`.
  - **Daily routine diagram (Overview tab)**: four-step Night → Morning → Transit → Arrival SVG replacing the plain list in “Simple travel routine”, with the current step highlighted via `getRoutinePhaseNow()` and `updateRoutineSvg(phase)`.
  - **Packing readiness gauge (Essentials tab)**: circular SVG gauge above the packing checklist that animates from 0–100% based on how many items are checked, updated in `renderPacking()` via `updatePackingGauge()`.
  - **Smart tips accent (Tips tab)**: a small lightbulb SVG above the built-in tips list; clicking it scrolls to the first smart tip for quick access.

- **Implementation notes**
  - All SVGs use the shared `.svg-diagram` class and existing color tokens (`var(--cyan)`, `var(--gold2)`, `var(--amber)`, `var(--green)`, `var(--line)`) so they visually match cards and KPIs.
  - Animations rely on CSS transitions triggered by data attributes (`data-phase`, `data-level`) instead of timers, and respect `prefers-reduced-motion` to stay comfortable for sensitive users.
  - No changes were made to the saved `state` shape, so JSON export/import remains fully compatible with earlier versions of the companion file.

