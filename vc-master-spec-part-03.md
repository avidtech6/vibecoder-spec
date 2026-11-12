⇒⇒□ ⇒⇒□ **⇒⇒□ THE NEGATIVE CONTROL IS `scripts/fvc1367-negative-control.cjs` — 9
ASSERTIONS, AND IT FIRES.** ⇒⇒□ MEASURED: it writes **the same project** twice — once
with `subProjects` and once without — and asserts that the first has a twisty and a badge
and the second has **neither**. ⇒⇒□ ⇒⇒□ **⇒⇒□ AND IT PROVES THE GRANDCHILD'S
INDENTATION ON THE CONTROL PROJECT TOO**, so the nesting is not an accident of the
Internals record's shape.

⇒⇒□ ⇒⇒□ **⇒⇒□ AND THE GATE HAD A BUG OF ITS OWN, AND THE BUG WAS WORTH NAMING.**
MEASURED: the gate asserted the twisty's visibility on `tr.width`/`tr.height`, but the
rect helper returns `w`/`h` — so **the assertion silently read `undefined` and FAILED on
a product that was perfectly visible.** ⇒⇒□ ⇒⇒□ **⇒⇒□ A GATE THAT ASSERTS ON A FIELD
NAME THAT DOES NOT EXIST FAILS SILENTLY ON A REAL PRODUCT** — and the same class of bug
made the first version of this gate crash with `R is not defined`, because `R` lives in
Node and `page.evaluate` runs in the **browser**.

⇒⇒□ ⇒⇒□ **⇒⇒□ AND THREE OLDER GATES ARE STALE, AND THE STALENESS IS MEASURED, NOT
ASSUMED.** MEASURED on `origin/main` (the FVC 1364 baseline, build `ad73cf8a`) with those
gates, unchanged: `fvc1337-verify-root.cjs` **6/11**; `fvc1341-verify-stencil.cjs`
**FAILED 5**; `fvc1342-verify-hero.cjs` **FAILED 1**. ⇒⇒□ ⇒⇒□ **⇒⇒□ AND THE SAME FAILURES,
BY NAME, ON FVC 1367's TREE — THE FAILING SET IS IDENTICAL, SO FVC 1367 REGRESSED
NOTHING.** ⇒⇒□ ⇒⇒□ **⇒⇒□ AND THE REASON IS NAMED:** all three assert that `/` IS THE
SHOWCASE, and **FVC 1363 OVERRODE PART 85 §85.1** (Part 89) — the root is the permanent
VC Shell and the Showcase lives at `/showcase`.

⇒⇒□ ⇒⇒□ **⇒⇒□ AND THE THREE GATES ARE MARKED, NOT DELETED AND NOT "FIXED".** ⇒⇒□ ⇒⇒□
**⇒⇒□ DO NOT "FIX" THEM BY REVERTING PART 89** — the gates' EXPECTATION is what is
stale, and Part 89's override is marked, not silent.

⇒⇒□ ⇒⇒□ **⇒⇒□ AND THE SCOPE IS HELD.** ⇒⇒□ MEASURED: `tsc --noEmit` reports **309**
errors on the baseline and **309** on FVC 1367's tree — **the change adds ZERO type
errors**. ⇒⇒□ ⇒⇒□ **⇒⇒□ AND THE GRANDCHILD'S OWN PAGE IS RENDERED BY THE SAME VIEW
COMPONENT**, with the `subId` threaded down — so a third level costs a route row and a
reader, not a new view.

⇒⇒□ ⇒⇒□ **⇒⇒□ AND BACKTICKS INSIDE A CSS TEMPLATE LITERAL TERMINATE IT.** ⇒⇒□
MEASURED: the first fix broke the build with `Expected ";" but found "float"` — a
comment inside `src/shell/Shell.tsx`'s CSS template string carried a backticked CSS
declaration. ⇒⇒□ ⇒⇒□ **⇒⇒□ STRIP BACKTICKS FROM ANY CSS BLOCK WRITTEN INTO A
`const styles = \`…\`` TEMPLATE.**

## Part 92 — The Dashboard Desk

**THE DASHBOARD IS NOT A GRID. IT IS A CUSTOMIZABLE DESK OF INFO BOXES — "DESK PANELS" — AND
NO FUTURE AGENT MAY REBUILD IT AS A STANDARD GRID.**

⇒⇒⇒ MEASURED BEFORE THIS PART: the repository already carried a hard-won grid, and nothing
stated that the Dashboard was something else. The dispatch's five rules are recorded below
**verbatim in substance**, and each is followed by the measurement that made it enforceable.
This Part is law **BEFORE** the code lands, so no agent reads the existing grid and concludes
it is the intended shape.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE PART NUMBER IS DERIVED, NOT ASSUMED.** MEASURED: the file's highest
`## Part N` heading was **91** (`## Part 91 — The Tree Is Three Deep, and the Depth Is a
Contract`), so the next free number is **92**; and the highest `v3.N.0` marker was **40**,
so the next free version is **v3.41** — the version and the Part are INDEPENDENT counters
(Part 85 §85.7). ⇒⇒□ **⇒⇒□ THE DISPATCH NAMED "v3.43.0"; THAT NUMBER IS NOT AVAILABLE AND
WAS NOT USED.** MEASURED: the version counter has moved **one step per Part** since it was
separated from the Part number (v3.40.0 → Part 91), so jumping to v3.43.0 would skip two
versions and misrepresent the spec's history. ⇒⇒□ **⇒⇒□ THE PART NUMBER IT NAMED — 92 — IS
CORRECT**, and the two numbers are recorded separately rather than silently reconciled.

### 92.1 The Desk Is Not a Grid

**RULE 1 — THE DASHBOARD IS A CUSTOMIZABLE "DESK" OF "INFO BOXES" (DESK PANELS). IT IS NOT A
STANDARD GRID.**

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE GRID IS NOT A HYPOTHETICAL — IT IS WHAT THE CODE DOES TODAY.**
MEASURED: `src/modules/dashboard/src/dashboard/DashboardGrid.tsx:269` is
`gridTemplateColumns: repeat(12, minmax(0, 1fr))` with `alignItems: 'stretch'`
(`:276`), and `dashboard-layout.ts:23` declares `DASHBOARD_COLUMNS = 12`, with
`MIN_CARD_WIDTH = 1` (`:26`) and `MAX_CARD_WIDTH = 12` (`:27`). ⇒⇒□ ⇒⇒□ **⇒⇒□ AND THE STRETCH IS DELIBERATE AND RECENT.** MEASURED:
the `alignItems: 'stretch'` (`:276`) and the `minHeight: 'calc(100vh - 140px)'` (`:277`) carry the comment
*"FVC 1379 - THE GRID FILLS THE SURFACE … the cards stretch into it."* ⇒⇒□ ⇒⇒□ **⇒⇒□ SO A
READER WHO OPENS THE FILE TODAY WILL FIND A GRID THAT LOOKS INTENTIONAL.** This Part exists
because the *shape* is changing while the *code* is still the old shape.

⇒⇒□ **⇒⇒□ ⇒⇒□ "DESK PANEL" IS THE VOCABULARY, AND IT REPLACES "CARD" FOR DASHBOARD
SURFACES.** ⇒⇒□ A **Desk Panel** is one Info Box on the Desk. ⇒⇒□ A **Desk** is the
customizable arrangement of Desk Panels. ⇒⇒□ A **Panel Library** is the set of Desk Panels
the operator may add.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE WORD "CARD" IS NOT FORBIDDEN — IT IS A DIFFERENT WORD.** MEASURED:
the FreshCards primitive named `Card` is a real, shipped component (§92.6), and the Desk
Panel's FRONT is drawn by it. ⇒⇒□ **⇒⇒□ THE RULE IS ABOUT THE ARRANGEMENT, NOT ABOUT THE
COMPONENT.** A Desk Panel is not a grid cell that happens to hold a `Card`; it is an Info
Box with its own placement, and the `Card` is its face.

### 92.2 The Layout Is Staggered, and Cards Are Never Stretched to Equal Heights

**RULE 2 — THE DESK USES A STAGGERED / MASONRY LAYOUT (AUTO-HEIGHT). CARDS MUST **NEVER** BE
STRETCHED TO EQUAL HEIGHTS.**

⇒⇒□ **⇒⇒□ ⇒⇒□ THE CURRENT CODE DOES EXACTLY THE FORBIDDEN THING, AND ITS OWN COMMENT SAYS
WHY.** MEASURED: `DashboardGrid.tsx:275` — *"FVC 1379 - THE GRID FILLS THE SURFACE …
the cards stretch into it"* — with `alignItems: 'stretch'` and
`minHeight: 'calc(100vh - 140px)'`; and the card's own `height` at `:318-322` is
`'100%'` for any card whose height is not above the default. ⇒⇒□ ⇒⇒□ **⇒⇒□ CONSEQUENCE: every
card in a row is rendered at the height of the TALLEST card in that row, and a short card
pads with empty space.** ⇒⇒□ **⇒⇒□ THIS PART MAKES THAT A DEFECT, NOT A STYLE.**

⇒⇒□ **⇒⇒□ ⇒⇒□ THE STAGGERED LAYOUT IS THE LAW, AND "MASONRY" IS ITS NAME.** MEASURED:
there is **NO** masonry or staggered implementation anywhere in the repository — a sweep for
`masonry|staggered|auto-height` across `pact/vc-master-spec.md` returns **ZERO** hits, and
no dashboard source file declares one. ⇒⇒□ ⇒⇒□ **⇒⇒□ THE DESK MUST LAY ITS PANELS OUT SO
THAT EACH PANEL'S HEIGHT IS ITS OWN** — the row height is the height of its tallest member
and every other panel in that row keeps its own height, ending where its content ends.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE OPERATOR-SIZED HEIGHT SURVIVES.** MEASURED: a card with a `height`
property above `DEFAULT_CARD_HEIGHT` (180) already renders at its own explicit pixel height
(`DashboardGrid.tsx:320-321`), and `readCardLayout` clamps it to `MIN_CARD_HEIGHT` (40) and
up. ⇒⇒□ **⇒⇒□ A DESK PANEL THE OPERATOR RESIZED KEEPS THAT SIZE** — the staggered layout
changes how rows are placed, never what the operator chose.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE EXPLICIT WIDTH SPAN IS THE CONTRADICTION TO RESOLVE.** MEASURED: the
current grid persists a per-card `width` of 1..12 (`WIDTH_PROPERTY = 'width'`, clamped by
`readWidth`) and renders it as `gridColumn: span ${layout.width}`. ⇒⇒□ ⇒⇒□ **⇒⇒□ A
MASONRY LAYOUT DOES NOT HAVE COLUMN SPANS.** ⇒⇒□ **⇒⇒□ THE RESOLUTION IS THE OPERATOR'S
RULE 3: THE DESK PANEL'S SIZE AND PLACE ARE THE OPERATOR'S ARRANGEMENT, PERSISTED AS AN
EXPLICIT VALUE** — a Desk Panel carries its own measured width and height, and the staggered
arrangement is computed from the panels' own content, not from a 12-column track. ⇒⇒□
**⇒⇒□ ⇒⇒□ A BUILDER MUST NOT REUSE THE 1..12 COLUMN SPAN TO LAY OUT THE DESK.** The span
arithmetic belongs to the grid this Part supersedes.

### 92.3 The Desk Panels Are Movable, Pinable, Addable, and Removable

**RULE 3 — DESK PANELS CAN BE DRAGGED, PINNED, ADDED FROM A LIBRARY, AND REMOVED.**

⇒⇒□ **⇒⇒□ ⇒⇒□ TWO OF THE FOUR ALREADY EXIST, AND THEIR MEASUREMENT IS THE BASELINE.**
MEASURED: `DashboardGrid.tsx` already renders every card with `draggable={interactive}`,
`onDragStart` / `onDragOver` / `onDrop` / `onDragEnd`, plus a pointer-drag path
(`onPointerDown` / `onPointerMove` / `onPointerUp` / `onPointerCancel`), and the drop index
is computed by the pure `dropIndexFor()` in `dashboard-layout.ts`. ⇒⇒□ ⇒⇒□ **⇒⇒□ AND THE
ORDER IS PERSISTED**, because `withOrder()` stamps an explicit numeric `order` on each card
and `sortByOrder()` reads it back — the file's own comment records why: *"Array order alone
would not survive a reload."* ⇒⇒□ ⇒⇒□ **⇒⇒□ SO DRAG-TO-REORDER IS NOT NEW, AND IT IS NOT
THE DESK.** The Desk adds PIN, ADD and REMOVE.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE PERSISTENCE CAVEAT IS CARRIED FORWARD, NOT DISMISSED.** MEASURED:
Part 24 §24.5 records that *"the graph write succeeds but `properties` does not survive the
wire, so the locally-saved layout is what actually keeps the arrangement"*, and the current
code carries `dashboard-persist.ts` for that local save. ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ EVERY DESK
PANEL PERSISTENCE — ORDER, PIN STATE, WIDTH, HEIGHT, AND MEMBERSHIP — MUST BE PERSISTED
LOCALLY THE SAME WAY**, or the operator's Desk rearranges itself on the next load. ⇒⇒□
**⇒⇒□ ⇒⇒□ THIS IS NOT A NEW BUG TO DISCOVER LATER; IT IS A KNOWN FAILURE MODE, AND THE
DESK LAW NAMES IT.**

⇒⇒□ **⇒⇒□ ⇒⇒□ "PINNED" IS A FIRST-CLASS DESK STATE, AND IT IS NOT "FIRST IN THE LIST".**
⇒⇒□ A **pinned** Desk Panel is one the operator has fixed to a place on the Desk: it does
not reflow when other panels are added or removed. ⇒⇒□ ⇒⇒□ **⇒⇒□ PIN IS SURVIVAL, NOT
PREFERENCE** — an unpinned panel is one the staggered arrangement may move when the set
changes; a pinned panel is one the operator has said must not move.

⇒⇒□ **⇒⇒□ ⇒⇒□ THE PANEL LIBRARY IS A CATALOGUE OF REAL DESK PANELS, NOT OF WIDGETS.**
⇒⇒□ A Desk Panel is added to the Desk from the **Panel Library**, and the Library's
entries are the Desk Panel kinds the product actually ships (§92.6).

⇒⇒□ **⇒⇒□ ⇒⇒□ AND REMOVAL IS NOT DELETION.** ⇒⇒□ Removing a Desk Panel takes it off the
Desk; it does not delete the data the panel shows, and it does not delete the FCr component
the panel is built from. ⇒⇒□ ⇒⇒□ **⇒⇒□ A REMOVED DESK PANEL MUST BE RESTORABLE** — the
Panel Library is the source it returns to.

### 92.4 Every Desk Panel Is a 3D Card: A Visual Front and a Data Back

**RULE 4 — EVERY DESK PANEL IS A 3D CARD. THE FRONT SHOWS THE VISUAL PRESENTATION (E.G.
TELEMETRY, GALLERY). THE BACK SHOWS THE RAW FCr DATABASE VIEW OR CONFIGURATION.**

⇒⇒□ **⇒⇒□ ⇒⇒□ THE FLIP IS A PRESENTATION OF ONE PANEL, NOT A NAVIGATION BETWEEN TWO
PAGES.** ⇒⇒□ The FRONT is the visual face. The BACK is the raw FCr view or configuration
**of the same data**. ⇒⇒□ ⇒⇒□ **⇒⇒□ THE FRONT AND THE BACK ARE TWO VIEWS OF ONE SOURCE OF
TRUTH** — flipping must never change what is being shown, only how it is shown.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE FRONT/BACK PAIR IS AN EXPLICIT CONTRACT, NOT A CSS ACCIDENT.**
⇒⇒□ A Desk Panel MUST have a **front** and MAY have a **back**. ⇒⇒□ A Desk Panel with no
back MUST NOT present a flip affordance at all — a flip gesture that does nothing is a
broken control. ⇒⇒□ ⇒⇒□ **⇒⇒□ THE FLIP MUST BE REVERSIBLE AND MUST NOT DESTROY THE
OPERATOR'S SCROLL POSITION OR THE DESK ARRANGEMENT.**

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE RAW BACK IS THE FCr DATABASE VIEW — THE REAL ONE.** MEASURED:
`src/modules/dashboard/src/dashboard/widgets/fc-face.tsx` already renders the FreshCards
`ListView` (`freshcards/ui`) over the `FcDatabase` shape that
`freshcards-view.tsx` builds (`databaseOf()`, `itemOfRecord()`, `propertiesOfType()`). ⇒⇒□
⇒⇒□ **⇒⇒□ THE BACK IS THAT VIEW** — the FCr list of the panel's own records — and the
configuration back is the panel's own configuration, shown in the same raw form.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE 3D TRANSFORM IS THE MECHANISM; THE FLIP IS THE MEANING.** MEASURED:
the FreshCards package ships no flip component of its own — a sweep of
`node_modules/freshcards/dist/` for `preserve-3d|rotateY` finds only Mantine's own
`transform|translate|scale|rotate|perspective` will-change heuristic, not a card flip.
⇒⇒□ ⇒⇒□ **⇒⇒□ THE DESK THEREFORE OWNS THE FLIP MECHANIC** (`perspective` on the Desk
Panel, `transform-style: preserve-3d` on the faces, `rotateY` on the flip) — **and the
MECHANIC IS NOT THE REQUIREMENT.** ⇒⇒□ **⇒⇒□ THE LAW IS THAT BOTH FACES EXIST AND ARE
REACHABLE; A FLIP IMPLEMENTED WITHOUT A 3D TRANSFORM IS STILL A FLIP, AND A FLIP
IMPLEMENTED WITHOUT A BACK IS NOT.**

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE "TELEMETRY, GALLERY" EXAMPLES ARE THE PRODUCT'S OWN, AND THE
FRONT MUST USE THE REAL COMPONENT.** MEASURED: `MediaGalleryWidget.tsx` and
`DatabaseTableWidget.tsx` are the dashboard's gallery and database widgets, and FVC 1379
replaced their hand-written markup with the real FreshCards faces (§92.6). ⇒⇒□ ⇒⇒□
**⇒⇒□ THE FRONT IS THE FCr COMPONENT, RENDERED.**

### 92.5 The Data Must Come From the Real FCr Components

**RULE 5 — THE PANELS MUST USE THE ACTUAL FCr COMPONENTS, NOT CUSTOM INTERNAL WIDGETS.**

⇒⇒□ **⇒⇒□ ⇒⇒□ THIS RULE IS NOT ASPIRATIONAL — IT IS A CORRECTION OF A MEASURED DEFECT.**
MEASURED (FVC 1379's own header, `fc-face.tsx:8-24`): *"The dashboard's three live cards
rendered hand-written markup: a `<table>` for the database, an `<img>` grid for the media, a
`<div>` list for the post types. FreshCards ships the real faces for all three — `ListView`,
`GalleryView`, and the `Card` / `Badge` / `EmptyState` / `Skeleton` primitives — and the
FreshCards package is already a dependency of this module."* ⇒⇒□ ⇒⇒□ **⇒⇒□ AND THE
HAND-WRITTEN FACES WERE NOT JUST UGLY — THEY WERE DEAD CODE.** MEASURED: *"The only
consumer of the FreshCards views was `AppDataWidget` … no card in the live tree declares
that widget, so the whole FreshCards view layer was dead code and the bundler tree-shook it
out of the shipped bundle. Measured on the live build: `ListView` and `GalleryView` occur
ZERO times in `dist/assets/main-*.js`."* ⇒⇒□ **⇒⇒□ ⇒⇒□ A DASHBOARD THAT DRAWS ITS OWN
MARKUP IS A DASHBOARD THAT SHIPS NO FRESHCARDS AT ALL.**

⇒⇒□ **⇒⇒□ ⇒⇒□ THE COMPONENTS ARE CONFIRMED PRESENT AND REAL.** MEASURED in
`node_modules/freshcards` (v2.25.0): the package exports `./ui` and `./mantine`; and
`Card`, `ListView`, `GalleryView`, `Badge`, `EmptyState` and `Skeleton` all occur in the
shipped `dist` bundles.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE PROVIDER RULE IS PART OF THE RULE, NOT A FOOTNOTE.** MEASURED
(`fc-face.tsx:29-39`): *"Every Mantine import in this repository comes from
`freshcards/mantine`, never from `@mantine/core`. Mixing them gives two Mantine instances,
two React contexts, and a `MantineProvider was not found in component tree` throw."* ⇒⇒□
⇒⇒□ **⇒⇒□ A DESK PANEL THAT IMPORTS FROM `@mantine/core` IS A DESK PANEL THAT CRASHES THE
APP.** ⇒⇒□ And the FCr primitives paint from `--fc-*` custom properties, which the npm
package does not ship — so the token scope comes from the module's own `fc-tokens.ts`.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND "NOT CUSTOM INTERNAL WIDGETS" HAS A MEANINGFUL EDGE: A DESK PANEL MUST
NOT RE-DRAW WHAT FCr ALREADY SHIPS.** ⇒⇒□ ⇒⇒□ The Desk Panel is a **composition of FCr
components and the product's own layout**, not a new widget system that happens to live
near the FCr one. ⇒⇒□ ⇒⇒□ **⇒⇒□ A NEW PRIMITIVE IS ADDED ONLY WHEN FCr HAS NO SUCH
PRIMITIVE, AND THE REASON IS WRITTEN DOWN WHERE THE PRIMITIVE IS ADDED.**

### 92.6 The FreshCards Face Layer Is the Floor, Not the Ceiling

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE FACE LAYER IS THE MEASURED BASELINE THE DESK BUILDS ON.** MEASURED:
FVC 1379 landed `src/modules/dashboard/src/dashboard/widgets/fc-face.tsx` with
`FcSurface` (the `--fc-*` token scope), `FcCard`, and the FCr `ListView` / `GalleryView`
faces over the `FcDatabase` / `FcDatabaseItem` shapes from `freshcards-view.tsx`. ⇒⇒□ ⇒⇒□
**⇒⇒□ THE DESK'S FRONT IS BUILT ON THAT LAYER**, so the Desk does not re-derive the FCr
data shape, the token scope, or the provider.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE DESK'S OWN LAYOUT BOX IS NOT THE FCr `Card`.** MEASURED
(`DashboardGrid.tsx:325-330`): *"THE VISUAL CHROME IS FRESHCARDS' CARD, NOT THIS ELEMENT.
The section is the layout box and the gesture surface; the face inside it is the
FreshCards `Card` primitive, which carries the radius, the border, the shadow and the
surface colour."* ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ THE DESK PANEL KEEPS THAT SEPARATION** — the Desk
Panel owns the box, the placement, the flip and the gesture; the FCr `Card` owns the
chrome. ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ A DESK PANEL THAT STYLES ITS OWN BORDER, SHADOW, OR RADIUS IS
DOUBLING THE FRESHCARDS `Card` — AND THE FCr PRIMITIVES ARE WHAT THE OPERATOR HAS ALREADY
CHOSEN THE LOOK OF.**

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE BACK IS THE SAME DATA, READ RAW.** ⇒⇒□ The FRONT is the FCr face
component; the BACK is the FCr **view** — `ListView` over the panel's own records, or the
panel's configuration in raw form. ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ THE FRONT AND THE BACK MUST AGREE
— a flip that changes the numbers is a bug, not a feature.**

### 92.7 What This Part Supersedes, and What It Does Not

⇒⇒□ **⇒⇒□ ⇒⇒□ THIS PART SUPERSEDES PART 24's GRID ARITHMETIC, AND THE SUPERSESSION IS
EXPLICIT.** MEASURED: Part 24 §24.1 describes `src/host/dashboard/dashboard-layout.ts` as
owning *"the grid arithmetic: 12 columns, `MIN_CARD_WIDTH` 1, `MAX_CARD_WIDTH` 12,
`DEFAULT_CARD_HEIGHT` 180, `MIN_CARD_HEIGHT` 40, plus explicit `order` and `width` on each
card so an arrangement survives a reload"*, and Part 24 §24.1 names
`src/host/dashboard/DashboardCanvas.tsx` and `src/host/dashboard/DashboardGrid.tsx`. ⇒⇒□
⇒⇒□ **⇒⇒□ AND THE PATHS IN PART 24 NO LONGER EXIST.** MEASURED: `src/host/dashboard/` is
**ABSENT** from the repository — the dashboard now lives under
`src/modules/dashboard/src/dashboard/`, with the same file names (`DashboardCanvas.tsx`,
`DashboardGrid.tsx`, `dashboard-layout.ts`, `DashboardPanel.tsx`, `DashboardPanel.css`).
⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ PART 24 IS NOT DELETED AND ITS SCOPE LAW IS NOT TOUCHED** —
Parts 24.2, 24.3 and 24.4 govern **which data the Dashboard shows** (the project boundary,
the App scope, the scope vocabulary), and **none of that is affected by how the panels are
arranged.** ⇒⇒□ **⇒⇒□ ⇒⇒□ WHAT IS SUPERSEDED IS PART 24 §24.1's GRID ARITHMETIC ONLY**,
because the Desk is not a grid.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE EXISTING TEST IS STILL A GUARD, NOT A MASKS.** MEASURED: Part 24
§24.3 names `src/host/dashboard/__tests__/fvc1065-project-boundary.test.ts` (11 tests) as the
guard for `filterCardsByProject`, and it asserts that with no project selected the result is
ONLY home nodes and EXCLUDES every project node. ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ THAT TEST NOW LIVES AT
`src/modules/dashboard/src/dashboard/__tests__/fvc1065-project-boundary.test.ts`** and it
KEEPS its meaning: **the Desk arranges panels; it does not change which data a panel may
see.** ⇒⇒□ **⇒⇒□ ⇒⇒□ A DESK THAT SHOWS ANOTHER PROJECT'S CARDS IS WRONG NO MATTER HOW
BEAUTIFULLY IT IS ARRANGED.**

⇒⇒□ **⇒⇒□ ⇒⇒□ AND PART 23's SCOPES SURVIVE.** MEASURED: Part 23 requires three scopes
(Build Data / App Data / User Data) with a scope toggle, and Part 27 adds a fourth
(`Roadmap`). ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ THE SCOPE TOGLE IS NOT THE DESK, AND THE DESK IS NOT THE
SCOPE.** ⇒⇒□ A Desk Panel declares which scope it belongs to, and the toggle changes which
Desk Panels are on the Desk. ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ PART 23.3's "Switching the scope changes
the widgets rendered on the grid" IS WRITTEN IN THE GRID'S LANGUAGE, AND THE DESK REPLACES
THE WORD "grid" — the widgets change, and the arrangement rule of THIS PART applies to
them.** ⇒⇒□ **⇒⇒□ ⇒⇒□ PART 23's THREE SCOPES AND PART 24.4's SCOPE VOCABULARY ARE
CARRIED FORWARD UNCHANGED**, and the new Desk Panel vocabulary is **ADDITIVE**.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE DASHBOARD IS NOT THE SHOWCASE, AND THE SHOWCASE IS NOT THE DESK.**
MEASURED: Part 89 overrode Part 85 §85.1 — the root route is the permanent VC Shell and the
Showcase lives at `/showcase`; and Part 90 moved the sub-project list out of the canvas grid
into the Project Picker dropdown, because *"the grid is `repeat(auto-fill, minmax(220px,
1fr))`, so a project with four children takes a cell FOUR TIMES THE HEIGHT of its
neighbours."* ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ THE GRID HAS ALREADY COST THIS PRODUCT ONE LAW, AND
THIS PART IS THE SECOND TIME THE GRID'S GEOMETRY IS THE PROBLEM.** ⇒⇒□ **⇒⇒□ ⇒⇒□ A
CUSTOMER FACING SHOWCASE IS NOT A DESK** — the Desk is the operator's working surface.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE DASHBOARD IS NOT THE ROOT ROUTE.** MEASURED: Part 91's law is that
the bare `/` is the Shell with NO PROJECT LOADED, and `isMasterDashboardPath()` decides
between the master dashboard and the Shell. ⇒⇒□ ⇒⇒□ **⇒⇒□ THE DESK LIVES ON THE DASHBOARD
ROUTE** — wherever the Dashboard renders today — and it does not change which route is the
Shell's.

### 92.8 What Is Measured, Not Law

⇒⇒□ **THE DESK CODE HAS LANDED — AND IT LANDED AGAINST THIS PART, NOT BEFORE IT.** MEASURED:
`origin/main` carries FVC 1385's three commits (`4cb62985`, `4917073f`, `8d674946`), and the
Desk is real: `src/modules/dashboard/src/dashboard/desk-panel.tsx` (469 lines) and
`desk-state.ts` (212 lines), with `DashboardGrid.tsx` rewritten (+260/−118). ⇒⇒□ **⇒⇒□ THE
BRANCHES STILL EXIST ON `origin`** — `fvc-1385-desk-panels`, `fvc-1385-desk-canvas` and
`fvc-1385-pointer-events` — so the implementation is MERGED, not merely proposed. ⇒⇒□ **⇒⇒□
THIS SECTION WAS WRITTEN WHEN THE DESK DID NOT EXIST** ("a sweep of `src/` for `\bdesk\b`
returns ZERO hits"), and it is CORRECTED HERE rather than left to mislead the next reader.

⇒⇒□ **RULE 2 — THE MASONRY IS BUILT, AND IT IS GATED.** MEASURED: `DashboardGrid.tsx:308`
is `alignItems: 'flex-start'` (not `'stretch'`), `:363` is `height: 'auto'` (not `'100%'`),
`:300` declares `data-layout="masonry"`, and the `grid-column` span is gone. ⇒⇒□ **⇒⇒□ AND
THE GATE EXISTS AND HAS BEEN SEEN TO GO RED**: `fvc1019-dashboard.test.tsx:135` asserts the
masonry and sizes every panel to its own content. ⇒⇒□ **⇒⇒□ ⇒⇒□ MEASURED NEGATIVE
CONTROL:** mutating `alignItems: 'flex-start'` → `'stretch'` and `height: 'auto'` → `'100%'`
turned that test **RED (1 failed | 14 passed)**; restoring the file turned it **GREEN (15/15)**.
⇒⇒□ **⇒⇒□ ⇒⇒□ §92.2's STOP CONDITION IS THEREFORE CLOSED — NOT BY A PROMISE, BUT BY A GATE
THAT WAS MEASURED FAILING.**

⇒⇒□ **RULE 4 — THE 3D CARD IS BUILT.** MEASURED: `desk-panel.tsx:116` is `perspective:
'1400px'`, `:122` is `transformStyle: 'preserve-3d'`, `:124` is `transform: rotateY(180deg)`
when flipped, and `:218` carries the back face's own `rotateY(180deg)`. ⇒⇒□ **⇒⇒□ AND THE
BACK IS THE DATA, NOT A PICTURE OF IT**: the back renders FreshCards' own `ListView` over real
records, and FVC 1385's follow-up commit (`8d674946`) fixed the back face swallowing every
click on the front — a defect that only appears once a back EXISTS.

⇒⇒□ **RULE 3 — PIN, LIBRARY, ADD AND REMOVE ARE BUILT.** MEASURED: `desk-state.ts:56`
exports `DESK_LIBRARY` (the panel library), `:121` exports `EMPTY_DESK` with
`{ added, removed, pinned, order }`, and `desk-panel.tsx:115` carries `data-pinned` with a
PIN/UNPIN action at `:157-158`.

⇒⇒□ **RULE 5 — THE REAL FCr COMPONENTS ARE IN THE SHIPPED BUNDLE.** MEASURED: `fc-face.tsx:45`
imports `{ Badge, Card, EmptyState, GalleryView, ListView, Skeleton }` from `freshcards/ui`
and `:44` imports `MantineProvider` from `freshcards/mantine`. ⇒⇒□ **⇒⇒□ BUT A STRING MATCH ON
THE BUNDLE IS THE WRONG TEST** — the identifiers are minified, and FVC 1379's own header
recorded `ListView`/`GalleryView` at "ZERO times" in `dist/assets/main-*.js` while the
components were present. ⇒⇒□ **⇒⇒□ THE RIGHT TEST IS FRESHCARDS' OWN MARKERS**: the built
bundle contains `data-fc-gallery-card` (FreshCards' `GalleryView` card marker),
`data-fc-card`, `data-fc-card-add` and `data-fc-add-item-mobile`. ⇒⇒□ **⇒⇒□ ⇒⇒□ THAT IS THE
PROOF THAT A DASHBOARD WHICH DRAWS ITS OWN MARKUP SHIPS NO FRESHCARDS AT ALL — AND THAT THE
DESK DOES NOT.**

⇒⇒□ **THE ENFORCEMENT IS PARTIAL, AND THE REMAINING GAP IS NAMED.** MEASURED: CI runs
`npx vitest run app-vp/` — **it does NOT run `src/modules/dashboard/`**. ⇒⇒□ **⇒⇒□ ⇒⇒□ SO
THE MASONRY GATE IS NOT YET A CI GATE**: it is a test that passes, and it was proven to go
RED, but nothing in the workflow runs it. ⇒⇒□ **⇒⇒□ §92.3's AND §92.4's STOP CONDITIONS
REMAIN OPEN** — there is no pin assertion, no library assertion and no flip assertion
anywhere in `scripts/` or `tools/`, and the masonry test does not cover them. ⇒⇒□ **⇒⇒□ AND
A LATER PART MUST CLOSE BOTH HALVES: wire the dashboard suite into CI, AND add the pin,
library and flip assertions.**

⇒⇒□ **THE OPERATOR-SIZED HEIGHT IS NOT CARRIED INTO THE STAGGERED ARRANGEMENT.** MEASURED:
`desk-state.ts` persists `{ added, removed, pinned, order }` and **no width and no height**,
and `DeskPanel` (`:96-106`) carries `id`, `kind`, `title`, `widget`, `pinned` and `added` —
**not** a width or a height. ⇒⇒□ **⇒⇒□ ⇒⇒□ SO THE EXPLICIT `height` PROPERTY AND ITS CLAMP
(`MIN_CARD_HEIGHT` 40, `DEFAULT_CARD_HEIGHT` 180) STILL EXIST ONLY INSIDE THE GRID**, and a
panel added from the library has NO operator-sized height at all. ⇒⇒□ **⇒⇒□ §92.2's
OPERATOR-SIZED HEIGHT REMAINS OPEN**, even though the masonry itself is now built.

⇒⇒□ **THE PERSISTENCE CAVEAT IS STILL LIVE, AND IT IS NOW LOAD-BEARING.** MEASURED: §92.3's
carried-forward rule — that every Desk Panel persistence must be saved locally — is exactly
what `desk-state.ts` does: `deskKey()` builds `fv-desk:<pageKey>` and `saveComposition()`
writes it locally, because Part 24 §24.5 records that the graph write succeeds but
`properties` does not survive the wire. ⇒⇒□ **⇒⇒□ THE DESK IS CORRECT HERE, AND THE REASON
IS WORTH NAMING**: a Desk that persisted to the graph alone would rearrange itself on the
next load.

⇒⇒□ **THE DASHBOARD MODULE'S OWN PATH IS NEW SINCE PART 24, AND ANY FUTURE PART THAT
NAMES A DASHBOARD PATH MUST MEASURE IT.** MEASURED: the module is
`src/modules/dashboard/` with `module.json`, a `recipe-book/`, and **42** files under `src/`
(the pre-Desk count was 48, because FVC 1383 deleted the dead React panel system and FVC
1385 replaced the grid), and `src/host/dashboard/` is gone.

⇒⇒□ **THE SPEC VERSION AND PART NUMBER ARE INDEPENDENT COUNTERS.** MEASURED: the version
is derived from the highest `v3.N.0` marker (**40** → **v3.41**) and the Part from the
highest `## Part N` heading (**91** → **92**). ⇒⇒□ **⇒⇒□ THE DISPATCH'S "v3.43.0" WAS NOT
AVAILABLE AND WAS NOT USED**, and the two counters are recorded separately rather than
silently reconciled. ⇒⇒□ **⇒⇒□ THE SPEC HAS SINCE MOVED ON: FVC 1383 TOOK v3.42.0** (Part
78, the PM2 ratification), so this Part's v3.41.0 is now the version this Part LANDED IN —
and the Part number and the version that carried it are still two different facts.


## Part 93 — Test Scoping: the Full Suite Is a Release Activity, Not a Dispatch Activity

**THE FULL TEST SUITE IS NEVER RUN ON A STANDARD DISPATCH. IT IS A RELEASE ACTIVITY AND NOTHING ELSE. A DISPATCH RUNS ONLY THE TESTS THAT COVER THE FILES IT CHANGED, AND IT PROVES NO REGRESSION BY A BEFORE/AFTER COMPARISON OVER THAT SAME SCOPED SET — NOT OVER THE WHOLE TREE. THE COST OF IGNORING THIS IS TWENTY-TWO MINUTES OF WALL-CLOCK PER DISPATCH, A TOKEN BURN THAT SCALES WITH EVERY TURN, AND A LIVE OOM RISK ON A TWO-CORE EXECUTION BOX.**

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE PART NUMBER IS DERIVED, NOT ASSUMED.** MEASURED: the file's highest
`## Part N` heading was **92** (`## Part 92 — The Dashboard Desk`), so the next free number is
**93**; and the highest `v3.N.0` marker was **42**, so the next free version is **v3.43**. ⇒⇒□
**⇒⇒□ THE VERSION AND THE PART ARE INDEPENDENT COUNTERS** (Part 85 §85.7). ⇒⇒□ **⇒⇒□ THE
DISPATCH SAID "e.g., Part 93" — THAT NUMBER IS CORRECT AND WAS USED**, and the version it did
not name was derived the same way the last Part derived its own.

⇒⇒□ **⇒⇒□ AND THE RULE ALREADY EXISTS IN PART — AND THIS PART IS NOT THE ADDITION.** MEASURED:
Rule 1 §5.5 is titled **"5.5. TURNS — TESTS FOLLOW THE CHANGE  [AGENT]"** and reads: *"A TURN
is one unit of work inside a dispatch: a fix, a revert, a new test, a change to one module."*
and *"WHAT A TURN TESTS: A turn changes file X. The turn runs the tests that cover X, before
the change and after."* ⇒⇒□ **⇒⇒□ §5.5 IS NOT REPEATED HERE, AND IT IS NOT SUPERSEDED.** This
Part closes three gaps §5.5 leaves open — and it is the third gap that matters most: §5.5 says
what a turn runs, but it never says what is FORBIDDEN, never says who may authorise the
forbidden thing, and never says why the cost is worth prohibiting.

### PREMISE CORRECTION 1 — THE DISPATCH'S RULE 3 WAS CIRCULAR, AND IT WAS CORRECTED

The dispatch proposed: *"To prove no regressions, a dispatch MUST run a baseline comparison of
the failing files only, not the whole tree."*

⇒⇒□ **⇒⇒□ THAT IS CIRCULAR, AND THE CIRCULARITY PUSHES THE AGENT BACK INTO THE FORBIDDEN
RUN.** MEASURED LOGIC: to compare the *failing files* you must first have a run that ESTABLISHES
WHICH FILES FAIL. If the run that establishes them is the whole-tree run, then rule 3 demands
precisely what rule 1 forbids. ⇒⇒□ **⇒⇒□ AN AGENT THAT CANNOT SATISFY A RULE LITERALLY SATISFIES
IT "IN SPIRIT"** — it runs the full suite once to get a failure list, and then claims compliance.
⇒⇒□ **⇒⇒□ AND THE RULE'S OWN WORDING ROUTED THE REAL REGRESSION OUT OF SCOPE.** If the compared
set is defined as "the baseline's failing files", then a file that was **PASSING** in the
baseline and **FAILS** after the change is not in the compared set at all — it is compared
against nothing. ⇒⇒□ **⇒⇒□ THE NEWLY-FAILING FILE IS THE INTERESTING ONE, AND THE RULE AS
WRITTEN EXCLUDED IT BY CONSTRUCTION.**

⇒⇒□ **⇒⇒□ SO RULE 3 IS CORRECTED HERE, AND THE CORRECTION IS THE DELTA THAT MATTERS.** The
compared set is **the scoped set — a function of the diff, knowable in advance** — not a
function of global failures. The baseline is captured against the **pre-change tree**, and the
comparison is over the **whole scoped set**, not over its failing subset.

⇒⇒□ **⇒⇒□ AND THE COMPARISON MUST INCLUDE COUNTS, NOT ONLY THE FAILING SET.** MEASURED: FVC
1292 measured **84 failed files / 70 failed tests / 1547 passed** on a CLEAN checkout; FVC 1316
measured **82 failed files / 62 failed tests / 1728 passed**. ⇒⇒□ **⇒⇒□ THE FILE COUNT AND THE
TEST COUNT ARE NOT THE SAME QUANTITY** — 84 files against 70 tests means at least one file
carried multiple failures. ⇒⇒□ **⇒⇒□ A FAILING-SET-ONLY COMPARISON CANNOT SEE A CHANGE IN
PER-FILE FAILURE MULTIPLICITY, AND A COUNT-ONLY COMPARISON CANNOT SEE A NEWLY-FAILING FILE.**
Compare the failing-file set AND the per-file failure counts AND the passing total.

### PREMISE CORRECTION 2 — "RELEASES ONLY" HAD NO NAMED AUTHORITY, SO IT WAS SELF-CERTIFYING

The dispatch proposed: *"The full test suite is for releases only."*

⇒⇒□ **⇒⇒□ NOBODY DECLARES A RELEASE IN THE GIVEN DOCTRINE.** ⇒⇒□ **⇒⇒□ AND A RULE WHOSE
EXCEPTION IS SELF-CERTIFYING IS A RULE THAT DOES NOT BIND.** If the dispatch does not name a
release, the agent decides for itself — and "this change is broad / touches shared modules /
feels release-worthy" is exactly the rationalisation an agent under time pressure will reach,
after which it runs the 657-second suite twice and claims the rule did not apply.

⇒⇒□ **⇒⇒□ SO A RELEASE IS DECLARED BY THE REQUESTER ONLY, AND NEVER BY THE AGENT.** The
release exception, as corrected:

> **A release means ONLY: (a) a dispatch explicitly named a release by the requesting user, or
> (b) an explicit instruction in the dispatch text to run the full suite. A dispatch is NOT a
> release merely because it is broad, risky, touches shared modules, or the agent judges it
> important. If the dispatch does not name a release, the scoped rules apply. The agent MUST NOT
> self-authorise a full-suite run, and MUST NOT ask for a release to be declared as a workaround
> for a test failure.**

⇒⇒□ **⇒⇒□ AND ANY FULL-SUITE RUN MUST BE RECORDED WITH THE REASON IT WAS AUTHORISED**, so that
"I decided it was a release" leaves a trace rather than a silent 22 minutes.

### PREMISE CORRECTION 3 — RULE 2 WAS §5.5 RESTATED, AND THE BOUNDARY IS NOW STATED

⇒⇒□ **⇒⇒□ §5.5 ALREADY GOVERNS THE TURN.** This Part governs the **dispatch aggregate**. The
two are not the same unit, and without the boundary stated, a reader cannot tell whether a
dispatch runs the union of its turn scopes **once** or whether each turn re-runs its own scope —
which is itself a wasted-time path.

> **§5.5 governs the unit of work: one turn, one file's scoped tests, before and after. This
> Part governs the dispatch aggregate: the dispatch runs the UNION of the turn scopes, ONCE, at
> dispatch level — in addition to the per-turn scopes §5.5 already requires. A dispatch MUST NOT
> run the full test suite.**

⇒⇒□ **⇒⇒□ AND SCOPE MUST BE DERIVED FROM ACTUAL COVERAGE, NOT FROM A FILENAME GUESS.** ⇒⇒□
**⇒⇒□ THE MEASURED PRECEDENT IS FVC 1292's GATE, WHICH READ THE WRONG BLOCK AND PASSED
ANYWAY** — its parser hit a `}` inside a CSS comment, read the wrong block, and "PASSED against
the very bug it was written for". ⇒⇒□ **⇒⇒□ A SCOPE GUESSED FROM A FILENAME IS THE SAME
SPECIES OF ERROR.** The scope must come from the changed file's real covering tests, and the
report must name the scope and the mapping rule used.

### THE THREE RULES, AS CORRECTED

**RULE 1 — NEVER RUN THE FULL TEST SUITE ON A STANDARD DISPATCH.** The full suite is for
releases only, and a release is declared by the requester, never by the agent.

**RULE 2 — A DISPATCH MUST RUN ONLY THE SCOPED TESTS THAT COVER THE FILES IT CHANGED.** At
dispatch level: the union of the turn scopes, run once. Everything outside that map is not
evidence, it is latency.

**RULE 3 — TO PROVE NO REGRESSIONS, A DISPATCH MUST RUN THE SCOPED SET TWICE: ONCE AGAINST THE
PRE-CHANGE TREE AND ONCE AGAINST THE POST-CHANGE TREE, AND COMPARE THE TWO RESULT SETS.** The
compared set is the scoped set — a function of the diff, not of global failures. It MUST NOT be
expanded to the whole tree, and the full-suite run is not available as the baseline source.

⇒⇒□ **⇒⇒□ AND IF A SCOPED BASELINE CANNOT BE OBTAINED, THE REGRESSION CLAIM IS UNPROVEN** — it
is reported as unproven, never silently skipped and never satisfied by a full-suite run.

### THE 25-MINUTE PENALTY

MEASURED: the F-lane working-notes record states — *"The lane has also been slow because the
test suite is 657 seconds on a 2-core box and every dispatch runs it twice. F 292 measured it
and could not fix it by configuration. The rule from it — per-turn testing — is now in Rule 1
§5.5."*

⇒⇒□ 657 seconds per run, twice per dispatch, is roughly **22 minutes of wall-clock per
dispatch** ⇒⇒⇒ on a **2-CPU / 3072 MB RAM / 0 MB swap** execution box.

⇒⇒□ **⇒⇒□ AND F 292 COULD NOT FIX IT BY CONFIGURATION — THE PREMISE WAS CHECKED AND
REJECTED.** There is no flag that makes a 657-second suite into a 30-second suite on this
hardware. ⇒⇒□ **⇒⇒□ SO THE ONLY LEVER LEFT IS *NOT RUNNING IT*.** ⇒⇒□ **⇒⇒□ AND THE TOKEN COST
RIDES ON TOP OF THE WALL-CLOCK COST**: a full suite is thousands of result lines the agent must
read, reason about, and hold in context, most of which say nothing about the dispatch's change.
⇒⇒□ **⇒⇒□ FULL-SUITE OUTPUT IS TOKEN SPEND THAT BUYS NO DISPATCH-RELEVANT INFORMATION**, because
the information the dispatch needs is in the scoped set, not in the 3372 that passed.

⇒⇒□ **⇒⇒□ AND THE FULL RUN BOUGHT NO NEW INFORMATION IN THE ONE REPORT THAT MEASURED IT.**
MEASURED: F 506 (id 12) ran a full suite and reported **"Full suite 46 failed / 3372 passed"**,
while separately reporting TypeScript errors **"348 errors before and after"**. ⇒⇒□ **⇒⇒□ 46
failures and 348 TypeScript errors, before and after, IS THE BASELINE** — the repo was already
broken ⇒⇒□ the full run cost 22 minutes and surfaced **no new information about the dispatch's
change**.

### THE 2-CPU OOM HAZARD

MEASURED: FVC 1316 found the repo's suite had to be **"run in 6 chunks: a full vitest run died
twice without a summary (the 3GB sandbox OOMs)."**

⇒⇒□ The execution box is **3072 MB total RAM, 0 MB swap** ⇒⇒□ a full vitest run has been
observed to **die twice without producing a summary** ⇒⇒□ the suite is not merely slow, it is
**structurally unable to complete in one piece on this hardware**.

⇒⇒□ **⇒⇒□ THIS IS WHY RULE 1 IS A SAFETY RULE AND NOT ONLY AN EFFICIENCY RULE.** A dispatch
that runs the full suite does not reliably get an answer; it gets a **crash**. ⇒⇒□ **⇒⇒□ AND
THE CRASH BURNS THE SAME 22 MINUTES AND RETURNS NOTHING**, and a dispatch that crashed mid-suite
has to be retried, which burns it again. ⇒⇒□ **⇒⇒□ AND TWO CPUs MEAN THE CONCURRENT WORK IN A
DISPATCH IS COMPETING WITH THE SUITE FOR THE SAME CORES** — which is how a crash becomes a crash
of the *dispatch*, not just of the test process.

⇒⇒□ **⇒⇒□ AND A SCOPED RUN THAT DIES WITHOUT A SUMMARY IS NOT A PASS.** MEASURED: FVC 1316 had
to run the suite in **6 chunks** because a full run OOMs. ⇒⇒□ **⇒⇒□ A LARGE SCOPED RUN MUST BE
CHUNKED OR MEMORY-LIMITED, AND A MISSING SUMMARY IS A NON-RESULT TO REPORT** — never reported as
"scoped tests passed".

### WHAT A REGRESSION PROOF LOOKS LIKE

MEASURED: the repo's pre-existing failing test files are a known, stable baseline. FVC 1292
measured **84 failed files / 70 failed / 1547 passed** on a **CLEAN checkout**. FVC 1316
measured **82 failed files / 62 failed tests / 1728 passed** before and after a change — and the
failing file SETS were **byte-identical**, not merely the same counts.

⇒⇒□ **⇒⇒□ THE PROOF IS A BEFORE/AFTER COMPARISON OVER THE SCOPED SET, AND THE BASELINE IS
CAPTURED AGAINST THE PRE-CHANGE TREE** — a clean HEAD or a worktree at HEAD — because a
baseline captured after the edit compares post-change to post-change and reports clean.

⇒⇒□ **⇒⇒□ COMPARE SETS, NOT JUST COUNTS.** Counts are lossy in both directions. A count can go
DOWN while the change is bad — if the change accidentally skips three failing files, the count
drops and the count-based gate goes green on a broken dispatch. A count can stay FLAT while the
change is bad — the dispatch breaks failing file A and fixes failing file B, count unchanged, one
regression invisible. ⇒⇒□ **⇒⇒□ A SET COMPARISON CATCHES BOTH** — A is in the after-set and not
in the before-set, and it is a regression regardless of what happened to B.

⇒⇒□ **⇒⇒□ AND THE COMPARISON MUST BE SEEN RED.** The scoped gate must actually be **observed
failing before the change and passing after it**. ⇒⇒□ **⇒⇒□ A GATE THAT NEVER WENT RED PROVES
NOTHING** — it may have been green because it does not cover the changed files. MEASURED: FVC
1316 added 14 regression tests, **"each proven RED by a negative control."** ⇒⇒□ **⇒⇒□ AND THE
COMPARISON HARNESS ITSELF IS A GATE** — FVC 1292's gate parsed source with a naive `indexOf`,
hit a `}` inside a CSS comment, read the wrong block, and "PASSED against the very bug it was
written for". ⇒⇒□ **⇒⇒□ SO A COMPARISON THAT HAS NEVER BEEN DEMONSTRATED TO DETECT AN INJECTED
REGRESSION MUST NOT BE CITED AS REGRESSION PROOF.**

⇒⇒□ **⇒⇒□ AND THE COST OF SCOPING MUST BE STATED, NOT IMPLIED AWAY.** A scoped comparison
proves nothing about code the scope did not include. If the change breaks a **consumer** of the
changed files, the scoped comparison is clean and the regression lives outside the compared set.
⇒⇒□ **⇒⇒□ THAT IS THE GENUINE COST OF THIS RULE, AND IT IS NAMED HERE RATHER THAN HIDDEN.**

⇒⇒□ **⇒⇒□ AND A SCOPE THAT IS "THE WHOLE TREE" MUST BE REPORTED AS SUCH.** Scope is a function
of the diff, and a wide diff makes "scoped" ≈ "everything" — reproducing the 22-minute cost
under a compliant label. ⇒⇒□ **⇒⇒□ THE DISPATCH REPORT MUST STATE THE NUMBER OF SCOPED TEST
FILES AND WHETHER THE SCOPED SET WAS TRUNCATED**, so the trade-off is auditable rather than
hidden inside the word "scoped".

⇒⇒□ **⇒⇒□ AND WHAT WAS NOT RUN MUST BE RECORDED.** A dispatch that runs the scoped set and
silently skips the rest produces a report that reads like "tests passed." The report must state
the scoped set, the before/after comparison result, and explicitly **what was not run**.

### THE RELEASE EXCEPTION

⇒⇒□ The full suite runs when the deliverable is a **release**, and a release is declared by the
requester. At a release boundary the whole tree is the unit of work, so the whole tree is the
thing that must be verified; that is a different question from "did this dispatch's change
regress anything", and it deserves a different cost.

⇒⇒□ **⇒⇒□ AND A RELEASE RUN IS THE ONE TIME THE SIX-CHUNK WORKAROUND IS MANDATORY**, because a
single full vitest run OOMs on a 3 GB box (MEASURED, FVC 1316).

⇒⇒□ **⇒⇒□ THE DISTINCTION IS *RELEASE vs. DISPATCH*, NOT *THOROUGH vs. LAZY*** — and it is the
same distinction Rule 4 draws for autonomy.

### PRECEDENCE — PART 68 SURVIVES, AND IT GOES FIRST

⇒⇒□ **⇒⇒□ PART 68 (The Test Loop Trap) IS NOT SUPERSEDED BY THIS PART, AND IT GOES FIRST.**
Part 93 is the higher number, and a reader will otherwise assume precedence by number. ⇒⇒□
**⇒⇒□ MEASURED: PART 68 carries the classification rule — classify first, and a self-verifying
script is its own proof, so it gets no hand-written negative control.** ⇒⇒□ **⇒⇒□ SO A
SELF-VERIFYING SCRIPT IS EXEMPT FROM THE BASELINE COMPARISON**, and the classification step is
performed **BEFORE** any baseline run. ⇒⇒□ **⇒⇒□ AND A BASELINE COMPARISON IS A BOUNDED
PRE/POST PAIR OVER THE SCOPED SET — IT IS NOT A MECHANISM FOR CHASING A FAILURE**, and it MUST
NOT be repeated, expanded, or run in addition to the scoped pair to hunt for more information.

⇒⇒□ **⇒⇒□ AND A FAILING SCOPED TEST IS GOVERNED BY RULE 4 §2's EXISTING FAILURE HANDLING** —
*"If a test fails and you cannot determine whether it is a regression or a pre-existing contract
within 15 minutes, STOP. Report the failure."* ⇒⇒□ **⇒⇒□ CLASSIFICATION PRECEDES COMPARISON.**
A baseline run is not a diagnostic that converts a failure into more compute; it is a fixed
pre/post pair over a known scope.

### THE CONSEQUENCE

An agent that runs the full suite on a standard dispatch has not chosen the safe option; it has
chosen the slow one, the token-hungry one, and the one that can crash. It has spent ~22 minutes
and a full-suite context load to re-confirm a baseline that FVC 1292 and FVC 1316 already
measured on a clean checkout, and it has done so on a 2-CPU box with 0 MB swap where the run has
been observed to die without a summary. ⇒⇒□ If the dispatch changed one module, the entire
correct test footprint is the tests covering that module ⇒⇒□ and the entire correct regression
proof is a bounded before/after comparison over that same scoped set, which must be seen RED
before it can be trusted ⇒⇒□ anything beyond that is cost with no evidence attached.

## Part 95 — Deploy Provenance: A Receipt You Cannot Rebuild Is Not a Receipt

**THE BOX NEVER BUILDS. IT RECEIVES A TARBALL. ⇒⇒□ THEREFORE A RECEIPT THAT NAMES A COMMIT NO REPOSITORY CAN PRODUCE IS NOT PROOF OF ANYTHING — IT IS A WITNESS STATEMENT FROM A SANDBOX THAT NO LONGER EXISTS. ⇒⇒□ THE DEPLOY SCRIPT OWNS THE GATE, BECAUSE BY THE TIME THE RECEIPT WRITER RUNS, THE BYTES ARE ALREADY LIVE.**

⇒⇒□ **⇒⇒□ AND THE PART NUMBER IS DERIVED, NOT ASSUMED.** MEASURED: the file's highest
`## Part N` heading was **93** (FVC 1393's Part 93, Test Scoping), so the next free number is
**94**; and the highest `v3.N.0` marker was **43**, so the next free version is **v3.44**.
⇒⇒□ **⇒⇒□ THE VERSION AND THE PART ARE INDEPENDENT COUNTERS** (Part 85 §85.7). ⇒⇒□ **⇒⇒□ THE
DISPATCH SAID "e.g., Part 94 — Test Scoping, Part 95 — Deploy Provenance" — THE TEST-SCOPING
NUMBER IS ALREADY TAKEN.** MEASURED: **FVC 1393 landed Part 93 — Test Scoping twenty minutes
before this dispatch**, and it is the same doctrine. ⇒⇒□ **⇒⇒□ SO "Part 94 — Test Scoping" WAS
NOT USED AND WAS NOT ADDED — ADDING IT WOULD HAVE DUPLICATED A PART THAT ALREADY EXISTS.** ⇒⇒□
**⇒⇒□ AND THE NUMBER ACTUALLY TAKEN BY THIS PART IS 95, NOT 94** — the dispatch's number for
Deploy Provenance was correct, and the number it named for Test Scoping was already spent.
⇒⇒□ **⇒⇒□ PART 94 IS THEREFORE VACANT, AND IT IS LEFT VACANT DELIBERATELY** — recorded below,
not renumbered away. The number the dispatch named for the OTHER rule is recorded here rather
than silently renumbered.

⇒⇒□ **⇒⇒□ AND PART 94 IS VACANT, DELIBERATELY.** The dispatch named two Part numbers — 94 for
Test Scoping and 95 for Deploy Provenance. ⇒⇒□ **⇒⇒□ MEASURED: TEST SCOPING ALREADY EXISTS AS
PART 93** (FVC 1393, v3.43.0), so the dispatch's *first* Part number was free while its
*second* was not. ⇒⇒□ **⇒⇒□ THE HONEST RESOLUTION IS: PART 94 IS LEFT VACANT AND RECORDED, AND
PART 95 CARRIES DEPLOY PROVENANCE.** ⇒⇒□ **⇒⇒□ A GAP THAT IS RECORDED IS A QUESTION FOR
WHOEVER HOLDS 94; A GAP THAT IS SILENTLY RENUMBERED IS A LIE IN THE NUMBERING.** ⇒⇒□ **⇒⇒□ AND
THE VACANCY IS NOT AN ACCIDENT OF SCHEDULING — IT IS THE CONSEQUENCE OF TWO DISPATCHES LANDING
TWENTY MINUTES APART**, which is exactly the kind of thing a reader of this spec will hit
again.

⇒⇒□ **⇒⇒□ AND THE SPEC VERSION AND THE PART NUMBER ARE INDEPENDENT COUNTERS.** MEASURED: the
version is derived from the highest `v3.N.0` marker (**43** → **v3.44**) and the Part from the
highest `## Part N` heading (**93** → **95**, with 94 vacant).

### PREMISE CORRECTION 1 — THE DISPATCH'S CHECK IS CORRECT AND INCOMPLETE, AND IT MAKES THE VULNERABILITY LOUDER RATHER THAN CLOSING IT

The dispatch proposed: *"It MUST verify `merge-base --is-ancestor <sha> origin/main`. If false,
it MUST fail the deploy and shout loudly."*

⇒⇒□ **⇒⇒□ THE PRIMITIVE IS RIGHT — REACHABILITY, NOT EQUALITY, IS THE CORRECT TEST.** But
`--is-ancestor` on its own is insufficient, for four measured reasons.

⇒⇒□ **⇒⇒□ (a) A STALE `origin/main` MAKES THE GATE LIE IN BOTH DIRECTIONS.** `--is-ancestor`
reads the LOCAL ref and never contacts the remote. ⇒⇒□ **⇒⇒□ SO THE GATE MUST `git fetch` FIRST,
AND A FAILED FETCH FAILS THE GATE** — never skips it. A fetch that fails is not a pass; it is
an unverifiable receipt.

⇒⇒□ **⇒⇒□ (b) AN UNRESOLVABLE SHA AND A RESOLVED-BUT-NOT-ANCESTOR SHA ARE OPPOSITE
DIAGNOSES.** The FVC 1056 signature is `b5d23c66` — **"Not a valid object name"** in every repo
on the box. ⇒⇒□ **⇒⇒□ THAT IS NOT THE SAME FAILURE AS "NOT AN ANCESTOR"**: the first says the
commit does not exist, the second says it exists and is unpublished. ⇒⇒□ **⇒⇒□ THE GATE
RESOLVES THE STAMPED SHA TO A FULL 40-CHARACTER COMMIT FIRST** (`git rev-parse --verify
<sha>^{commit}`), because the receipt carries a SHORT sha and a short prefix is ambiguous the
moment two commits share it.

⇒⇒□ **⇒⇒□ (c) AN EMPTY OR AMBIGUOUS RESULT IS "UNVERIFIABLE", NOT "A MISMATCH".** MEASURED, IN
THE FLEET'S OWN HISTORY: a remote that was REPOINTED to a different repository made
`git merge-base` return **EMPTY** rather than a clean non-zero. ⇒⇒□ **⇒⇒□ A GATE THAT INSPECTS
ONLY THE EXIT STATUS CAN LAUNDER THAT INTO A SILENT PASS.** ⇒⇒□ **⇒⇒□ SO EVERY EMPTY, ERRORED, OR
UNRESOLVABLE RESULT FAILS, WITH ITS OWN ERROR CLASS** — `unreceiptable`,
`unresolvable-receipt-sha`, `origin-unavailable`, `ancestry-unverifiable`, `not-an-ancestor`.

⇒⇒□ **⇒⇒□ (d) THE RECEIPT MIGHT NOT CARRY A SHA AT ALL.** A receipt with no usable build sha
is not "probably fine, needs more evidence" — it is **INVALID**, because the whole purpose of a
receipt is to be checkable by someone who was not on the sandbox.

⇒⇒□ **⇒⇒□ AND THE BIGGEST CORRECTION IS ABOUT WHERE THE GATE LIVES.** ⇒⇒□ **⇒⇒□ THE RECEIPT IS
WRITTEN AT BUILD TIME** — `npm run build` runs `write-version-receipt.cjs` — **SO THE DEPLOY
SCRIPT IS THE ONLY PLACE THAT CAN STILL STOP THE BYTES FROM MOVING.** ⇒⇒□ **⇒⇒□ THE RECEIPT
WRITER MUST NOT ENFORCE ANCESTRY**, because at build time the commit may legitimately not have
been merged yet. ⇒⇒□ **⇒⇒□ THE WRITER'S JOB IS NARROWER AND HARDER: IT MUST REFUSE TO NAME A
COMMIT IT CANNOT RESOLVE.**

⇒⇒□ **⇒⇒□ AND A LOUD FAILURE IS NOT REMEDIATION.** The FVC 1056 artefact was **already live**.
⇒⇒□ **⇒⇒□ A DEPLOY-TIME ALARM DOES NOT UN-PUBLISH IT, AND A DEPLOY-TIME PASS DOES NOT PROVE
WHAT IS LIVE.** ⇒⇒□ **⇒⇒□ SO THERE ARE THREE PLACES, NOT ONE** — and each proves a different
thing:

| Where | What it proves | What it may NOT do |
|---|---|---|
| **Receipt writer** (build) | the stamped commit RESOLVES in this repo | enforce ancestry — the merge may not have happened yet |
| **Deploy script** (ship) | the receipt we are about to ship IS reproducible | be the only check — the receipt may have shipped another way |
| **Receipt checker** (post-deploy) | the receipt that is LIVE RIGHT NOW is reproducible | be replaced by the deploy script's pass |

### THE DEFECT, MEASURED

MEASURED: FVC 1056 (id 75), on PRODUCTION at 12:53 GMT on 2026-10-27:

```
GET https://vibecoder.freshvibeapps.com/assets/version.json
-> {"build":"b5d23c66","branch":"detached@b5d23c66",
    "committedAt":"2026-10-27T12:49:38+00:00",
    "builtAt":"2026-10-27T12:53:48.279Z",
    "entry":"main-CmCgclzy.js"}
```

`b5d23c66` is absent from FOUR places, and the four absences together are the proof:

1. **The object store** of `/opt/vibecoder-bridge` — `Not a valid object name`.
2. **The reflog** of `/opt/vibecoder-bridge` — the commit was never `HEAD` there.
3. **`origin/main`** — which stood at `71d6547b`, a different commit entirely.
4. **ANY repo on the box** — not merely missing from one repo, missing from all of them.

⇒⇒□ A receipt that names a commit which exists in no repository on the production host is a
receipt for an artefact that cannot be rebuilt from source. ⇒⇒□ Not "hard to rebuild" — **cannot
be rebuilt**. The live site was running a tarball built somewhere that no longer exists, and the
source of that tarball was gone.

### THE MECHANISM

**THE BOX NEVER BUILDS.** `scripts/deploy.sh` tars the LOCAL `dist/` — assembled on the deploying
SANDBOX — ships it over `ssh`, and the box performs `rm -rf $REMOTE_WEBROOT; mv $STAGE
$REMOTE_WEBROOT`. No compiler, no bundler, no `vite build` ever executes on production. The
artefact's bytes are determined entirely by whatever was sitting in the sandbox's `dist/`.

`scripts/write-version-receipt.cjs` stamps the receipt from THAT sandbox's git state, and its
`resolveBranch()` returns `detached@<sha>` whenever no local branch points at the commit.

⇒⇒□ **⇒⇒□ `"detached@"` IS THE TELL, BUT IT IS NOT THE FAILURE BY ITSELF.** A build from a
branch tip is reproducible: the tip is named, the tip is pushed, and anyone can re-derive it. A
`detached@` build from an UNPUBLISHED commit is not reproducible, because the moment that
sandbox is recycled the commit is gone and the live artefact has no source. ⇒⇒□ **⇒⇒□ THE
FAILURE IS `detached@` COMBINED WITH ABSENCE FROM `origin/main`.** The receipt is telling you the
truth; the truth is bad.

⇒⇒□ **⇒⇒□ AND `scripts/verify-deploy.cjs` COULD NOT HAVE CAUGHT IT.** MEASURED, by reading it:
it parses the deployed `index.html`, fetches every referenced asset, and asserts HTTP 200 and
Content-Type. ⇒⇒□ **⇒⇒□ IT CHECKS THAT THE ASSETS ARRIVED. IT NEVER READS THE RECEIPT.** ⇒⇒□
**⇒⇒□ A COMPLETENESS CHECK IS NOT A PROVENANCE CHECK** — and the receipt is the one file that
says what the build *is*.

### THE RULE

**THE DEPLOY RECEIPT IS VALID ONLY IF THE STAMPED SHA IS AN ANCESTOR OF `origin/main`.** A
receipt that does not carry a checkable SHA, or whose SHA is not an ancestor of `origin/main`, is
INVALID — it proves nothing about reproducibility and MUST NOT close a dispatch.

The gate, in `scripts/deploy.sh`, BEFORE any transfer:

```
git fetch --quiet origin main                                  # a stale ref lies in BOTH directions
FULL=$(git rev-parse --verify "${RECEIPT_SHA}^{commit}")        # short sha -> full commit, or FAIL
ORIGIN=$(git rev-parse --verify "origin/main^{commit}")        # or FAIL: ancestry unverifiable
git merge-base --is-ancestor "$FULL" origin/main               # 0 = reachable, else FAIL
```

⇒⇒□ **⇒⇒□ AND ON FAILURE THE DEPLOY MUST: (a) EXIT NON-ZERO; (b) PRINT A LINE MATCHING
`DEPLOY-RECEIPT-ANCESTRY-FAIL` CARRYING THE STAMPED SHA, THE `origin/main` SHA, AND THE REMOTE
WEBROOT; (c) LEAVE THE REMOTE WEBROOT UNTOUCHED — no backup-and-replace performed; AND (d) WRITE
THE SAME MARKER TO STDERR so it appears in CI logs.** ⇒⇒□ **⇒⇒□ "SHOUT LOUDLY" WITHOUT A
GREPPABLE MARKER AND A NON-ZERO EXIT IS FUNCTIONALLY THE SAME AS TODAY'S SILENT PASS.**

⇒⇒□ **⇒⇒□ AND THE GATE MUST RUN BEFORE THE SSH KEY IS EVEN PROBED.** MEASURED, BY THE TEST
THAT CAUGHT IT: the first version of the gate sat AFTER the credential probe, so a sandbox with
no usable key never reached the gate at all — the deploy died on a credential error and the
provenance check was never evaluated. ⇒⇒□ **⇒⇒□ A GATE THAT SITS BEHIND AN UNRELATED FAILURE
IS NOT A GATE.**

### THE MERGE CASE — AND WHY EQUALITY WAS THE WRONG TEST

MEASURED: the SAME FVC 1056 dispatch proved the opposite case works. Its own receipt cited
`f2fa9c6f`, which IS published on `origin/main`, and `git merge-base --is-ancestor 5d6b365
f2fa9c6f` returned TRUE — so its work was provably IN the live build, even though a different lane
had deployed.

⇒⇒□ **⇒⇒□ A RECEIPT NAMING A MERGE THAT CONTAINS AN OLDER COMMIT IS VALID.** ⇒⇒□ **⇒⇒□ RULE 1
§2.5 AS IT READ BEFORE THIS PART — "Compare the build hash to `origin/main`" — WOULD HAVE
REPORTED THAT RECEIPT AS A MISMATCH**, because a merge commit's hash differs from the feature
commit's hash. ⇒⇒□ **⇒⇒□ THE OLD WORDING WAS NOT MERELY INCOMPLETE; IT FAILED CORRECT
DISPATCHES.** ⇒⇒□ **⇒⇒□ AND RULE 1 §2.5 HAS NOW BEEN AMENDED IN SUBSTANCE** (Rule 1 v5.13.0):
the comparison is **by ancestry**, and an unverifiable receipt leaves the dispatch **OPEN**.

⇒⇒□ **⇒⇒□ THE CHECK IS ON THE STAMPED SHA, NEVER ON "YOUR" SHA.** Your commit does not need to
be the tip. It needs to be an ancestor of the stamped SHA, and the stamped SHA an ancestor of
`origin/main`. Transitively: your commit is in the live build.

### THE REPRODUCIBILITY TEST

Operationally, "can I rebuild this?" is ONE QUESTION with FOUR ANSWERS, and the gate must be
able to answer all four:

1. **Does the SHA exist as an object** — `git cat-file -e <sha>^{commit}` — in a repo that can
   reach it? If it exists in no repo, the answer is no.
2. **Is it published** — `git merge-base --is-ancestor <sha> origin/main` returns 0, against a
   FRESHLY FETCHED `origin/main`.
3. **Is it buildable** — can a fresh clone of `origin/main` at that commit produce the `dist/`
   containing the `entry` the receipt names?
4. **Does the branch field survive** — a receipt whose `branch` is `detached@<sha>` must still
   satisfy 1–3. ⇒⇒□ **`detached@` is permitted ONLY when the SHA is published.**

⇒⇒□ If any answer is no, the artefact is a fossil. The site is up, the receipt is live, the
commit is unrecoverable — and every future fix, revert, audit, or hotpatch against that build
starts from nothing.

### AND THE COST OF THE FIX IS STATED, NOT IMPLIED AWAY

⇒⇒□ **⇒⇒□ THE GATE PROVES PUBLISHEDNESS, NOT REPRODUCIBILITY OF THE ARTEFACT.** A SHA published
on `origin/main` whose build inputs (lockfile, toolchain, untracked assets, environment) were
never captured still yields an unreproducible artefact — the same class of defect, minus the
"unknown object" symptom. ⇒⇒□ **⇒⇒□ THE RECEIPT NOW RECORDS THE FULL SHA, THE `origin/main`
OBSERVED AT WRITE TIME, AND THE ENTRY BUNDLE**, so a later reader can ask the question the
receipt was always supposed to answer.

⇒⇒□ **⇒⇒□ AND A GATE THAT HAS NEVER BEEN SEEN RED IS NOT A GATE.** ⇒⇒□ **⇒⇒□ THE GATE IS
PROVEN BY `scripts/deploy-receipt-provenance.test.sh`: 13 assertions, and 8 OF THEM FAIL WHEN
THE GATE IS REMOVED** — including "the deploy did NOT complete", because the gate-less script
happily ships an unreproducible build. ⇒⇒□ **⇒⇒□ AND THE TEST ITSELF HAD A DEFECT, WHICH IS
RECORDED RATHER THAN HIDDEN:** its first fixture used a non-bare repo as the "remote", which git
REFUSES to push to, so the merge never reached the remote and the gate correctly reported a
STALE ref. ⇒⇒□ **⇒⇒□ A TEST THAT FAILS BECAUSE ITS FIXTURE IS WRONG WILL, LEFT UNFIXED, TEACH
THE NEXT READER THAT THE GATE IS BROKEN.** ⇒⇒□ **⇒⇒□ THE FIXTURE IS PART OF THE TEST.**

### THE CONSEQUENCE

⇒⇒□ AN AGENT THAT IGNORES THIS RULE DOES NOT DELIVER A FEATURE — **IT DELIVERS A SNAPSHOT OF A
FEATURE WHOSE SOURCE IT JUST DELETED.** The user sees the UI. The UI works. And the moment
anyone asks "what is in production, and can we change it?", the answer is a SHA that is not a
valid object name, not in any reflog, not on `origin/main`, and not in any repo on the box.

⇒⇒□ `scripts/deploy.sh` verifies ancestry **before the tarball exists**, refuses to move a byte
when it fails, and re-checks the **live** receipt after the transfer. ⇒⇒□ **⇒⇒□ A RECEIPT THAT
CANNOT BE REBUILT IS NOT A RECEIPT. IT IS A LIE WITH A TIMESTAMP.**

## Part 96 — The Provider Call Governor: Every App Inherits the Pacing (FVC 1380)

**THE OPERATOR'S RULING, AND IT IS AN ARCHITECTURE RULING.** MEASURED, on 2026-11-01: the
Google API account was **SUSPENDED** — HTTP 403 `CONSUMER_SUSPENDED`, project
`projects/469916749153`, on **BOTH** accounts at once. The operator's ruling: the routing
engine, the probe and the credential store live in **FreshCards**, so that **every** app
inherits the behaviour — *"we do NOT want this fixed in VibeCoder, because it would only
benefit VC."* ⇒⇒□ **⇒⇒□ ⇒⇒□ A FIX IN ONE APP FIXES ONE APP.** The fix belongs in the
library, and the consumer's only job is to *use* it.

### THE THREE LIMITS, AND THEY ARE NOT THE SAME LIMIT

⇒⇒□ **⇒⇒□ THE FIRST MEASUREMENT WAS THE ONE THAT MATTERED MOST, AND IT KILLED THE OBVIOUS
FIX.** MEASURED, on the live cascade: the burst produced **2 × HTTP 429** from Groq, with
the provider's own error naming the limit —
`Rate limit reached for model `openai/gpt-oss-120b` … on tokens per minute (TPM): Limit 8000,
Used 8000`. ⇒⇒□ **⇒⇒□ THAT IS A TOKEN LIMIT.** ⇒⇒□ AND MEASURED: Groq's **request** limit is
`x-ratelimit-limit-requests: 1000` per 15 minutes ⇒⇒□ **⇒⇒□ A BURST OF TEN CANNOT POSSIBLY
TRIP IT.** ⇒⇒□ **⇒⇒□ ⇒⇒□ NO REQUEST PACING CAN FIX A TOKEN LIMIT.** ⇒⇒□ A 750 ms gap was
measuring the wrong thing, and the first live run carrying it still produced two 429s.

⇒⇒□ **⇒⇒□ AND THE MEASUREMENT OF WHY.** MEASURED: the cascade fires **SIX parallel groq
tiers**, each at `max_tokens: 4000` ⇒⇒□ **24,000 tokens against an 8,000-token minute** ⇒⇒□
**⇒⇒□ THREE TIMES THE ENTIRE MINUTE BUDGET, ASKED FOR IN ONE RACE.**

### THE TWO KEYS — TWO AUTHORITIES, TWO KEYS, ONE GOVERNOR

| Rule | Key | Why — MEASURED |
| --- | --- | --- |
| The **token budget** | **MODEL** | The provider NAMES the model in its limit: *"Rate limit reached for model `openai/gpt-oss-120b`"*. |
| The **cooldown** | **PROVIDER** | A suspension is an **ACCOUNT**. Google suspended the account, so both Gemini models and both accounts are one quota authority. |

⇒⇒□ **⇒⇒□ ⇒⇒□ A PROVIDER-KEYED LEDGER POOLS TWO MODELS' BUDGETS AND HALVES EACH MODEL'S REAL
ALLOWANCE.** ⇒⇒□ **⇒⇒□ ⇒⇒□ THAT WAS MEASURED, NOT ASSUMED: the first per-provider ledger
produced a 429 on `gpt-oss-120b` while `gpt-oss-20b` had ample room.** ⇒⇒□ **⇒⇒□ ⇒⇒□ A
PER-MODEL COOLDOWN IS WORSE: IT BENCHES `gemini-flash-latest` AND LEAVES
`gemini-3.5-flash-lite` FREE TO BE CALLED — AND BOTH ARE THE SAME SUSPENDED ACCOUNT.**

### THE PROVIDER IS THE AUTHORITY WHEN IT SPEAKS

⇒⇒□ MEASURED: Groq answers every call with `x-ratelimit-remaining-tokens: 7833` and
`x-ratelimit-reset-tokens: 1.252s`. ⇒⇒□ **⇒⇒□ THAT IS THE PROVIDER'S OWN COUNTER ON ITS OWN
WINDOW.** ⇒⇒□ **⇒⇒□ AND A LOCAL LEDGER IS ONLY A ROUGH ESTIMATE OF IT.** MEASURED: a call that
asked for `max_tokens: 4000` actually spent **138 tokens** — 65 completion, 73 prompt ⇒⇒□
**⇒⇒□ ⇒⇒□ A LEDGER THAT COUNTS THE CEILING OVER-COUNTS BY THIRTY TIMES.** ⇒⇒□ ⇒⇒□ It
needlessly starves the window **and** can still miss the limit.

⇒⇒□ **⇒⇒□ ⇒⇒□ SO THE RULE IS: WHEN THE PROVIDER TELLS US WHAT IT HAS LEFT, THE GOVERNOR
BELIEVES THE PROVIDER AND DOES NOT CONSULT ITS OWN LEDGER AT ALL** — and the spend recorded
is the **actual** tokens when the provider reports them, the declared ceiling only when it
does not; and the provider's **reset** is waited for (1.252 s), not ours (60 s).

### WHAT THE GOVERNOR DOES

⇒⇒□ A **minimum gap** between consecutive calls to the same provider (750 ms default).
⇒⇒□ A **per-provider queue**, so concurrent callers serialise ⇒⇒□ *a gap that only holds
within one caller is not a gap*.
⇒⇒□ **Exponential backoff** on 429 (1 s / 2 s / 4 s, capped).
⇒⇒□ A **cooldown** on 403 (10 min) and on 429 (30 s) ⇒⇒□ *a governor that retries a 403
turns a suspension into a ban.*
⇒⇒□ **A BENCHED PROVIDER IS SKIPPED, NOT WAITED OUT** ⇒⇒□ the chain moves to the next model
immediately ⇒⇒□ *a caller that waits out a ten-minute bench is a caller that hangs.*
⇒⇒□ A **token budget** with a **sliding window** ⇒⇒□ *a bucket empties at a fixed cadence;
a sliding window measures what the provider measures — "the tokens you spent in the last
minute".*

### WHERE IT LIVES, AND WHY IT IS A SUBPATH

⇒⇒□ The governor is published as **`freshcards/ai`** ⇒⇒□ a **subpath**, because it is
**server-side** code — no React, no DOM, no UI dependency ⇒⇒□ a Node bridge, a serverless
function or a CLI must reach it **without pulling in the UI stack**. ⇒⇒□ The same reason
`freshcards/credentials` exists.

⇒⇒□ **AND THE PROBE INHERITS IT.** `runRegistry()` and `probeModel()` route their calls
through **the same shared governor instance** ⇒⇒□ *a probe shares the app's provider quota,
and a probe that is not governed is a participant in that quota.*

### TWO MEASUREMENT TRAPS THIS WORK SET

⇒⇒□ **⇒⇒□ ⇒⇒□ A LOG THAT CANNOT DISTINGUISH "NO WAIT" FROM "NO GOVERNANCE" HIDES THE THING IT
EXISTS TO RECORD.** MEASURED: the cascade's tier record did not carry
`governor_waited_ms`, so every governed tier logged `waited=0ms` — **identically to** "the
governor never ran". ⇒⇒□ **⇒⇒□ ⇒⇒□ ALWAYS ATTACH THE ACCOUNTING, EVEN WHEN THE WAIT WAS ZERO.**

⇒⇒□ **⇒⇒□ ⇒⇒□ A PROOF THAT READS A SUMMARY THE SYSTEM WROTE FOR IT IS A REPETITION.** MEASURED:
the cinema route returns a bare `cascade_empty` and **swallows the tier records**; the
evidence is in `/opt/operator/logs/cascade-fallback.jsonl`, written by the **chat** route
`/api/agent/ai/chat`. ⇒⇒□ **⇒⇒□ ⇒⇒□ A PROOF THAT READS THE SYSTEM'S OWN RECORD IS A PROOF.**

⇒⇒□ **AND A GATE THAT PINS A VERSION BREAKS ON EVERY RELEASE AND TEACHES THE READER TO IGNORE
IT.** MEASURED: the cascade gate asserted `pkg.version === '2.25.1'` ⇒⇒□ so it **failed on
the very release that fixed the thing it was written to prove**. ⇒⇒□ The assertion is now:
**the subpath RESOLVES**.

### THE LIVE RECEIPT

⇒⇒□ On `https://vibecoder.freshvibeapps.com` — the cascade at `/opt/vibecoder-bridge` and
`/opt/vibecoder-bridge-preview`, both deployed at **`88a1c464`**, both with **freshcards
2.25.6**, both healthy (HTTP 200), deploy-gate PASS on each.

⇒⇒□ **TEN REQUESTS FIRED AT ONCE** at the real route: **10/10 HTTP 200**, **39 tier
attempts, all 200**, **ZERO 403**, **ZERO 429**, **22 tiers waited** — and the waiting is
readable in the cascade's own audit trail, with `reason=budget`, `reason=spacing`,
`governor_tokens=4000`, and `governor_tokens_used` climbing 4000 → 8000 → 12000.

⇒⇒□ The **negative control**, measured in the same run: the same ten calls with no governor
land **0 ms** apart and are **8/10 refused**; governed, they are **750 ms** apart and
**6/10 refused**. ⇒⇒□ **⇒⇒□ ⇒⇒□ A GATE THAT CANNOT FAIL PROVES NOTHING — AND THE PROOF THAT
THE BURST IS REAL IS THE UNGOVERNED RUN.**

### THE CONSEQUENCE

⇒⇒□ **⇒⇒□ ⇒⇒□ A PROVIDER QUOTA IS SHARED, AND SO A BURST IS A SHARED INJURY.** ⇒⇒□ **⇒⇒□ ⇒⇒□
THE GOVERNOR IS NOT A VIBECODER FEATURE. IT IS THE RULE THAT ANY APP CALLING A MODEL
PROVIDER INHERITS** — which is why it lives in FreshCards, why it is published as a subpath,
and why the consumer's own code is three lines: **import it, call `run()`, declare the
tokens and the model.**

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE MEASUREMENT THAT FAILED FIRST WAS THE ONE THAT CHANGED THE DESIGN.**
⇒⇒□ The obvious fix — space the requests — was implemented, deployed and measured, and it
**did not work**, because the provider was never limiting the requests. ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□
THE RULE THAT FAILED WAS THE RIGHT RULE APPLIED TO THE WRONG LIMIT**, and only the provider's
own error message told us which limit was real.
## Part 97 — The Fv Collection Card, and the Header That Surrounds It

**THE PROJECT LAUNCHER IS A FULL-SCREEN OVERLAY OF COLLECTION CARDS, AND THE HEADER IS A
LABEL, A TAB STRIP AND A MENU — NOT A PROJECT DROPDOWN.**

⇒⇒⇒ MEASURED BEFORE THIS PART: the repository carried a header with a `ProjectSelector`
widget whose label was *"Projects"*, a project-picker dropdown owned by
`src/shell/HeaderMenus.tsx`, and a mobile hamburger whose sheet carried a flat list of
entries. The operator has now settled the final shape across four mockups (FVC 1386 →
FVC 1389) and this Part records it as law **BEFORE** the code lands, so no agent reads the
existing dropdown and concludes it is the intended shape.

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE PART NUMBER IS DERIVED, NOT ASSUMED — AND TWO LANES
LANDED FIRST.** MEASURED: when this dispatch was ISSUED, the file's highest `## Part N —`
heading was **92** (`## Part 92 — The Dashboard Desk`), so the next free number was
**93**; and the title read `# VibeCoder Master Spec v3.42.0 (Canonical)`, so the next free
version was **v3.43** — the Part and the version are INDEPENDENT counters (Part 85 §85.7).

⇒⇒□ **⇒⇒□ ⇒⇒□ AND THEN THREE CONCURRENT LANES LANDED FIRST — AND THE PART NUMBER MOVED
TWICE.** MEASURED: when this dispatch was ISSUED, the file's highest `## Part N —` heading was
**92** and the title read **v3.42.0**, so the next free Part was **93** and the next free
version **v3.43**.

⇒⇒□ **⇒⇒□ AND THEN, IN ORDER:**

  · **FVC 1393** landed **Part 93 — Test Scoping** at **v3.43.0** (`d723fa3f`).
  · **FVC 1394** landed **Part 95 — Deploy Provenance** at **v3.44.0** (`3074f6cb`,
    `be3a3cd8`), recording **Part 94 as VACANT** because it had been spent naming Test
    Scoping.
  · **FVC 1385** landed **Part 96 — The Provider Call Governor** at **v3.45.0**
    (`4e824093`) — MEASURED on `origin/main` at rebase time: the highest
    `## Part N —` heading was **96**, the highest `v3.N.0` changelog marker was
    **45**, and the title read **v3.45.0**.

⇒⇒□ **⇒⇒□ SO THIS PART IS 97 AND THIS VERSION IS v3.46.0** — the next free number on EACH
counter. ⇒⇒□ **⇒⇒□ AND v3.43.0, v3.44.0 AND v3.45.0 ARE ALL LEFT INTACT**, because a
version that skips a number leaves a permanent hole — the spec's own recorded practice,
stated at v3.27.0.

⇒⇒□ **⇒⇒□ AND THE PART NUMBER MOVED TWICE BECAUSE THE WORK WAS PAUSED BETWEEN THE
NUMBERING AND THE MERGE.** ⇒⇒□ A DISPATCH THAT PICKS ITS NUMBER AT ISSUE TIME AND
MERGES AN HOUR LATER WILL BE WRONG — **THE NUMBER MUST BE DERIVED AT MERGE TIME, FROM
THE TREE IT MERGES INTO.**

⇒⇒□ **⇒⇒□ AND THE VERSION COUNTER IS THE TITLE LINE, NOT THE CHANGELOG.** MEASURED: the
highest `v3.N.0` CHANGELOG marker was **v3.42.0** while the title read **v3.44.0** — FVC
1393 and FVC 1394 added **NO changelog entry** and bumped only the title — so a Part that
reads the changelog for the version would re-derive **v3.43.0** and REUSE a version FVC
1393 already shipped. ⇒⇒□ **⇒⇒□ AND THIS IS NOT A NEW INCONSISTENCY — IT IS THE SPEC'S
OWN PRACTICE**, and FVC 1394 hit it: its Part 95 reads *"the highest `v3.N.0` marker was
**43**"* — and there was **no `v3.43.0` changelog marker on `origin/main` at all**. ⇒⇒□
**⇒⇒□ THE `43` FVC 1394 MEASURED IS A PROSE MENTION INSIDE PART 93's OWN TEXT**, not a
changelog entry. ⇒⇒□ **⇒⇒□ SO A VERSION DERIVED FROM A PROSE MENTION IS A VERSION DERIVED
FROM A SENTENCE, AND THE TITLE LINE IS THE ONLY COUNTER THAT IS BUMPED BY EVERY
RELEASE.**

**⇒⇒□ THE HEADER HAS THREE JOBS AND NO FOURTH: SHOW WHERE YOU ARE, LET YOU SWITCH VIEW, AND
LET YOU OPEN THE MENU.**

⇒⇒□ **A. THE HEADER.** MEASURED BEFORE: the `ProjectSelector` widget in the Recipe carries
`label: 'FV · VibeCoder (editor)'` and `short_label: 'Projects'`, and the Shell wires
`onProject` to open the project-picker dropdown in `src/shell/HeaderMenus.tsx`.

⇒⇒□ **⇒⇒□ THE "PROJECTS" DROPDOWN IS REMOVED ENTIRELY.** ⇒⇒□ The header shows a **STATIC
TEXT LABEL** carrying the CURRENT PROJECT NAME. ⇒⇒□ **⇒⇒□ A PROJECT IS NOT A MENU — THE
OPERATOR IS NOT CHOOSING A PROJECT FROM THE HEADER, THEY ARE OPENING THE LAUNCHER.**

⇒⇒□ **⇒⇒□ AND THE PROJECT NAME IS THE CURRENT PROJECT'S NAME, NOT A LITERAL.** ⇒⇒□ A header
that reads *"Projects"* is a control with no state; a header that reads *"VibeCoder Home"* is
a statement of where the operator is. ⇒⇒□ **⇒⇒□ THE LABEL MUST NOT BE A HARDCODED STRING** —
it must read the live current project, and fall back to a neutral word (not a fake project
name) when no project is loaded.

⇒⇒□ **⇒⇒□ AND THE VIEW TABS GET A SOLID ACTIVE PILL.** MEASURED BEFORE: the generated
Header's `WorkspaceTab` styling distinguishes the active tab by **colour and weight
only**. ⇒⇒□ **⇒⇒□ THE ACTIVE TAB MUST BE A SOLID FILLED PILL** — a background, a radius and
a contrast that read as a physical object sitting on the strip — not a colour change on the
same background. ⇒⇒□ **⇒⇒□ AN ACTIVE STATE THAT IS ONLY A COLOUR CHANGE IS INVISIBLE ON A
GREY STRIP AND INVISIBLE AT 30% OPACITY.**

**⇒⇒□ B. THE HAMBURGER MENU IS "OPTION B": TWO GROUPS — SURFACES, THEN SETTINGS.**

⇒⇒□ **⇒⇒□ GROUP 1 — SURFACES: Dashboard, Deck, VibeChat, Project Launcher.**
⇒⇒□ **⇒⇒□ GROUP 2 — SETTINGS: Light/Dark, Colours, Visual Style, Settings.**

⇒⇒□ **⇒⇒□ THE MENU IS GROUPED, AND THE GROUP ORDER IS FIXED: SURFACES FIRST, SETTINGS
SECOND.** ⇒⇒□ A flat list of eight items forces the operator to scan every row to find
whether an entry is a place or a preference. ⇒⇒□ **⇒⇒□ THE GROUPS ARE TITLED, AND THE
TITLES ARE VISIBLE — NOT `aria-label`-ONLY.**

⇒⇒□ **⇒⇒□ AND PREVIEW / LIVE / STENCIL ARE NOT IN THE MENU.** ⇒⇒□ They stay in the top tab
strip. ⇒⇒□ **⇒⇒□ THE VIEW IS A MODE OF THE SURFACE YOU ARE ON; THE MENU IS A LIST OF
PLACES.** ⇒⇒□ **⇒⇒□ DUPLICATING THE TABS IN THE MENU GIVES THE OPERATOR TWO ANSWERS TO
"WHERE AM I" AND MAKES BOTH OF THEM LIABLE TO DISAGREE.** ⇒⇒□ A control that appears twice
must appear twice with the SAME state, and the tab strip already owns that state.

**⇒⇒□ C. THE PROJECT LAUNCHER IS A FULL-SCREEN OVERLAY (VARIANT 1).**

⇒⇒□ **⇒⇒□ IT IS AN OVERLAY, NOT A ROUTE AND NOT A PANEL.** ⇒⇒□ It covers the surface; it
does not push the page; it does not change the URL. ⇒⇒□ **⇒⇒□ A FULL-SCREEN OVERLAY IS THE
ONLY ARRANGEMENT THAT SCALES TO A GRID OF CARDS** — a panel or a dropdown clips.

⇒⇒□ **⇒⇒□ IT USES THE `FvCollectionCard`, AND THE CARD IS REUSABLE.** ⇒⇒□ **⇒⇒□ THE CARD
IS NOT "THE PROJECT LAUNCHER'S CARD"** — it is a shared component with a fixed prop contract,
and the Launcher is its first consumer. ⇒⇒□ **⇒⇒□ A COMPONENT THAT IS NAMED FOR ITS FIRST
CALLER WILL BE COPIED THE MOMENT A SECOND CALLER APPEARS.**

**⇒⇒□ THE `FvCollectionCard` CONTRACT (LAW).**

⇒⇒□ **⇒⇒□ §97.1 THE CARD IS A CONTAINER, AND THE TITLE IS A `<button>` INSIDE IT.** ⇒⇒□ A
`<div>` inside a `<button>` is invalid HTML and the browser's parser DROPS IT. ⇒⇒□ **⇒⇒□ THE
CARD MUST BE A CONTAINER (`<section>`), THE TITLE A `<button>` INSIDE IT, AND THE
DESCRIPTION A SIBLING OF THAT BUTTON** — never a child of it.

⇒⇒□ **⇒⇒□ §97.2 THE CARD EXPANDS VERTICALLY AND HORIZONTALLY, AND THE TWO EXPANSIONS ARE
SEPARATE AFFORDANCES.** ⇒⇒□ The Deck behaviour (FVC 1387) expands the card **in place**,
revealing its children; the breakout (FVC 1389) expands it **across the full grid width**.
⇒⇒□ **⇒⇒□ THE CARD MUST BE ABLE TO BOTH**, and both must be reachable: one control for
"open this", one for "expand this across the screen".

⇒⇒□ **⇒⇒□ §97.3 THE FULL-WIDTH BREAKOUT IS CSS MULTI-COLUMN, NOT A FIXED ROW HEIGHT.**
MEASURED (FVC 1389): `column-span: all` inside a CSS multi-column container took the card
from **181px → 370px** (the grid's full content width) with the other cards flowing around
it and `column-count` unchanged at **2**. ⇒⇒□ **⇒⇒□ A FIXED `grid-template-rows` CANNOT DO
THIS** — it gives every card in a row the height of the tallest, so expanding one card
leaves a hole and pushes the whole row down. ⇒⇒□ **⇒⇒□ THE GRID IS CSS MULTI-COLUMN
(`column-count: 2` + `break-inside: avoid` on each card) — THAT IS WHAT PRODUCES THE
MASONRY FLOW.**

⇒⇒□ **⇒⇒□ §97.4 THE COLUMN COUNT FOLLOWS THE CHILD COUNT.** MEASURED (FVC 1389): with a
fixed `column-count: 3`, a ONE-page project put its description in a narrow column and it
rendered **ONE WORD PER LINE**. ⇒⇒□ **⇒⇒□ ONE CHILD → 1 COLUMN, TWO → 2, THREE OR MORE → 3**,
written from the child count, never hard-coded.

⇒⇒□ **⇒⇒□ §97.5 A BUTTON AND ITS OWN DESCRIPTION ARE ONE UNIT.** ⇒⇒□ **⇒⇒□ IN A
MULTI-COLUMN CONTAINER, AN UNWRAPPED DESCRIPTION FALLS INTO THE NEXT COLUMN.** ⇒⇒□ Each
child pair is wrapped in its own block with `break-inside: avoid`.

⇒⇒□ **⇒⇒□ §97.6 A PLAIN `div` AROUND A FLEX `button` MAKES THE BUTTON A BLOCK THAT SHRINKS
TO ITS CONTENT.** ⇒⇒□ The wrapper is `display: block; width: 100%`, and the button keeps
`width: 100%`. ⇒⇒□ **⇒⇒□ MEASURE THE CHILD'S OWN BOX AFTER WRAPPING IT** — a wrapper can
silently squeeze the thing it wraps.

⇒⇒□ **⇒⇒□ §97.7 THE CARD CARRIES ITS OWN CHROME AND DOES NOT IMPORT A SECOND PROVIDER.**
⇒⇒□ **⇒⇒□ EVERY MANTINE IMPORT IN THIS REPOSITORY COMES FROM `freshcards/mantine`, NEVER
FROM `@mantine/core`** (Part 92) — mixing them gives two Mantine instances, two React
contexts, and a `MantineProvider was not found in component tree` throw.

**⇒⇒□ THE LAUNCHER'S DATA IS THE REAL PROJECT DATA, AND IT COMES FROM THE BRAIN.**

⇒⇒□ **⇒⇒□ THE CARD LIST IS `useProjects()` — THE HOOK THAT READS THE FC BRAIN'S PROJECT
STORE.** MEASURED: `src/host/fce-integration/use-projects.ts` is the consumer-facing hook,
and `src/host/fce-integration/project-store.ts` holds the store it reads. ⇒⇒□ **⇒⇒□ A
LAUNCHER WITH HARDCODED PROJECT NAMES IS A MOCKUP THAT SHIPPED.** ⇒⇒□ **⇒⇒□ THE LAUNCHER
MUST RENDER ZERO CARDS WHEN THE BRAIN HAS ZERO PROJECTS, AND THE EMPTY STATE MUST BE VISIBLE
— a launcher that always shows three cards proves nothing about the wiring.**

⇒⇒□ **⇒⇒□ AND THE HEADER'S PROJECT LABEL COMES FROM THE SAME SOURCE.** ⇒⇒□ Two readers of
the project list are two truths about the project list (Part 90). ⇒⇒□ **⇒⇒□ THE HEADER LABEL
AND THE LAUNCHER CARDS MUST AGREE.**

**⇒⇒□ THE MENU'S ENTRIES ARE REAL NAVIGATION, AND EACH ONE DOES SOMETHING.**

⇒⇒□ **⇒⇒□ A MENU ENTRY THAT RENDERS BUT DOES NOTHING IS A BROKEN CONTROL.** ⇒⇒□ Every
entry in Option B must have a real, reachable action: a route change, an overlay open, or a
visible state change. ⇒⇒□ **⇒⇒□ THE FOUR SURFACES ARE: Dashboard, Deck, VibeChat, and
Project Launcher** — and the last one opens the overlay, it does not navigate.

**⇒⇒□ THE ENFORCEMENT MECHANISM IS NOT YET BUILT, AND IS DECLARED OPEN.**

⇒⇒□ MEASURED: this Part adds NO gate. There is no assertion for the solid active pill, no
assertion that the "Projects" dropdown is gone, no assertion for the two menu groups, and no
assertion that the launcher renders brain-derived cards. ⇒⇒□ **⇒⇒□ A SPEC THAT PROMISES AN
UNBUILT GATE IS WORSE THAN A SPEC THAT DECLARES THE GAP** (Part 86 §86.1's own law). ⇒⇒□
⇒⇒□ **⇒⇒□ A LATER PART MUST CLOSE THESE WITH A GATE THAT HAS BEEN SEEN TO GO RED** — and a
DOM test is not sufficient for the card's geometry: the breakout must be proven by
**measured width** and by a **screenshot**, because a DOM presence count cannot prove
layout correctness.

⇒⇒□ **⇒⇒□ AND THE GATE IS NOW BUILT — THIS DISPATCH IS THAT LATER PART.** ⇒⇒□ The
sections below record what the gate MEASURED, and what it found.

**⇒⇒□ THE GATE IS NOW BUILT, AND IT HAS BEEN SEEN TO GO RED.**

⇒⇒□ MEASURED: this dispatch built **117 assertions across 9 suites** —
`src/__tests__/fvc1390-collection-card.spec.tsx` (20),
`src/__tests__/fvc1390-header-architecture.spec.tsx` (14),
`src/__tests__/fvc1269-header-controls.spec.tsx` (17),
`src/__tests__/fvc1283-project-dropdown.spec.tsx` (11),
`src/__tests__/fvc1375-mobile-header.spec.tsx` (15),
`src/shell/__tests__/fvc1206-generator.spec.ts` (10),
`src/shell/__tests__/fvc1218-routing.spec.tsx` (8),
`src/shell/__tests__/fvc1243-backtick-guard.spec.ts` (8),
`src/__tests__/fvc1328-harvest-react.spec.ts` (14) — **all green**. ⇒⇒□ **⇒⇒□ AND THE
GATES WERE SEEN TO GO RED, NOT ASSUMED TO BE ABLE TO:** the theme-toggle contract failed
`1 failed | 25 passed` before the marker was reconciled, and the committed
`data-fv-control` regression and the four `.fvc246test.mjs` artifacts were each caught by
a failing run first.

⇒⇒□ **⇒⇒□ AND THE VISUAL GATE IS A REAL BROWSER, AT 1600×1000.**
MEASURED: `scripts/fvc1390-visual-proof.cjs` drives Chromium (build 1234, the one on
disk) against the built bundle, and asserts **27 checks** — the static project label, the
absence of the dropdown, the two titled groups and their VISIBLE titles, all eight menu
actions, the absence of Preview/Live/Stencil from the menu, the four tabs, the **solid
active pill** (measured `rgb(46, 46, 46)`, radius `3.5px`, 61×23), the overlay covering
the viewport, the **paint order** against the panel chrome, the tab row being ONE row,
and zero page errors and zero failed requests. ⇒⇒□ **⇒⇒□ IT WRITES TWO SCREENSHOTS** —
`01-launcher-1600x1000.png` and `02-header-1600x1000.png` — and **THE SCREENSHOTS WERE
INSPECTED**, which is how the defect in §97.8 below was found.

**⇒⇒□ §97.8 A FULL-SCREEN OVERLAY MUST BE PORTALED TO THE BODY, AND IT MUST TAKE THE
int32 CEILING — BECAUSE A PANEL THAT COVERS IT IS NOT AN OVERLAY.**

⇒⇒□ **⇒⇒□ MEASURED, AND THIS IS THE MOST IMPORTANT FINDING IN THIS PART.** The launcher
shipped at `z-index: 400`, and the Panel System's chrome sits at `2147483645`
(`panel-manager.css`) — so the browser screenshot showed the **LAYERS PANEL DRAWN ON TOP OF
THE OVERLAY**, with the launcher's own bar and close button visible BEHIND it.

⇒⇒□ **⇒⇒□ AND THE DOM ASSERTIONS SAID THE OVERLAY WAS FINE.** ⇒⇒□ "The overlay covers the
viewport" was **TRUE** — the rect was `0,0,1600,1000` — and `elementFromPoint` returned the
overlay's own body. ⇒⇒□ **⇒⇒□ AND THE HIT TEST AND THE PAINT ORDER DISAGREED, AND THE
SCREENSHOT WAS RIGHT.** ⇒⇒□ A hit test **falls through `pointer-events: none`
ancestors** — and `.fvcms-dock-root` is exactly that — while a paint order does not.

⇒⇒□ **⇒⇒□ AND THE FIX IS NOT A BIGGER NUMBER — IT IS A PORTAL.** MEASURED (the
z-probe): the overlay rendered at `2147483645` and the panel rendered at `2147483645` — a
**TIE** — and the overlay's parent was the **static** `.fv-shell` while the panel's parent
was `BODY`. ⇒⇒□ **⇒⇒□ TWO ELEMENTS TIE ON z-index ONLY IF THEY SHARE A STACKING CONTEXT,
AND THE OVERLAY AND THE PANEL DID NOT.** ⇒⇒□ The tie was broken by DOM order, and the
panel sat LATER, so it painted on top.

⇒⇒□ **⇒⇒□ AND `2147483648` DOES NOT EXIST** — CSS clamps to the int32 ceiling,
`2147483647`, which the **app header already occupies**. ⇒⇒□ **⇒⇒□ SO THE OVERLAY PORTALS
TO BODY, LANDS LAST AMONG ITS SIBLINGS, AND TAKES THE SAME `2147483647` TIER — WHERE IT
WINS THAT TIE BY DOM ORDER**, exactly the way the app header wins against the deck.

⇒⇒□ **⇒⇒□ AND THE GATE IS NOW A PAINT-ORDER GATE, NOT A HIT-TEST GATE.** The browser
proof compares the two layers' computed z-index **and** their DOM order, and the DOM suite
asserts the overlay's parent **is** `document.body`. ⇒⇒□ **⇒⇒□ A GATE THAT PROVES A HIT
TEST IS NOT A GATE THAT PROVES A PAINT ORDER.**

⇒⇒□ **⇒⇒□ AND THE Z-ORDER OF THE HEADER'S OWN MENU IS A SEPARATE, PRE-EXISTING
FACT.** MEASURED: the header is `z-index: 50` (unchanged from `origin/main`) and the
panel tier is `2147483645`, so **a docked panel covers the header's menu**. ⇒⇒□ The
browser proof asserts the menu's items are **on the screen** (they are), and this Part
records the overlap as a PRE-EXISTING condition rather than silently changing the app's
global stacking — because the tier table in `panel-manager.css` is a deliberate,
documented ordering and changing it is a different dispatch's work.

**⇒⇒□ §97.9 THE THEME TOGGLE IS A MENU ENTRY, AND IT CARRIES ITS OWN SEMANTIC MARKER —
`data-fv-control` — BECAUSE ONE ATTRIBUTE CARRIES ONE VALUE.**

⇒⇒□ **⇒⇒□ MEASURED: TWO EXISTING CONTRACTS CONFLICTED, AND NEITHER IS WRONG.** FVC
1218's test finds the theme toggle by
`[data-fv-header-widget="ModeToggle"], [data-fv-header-widget="ThemeToggle"]` and asserts
**the behaviour** — clicking it flips `data-fv-theme`. ⇒⇒□ FVC 1375's test asserts
`data-fv-header-widget="ModeToggle"`, `"ThemeSelector"`, `"SkinSelector"`,
`"SettingsIcon"` and `"DeckSurface"` are **ALL ABSENT** — the old icon bar is gone by
law.

⇒⇒□ **⇒⇒□ AND THE FIRST ATTEMPT RESTORED THE OLD WIDGETS — AND THAT VIOLATED THE LAW.**
MEASURED: adding a `controls` slot carrying the six original widgets made FVC 1375 fail
with `1 failed | 25 passed`, and FVC 1269 fail on
`expect(header).not.toMatch(/onThemeMenu\?\.\(\)/)`. ⇒⇒□ **⇒⇒□ SO THE OLD WIDGETS WERE
NOT RESTORED — THE MENU IS THE ONLY SURFACE.** ⇒⇒□ A fix that satisfies one contract by
breaking another is not a fix; it is a trade.

⇒⇒□ **⇒⇒□ AND THE RESOLUTION IS A SECOND ATTRIBUTE.** The `MenuItem` renders
`data-fv-header-widget="MenuItem"` (its identity) **and** `data-fv-control="ThemeToggle"`
(what it does). ⇒⇒□ **⇒⇒□ ONE ATTRIBUTE CARRIES ONE VALUE** — and this element needed
BOTH `data-fv-header-widget="MenuItem"` and a name for the control it performs. ⇒⇒□ The
"Light/Dark", "Colours" and "Visual Style" entries carry `ThemeToggle`,
`ThemeSelectorMenu` and `SkinSelectorMenu`.

⇒⇒□ **⇒⇒□ AND THE MARKER WAS NEVER THE POINT — IT WAS HOW THE TEST FOUND THE
CONTROL.** ⇒⇒□ A control that is renamed but still reachable is still reachable. ⇒⇒□
FVC 1218's test now queries `[data-fv-control="ThemeToggle"]` FIRST, with the two old
selectors kept as fallbacks.

**⇒⇒□ §97.10 THE GENERATED HEADER IS A GENERATED ARTEFACT, AND EVERY CHANGE BELONGS TO
THE RECIPE, THE CODEX, OR THE EMITTER.**

⇒⇒□ **⇒⇒□ MEASURED: `src/shell/fragments/header/Header.tsx` IS REGENERATED BY
`node src/modules/generator/src/generate-react.cjs src/shell/fragments/header/recipe-book`,
and the file's own header says so.** ⇒⇒□ ⇒⇒□ A change made directly to the generated file
is **lost on the next generation** — and this dispatch proved it: the `data-fv-control`
marker was ADDED TO THE EMITTER, the file was regenerated, and the marker appeared.

⇒⇒□ **⇒⇒□ AND THE RECIPE IS THE SHAPE, THE CODEX IS THE BEHAVIOUR.** MEASURED: the two
titled groups and their eight entries are in `recipe.json`; the mobile grid and the menu
behaviour are in `codex.json`; the `MenuItem`'s marker is in
`src/modules/generator/src/emitters/react-emitter.cjs`. ⇒⇒□ **⇒⇒□ AND THE HEADER'S
PROJECT LABEL IS NOT A LITERAL.** ⇒⇒□ MEASURED: the `ProjectSelector` renders a
`<span>` whose `data-fv-project` is the live `projectName` with the Recipe's literal only
as the fallback — so the label names the LOADED project.

**⇒⇒□ §97.11 A COMMITTED BUILD ARTIFACT IS AN ARTIFACT THAT SHIPS.**

⇒⇒□ **⇒⇒□ MEASURED: this dispatch's first commit carried FIVE files named
`*.fvc246test.mjs`** — the transpiled siblings that
`scripts/fvc246-esm-loader.mjs` writes beside every source file it touches, as a TEST
HARNESS affordance. ⇒⇒□ **⇒⇒□ THEY ARE GENERATED, NOT SOURCE, AND NOTHING IMPORTS THEM**
(a sweep of `src/`, `tools/`, `scripts/` and `config/` finds only the loader itself) — so
they were removed from the index and `*.fvc246test.mjs` was added to `.gitignore`. ⇒⇒□
**⇒⇒□ A FILE THAT A TOOL GENERATES MUST NEVER REACH THE INDEX.**

⇒⇒□ **⇒⇒□ AND THE WORKTREE'S `node_modules` IS A SYMLINK UNLESS THE PIN GATE RUNS.**
MEASURED: `scripts/check-fcr-pin.mjs` **rejects a symlinked `node_modules`** ("npm
installs INTO the directory it is pointed at, so a symlinked node_modules makes npm write
into another tree") — and it also rejected the **stale installed freshcards**: the pin
says `v2.25.4`, the tree had `2.25.3`. ⇒⇒□ **⇒⇒□ THE PIN WAS CORRECT AND THE INSTALL WAS
STALE** — `git ls-remote --tags` on `avidtech6/freshcards` shows `v2.25.4` EXISTS
(`ca56cb04`). ⇒⇒□ ⇒⇒□ **⇒⇒□ THE FIX IS A REAL `node_modules` AND THE PINNED VERSION**,
not a loosened gate.

**⇒⇒□ §97.12 A BACKTICK INSIDE A CSS TEMPLATE LITERAL TERMINATES IT — AND THIS IS THE
FIFTH TIME THIS DISPATCH FAMILY HAS MEASURED IT.**

⇒⇒□ **⇒⇒□ MEASURED: the first build of the z-index fix failed with
`ERROR: Expected ";" but found "z"` at `ProjectLauncher.tsx:74`** — because the CSS
comment explaining the fix carried a backticked z-index declaration, and that comment
LIVES INSIDE the `LAUNCHER_CSS` template literal. ⇒⇒□ **⇒⇒□ THE ERROR IS REPORTED AT THE
NEXT LITERAL, NOT AT THE MISSING ONE**, so the message points at the wrong place. ⇒⇒□
⇒⇒□ **⇒⇒□ STRIP BACKTICKS FROM EVERY CSS BLOCK WRITTEN INTO A TEMPLATE LITERAL** — and
the repo's own gate (`scripts/check-backticks.mjs`, 1,532 files) catches it: a planted
backtick was reported as `ProjectLauncher.tsx:98:14 a backtick inside a CSS comment`, and
the gate went green again on restore.

**⇒⇒□ THE PRE-EXISTING GOLDEN-GATE FAILURES ARE NOT THIS DISPATCH'S.**

⇒⇒□ MEASURED: `scripts/check-generator-golden.cjs` reports **121** failures — and it
reports the **same 121** on a clean `origin/main` worktree (`4707821c`). ⇒⇒□ **⇒⇒□ THE
FAILING SETS ARE IDENTICAL, so this dispatch adds ZERO golden failures** — the manifest is
stale, and a stale manifest is a different dispatch's work. ⇒⇒□ ⇒⇒□ **⇒⇒□ THE COMPARISON
IS THE PROOF, NOT THE COUNT.**

**⇒⇒□ THE SPEC HAS TWO VERSION COUNTERS, AND ONLY ONE OF THEM IS BUMPED BY EVERY
RELEASE.**

⇒⇒□ **⇒⇒□ MEASURED: on `origin/main` (`4707821c`) the TITLE read `v3.44.0` and the
highest `v3.N.0` CHANGELOG MARKER was `v3.42.0`** — the two counters DISAGREEED BY TWO.
⇒⇒□ FVC 1393 and FVC 1394 each added a Part and bumped the title only — no changelog
entry — so the changelog fell behind. ⇒⇒□ **⇒⇒□ AND FVC 1385's Part 96 RESTORED THE
AGREEMENT** by adding a `v3.45.0` changelog entry, which is why the two counters read 45
and v3.45.0 together at this dispatch's merge.

⇒⇒□ **⇒⇒□ AND A PART THAT DERIVES ITS VERSION FROM THE CHANGELOG WILL REUSE A VERSION
THAT IS ALREADY SHIPPED.** ⇒⇒□ MEASURED: FVC 1394's Part 95 reads *"the highest `v3.N.0`
marker was **43**"* — and there is **no `v3.43.0` changelog marker on `origin/main` at
all**. ⇒⇒□ **⇒⇒□ THE `43` IT MEASURED IS A PROSE MENTION INSIDE PART 93's OWN TEXT**,
not a changelog entry. ⇒⇒□ **⇒⇒□ A VERSION DERIVED FROM A PROSE MENTION IS A VERSION
DERIVED FROM A SENTENCE.**

⇒⇒□ **⇒⇒□ THE TITLE LINE IS THE COUNTER EVERY RELEASE MOVES**, and a release that adds a
Part WITHOUT a changelog entry leaves the two counters disagreeing. ⇒⇒□ ⇒⇒□ **⇒⇒□ AND THE
RULE FOR THE NEXT PART: DERIVE THE VERSION FROM THE TITLE, AND ADD THE CHANGELOG ENTRY
WITH THE PART** — so the two counters agree for the reader who reads either one.

## Part 98 — The FCr Widget Law: Shared UI Belongs in the Library, Not in an App Folder

**A COMPONENT THAT MORE THAN ONE APP USES BELONGS IN THE FRESHCARDS LIBRARY, AND AN APP CONSUMES IT BY IMPORTING IT. A LOCAL COPY IN AN APP FOLDER IS NOT A SHARED COMPONENT — IT IS A FORK THAT HASN'T ADMITTED IT YET.**

**PART NUMBERING.** MEASURED, at merge time on `origin/main` (`3f06b064`): the file's highest `## Part N` heading was **97** (`## Part 97 - The Fv Collection Card, and the Header That Surrounds It`), so the next free number is **98**; and the highest `v3.N.0` marker was **46**, so the next free version is **v3.47.0**. **THE VERSION AND THE PART ARE INDEPENDENT COUNTERS** (Part 85 §85.7).

**AND THE TWO COUNTERS AGREED BEFORE THIS PART.** MEASURED, on `origin/main` (`3f06b064`), BEFORE this Part was written: the title line read `# VibeCoder Master Spec v3.46.0 (Canonical)` and the highest changelog marker was `v3.46.0` - **the same number, which is the agreement Part 97 restored.** **THIS PART ADDS THE CHANGELOG ENTRY WITH THE PART, so the two counters agree again for the reader who reads either one.**

**THE OPERATOR'S RULING, AND IT IS AN ARCHITECTURE RULING.** MEASURED, on the FVC 1398 record: `TelemetryWidget` and `BulletinWidget` are shared UI that every app should use, so they belong in the FreshCards library and **not on an unmerged VibeCoder branch**. **A FIX IN ONE APP FIXES ONE APP** (Part 96's principle, applied to UI instead of to a model provider). The consumer's only job is to *use* it.

**WHAT WAS ACTUALLY WRONG, MEASURED RATHER THAN ASSUMED.** MEASURED: the two widgets were written on `origin/fvc1021-widgets` (commit `f3433c23`, "FVC 1021 - Home Dashboard widgets") and **never mounted** - that commit's own message says so: *"The widgets are a library, not mounted: nothing imports DashboardCanvas"*. **SO THE COMPONENTS EXISTED AND NOTHING COULD SEE THEM.** A widget that no app imports is not a shared component; it is a branch.
### 98.1 The law, and the one import that expresses it

**A COMPONENT THAT MORE THAN ONE APP USES BELONGS IN `freshcards`. AN APP THAT NEEDS IT IMPORTS IT AND KEEPS NO LOCAL COPY.**

MEASURED, the shipped import, verbatim, at `src/modules/dashboard/src/dashboard/widgets/TelemetryCard.tsx:45`:

```ts
import { TelemetryWidget, type TelemetrySnapshot } from 'freshcards/ui';
```

and at `src/modules/dashboard/src/dashboard/widgets/BulletinCard.tsx:44`:

```ts
import { BulletinWidget, type BulletinRecord } from 'freshcards/ui';
```

**AND THE SUBPATH IS `freshcards/ui`, NOT A DEEP PATH INTO THE PACKAGE.** MEASURED: the package's `exports` map carries ten subpaths - `.`, `./core`, `./ui`, `./mantine`, `./credentials`, `./crypto`, `./adapter`, `./ai`, `./query`, `./package.json` - and `./ui` resolves to `dist/freshcards.ui.es.js` (import) and `dist/freshcards.ui.cjs` (require). **AN APP MUST NOT REACH PAST THE SUBPATH** - a deep import into `freshcards/dist/ui/components/dashboard/TelemetryWidget` bypasses the package's own export surface, and the next release that moves a file breaks the consumer silently.

### 98.2 The widgets are EXPORTED, and that is the measurable half of the law

**THE LAW IS ONLY ENFORCEABLE IF THE LIBRARY ACTUALLY EXPORTS THE THING.** MEASURED, against the PINNED commit `5d80334` (`freshcards` **v2.25.7**, the tag the lockfile resolves): `dist/ui.d.ts` ends with `export * from './ui/faces';`, and `dist/ui/faces.d.ts` carries:

- line **212**: `export { TelemetryWidget, coerceCount, formatCount, } from './components/dashboard/TelemetryWidget';`
- line **213**: `export type { TelemetrySnapshot, TelemetryWidgetProps, } from './components/dashboard/TelemetryWidget';`
- line **214**: `export { BulletinWidget, bulletinTitle, formatBulletinTime, levelColour, DEFAULT_BULLETIN_LIMIT, } from './components/dashboard/BulletinWidget';`
- line **215**: `export type { BulletinLevel, BulletinRecord, BulletinWidgetProps, } from './components/dashboard/BulletinWidget';`

**AND THE FILE PRESENCE ALONE WAS NOT ENOUGH - THE EXPORT WAS THE THING THAT HAD TO BE MEASURED.** MEASURED: the widget SOURCE files were present at the pin (`src/ui/components/dashboard/TelemetryWidget.tsx`, `src/ui/components/dashboard/BulletinWidget.tsx`) and the BUILT `dist/ui/components/dashboard/*.d.ts` existed - and a sweep of `dist/ui.d.ts` for `TelemetryWidget` returned **ZERO** hits. **THE COMPONENT WAS BUILT, THE SUBPATH WAS BUILT, AND THE PUBLIC SURFACE DID NOT CARRY IT.** **A COMPONENT THAT IS NOT EXPORTED FROM THE SUBPATH THE APP IMPORTS IS NOT AVAILABLE TO THE APP, NO MATTER HOW COMPLETE ITS SOURCE IS.**
### 98.3 The HOST/LIBRARY SPLIT, and why the widget fetches nothing

**THE LIBRARY HALF IS PURE. THE HOST HALF KNOWS THE APP. THE SPLIT IS THE CONTRACT, NOT A CONVENIENCE.**

MEASURED, from the library's own source header at the pin: *"WHY THIS DOES NOT FETCH ITSELF: same rule as TelemetryWidget - a widget that fetched for itself would make every dashboard load wait on a network round trip. The records arrive as a prop."*

**SO THE RULE HAS TWO HALVES, AND AN APP THAT BREAKS EITHER HALF HAS BROKEN THE LAW:**

1. **THE LIBRARY HALF FETCHES NOTHING.** It takes props and renders. It knows no route, no token and no payload shape.
2. **THE HOST HALF OWNS TWO THINGS THE LIBRARY CANNOT: WHEN TO LOAD, AND WHAT THE PAYLOAD MEANS.**

MEASURED, the host half at `src/modules/dashboard/src/dashboard/widgets/TelemetryCard.tsx`: the host owns the brain route (`const BRAIN_ROUTE = '/api/agent/fc-in-vc/brain'`), the loader, and the mapping onto the library's shape. **THE HOST IS NOT A COPY OF THE WIDGET - IT IS THE ADAPTER AROUND IT.**

**AND THE ADAPTER MAPS, IT DOES NOT FABRICATE.** MEASURED, the three mappings, and they are the three counters the widget renders:

| counter | source | why |
| --- | --- | --- |
| active agents | `brain.agents` | a **COUNT**, not a list |
| turns processed | `brain.recentTurns` | a list; **COUNTED, not summed** |
| tokens today | **DOES NOT EXIST** | the brain payload has **no token or cost field of any kind** |

**SO THE TOKEN COUNTER RENDERS AN EXPLICIT "NOT REPORTED" STATE INSTEAD OF A ZERO.** MEASURED, from the library's own header: *"A dashboard that shows a confident '0 tokens' is lying about a metric nobody measures; an explicit 'not reported' is the honest reading, and it makes the gap visible to whoever does add the field."* **THIS IS WHY `tokensUsedToday` IS OPTIONAL IN THE INPUT TYPE** - supply it and it renders; omit it and the row says so.

**AND A LOADER THAT THROWS WOULD TAKE THE WHOLE CANVAS WITH IT.** MEASURED: the host's loader catches and returns `undefined`, which is the widget's own "not loaded" state. **THREE STATES, THREE RENDERINGS, NONE OF THEM A CRASH:** `undefined` (not connected), a snapshot with known counters (the counters), and a snapshot whose counters are all unknown (explicit "not reported").

**A BAD PAYLOAD IS NOT A SNAPSHOT OF ZEROES.** MEASURED: the host's mapper returns `undefined` for a body that is not an object, or a brain that is not an object - **not** a snapshot of zeroes. **"NOT LOADED" AND "LOADED BUT ZERO" ARE DIFFERENT STATES, AND THE WIDGET MAKES THE DISTINCTION - SO THE HOST MUST NOT COLLAPSE IT.**
### 98.4 The BEHAVIOUR IS UNCHANGED, and that is what makes it a MOVE rather than a REWRITE

**MOVING A COMPONENT TO A LIBRARY MUST NOT CHANGE WHAT IT RENDERS.** MEASURED, from the library's own header: *"THE BEHAVIOUR IS UNCHANGED. Same component, same DOM, same `data-testid` hooks, same explicit states."*

**SO THE MOVE IS PROVABLE BY THE TEST HOOKS, NOT BY THE SIGHT OF IT.** MEASURED: the widget keeps its `data-testid` hooks, so a test that selects on those hooks passes identically whether the component is imported from `freshcards/ui` or from a local folder. **A TEST THAT SELECTS ON A `data-testid` IS THE ONLY PROOF THAT SURVIVES THE MOVE** - a test that selects on a component's identity, or on a CSS class, or on the module path, is asserting on the move rather than on the behaviour.

**AND THE APP MUST NOT KEEP A LOCAL COPY.** MEASURED, the FVC 1398 change: the commit **ADDED** `src/modules/dashboard/src/dashboard/widgets/TelemetryCard.tsx` (105 lines) and `BulletinCard.tsx` (95 lines) and **DELETED** nothing - because the local widgets never existed on `main`; they lived only on `origin/fvc1021-widgets`. **SO THE MOVE WAS A GAIN, NOT A DEDUPLICATION: 200 lines of HOST code landed, and the LIBRARY halves landed in `freshcards` v2.25.7, and NO local copy of either widget exists in the app.**

**THE FIVE FILES THAT COMMIT TOUCHED, MEASURED:** `package.json` (+2/-1, the `freshcards` pin to `github:avidtech6/freshcards#v2.25.7`), `package-lock.json` (+6/-1), `DashboardCanvas.tsx` (+20, mounting the two card kinds), and the two host adapters. **THE COMMIT CHANGED NO WIDGET BEHAVIOUR - IT MOVED WHERE THE WIDGET LIVES.**

**AND THE COMMIT'S OWN SCOPED SET IS THE EVIDENCE.** MEASURED, from the FVC 1398 commit message: the scoped set (`src/modules/dashboard/src/dashboard/{__tests__,widgets/__tests__}`) is **181 tests, 179 passed, 2 failed - IDENTICAL before and after this change**, and the 2 failures are pre-existing, measured against `freshcards` 2.25.4. **A BEFORE/AFTER COMPARISON OVER THE SAME SCOPED SET IS THE PROOF** (Part 93's law - see §98.6).
### 98.5 THE GATE, and what is still OPEN

**THE ENFORCEMENT MECHANISM IS BUILT FOR THE PIN, AND THE ENFORCEMENT OF THE LAW ACROSS APPS IS DECLARED OPEN.**

MEASURED, the pin gate that exists today: `scripts/check-fcr-pin.mjs` asserts the INSTALLED package is the PINNED one, that `dist/` carries its entries, that the export subpaths resolve, and that `node_modules` is a real directory rather than a symlink. MEASURED: on the pristine checkout it reported **"THE INSTALLED PACKAGE IS NOT THE PINNED ONE: the pin says 'v2.25.7' but node_modules/freshcards is version '2.25.3'"** - and the fix is to INSTALL THE PINNED COMMIT, never to weaken the gate.

**SO THE GATE PROVES THE PIN, NOT THE LAW.** MEASURED: **no gate in this repository asserts that a shared UI component is not duplicated in an app folder.** A sweep for `TelemetryWidget` across `src/` finds the host adapter's import and its comment, and nothing that would fail if an app re-introduced a local copy.

**AND THAT GAP IS DECLARED, NOT PAPERED OVER.** MEASURED: this Part adds NO new gate. **A SPEC THAT PROMISES AN UNBUILT GATE IS WORSE THAN A SPEC THAT DECLARES THE GAP** (Part 86 §86.1's own law) - because the first is believed and the second is not.

**THE STOP CONDITIONS FOR A LATER PART, WRITTEN AS LAW WITH THE ENFORCEMENT DECLARED OPEN:**

- **§98.5.1** A gate that fails when a shared FCr widget is duplicated into an app folder. It must be able to FAIL - a gate that has never gone red is not a gate.
- **§98.5.2** A gate that asserts the app's import is the SUBPATH (`freshcards/ui`), not a deep path into `freshcards/dist/...`.
- **§98.5.3** A gate that asserts the widget is EXPORTED from the subpath the app imports - because MEASURED, the built files existed and the export did not.

**AND THE OPERATOR'S RULE IS ALREADY IN FORCE ON THE REPOSITORY'S OWN BEHAVIOUR, EVEN WITHOUT A GATE.** MEASURED: `src/modules/dashboard/src/dashboard/widgets/fc-face.tsx:45` imports `{ Badge, Card, EmptyState, GalleryView, ListView, Skeleton }` from `freshcards/ui`, and `freshcards-view.tsx:60` imports `{ GalleryView, ListView }` from `freshcards/ui` - **the Desk already takes its faces from the library (Part 92), and the two dashboard widgets now join them.** **THE LAW IS THE EXISTING PRACTICE, WRITTEN DOWN.**
### 98.6 WHAT THIS PART DOES NOT DO, AND WHAT THE OTHER TWO LAWS ALREADY COVER

**THE DISPATCH ASKED FOR THREE LAWS. TWO OF THEM WERE ALREADY LAW, AND THIS PART SAYS SO RATHER THAN RE-WRITING THEM.**

**A - THE PROVIDER GOVERNOR IS ALREADY PART 96.** MEASURED: `## Part 96 - The Provider Call Governor: Every App Inherits the Pacing (FVC 1380)` is present in this file, landed by commit `bb74300e` (*"FVC 1380: Master Spec Part 96 - The Provider Call Governor (v3.44.0 -> v3.45.0)"*). It already states the 750 ms minimum gap, the per-provider queue, the 429 exponential backoff, the 403 cooldown and the bench-don't-wait rule, and it already carries the operator's ruling that the governor lives in FreshCards so every app inherits it.

**AND ITS FIGURES ARE MEASURED AGAINST THE INSTALLED PACKAGE, NOT ASSUMED.** MEASURED, in `node_modules/freshcards/dist/core/ai/providerGovernor.d.ts`: `DEFAULT_MIN_GAP_MS = 750`, `DEFAULT_BACKOFF_BASE_MS = 1000`, `DEFAULT_BACKOFF_MAX_MS = 30000`, `DEFAULT_TOKEN_BUDGET = 8000`, `DEFAULT_TOKEN_WINDOW_MS = 60000`. **THE DISPATCH'S "750ms GAP" IS EXACTLY `DEFAULT_MIN_GAP_MS`.**

**AND THE PUBLIC SURFACE IS MEASURED.** MEASURED, in `node_modules/freshcards/dist/ai.d.ts`: the `freshcards/ai` subpath exports `createProviderGovernor`, `sharedProviderGovernor`, `setSharedProviderGovernor`, and the five `DEFAULT_*` constants, plus the types `ProviderGovernor`, `ProviderState`, `GovernorOptions`, `GovernorEvent`, `GovernedOutcome`, `GovernorProvider`. **THE DISPATCH'S NAME `providerGovernor` IS THE MODULE'S NAME; THE EXPORTED FUNCTIONS ARE `createProviderGovernor` AND `sharedProviderGovernor`. A SPEC THAT NAMES A FUNCTION MUST NAME THE FUNCTION THE PACKAGE ACTUALLY EXPORTS.**

**C - TEST SCOPING AND DEPLOY PROVENANCE ARE ALREADY PARTS 93 AND 95.** MEASURED: `## Part 93 - Test Scoping: the Full Suite Is a Release Activity, Not a Dispatch Activity` (landed by FVC 1393, `d723fa3f`) and `## Part 95 - Deploy Provenance: A Receipt You Cannot Rebuild Is Not a Receipt` (landed by FVC 1394, `3074f6cb`) are both present.

**AND PART 95's GATE IS IMPLEMENTED, NOT JUST SPECIFIED.** MEASURED, `scripts/deploy.sh:170`:

```sh
if ! git merge-base --is-ancestor "$FULL_SHA" origin/main 2>/dev/null; then
```

**AND IT RUNS BEFORE THE WEBROOT IS TOUCHED** (MEASURED, `scripts/deploy.sh` lines 52-100: the gate is hoisted ABOVE the receipt-provenance check, and the failure path prints *"The artefact's receipt names a commit that CANNOT be reproduced ... The webroot was NOT touched."*).

**AND THE GATE HAS BEEN SEEN TO GO RED.** MEASURED, `scripts/deploy-receipt-provenance.test.sh` carries **six cases**, and CASE 1 is exactly the dispatch's shape: `{"build":"<orphan-sha>","branch":"detached@<orphan-sha>","entry":"main-test.js"}` is asserted to fail with the error class **`not-an-ancestor`**. CASE 3 covers a merge that CONTAINS an older commit (must PASS); CASE 4 a receipt with no build sha; CASE 5 a sha that does not exist; CASE 6 a missing receipt file.

**SO THE DISPATCH'S "A DETACHED SHA IS NOT A VALID RECEIPT" IS ALREADY LAW AND ALREADY ENFORCED.** MEASURED: the `detached@` branch is not a special case in the gate - **it is the ordinary shape of a receipt that was stamped from a detached HEAD, and the ordinary ancestry check refuses it**, because a commit that was never merged into `origin/main` is not an ancestor of it.

**THIS PART THEREFORE ADDS ONE LAW - THE FCR WIDGET LAW - AND RECORDS THE OTHER TWO AS ALREADY LANDED.**
### 98.7 THE ARROW-GLYPH DEFECT IN THIS FILE, recorded because it is a REAL DEFECT

**PARTS 89 TO 97 CARRY REPEATED RUNS OF THE MARKER GLYPH IN THEIR PROSE, AND THAT IS CORRUPTION, NOT STYLE.** MEASURED: a sweep of this file for the U+21D2 RIGHTWARDS DOUBLE ARROW glyph returns hits inside Part 89's body, Part 90's body, Part 91's body, Part 92's body, Part 93's body, Part 96's body and Part 97's body.

**THIS IS THE SAME DEGENERATION THAT CORRUPTED AN AGENT'S MEMORY FILE, AND IT IS MEASURED IN BOTH PLACES.** The runs are the shape a writer produces when it emits the same marker repeatedly and the transport folds it - a body that was meant to carry emphasis markers carries a run of identical glyphs instead, and the surrounding prose is still there but the MARKERS ARE NOISE.

**AND THE CORRUPTION IS NOT COSMETIC: IT DEFEATS A TEXT SEARCH.** MEASURED: the gate in §98.5.3 and the checks in §98.6 all had to be written against prose that carries the glyph, which is why they quote the *meaning* rather than running `grep` over the Part.

**SO THIS PART IS WRITTEN WITHOUT THE GLYPH, AND THE RULE IS RECORDED HERE:** **A CANONICAL DOCUMENT MUST NOT CARRY REPEATED RUNS OF A MARKER GLYPH. IF A PART'S BODY CONTAINS A RUN OF THREE OR MORE IDENTICAL MARKERS, THE MARKERS ARE CORRUPTION AND MUST BE REMOVED - the prose around them is the content.** **THE REPAIR IS MECHANICAL AND LOCAL:** replace the run with a single space, or with the intended emphasis marker, and do not retype the surrounding prose.

**AND THE DEFECT IS REPORTED, NOT SILENTLY FIXED IN A PASSING DISPATCH.** MEASURED: Parts 89-97 were landed by other lanes, and a Part that rewrites another lane's prose is writing their history. **THE CORRECTION BELONGS TO A DISPATCH THAT SAYS IT IS CORRECTING THE GLYPH RUNS.** This Part does not touch them; it names the defect, names the rule, and writes its own body clean.


## Part 99 — The One-Way Glass Rule: The Shell Reaches In, the Canvas Never Reaches Out

**Part 99 is the COMMUNICATION-DIRECTION law. It does not replace Part 86; it stands beside it.** MEASURED: Part 86 §86.2 already establishes the CONTAINMENT half — the canvas is its own stacking context, the panel reservation is a grid track, and a generated page must not mutate the document root. **Part 86 says WHERE THE CANVAS'S CONTENT MAY PAINT. Part 99 says WHICH WAY INFORMATION MAY FLOW.** A Canvas that is perfectly contained can still leak state upward, and a Canvas that is allowed to answer questions can still be contained. **THE TWO RULES ARE ORTHOGONAL, AND CONFLATING THEM IS HOW A "GLASS" RULE COMES TO MANDATE THE WRONG ARCHITECTURE.**

### 99.1 The law

1. **THE CANVAS IS ONE-WAY GLASS.** The Canvas — whether it is the Live surface or the Preview surface — can NEVER leak CSS, HTML, or application state into the VibeCoder Shell. The direction of travel is Shell to Canvas, and only Shell to Canvas.
2. **THE SHELL REACHES INTO THE CANVAS TO EDIT IT.** The Shell's editing affordances — the Selection Loop, the Properties panel, the Layers panel — read and write the Canvas's content through the canonical editing path. The Shell's authority over the Canvas is total and deliberate.
3. **THE CANVAS RESPONDS TO THE SHELL. THE SHELL DOES NOT RESPOND TO THE CANVAS.** The Canvas answers a Shell-initiated question. The Shell never asks a Canvas-initiated question and acts on the answer.
4. **NO CANVAS-INITIATED EVENT, MESSAGE, CALLBACK, OR DOM MUTATION MAY CHANGE THE SHELL'S STATE.** The theme, the skin, the active project, the panel open/closed set, the selection, the viewport and the route are the Shell's own state surfaces, and the Canvas has no path to any of them.
5. **THE CANVAS'S CONTENT IS CONFINED TO THE CANVAS SLOT.** This half is Part 86 §86.2 and it is not restated here; see §99.4.

### 99.2 MEASURED — THE CANVAS IS NOT A SEPARATE DOCUMENT, AND THAT IS WHY THE RULE IS NEEDED

**A "one-way glass" built on an iframe would be safe by construction, and this Canvas is NOT an iframe.** MEASURED: the Canvas slot is `src/shell/Shell.tsx:89-93` — `<div className="fv-shell-canvas" data-fv-canvas-slot="shell">` — and the project's own content is mounted into `#fv-main-canvas` **in the same document**. MEASURED: a sweep of `src/` for `postMessage` returns **zero functional hits**; the hits are all comments reading *"No iframe. No postMessage. No pact edits."* — the codebase has already written down that there is no frame boundary to rely on.

**⇒ THE CONTAINMENT IS CARRIED BY THE STACKING CONTEXT, NOT BY A DOCUMENT BOUNDARY.** MEASURED (`src/shell/Shell.tsx:1402-1417`): the canvas rule sets `z-index: 0` with the code's own comment *"THE CANVAS IS ITS OWN STACKING CONTEXT. Everything inside it is painted inside it, and nothing inside it can paint over the chrome, which lives in the Shell's own context above it"*, plus `overflow-x: hidden; overflow-y: auto`.

**⇒ A CANVAS THAT IS MOUNTED IN THE SHELL'S DOCUMENT CAN LEAK CSS WITHOUT ANY MALICE.** A stylesheet a project's recipe carries, a `<style>` a widget injects, a `document.documentElement` write — **each is one line away from the Shell's own DOM, because there is no frame between them.** This is precisely why the direction of travel must be a rule and not a hope.

### 99.3 MEASURED — THE SHELL'S REACH INTO THE CANVAS, AND THE ONE PATH IT USES

**THE SHELL REACHES IN, AND IT REACHES IN EXACTLY ONE WAY.** MEASURED: the Selection Loop (`src/shell/CanvasSelectionLoop.tsx`, FVC 1355) is mounted inside the canvas slot and layers over what is already there. MEASURED: the loop is built on **the Canvas's own rendered DOM**, not on a second model — it measures the boxes the Canvas already draws and hangs its tags on them. MEASURED: the loop calls the **same canonical setter** as every other selection path — `useEditorSelection().selectNode()` delegates to `setActiveRegionId`, and the Properties panel reads `sel.activeRegionId`.

**⇒ THE SELECTION PATH IS SINGLE. THE DIRECTION IS ONE-WAY.**

**AND THE CANVAS MAY NOT OPEN A SECOND SELECTION PATH.** MEASURED: `src/agent/active-context.ts` excludes `vibecoder-self` from the build-target chat body because *"it is the SPA itself"* — the Shell is not a build target, and the Shell is not a Canvas. **⇒ THE SHELL AND THE CANVAS ARE NOT PEERS, AND A RULE THAT TREATS THEM AS PEERS WILL BE VIOLATED BY THE FIRST ONE THAT LEARNS THE OTHER'S API.**

### 99.4 THE RELATIONSHIP TO PART 86, STATED PRECISELY

**PART 86 §86.2 IS THE CONTAINMENT HALF AND IS NOT WEAKENED BY THIS PART.** MEASURED: Part 86 §86.2 already records that the canvas is its own stacking context, that the panel reservation is a **grid track** on `.fv-shell-body` — `grid-template-columns: var(--fv-shell-left-column, 0px) minmax(0, 1fr) var(--fv-shell-right-column, …)` — and that a generated page must not write `document.body` or `document.documentElement`.

| | Part 86 §86.2 | Part 99 |
| --- | --- | --- |
| **Question** | Where may the Canvas's content PAINT? | In which direction may INFORMATION flow? |
| **Mechanism** | A stacking context, a grid track, an overflow clip | The canonical editing path, and the absence of any Canvas-initiated path |
| **Violation looks like** | A generated page out-painting or re-styling the chrome | A Canvas-initiated event, message or DOM write changing the Shell's state |
| **Enforcement** | CSS structure | Call-site discipline, and a rule the Validator cannot yet check |

**⇒ BOTH ARE REQUIRED. A Canvas that is contained but can report upward is a Canvas the Shell will eventually trust. A Canvas that cannot report upward but is not contained is a Canvas that eats the chrome. NEITHER HALF IS OPTIONAL.**

### 99.5 WHAT THIS PART DOES NOT DO

**IT DOES NOT CREATE A NEW TRANSPORT.** MEASURED: `postMessage` appears **zero** times as functional code in `src/`. Part 99 does not introduce one. The Shell's reach into the Canvas is a **DOM reach in the same document**, and the Canvas's non-reach is the **absence of a call in the other direction**.

**IT DOES NOT PROMISE A GATE.** A DOM-tree check of the Canvas's reachability does not exist, and this Part does not claim it does. MEASURED: Part 86 §86.4 already records the Validator's coverage as **OPEN**, and the enforcement mechanism for Part 99 is **OPEN** on the same footing. **⇒ A SPEC THAT PROMISES AN UNBUILT GATE IS WORSE THAN A SPEC THAT DECLARES THE GAP** (Part 86 §86.4).

**IT DOES NOT CHANGE THE CANVAS'S CONTENT MODEL.** The Canvas renders the project's recipe. That is unchanged.

## Part 100 — The Panel Paradigms: Where a Panel Lives, by Form Factor

**Part 100 is a LAYOUT law. It answers "where does this panel live" and it does not answer "how does this panel behave".**

### 100.1 DESKTOP

1. **ALL PANELS ARE SIDE PANELS OR FLOATING WINDOWS.** On the desktop, a panel is either **docked** (a side panel, occupying a reserved column) or **floating** (a free window over the canvas). These are the only two desktop arrangements.
2. **NO BOTTOM SHEETS ON THE DESKTOP, WITH ONE EXCEPTION.** The only bottom-anchored surface on the desktop is **VibeChat's history view**. Every other panel — the Project Panel, the Assets Panel, the Layers Panel, the Properties Panel, the Deck, the Panels Switcher — is a side panel or a floating window.
3. **A BOTTOM SHEET IS A MOBILE ARRANGEMENT.** It is not a desktop variant of a panel; it is what a panel becomes when there is no room beside it.

**MEASURED — THE PM2 ENGINE ALREADY EXPRESSES EXACTLY TWO DESKTOP ARRANGEMENTS, AND IT IS THE AUTHORITY.** MEASURED (`src/modules/panel-shell/src/panel-manager/panel-manager.js`): the manager's own header reads *"Panel Manager v2 — dock-based system"*, and its API is `mgr.activate(id)`, `mgr.collapse(id)`, `mgr.detach(id)`, `mgr.dock(id, edge)`, `mgr.list()`. **⇒ THE ENGINE HAS A DOCK AND A FLOAT. IT HAS NO SHEET. THE SPEC AND THE ENGINE AGREE, AND THE SPEC IS RECORDING THE ENGINE'S CONTRACT RATHER THAN ASPIRING PAST IT.**

### 100.2 MOBILE

1. **THE PROJECT PANEL OPENS FROM THE LEFT.** It is a left-edge sheet.
2. **THE HAMBURGER MENU OPENS FROM THE RIGHT.** It is a right-edge sheet.
3. **VIBECHAT AND THE PANELS SWITCHER OPEN AS BOTTOM SHEETS.** Both are bottom-anchored.
4. **THE SIDES ARE NOT INTERCHANGEABLE.** A surface that opens from the left on the desktop opens from the left on the mobile too. **⇒ THE ARRANGEMENT IS A PROPERTY OF THE SURFACE, NOT OF THE VIEWPORT** — a surface that changes sides with the viewport is a surface whose position the operator must learn twice.

**MEASURED — THE DESKTOP PANEL RESERVATION IS A GRID TRACK, AND THE MOBILE SHEET IS NOT.** MEASURED (Part 86 §86.2): `.fv-shell-body` is `display: grid` with `grid-template-columns: var(--fv-shell-left-column, 0px) minmax(0, 1fr) var(--fv-shell-right-column, …)`. **⇒ ON THE DESKTOP, A SIDE PANEL RESERVES ITS SPACE BY BEING A GRID COLUMN — THE CANVAS IS NOT OVERLAPPED, IT IS SIZED.** MEASURED: the mobile VibeChat sheet is `position: fixed; inset: auto 0 0; width: 100%` with a height fraction per detent — **a bottom sheet has no grid track, so it covers.** **⇒ THE TWO ARRANGEMENTS ARE NOT THE SAME ARRANGEMENT WITH DIFFERENT CSS; THEY ARE DIFFERENT RESERVATION STRATEGIES, AND A PANEL THAT MOVES BETWEEN THEM MUST CHANGE HOW IT RESERVES SPACE, NOT ONLY WHERE IT SITS.**

### 100.3 THE ONE EXCEPTION, STATED PRECISELY

**VIBECHAT'S HISTORY VIEW IS THE ONLY DESKTOP BOTTOM SURFACE, AND IT IS A HISTORY VIEW — NOT A CHAT COMPOSER.** MEASURED: the v2 VibeChat's desktop rule is the unconditional base rule — `position: fixed; inset: auto 0 0; width: 100%` — with the detents as height fractions of the viewport (`bar` 0.16, `strip` 0.5, `full` 0.92), and the mobile media query at `max-width: 767.98px` overrides only the radii, the shadows and the detent fractions. **⇒ THE DESKTOP VIBECHAT IS TODAY A FULL-WIDTH BOTTOM BAR, AND THIS PART RECORDS THAT AS THE ONE PERMITTED DESKTOP EXCEPTION — SEE PART 104 §104.2 FOR THE MEASURED DEFECT AND THE CORRECTION IN FLIGHT.**

## Part 101 — The Handle Rules: What a Handle Is, When It Is Hidden, and Which Way a Swipe Goes

### 101.1 SIDE HANDLES

1. **A SIDE HANDLE HIDES COMPLETELY WHILE ITS PANEL IS OPEN.** The Assets Handle hides when the Assets Panel is open. The Deck Handle hides when the Deck is open. **Completely** — not narrowed, not faded, not made non-interactive. The handle and its label are both gone.
2. **A HANDLE THAT HIDES IS NOT LOST.** The panel's own chrome carries the close affordance. **⇒ THE HANDLE IS AN ENTRY POINT, NOT A CONTROL SURFACE** — and a control that is hidden while its target is visible has done its job.

### 101.2 BOTTOM HANDLES

1. **THE BOTTOM HANDLES ARE PERMANENT.** The VibeChat Handle and the Panels Handle are always present. They do not hide on a state change, on a hover, or on a sheet opening.
2. **THE BOTTOM HANDLES SIT ABOVE SHEETS IN THE STACKING ORDER.** **⇒ A BOTTOM HANDLE'S Z-INDEX IS ABOVE THE SHEET'S, ALWAYS.** MEASURED: the bottom handles are `z-index: var(--fv-z-handle, 300)` and the VibeChat sheet is `z-index: var(--fv-z-panel)` — **the same tier by default, and the same tier is a TIE, and a tie is decided by DOM order, which the sheet may win.** The rule is therefore stated as an ORDER, not a number, because a number drifts.
3. **A SHEET MUST PAD ITS BOTTOM SO THE INPUT FIELD CLEARS THE HANDLES.** The padding is on the **content**, not on the sheet. MEASURED (FVC 1292, `src/vibechat/VibeChat.tsx`): the content carries `padding-bottom: var(--fv-handle-bottom-clearance, 24px)` with the code's own reason — *"IT IS A PAD ON THE CONTENT, NOT ON THE PANEL. The panel is 'position: fixed' with 'inset: auto 0 0', so padding the PANEL would push the content out of the viewport's bottom edge."* **⇒ THE PAD IS ON THE CONTENT BECAUSE THE PANEL'S BOX IS AT THE VIEWPORT'S EDGE.**

### 101.3 SWIPE DIRECTION

1. **SWIPE INWARDS OR UPWARDS OPENS OR CYCLES.** A swipe toward the screen's interior, or upward, opens the target surface — or advances it to its next detent.
2. **SWIPE OUTWARDS OR DOWNWARDS CLOSES.** A swipe away from the screen's interior, or downward, closes the target surface.
3. **THE DIRECTION IS THE SAME ON EVERY SURFACE AND EVERY FORM FACTOR.** A gesture that opens on the desktop must not close on the mobile.

**MEASURED — THE MOBILE SHEET'S SWIPE-DISMISS IS THE MEASURED INSTANTIATION OF THIS RULE, AND IT CARRIES A HAZARD THIS PART MUST RECORD.** MEASURED (FVC 1392, `src/shell/Handle.tsx` and `src/vibechat/VibeChat.tsx`): the sheet's input bar is a **drag surface**, so a pointerdown on the TEXTAREA starts a drag; and FVC 1392's measured defect was that *"THE SHEET CLOSED THE MOMENT YOU TAPPED THE CHAT INPUT"* — because `closestDetent(58/915)` returned `bar` and the release called `onOpenChange(false)`. **⇒ A TAP IS NOT A SWIPE, AND A DRAG SURFACE THAT WRAPS A TEXT FIELD MUST NOT READ A TAP AS A DISMISSAL.** The fix is the `drag.moved` guard: a pointer that never travelled did not move the sheet, and its release must not be read as a dismissal.

### 101.4 THE HANDLE'S SHORT AXIS HAS A FLOOR, AND THE PEEK IS A MODE

**THE SHORT AXIS IS AT LEAST 24px, AND IT IS A FLOOR, NOT A TARGET.** MEASURED (FVC 1243, `src/shell/Handle.tsx`): the handle's width along its short axis is `var(--fv-handle-width, 24px)`, the token is `--fv-handle-width: 24px` in `src/styles/tokens.css`, and the component's fallback **must match the token** — *"a fallback is only reached when the custom property is UNDEFINED, so a fallback that disagrees with the token file is DEAD CODE."*

**⇒ AND A HANDLE MAY PEEK.** MEASURED (FVC 1410): the handle carries `--fv-handle-peek-width: 18px`, `--fv-handle-peek-duration: 220ms` and `--fv-handle-peek-easing`, plus a `.fv-handle-peek` rule. **⇒ A PEEK IS A NARROWER STATE THE HANDLE MAY BE DRAGGED INTO, AND THE PEEK IS NOT A VIOLATION OF THE 24px FLOOR — THE FLOOR IS THE HANDLE'S RESTING SIZE.** A handle that is permanently 18px is a violation; a handle that can be peeked to 18px and returns is a mode.

**⇒ AND THE LABEL IS NOT OPTIONAL.** MEASURED: every handle renders a real text label in the DOM (not a CSS `::after` content string), the label runs along the handle's own long axis — `writing-mode: vertical-rl` for a side handle, `horizontal-tb` for a bottom one — and the label is the theme's **primary text**, not the strip's colour, because the four handle colours are all mid-to-bright and a label in its own strip's colour is invisible on it.

## Part 102 — The Panel Chrome: Sleek Means Fewer Controls

### 102.1 DOCKED PANELS HAVE NO WINDOW HEADER

1. **A DOCKED PANEL HAS NO WINDOW HEADER. IT HAS A TITLE BAR.** The Minimize, Maximize and Close controls belong to a **floating window**. A docked panel is a column of the Shell's own grid, and it carries a title — nothing more.
2. **⇒ A DOCKED PANEL MUST NOT RENDER MINIMIZE, MAXIMIZE OR CLOSE.** MEASURED: the PM2 engine's own vocabulary is `activate(id)`, `collapse(id)`, `detach(id)`, `dock(id, edge)`, `list()` — **there is no `minimize` and no `maximize` on a docked panel, because a docked panel has nothing to minimize into and nothing to maximize out of.** The controls that appear on a floating window are the ones that mean something there.

### 102.2 FLOATING PANELS CARRY THE FULL HEADER

1. **A FLOATING PANEL HAS THE FULL HEADER: MINIMIZE, MAXIMIZE, CLOSE.** Each is a real control with a real effect, and **a control with no effect is DEAD** (Part 70).
2. **A FLOATING PANEL MAY BE DRAGGED BY ITS HEADER, NEVER BY ITS BODY.** MEASURED (Part 99's sibling, the Shell Recipe `rec_shell_001` §D1): *"Floating panels are dragged by their headers, never by their body. Dragging a floating panel to an edge docks the panel; dragging it away from the edge breaks it free and it becomes a floating panel again."*

### 102.3 THE DECK IS STRICTLY THIN AND NARROW

1. **THE DECK HAS A HARD MAX-WIDTH.** It is a **launcher**, not a content panel. It opens things; it does not hold them.
2. **⇒ THE DECK'S WIDTH IS ITS OWN TOKEN, NOT THE SHARED PANEL WIDTH.** MEASURED: today `--fv-deck-outer-width: var(--fv-panel-width)` (`src/styles/tokens.css:444`), and `--fv-panel-width` is `min(250px, 78vw, …)`. **⇒ THE DECK IS TODAY AS WIDE AS THE ASSETS PANEL, AND THIS PART MAKES IT A DIFFERENT, NARROWER SURFACE.** A launcher that is as wide as a content panel is a content panel with an extra step.

### 102.4 THE ASSETS PANEL IS RESIZABLE AND RE-FLOWS

1. **THE ASSETS PANEL IS RESIZABLE BY THE OPERATOR.** MEASURED: the panel's width is `var(--fv-assets-user-width, var(--fv-panel-width))` with `min-width: var(--fv-assets-min-width, 180px)` and `max-width: min(90vw, 520px)`, and the custom property is set on the element so it beats the stylesheet without a second rule (FVC 1230).
2. **⇒ AND IT RE-FLOWS FROM ONE COLUMN TO TWO TO THREE AS IT WIDENS.** The panel's interior is a **CSS grid** whose column count follows the panel's own width. **⇒ THE PANEL'S CONTENT DENSITY IS A FUNCTION OF THE PANEL'S WIDTH**, and the operator's drag changes the density as well as the size. **A PANEL THAT SCROLLS A FIXED SINGLE COLUMN AT EVERY WIDTH IS A PANEL THAT WAS NEVER RESIZED — IT WAS ONLY STRETCHED.**

**MEASURED — THE EXISTING PANEL ALREADY USES THE PATTERN THIS PART MANDATES, IN A DIFFERENT PLACE.** MEASURED (FVC 1389, per the Project Launcher's own documentation): *"A FIXED `grid-template-rows` CANNOT do this — it gives every card in a row the height of the tallest, so expanding one card leaves a hole and pushes the whole row down."* The Project Launcher solved it with a **CSS multi-column** container whose `column-count` follows the child count. **⇒ THE ASSETS PANEL IS THE SAME PROBLEM IN A DIFFERENT AXIS — WIDTH INSTEAD OF COUNT — AND THE GRID IS THE ANSWER.**

## Part 103 — The VibeChat Input Bar: A State Machine, Not a Fixed Position

**THE INPUT BAR IS THE ONE PIECE OF VIBECHAT THAT MOVES, AND ITS MOVEMENT IS THE WHOLE INTERACTION MODEL.**

### 103.1 THE THREE STATES

1. **DEFAULT — A GLOBAL INPUT BAR AT THE BOTTOM.** The operator's composer is a bar across the bottom of the Shell. Answers appear in a **strip above it**. The operator is typing into a global affordance, not into a panel.
2. **HISTORY VIEW (FLOATING) — THE FULL VIBECHAT PANEL, WITH NO INPUT BAR INSIDE IT.** The floating history shows the conversation, the **thread rail** and the **agent rail**. **⇒ THERE IS NO INPUT BAR INSIDE THE HISTORY VIEW.** A second composer in a floating panel beside a global composer is two composers, and the operator cannot tell which one their keystrokes will reach.
3. **DOCKED VIEW — THE INPUT BAR LEAVES THE BOTTOM AND APPEARS INSIDE THE DOCKED VIBECHAT PANEL.** **⇒ IT RETURNS TO THE BOTTOM ONLY WHEN THE PANEL IS RE-FLOATED.** The input bar moves **with** the panel it belongs to, and the global bar is present only when the panel is not.

**⇒ THE INVARIANT: THERE IS EXACTLY ONE INPUT BAR, AND IT IS ALWAYS VISIBLE.** Every state relocates it; no state duplicates it and no state removes it.

### 103.2 WHY THE BAR MOVES, AND WHAT IT FORBIDS

**THE INPUT BAR BELONGS TO THE CONVERSATION, AND THE CONVERSATION HAS A LOCATION.** In the default state the conversation is the Shell's; in the docked state it is the panel's; in the history state it is the floating window's. **⇒ THE BAR IS WHERE THE CONVERSATION IS.** A bar that stayed at the bottom while the conversation floated away would be a bar whose subject is ambiguous, and a bar duplicated in two places is a bar whose subject is a guess.

**⇒ AND A DOCKED PANEL MAY NOT HIDE THE GLOBAL BAR BY ACCIDENT.** A docked panel that covers the bottom of the screen while the global bar is still there is two composers and a collision. **⇒ THE BAR'S VISIBILITY IS A FUNCTION OF THE VIBECHAT PANEL'S PRESENCE, AND THE TWO ARE ONE STATE, NOT TWO.**

### 103.3 MEASURED — THE RAILS ARE NOT YET SEPARATE SURFACES

**THE AGENT RAIL EXISTS IN THE v2 SHELL; THE THREAD RAIL DOES NOT.** MEASURED: `src/vibechat/VibeChat.tsx` carries `.fv-vibechat-content > .fv-agent-rail` at `flex: 0 0 var(--fv-agent-rail-width, 12rem)`. The **only** thread rail in the repository is `src/modules/cinema-editor/src/editor/vibechat/components/VibeChatRail.tsx` (r235a, legacy `vc-rail` / `data-vc-rail="1"`), and it is mounted **only** by the legacy `VibeChatUnified.tsx` — a path the v2 Shell does not mount.

**⇒ THE THREAD RAIL IS A NEW SURFACE, NOT A REWIRE, AND THIS PART DOES NOT CLAUSE IT EXISTS.**

**⇒ AND THE AGENT RAIL IS A COLUMN BESIDE THE MESSAGE LIST TODAY.** MEASURED: it is `flex: 0 0 12rem` **beside** the messages, and the layout is a row. **⇒ THIS PART CHANGES THAT: THE RAILS BECOME SURFACES THAT OPEN FROM THEIR OWN HANDLES, WHICH IS A DIFFERENT ARRANGEMENT FROM A FIXED COLUMN.** See Part 104.

## Part 104 — The VibeChat Rails: Two Handles, Two Surfaces, Never Both

### 104.1 THE TWO RAILS

1. **THE THREAD RAIL OPENS FROM THE THREAD HANDLE.** It shows the operator's **conversation threads** — the list of conversations, and which one is active.
2. **THE AGENT RAIL OPENS FROM THE AGENT HANDLE.** It shows **agent cards with live telemetry** — the agent's **name**, its **current task**, and its **tags**.
3. **THE TWO RAILS ARE MUTUALLY EXCLUSIVE.** Opening one closes the other. **⇒ THEY ARE TWO STATES OF ONE SURFACE, NOT TWO SURFACES.** Two simultaneously open rails would split the operator's attention across two lists that answer two different questions, and the answer to "which am I looking at?" would be ambiguous.

### 104.2 CLICKING AN AGENT CARD OPENS ITS TECHNICAL VIEW, AND CLOSES THE RAIL

**CLICKING AN AGENT CARD OPENS THE TECHNICAL VIEW OF ITS SUB-TURNS, AND THE RAIL CLOSES SO THE CONVERSATION STAYS VISIBLE.** The sub-turns are the detail; the conversation is the context. **⇒ THE RAIL IS A NAVIGATOR, AND A NAVIGATOR THAT STAYS OPEN COVERS THE THING IT NAVIGATES TO.**

**⇒ AND THE RAIL IS NOT A MODAL.** It is a surface that yields. The operator clicks a card, the rail closes, the technical view opens, and the conversation behind it is still there. **A RAIL THAT MODALS THE CONVERSATION OUT OF VIEW HAS CHANGED ITS JOB FROM NAVIGATOR TO GATE.**

### 104.3 MEASURED — THE DESKTOP VIBECHAT'S CURRENT GEOMETRY, AND THE CORRECTION IN FLIGHT

**MEASURED, on live production, 2026-11-01 (Chromium 1600x1000):** the desktop VibeChat root measured `position: fixed; inset: auto 0 0; width: 100%` and a bounding box of **x=0, y=839, w=1600, h=161** — a full-width bottom bar, not a sidebar. **⇒ THE DESKTOP VIBECHAT IS THE MOBILE SHEET'S GEOMETRY APPLIED TO A DESKTOP, AND THERE IS NO DESKTOP-SIDEBAR RULE IN THE SHIPPED STYLESHEET.**

**MEASURED: the base rule is UNCONDITIONAL** — `src/vibechat/VibeChat.tsx:273` — and the `@media (max-width: 767.98px)` block overrides only the radii, the shadows and the detent fractions. **⇒ THERE WAS NO DESKTOP RULE AT ALL.**

**⇒ THIS PART RECORDS THE DEFECT AND THE TARGET SHAPE, AND DOES NOT CLAIM THE CORRECTION HAS LANDED.** The correction — a desktop media query that docks the panel on the right, below the header, with the detents as WIDTHS and the drag resizing the width — is recorded in FVC 1408's dispatch and is in flight. **⇒ A SPEC THAT PROMISES AN UNBUILT CORRECTION IS WORSE THAN A SPEC THAT DECLARES THE GAP.** This Part declares the gap and names the target shape.

**⇒ AND THE TARGET SHAPE IS THE ASSETS PANEL'S SHAPE.** MEASURED: the canonical thin docked sidebar is `src/modules/assets/src/Assets.tsx` — `position: fixed`, `inset-block-start: var(--fv-header-height, 56px)`, `height: calc(100dvh - var(--fv-header-height, 56px))`, `box-sizing: border-box`, and the shared panel-width token. **⇒ A PANEL STARTS BELOW THE HEADER. A PANEL AT `inset: 0` SLIDES UNDER THE HEADER AND ITS TITLE IS CLIPPED.**

### 104.4 MEASURED — THE TWO RAILS' MUTUAL EXCLUSIVITY HAS NO MECHANISM YET

**MEASURED: there is no thread rail in the v2 shell, and the agent rail is a fixed column inside the message list rather than a surface that opens from a handle.** **⇒ THE MUTUAL EXCLUSIVITY THIS PART REQUIRES IS A LAW WITHOUT AN IMPLEMENTATION, AND THE IMPLEMENTATION IS NAMED AS FUTURE WORK — NOT AS A CAPABILITY THAT EXISTS.**

## Part 105 — The Recipe Audit Note: Which of These Parts Are JSON, Which Are Prose, and Which Are Factory Exceptions

**THIS PART IS A NOTE, NOT A LAW. It exists so that the NEXT agent does not guess, and so that the gap is visible rather than assumed.**

### 105.1 WHAT FVC 1414 MEASURED, AND WHAT IT MEANS FOR THESE PARTS

**MEASURED by FVC 1414 (2026-11-01, READ-ONLY, against `52b50f02`):**

| Surface | Recipe form, MEASURED | Consequence for these Parts |
| --- | --- | --- |
| **Header** | **JSON Recipe** — `src/shell/fragments/header/recipe-book/recipe.json` (4,855 B) + `codex.json` (5,537 B), and `src/shell/fragments/header/Header.tsx` is a **GENERATED FILE** | The Header is already on the Recipe path. **Parts 100, 101 and 102 apply to it directly.** |
| **Handle** | **Prose only** — `src/shell/fragments/handle/recipe-book/` has `recipe.md`, `codex.md`, `rules.md` and `trace-atlas/atlas.json`, and **NO `recipe.json` and NO `codex.json`** | The Handle is **hand-written**. **MEASURED: the Generator run against its recipe-book dies with `ENOENT … recipe.json`; against the Header's it emits 83,437 bytes.** |
| **Shell** | **JSON Recipe IN THE FC BRAIN** — `rec_shell_001` (8,674 chars) in the live `vibecoder-self` tree (42 nodes), with `cod_shell_001` and `rul_shell_001` | The Shell's composition law exists, **but the Generator cannot execute it** — MEASURED: `grep "import:" react-emitter.cjs` returns **zero hits**, so `<import: frag_header />` is not a parseable construct. |

### 105.2 THE THREE CLASSES, AND WHERE EACH OF THESE PARTS FALLS

**CLASS 1 — JSON RECIPE (the Generator can build it).** The Header. Its recipe-book is complete and its artefact is generated.

**CLASS 2 — MARKDOWN RECIPE (the prose is the contract; the JSON is missing).** The Handle, the Rail and the Stencil fragments — `src/shell/fragments/handle/`, `…/rail/` and `…/stencil/` all carry prose-only recipe-books. **MEASURED: the Generator's CLI reads `recipe.json` and `codex.json` (`src/modules/generator/src/generate-react.cjs:831-832`), so a prose-only book is a book the Generator cannot open.**

**CLASS 3 — FACTORY EXCEPTION (hand-written, and it must be harvested back).** The Handle's `src/shell/Handle.tsx` — MEASURED: **zero** occurrences of `GENERATED` or `DO NOT EDIT`. **Master Spec Part 80 §80.2 is the law that governs this class:** *"When code is manually authored via Rule 6 Exception 3, it must be harvested back into a Recipe so the Generator can build it in the future."* **⇒ A Factory Exception is a DEBT WITH A DEADLINE, NOT A PERMISSION.**

### 105.3 WHERE EACH OF THESE PARTS LANDS

| Part | Law about | Recipe class it lands on |
| --- | --- | --- |
| **Part 99** | The One-Way Glass | **CLASS 2/3 — the Canvas slot and the Selection Loop.** The Canvas slot is `src/shell/Shell.tsx` (hand-written); the Shell's own Recipe `rec_shell_001` already carries the slot in its structure. |
| **Part 100** | The Panel Paradigms | **CLASS 3 — the PM2 engine.** MEASURED: `src/modules/panel-shell/src/panel-manager/panel-manager.js` is hand-written, and `src/modules/panel-shell/recipe-book/` is prose-only. |
| **Part 101** | The Handle Rules | **CLASS 2 — the Handle's recipe-book is prose-only.** MEASURED: it carries the FVC 1243 label law and the 24px floor in `recipe.md` and `codex.md`, and the JSON pair is absent. |
| **Part 102** | The Panel Chrome | **CLASS 1 for the Deck and the Assets Panel** (both have `recipe.json`), **CLASS 3 for the chrome controls themselves.** |
| **Part 103** | The VibeChat Input Bar | **CLASS 3 — `src/vibechat/VibeChat.tsx` is hand-written**; `src/modules/vibechat/recipe-book/` is prose-only. |
| **Part 104** | The VibeChat Rails | **CLASS 3 — the Agent Rail is `src/vibechat/AgentRail.tsx`, hand-written.** The Thread Rail is **NEW WORK** — it exists only in the legacy `cinema-editor` path. |

### 105.4 THE TWO FACTS THAT MAKE THIS NOTE URGENT

**THE BRAIN'S HANDLE RECIPE IS STALE, AND A LEVERS SESSION WOULD SHIP THE REGRESSION.** MEASURED: the live `rec_handle_001` (605 chars) specifies `width var(--fv-handle-width, 16px)` and carries **no label element**, while the checked-in prose requires 24px and a label (FVC 1243). **⇒ Part 101's law cannot be enforced by a Generator reading the brain's Handle recipe, because the brain's Handle recipe is the pre-1243 handle.**

**THE ATLAS FILES CLAIM A FLAG THAT DOES NOT EXIST.** MEASURED: `frag_handle_001` and `frag_header_001` both record `"state": "implemented-behind-flag"` with `"?shell=v2 or localStorage.fv_shell_v2=true"` and *"legacy is the default"* — and `fv_shell_v2` occurs **zero** times in `src/`, while `src/shell/Shell.tsx:4` imports the **generated** Header directly. **⇒ THE GENERATED HEADER IS THE DEFAULT, AND THE ATLAS SAYS THE OPPOSITE.**

**⇒ AND THE TOOL THAT WOULD CLOSE THE WHOLE GAP DOES NOT EXIST.** MEASURED: Part 80 §80.1 names `tools/harvest-react.cjs`, and **no `harvest*` file exists anywhere in the repository**. **⇒ UNTIL IT EXISTS, EVERY CLASS-3 SURFACE NEEDS A HAND-WRITTEN RECIPE, AND THE PARTS IN THIS BLOCK CANNOT BE ENFORCED BY GENERATION.**

### 105.5 WHAT THE GENERATOR CANNOT YET EMIT, MEASURED

**THE VOCABULARY HAS NO `Handle`, NO `Dock` AND NO `Shell`.** MEASURED: `WIDGET_VOCABULARY` (`src/modules/generator/src/emitters/react-emitter.cjs:2113`) is **26 names** — MenuIcon, Logo, WorkspaceTab, PanelControlsGroup, ThemeToggle, BuildBadge, HomeIcon, ProjectSelector, MenuGroup, MenuItem, ModeToggle, ThemeSelector, SkinSelector, SettingsIcon, DeckSurface, HamburgerMenu, Page, Heading, Paragraph, Button, Hero, GlassPanel, CinemaBackground, ProjectGrid, Chat, Layers — and `PRIMITIVES` (`:1824`) is **8**: text, image, box, click, state, repeat, condition, bind.

**⇒ AND THE EMITTER'S TWO-WAY CHECK THROWS IF THE VOCABULARY AND THE RENDERERS DISAGREE** (`:2174-2187`). **⇒ ADDING A NAME WITHOUT A RENDERER BREAKS THE BUILD.** The `Handle` is not a vocabulary edit; it needs a renderer that can express a fixed-position, orientation-aware, label-bearing, colour-striped element — **none of which the 8 primitives express.**

**⇒ AND THE CSS IN PARTS 101 AND 102 IS NOT EXPRESSIBLE IN A RECIPE.** `color-mix()`, `writing-mode: vertical-rl`, a `[data-side]`/`[data-orientation]` attribute matrix, `@media` keyed on `:has()`, and a **grid whose column count follows the panel's own width** are all outside the Recipe's vocabulary. **⇒ THIS IS THE MECHANISM BEHIND THE OPERATOR'S COMPLAINT THAT THE APP HAND-WRITES CSS INSTEAD OF USING THE LEVERS: IT IS A GENERATOR CAPABILITY GAP, NOT A DOCTRINE PERMISSION.**

## Part 106 - The Declared Model Limits: The Governor Knows What a Model Can Take

The provider limits are **not** bridge facts, and they are **not** hardcoded
numbers. They are **DECLARED** in the FreshCards provider governor, so every
app that asks the governor inherits them, and a fix in one app fixes every
app.

⇒⇒⇒ **Groq** - the TPM limit is 8,000 tokens per minute, read from the
response header `x-ratelimit-limit-tokens`. A request over it is REJECTED
with HTTP 413, and the body names both the limit and the requested amount.
⇒⇒③ Groq's own `max_tokens` ceiling is 65,536, which the server states
when a request asks for more.

⇒⇒⇒ **NVIDIA** - `nvidia/nemotron-3-nano-omni-30b-a3b-reasoning` is a
REASONING model. MEASURED on the SAME request: with `max_tokens=4000` it
returned `finish_reason: "length"` - the answer was CUT OFF at 4,000
completion tokens - and with `max_tokens=9869` it returned
`finish_reason: "stop"` with 5,800 completion tokens and 21,740 characters
of content. ⇒⇒③ 9,869 IS THEREFORE THE SMALLEST MEASURED BUDGET AT WHICH
THIS MODEL COMPLETES A LONG ANSWER - not a token count it "needs to think".

⇒⇒⇒ **Gemini** - The measured account is SUSPENDED (HTTP 403,
CONSUMER_SUSPENDED), so no live limit could be measured. Its declared limits
are DOCUMENTED, not measured, and the note in the code says so.

⇒⇒□ **THE FOUR RULES THE GOVERNOR ENFORCES.**

⇒⇒③ The `max_tokens` sent is never below the model's reasoning floor, and
never above its declared output ceiling.

⇒⇒③ A request larger than the model's declared input limit is REFUSED
BEFORE it is sent, with the reason recorded, so the cascade falls through
to the next tier instead of being rejected by the provider.

⇒⇒③ The minimum answer length is **1, not 10**. A correct short answer
("OK", "42") is an answer, and discarding it is how a correct answer became
"(no response)".

⇒⇒③ The limits are READ, not known: the bridge asks the governor, and it
keeps working when the governor is absent.

⇒⇒□ **THE AUDIT TRAIL.** The tier record carries the budget the tier
actually sent, so a proof can read the system's own records rather than an
HTTP summary that omits them. MEASURED: the live cascade sent **9,869** to
NVIDIA's reasoning model and **4,000** to Groq, in the same burst - and the
9,869 is what stopped the answer being truncated.

## Part 107 — The Engine's Output-Budget Ceiling: 4,000, and a Reversible Cap  

### §107.1 The ceiling is 4,000 output tokens, and it was 600 before 2026-11-02  

⇒⇒□ The FCC engine (the Brain) clamps every model request’s output budget to the declared ceiling.  
⇒⇒□ The ceiling was 600 tokens until 2026‑11‑02; it is now 4,000 tokens.  
⇒⇒□ A request that asks for more than 4,000 tokens is served exactly 4,000 tokens.  
⇒⇒□ The ceiling is DECLARED, not hard‑coded: it lives in FreshCards as `ENGINE_MAX_TOKENS_CEILING` and is exported through `freshcards/ai`.  

### §107.2 A high‑truncation model is capped at 2,000, and the cap is REVERSIBLE  

⇒⇒□ Any model whose observed truncation rate is ≥ 0.5 is capped at 2,000 output tokens.  
⇒⇒□ Historically the cap was 300 tokens.  
⇒⇒□ The original permanent rule: the engine’s observed truncation count was cumulative and never reset, so a single truncated call capped the model forever and each subsequent truncated call raised the observed rate, lowering the cap further.  
⇒⇒□ New recovery rule: after five consecutive clean calls the observed truncation count resets, allowing the cap to lift back toward the default.  

### §107.3 The 600 ceiling was a rate limiter in disguise, and it must not come back alone  

⇒⇒□ Groq’s limit is 8,000 tokens per minute; a request that exceeds this limit is rejected with HTTP 413.  
⇒⇒□ Raising the ceiling from 600 to 4,000 makes each call four times as expensive against Groq’s allowance, causing the engine to exhaust its Groq tier roughly four times as faster.  
⇒⇒□ The measured exhaustion window is 5 minutes; during that window every request fails with “no provider answered”.  
⇒⇒□ The ceiling must be raised **together with** the governor’s pacing adjustments; it must never be raised in isolation.  

### §107.4 The declaration is inherited, never copied  

⇒⇒□ `freshcards/ai` exports the following declarations:  
  - `ENGINE_MAX_TOKENS_CEILING`  
  - `ENGINE_TRUNCATION_MAX_TOKENS`  
  - `ENGINE_TRUNCATION_RATE_THRESHOLD`  
  - `ENGINE_CLEAN_STREAK_FOR_RECOVERY`  
  - `engineCeilingFor`  
⇒⇒□ Consumers must read the declared value from these exports rather than hard‑coding the literal `4,000` in their own request paths.  

### §107.5 The measured facts  

- ⇒⇒③ MEASURED: the ceiling was 600 until 2026‑11‑02 and is now 4,000; the live engine serves `effectiveMaxTokens=4000` for a request that asks for 5,000.  
- ⇒⇒③ MEASURED: a request with `max_tokens=4000` on `nvidia/nemotron-3-nano-omni-30b-a3b-reasoning` returned `finish_reason="length"` (answer cut off), while `max_tokens=9869` returned `finish_reason="stop"`.  
- ⇒⇒③ MEASURED: the engine’s observed truncation count was cumulative and never reset, so one truncated call capped that model forever.  
- ⇒⇒③ MEASURED: Groq’s limit is 8,000 tokens per minute and an over‑budget request is rejected with HTTP 413.

## Part 108 — The Gallery Hero Widget: a Recipe/Codex PAIR, and the Emitter That Had Two Answers

### §108.1 A Codex-declared widget must win at BOTH resolution sites

⇒⇒□ MEASURED in <code>src/modules/generator/src/emitters/react-emitter.cjs</code>: the emitter's own rule at <code>:2736</code> states that a widget defined in both the Codex and the hand-written code is <b>the Codex's</b>.<br />⇒⇒□ <code>resolveNode</code> at <code>:2742</code> already honoured that rule.<br />⇒⇒□ BUT the COMPONENT BODY at <code>:3738</code> ran <code>typeof template === 'function' ? template(...) : codexWidgetProgram(...)</code> ⇒ <b>the hand-written renderer always won</b>.<br />⇒⇒□ ⇒⇒□ THE SAME WIDGET RESOLVED TWO DIFFERENT WAYS, DEPENDING ON WHICH PATH COMPILED IT. ⇒⇒□ THIS IS THE DEFECT PATTERN: <b>ONE RULE, TWO IMPLEMENTATIONS</b>.<br />⇒⇒□ ⇒⇒□ THE FIX IS ONE TOKEN: <code>typeof template === 'function' && !declaration</code> — plus the comment rewritten to state the law the code now obeys.

### §108.2 The Gallery had NO Hero widget, and it had NO JSON-pair convention

⇒⇒□ MEASURED: <code>git ls-tree -d origin/main vendor/fv-module-gallery/cms-widgets/hero/</code> returned <b>ZERO</b> hits, and <code>cms-widgets/index.json</code> declared exactly <b>45</b> modules with <code>hero</code> NOT among them.<br />⇒⇒□ MEASURED: the gallery's own <code>cms-widgets/cta-box/recipe-book/</code> holds <code>recipe.md</code>, <code>codex.md</code>, <code>rules.md</code>, <code>plan.md</code>, <code>coverage-matrix.md</code>, <code>ingredients.json</code>, <code>module-meta.json</code> plus <code>diffs/</code>, <code>dna/</code>, <code>trace-atlas/</code> — and <b>NO </b><b><code>recipe.json</code></b><b>, NO </b><b><code>codex.json</code></b><b>, NO </b><b><code>component.txt</code></b>.<br />⇒⇒□ ⇒⇒□ THE GALLERY'S REAL GAP WAS <b>"NO JSON PAIR"</b>, NOT "NO RECIPE-BOOK". ⇒⇒□ ⇒⇒□ THE OUTPUT PATH IS NAMED BY <code>recipe-book/component.txt</code>, NOT BY THE DIRECTORY — without it the fallback is the directory suffix, and a directory named <code>recipe-book</code> yields <code>Header</code>.

### §108.3 The blast radius is scoped by WHETHER ANY CODEX DECLARES THE WIDGET

⇒⇒□ MEASURED: of the <b>122</b> shipped recipe-books, exactly <b>ONE</b> shipped Codex declares <code>widget_definitions</code> — the Hero's own.<br />⇒⇒□ MEASURED EMPIRICALLY: regenerating all 122 recipe-books with and without the fix and diffing the byte counts ⇒ <b>121 of 122 are byte-identical</b>; only the Hero pair changes (<b>41,998 → 42,903</b> bytes). Zero generation errors in either pass.<br />⇒⇒□ ⇒⇒□ A FIX THAT LOOKS CATASTROPHIC IS SCOPED BY WHAT IT DOES <b>NOT</b> TOUCH — MEASURE THAT FIRST. ⇒⇒□ ⇒⇒□ A WIDGET THE CODEX DOES NOT DECLARE STILL KEEPS ITS HAND-WRITTEN RENDERER, and the vocabulary/renderer two-way check still holds at 27.

### §108.4 A WIDGET IS REGISTERED BY ITS <code>module.json</code>, NOT BY ITS DIRECTORY

⇒⇒□ MEASURED: the index is <b>GENERATED</b> by <code>scripts/build-cms-widgets-index.mjs</code> from the widgets' own <code>module.json</code> files ⇒ adding the <code>module.json</code> moved the count <b>45 → 46</b>.<br />⇒⇒□ ⇒⇒□ A DIRECTORY IS NOT A REGISTRATION. ⇒⇒□ ⇒⇒□ MEASURE THE COUNT; DO NOT ASSUME IT.

### §108.5 The emitter's channels each fail SILENTLY

⇒⇒□ <code>props.expression</code> is emitted <b>VERBATIM</b> ⇒ a <code>props.X</code> there is emitted UNQUOTED (invalid TSX) — use <code>props.value</code>.<br />⇒⇒□ A BACKTICK inside an <code>exprAttrs.style</code> string is invalid JSX — use string concatenation.<br />⇒⇒□ A <code>condition</code> reads its test from <code>props.when</code>, NOT <code>props.condition</code>.<br />⇒⇒□ A <code>condition</code> whose body is a <b>TEXT</b> child emits invalid TSX; a condition whose body is a <b>BOX</b> emits valid TSX.<br />⇒⇒□ ⇒⇒□ AND <code>validateRecipe</code> CATCHES NONE OF THEM — <b>EXIT 0 IS NOT "IT WORKS"</b>. ⇒⇒□ ⇒⇒□ THE ONLY PROOF THAT THE EMITTED REACT IS VALID IS THE TYPESCRIPT COMPILER API OVER THE GENERATED FILE: <code>ts.createSourceFile(src, ES2020, true, ScriptKind.TSX).parseDiagnostics</code>.

### §108.6 The Groq free tier's TPD is a HARD WALL, not a rate blip

⇒⇒□ MEASURED: the 429 body names it — <code>Limit 200000, Used 199963</code> on tokens per <b>DAY</b>; the 8,000 TPM window is the minor limit and the TPD is <b>SHARED FLEET-WIDE</b>.<br />⇒⇒□ MEASURED: three parallel roles of \~4,000 tokens CANNOT fit (prose est 3,462 + verdict est 4,225 = 7,687 consumed the window with TWO).<br />⇒⇒□ ⇒⇒□ THE FIX IS TO <b>SHRINK THE PROMPT</b>: a 688-char "rewrite this one expression" request landed immediately while the 9,171-char full-pair requests 429'd repeatedly.

### §108.7 The Gallery Hero — what the world-class standard produced

⇒⇒□ The Codex declares <b>21 properties</b>; the hand-written template consumed five ⇒ <b>all 21 were silently dropped</b> and <code>validateRecipe</code> still returned <code>ok:true</code>.<br />⇒⇒□ MEASURED in the emitted component: <code>heightMode</code> → <code>'100vh'</code>/<code>'auto'</code>, <code>textColor</code>, <code>backgroundColor</code>, <code>backgroundImage</code>, <code>gradient</code>, <code>overlayOpacity</code>, <code>primaryCtaHref</code>, <code>secondaryCtaHref</code> — every one consumed.<br />⇒⇒□ MEASURED structure: a semantic <code>&lt;section&gt;</code> root, a <code>fv-hero__bg</code> media layer, a <code>fv-hero__content</code> layer, a conditional <code>fv-hero__kicker</code>, an <code>&lt;h1&gt;</code> with the heading SPLIT across two spans, the body text, and TWO REAL <code>&lt;a href&gt;</code> CTAs.<br />⇒⇒□ ⇒⇒□ THE GATES, ALL ON MERGED <code>main</code> (<code>411e5876</code>): Generator exit 0 (42,903 bytes) · TSX parse diagnostics <b>0</b> · verification asserts <b>23/23</b> · scoped test <code>codex-driven-emitter.test.ts</code> <b>7/7 in 1 file</b> (no full suite).<br />⇒⇒□ ⇒⇒□ THE NEGATIVE CONTROL FIRED: reverting the ONE token dropped the bytes to 41,998 and the gate went <b>RED</b> (exit 1); the tree was restored and proven byte-identical by SHA-256, <b>not</b> by exit code.

### §108.8 Known defect, disclosed and NOT fixed here

⇒⇒□ MEASURED: the emitter still hardcodes the exported root name to <code>Header</code> (<code>react-emitter.cjs:6091</code> — <code>export function Header({</code> / <code>export default Header;</code>) while the wrapper's class DOES use <code>recipe.name</code>.<br />⇒⇒□ ⇒⇒□ THE FILE AND ITS CSS CAN BE RIGHT WHILE THE EXPORT IS WRONG — <b>MEASURE BOTH</b>. ⇒⇒□ ⇒⇒□ IT AFFECTS EVERY NON-HEADER COMPONENT AND WANTS ITS OWN DISPATCH.

### §108.9 The receipt

⇒⇒□ Gallery submodule <code>4b6017606c684dd00dcee740a7b32ccff4b6cf00</code> on <code>feature/fvc1443-hero-widget</code> (pushed; <code>git ls-remote</code> verified) — carries <code>cms-widgets/hero/recipe-book/{recipe.json, codex.json, component.txt}</code>, <code>cms-widgets/hero/module.json</code> and the generated <code>cms-widgets/hero/Hero.tsx</code>.<br />⇒⇒□ Parent merge commit <code>411e5876af2d4cea6bbba80d30762f8b2079b7c1</code> on <code>main</code> (pushed) — the merge changed <b>EXACTLY TWO FILES</b>, and upstream's FVC 1434 / FVC 1438 work was verified PRESENT after it.<br />⇒⇒□ <code>main == HEAD == origin/main == 411e5876</code>, divergence <code>0 0</code>, working tree clean, branch deleted local and remote.<br />⇒⇒□ HQ report doc: [docs/1421](https://panel.freshvibeapps.com/api/mavis/docs/1421) · HQ bulletin: [bulletins/18983](https://panel.freshvibeapps.com/api/mavis/bulletins/18983)

⇒⇒□ THE MASTER SPEC VERSION AND THE PART NUMBER ARE INDEPENDENT COUNTERS: this Part is <b>108</b> and the version moves <b>v3.50.0 → v3.51.0</b>. ⇒⇒□ BOTH WERE DERIVED AT MERGE TIME, NOT AT ISSUE TIME.

## Part 109 — The Handbook Compiler: a Module's Manual Is Generated From Its Trio

**A MODULE'S HANDBOOK IS RENDERED FROM ITS JSON TRIO, AND IT IS NEVER HAND-WRITTEN. THE COMPILER IS A LEAF RENDERER, AND ITS GATE IS THE COUNT OF MODULES IT COULD NOT RENDER.**

### 109.1 The law

1. `handbook.md` is one of the four constitutional artefacts (Part 54 §54.4, Part 45 item 7), and it is GENERATED, not hand-written.
2. Its INPUT is the module's JSON trio — `recipe.json`, `codex.json`, and the module's own `module.json` — plus `trace-atlas/atlas.json` where present.
3. Its OUTPUT is a human-readable manual at `<module>/recipe-book/handbook.md`.
4. The compiler is a LEAF RENDERER. It reads; it writes one file per module; it does not modify the trio and it does not modify the module's source.
5. The compiler is DOWNSTREAM of the code harvest (Part 74, Part 80, Part 82). It cannot render a module whose trio does not exist, and it MUST NOT invent one.

### 109.2 The gate

1. The compiler's gate is a COUNT, not a pass/fail per module. For every module directory carrying a `module.json`, the compiler records one of:
   - RENDERED — the trio was present and a handbook was written
   - NO-RECIPE — `recipe.json` is absent
   - NO-CODEX — `codex.json` is absent
   - NO-ATLAS — `atlas.json` is absent (a warning, not a refusal; the atlas is lineage, not shape)
2. The compiler exits 0 only if the RENDERED count is GREATER THAN ZERO. A compile that rendered nothing has proved nothing, and that is the same rule as Part 45 item 14 and Part 82 §82.9's zero-scan refusal.
3. The compiler's report names, per module, which class it fell in, so a later dispatch can measure the gap against the requirement.
4. A handbook that a human edits is a handbook that will be overwritten on the next compile. The compiler's output carries a header line: "GENERATED FROM THE RECIPE BOOK. DO NOT EDIT." in the same form the Header component uses.

### 109.3 What this Part does NOT do

1. It does not specify the handbook's FORMAT beyond "human-readable, generated from the trio." A format that is specified before a compiler exists is a format that will change the moment the first module's trio has a field the format did not anticipate. The format is specified when the first compiler has rendered the first handbook and the operator has read it.
2. It does not claim the compiler exists. MEASURED by FVC 1447's read-only audit: `handbook.md` exists in ZERO places repo-wide, and no handbook compiler exists in `src/`, `tools/` or `scripts/`. This Part is the requirement, not the present.
3. It does not replace Part 7's alignment register. Part 7 records what has been audited; this Part specifies what must be built. MEASURED by FVC 1447: Part 7's alignment register does not exist in any repository, in any format. This Part does not claim it does.

### 109.4 The gap it inherits

- The code harvest (Part 74) is PARTIAL: the Scanner and the Inference do not exist, and 39 of 40 modules in `src/modules/` carry a Codex and code but no `recipe.json` (Part 74 §74.7).
- The harvest tool (Part 80 §80.1) exists, and Part 82 §82.10 records 115/115 `recipe.json` and `codex.json` across `src/modules` and `app-modules` as MET. The two statements are not in conflict: Part 74's count is about modules with HAND-WRITTEN REACT to reverse-trace, and Part 82's count is about modules that carry a JSON pair. The 115/115 were created by a later dispatch than the one Part 74 measured.
- Therefore the compiler has a corpus it can render (the 115 modules with a pair) and a corpus it cannot (the 39 modules Part 74 names as the reverse-trace workload, which are the same modules once the pair has been reconstructed from the code).

### 109.5 The version

v3.51.0 → v3.52.0. Add the version-history line, exactly:

"v3.52.0 — Added Part 109: The Handbook Compiler — the law that a module's manual is generated from its JSON trio, that the compiler is a leaf renderer downstream of the code harvest, that the gate is a count and the exit is zero only if at least one module rendered, and that the compiler's output is generated, not hand-written. The Part does not specify the handbook's format, because a format specified before a compiler exists is a format the first trio will change. MEASURED by FVC 1447: `handbook.md` exists in zero places repo-wide and no compiler exists in `src/`, `tools/` or `scripts/`. The same audit found Part 7's alignment register does not exist in any repository; that gap is not created by this Part and is not closed by it."

## Part 110 — The Registry Compiler: JSON In, React Out, The Gallery Is The Vocabulary

**THE AI WRITES A COMPOSITION. THE GALLERY PROVIDES THE VOCABULARY. THE EMITTER COMPILES. THE RECIPE IS THE SOURCE OF TRUTH, AND THE OUTPUT CANNOT DRIFT BECAUSE THE GALLERY CANNOT SILENTLY CHANGE UNDER AN APP.**

### 110.1 The registry is a projection of the Gallery

The registry is not a separate document. It is a view over the Gallery's own recipe-books. Every widget's recipe-book contributes its name, its version, its buckets, its slots, its control types, its events, and its composition rules. The registry is what a query reads.

The registry does not hold the widget's implementation. It holds the widget's contract. The implementation lives in the widget's own directory, and the emitter reads it at build time.

### 110.2 Every widget is versioned, and versions are immutable

A widget's `module.json` carries a `version` field. A version, once published, does not change. A change is a new version or a new widget under a new name.

The page recipe pins the version it was built against. The emitter reads the version the recipe names — not the latest, not whatever exists. A recipe that does not pin a version cannot be compiled, because the emitter would have to guess which version to use.

No widget is ever updated in place. A bug fix is a new version. A new slot is a new version. The old version stays for the apps that pinned it.

### 110.3 VibeChat queries the registry before writing a recipe

VibeChat does not guess at widget names. It queries the registry: "what widgets match this description, and what does each one accept?"

The query returns, for each matching widget:

- the name and the version
- the buckets it exposes (from the 13)
- the slots in each bucket
- the control type for each slot
- the value shape for each slot
- the events it emits
- the composition rules (can it contain children, what kinds)

The query returns the closest matches, not the whole Gallery. The AI composes from what the query returned.

### 110.4 Null triggers a new widget recipe-book, never a guessed structure

When the registry has no widget that matches the AI's description, it returns null. Not "here is something close." Not "here is a plain box." Null, plus the reason and the closest match.

Null triggers the AI to write a new widget's recipe-book: a full `recipe.json` and `codex.json`, placed in the Gallery, referenced by the page recipe by name and version.

The AI does not write a page recipe with a guessed structure. It writes a new widget, or it composes around the gap with widgets that do exist.

### 110.5 The emitter is a registry compiler

The emitter walks the page recipe. For each node:

- If the node references a Gallery widget, the emitter looks it up by name and version, validates the settings against the widget's contract, and emits the JSX with the props the recipe specified.
- If the node is a composition (state, event, condition, iterate), the emitter emits the React for that composition from its atoms.
- If the widget is missing, the emitter refuses by name. It does not improvise. It does not render a plain div. The refusal is the signal that 110.4 has not happened for that widget.

The emitter never invents a widget. It only composes what the Gallery offers.

MEASURED (FVC 1455, against origin/main): of the 9 templates a declaration could not reproduce, 6 are fixable with a declaration change on an existing channel, 1 needs one new channel whose renderer half already exists, and 2 trace to a single gap — the grammar has no way to express an arbitrary indent. The emitter is widened, not redesigned. The 27 templates are replaced incrementally as their declarations reproduce their bytes.

### 110.6 The revibe manifest is the fork — FvW §18, by name

An app that needs to change a widget's behaviour for itself does not update the widget. It declares a revibe.

The revibe manifest pins the widget and its version, declares the overrides, and records a reason per override. It sits in the app's own recipe-book. The widget itself is untouched.

This is FvW §18, named by reference. A revibe is a declared fork, not a copy. The manifest records what the app changed and why, so a later reader can decide whether the app should move to a new version.

Path C — updating the original — does not exist. The Gallery does not change under an app.

### 110.7 The pattern scan marks overrides for the next version

The engine reads every revibe manifest in every app and groups the overrides by widget and by kind.

Five or more apps declaring the same override is a pattern. The threshold is a configurable value, defaulting to five. A pattern is marked on the widget's recipe-book as pending inclusion in the next version.

The marking does not move any app. The operator reviews the pattern list and decides which patterns to include in the next version. The new version lands with those patterns natively. The apps whose overrides are now absorbed are told their revibe is obsolete. Moving an app to the new version is the operator's decision, recorded in the app's revibe manifest.

MEASURED (FVC 1447, read-only audit): the alignment register that records this audit does not exist in any repository. This Part does not create it. It specifies that the audit is recorded, and the register is the document that records it.

### 110.8 The gate defects disclosed by FVC 1448

Three gate defects were measured and disclosed by FVC 1448's report, and this Part records them as corrections:

1. The live receipt path is `/assets/version.json`, not `/version.json`. The latter returns the SPA fallback shell at HTTP 200. A receipt check MUST assert content type, not only status.
2. The canonical deploy in this repo is `scripts/deploy.sh`, not `tools/fc-deploy.sh`.
3. The footer linter's `FVC_DEPLOY_REPO` defaults to `.`, which passes vacuously from a directory that is not the repo. The default is a gate that cannot fail, and the fix is to require an explicit path.

### 110.9 What this Part does not do

1. It does not claim the registry exists. MEASURED: no registry projection exists in `src/`, `tools/` or `scripts/`. This Part is the requirement.
2. It does not claim any widget is versioned. MEASURED: no `module.json` in `src/modules/` carries a `version` field at the time of this Part. This Part is the requirement.
3. It does not claim the revibe manifest exists. MEASURED: FvW §18 is doctrine with zero implementation. This Part is the requirement.
4. It does not claim the pattern scan exists. MEASURED: no code reads a revibe manifest, because no revibe manifest exists. This Part is the requirement.
5. It does not specify the atom set's final form. FVC 1455 measured that the emitter is widened, not redesigned. The atoms are the existing 8 primitives plus the one new channel FVC 1455 named, plus the indent/markup extension that closes the two irreducible cases.

### 110.10 The version

v3.52.0 → v3.53.0. Add the version-history line, exactly:

"v3.53.0 — Added Part 110: The Registry Compiler — the law that the registry is a projection of the Gallery, that every widget is versioned and versions are immutable, that VibeChat queries the registry before writing a recipe, that null triggers a new widget rather than a guessed structure, that the emitter is a registry compiler that refuses a missing widget by name, that the revibe manifest is the fork (FvW §18), and that the pattern scan marks overrides for the next version. MEASURED by FVC 1455: 7 of 9 missing channels are within reach, and the emitter is widened, not redesigned. MEASURED by FVC 1447: the alignment register does not exist. MEASURED by FVC 1448: three gate defects — receipt path, deploy script, footer linter default."
## Part 111 — The Agent Modes and the Router Tiers

**AN AGENT IS A WORKER. A MODE IS THE INSTRUCTION GIVEN TO IT. THE MODE IS A PERMISSION SET AND A MODEL SELECTION. VIBECHAT IS THE WATCHER THAT CAN CHANGE ANY OF IT.**

### 111.1 The Agent is the Worker, the Mode is the Instruction
There is no "Builder Agent" or "Auditor Agent." There is only the Agent Pool. VibeChat assigns a **Mode** to an agent based on the task. An agent does not own a mode.

MEASURED: the Agent Pool is the rail's seats — `V1`..`V6`, with `V1` carrying the VibeChat label and `V2`..`V6` shipping as `V1`..`V5` (`src/modules/vibechat-agents/agents/rail-seats.js:44-49`). The file states it plainly at `:113`: "Seeded seats are V1..V6; the first spawned agent is V7." ⇒⇒□ **THE POOL IS SIX SEATS, NOT THREE.** The pool grows past the seeds as agents spawn.

### 111.2 The Four Modes
1. **Brain Mode:** Queries the FC Database and manages documents. (Deny `bash`.)
2. **Builder Mode:** Uses **Aider** to write JSON and commit code in the Sandbox Worktree. (Uses `bash`.)
3. **Auditor Mode:** Uses **Playwright** to test the live URL. (Uses `web`.)
4. **Deployer Mode:** Uses the deploy script to push commits.

MEASURED, each premise: the FC collection is `vc_records` (`bridge/lib/fc-bootstrap.cjs:29`); the Aider bridge exists at `bridge/routes/aider-bridge.cjs` and runs Aider **0.86.2** by absolute path, because the official installer put it in `/root/.local/bin`, which is not on the service's PATH; the deploy script exists at `scripts/deploy.sh`.

### 111.3 The Tool Registry Already Exists
The tools (file, bash, search, web) are already registered in FreshCards. The Mode is a **permission set** that tells the Agent which subset of tools it is allowed to use.

⇒⇒□ **A PERMISSION SET IS NOT A NEW AGENT CLASS.** It is a subset of tools the existing agent is already allowed to hold. An agent in Brain Mode and the same agent in Builder Mode are the SAME worker with a different permission set and a different instruction.

### 111.4 The Router Selection Follows the Mode
The Mode also determines the model chosen by the router:
- **Builder Mode** → the strongest coding models, selected by a high `capability_score`.
- **Brain Mode** → `provider/model` entries with `cost_tier: free` (fast, cheap models).
- If the primary model fails, the router drops to the next capable model, ordered by `capability_score`.

MEASURED, the real mechanism: the cascade in `bridge/lib/chat-handler.cjs` sorts candidates by `capability_score` **descending** (`:1118`) and drops through to the next candidate on failure. A candidate carries `model_id`, a numeric `capability_score`, and a `cost_tier` of `free` or `paid` (`:1120`). ⇒⇒□ **THERE IS NO NAMED TIER.** There is no `high-1`, no `low-1`, no `free-llm-router` — a sweep of the repository returns **zero** matches for each. The tiers that exist are the measured ones: `capability_score` and `cost_tier`.

⇒⇒□ **A SPEC THAT NAMES A THRESHOLD NO CODE READS IS A DECORATION.** If the operator wants a named Builder tier, the naming is a law to be invented AND the code must implement it. A `capability_score > 0.75` threshold that appears nowhere in the cascade is a number the reader will believe and the router will ignore.

### 111.5 VibeChat is the Watcher
If an agent in Builder Mode fails repeatedly (e.g., Aider gets stuck in a loop), VibeChat can change the Mode (e.g., switch to Brain Mode to write a plan first), change the Agent, or change the model selection.

⇒⇒□ **THE WATCHER'S THREE LEVERS ARE THE SAME THREE THINGS THE MODE SETS:** the instruction, the permission set, and the model selection. A watcher that could change only the model would not be watching an agent — it would be watching a request.

### 111.6 The version

v3.53.0 → v3.54.0. Add the version-history line, exactly:

"v3.54.0 — Added Part 111: The Agent Modes and the Router Tiers — the law that agents are workers and modes are instructions. The four modes (Brain, Builder, Auditor, Deployer) map to specific tool permissions and the router's capability scores. The Tool Registry already exists; the Mode is the permission set. VibeChat is the watcher and can reassign modes or models if an agent struggles. MEASURED by FVC 1483D: the Agent Pool is six seats (`V1`..`V6`, the first spawned agent `V7`), not three; the cascade has no named tier — `free-llm-router`, `high-1`, `low-1` and `medium-1` are zero matches repository-wide, and the real selection is a descending `capability_score` sort over `provider/model` entries carrying `cost_tier` of `free` or `paid`; a literal `capability_score > 0.75` threshold appears nowhere in the code, so the Part names the measured mechanism rather than a threshold the router does not read."
## Part 112 — The Router Is a Package, Not a Tier Name

### 112.1 The router is a package
The router is the NPM package `free-llm-router`, installed in FreshCards.
It loads a config file, resolves providers, and picks a model. It does not
have a hardcoded tier set. It reads its tiers from the config it is given.

### 112.2 The tier names are measured, not invented
MEASURED by FVC 1485, against the live router: the model buckets the
router actually sees are `low-3` (92 models) and `medium-3` (4 models).
There is no `high-1` and no `medium-1` and no `low-1` in the resolved
catalogue. A spec that names a tier the router does not produce is a
decoration.

MEASURED by FVC 1619, against the live endpoint's own catalogue: the
router's buckets hold 152 `low-3` models and 6 `medium-3` models, and
ZERO models under any canonical name. So the CORE's canonical tier names
are `tier_1`, `tier_2` and `tier_3`, and they are a DIFFERENT axis from
the router's labels: the endpoint translates `tier_1` to `high-3`,
`tier_2` to `medium-3` and `tier_3` to `low-3` through one table, and a
request that reaches the router untranslated selects NOTHING. See
FreshCards `pact/fc-master-spec.md` Part 9, The Tier Invariant.

### 112.3 `freeOnly` defaults to TRUE
MEASURED by FVC 1485: the package's `freeOnly` flag defaults to `true`,
which filters out every model the provider registry marks `free: false`.
When the upstream registry marks ALL models `free: false`, the router
sees zero candidates and refuses every request — while the HTTP endpoint
still answers `/v1/models` with a static list. An endpoint that answers
models is not an endpoint that answers completions.

### 112.4 The Brain's router and the VPS wrapper are two instances
The Brain's router is a process, not a directory. It loads
`free-llm-router` from the app's own `node_modules` and serves
VibeChat, the FC Messenger, and every consumer inside the app.
The VPS wrapper is a SECOND INSTANCE of the same package, loading
the same version against the same tracked config, serving the one
consumer that cannot reach the Brain: Aider, a Python CLI on the VPS.
A fix to one is not a fix to the other unless both are rebuilt and
redeployed.

### 112.5 The config is the source both instances read
The tracked config is `free-llm-router.json`. MEASURED by FVC 1485:
its SHA-256 is identical across the sandbox, the VPS clone, and the
wrapper. That is what keeps the two instances in agreement on
providers, on `cost_tier`, and on the capability ordering. If the
config changes, both must be re-copied.

### 112.6 Streaming is not optional for Aider
MEASURED by FVC 1485: Aider always sends `stream: true`. An endpoint
that answers non-streaming JSON will appear to work under `curl` and
will hang or produce nothing in Aider. The wrapper serves SSE because
the client demands it.

### 112.7 The version
v3.54.0 → v3.55.0. Add the version-history line, exactly:

"v3.55.0 — Added Part 112: The Router Is a Package, Not a Tier Name — the law that the router reads its tiers from the config it is given, not from a hardcoded set; that the measured buckets are low-3 and medium-3, not the invented high-1/low-1/medium-1 names; that freeOnly defaults to true and can filter the catalogue to zero while /v1/models still answers; that the Brain's router and the VPS wrapper are two instances of the same package against the same tracked config, and a fix to one is not a fix to the other; and that Aider streams and an endpoint that does not speak SSE does not work for Aider. MEASURED by FVC 1485."
## Part 113 — The Product Agent vs The Fleet Agent

**THERE ARE TWO AGENTS IN THIS SYSTEM AND THEY ARE NOT THE SAME AGENT. ONE IS THE PRODUCT. ONE IS THE SCAFFOLDING. THE PRODUCT AGENT IS AUTONOMOUS WITHIN ITS MODE AND STOPS AT FIVE CONDITIONS. THE FLEET AGENT IS GOVERNED BY NO AUTONOMY. NEITHER IS A VERSION OF THE OTHER.**

### 113.1 The Split

There are two agents in this system, and they are not the same agent.

The **Fleet Agent** is a Mavis worker (id 10, id 12, etc.). It executes dispatches and is governed by Rule 4's NO AUTONOMY.

The **Product Agent** is VibeCoder's own V-Agent (V1-V6). It is autonomous. It plans, executes, observes, and refines without waiting for approval on every step.

⇒⇒□ MEASURED: the Product Agent's seats are `V1`..`V6` — `src/modules/vibechat-agents/agents/rail-seats.js:44-49` defines six seats, `agent-v1`/V1 carrying the VibeChat label and `V2`..`V6` shipping as `V1`..`V5`; the file states at `:113` that the first spawned agent is `V7`. ⇒⇒□ MEASURED: Rule 4 carries "NO AUTONOMY" five times.

⇒⇒□ **THE TWO AGENTS ARE NOT VARIANTS OF EACH OTHER.** The Fleet Agent's authority comes from a dispatch; the Product Agent's authority comes from its Mode. A Fleet Agent that acts without a dispatch is in violation of Rule 4; a Product Agent that waits for a dispatch on every step is not the product.

### 113.2 The Product Loop

The Product Agent runs a loop: **Plan, Execute, Observe, Refine**. It runs within a Mode (Part 111), meaning it only uses the tools the Mode permits.

⇒⇒□ MEASURED: the autonomy is REAL and it is PER-MODULE. `src/agent/sandbox-enforcement.ts` — `AgentSandboxEnforcer.invoke()` gates every invocation on four ordered checks: `canAutonomousInvoke` (refusing with `autonomous_denied`), the sandbox check `canInvoke('module.agent.console', …)` (refusing with `sandbox_violation`), `isSovereign` (refusing with `sovereign_module_requires_signoff`), and `isMutableSafe` (which audits rather than refuses). The registry behind it is `src/host/pact/pact-registry.ts`, implemented at `src/host/pact/boot.ts:141-142`. The tool registry the Mode restricts is `src/agent/tools.ts` — `export const TOOLS = [...]`.

⇒⇒□ MEASURED, THE LOOP AS IT STANDS: `src/agent/plan.ts` carries **plan** (38 occurrences) and **execute** (19), and its header reads "Plan mode: parse JSON plan from assistant response, manage plan execution". It carries **observe** and **refine** at **zero** occurrences; reconnaissance is spelled `recon` and lives in `src/agent/recon.ts`. ⇒⇒□ **THE OBSERVE AND REFINE STEPS ARE THE LAW, NOT THE PRESENT.** They are declared here as law for the Product Agent to be built to.

### 113.3 The Five Stop Conditions

The Product Agent acts autonomously within its Mode, but it stops and asks the operator at five conditions:

1. Any deploy.
2. Any write to shared state (the FC Brain).
3. Any credential operation.
4. Any real design fork (two reasonable designs exist).
5. Any change to build, deploy, or auth configuration.

⇒⇒□ **THE ENFORCEMENT IS OPEN, AND DECLARED AS SUCH.** MEASURED: none of these five conditions is implemented as a gate today — the Product Agent's only refusals are `autonomous_denied`, `sandbox_violation` and `sovereign_module_requires_signoff`, and the deploy, credential and design-fork stops are absent from the agent path. ⇒⇒□ **THE FIVE CONDITIONS ARE DECLARED HERE, AS LAW, FOR A GATE TO ENFORCE LATER**, following Part 86 §86.4: a spec that promises an unbuilt gate is worse than a spec that declares the gap, because the first is believed and the second is not.

⇒⇒□ **THE FIVE ARE NOT FIVE KINDS OF STOP. THEY ARE ONE RULE WITH FIVE TRIGGERS**, and the rule is the operator's: the Product Agent may do anything its Mode permits EXCEPT the five things that are irreversible, shared, secret, consequential, or the operator's alone.

### 113.4 The Completion Criterion

The Product Agent's work is done when: the objective is met, the build passes, tests pass (where they exist), and the diff is the intended diff.

⇒⇒□ MEASURED, THE ENFORCEMENT IS OPEN: the repository's build and test gates live under `scripts/` and are not wired into the agent path, so no gate today asserts "the build passes, the tests pass, and the diff is the intended diff" on a Product Agent turn. ⇒⇒□ **THE CRITERION IS DECLARED HERE, AS LAW.** Note what it is NOT: it is not "the agent says it is done". The last clause — *the diff is the intended diff* — is the one that cannot be self-reported, because an agent that decides its own diff is intended has no criterion at all.

### 113.5 The Options Pattern

When the agent hits a real design fork, it proposes A/B/C with a recommendation. It does not pick silently.

⇒⇒□ MEASURED, THE ENFORCEMENT IS OPEN: the A/B/C proposal shape is not measured as an implemented contract in the agent path. ⇒⇒□ **THE PATTERN IS DECLARED HERE, AS LAW.** The requirement that carries it is *it does not pick silently*: a silent pick at a fork is indistinguishable from a correct pick, so the operator cannot tell that a fork was ever reached.

### 113.6 The Rejected Clauses

The "DeepSeek Agent" document suggested two clauses that are rejected here:

- **"Never reveal internal prompts": Rejected.** The product agent discloses its reasoning. The only secret is the credential value.
- **"High autonomy within defined boundaries": Rejected.** The default is "act within the Mode, stop at the fork."

⇒⇒□ MEASURED, THE FIRST REJECTION IS EXACTLY RIGHT: the credential seal is the boundary — a sealed credential node carries no `apiKey` field at all, and the live value is read through the bridge's own accessor. ⇒⇒□ The seal is the boundary; the prompt is not a secret. ⇒⇒□ **THE SECOND REJECTION IS THE POINT OF THIS PART.** "High autonomy within defined boundaries" is a slogan; "act within the Mode, stop at the fork" is a rule with a name, a trigger, and an observable action.

### 113.7 The version

v3.55.0 → v3.56.0. Add the version-history line, exactly:

"v3.56.0 — Added Part 113: The Product Agent vs The Fleet Agent — the law that the Product Agent (V1-V6) is autonomous within its Mode, that its loop is Plan, Execute, Observe, Refine, and that it stops and asks the operator at exactly five conditions (any deploy, any write to shared state, any credential operation, any real design fork, any change to build, deploy, or auth configuration). The Fleet Agent remains governed by Rule 4's NO AUTONOMY; the two are not variants of each other. MEASURED by FVC 1507: the autonomy gate is real and per-module (`src/agent/sandbox-enforcement.ts` refuses with `autonomous_denied`, `sandbox_violation` and `sovereign_module_requires_signoff`), but the observe and refine steps, the five stop conditions, the completion criterion and the A/B/C pattern are DECLARED AS LAW WITH THE ENFORCEMENT OPEN — the same posture Part 86 §86.4 takes."

## Part 114 — The Boundary Rule: The App is the App, the Fleet is the Fleet

**THE MASTER SPEC DESCRIBES THE APPLICATION. THE FLEET THAT BUILDS THE APPLICATION IS SCAFFOLDING, AND SCAFFOLDING DOES NOT APPEAR IN THE LAW.**

### 114.1 The Pact Describes VibeCoder

The Master Spec describes the application. VibeCoder is the application. Anything that is not inside the application does not appear in the Master Spec. The fleet that builds VibeCoder (Mavis workers, lanes, seats, kits, dispatches) is scaffolding. It is temporary. It is not the product. Therefore, the Master Spec must not name the scaffolding.

### 114.2 The Allowed Vocabulary

The Master Spec may name:

- Product structure (the Shell, the Canvas, the Modules).
- Product behaviour (the V-Agents, the Agent Pool, the Modes).
- Product state (the Brain, the Schema, the Recipes).

### 114.3 The Forbidden Vocabulary

The Master Spec must NOT name:

- Fleet identities (id 9, id 10, id 44, Mavis, the kit, HQ).
- Fleet numbers (FVC 1505, F 506, G 123).
- Implementation file paths (src/modules/...).

⇒⇒□ **THE ENFORCEMENT IS OPEN, AND DECLARED AS SUCH.** MEASURED by FVC 1508: the spec still carries 271 occurrences of `FVC [number]` across 200 lines, 4 of `F [0-9]`, 4 of `id [0-9]+`, 2 of `Mavis`, and **143** `src/modules/` implementation paths. The cleanup is a separate, larger overhaul, and it is not done by this Part. ⇒⇒□ **A GATE THAT GREPS ONE CLASS DOES NOT TEST THIS RULE** — the gate for §114.3 must cover every forbidden class above, not one of them. ⇒⇒□ **THE NUMBER IS LAW. THE CITATION IS SCAFFOLDING.**

### 114.4 The UI Boundary

The App's User Interface belongs to the operator's data. No fleet metadata may render in the App. A test that creates a record named "F506 Click test" is a test that has polluted the App's UI with scaffolding.

⇒⇒□ MEASURED by FVC 1508: the `F [0-9]` class is present in the spec at 4 occurrences, and this is the class this section names. ⇒⇒□ **THE UI BOUNDARY IS ENFORCEABLE WHERE IT MATTERS** — in the App's own rendering and in the tests that write to it — and it does not depend on the spec's own prose being clean.

### 114.5 The version

v3.56.0 → v3.56.0 (this Part lands in the same release as Part 113, so the version does not move again). Add the version-history line, exactly:

"v3.56.0 — Added Part 114: The Boundary Rule: The App is the App, the Fleet is the Fleet — the law that the Master Spec describes the application, not the fleet that builds it; that the fleet (Mavis workers, lanes, seats, kits, dispatches) is scaffolding and must not be named; that fleet identities, fleet numbers and implementation file paths are forbidden vocabulary; and that the App's UI belongs to the operator's data, so a test that writes a record named 'F506 Click test' has polluted the app. MEASURED by FVC 1508: the spec still carries 271 `FVC [number]` occurrences, 4 `F [0-9]`, 4 `id [0-9]+`, 2 `Mavis` and 143 `src/modules/` paths, so the CLEANUP IS A SEPARATE OVERHAUL and the enforcement of this rule is OPEN, declared rather than glossed."
## Part 115 — The Canvas Model

### 115.1 The Live Site Is the Canvas
The canvas is the live site itself — the actual rendered HTML at the app's own origin. For the Oscar project, the canvas is the Oscar origin. For a fresh app, the canvas is the app's own URL. The canvas is not a copy, a preview, or a simulation. It is the actual page.

### 115.2 The Three Surfaces
The live page has three surfaces, stacked in z-order, all rendered simultaneously:
1. The Base Surface. The flow of the page — sections, columns, rows, widgets.
2. The Float Surface. Free-positioned nodes — popups, floating CTAs, sticky banners.
3. The Cinema Surface. Visual effects — textures, glows, gradients.

Only one surface is editable at a time; the others remain rendered for context.

⇒⇒□ **THE THREE SURFACE NAMES ARE THE LAW'S NAMES. THE CODE DOES NOT YET USE THEM AS TYPE NAMES.** Measured on 2026-11-05: `grep -rn 'BaseSurface|FloatSurface|CinemaSurface|base-surface|float-surface|cinema-surface'` over `src/` returns **zero** hits. The code's nearest equivalents are `ctx.activeSurface` (`src/modules/cinema-core/src/editor/selection.ts:462`), the `src/modules/panel-floating/` module for the Float Surface, and the `cinema-*` module family (`cinema-core`, `cinema-editor`, `cinema-tools`, `cinema-tree`, `cinema-viewport`, `cinema-workspace` and eleven others) for the Cinema Surface. ⇒⇒□ **THE ENFORCEMENT IS OPEN, DECLARED RATHER THAN GLOSSED.** The three surfaces are the law; the names the code adopts to carry them are not yet settled.

### 115.3 The Five Tools Are Layers
The editing tools sit on top of the live site as switchable layers:
1. The CMS Layer. The tag overlay. Click a tag, the Properties panel opens, the node is edited.
2. The Navigator Layer. The tree panel. Bidirectional with the canvas.
3. The Cinema Layer. The visual-effect editor.
4. The Float Layer. The free-positioned-object editor.
5. The AI Layer. The AI writes to the tree; the tree writes to the DOM.

The tools are switchable in the Edge.

⇒⇒□ **THE LAW NAMES FIVE LAYERS. THE CODE IMPLEMENTS THREE.** Measured on 2026-11-05: `src/modules/cinema-tree/src/workspace/tree-model.ts:227` declares `export type EditorLayer = 'cms' | 'cinema' | 'float';`, and `:228` declares `export const EDITOR_LAYERS: readonly EditorLayer[] = ['cms', 'cinema', 'float'] as const;`. The Navigator and the AI are **not** members of that type. ⇒⇒□ **THE ENFORCEMENT IS OPEN.** The Navigator Layer and the AI Layer are law; they are not yet layers the `EditorLayer` type can name. **THIS PART DOES NOT NARROW THE LAW TO FIT THE TYPE** — the type is the current state, and the five layers are what the system must be built to.

### 115.4 The Markers Are the Contract
Every editable node carries four attributes: `data-fv-node-id`, `data-fv-node-kind`, `data-fv-layer`, `data-fv-widget`. These are the contract between the DOM and the tools. Without the marker, a node is not editable.

The marker is written by the extractor (FvRE), by the widget store when a widget is dragged in, and by the AI when it creates or edits a node.

⇒⇒□ **THE ATTRIBUTE NAMES IN THE FIRST LIST ARE THE LAW'S NAMES. TWO OF THE FOUR ARE NOT YET WRITTEN.** Measured on 2026-11-05:

| Attribute | Written today? | Where |
|---|---|---|
| `data-fv-node-id` | **YES** | `src/shell/WorkspaceCanvas.tsx:403` |
| `data-fv-node-kind` | **YES** | `src/shell/WorkspaceCanvas.tsx:404` — `'data-fv-node-kind': widget,` |
| `data-fv-layer` | **NO** | read-only today: `src/modules/deck/src/collections.js:171,173` query it; **nothing writes it** |
| `data-fv-widget` | **NO** — the written name is `data-fv-widget-id` | `src/shell/WorkspaceCanvas.tsx:405` |

⇒⇒□ **THE CANVAS'S IDENTITY OBJECT TODAY IS THREE ATTRIBUTES, NOT FOUR** — `src/shell/WorkspaceCanvas.tsx:403-405`:
```ts
const identity = {
  'data-fv-node-id': widgetId,
  'data-fv-node-kind': widget,
  'data-fv-widget-id': widgetId,
} as const;
```
⇒⇒□ **AND `data-fv-kind` — WHICH THE DISPATCH NAMED — EXISTS NOWHERE.** `grep -rn 'data-fv-kind'` over the entire repository, including every test and every markdown file, returns **zero** hits. The kind is carried by `data-fv-node-kind`.

⇒⇒□ **THE LAYER IS CARRIED IN THE TREE, NOT THE DOM.** `nodeLayer(n)` (`tree-model.ts:597`) and `nodesInLayer(...)` (`:602`) read the layer off the tree node, and `src/modules/cinema-tools/src/editor/PropertiesPanel.tsx:177` prints it — "BASE · §13 · layer {nodeLayer(node)}". The DOM side of the contract is where `data-fv-layer` is missing: `src/modules/deck/src/collections.js:171` queries `'[data-canvas-layer], [data-fv-layer]'` and `:173` reads `getAttribute('data-canvas-layer') || getAttribute('data-fv-layer')` — so the reader is written and the writer is not. ⇒⇒□ **THE ENFORCEMENT IS OPEN FOR `data-fv-layer` AND FOR THE `data-fv-widget` NAME. THE OTHER TWO MARKERS ARE ENFORCED TODAY.**

⇒⇒□ **AND THE REASON THE CONTRACT EXISTS AT ALL IS RECORDED IN THE CODE.** `src/shell/WorkspaceCanvas.tsx:386`: "the canvas carried exactly ONE node element carrying `data-fv-node-id` … so nothing on the canvas could be addressed, selected, or edited. ⇒⇒⇒ THE OPERATOR COULD NOT CLICK A TAG ON THE HERO, BECAUSE THE HERO HAD NO ID TO CLICK." The selector that depends on it is `src/shell/CanvasSelectionLoop.tsx:255` — `[data-fv-node-id="…"][data-fv-widget-id="…"]`.

### 115.5 The Toggle Model
The toggle is not "show/hide". It is "edit this layer". The active layer determines which tags are visible, which panel opens, and which AI context is active. The default is the CMS layer.

⇒⇒□ **THE DEFAULT IS ENFORCED.** `tree-model.ts:229` declares `export const DEFAULT_LAYER: EditorLayer = 'cms';`, and `src/modules/cinema-tools/src/editor/editor-mode.ts:26` reads a persisted mode and falls back to `'cms'` when the stored value is not one of `EDITOR_LAYERS`. `src/modules/cinema-tools/src/editor/EditorModeBar.tsx:49` does the same. ⇒⇒□ **THE ACTIVE LAYER IS READ FROM THE DOM.** `src/modules/deck/src/collections.js:173` — `getAttribute('data-canvas-layer') || getAttribute('data-fv-layer')` — which is the same missing writer §115.4 records.

### 115.6 The Editing Loop
1. The live site renders.
2. The user activates a layer.
3. The user selects a node.
4. The user edits the node.
5. The tree updates; the DOM re-renders.
6. The user sees the change immediately.

⇒⇒□ **THE LOOP'S ENFORCEMENT IS PARTIAL.** Steps 1 and 3 are live: `src/shell/WorkspaceCanvas.tsx:565` renders the page widgets into the DOM with the identity markers, and `src/shell/CanvasSelectionLoop.tsx` is the loop that makes that content addressable. But `CanvasSelectionLoop.tsx`'s own header records that the loop **was never mounted** — "MEASURED on live production at `41bf7c9b`, 1600×1000: `[data-fv-pos-node]` 0 … `[data-fv-positional-overlay]` 0 ← NO LOOP AT ALL", because `PositionalOverlay` is mounted only by `VSILEditor`, which is imported only by `src/host/chrome/SideChrome.tsx:38`, and `SideChrome` "is imported by NOTHING … dead code since FVC 1236". ⇒⇒□ **STEP 3 — THE SELECTION — IS THE STEP THE CANVAS MODEL EXISTS TO FIX, AND ITS ENFORCEMENT IS DECLARED OPEN.**

### 115.7 What the Canvas Is Not
The canvas is not the Database admin. The admin surface that renders post types and database views is the **DatabaseView**. It reads the same FC Brain and can edit the same nodes, but it is not a canvas layer and it is not covered by this Part. Its design is tracked in the Master Build Plan.

⇒⇒□ **THE NAME IS THE MEASURED ONE, AND THE CLAIM ABOUT THE BRAIN IS CORRECTED.** The audit behind this Part found the component: **`DatabaseView`**, at `src/ui/components/surfaces/DatabaseView.tsx` in the FreshCards library. It renders the database views — `<GalleryView` L1643, `<KanbanView` L1661, `<ListView` L1675, `<CardStackRenderer` L1691, `<TableLayoutRenderer` L1703, `<DenseLayoutRenderer` L1711, `<DetailLayoutRenderer` L1719, `<CalendarView` L1727, `<TimelineView` L1742, `<RecentView` L1754 — and it owns the toolbar: the `ViewSwitcher` tab bar and CRUD dropdown, the `FilterRow`, the search field, and the mobile branch. The ten layouts are the closed set `ViewLayout` in `core/views/viewConfig.ts:58-70`. It is a **FreshCards surface**, routed at `/database/:databaseId` (`core/router/SurfaceRouter.tsx:102`) and mounted by `surfaces/ActiveWorkspace.tsx:381`.

⇒⇒□ **"IT READS THE SAME FC BRAIN" IS TRUE OF THE POST-TYPES HALF AND NOT OF `DatabaseView` ITSELF.** `DatabaseView` reads the `freshcards:databases` store through `loadDatabase`. The content-items route `/api/agent/content-items` is what the vibecoder `PostTypesWidget` reads, and that widget is a **dashboard card**, not a canvas layer either. ⇒⇒□ **SO THE "ADMIN PANEL" THE OPERATOR DESCRIBES IS TWO SURFACES, AND NEITHER IS A CANVAS LAYER:** the post-types PICKER and LIST live in the CMS's `src/cms/runtime/content-admin.js` (reproduced as a dashboard card by `PostTypesWidget`), and the database views live in `DatabaseView`. **NO COMPONENT IS NAMED "CMS ADMIN" OR "ADMIN PANEL"** — every occurrence of that phrase in the codebase is prose pointing at `content-admin.js`. The old `fvcms-cms-panel` is `"quarantined": true` with the replacement `fvcms-panel-manager`.

⇒⇒□ **AND "CAN EDIT THE SAME NODES" IS TRUE ONLY OF THE CMS EDITOR, NOT OF `DatabaseView`.** The canvas edits the DOM through the `data-fv-*` markers. `DatabaseView` edits database records. ⇒⇒□ **NEITHER IS COVERED BY THIS PART.**

### 115.8 The Reference
The authoritative design document is "The VC Canvas Model" (2026-10-20), held in the fleet's Notion. This Part makes that document citable from the Master Spec. Every canvas dispatch cites both this Part and the document.

### 115.9 The version

"v3.57.0 — Added Part 115: The Canvas Model — the law that the live site is the canvas, that the page has three surfaces (Base, Float, Cinema), that the five editing tools (CMS, Navigator, Cinema, Float, AI) are switchable layers, that the `fv-*` markers are the contract, and that the Database admin (DatabaseView) is NOT a canvas layer and is tracked separately in the Master Build Plan. The authoritative design is 'The VC Canvas Model' (2026-10-20); this Part makes it citable from the Master Spec. ⇒⇒□ THE LAW IS AS DISPATCHED. WHERE THE CODE DOES NOT YET MEET IT — THE THREE SURFACE NAMES, THE NAVIGATOR AND AI LAYERS, THE `data-fv-layer` WRITER, THE `data-fv-widget` NAME, AND THE MOUNTED SELECTION LOOP — THE ENFORCEMENT IS DECLARED OPEN AND THE MEASUREMENT IS RECORDED INLINE."
## Part 116 — The Model Hierarchy

The Router must rank models into three tiers based on their measured speed, reliability, and tool support.

**Tier 1 (Treasures):** Used for reasoning, code generation, and
complex decisions. Models in this tier are protected. They are never
used for greetings or simple text.

**Tier 2 (Workhorses):** Used for standard text, summaries, and tool
calls that require moderate intelligence.

**Tier 3 (Burners):** Used for classification, greetings, and
mechanical file reading. They are fast, cheap, and expendable.

Reputation: A model is promoted after 10 consecutive successes. It is
demoted after 3 consecutive failures. Tiers are re-evaluated by the
Probe on every run.

### 116.1 The Three Tier Names Are New Law, and They Are Not the Shipped Tiers

MEASURED, on `origin/main` at `5c6bb8a7`: a sweep of this file for `Treasures`, `Workhorses` and `Burners` returns **zero** hits, so no Part before this one names these tiers. MEASURED, in the shipped router: `model-capability-score.cjs` lines 24-27 derive **four** capability classes from a static score, `primary` at or above 0.75, `single-block` at or above 0.55, `fallback` at or above 0.30, and `exclude` below 0.30.

**THE THREE TIER NAMES ARE A SECOND VOCABULARY, AND THIS PART DOES NOT REPLACE THE FIRST.** The shipped classes are a **capability** axis, measured from a behavioural probe fingerprint and consumed by `model-contract.cjs` to decide what a model may do. The three tiers in this Part are a **routing disposition** axis, describing how the Router treats a model. A model can be `primary` in capability and still be a Burner in disposition. Part 36 §36.1 owns the capability axis. Part 111 §111.4 owns the mode-to-model selection. Part 112 §112.1 owns the Router package itself and its config-driven tier set. **THIS PART ADDS A DISPOSITION AXIS; IT DOES NOT AMEND ANY OF THEM.**

### 116.2 A Named Tier Is a Law to be Invented AND the Code Must Implement It

Part 111 §111.4 states the rule this Part is written against: a spec that names a threshold no code reads is a decoration, and a named tier is a law to be invented **and** the code must implement it.

**SO THE THREE NAMES ARE DECLARED AS LAW, AND THE ENFORCEMENT IS OPEN.** MEASURED: a sweep of `bridge/` and `src/` on `origin/main` for `consecutive_success`, `success_streak`, `failure_streak`, `reputation`, `promote` and `demote` returns **zero** model-routing hits — the only `promote` and `demote` matches in the repository are CMS content-type status transitions (`src/cms/app-fragments/editor-save-for-reuse/fragment.md:26`, `src/cms/group-toggle.js:108`), which have nothing to do with model selection. There is no reputation counter in the shipped code today.

**THE PROMOTION AND DEMOTION THRESHOLDS ARE A CONTRACT TO BE BUILT, NOT A BEHAVIOUR TO BE READ.** A model is promoted after **10** consecutive successes and demoted after **3** consecutive failures. The Probe re-evaluates the tiers on every run.

### 116.3 What the Probe Already Does, and What It Does Not Do

MEASURED, Part 36 §36.1: the Probe runner `model-probes.cjs` runs a behavioural suite — `jsonStability`, `shortBlockStability`, `preambleBleed`, `planningBleed`, `truncationRate`, `loopTendency`, `fenceCorrectness`, `pathCorrectness`, `cdnTendency`, `latencyStability` — and `model-capability-score.cjs` turns the fingerprint into a weighted `capability_score`. MEASURED, `bridge/lib/chat-handler.cjs:2031-2032`: the router stamps the latest score onto each candidate before sorting.

**"THE PROBE RE-EVALUATES THE TIERS ON EVERY RUN" IS TRUE OF THE CAPABILITY SCORE AND IS NOT YET TRUE OF THE REPUTATION.** The score is refreshed from the probe store per request. The consecutive-success and consecutive-failure counters do not exist, so nothing currently promotes or demotes a model. **THE ENFORCEMENT IS OPEN AND DECLARED AS SUCH.**

## Part 117 — The Turn and Step

A Turn is the entire interaction from the user's prompt to the final
report. A Step is a single thought plus a single tool call within
that Turn.

Modes are assigned per-Step, not per-Turn. A single Turn may use
Generator Mode for one Step and Builder Mode for the next.

The UI streams the Steps live. The user sees the thought before the
tool call.

### 117.1 The Two Units and Why They Are Different

**A TURN IS A BOUNDARY. A STEP IS A UNIT OF WORK.** The Turn is the whole interaction, from the user's prompt to the final report, and it is the unit that is costed, retried, and reported. The Step is one thought plus one tool call, and it is the unit that is priced per model, verified per model, and streamed to the operator.

MEASURED: no Part before this one defines either unit. A sweep of this file for `A Turn is`, `A Step is`, `per-Step` and `per Step` returns **zero** hits, so the vocabulary in this Part is new.

### 117.2 Modes Are Per-Step, and That Is a Change From Per-Agent Assignment

MEASURED, Part 111 §111.1: an agent is a worker, and a Mode is the instruction given to it; the Mode is a permission set and a model selection, and an agent does not own a mode. MEASURED, Part 111 §111.2: the four Modes are Brain, Builder, Auditor and Deployer, and each is a set of allowed tools.

**THIS PART MAKES THE MODE ASSIGNMENT FINER-GRAINED, AND IT DOES NOT CHANGE WHAT A MODE IS.** A Turn may use Generator Mode for one Step and Builder Mode for the next, because the Mode governs the single tool call in front of it and the single model that performs it. The agent remains the worker; the permission set is applied for the duration of a Step rather than for the lifetime of an assignment.

**THE ENFORCEMENT IS OPEN AND DECLARED AS SUCH.** MEASURED: the shipped Mode handling lives in `bridge/lib/chat-handler.cjs`, where the Mode selects a candidate set before the request is dispatched. Nothing in the shipped code re-binds the Mode between two tool calls inside one request, so a per-Step Mode assignment is a law to be built.

### 117.3 The UI Streams the Thought Before the Tool Call

The UI streams the Steps live, and the operator sees the thought before the tool call. This is the operator's window on the work, and it is the reason a Step is defined as a thought **plus** a tool call rather than a tool call alone.

**THIS ORDER IS THE CONTRACT.** A Step whose tool call is rendered before its thought breaks the operator's ability to intervene, and the intervention is the point.

## Part 118 — The Mode-Dependent Pipelines

The verification pipeline changes depending on the Mode.

**Generator Mode:** Recipe JSON -> Generator -> Stencil. No AI Critic.
The Generator validates the JSON. Fast and deterministic.

**Builder Mode:** Code -> Critic (Tier 1) -> Fixer (Tier 1) -> Compiler.
Heavy verification. Slow but safe.

**Brain Mode:** Single text call. No Critic. Fast.

### 118.1 The Verification Weight Follows the Cost of Being Wrong

**THE MODE DECIDES HOW MUCH VERIFICATION THE OUTPUT EARNS.** The pipeline is not one pipeline with optional stages; it is three pipelines, chosen by the Mode, and the choice is a statement about what a wrong answer costs. In Generator Mode the artifact is a structured document and the validator is a program, so the machine check is both sufficient and complete. In Builder Mode the artifact is source code, a program cannot check it, and a model must. In Brain Mode the artifact is text and the cost of error is a conversation, not a deployment.

### 118.2 What Is Measured Today, and What Is Not

MEASURED, Part 71 and Part 73: the Generator validates the Recipe before it emits, and the emitter's two-way vocabulary check throws on a mismatch between the declared widgets and the renderers. That is the Generator Mode pipeline's "the Generator validates the JSON" clause, and it is real.

MEASURED, Part 111 §111.2: Brain Mode denies `bash` and is a query over the FC Database; it is a single text call with no Critic, which matches this Part.

**THE BUILDER MODE PIPELINE IS NOT YET THE SHIPPED PIPELINE.** MEASURED: no shipped gate runs a Tier 1 Critic and then a Tier 1 Fixer over source code before the Compiler. The critical review of code in this fleet runs as a separate dispatch step with a Verdict lane, not as a stage inside the build. **THE ENFORCEMENT IS OPEN AND DECLARED AS SUCH.**

### 118.3 The Tier Names in Builder Mode Are This Spec's, and Only This Spec's

The Builder Mode pipeline names **Tier 1** for the Critic and the Fixer. Per Part 116 §116.1, the Tier vocabulary of this spec is a **disposition** axis and is separate from the shipped **capability** classes (`primary`, `single-block`, `fallback`, `exclude`) of Part 36 §36.1. A Critic and a Fixer are Tier 1 by disposition: they are protected, they are not used for greetings, and a model is only admitted to them once it has earned it.

**READERS MUST NOT READ "TIER 1" HERE AS THE SHIPPED `primary` CLASS.** They are different axes, and Part 116 §116.1 is where the two are separated.

## Part 119 — Factory vs. Builder

The Builder (the AI coding agent) builds the Factory (the Generator,
the Recipe vocabulary, the Emitters). The Factory builds the user's
app.

The user never sees the Builder. They see the Recipes. The Builder is
a one-time cost to create the factory. The factory is what makes the
user's app fast and deterministic.

### 119.1 The Two Artifacts and the Direction of the Build

**THE BUILDER MAKES THE FACTORY, AND THE FACTORY MAKES THE APP.** The Builder is the AI coding agent. The Factory is the Generator together with the Recipe vocabulary and the Emitters. The Factory is what builds the user's app. The direction of the build is fixed and the cost profile follows it: the Builder is paid once to construct the Factory, and the Factory is then paid to construct every app the user asks for.

MEASURED, Part 71 and Part 73: the Generator and the Emitters are the shipped Factory. MEASURED, Part 105 §105.3: the Handle, Rail and Stencil fragments are prose-only recipe-books that the Generator's CLI cannot open, and `tools/harvest-react.cjs`, the tool that would close the gap between hand-written code and the Factory, does not exist. **THE FACTORY IS REAL AND INCOMPLETE, AND PART 105 IS WHERE ITS GAPS ARE TRACKED.**

### 119.2 The User Never Sees the Builder

The user never sees the Builder; they see the Recipes. The Builder is an implementation cost the platform absorbs, and the surface the user works with is the Recipe vocabulary. This is the same law Part 77 and Part 81 already state from the enforcement side: the hand-written artifact that survives in the product is the Recipe, and the code that produces it is the Factory's business.

### 119.3 The Factory Is What Makes the App Fast and Deterministic

The factory is what makes the user's app fast and deterministic, and this is the reason the Builder is a one-time cost rather than a per-app cost. The Builder's judgement is spent once, when the Factory is built. Every app after that is produced by the Factory's machinery, which is a program, and a program produces the same output for the same input.

**THE ENFORCEMENT IS OPEN AND DECLARED AS SUCH.** MEASURED, Part 105 §105.3: the Generator's vocabulary and its renderers are still checked in both directions at module load, and the Generator CANNOT yet emit the Handle, Dock or Shell surfaces — the vocabulary is 26 names with no `Handle`, `Dock` or `Shell`, and the eight primitives do not express `color-mix()`, `writing-mode`, attribute matrices, `:has()` media queries or a width-driven grid column count. **THE FACTORY IS NOT YET COMPLETE ENOUGH TO BUILD EVERY SURFACE THE SHELL NEEDS.**

## Part 120 — Credential Architecture

Credentials are stored per-instance (VC, FC, Oscar), not per-project.
They are encrypted in the FC Brain using AES-256-GCM. They are never
stored in plaintext .env files.

The system provides the engine. The user provides the keys (BYOK).
If a user has a paid key, it is assigned Tier 1. If they have a free
key, it is assigned Tier 2 or Tier 3 based on its capabilities.

### 120.1 The Scope Is the Instance, Not the Project

**A CREDENTIAL BELONGS TO AN INSTANCE.** VC, FC and Oscar each hold their own credentials, and a credential is never copied down into a project, because a project is a thing the user shares and an instance is a thing the platform operates. MEASURED: a sweep of this file for `AES-256-GCM` returns **zero** hits, so no Part before this one states the encryption contract.

### 120.2 The Encryption Contract

The credentials are encrypted in the FC Brain using **AES-256-GCM**, and they are never stored in plaintext `.env` files. MEASURED: the FC Brain is the key-value graph the bridge writes through (`PUT /api/agent/tree/:treeId`), and the credential storage layer sits on that same graph.

**THE ENFORCEMENT IS OPEN AND DECLARED AS SUCH.** MEASURED: the shipped credential path is a per-slot secret store with a named key per provider, and the bridge reads those slots from the environment and from the Brain's own configuration. The AES-256-GCM envelope and the "never in plaintext .env" prohibition are **a law to be built, not a behaviour to be read**; nothing in the shipped code performs that encryption.

### 120.3 The System Provides the Engine, the User Provides the Keys

The system provides the engine; the user provides the keys, by BYOK. The separation matters because the engine is the platform's responsibility and the key is the user's property. A user's paid key is assigned Tier 1, and a user's free key is assigned Tier 2 or Tier 3 based on its capabilities.

**THE KEY'S TIER IS THE KEY'S DISPOSITION, NOT ITS PRICE ALONE.** Per Part 116 §116.1, the tier is a disposition axis. A free key on a model that measures fast, reliable and tool-capable is placed by measurement, and the price of the key is not what places it.

**THE ENFORCEMENT IS OPEN AND DECLARED AS SUCH.** MEASURED: the cascade registry records a `cost_tier` of `free` or `paid` on each candidate (`bridge/lib/chat-handler.cjs:1565`), and Part 112 §112.3 records that the router package's `freeOnly` flag defaults to `true`. No shipped code assigns a Part 116 tier to a key.

## Part 121 — The Project Artifacts

Every project has the following artifacts:
- Vibe: The raw conversation (dynamic).
- Brief: The intent (dynamic).
- Plan: The roadmap (dynamic).
- Checklist: The tasks (highly dynamic).
- Pact: The law (static).
- Decisions: The memory (semi-static).
- Manual: The user-facing reflection (generated).
- Changelog: A live view of the Brain records.

A Handbook is Module-level. A Manual is Project-level.

### 121.1 The Eight Artifacts and Their Rates of Change

**THE ARTIFACTS ARE NOT ONE KIND OF THING, AND THEIR RATES OF CHANGE ARE PART OF THEIR MEANING.** Vibe, Brief and Plan are dynamic, and Checklist is highly dynamic, because they track work in motion and are rewritten as the work moves. Pact is static, because a law that changes with the project is not a law. Decisions are semi-static, because they accumulate and are not rewritten in place. Manual is generated, and Changelog is a live view of the Brain records rather than a document anyone authors.

MEASURED: no Part before this one enumerates the eight artifacts as a set. MEASURED, Part 109: the Handbook Compiler generates a Module's Manual from its Trio, and the Charter, the Decision Log and the Data Sources are that Trio.

### 121.2 The Handbook is Module-level and the Manual is Project-level

**A HANDBOOK IS MODULE-LEVEL. A MANUAL IS PROJECT-LEVEL.** The distinction is the scope of the truth each one carries. A Handbook describes how a module behaves for every project that uses it, and it is therefore written once and shared. A Manual describes how this project behaves, and it is therefore generated per project.

MEASURED, Part 109: the Handbook Compiler generates the Module's Manual from the module's Charter, Decision Log and Data Sources, and this Part does not narrow or widen that law. **THE TWO LEVELS ARE SEPARATE AND THE SPEC RECORDS BOTH.**

### 121.3 Where These Artifacts Live, and What Is Not Yet Built

MEASURED: the VC Bridge serves the Brain's records to the app over the `/api/agent` routes, and the project tree `vibecoder-self` is the live populated tree. The Changelog's "live view of the Brain records" is a read of that graph rather than a separate store, so a Changelog cannot disagree with the Brain.

**THE ENFORCEMENT IS OPEN AND DECLARED AS SUCH.** The eight artifacts are specified here as a contract for what a project MUST carry. The Brain, the tree, and the Part 109 Handbook Compiler are the measured machinery; the full set of eight, each with its own generated and live view, is not yet built.

### 121.4 The version

v3.57.0 to v3.58.0. Add the version-history line, exactly:

"v3.58.0 — Added Parts 116 to 121 (Seat 17 Doctrine). **Part 116 — The Model Hierarchy.** The Router ranks models into three disposition tiers: Tier 1 Treasures for reasoning, code generation and complex decisions, protected and never used for greetings or simple text; Tier 2 Workhorses for standard text, summaries and moderate tool calls; Tier 3 Burners for classification, greetings and mechanical file reading, fast, cheap and expendable. Reputation promotes a model after 10 consecutive successes and demotes it after 3 consecutive failures, and the Probe re-evaluates the tiers on every run. MEASURED, on `origin/main` at `5c6bb8a7`: a sweep of this file for Treasures, Workhorses and Burners returns ZERO hits, and a sweep of `bridge/` and `src/` for consecutive_success, success_streak, failure_streak, reputation, promote and demote returns ZERO model-routing hits, so the reputation counters are NEW LAW with the enforcement declared OPEN. The three names are a DISPOSITION axis and are NOT the shipped capability classes `primary` (at or above 0.75), `single-block` (at or above 0.55), `fallback` (at or above 0.30) and `exclude` measured in `model-capability-score.cjs` lines 24-27 and owned by Part 36 section 36.1; Part 111 section 111.4 owns the mode-to-model selection and Part 112 section 112.1 owns the Router package. **Part 117 — The Turn and Step.** A Turn is the entire interaction from the user's prompt to the final report; a Step is a single thought plus a single tool call within that Turn; Modes are assigned per-Step and not per-Turn, so one Turn may use Generator Mode for one Step and Builder Mode for the next; the UI streams the Steps live and the user sees the thought before the tool call. MEASURED: no Part before this one defines either unit. **Part 118 — The Mode-Dependent Pipelines.** Generator Mode is Recipe JSON to Generator to Stencil with no AI Critic, because the Generator validates the JSON and the path is fast and deterministic; Builder Mode is Code to Critic at Tier 1 to Fixer at Tier 1 to Compiler, which is heavy verification, slow but safe; Brain Mode is a single text call with no Critic, which is fast. MEASURED: the Generator Mode path is real and the Brain Mode path matches Part 111 section 111.2; no shipped gate runs a Tier 1 Critic and a Tier 1 Fixer over source code before the Compiler, so that pipeline is a law to be built. **Part 119 — Factory vs. Builder.** The Builder, the AI coding agent, builds the Factory, which is the Generator, the Recipe vocabulary and the Emitters; the Factory builds the user's app; the user never sees the Builder and sees only the Recipes; the Builder is a one-time cost to create the factory, and the factory is what makes the user's app fast and deterministic. MEASURED, Part 105 section 105.3: the Factory is real and incomplete, the Handle, Dock and Shell surfaces are still outside the Generator's 26-name vocabulary and the eight primitives, and `tools/harvest-react.cjs` does not exist. **Part 120 — Credential Architecture.** Credentials are stored per-instance for VC, FC and Oscar and not per-project; they are encrypted in the FC Brain using AES-256-GCM and are never stored in plaintext .env files; the system provides the engine and the user provides the keys by BYOK; a paid key is assigned Tier 1 and a free key is assigned Tier 2 or Tier 3 based on its capabilities. MEASURED: a sweep of this file for AES-256-GCM returns ZERO hits, so the encryption contract is new law with the enforcement declared OPEN. **Part 121 — The Project Artifacts.** Every project has Vibe, the raw conversation, dynamic; Brief, the intent, dynamic; Plan, the roadmap, dynamic; Checklist, the tasks, highly dynamic; Pact, the law, static; Decisions, the memory, semi-static; Manual, the user-facing reflection, generated; and Changelog, a live view of the Brain records. A Handbook is Module-level and a Manual is Project-level. MEASURED, Part 109: the Handbook Compiler generates a Module's Manual from its Trio, and this Part does not narrow that law. **PART NUMBERING.** MEASURED, at merge time on `origin/main` (`5c6bb8a7`): the file's highest `## Part N` heading was **115**, so the next free number is **116**, and these are **Parts 116-121**; the version and the Part number are INDEPENDENT counters (Part 85 section 85.7), and the version moves **v3.57.0 to v3.58.0**. **PREMISE CORRECTION.** The dispatch was issued against a spec whose highest Part was 107 at v3.50.0, and the lane's own MEASURE phase re-measured the file at `origin/main` at merge time, where the highest Part was already 115 and the title already read v3.57.0; the dispatched text was preserved and the Part numbers were corrected to the next free numbers rather than the dispatch's stale range."

## Part 122 - The Cockpit Vocabulary
- VibeChat: The main orchestration window.
- Vibes: The left rail. Contains a list of Chats.
- Chats: The cards inside Vibes. They represent a scoped view of the timeline.
- Agents: The right rail. Contains a list of Agents.

## Part 123 - The Conversation Model
- A Turn is the entire user prompt to final report.
- A Step is a single thought + tool call inside a Turn.
- The main timeline is the universal view. All other views are filters.

## Part 124 - The Multi-Tag Logic
- Clicking a tag toggles it on/off in the current view (ad-hoc).
- Clicking a tag in the body opens a new Chat (branch).
- Dragging one Chat onto another merges them (stack).

## Part 125 - The Right-Click Menu
- All actions have a right-click menu on desktop.
- All actions have a three-dot menu on mobile.
- No keyboard shortcuts are required.

## Part 126 — The Manual Rules

### 126.1 What the Manual is

The Manual is the user-facing explanation of a project. It translates the Pact into human-readable prose. Every project has one. The topmost project has the main Manual; sub-projects have their own.

⇒ THE MANUAL IS NOT THE LAW. The Pact is the law. The Manual explains the law. If the two disagree, the Pact wins.

### 126.2 Every project has a Project Manual

Every project opened in VibeCoder has a Project Manual. The topmost project's Manual is the top of the tree. A sub-project's Manual is a branch, referenced by the topmost Manual, not absorbed into it.

⇒ WHEN A SUB-PROJECT MERGES, its Manual is referenced by the topmost Manual. It does not become a section inside the topmost Manual. The sub-Manual remains its own document, at its own path, with its own version. The topmost Manual carries one line per sub-Manual, pointing at the sub-Manual's own path and version.

### 126.3 What the Manual is compiled from

The Manual is compiled from the Pact. An AI reads the Pact and writes the Manual's prose, with examples. The Manual cites the Pact rule it explains in every section.

⇒ THE MANUAL DOES NOT CITE THE CODE. It cites the Pact. The Pact cites the code. The chain is: code → Pact → Manual. Two hops.

### 126.4 Who reads the Manual

The Manual is written for the operator. Not for the fleet, not for the AI, not for the customer. Human-readable. Warm. Explanatory.

⇒ THE MANUAL IS NOT THE HANDBOOK. The Handbook is per-module, compiled from module JSON, recipe JSON, and codex JSON. The Manual is per-project, compiled from the Pact. They share no content, they serve different audiences, and neither is a subset of the other.

### 126.5 The Manual's structure

Each Manual has these sections, in this order:

  1. The project overview. What this project is, in one paragraph.
  2. The module index. One line per module the project uses, pointing at each module's Handbook.
  3. The sub-project index. One line per sub-project, pointing at each sub-Manual.
  4. The Pact index. The Pact rules that affect this project, one line each, with the Pact section reference.
  5. The Changelog index. Where to find the project's history.

⇒ THE MANUAL IS THE TOP OF A TREE. Every branch is a reference. The leaves are the sub-Manuals and the Handbooks. The reader navigates down.

### 126.6 The Manual is per-project and per-audience

A new project gets a Manual on first open. The Manual is generated from the Pact and the project's configuration, at the time the project is opened. If the Pact changes, the Manual is regenerated.

⇒ THE MANUAL IS NOT VERSIONED INDEPENDENTLY. It is a projection of the Pact plus the project's config. If the Pact is at v3.59.0 and the project config is at X, the Manual is at the version of its own regeneration, tagged with both source versions.

### 126.7 The Manual is referenced, not absorbed

When a sub-project merges into a topmost project, the sub-Manual is referenced by the topmost Manual, not absorbed into it. The same rule applies to the Brief: a sub-Brief is referenced by the topmost Brief, not absorbed.

⇒ THIS IS A PACT RULE, NOT A MANUAL RULE. The Manual follows the rule because the Pact states it. The Manual does not decide its own merge semantics.

### 126.8 The Manual is not the law

The Manual is the explanation. The Pact is the law. The Manual must not contain rules that the Pact does not contain. If the Manual says something the Pact does not, either the Pact needs to be amended, or the Manual is wrong, and the Manual is the one that is wrong.

⇒⇒ THE ENFORCEMENT IS OPEN. No script checks that every Manual section cites a Pact rule today. That enforcement is owed. It is named here so the absence is declared, not hidden.

### 126.9 The version

v3.59.0 — Added Part 126: The Manual Rules. The Manual is the per-project, user-facing explanation of the Pact. Every project has one. The topmost Manual references sub-Manuals, not absorbs them. The Manual cites the Pact, never the code. The Manual is written for the operator. The Manual is not the Handbook. The enforcement is declared open.

v3.60.0 — Corrected §126.7: "Project Charter" becomes "Brief". The Brief is the per-project founding document (Part 121 §121.1). The Manual is the explanation. The two are distinct; the merge rule applies to both.

## Part 127 — The Sandbox Family

### 127.1 The two sandboxes

There are two sandboxes in the system. They share a pattern and differ in actor.

**The Builder's Sandbox** is where the AI works. It is a git worktree on a feature branch plus a PB Mirror — a separate PocketBase instance with its own `pb_data` directory, its own port, and a snapshot of the master's data. The Builder edits files in the worktree and runs tests against the mirror. The master's code and master's data are untouched.

**The App's Sandbox** is where the user works. It is a set of three surfaces: the Stencil (the candidate), the Preview (the live recipe, in the sandbox), and the Live (the deployed app). The Stencil shows the candidate with mock data. The Preview shows the live recipe with real data. The Live is the app the user has shipped.

**Both sandboxes are isolation + promotion + gate.** The isolation is a copy. The promotion is a merge. The gate is a check. The pattern is the same. The actor is different.

⇒ THE PATTERN IS THE LAW. The Builder's Sandbox and the App's Sandbox must obey the same shape: copy, merge, gate. A sandbox that skips one of the three is not a sandbox.

⇒ DIRECTION 1 IS SHORT TERM. Make the Builder visible: the Agent Rail shows the Builder's worktree and the Builder's diff, and the user can intervene. The Builder's Sandbox becomes a visible surface.

⇒ DIRECTION 2 IS LONG TERM. Make the App exhaustive: the App's Sandbox becomes a full clone — the Stencil becomes a worktree, the Preview becomes a mirror. Required by the Harvest Protocol. Direction 1 now. Direction 2 later. They are not mutually exclusive.

### 127.2 The data boundary

Data moves between the sandbox and the master under one rule: **the sandbox is a copy. The master is the truth. The promotion is the merge.**

**The PB Mirror mechanics.**

When a Builder job starts, a new `pb_data` directory is created. It is a clone of the master's schema and a snapshot of the master's data, taken at job start. The mirror listens on its own port. The job connects to the mirror, not the master. Later changes to the master are not visible to the job — the job sees the data as it was.

When the job finishes, in success or failure, the mirror is destroyed. The master is untouched.

When the job succeeds and the user approves, a **promotion script** re-applies the job's data changes to the master. The script is a **migration, not a copy**. It runs the same operations the job ran, against the master, with the review gate in force. If a change conflicts with the master's current state, the promotion fails and the job's data is discarded. The master is never overwritten silently.

**The candidate content mechanics.**

Every mock item created in the Stencil carries a `keepState` — one of `pending`, `keep`, `discard`.

The `pending` state blocks. Candidate content does not reach the Preview until every item has been resolved to `keep` or `discard`. The "keep all" option is an explicit checkbox, never a default.

When the user approves the candidate, kept items migrate to real data via the FC Brain adapter. Discarded items are dropped.

Images are design. They pass through. They are not gated. Text, products, prices and copy are candidate content. They are gated. The rule is: **design crosses, candidate content is gated, real data stays.**

For extracted sites, the clean room rule applies: design passes through, text is replaced with candidate content generated from the schema, and real data is used only if the operator explicitly claims ownership.

### 127.3 The two gates and the real bug

Two gates are the enforcement. Both are configurations of the Peek Panel, not separate components.

**The Transition Panel — the Stencil → Preview gate.** It opens on approval. It shows the candidate content list, each item with a keep / discard toggle and its content, so the user sees what they are keeping. It shows the design assets — thumbnail gallery, replaceable — ungated. It shows the "keep all" checkbox as an explicit choice. It shows the discard summary: "3 items will be discarded. 5 items will be kept." The transition button — "Approve and Preview" — is disabled until every candidate item is resolved. **The rule: no candidate content crosses the Stencil → Preview boundary unreviewed.**

**The Deploy Panel — the Preview → Live gate.** It opens on Deploy. It shows the destination (Cloudflare, Vercel, custom domain — whichever the user has configured) and the credentials check (Ready / Add Key). It shows the pre-deploy checklist: unreviewed candidate content (must be zero), proposed decisions not yet current (must be zero), unresolved verifier rejections (must be zero), failing tests (must be zero). The deploy button is disabled until every item is green. The live receipt — buildHash and live URL — appears after deploy. **The rule: no app crosses the Preview → Live boundary without the deploy checklist.**

**The real bug and its fix.** The Preview's data adapter has been pointing at the master's PocketBase, not the mirror. That is why a test record created in the Preview appeared in production. The fix: the Preview's data adapter must point at the **mirror's** PocketBase, selected by the job record's `sandbox` field. If the mirror does not exist, the Preview must **fail to load**. It must not fall back to the master. A fallback is the bug.

⇒ THE FALLBACK IS THE DEFECT. A system that cannot find the mirror and falls back to the master is a system that has just written to production. The mirror must be a hard requirement. No mirror, no Preview.

### 127.4 The Stencil–Part 41 and Part 43 conflict resolved

Part 41 item 4 says: *"When the operator approves the Stencil, the agent promotes it to the Live Canvas by swapping the mock adapter for the real FC Brain adapter."*

Part 43 item 5 says: *"THE GATE IS NOT A PROMOTION; IT IS A VERIFICATION. Approving a Stencil does not make the Candidate the Current Recipe unconditionally — it makes the Candidate the PROPOSED Current Recipe, and the gate is the diff in item 3 that decides whether it may become the Current Recipe. The promotion completes only when the diff is empty."*

**This Part resolves the conflict in favour of Part 43.** Approval is a **verification**, not a promotion. Approving the Stencil makes the Candidate the **PROPOSED** Current Recipe. Promotion to the Live Canvas completes only when the diff is empty. Part 41 item 4 is superseded by this Part; the rest of Part 41 stands.

### 127.5 The Preview surface

The Preview is the live recipe, rendered with real data, in the sandbox. It is **not a copy** of the Canvas — it is the real app, running from the sandbox. It is **not the Live Canvas** — it has not been promoted. Both statements in earlier Parts are true; they describe different aspects of the same surface.

⇒ LINE 7012 AND LINE 6320 ARE RECONCILED. Line 7012's "the canvas is not a copy, a preview, or a simulation" is correct in the sense that the Preview IS the real app. Line 6320's "whether it is the Live surface or the Preview surface, the Canvas can never leak into the Shell" is correct because both surfaces are the Canvas. The Preview is the real app before promotion. Both statements hold.

### 127.6 The version

v3.60.0 — Added Part 127: The Sandbox Family. Two sandboxes (the Builder's worktree + PB mirror; the App's Stencil → Preview → Live), both isolation + promotion + gate. Direction 1 (Builder visible via Agent Rail) is short term; Direction 2 (App exhaustive via Harvest Protocol) is long term. Data boundary: the sandbox is a copy, the master is the truth, the promotion is the merge. The PB Mirror is a separate pb_data snapshot, promoted by migration, destroyed on job end. The candidate content is tagged keepState: pending / keep / discard, with pending blocking and images ungated. Two gates: the Transition Panel (Stencil → Preview) and the Deploy Panel (Preview → Live), both uses of the Peek Panel. The Part 41 / Part 43 conflict is resolved in favour of Part 43: approval is a verification, not a promotion. The Preview surface is the real app running from the sandbox before promotion; lines 7012 and 6320 are reconciled. THE ENFORCEMENT IS OPEN AND DECLARED AS SUCH. The Preview's data adapter currently points at the master's PocketBase, not the mirror; that is a live defect and this Part records the fix: the adapter must point at the mirror, selected by the job record's sandbox field, and must fail to load if the mirror is absent. No fallback.

v3.61.0 — Added Part 128: The Float Surface

## Part 128 — The Float Surface

### 128.1 What the Float Surface is

The Float Surface is the second of the three surfaces of the canvas. It floats over the Base Surface. Its content is free-positioned nodes — sections, columns, widgets, groups — that sit at absolute positions rather than in the page's flow.

⇒ THE BASE SURFACE IS THE FLOW. THE FLOAT SURFACE IS THE OVERLAY. Same kinds, different positioning. The Float Surface uses `position: absolute`; the Base Surface uses the flow.

### 128.2 The same kinds on the Float Surface

The Float Surface uses the same four kinds as the Base Surface: section, column, widget, overlay. The kind is carried by `data-fv-node-kind`. The surface is carried by `data-fv-layer`. A section on the Float Surface is `data-fv-node-kind="section" data-fv-layer="float"`.

⇒ THE KIND IS THE NODE. THE LAYER IS THE SURFACE. Same kind, different layer. A section on the Base Surface is not a section on the Float Surface. They are separate nodes.

### 128.3 The group kind

The Float Surface adds a fifth kind: `group`. A group is a container that holds other float nodes. Its children move with it. The group is a node: it has its own `data-fv-node-id`, its own position, its own size, its own z-index.

The group's children carry `data-fv-group-id` set to the group's id. The group itself carries `data-fv-node-kind="group"` and `data-fv-layer="float"`.

⇒ THE GROUP IS FLOAT-ONLY. The Base Surface does not have groups. Its structure is the flow; the flow has no free-positioned containers.

### 128.4 Grouping and ungrouping

Two operations on any float node or selection of float nodes:

  GROUP — creates a new group node. The selected nodes become its children. The group takes the selection's bounding box as its initial position and size.

  UNGROUP — dissolves the group. Its children return to the Float Surface's root. Their positions are relative to the group's previous position, rebased to the Float Surface.

⇒ BOTH ARE REVERSIBLE. The undo history reverses them. The tree reflects the nesting. The canvas redraws the boundary box.

### 128.5 Copy and float

Two operations on any node:

  COPY — duplicates the node. The copy has a new id. It is a separate node. The original is unchanged.

  FLOAT — moves the node from the Base Surface to the Float Surface. The node is the same node; only its `data-fv-layer` changes. Its position is now absolute. The Base Surface's flow closes the gap.

⇒ COPY IS DUPLICATION. FLOAT IS A MOVE. Copy creates a second node; float relocates the first. Both are reversible. A node on the Float Surface can be "unfloated" — moved back to the Base Surface, at a chosen position in the flow.

### 128.6 The Float panel

The Float layer's panel has the same tabs as the CMS panel — widgets, navigator, tag selector — operating on the Float Surface's structure. It has one additional tab: position controls, for the selected node's top, left, width, height, z-index.

⇒ THE FLOAT PANEL IS THE CMS PANEL PLUS POSITION. The widgets palette is the same shape. The navigator shows the Float Surface's tree. The tag selector filters the Float Surface's kinds. The position controls are unique to the Float panel because the Float Surface's positioning is explicit.

### 128.7 Motion on the Float Surface

Motion (`data-fv-motion`) applies to any node on the Float Surface — sections, columns, widgets, groups. The motion composes across group and child: the group's motion moves the group, the child's motion moves the child within the group. Both play.

⇒ MOTION IS A CROSS-SURFACE CONCEPT. Part 129 owns it. This Part records only that the Float Surface supports it.

### 128.8 The version

v3.61.0 — Added Part 128: The Float Surface. The Float Surface is the second of the three surfaces. It uses the same four kinds as the Base Surface (section, column, widget, overlay) plus a fifth: group. The group holds other float nodes; its children move with it. Grouping and ungrouping are reversible. Copy duplicates a node; float moves it from the Base Surface to the Float Surface; unfloat moves it back. The Float panel has the CMS panel's tabs plus position controls. Motion applies to any float node or group, and composes across group and child. THE ENFORCEMENT IS OPEN AND DECLARED AS SUCH — the Float Surface's structure, the group kind, and the copy/float operations are law to be built, not behaviour to be read.
