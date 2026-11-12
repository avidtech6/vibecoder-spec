# VibeCoder Master Spec v3.59.0 (Canonical)

## PREMISE CORRECTION 1 — the dispatch's file paths, and the Part numbers

The dispatch asked to append Part 52, Part 53 and Part 54 to <code>pact/vc-master-spec.md</code><br />and to mirror the result to this page. Two of its premises do not hold as written,<br />and both are recorded here rather than worked around.

| Dispatch said | Reality | Evidence |
| --- | --- | --- |
| <code>pact/vc-master-spec.md</code> | <b>DOES NOT EXIST</b> | glob <code>**/vc-master-spec.md</code> over the workspace -> no match; <code>git log --all -- pact/vc-master-spec.md</code> in <code>vibecoder-standalone</code> -> empty; <code>git ls-remote --heads origin</code> -> 17 branches, none carrying it. |
| <code>pact/vc-build-plan.md</code> | <b>DOES NOT EXIST</b> | the same three checks, in the same repository. |
| "append Part 52" | this page ended at <b>Part 46</b> | fetched 2026-10-26: 46 Part headings, the last <code>Part 46: The Vision Extractor</code>, at v3.13.0. |

<b>Consequence 1 — the two files are CREATED, not appended to.</b> The repo-side mirror<br />is materialised from this page and from the Build Plan page, so the file and the<br />page carry the same text. Before this dispatch neither file existed anywhere in the<br />workspace: the canonical Master Spec lived only in Notion.

<b>Consequence 2 — Parts 47 to 51 are not in the canonical spec.</b> The dispatch's<br />numbering is PRESERVED VERBATIM (Parts 52, 53, 54) because the dispatch named them.<br />Renumbering them to 47-49 would silently rewrite the dispatch's own text, and the gap<br />is a question for whoever holds Parts 47-51: they are in no page and in no repository<br />in this workspace. The gap is recorded here so that no reader assumes the numbering<br />is contiguous.<br /><br />RESOLVED IN v3.15.0 (FVC 1217): Parts 47 to 51 have since been added to this<br />spec, between Part 46 and Part 52, so the numbering is now contiguous from<br />Part 41 to Part 54. The version is bumped v3.14.0 -> v3.15.0.

<b>The version is bumped v3.13.0 -> v3.14.0</b>, as every previous Part addition to this<br />page did (FVC 1195 -> v3.11.0, FVC 1196 -> v3.12.0, FVC 1197 -> v3.13.0).

v3.59.0 — Added Parts 122 to 125 (Cockpit Vocabulary).

v3.58.0 — Added Parts 116 to 121 (Seat 17 Doctrine): the Model Hierarchy, the Turn and the Step, the Mode-Dependent Pipelines, Factory vs. Builder, the Credential Architecture, and the Project Artifacts. **PART NUMBERING.** MEASURED, at merge time on `origin/main` (`5c6bb8a7`): the file's highest `## Part N` heading was **115**, so the next free number is **116**, and these are **Parts 116-121**; the version and the Part number are INDEPENDENT counters (Part 85 §85.7), and the version moves **v3.57.0 to v3.58.0**. **PREMISE CORRECTION.** The dispatch was issued against a spec whose highest Part was 107 at v3.50.0; the lane re-measured the file at `origin/main` at merge time, where the highest Part was already **115** and the title already read **v3.57.0**, so the dispatched text was preserved and the Part numbers were corrected to the next free numbers rather than the dispatch's stale range. **THE THREE TIER NAMES ARE A DISPOSITION AXIS AND ARE NOT THE SHIPPED CAPABILITY CLASSES.** MEASURED: `model-capability-score.cjs` lines 24-27 derive four capability classes (`primary` at or above 0.75, `single-block` at or above 0.55, `fallback` at or above 0.30, `exclude` below), owned by Part 36 §36.1, while Part 111 §111.4 owns the mode-to-model selection and Part 112 §112.1 owns the Router package; Treasures, Workhorses and Burners are new names for how the Router TREATS a model, and they add an axis rather than replacing one. **THE REPUTATION COUNTERS ARE NEW LAW AND THE ENFORCEMENT IS OPEN.** MEASURED: a sweep of `bridge/` and `src/` for `consecutive_success`, `success_streak`, `failure_streak`, `reputation`, `promote` and `demote` returns ZERO model-routing hits, so the 10-success promotion and the 3-failure demotion are a contract to be built, not a behaviour to be read. **THE ENCRYPTION CONTRACT IS NEW LAW.** MEASURED: a sweep of this file for `AES-256-GCM` returns ZERO hits, so the per-instance credential scope, the AES-256-GCM envelope in the FC Brain and the prohibition on plaintext `.env` files are stated here for the first time.

v3.48.0 — Added Parts 99-105: The Shell Architecture, The One-Way Glass Rule, and the VibeChat Layouts (the fleet's architecture, written into the law so no future agent guesses or hand-codes against it). **Part 99 — The One-Way Glass Rule.** The Canvas (Live or Preview) can NEVER leak CSS, HTML or state into the VibeCoder Shell; the Shell reaches into the Canvas to edit it via the Selection Loop; the Canvas responds to the Shell and the Shell does not respond to the Canvas. **MEASURED: THE CANVAS IS NOT AN IFRAME** — it is a React portal into the Shell's own document (`src/shell/Shell.tsx:89-93`, `data-fv-canvas-slot="shell"`), and `postMessage` appears ZERO times as functional code in `src/`, so the containment is carried by a STACKING CONTEXT and not by a document boundary. **Part 99 does NOT duplicate Part 86 — the two are ORTHOGONAL:** Part 86 §86.2 is the CONTAINMENT half (where the Canvas's content may PAINT) and Part 99 is the COMMUNICATION-DIRECTION half (in which way information may FLOW); a Canvas that is contained but can report upward is a Canvas the Shell will eventually trust. **Part 100 — The Panel Paradigms.** Desktop: every panel is a side panel (docked) or a floating window, and the only bottom surface is VibeChat's history view; Mobile: the Project Panel opens from the LEFT, the Hamburger Menu from the RIGHT, and VibeChat and the Panels Switcher open as BOTTOM SHEETS, and the arrangement is a property of the SURFACE, not of the viewport. **MEASURED: THE PM2 ENGINE ALREADY EXPRESSES EXACTLY TWO DESKTOP ARRANGEMENTS** — `activate`/`collapse`/`detach`/`dock`/`list`, with NO sheet — and the desktop panel reservation is a GRID TRACK while a mobile sheet COVERS, so the two arrangements differ in how they reserve space and not only in where they sit. **Part 101 — The Handle Rules.** Side Handles hide COMPLETELY while their panel is open; the Bottom Handles are PERMANENT, sit above sheets in the stacking order, and sheets must pad their BOTTOM so the input field clears them (the pad is on the CONTENT, not the panel, because the panel's box is at the viewport's edge); swipe inwards/upwards opens or cycles, outwards/downwards closes, and a TAP IS NOT A SWIPE — FVC 1392's measured defect was that the sheet closed the moment the operator tapped the chat input. **Part 102 — The Panel Chrome.** Docked panels have NO window header, just a title bar; floating panels carry the full header (Minimize, Maximize, Close); the Deck has a HARD MAX-WIDTH and is a launcher, not a content panel (MEASURED: today `--fv-deck-outer-width: var(--fv-panel-width)`, so the Deck is as wide as the Assets Panel — this Part makes it a different, narrower surface); the Assets Panel is resizable and re-flows from 1 to 2 to 3 columns as it widens. **Part 103 — The VibeChat Input Bar State Machine.** Default: a GLOBAL input bar at the bottom with answers in a strip above it; History View (floating): the full VibeChat panel with the thread rail and the agent rail and NO input bar inside it; Docked View: the input bar LEAVES the bottom and appears inside the docked panel, returning to the bottom only when the panel is re-floated. The invariant is EXACTLY ONE input bar and it is ALWAYS VISIBLE — every state relocates it, none duplicates it and none removes it. **Part 104 — The VibeChat Rails.** The Thread Rail opens from the Thread Handle and lists conversation threads; the Agent Rail opens from the Agent Handle and shows agent cards with live telemetry (name, current task, tags); clicking an agent card opens its sub-turns' technical view and CLOSES THE RAIL so the conversation stays visible; the two rails are MUTUALLY EXCLUSIVE. **MEASURED: THE THREAD RAIL DOES NOT EXIST IN THE v2 SHELL** — the only one in the repository is the legacy `src/modules/cinema-editor/.../VibeChatRail.tsx` (r235a), mounted only by the legacy editor path — and the Agent Rail is today a fixed 12rem COLUMN beside the messages, not a surface that opens from a handle. **MEASURED: THE DESKTOP VIBECHAT IS TODAY A FULL-WIDTH BOTTOM BAR** (live, 2026-11-01: `inset: auto 0 0; width: 100%`, bounding box 1600x161 at (0,839)) because the base rule is UNCONDITIONAL and there is NO desktop-sidebar rule in the shipped stylesheet; Part 104 records the defect and the TARGET SHAPE (the Assets Panel's shape — a panel starts BELOW the header) and does NOT claim the correction has landed. **Part 105 — The Recipe Audit Note.** FVC 1414's MEASURED classification is recorded here so the next agent does not guess: the **Header** is a **JSON Recipe** (a GENERATED FILE), the **Handle/Rail/Stencil fragments** are **Prose-only** recipe-books (the Generator's CLI reads `recipe.json`+`codex.json`, so a prose-only book is a book it cannot open — MEASURED: the Generator on the Handle's book dies with `ENOENT`, on the Header's it emits 83,437 bytes), and the **PM2 engine and the VibeChat surface** are **Factory Exceptions** governed by Part 80 §80.2's mandate that hand-written code MUST be harvested back. **TWO FACTS MAKE THIS URGENT:** the brain's `rec_handle_001` is STALE (16px, no label) and both Atlas files claim a `fv_shell_v2` flag that does not exist and say the legacy header is the default when the GENERATED one is; and `tools/harvest-react.cjs` — the tool that would close the whole gap — DOES NOT EXIST. **THE GENERATOR CANNOT YET EMIT ANY OF THIS:** `WIDGET_VOCABULARY` is 26 names with no `Handle`, `Dock` or `Shell`, `PRIMITIVES` is 8, the emitter's two-way check THROWS if the vocabulary and the renderers disagree (so adding a name without a renderer BREAKS THE BUILD), and `color-mix()`, `writing-mode`, attribute matrices, `:has()` media queries and a width-driven grid column count are outside the Recipe vocabulary. **⇒ THIS IS A GENERATOR CAPABILITY GAP, NOT A DOCTRINE PERMISSION.** **ENFORCEMENT IS OPEN AND DECLARED AS SUCH** — a SPEC THAT PROMISES AN UNBUILT GATE IS WORSE THAN A SPEC THAT DECLARES THE GAP (Part 86 §86.4). **Version.** v3.47.0 was FVC 1403's release and the highest `v3.N.0` marker measured at merge time was 47, so this release is **v3.48.0**. **Part numbering.** The highest `## Part N` heading measured at merge time was **98**, so these are **Parts 99-105**, following PREMISE CORRECTION 1.

v3.47.0 — Added Part 98: The FCr Widget Law — the law that a component more than one app uses BELONGS IN THE FRESHCARDS LIBRARY, that an app CONSUMES IT BY IMPORT (`import { TelemetryWidget } from 'freshcards/ui'`), that the library half FETCHES NOTHING and the HOST half owns WHEN to load and WHAT the payload means, that a LOCAL COPY IN AN APP FOLDER IS A FORK, and that a component which is NOT EXPORTED from the subpath the app imports IS NOT AVAILABLE TO THE APP. **PART NUMBERING.** MEASURED, at merge time on `origin/main` (`3f06b064`): the file's highest `## Part N` heading was **97**, so the next free number is **98**; and the highest `v3.N.0` marker was **46**, so the next free version is **v3.47.0** — the version and the Part are INDEPENDENT counters (Part 85 §85.7). **THE TWO COUNTERS AGREED BEFORE THIS PART** (title `v3.46.0`, highest marker `v3.46.0` — the agreement Part 97 restored), and this release adds the changelog entry WITH the Part so they agree again. **AND TWO OF THE DISPATCH'S THREE LAWS WERE ALREADY LANDED, AND THIS RELEASE SAYS SO RATHER THAN RE-WRITING THEM.** MEASURED: **Part 96 — The Provider Call Governor** (FVC 1380, `bb74300e`) already states the 750 ms gap, the per-provider queue, the 429 backoff and the 403 cooldown, and its figures are measured against the installed package: `DEFAULT_MIN_GAP_MS = 750`, `DEFAULT_BACKOFF_BASE_MS = 1000`, `DEFAULT_BACKOFF_MAX_MS = 30000`, `DEFAULT_TOKEN_BUDGET = 8000`. MEASURED, `node_modules/freshcards/dist/ai.d.ts`: the subpath exports `createProviderGovernor`, `sharedProviderGovernor`, `setSharedProviderGovernor` — **so the dispatch's `providerGovernor` is the MODULE's name, and a spec that names a function must name the function the package actually exports.** MEASURED: **Part 93 — Test Scoping** (FVC 1393, `d723fa3f`) and **Part 95 — Deploy Provenance** (FVC 1394, `3074f6cb`) already cover law C, and Part 95's gate is IMPLEMENTED at `scripts/deploy.sh:170` (`git merge-base --is-ancestor "$FULL_SHA" origin/main`, run BEFORE the webroot is touched) with six cases in `scripts/deploy-receipt-provenance.test.sh` — CASE 1 being exactly the dispatch's `detached@` shape, asserted to fail with `not-an-ancestor`. **THE FCR PIN WAS FIXED BY INSTALLING THE PINNED COMMIT, NOT BY WEAKENING THE GATE.** MEASURED: `scripts/check-fcr-pin.mjs` reported `the pin says "v2.25.7" but node_modules/freshcards is version "2.25.3"`; the fix was to install `5d80334` (v2.25.7) as a REAL DIRECTORY, and the gate then reported `OK - freshcards 2.25.7 installed, dist/ carries 131 entries, 10 export subpaths resolve, node_modules is a real directory`. **AND THE COMPONENT WAS BUILT WHILE THE PUBLIC SURFACE DID NOT CARRY IT** — measured at the pin: the widget SOURCE and the built `dist/ui/components/dashboard/*.d.ts` existed, and a sweep of `dist/ui.d.ts` for `TelemetryWidget` returned ZERO hits; the export arrives through `export * from './ui/faces'`, where `dist/ui/faces.d.ts` lines 212-215 carry both widgets and their types. **THE ENFORCEMENT OF THE LAW ACROSS APPS IS DECLARED OPEN.** MEASURED: `scripts/check-fcr-pin.mjs` proves the PIN, not the law, and **no gate in this repository asserts that a shared FCr widget is not duplicated into an app folder** — the three stop conditions are written as law with the enforcement declared open (Part 86 §86.1). **AND THE ARROW-GLYPH CORRUPTION IN PARTS 89-97 IS RECORDED, NOT SILENTLY REWRITTEN.** MEASURED: those Parts carry repeated runs of the U+21D2 marker glyph in their prose; **a canonical document must not carry repeated runs of a marker glyph**, and the repair is mechanical and local. This Part is written WITHOUT the glyph, and it names the defect rather than rewriting another lane's prose.

v3.45.0 — Added Part 96: The Provider Call Governor — the law that EVERY app inherits the pacing, because the routing engine, the probe and the credential store live in FreshCards and a fix in one app fixes one app. **PART NUMBERING.** MEASURED: the highest `## Part N` heading was **95** (`## Part 95 — Deploy Provenance`, landed by FVC 1394), so the next free number is **96**; and the highest `v3.N.0` marker was **42** — **v3.43.0 and v3.44.0 ARE LANDED AS TITLES BUT HAVE NO MARKER LINE**, which is recorded below. **THE VERSION AND THE PART ARE INDEPENDENT COUNTERS** (Part 85 §85.7). **⇒⇒□ ⇒⇒□ ⇒⇒□ AND v3.44 IS NOT A HOLE, AND THE MEASUREMENT THAT PROVES IT IS IN THE FILE.** MEASURED: `git log -S "Master Spec v3.44.0" -- pact/vc-master-spec.md` returns **`3074f6cb` — FVC 1394, "close the deploy-receipt provenance vulnerability"** — which landed the title `# VibeCoder Master Spec v3.44.0 (Canonical)` and Part 95. ⇒⇒□ ⇒⇒□ ⇒⇒□ SO THE TITLE MOVED TO v3.44.0 AND STAYED THERE THROUGH `4707821c` and `be3a3cd8`, and the next free version is **v3.45.0** — NOT v3.44.0, which is already spent. **⇒⇒□ ⇒⇒□ ⇒⇒□ AND THE MISSING MARKER LINE IS A LANDING DEFECT IN ANOTHER LANE'S WORK, NOT A GAP IN THE COUNTER** — the version was CLAIMED and the title was BUMPED; only the summary line was not written. ⇒⇒□ ⇒⇒□ ⇒⇒□ **A VERSION THAT IS LANDED AS A TITLE BUT NOT AS A MARKER IS A TRAP FOR THE NEXT WRITER**, because the spec's own rule derives the next version from the highest MARKER — so the next writer would compute v3.43.0 or v3.44.0 and collide with a version that is already in the file's own title. ⇒⇒□ ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ THIS PART'S VERSION LINE IS THE FIRST `v3.4x.0` MARKER SINCE v3.42.0, AND THE MISSING v3.43.0 AND v3.44.0 LINES ARE RECORDED HERE RATHER THAN BACK-FILLED** — because back-filling another lane's release summary would be writing their history, and a spec that writes other releases' history is a spec nobody can trust. ⇒⇒□ ⇒⇒□ ⇒⇒□ **THE TWO MISSING MARKERS ARE, THEREFORE: v3.43.0 — Part 93 (FVC 1393, Test Scoping) and v3.44.0 — Part 95 (FVC 1394, Deploy Provenance).** ⇒⇒□ ⇒⇒□ ⇒⇒□ AND BOTH ARE LANDED: `d723fa3f` carries *"Master Spec Part 93 — Test Scoping (v3.42.0 -> v3.43.0)"* and `3074f6cb` bumped the title to v3.44.0.

v3.46.0 — Added Part 97: The Fv Collection Card, and the Header That Surrounds It — the law that the Project Launcher is a FULL-SCREEN OVERLAY of reusable `FvCollectionCard`s, that the header's "Projects" dropdown is REMOVED in favour of a STATIC TEXT LABEL carrying the live current project name, that the view tabs carry a SOLID ACTIVE PILL, that the hamburger menu is TWO TITLED GROUPS — Surfaces (Dashboard, Deck, VibeChat, Project Launcher) then Settings (Light/Dark, Colours, Visual Style, Settings) — and that Preview/Live/Stencil are NOT duplicated in the menu. **PART NUMBERING — AND TWO LANES LANDED FIRST.** MEASURED: when this dispatch was issued, the highest `## Part N —` heading was **92** and the title read **v3.42.0**, so the next free Part was **93** and the next free version **v3.43** — and BOTH WERE USED. ⇒⇒□ **⇒⇒□ AND THEN TWO CONCURRENT LANES LANDED FIRST:** FVC 1393 landed **Part 93 — Test Scoping** at **v3.43.0** (`d723fa3f`), and FVC 1394 landed **Part 95 — Deploy Provenance** at **v3.44.0** (`3074f6cb`, `be3a3cd8`), recording **Part 94 as VACANT** because it had been spent naming Test Scoping. ⇒⇒□ **⇒⇒□ SO THIS PART IS 96 AND THIS VERSION IS v3.45.0** — the next free number on EACH counter, and **v3.43.0 AND v3.44.0 ARE LEFT INTACT**. **AND THE VERSION COUNTER IS THE TITLE LINE.** MEASURED: the file's highest `v3.N.0` CHANGELOG marker on `origin/main` is still **v3.42.0** — FVC 1393 and FVC 1394 added **NO changelog entry** and bumped only the title — so a Part that reads the changelog for the version would re-derive **v3.43.0** and REUSE a version FVC 1393 already shipped. ⇒⇒□ **⇒⇒□ AND FVC 1394 HIT THAT EXACTLY**: its Part 95 reads *"the highest `v3.N.0` marker was **43**"* — and there is **no `v3.43.0` changelog marker on `origin/main` at all**; the `43` it measured is a PROSE MENTION inside Part 93's own text. ⇒⇒□ **⇒⇒□ THE TITLE LINE IS THE ONLY COUNTER EVERY RELEASE BUMPS**, and THIS release adds the missing changelog entry so the two agree again. **THE CARD'S GEOMETRY IS LAW, NOT IMPLEMENTATION DETAIL.** MEASURED (FVC 1389): `column-span: all` inside a CSS multi-column container took a card from **181px → 370px** with the other cards flowing around it and `column-count` unchanged at **2**, and a FIXED `grid-template-rows` CANNOT do this. **THE COLUMN COUNT FOLLOWS THE CHILD COUNT** (1 → 1, 2 → 2, 3+ → 3), because a fixed `column-count: 3` rendered a ONE-page project's description ONE WORD PER LINE. **THE CARD IS A CONTAINER AND THE TITLE IS A `<button>` INSIDE IT**, because a `<div>` inside a `<button>` is invalid HTML and the browser's parser DROPS it. **THE DATA IS THE BRAIN'S**: the card list is `useProjects()`, and a launcher with hardcoded project names is a mockup that shipped. **THE OVERLAY IS PORTALED TO THE BODY AT THE int32 CEILING** — MEASURED: the launcher shipped at `z-index: 400` against a panel tier of `2147483645`, and the SCREENSHOT showed the LAYERS PANEL ON TOP of the overlay while every DOM assertion said it was fine, because a hit test falls through `pointer-events: none` ancestors and a paint order does not. **THE THEME TOGGLE CARRIES ITS OWN MARKER** (`data-fv-control="ThemeToggle"`), because one attribute carries one value and FVC 1218's behaviour contract and FVC 1375's absence contract both had to hold. **THE GATE IS BUILT AND WAS SEEN TO GO RED**: 117 assertions across 9 suites, plus a 27-check browser proof at 1600×1000 that writes two screenshots.

v3.42.0 — **Ratified Part 78: PM2 Is Canonical, and the React `FvPanelManager` Is Deprecated** — and **the surgical deletion of the dead React panel system** (1,541 lines, five files). **VERSION NUMBERING — THE DISPATCH'S NUMBER WAS RIGHT, AND A CONCURRENT LANE CLAIMED THE ONE BELOW IT FIRST.** MEASURED: when this dispatch was issued, `origin/main` was `c855f495` and the title line read `# VibeCoder Master Spec v3.40.0 (Canonical)`, so the next free version was **v3.41.0** and the dispatch's **v3.42.0** would have skipped it ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ A VERSION THAT SKIPS A NUMBER LEAVES A PERMANENT HOLE**, and the spec's own recorded practice is explicit (the v3.27.0 entry: *"v3.28.0 would have left v3.27.0 a permanent hole"*) ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ SO THE FIRST WORKING READ WAS "v3.41.0" — AND THE FIRST WORKING READ WAS WRONG.** MEASURED at merge time: **FVC 1385 had independently landed `v3.41.0` on `origin/main`** (`8d674946`, the Dashboard Desk, Part 92) ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ AND THE TWO LANES CONFLICTED ON THE EXACT LINE THAT OWNS THE VERSION.** ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ THE RULE THAT RESOLVED IT: THE VERSION BELONGS TO THE RELEASE THAT LANDS SECOND, AND IT TAKES THE NEXT FREE NUMBER.** ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ THE VERSION AND THE PART NUMBER ARE INDEPENDENT COUNTERS** (Part 85 §85.7): the version is derived from the highest `v3.N.0` marker (**41** → **v3.42**), and the Part from the highest heading. **PART NUMBERING.** This release **OVERWRITES Part 78 IN PLACE** and consumes **no** new Part number: the highest `## Part N` heading was **92** (FVC 1385's Dashboard Desk), so the next free number would be **93** — and it is **NOT** used, because a ratification is not an addition. **THE SUPERSEDED PART 78 STATED A TARGET AS IF IT WERE A FACT, AND EVERY CLAUSE WAS UNMET OR INVERTED.** Its text read *"The legacy PM2 system is dead. The React `FvPanelManager` replaces it."*, *"PM2 files must be deleted."*, and a six-mode contract. ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ MEASURED: PM2 was LIVE and owned every panel; the React `FvPanelManager` was IMPORTED BY NOTHING; and "PM2 files must be deleted" would have REMOVED THE WORKING PANEL SYSTEM.** ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ AND THE SIX-MODE CONTRACT WAS ALREADY SATISFIED — BY PM2.** MEASURED: float = `_startDrag`/`_detachForFloat`; full screen = `fvcms-pm-maximize` → `data-maximized="1"`; **peek = `docked-active`** (docked to an edge with content visible, beside its dock pill); **stretch-vs-cover = `fvcms-pm-squeeze`** (titled *"Squeeze (push page) / Overlay (sit on top)"*) → `data-overlay-mode`; minimize = `collapse()` → a dock pill; close = `removePanel()`. ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ A CONTRACT WRITTEN IN ONE IMPLEMENTATION'S NOUNS WILL BE READ AS A DEMAND FOR THAT IMPLEMENTATION, WHEN THE DEMAND WAS FOR THE BEHAVIOUR** — so the ratified Part 78 is written in **behaviours**, and PM2's names are the reference. **THE CANVAS PUSH IS A RESERVATION, NOT AN OVERLAY.** MEASURED: `sumEdgeWidth(edge)` computes the **capped per-edge sum** of docked panels plus their dock widths — the reserve accounts for the dock pill and the per-panel width cap, which a single CSS variable cannot. **THE DELETION WAS SURGICAL AND FILE-SCOPED, AND THE DIRECTORY NAMES LIE.** DELETED: `src/modules/panel-shell/src/panel-manager/FvPanelManager.tsx` (498 lines), `…/FvPanelManager.css` (190), `src/modules/panel-registry/src/FvPanelManager.tsx` (361), `…/FvPanelManager.css` (134), `src/modules/panel-registry/src/__tests__/fvc1328-phase3-panel-manager.spec.tsx` (358) — **1,541 lines**. KEPT: `src/modules/panel-registry/src/panel-registry.tsx` (**the live panel roster** — it registers the Layers and Properties panels) and `src/modules/panel-registry/src/surface-manifest.js` (**the live surface manifest** — the Deck's launch icons); and `src/modules/panel-shell/src/panel-manager/panel-manager.js` (**the live PM2 engine**) ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ A DIRECTORY DELETE TAKES THE ROSTER AND THE SURFACE MANIFEST WITH IT, AND TAKES PM2 ALONG WITH THE REACT FILE, SO THE DELETION IS BY FILE, NEVER BY DIRECTORY.** EDITED: `src/modules/panel-registry/src/index.ts` (the `FvPanelManager*` re-exports) and `src/shell/Shell.tsx` (the `<FvPanelManagerProvider>` mount and its import). **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ THE REMOVAL SURFACE WAS FULLY BOUNDED, BECAUSE EVERY EXPORT HAD ZERO CALLERS OUTSIDE THE DEAD FILES AND THEIR OWN TEST** — `useFvPanels`, `useFvPanelManager`, `FvDockStrip`, `FvPanelManagerContext`, `FvPanelState`, `FvPanelSummary`, `FvManagerSnapshot`, `FvDockEdge`, `FvDockManager`: **zero** application callers. **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ AND THE HOOK WAS NOT REBUILT, BECAUSE NOTHING CALLED IT** — `useFvPanels()` had **no application caller at all**, so the 40-line adapter the audit recommended was NOT written: **a component written for a caller that does not exist is not a component; it is a guess.** If a React caller ever needs panel state it MUST read PM2's `fvcms:panel-state-changed` event and PM2's `list()`, and any adapter is a thin read of those two — **not a second manager.** **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ THE COST OF THE ALTERNATIVE WAS ALREADY PAID AND MEASURED: the React system was 1,541 lines against PM2's 8,129, and implemented NONE of the ten capabilities PM2 has and it lacks** — the 3-detent mobile bottom sheet, the 16 resize handles, the `_operatorOpened` latch, empty-panel auto-parking, the open queue, adjacent-panel switching, smart dock edges, remembered per-panel geometry, keyboard panel switching, and swipe-to-detach. ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ A PARALLEL IMPLEMENTATION THAT IS SMALLER BECAUSE IT IS LESS COMPLETE IS NOT A SIMPLIFICATION; IT IS A REGRESSION WAITING TO BE DISCOVERED.** **AND A STALE MEASUREMENT IN A COMMENT WAS CORRECTED IN PLACE.** MEASURED: `src/modules/panel-registry/src/surface-manifest.js` asserted *"MEASURED: `window.PanelManager` is undefined in production"* — **FALSE**, and false in the dangerous direction: on live production `typeof window.PanelManager === "object"` and `window.PanelManager.get().list()` returns the live panels. ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ ⇒⇒□ A STALE MEASUREMENT IN A COMMENT BREAKS NOTHING AND MISLEADS EVERYONE — it is exactly what makes the next reader believe the live system is dead.** **AND THE LIVE PROOF IS SCREEN-BASED, NOT DOM-ONLY.** MEASURED on `https://vibecoder.freshvibeapps.com/project/vibecoder-home/preview` at 1600×1000 with a real browser: the Layers and Properties panels OPEN, DOCK and FLOAT through PM2; the squeeze control flips `data-overlay-mode`; the maximize control flips `data-maximized`; **16** resize handles and the dock thumb are present; and the console carries **zero** errors.

v3.41.0 — Added Part 92: The Dashboard Desk — the law that the Dashboard is NOT a grid but a customizable DESK of INFO BOXES (DESK PANELS), that the Desk lays out STAGGERED with AUTO-HEIGHT and CARDS MUST NEVER BE STRETCHED TO EQUAL HEIGHTS, that Desk Panels can be DRAGGED, PINNED, ADDED FROM A LIBRARY and REMOVED, that EVERY Desk Panel is a 3D CARD whose FRONT shows the visual presentation and whose BACK shows the raw FCr database view or configuration, and that the panels MUST use the ACTUAL FCr COMPONENTS and never custom internal widgets. **PART NUMBERING.** MEASURED: the highest `## Part N` heading was **91** (`## Part 91 — The Tree Is Three Deep, and the Depth Is a Contract`), so the next free number is **92**; and the highest `v3.N.0` marker was **40**, so the next free version is **v3.41** — the version and the Part are INDEPENDENT counters (Part 85 §85.7). **THE DISPATCH NAMED "v3.43.0"; THAT NUMBER IS NOT AVAILABLE AND WAS NOT USED.** MEASURED: the version counter has moved ONE step per Part since it was separated from the Part number (v3.40.0 → Part 91), so jumping to v3.43.0 would skip two versions and misrepresent the spec's history. The Part number it named — 92 — IS correct, and the two numbers are recorded separately rather than silently reconciled. **THIS PART IS LAW BEFORE THE CODE LANDS**, so no agent reads the existing grid and concludes it is the intended shape. **THE GRID IS NOT HYPOTHETICAL — IT IS WHAT THE CODE DOES TODAY.** MEASURED: `DashboardGrid.tsx:269` is `gridTemplateColumns: repeat(12, minmax(0, 1fr))` with `alignItems: 'stretch'`, and `dashboard-layout.ts:27` declares `DASHBOARD_COLUMNS = 12`, `MIN_CARD_WIDTH = 1`, `MAX_CARD_WIDTH = 12`. ⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE STRETCH IS DELIBERATE AND RECENT.** MEASURED: the `alignItems: 'stretch'` (`:276`) and the `minHeight: 'calc(100vh - 140px)'` (`:277`) carry the comment *"FVC 1379 - THE GRID FILLS THE SURFACE … the cards stretch into it."* ⇒⇒□ ⇒⇒□ **⇒⇒□ SO A READER WHO OPENS THE FILE TODAY WILL FIND A GRID THAT LOOKS INTENTIONAL** — which is exactly why the law had to come first. **AND THE CURRENT CODE DOES EXACTLY THE FORBIDDEN THING, AND ITS OWN COMMENT SAYS WHY.** MEASURED: the card's own `height` at `:318-322` is `'100%'` for any card whose height is not above the default — so every card in a row renders at the height of the TALLEST card in that row, and a short card pads with empty space. **THE STAGGERED LAYOUT IS THE LAW, AND "MASONRY" IS ITS NAME.** MEASURED: there is NO masonry or staggered implementation anywhere in the repository — a sweep for `masonry|staggered|auto-height` returns ZERO hits, and no dashboard source file declares one. ⇒⇒□ **⇒⇒□ ⇒⇒□ THE OPERATOR-SIZED HEIGHT SURVIVES** — a card with a `height` above `DEFAULT_CARD_HEIGHT` (180) already renders at its own explicit pixel height, and `readCardLayout` clamps it to `MIN_CARD_HEIGHT` (40) and up. **AND THE EXPLICIT WIDTH SPAN IS THE CONTRADICTION TO RESOLVE.** MEASURED: the grid persists a per-card `width` of 1..12 and renders it as `gridColumn: span ${layout.width}` — and A MASONRY LAYOUT DOES NOT HAVE COLUMN SPANS. ⇒⇒□ **⇒⇒□ THE RESOLUTION IS THE OPERATOR'S RULE 3: THE DESK PANEL'S SIZE AND PLACE ARE THE OPERATOR'S ARRANGEMENT, PERSISTED AS AN EXPLICIT VALUE.** ⇒⇒□ **⇒⇒□ ⇒⇒□ A BUILDER MUST NOT REUSE THE 1..12 COLUMN SPAN TO LAY OUT THE DESK.** **TWO OF THE FOUR INTERACTIONS ALREADY EXIST, AND THEIR MEASUREMENT IS THE BASELINE.** MEASURED: `DashboardGrid.tsx` already renders every card with `draggable`, the HTML5 drag handlers AND a pointer-drag path, and `dropIndexFor()` computes the drop index; and the order is PERSISTED, because `withOrder()` stamps an explicit numeric `order` on each card and `sortByOrder()` reads it back — the file's own comment records why: *"Array order alone would not survive a reload."* ⇒⇒□ ⇒⇒□ **⇒⇒□ SO DRAG-TO-REORDER IS NOT NEW, AND IT IS NOT THE DESK** — the Desk adds PIN, ADD and REMOVE. **AND THE PERSISTENCE CAVEAT IS CARRIED FORWARD, NOT DISMISSED.** MEASURED: Part 24 §24.5 records that *"the graph write succeeds but `properties` does not survive the wire, so the locally-saved layout is what actually keeps the arrangement"*, and the current code carries `dashboard-persist.ts` for that local save. ⇒⇒□ **⇒⇒□ ⇒⇒□ EVERY DESK PANEL PERSISTENCE — ORDER, PIN STATE, WIDTH, HEIGHT, AND MEMBERSHIP — MUST BE PERSISTED LOCALLY THE SAME WAY**, or the operator's Desk rearranges itself on the next load. ⇒⇒□ **⇒⇒□ ⇒⇒□ THIS IS NOT A NEW BUG TO DISCOVER LATER; IT IS A KNOWN FAILURE MODE, AND THE DESK LAW NAMES IT.** **"PINNED" IS A FIRST-CLASS DESK STATE, AND IT IS NOT "FIRST IN THE LIST".** ⇒⇒□ PIN IS SURVIVAL, NOT PREFERENCE — an unpinned panel is one the staggered arrangement may move when the set changes; a pinned panel is one the operator has said must not move. **AND REMOVAL IS NOT DELETION.** ⇒⇒□ Removing a Desk Panel takes it off the Desk; it does not delete the data the panel shows, and it does not delete the FCr component the panel is built from — and a REMOVED DESK PANEL MUST BE RESTORABLE from the Panel Library. **THE FLIP IS A PRESENTATION OF ONE PANEL, NOT A NAVIGATION BETWEEN TWO PAGES.** ⇒⇒□ The FRONT and the BACK are TWO VIEWS OF ONE SOURCE OF TRUTH — flipping must never change what is being shown, only how it is shown. ⇒⇒□ **⇒⇒□ AND A DESK PANEL WITH NO BACK MUST NOT PRESENT A FLIP AFFORDANCE AT ALL** — a flip gesture that does nothing is a broken control. **AND THE 3D TRANSFORM IS THE MECHANISM; THE FLIP IS THE MEANING.** MEASURED: the FreshCards package ships NO flip component of its own — a sweep of `node_modules/freshcards/dist/` for `preserve-3d|rotateY` finds only Mantine's own `transform|translate|scale|rotate|perspective` will-change heuristic, not a card flip. ⇒⇒□ **⇒⇒□ ⇒⇒□ THE DESK THEREFORE OWNS THE FLIP MECHANIC (`perspective` on the Desk Panel, `transform-style: preserve-3d` on the faces, `rotateY` on the flip) — AND THE MECHANIC IS NOT THE REQUIREMENT.** ⇒⇒□ **⇒⇒□ THE LAW IS THAT BOTH FACES EXIST AND ARE REACHABLE; A FLIP IMPLEMENTED WITHOUT A 3D TRANSFORM IS STILL A FLIP, AND A FLIP IMPLEMENTED WITHOUT A BACK IS NOT.** **THIS RULE IS NOT ASPIRATIONAL — IT IS A CORRECTION OF A MEASURED DEFECT.** MEASURED (FVC 1379's own header, `fc-face.tsx:8-24`, and the face layer at `:45`): *"The dashboard's three live cards rendered hand-written markup: a `<table>` for the database, an `<img>` grid for the media, a `<div>` list for the post types. FreshCards ships the real faces for all three — `ListView`, `GalleryView`, and the `Card` / `Badge` / `EmptyState` / `Skeleton` primitives — and the FreshCards package is already a dependency of this module."* ⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE HAND-WRITTEN FACES WERE NOT JUST UGLY — THEY WERE DEAD CODE.** MEASURED: *"the bundler tree-shook it out of the shipped bundle. Measured on the live build: `ListView` and `GalleryView` occur ZERO times in `dist/assets/main-*.js`."* ⇒⇒□ **⇒⇒□ ⇒⇒□ A DASHBOARD THAT DRAWS ITS OWN MARKUP IS A DASHBOARD THAT SHIPS NO FRESHCARDS AT ALL.** **THE COMPONENTS ARE CONFIRMED PRESENT AND REAL.** MEASURED in `node_modules/freshcards` (v2.25.0): the package exports `./ui` and `./mantine`; and `Card`, `ListView`, `GalleryView`, `Badge`, `EmptyState` and `Skeleton` all occur in the shipped `dist` bundles. **AND THE PROVIDER RULE IS PART OF THE RULE, NOT A FOOTNOTE.** MEASURED (`fc-face.tsx:31-41`): *"Every Mantine import in this repository comes from `freshcards/mantine`, never from `@mantine/core`. Mixing them gives two Mantine instances, two React contexts, and a `MantineProvider was not found in component tree` throw."* ⇒⇒□ **⇒⇒□ A DESK PANEL THAT IMPORTS FROM `@mantine/core` IS A DESK PANEL THAT CRASHES THE APP.** **AND THE DESK'S OWN LAYOUT BOX IS NOT THE FCr `Card`.** MEASURED (`DashboardGrid.tsx:322-330`): *"THE VISUAL CHROME IS FRESHCARDS' CARD, NOT THIS ELEMENT. The section is the layout box and the gesture surface; the face inside it is the FreshCards `Card` primitive, which carries the radius, the border, the shadow and the surface colour."* ⇒⇒□ **⇒⇒□ ⇒⇒□ THE DESK PANEL KEEPS THAT SEPARATION** — the Desk Panel owns the box, the placement, the flip and the gesture; the FCr `Card` owns the chrome. ⇒⇒□ **⇒⇒□ ⇒⇒□ A DESK PANEL THAT STYLES ITS OWN BORDER, SHADOW, OR RADIUS IS DOUBLING THE FRESHCARDS `Card` — AND THE FCr PRIMITIVES ARE WHAT THE OPERATOR HAS ALREADY CHOSEN THE LOOK OF.** **THIS PART SUPERSEDES PART 24's GRID ARITHMETIC, AND THE SUPERSESSION IS EXPLICIT.** MEASURED: Part 24 §24.1 describes `src/host/dashboard/dashboard-layout.ts` as owning *"the grid arithmetic: 12 columns … plus explicit `order` and `width` on each card"*, and names `src/host/dashboard/DashboardCanvas.tsx` and `src/host/dashboard/DashboardGrid.tsx`. ⇒⇒□ **⇒⇒□ ⇒⇒□ AND THE PATHS IN PART 24 NO LONGER EXIST.** MEASURED: `src/host/dashboard/` is ABSENT — the dashboard now lives under `src/modules/dashboard/src/dashboard/`, with the same file names. ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ PART 24 IS NOT DELETED AND ITS SCOPE LAW IS NOT TOUCHED** — Parts 24.2, 24.3 and 24.4 govern WHICH DATA the Dashboard shows, and none of that is affected by how the panels are arranged. ⇒⇒□ **⇒⇒□ ⇒⇒□ WHAT IS SUPERSEDED IS PART 24 §24.1's GRID ARITHMETIC ONLY**, because the Desk is not a grid. **AND THE EXISTING TEST IS STILL A GUARD, NOT A MASK.** MEASURED: Part 24 §24.3 names `fvc1065-project-boundary.test.ts` (11 tests) as the guard for `filterCardsByProject`; it now lives at `src/modules/dashboard/src/dashboard/__tests__/fvc1065-project-boundary.test.ts` and it KEEPS its meaning: **the Desk arranges panels; it does not change which data a panel may see.** ⇒⇒□ **⇒⇒□ ⇒⇒□ A DESK THAT SHOWS ANOTHER PROJECT'S CARDS IS WRONG NO MATTER HOW BEAUTIFULLY IT IS ARRANGED.** **AND PART 23's SCOPES SURVIVE.** MEASURED: Part 23 requires three scopes with a scope toggle and Part 27 adds a fourth (`Roadmap`). ⇒⇒□ **⇒⇒□ ⇒⇒□ THE SCOPE TOGGLE IS NOT THE DESK, AND THE DESK IS NOT THE SCOPE.** ⇒⇒□ **⇒⇒□ ⇒⇒□ PART 23.3's "Switching the scope changes the widgets rendered on the grid" IS WRITTEN IN THE GRID'S LANGUAGE, AND THE DESK REPLACES THE WORD "grid" — the widgets change, and the arrangement rule of THIS Part applies to them.** ⇒⇒□ **⇒⇒□ ⇒⇒□ PART 23's THREE SCOPES AND PART 24.4's SCOPE VOCABULARY ARE CARRIED FORWARD UNCHANGED**, and the new Desk Panel vocabulary is ADDITIVE. **AND THE DASHBOARD IS NOT THE SHOWCASE, AND THE SHOWCASE IS NOT THE DESK.** MEASURED: Part 89 overrode Part 85 §85.1 — the root route is the permanent VC Shell and the Showcase lives at `/showcase`; and Part 90 moved the sub-project list out of the canvas grid into the Project Picker dropdown, because *"the grid is `repeat(auto-fill, minmax(220px, 1fr))`, so a project with four children takes a cell FOUR TIMES THE HEIGHT of its neighbours."* ⇒⇒□ **⇒⇒□ ⇒⇒□ THE GRID HAS ALREADY COST THIS PRODUCT ONE LAW, AND THIS PART IS THE SECOND TIME THE GRID'S GEOMETRY IS THE PROBLEM.** ⇒⇒□ **⇒⇒□ ⇒⇒□ A CUSTOMER FACING SHOWCASE IS NOT A DESK** — the Desk is the operator's working surface. **AND THE DASHBOARD IS NOT THE ROOT ROUTE.** MEASURED: Part 91's law is that the bare `/` is the Shell with NO PROJECT LOADED, and `isMasterDashboardPath()` decides between the master dashboard and the Shell. **⇒⇒□ ⇒⇒□ THE DESK LIVES ON THE DASHBOARD ROUTE** — wherever the Dashboard renders today — and it does not change which route is the Shell's. **WHAT IS MEASURED, NOT LAW.** MEASURED: no branch on `origin` carries FVC 1385 or the Desk — `git ls-remote --heads origin` returns no `1385`/`desk` branch, and a sweep of `src/`, `tools/`, `scripts/`, `config/` for `\bdesk\b` returns ZERO hits. ⇒⇒□ **⇒⇒□ SO THIS PART SPECIFIES THE TARGET, NOT A MEASURED SURFACE**, and every rule above that quotes current behaviour is quoting the code the Desk REPLACES. MEASURED: the FreshCards package ships no flip component, and no dashboard source declares a `perspective`, `preserve-3d` or `rotateY` — the FLIP MECHANIC IS NOT YET MEASURED, and this Part specifies its CONTRACT, not its implementation. MEASURED: `dashboard-layout.ts` provides `reorderCards`, `dropIndexFor`, `withWidth`, `withOrder`, `sortByOrder` — reorder, width, height and order ONLY. There is NO pin field, NO library, and NO add/remove path in the module. **THE ENFORCEMENT MECHANISM IS NOT YET BUILT, AND IS DECLARED OPEN.** MEASURED: this Part adds NO gate. There is no masonry assertion, no pin assertion, and no flip assertion in `scripts/`, `src/` or `tools/`. ⇒⇒□ **⇒⇒□ ⇒⇒□ A SPEC THAT PROMISES AN UNBUILT GATE IS WORSE THAN A SPEC THAT DECLARES THE GAP** (Part 86 §86.1's own law) — because the first is believed and the second is not. ⇒⇒□ **⇒⇒□ ⇒⇒□ THE STOP CONDITIONS IN §92.2, §92.3 AND §92.4 ARE WRITTEN AS LAW WITH THEIR ENFORCEMENT DECLARED OPEN**, and a later Part MUST close them with a gate that has been seen to go RED.


v3.40.0 — Added Part 91: The Tree Is Three Deep, and the Depth Is a Contract — the law that the operator's hierarchy is THREE DEEP (`VibeCoder Internals` → `Home Page` → `Train Page`), that a PROJECT'S CHILDREN LIVE IN `project.subProjects` and NOT IN A `parentId` COLUMN, that the READER MUST DESCEND, that a GRANDCHILD NEEDS ITS OWN ROUTE ROW, and that a FLOAT IN A COLUMN FLEX BOX IS A FLEX ITEM. **PART NUMBERING.** MEASURED: the highest `## Part N` heading was **90** (`## Part 90 — The Picker Is a Tree, and the Canvas Is a Poster Wall`, landed by FVC 1364), so the next free number is **91**; and the highest `v3.N.0` marker was **39**, so the next free version is **v3.40** — the version and the Part are INDEPENDENT counters. **THE DISPATCH'S PREMISE ABOUT THE RECORDS WAS WRONG, AND THE CORRECTION IS STRONGER.** MEASURED: a sweep of EVERY key in the FC Brain — `project:` (42), `artifact:` (104), `conversation:` (59), `turn:` (121), `decision:` (1), `agent:` (1), `tree:` (500) — **828 keys**, each fetched and searched for "train", "home page" and "homepage" — found **ZERO** matches; and `git log --all -S "Train Page"` and `-S "Home Page Project"` both return **empty**. ⇒⇒□ **⇒⇒□ AND THE OPERATOR'S TWO PAGES WERE ALREADY REAL — UNDER DIFFERENT NAMES:** the two routes that render them are `/project/vibecoder-internals/home` and `/project/vibecoder-internals/train**, so the hierarchy was written to the records that CARRY the operator's pages and NOT to invented records. **THE NESTING CONTRACT IS `project.subProjects`, AND `parentId` IS A TREE COLUMN.** MEASURED, in the bridge's own words (`bridge/routes/brain-graph.cjs:117-120`): *"There is deliberately no column-lifting here the way tree-write.cjs lifts parentId/order: **a project has no tree containment**"* — and `parentId` IS a tree-node column, provisioned by the adapter and lifted ONLY by the tree write route. **THE WRITE PATH WAS MEASURED, NOT ASSUMED.** MEASURED: the bridge runs with `FVC_AUTH_MODE=dev`, so `checkAuth` is a no-op; `POST /api/agent/fc-in-vc/project/:id` returns `{"ok":true,…}`; the record round-trips VERBATIM; and the tombstone guard is REAL — writing over a retired record returns **409 `project_retired`** without `{"deleted":true}` or `{"undelete":true}`. **THE READER COULD NOT DESCEND, AND A VALIDATOR THAT REBUILDS THE RECORD HID IT.** MEASURED: `SubProject` had no children field and `readSubProjects()` did not recurse; and the first fix read the children off the VALIDATED value — but `validate()` returns a NEW OBJECT carrying only `id`, `title`, `description` and `route`, so the children were DROPPED BEFORE THE RECURSION EVER SAW THEM, and the symptom was DECEPTIVE: the badge counted the RIGHT number, the DOM was healthy, and the twisty was ABSENT. ⇒⇒□ **⇒⇒□ A VALIDATOR THAT REBUILDS THE RECORD MUST NOT BE THE PLACE THE EXTRA FIELDS ARE READ FROM.** **THE GRANDCHILD'S HREF WAS WRONG IN A SECOND, SUBTLER WAY.** MEASURED: the first version passed the CHILD's route down as the next `projectId`, so the href came out `/project/home/home/train` — the child's own segment sitting in the PROJECT slot. ⇒⇒□ **⇒⇒□ A ROUTE IS NOT A PROJECT.** **A GRANDCHILD WITH NO ROUTE ROW IS A NODE THE OPERATOR CANNOT OPEN.** MEASURED: the route table's deepest row was TWO segments, so a grandchild had NO URL; and the four-segment row cannot be shadowed, because *"a segment count mismatch is not a match"*. **A FLOAT IN A COLUMN FLEX BOX IS A FLEX ITEM, AND IT LANDS ON THE TEXT.** MEASURED: the badge is `float: right` and the sub-project row is `display: flex; flex-direction: column`, so the badge dropped BELOW the description and the pill sat ON the text — before: badge `[80,371,368,15]` against description `[70,358,378,12]`; after: the title and the badge share ONE row and the badge is `[430,343,18,15]`, **overlap 0**. **THE GATE IS 26 ASSERTIONS AND IT MEASURES GEOMETRY.** ⇒⇒□ It asserts the dispatch's three, and that the grandchild is INDENTED past, BELOW, and NARROWER than its parent, and that the badge overlaps neither the title nor the description, and that the grandchild navigates to `/project/vibecoder-internals/home/train` with the picker CLOSED. **THE NEGATIVE CONTROL FIRES — 9/9.** ⇒⇒□ MEASURED: it writes THE SAME project twice, once with `subProjects` and once without, and asserts that the first has a twisty and a badge and the second has NEITHER. **THE GATE HAD A BUG OF ITS OWN, AND THE BUG WAS WORTH NAMING.** ⇒⇒□ MEASURED: the gate asserted the twisty's visibility on `tr.width`/`tr.height` while the rect helper returns `w`/`h`, so the assertion read `undefined` and FAILED on a product that was perfectly visible; and the first version crashed with `R is not defined`, because `R` lives in Node and `page.evaluate` runs in the BROWSER. ⇒⇒□ **⇒⇒□ A GATE THAT ASSERTS ON A FIELD NAME THAT DOES NOT EXIST FAILS SILENTLY ON A REAL PRODUCT.** **AND THREE OLDER GATES ARE STALE, AND THE STALENESS IS MEASURED, NOT ASSUMED.** MEASURED on `origin/main` (build `ad73cf8a`): `fvc1337-verify-root` **6/11**; `fvc1341-verify-stencil` **FAILED 5**; `fvc1342-verify-hero` **FAILED 1** — and THE SAME FAILURES, BY NAME, on FVC 1367's tree, so FVC 1367 REGRESSED NOTHING. ⇒⇒□ **⇒⇒□ AND THE REASON IS NAMED:** all three assert that `/` IS THE SHOWCASE, and FVC 1363 OVERRODE PART 85 §85.1 (Part 89). ⇒⇒□ **⇒⇒□ AND THE THREE GATES ARE MARKED, NOT DELETED AND NOT "FIXED" — DO NOT "FIX" THEM BY REVERTING PART 89.** **AND THE SCOPE IS HELD.** MEASURED: `tsc --noEmit` reports **309** errors on the baseline and **309** on FVC 1367's tree — the change adds ZERO type errors. **AND BACKTICKS INSIDE A CSS TEMPLATE LITERAL TERMINATE IT** — MEASURED: the first fix broke the build with `Expected ";" but found "float"`.

v3.39.0 — Added Part 90: The Picker Is a Tree, and the Canvas Is a Poster Wall — the law that the Project Picker DROPDOWN renders the project hierarchy, that a parent is SELECTABLE **and** EXPANDABLE through two separate controls, that the canvas grid carries a BADGE instead of the children, and that ONE canonical reader owns the sub-project list. **PART NUMBERING.** MEASURED: the highest `## Part N` heading was **89** (`## Part 89 — The Root Route Is the Shell`), so the next free number is **90**; and the highest `v3.N.0` marker was **38**, so the next free version is **v3.39** — the version and the Part are INDEPENDENT counters. **THIS PART AMENDS PART 89 §89.4, AND THE AMENDMENT IS THE OPERATOR'S.** MEASURED: the operator's words — "Do not just dump the sub-projects onto the main canvas grid. They must be in the dropdown menu." ⇒⇒□ **⇒⇒□ AND THE REASON IS MEASURABLE, NOT A MATTER OF TASTE:** the grid is `repeat(auto-fill, minmax(220px, 1fr))`, so a project with four children takes a cell FOUR TIMES THE HEIGHT of its neighbours. **THE DROPDOWN WAS THE FLAT LIST, AND FVC 1363 FIXED THE WRONG SURFACE.** MEASURED: the Project Picker dropdown is `src/shell/HeaderMenus.tsx` — the Shell's OWN surface, a sibling of the generated Header — and its project panel was `projects.map((project) => <button …>)`, A FLAT LIST OF TEXT. ⇒⇒□ **⇒⇒□ AND FVC 1363'S GATE ASSERTED THE SUB-PROJECTS WERE RENDERED BY `[data-fv-project-grid="subproject"]` — THE CANVAS GRID'S ATTRIBUTE, NOT THE DROPDOWN'S.** ⇒⇒□ ⇒⇒□ **⇒⇒□ THE GATE MEASURED THE WRONG SURFACE, AND A GATE THAT MEASURES THE WRONG SURFACE PASSES WHILE THE COMPLAINT STAYS OPEN.** **TWO READERS OF THE SAME LIST ARE TWO TRUTHS ABOUT THE SAME LIST.** MEASURED: FVC 1362 introduced `src/shell/project-subprojects.ts`, a WEAKER COPY of the Test Playground's own `readSubProjects()` (FVC 1288) — which validates the entries, DE-DUPES them by id, falls back to the id when a sub-project declares no route, and builds each href with the ROUTING ENGINE's own `buildPath`. ⇒⇒□ **⇒⇒□ THE CANONICAL READER WINS AND THE COPY IS DELETED.** **A PARENT MUST BE SELECTABLE *AND* EXPANDABLE, AND ONE ROW CANNOT BE BOTH.** MEASURED: the operator asked for a visible way to expand AND for the ability to select the parent OR a child. ⇒⇒□ ⇒⇒□ **⇒⇒□ SO THE PARENT IS A ROW WITH A TWISTY AND A SEPARATE SELECT TARGET** — a control that does two things is a control whose meaning depends on where you click it. **THE EXPANDED SET IS THE MENU'S OWN STATE, NOT A PROPERTY OF THE PROJECTS.** ⇒⇒□ A parent's children are a fact about the BRAIN; whether they are open is a fact about the OPERATOR. **A Set IS READ WITH `.has()`, NOT WITH `[id]` — AND `tsc` DID NOT CATCH IT.** MEASURED: the first version declared `ReadonlySet<string>` and read `expandedGroups[id] === true`; a Set HAS NO INDEX SIGNATURE, so every lookup returned `undefined` and every group was permanently collapsed. ⇒⇒□ **⇒⇒□ THE CLICK WORKED, THE STATE UPDATED, AND THE READ WAS WRONG** — and `ReadonlySet<string>` carries an index signature that silently yields `undefined`. ⇒⇒□ **⇒⇒□ A TYPE THAT PERMITS A SILENT `undefined` IS NOT A GUARD — IT IS A HOLE WITH A TYPE ON IT.** ⇒⇒□ ⇒⇒□ AND THE SYMPTOM WAS WORTH MEASURING: the button was present, hit-testable, `elementFromPoint` returned its own glyph, a JS `.click()` changed nothing, and the panel SURVIVED the click — so the component was not remounting, and the bundle made it obvious (`const k=p[g]===!0`). **THE MENU MUST FIT ITS CONTENT, AND NEVER RUN OFF THE SCREEN.** MEASURED: the cap was `min(60vh, 420px)` and the EXPANDED menu's content is 450px — so the panel clipped the last project by 30px and the operator had to SCROLL to reach "VibeCoder Internals". ⇒⇒□ **⇒⇒□ A DROPDOWN THAT CLIPS ITS OWN LAST ITEM IS A DROPDOWN THAT HIDES A PROJECT.** ⇒⇒□ ⇒⇒□ AND THE NEW CAP IS THE VIEWPORT, NOT A MAGIC NUMBER: `calc(100vh - 72px)`, because the menu is `top: 52px` — 928px on a 1000px desktop (fits the 450px content) and 528px on a 600px phone. **THE GATE IS 13 ASSERTIONS AND IT MEASURES GEOMETRY, NOT CLASS NAMES.** ⇒⇒□ It asserts the dropdown is open; a parent has a VISIBLE twisty with `aria-expanded` and a child-count badge; and the children are INDENTED PAST and BELOW their parent — **a child that is in the DOM but not nested is not nested.** ⇒⇒□ ⇒⇒□ AND IT PROVES THE CLICK PATH: clicking a child navigates to `/project/test-playground/html-extraction` and the menu CLOSES. **THE NEGATIVE CONTROL FIRED: 2/11 against the pre-FVC-1364 build, 13/13 against the new one.** MEASURED on the old build: zero groups, zero twisties, zero children — the flat list the operator described. **AND FVC 1363'S OWN GATE WAS CORRECTED, NOT DELETED** — it now asserts the grid does NOT dump the sub-projects and carries a child-count badge instead. **AND ONE PRE-EXISTING FAILURE WAS FIXED ON THE WAY.** MEASURED: `fvc1256-home-stable.spec.tsx` failed 3 tests on `origin/main` as well as on the FVC 1363 tree, because FVC 1363 changed `DEFAULT_PROJECT_VISIBILITY` from `customer` to `operator` and the tests rendered `<ProjectGrid />` with NO prop and expected the customer view. ⇒⇒□ ⇒⇒□ **⇒⇒□ THE TESTS NOW ASK FOR THE VIEW THEY MEAN** — the customer view still exists; it is one prop away.

v3.38.0 — Added Part 89: The Root Route Is the Shell, and the Shell and the Canvas Are Two Things — the law that the bare `/` is the Shell with NO PROJECT LOADED, that a route naming no project reads NO TREE, that the Mountain Rail page belongs to `vibecoder-home` and to nothing else, that a sub-project is a CHILD of a project record and not a sibling of it, and that the customer visibility view is a production concern for a production that does not exist yet. **PART NUMBERING.** MEASURED: the highest `## Part N` heading was **88** (`## Part 88 — The Visual Feedback Loop and the Hero`), so the next free number is **89**; and the highest `v3.N.0` marker was **37**, so the next free version is **v3.38** — the version and the Part are INDEPENDENT counters. **THIS PART OVERRIDES PART 85 §85.1, AND THE OVERRIDE IS THE OPERATOR'S.** MEASURED: Part 85 §85.1 says "THE CUSTOMER'S LANDING PAGE IS A NEW PAGE, NOT A RE-SKIN OF THE EDITOR" and "a customer should see none of them"; the operator said the opposite and said why — "This is a development environment. The operator needs quick links." ⇒⇒□ **⇒⇒□ AND PART 85 IS NOT DELETED — THE SHOWCASE IS MOVED TO `/showcase`.** ⇒⇒□ **⇒⇒□ A ROUTE IS A PLACE; THE PAGE WAS NEVER SUPPOSED TO BE WELDED TO `/`.** **THE ROOT RENDERED NO SHELL AT ALL.** MEASURED on live production at `103487dd`, 1600×1000: the bare `/` was `div.fv-showcase-root` — the Showcase's OWN top bar, its OWN intro (`.fv-showcase-headline` "Welcome to VibeCoder" at `[0,84,1600,45]`) and its own hero card. ⇒⇒□ **⇒⇒□ THE EDITOR HEADER, THE HANDLES AND THE RAILS WERE ABSENT.** **THE MOUNTAIN RAIL PAGE WAS ON THE ROOT TWICE.** MEASURED: `treeIdForRoute(undefined, 'home')` resolved to `vibecoder-internals/home`, whose recipe node is named "Recipe: VibeCoder Home (Mountain Rail Tours)" — and the Showcase's hero card painted the SAME copy over the SAME artwork (`.fv-showcase-hero__title` "Empower Your Journey" at `[401,464,798,37]`). ⇒⇒□ **⇒⇒□ AND THE SAME RECIPE IS ALSO IN `vibecoder-home`** — so the Mountain Rail page was already in its own project. **THE WELD WAS ONE RESOLVER, AND TWO RESOLVERS DISAGREED.** MEASURED: `projectIdForRoute('')` returned `vibecoder-home` and `internalsProjectIdForRoute('')` returned `vibecoder-internals` — two answers for a route that named no project. ⇒⇒□ **⇒⇒□ A RESOLVER THAT RETURNS A PROJECT FOR A ROUTE THAT NAMED NONE IS THE WELD ITSELF.** **THERE IS NO "BLANK" TREE IN THE BRAIN.** MEASURED: `/api/agent/tree/vibecoder-internals` returns `{"ok":true,"nodes":[],"count":0}` and `/api/agent/tree/home` returns the same. ⇒⇒□ **⇒⇒□ SO THE BLANK PAGE IS A SHELL SURFACE THAT READS NOTHING** — and the EMPTY STRING is already the "read nothing" answer, because the tree store's loader refuses an empty key (`tree-store.ts:238`). **THE OLD PLACEHOLDER'S WORDS ARE KEPT, AND ITS FIVE MOUNTAIN RAIL CARDS ARE NOT.** MEASURED at `503fc415^`: the old home recipe's Hero carried `title: "Welcome to VibeCoder"` and `subtitle: "Build a whole new class of web apps — describe it, and watch it become real."` — beside a ProjectGrid carrying five cards that DESCRIBE THE MOUNTAIN RAIL DESIGN, which FVC 1289's own commit message called "five text cards that DESCRIBED the design, twice over". **"NO PROJECT" AND "THE ROOT" ARE TWO DIFFERENT FACTS.** MEASURED: a predicate asking only "does this route name a project?" is ALSO TRUE on `/operator`, which carries no `:projectId` — and `/operator` rendered the operator's own project grid (10 cards) and read `vibecoder-internals%2Fhome`. ⇒⇒□ **⇒⇒□ A PREDICATE THAT CANNOT TELL THEM APART BREAKS A ROUTE THAT WAS WORKING.** ⇒⇒□ **⇒⇒□ SO THE PREDICATE ASKS THE ROUTE'S OWN VIEW, AND THE RESOLVER NAMES EVERY NAMED VIEW EXPLICITLY.** **THE HEADER'S LINK TARGET IS A SEPARATE FACT FROM THE CANVAS'S CONTENT.** MEASURED: FVC 1269 requires the workspace tabs on `/` to be LIVE LINKS — on live production every one of them rendered as a `<button>` with `href=null` — and `buildPath` returns `null` for an empty param. ⇒⇒□ **⇒⇒□ SO THE HEADER POINTS AT `vibecoder-home` (WHICH EXISTS) AND THE CANVAS READS NO TREE. THAT IS THE SEPARATION.** **A SUB-PROJECT IS A CHILD OF A PROJECT RECORD, NOT A SIBLING OF IT.** MEASURED: the brain's list carries 41 keys and 31 of the records are tombstoned (`deleted: true`), so the live list is 10; and `project:html-extraction` is NOT among them — `test-playground`'s OWN record carries four `subProjects`. ⇒⇒□ **⇒⇒□ A PICKER THAT LISTS ONLY THE 41 KEYS CAN NEVER SHOW A SUB-PROJECT.** ⇒⇒□ **⇒⇒□ AND A SUB-PROJECT IS A ROW UNDER ITS PARENT** — the grid is `repeat(auto-fill, minmax(220px, 1fr))`, so every direct child is a cell. **THE DEFAULT VISIBILITY IS NOW `operator`, AND THE PREFIX RULE STAYS.** MEASURED: the `vibecoder-` prefix hid `vibecoder-home`, `vibecoder-internals` and `vibecoder-self` — the product's OWN scaffolding — from a picker whose only consumers are the operator. ⇒⇒□ **⇒⇒□ A RULE THAT IS CORRECT BUT NOT THE DEFAULT IS NOT DELETED; IT IS DEMOTED.** **THE GATE IS 28 ASSERTIONS AND IT READS THE SCREEN.** ⇒⇒□ It asserts the dispatch's five, PLUS the absence of the Showcase at `/`, PLUS **that the root fetched NO TREE AT ALL** — because "no Mountain Rail copy" and "no Mountain Rail fetch" are two different assertions and only the second proves the weld is gone. ⇒⇒□ **⇒⇒□ THE NEGATIVE CONTROL FIRED HARD: 4/22 against the pre-FVC-1362 build, 28/28 against the new one.** **TWO OF THE GATE'S OWN ASSERTIONS WERE WRONG AT FIRST, AND BOTH WERE FIXED IN THE GATE, NOT IN THE PRODUCT.** MEASURED: `body.innerText.slice(0, 400)` cut the subject off — "VibeCoder Internals" sits BELOW the first 400 characters, so the gate said it was missing **while the screenshot showed it**; and a fixed 2.5 s wait read the body **before the brain answered**. ⇒⇒□ **⇒⇒□ THE FIX WAS TO WAIT FOR THE GRID'S OWN STATE ATTRIBUTE AND TO READ THE WHOLE BODY.** ⇒⇒□ **⇒⇒□ A GATE THAT FAILS BECAUSE OF ITS OWN TIMING IS A GATE THAT TEACHES THE READER NOTHING.** **A CSS CUSTOM PROPERTY WITH NO DEFINITION IS NOT A THEME.** MEASURED: the placeholder's title rendered `rgb(31, 41, 55)` on a `rgb(14, 14, 22)` background, because the CSS used `var(--fv-text, #1f2937)` and **`--fv-text` IS UNSET**; the tokens the app actually sets are `--fv-text-primary: #e8e8e8` and `--fv-text-muted: #7a7a7a`.

v3.37.0 — Added Part 88: The Visual Feedback Loop and the Hero — the law that the copy belongs to the DOM and the picture belongs to the artwork, NEVER BOTH. **PART NUMBERING.** MEASURED: the highest `## Part N` heading was **87** (`## Part 87 — The True Vision Pipeline`, landed by FVC 1341), so the next free number is **88**. **THE VERSION AND THE PART NUMBER ARE INDEPENDENT COUNTERS** (Part 85 §85.7): the version is derived from the highest `v3.N.0` marker (**36** → **v3.37**) and the Part from the highest heading (**87** → **88**). **THE DUPLICATION WAS MEASURED, NOT ASSUMED.** MEASURED ON LIVE `/project/vibecoder-home/stencil`: the Hero image was 510×238 and its PIXELS carried "Empower Your Journey", "Scenic rail adventures since 1987" and "Book Now" — and the SAME words appeared as DOM `<p>` elements **BELOW** the picture. ⇒⇒□ **⇒⇒□ AND `[data-fv-widget="Hero"]` COUNTED 0** — the recipe used raw primitives, so the copy had NO HERO to draw it over the artwork. ⇒⇒□ **⇒⇒□ THE ROOT CAUSE WAS THE ABSENCE OF A `Hero` WIDGET, NOT A FAULT INSIDE ONE.** **THE MASK IS MEASURED FROM THE COPY'S OWN BOXES.** MEASURED: title `x=548 y=371 w=340 h=40`, subtitle `x=597 y=409 w=240 h=24`, CTA `x=658 y=443 w=100 h=43` — 23,180 pixels masked, **97.86%** of the artwork kept. ⇒⇒□ **⇒⇒□ A GLOBAL DARK THRESHOLD IS NOT A MASK** — the artwork carries dark mountain and train silhouettes. **THE FILL'S THREE FAILURES WERE THREE DIFFERENT BUGS.** ⇒⇒□ (a) the first diffusion averaged the MASKED neighbours, and the masked pixels STARTED at the text's own colour — MEASURED, the delta at source `y=395` was **604**; ⇒⇒□ (b) the second refused to read a masked neighbour, so a pixel with no unmasked 8-neighbour was **never written** and KEPT the text's colour; ⇒⇒□ (c) the third never pre-seeded the interior. ⇒⇒□ **⇒⇒□ THE FIX IS ALL THREE AT ONCE: PRE-SEED, THEN DIFFUSE, THEN FEATHER.** **THE HERO'S SHAPE IS THE PICTURE'S SHAPE.** MEASURED: FVC 1332 set `aspect-ratio` on the `<img>`, and FVC 1342 pinned BOTH axes — so the ratio had NO effect; and `min-height: 240px` plus `padding: 35px 21px` OVERRODE it, rendering the hero **593×349** (ratio 1.699) and letterboxing the slice. ⇒⇒□ **⇒⇒□ THE HERO CARRIES THE MEASURED RATIO AND `min-height` IS REMOVED** — now **593×277** (ratio **2.141** vs the mockup's **2.143**). **THE IMAGE AND THE OVERLAY SHARE ONE BOX.** MEASURED: in the flow they differed by the Hero's own **21px** of padding. ⇒⇒□ **⇒⇒□ THE OVERLAY IS A SIBLING OF THE IMAGE**, both `position: absolute; inset: 0`. **A CSS CUSTOM PROPERTY ON A CHILD DOES NOT AFFECT THAT CHILD.** MEASURED: the emitter put `--fv-widget-hero-color` on the title and NO RULE CONSUMED IT, so the title rendered **white**. ⇒⇒□ **⇒⇒□ THE COLOURS ARE DIRECT INLINE COLOURS.** **A PRODUCT WIDGET'S SECTION ID CANNOT RIDE ON THE NODE'S `attrs`.** MEASURED: a product widget is emitted as `<HeroWidget state={state} />` and the COMPONENT renders the section, so the hero section read as **GONE**. ⇒⇒□ **⇒⇒□ THE SECTION ID RIDES IN `props.attrs`** — the box primitive's own channel. ⇒⇒□ **⇒⇒□ ONE VOCABULARY.** **A GATE THAT CANNOT FAIL PROVES NOTHING.** THREE negative controls, ALL FIRED. ⇒⇒□ **⇒⇒□ AND CONTROL B ANSWERED A QUESTION THE DISPATCH DID NOT ASK**: with the overlay static, "the title is inside the image bounds" STILL PASSED — the box GREW to contain the copy — so the gate gained "the overlay is ABSOLUTELY positioned". **THE GOLDEN GATE COMPARES THE GENERATOR'S OUTPUT, NOT THE TRACKED FILE.** MEASURED: at `origin/main`, **118 OF THE 121** generated files were NOT TRACKED and the **THREE** that were were ALL STALE — and regenerating the Header exposed **12 PRE-EXISTING FAILURES**, because the BASELINE emitter also emits a Header with NO "Preview" TAB. ⇒⇒□ **⇒⇒□ A STALE GENERATED FILE IS A MASK, AND THE MASK HID A REAL BUG.** ⇒⇒□ **⇒⇒□ THE SCOPE IS HELD AND WHAT IS FOUND IS NAMED** — the Header's missing workspace tabs want their own dispatch.

v3.36.0 — Added Part 87: The True Vision Pipeline (Stencil Scene Recreation) — the law that a scene is not a widget tree: the extractor must separate the ASSETS, the STRUCTURE, the TEXT and the FLOATS, and the mockup's own chrome is not part of the scene. **PART NUMBERING.** MEASURED: the highest `## Part N` heading was **86** (`## Part 86 — The Chrome Inviolability Rule`, landed by FVC 1338), so the next free number is **87**. **THE VERSION AND THE PART NUMBER ARE INDEPENDENT COUNTERS** (Part 85 §85.7): the version is derived from the highest `v3.N.0` marker (**35** → **v3.36**) and the Part from the highest heading (**86** → **87**). **THE TEXT PRIMITIVE IS A BARE REACT CHILD.** MEASURED (`src/modules/generator/src/emitters/react-emitter.cjs:1887-1899`): the primitive emits `{${jsString(props.value)}}` with NO wrapper — so two text nodes in the same parent CONCATENATE, and a generated file rendered `{"Empower Your Journey"}{"Scenic rail adventures since 1987"}` as one run-on string. ⇒⇒⇒ **⇒⇒□ A RECIPE THAT WANTS SEPARATE COPY MUST WRAP EACH TEXT IN ITS OWN ELEMENT.** **THE SLOT'S DIRECTION IS DEFAULTED, NOT DERIVED.** MEASURED (`react-emitter.cjs:345`): `flex-direction: ${definition.direction || 'row'}` — so a slot with no `direction` lays its sections SIDE BY SIDE. **THE CHROME RULE IS ENFORCED ON `node.widget`, NOT ON TEXT CONTENT.** MEASURED (`tools/fvc1341-extract-core.cjs:491`): the check is on `node.widget` against `CHROME_WORDS` (`:59-76`) — a page whose copy says "Layers" is not building the Layers panel; a page whose WIDGET is `MenuIcon` is. **THE BOUNDARY IS THE ROUTE, NOT THE IMPORT GRAPH.** MEASURED: the Shell imports `GeneratedStencilView` at the top of the file and the Shell is imported by `ApplicationRoot`, so the import graph ALWAYS contains the generated component. ⇒⇒⇒ **⇒⇒□ A GATE THAT FORBIDS THE IMPORT GRAPH WOULD FORBID THE STENCIL ITSELF.** ⇒⇒□ **BOTH GATES ARE REQUIRED — "THE STENCIL RENDERS" IS NOT "THE APP IS CORRECT".** **AN UNPLACED GRID ITEM GETS AN IMPLICIT COLUMN.** MEASURED (`src/shell/Shell.tsx:1028-1032`, `:1112`): the grid has three columns and the canvas is `grid-column: 2`; the Stencil had NO placement, so it was auto-placed into an implicit fourth column — and when every descendant was also zero-wide, that column was zero-wide too. MEASURED ON THE LIVE ROUTE AT 1600×1000: `.fv-stencil` width 0, `.fv-stencil-generated` width 0. ⇒⇒□ **⇒⇒□ AND EVERY SECTION INSIDE IT STILL MEASURED AS "VISIBLE" TO A GEOMETRY PROBE**, because visibility was measured on the DESCENDANTS. ⇒⇒□ **⇒⇒□ THE FIX IS THE SAME RULE AS THE CANVAS'S — `grid-column: 2` AND `min-width: 0`.** **A HIT TEST CANNOT FIND AN OVERLAPPING FIXED-POSITION HANDLE.** MEASURED (`src/shell/Handle.tsx:18`, `:64`): the handle is `position: fixed; left: 0`, and with the grid's left column at 0px it lands on the Stencil's content. MEASURED: `document.elementFromPoint(30, 470)` returned the Stencil's own `<section>` — the handle's BOX is there but its PAINTED TEXT is a child span. ⇒⇒□ **⇒⇒□ THE ELEMENT UNDER THE POINTER IS NOT ALWAYS THE ELEMENT THAT PAINTS THERE.** **THE PROMPT'S FIRST WORD SELECTS THE TIER.** MEASURED (`bridge/lib/chat-handler.cjs:352`): the question-intent word list contains BOTH `please` AND `describe`; MEASURED (`:361`, `:370`, `:391`) the mode chain; MEASURED (`config/provider-registry.cjs:46-47`) the ONLY two vision-capable models carry `modes: ['build']` ONLY; MEASURED (`:107-112`) `getTiersForMode` FILTERS by mode. ⇒⇒□ **⇒⇒□ ⇒⇒□ CONSEQUENTLY A PROMPT BEGANNING "Please describe…" ROUTES TO `chat`, THE VISION TIERS ARE FILTERED OUT, AND A TEXT-ONLY MODEL WINS THE RACE** — MEASURED ON THE LIVE SERVER, "[v-agent] mode = chat | reply chars = 359", and the resulting recipe carried ZERO assets. ⇒⇒□ **⇒⇒□ ⇒⇒□ THE FIX IS THE FIRST WORD: `generate` IS IN `_startsWithBuildCmd`. ⇒⇒□ THE QUESTION FRAME MOVES TO THE SECOND LINE, NOT AWAY — THE MODE SELECTS THE TIER AND THE RULE TELLS THE MODEL WHAT TO DO, AND THOSE ARE TWO DIFFERENT THINGS.** **THE VISION-SPECIFIC CASCADE IS COMPUTED AND NEVER READ.** MEASURED (`bridge/lib/chat-handler.cjs:936`): `const cascade = … _visionRequired ? [gemini…]` — the ONLY occurrence of that variable between `:936` and the end of the function. MEASURED (`:1293`): the cascade that RUNS comes from `getTiersForMode(systemPromptMode)`. ⇒⇒□ **DECLARED OPEN — THE BRIDGE IS OUTSIDE THE EXTRACTOR'S SCOPE.** **THE GENERATOR ALWAYS NAMES THE COMPONENT `Header`.** MEASURED (`react-emitter.cjs:4336`) and across three books — so the import is `import { Header as VibeCoderUI }`. **AND A GENERATED FILE MUST BE FORCE-ADDED.** MEASURED (`.gitignore:19`) and MEASURED (`scripts/check-generator-golden.cjs`): the gate DELETES the untracked produced files when it restores the tree — so an untracked generated component DISAPPEARS after a golden run. **THE EXTRACTOR'S EXIT CODE IS NOT A GATE.** MEASURED: before the prompt fix the extractor exited **0** with **FOUR** violations and ZERO assets. ⇒⇒□ **⇒⇒□ A SEPARATE GATE EXITS 1 WHEN THE RECIPE IS NOT A SCENE, AND PROVES IT REJECTS THE FOUR KNOWN-BAD SHAPES** — a gate that has never been seen to go RED is not proven. ⇒⇒□ **⇒⇒□ AND A GATE THAT READS ITS OWN VALIDATOR MUST NORMALISE THE VALIDATOR'S RETURN SHAPE EXPLICITLY** — MEASURED: `validateExtractedRecipe` RETURNS AN ARRAY, and reading `.violations` off that array (then falling back to `|| []`) made **EVERY KNOWN-BREAK CASE REPORT ZERO VIOLATIONS AND THE GATE PASS ALL FOUR**. ⇒⇒□ **⇒⇒□ A FIELD ACCESS ON THE WRONG SHAPE IS SILENT, AND `|| []` HID IT.**

v3.35.0 — Added Part 86: The Chrome Inviolability Rule — the law that the VibeCoder Shell is the permanent physical architecture, that no generated Recipe may render over, hide or replace it, and that the Generator's output is confined to the canvas slot. **PART NUMBERING.** The dispatch named **Part 85** and instructed "find the highest `## Part N` heading and use N+1". MEASURED: the highest heading was already **85** (`## Part 85 — The Standalone Showcase`, landed by FVC 1328 at `a80fbc54`), so the next free number is **86** — the dispatch's RULE is followed and its TEXT's number is stale, and the two are recorded separately rather than silently reconciled. **THE VERSION AND THE PART NUMBER ARE INDEPENDENT COUNTERS** (Part 85 §85.7): the version is derived from the highest `v3.N.0` marker (**34** → **v3.35**) and the Part from the highest heading (**85** → **86**). **THREE OF THE DISPATCH'S FOUR CLAUSES DESCRIBE A CODEBASE THAT DOES NOT EXIST, AND THE CORRECTIONS ARE STRONGER THAN THE CLAIMS THEY REPLACE.** **THE HEADER IS NOT `position: fixed` AND NOT AT THE HIGHEST Z-INDEX.** MEASURED: `src/shell/fragments/header/Header.tsx:140-142` is `position: sticky; top: 0; z-index: 50`, and `src/modules/panel-floating/src/panel-floating.css` carries `z-index: 2147483645` and `2147483646`. ⇒⇒⇒ **⇒⇒□ A RULE THAT NAMES A z-INDEX IT HAS NOT MEASURED CANNOT BE ENFORCED** — and the correct law is stronger anyway: the chrome is inviolable **by construction**, not by winning a stacking contest. **THE CHROME IS A GENERATED ARTEFACT — THAT IS THE REAL DANGER.** MEASURED: `src/shell/fragments/header/Header.tsx:1-2` reads `Header — GENERATED FILE. DO NOT EDIT.`, emitted by `src/modules/generator/src/generate-react.cjs`. ⇒⇒⇒ **⇒⇒□ THE INVOLABILITY IS NOT ABOUT WHO WROTE THE CHROME; IT IS ABOUT WHERE THE GENERATOR'S OUTPUT IS ALLOWED TO MOUNT.** **THE CANVAS NODE IS NOT `.fv-canvas-container`.** MEASURED: no such class exists; the real contract is `src/shell/Shell.tsx:72-76` — `<div className="fv-shell-canvas" data-fv-canvas-slot="shell">`. ⇒⇒□ **⇒⇒□ THE RULE NAMES THE REAL NODE, OR IT NAMES NOTHING.** **AND THE REAL MECHANISM IS A STACKING CONTEXT, NOT A `z-index` RULE.** MEASURED (`src/shell/Shell.tsx:1137-1152`): the canvas is `z-index: 0` with the code's own comment *"THE CANVAS IS ITS OWN STACKING CONTEXT … nothing inside it can paint over the chrome"*, and `overflow-x: hidden; overflow-y: auto`. The panel reservation is a **GRID TRACK** on `.fv-shell-body` — `grid-template-columns: var(--fv-shell-left-column, 0px) minmax(0, 1fr) var(--fv-shell-right-column, …)` (`:1026-1032`), the canvas is `grid-column: 2` (`:1110-1113`), and the side columns are set at `:1310-1315` — not padding on the canvas, and not an overlay. **THE SHOWCASE IS A GENERATED RECIPE, NOT A HAND-AUTHORED PAGE.** MEASURED: `src/shell/showcase/ShowcaseHeroCard.tsx:44` imports `HeroWidget` from `../../modules/showcase/Showcase`, and `src/modules/showcase/Showcase.tsx:2` reads `Header — GENERATED FILE. DO NOT EDIT.` ⇒⇒⇒ **⇒⇒□ THE SHOWCASE IS STATIC IN BEHAVIOUR AND GENERATED IN SUBSTANCE** — the two facts are ORTHOGONAL, and conflating them is how a chrome rule comes to mandate the wrong architecture. **THE VALIDATOR DOES NOT CHECK THE ROOT ROUTE'S DOM, AND THIS PART DOES NOT CLAIM IT DOES.** MEASURED: `scripts/fvc1328-validate.cjs` is **not in `package.json`'s `scripts` and not in `.github/workflows/ci.yml`**; the build is `audit-operator-flow.py && vite build && write-version-receipt.cjs && copy-pact-specs.cjs`; and there is **no DOM-tree check of the root route** in `scripts/`, `src/` or `tools/`. ⇒⇒□ **⇒⇒□ A SPEC THAT PROMISES AN UNBUILT GATE IS WORSE THAN A SPEC THAT DECLARES THE GAP** — because the first is believed and the second is not. ⇒⇒□ The STOP CONDITIONS are written as law with the enforcement mechanism declared **OPEN**. **THE REAL INVASION MECHANISM IS THE DOCUMENT ROOT, NOT THE STACKING ORDER.** MEASURED: the theme and skin live on `document.documentElement`'s `data-fv-theme` / `data-fv-skin` attributes (`src/__tests__/fvc1269-header-controls.spec.tsx:246`, `:268`), so a generated page that wrote `document.body` or `document.documentElement` would rewrite the app's own state surface. ⇒⇒□ **⇒⇒□ THAT IS HOW A RECIPE INVADES THE CHROME** — not by out-ranking it, but by changing the attributes the chrome reads. **THE ROOT DECIDES, ON ONE TRUTH.** MEASURED: `src/shell/ApplicationRoot.tsx:71-81` asks `isMasterDashboardPath`, then `isShowcasePath`, and otherwise returns `<Shell />`; `isShowcasePath()` (`src/shell/showcase-route.ts:48-52`) compares `===` against `'/'`. ⇒⇒□ **⇒⇒□ A RECIPE CANNOT INVADE THE SHELL BECAUSE THE ROOT NEVER HANDS THE SHELL'S SLOTS TO A RECIPE.** 

v3.34.0 — Added Part 85: The Standalone Showcase — the customer's landing page, the three-column composition with the glowing canvas, and the designed empty state. **PART NUMBERING.** Part 85 is the next free number: the file carries **80** `## Part N` headings and the highest is **84**, so the next is **85** — derived by scanning the headings, not assumed. **THE VERSION AND THE PART NUMBER ARE INDEPENDENT COUNTERS.** MEASURED: they have never matched — v3.29.0 added Parts 77–80, v3.17.0 added Part 61, v3.20.0 added Part 64 — so the version is derived from the highest `v3.N.0` marker (**33** → **v3.34**) and the Part from the highest heading (**84** → **85**). **THE SHOWCASE RENDERS OUTSIDE THE SHELL.** The dispatch's acceptance criterion is a three-column page, and the editor chrome belongs to the BUILDER at `/project/:id` — so the Showcase is a NEW page, not a re-skin. MEASURED: the live `/` was the toolbar, the ASSETS and DECK handles, the VIBECHAT and PANELS pills, a flat mountain-rail hero with NO card and NO glow, and a project grid that included the product's own scaffolding. **THE BYPASS IS AT THE APP ROOT, ON THE MASTER DASHBOARD'S SHAPE.** MEASURED: the old code read `window.location.pathname` ONCE, at boot, and rendered the result — so a client-side navigation to `/` would have LEFT THE SHELL ON THE PAGE. ⇒⇒⇒ The decision now lives in `ApplicationRoot`, which reads the pathname from the routing engine's own `useSyncExternalStore` subscription — ONE truth about the URL, not two. **AND THE ROUTE TABLE IS UNCHANGED.** The Showcase is deliberately NOT a row: the route table binds a URL to a SHELL view, and a row with no Shell branch is a latent fall-through to the home view. **THE OVERLAP IS VISUAL, NOT INTERACTIVE.** MEASURED TWICE: the hero's overlap first covered the chat card's SEND BUTTON — rendered, visible, and UNREACHABLE — and then the hero's own FRAME intercepted the click, because a painted background still swallows a click. ⇒⇒⇒ A TRANSPARENT BACKGROUND IS NOT A FIX; IT ONLY MOVES THE PROBLEM TO THE NEXT PAINTED LAYER. ⇒⇒⇒ ⇒⇒□ The visible card is the ARTWORK, the frame is transparent and pointer-transparent, and the only thing that crosses the side columns is the GLOW, which is `pointer-events: none`. **THE GLOW IS ONE LAYER WITH ONE GRADIENT.** MEASURED FOUR TIMES: `inset: -26%` made it a wash in the viewport's top-left corner (a percentage of a box that is itself oversized is not a radius); fixed offsets on the FRAME centred it 144px left of the card (a centre measured from the wrong box is not the card's centre); the artwork's own background painted OVER it (a gate that measures an element's properties cannot see that the element is covered); and `overflow: hidden` on the artwork clipped it at the card's own edge. ⇒⇒⇒ ⇒⇒□ **THE SCREENSHOT IS THE PROOF** — the gate passed while the card had NO GLOW AT ALL. **THE EMPTY STATE IS A DESIGNED PAGE.** MEASURED: the empty list and the loading state are DIFFERENT FACTS, and a page that chose between them on `projects.length` alone would tell a customer they have no projects BEFORE THE BRAIN HAS ANSWERED. ⇒⇒⇒ The precedence is LOADING → EMPTY → READY, and the empty state keeps the top bar and the status bar. **NO NEW RUNTIME DEPENDENCIES.** MEASURED: `package.json` and `package-lock.json` are UNTOUCHED — no `react-router`, no icon package, no animation library. The icons are inline SVG, the animations are CSS keyframes, and the routing is the engine's own. 

v3.33.0 — Added Part 84: The Root Route and Scoping — the `/operator` route, the rule that hides the product's own scaffolding from a customer, and the resolution of the 15 harvested components into real renderable widgets. **PART NUMBERING.** Part 83 is the next free number: the file carries **78** `## Part N` headings and the highest is **82**, so the next is **83** — derived by scanning the headings, not assumed. **NO `react-router`.** The dispatch asked to "implement the React Router", and MEASURED: there is no `react-router`, the routing engine is **deliberately** dependency-free (History API + `useSyncExternalStore`), and its own header states three measured reasons — the Header is a GENERATED file whose contract is "plain React, no runtime dependencies"; Master Spec Part 53 item 3 asks for `<a href="...">`, not for `<Link>`; and zero dependencies means zero lockfile churn. ⇒⇒⇒ **⇒⇒⇒ THE ROUTE SEPARATION IS DELIVERED BY EXTENDING THE EXISTING ENGINE.** ⇒⇒⇒ ⇒⇒⇒ **THE ROUTE TABLE GAINS AN `operator` ROW.** ⇒⇒⇒ MEASURED: before it, `resolvePath('/operator')` returned `{kind:'none'}` and the operator's route **silently rendered the home page**. ⇒⇒⇒ ⇒⇒⇒ **⇒⇒⇒ A ROUTE THAT DOES NOT RESOLVE IS A ROUTE THAT DOES NOT EXIST, WHATEVER A DISPATCH SAYS ABOUT IT.** ⇒⇒⇒ ⇒⇒⇒ **THE HIDING IS BY PREFIX, NOT BY A DENY-LIST.** ⇒⇒⇒ MEASURED: the live project list carries `vibecoder-internals`, `vibecoder-home` and `vibecoder-self` — and the customer's grid showed all three. ⇒⇒⇒ ⇒⇒⇒ **⇒⇒⇒ THE PREFIX MAKES THE DEFAULT SAFE: `vibecoder-something-new` IS HIDDEN ON THE DAY IT IS CREATED.** ⇒⇒⇒ ⇒⇒⇒ **⇒⇒⇒ AND `vibecoder-self` HAS NO EXCEPTION.** ⇒⇒⇒ ⇒⇒□ MEASURED: the live list carries it under the NAME **"VibeCoder (editor)"**, and the repository's own doctrine says (`src/agent/active-context.ts:51`, `:86`) that it is "the SPA itself, not a project a node can belong to". ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ A PLAN PROPOSED EXCEPTING IT — AND THAT EXCEPTION WOULD HAVE LEFT THE PRODUCT'S OWN WORKSPACE ON EVERY CUSTOMER'S FIRST SCREEN.** ⇒⇒□ ⇒⇒□ **THE 15 HARVESTED COMPONENTS RESOLVE TO REAL COMPONENTS.** ⇒⇒□ MEASURED: the `box` atom renders a GENERIC element and does **not** look up `data-widget` — so a harvested local component rendered as a PLAIN DIV and the component was SILENTLY LOST. ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ THE EMITTER NOW RESOLVES IT, AND AN UNRESOLVED ONE IS A BUILD ERROR.** ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ AND A STRING PROP IS `name="value"` WHILE AN EXPRESSION PROP IS `name={value}`** — because a component receiving the TEXT `"rowsOf(card.properties)"` instead of the VALUE renders empty, and it does not fail to compile. ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ PREMISE CORRECTED BY MEASUREMENT: THE `vibecoder-internals/home` TREE IS NOT MISSING.** ⇒⇒□ ⇒⇒□ MEASURED: a `curl` with an unencoded slash answered **404**, and the first version of this phase "corrected" the binding on that evidence. ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ THAT WAS WRONG** — the client reads a tree at `/api/agent/tree/${encodeURIComponent(pageKey)}` (`tree-store.ts:138`), so the tree is fetched as `vibecoder-internals%2Fhome` and answers **HTTP 200**. ⇒⇒□ ⇒⇒□ **⇒⇒□ ⇒⇒□ ⇒⇒□ A PROBE THAT IS NOT THE CLIENT'S PROBE IS NOT A PROBE.** ⇒⇒□ ⇒⇒□ ⇒⇒□

v3.32.0 — Added Part 83: The VSIL Semantic Deduction — the operator's mandate that tooltips, tags and floating text overlays are, **by definition**, in front of the main subject, and the machinery that makes the model, the prompt and the validator agree on that one rule. **PART NUMBERING.** Part 82 is the next free number: the file carries **77** `## Part N` headings and the highest is **81**, so the next is **82** — derived by scanning the headings, not assumed. **THE VOCABULARY IS NEW.** MEASURED: `vsil:ui` and `vsil:float` existed NOWHERE — not in this repository, not in the Gallery's `feed/registry.json` (whose `vsil` entries are empty arrays), and not in the FvW §20 doctrine, which describes a VSIL **scene** but names no profiles and no layers. ⇒⇒⇒ So this Part **defines** them, and §82.1 is the definition. **THE MANDATE IS CARRIED VERBATIM.** §82.2 states the operator's words: *"If you see tooltips or tags over an image, you MUST assign them to the `vsil:ui` or `vsil:float` profile, assign them a `layer` integer higher than the underlying image, and provide an `anchor` or `transform` coordinate."* **AND THE OUTPUT REFLECTS IT.** A base image node is layer **1**; a floating text node over it is layer **2** or higher. **ONE SOURCE, NOT TWO.** MEASURED: the VSIL vocabulary lived in **two** prompt builders — `scaffolding/prompt-builder.cjs` and `multi-step-prompt-builder.cjs` — and neither imported the other, so two copies of a rule is two rules that drift. ⇒⇒⇒ The rule now lives in `scaffolding/vsil-semantic.cjs` and both builders import it. **THE PROMPT IS NOT ENOUGH.** The clause is appended to the PROMPT — last, because the last block is the one a model follows most closely, as the multi-step builder already says of itself — **and** the deduction is applied in the REPAIR LAYER, because a prompt is a request and a repair layer is a correction. ⇒⇒⇒ MEASURED: a model that answers `layer: 1` for a tooltip is RAISED to layer 2, and the correction is REPORTED rather than applied silently. **THE SILENT FAILURE THIS PREVENTS.** An overlay that shares a layer with the subject, or sits below it, renders **behind** the image. ⇒⇒⇒ The build succeeds, the gate passes, and the tooltip is invisible. ⇒⇒⇒ That is a lie that ships. **TWO OVERLAYS MAY NOT SHARE A LAYER.** MEASURED: the first version of the stacking rule used the overlay's INDEX as its floor, and with a base at layer 1 two overlays both landed on layer 2 — the second drawn under the first. ⇒⇒⇒ The floor is now the highest layer assigned so far, plus one. **AND THE GATE REPORTS THE INPUT'S FAULTS, NOT THE OUTPUT'S.** MEASURED: the first version validated the DEDUCED images — which the deduction had already corrected — so it returned `ok: true` for an input that was wrong. ⇒⇒⇒ A gate that passes everything is not a gate.

v3.31.0 — Added Part 82: The Harvest Protocol — the tool Part 80 mandated, as built and measured, plus the one place this implementation had to go beyond the letter of Part 77.1. **PART NUMBERING.** Part 81 is the next free number: the file carries **76** `## Part N` headings and the highest is **80**, so the next is **81** — derived by scanning the headings, not assumed. **PART 81 DOES NOT WEAKEN PARTS 77–80.** Part 80 §80.1 named the tool; this Part states what the tool IS, so that a later build measures against a written contract rather than against an implementation. **§81.6 IS A MEASURED DEVIATION, DECLARED.** Part 77.1 writes the Codex shape as `{ behaviors: { [nodeId]: { onClick, onMount, dataSource } } } }`. A real harvest of the Dashboard produces an **`onChange`** behaviour — `DashboardScopeControl` carries `onChange={setActiveScope}` — so a rule that accepted ONLY the three enumerated names would make the harvester's own output **INVALID BY CONSTRUCTION**, and would force an operator to either drop a real behaviour or rename it to `onClick`, both of which are **false**. The Validator therefore enforces the **STRUCTURE** (an entry is an object; the map is an object) and accepts the three named behaviours **plus the React event family**, listed in one visible place in the rule. **This is a widening of the law's example, and it is declared here rather than hidden in code.** **THE VACUOUS PASS IS CLOSED.** Measured: the Validator's previous discovery was "a directory under `pact/<scope>/` that has a `recipe.md`", and this repository has **no** `pact/<scope>/<module>/recipe.md` layout — so it found **ZERO** module roots, and a validator that scans nothing reports nothing wrong and exits 0. Part 77 §77.2 already required the exit-1; Part 81 states the JSON discovery that makes the count meaningful — **115** module roots (`src/modules` 40, `app-modules` 75). **A RULE'S STATS ARE NOW CARRIED THROUGH THE ENGINE.** Measured: `validator-engine.js` kept only `{ ok, errorCount, warningCount }` and **dropped** the rest of a rule's `stats`, so a rule that reported `modulesScanned` had its number thrown away and the CLI had no way to ask the question Part 77 §77.2 turns on. **THE HARVESTER USES A REAL PARSER.** `typescript@5.9.3`'s compiler API, not regex — because regex over JSX silently mis-reads a nested tag, and the failure is a recipe that LOOKS right and builds the wrong thing. **A NORMALISER MUST NOT DECIDE WHICH KEYS SURVIVE BY WHITELIST.** Measured: the first artifact normaliser rebuilt each Codex from a fresh object and copied only `rules`, and it **destroyed** `src/modules/properties-panel/recipe-book/codex.json`'s `schemas` map — which is what the Properties Panel renders (`properties-panel.tsx:176` reads `cdx.schemas[kind]`). The browser gate caught it; a unit test could not, because the Codex is read only at runtime by a mounted panel. The rule is now: **copy everything not deliberately replaced**, and the release ships an audit that checks every original top-level key survives across all **160** artifact files. **THE HARVEST RECORDS WHAT IT CANNOT BUILD.** Measured: the Dashboard uses **fifteen** local components with no renderer in the 23-widget vocabulary. They are recorded as `harvestOnly` nodes and named in the Codex's `harvestOnly` block — **truthful**, rather than mapped to a `box` atom that the Generator would render as a plain div and silently lose the component.

v3.29.0 — Added Parts 77–80: The JSON Mandate & Schema Enforcement, The Panel System Replacement, The Routing Boundaries & Renderer, and The Harvest Protocol. **PART NUMBERING CORRECTED.** The dispatch asked to append Parts 46, 47, 48 and 49, but **all four numbers are already occupied** with different subjects — Part 46 is "The Vision Extractor" (line 1195), Part 47 is "The Stencil Snapshot Archive" (line 1209), Part 48 is "The Decision Graph" (line 1215) and Part 49 is "The FvW Module Structure" (line 1224) — so the four new Parts are **77, 78, 79 and 80**, the next free numbers. **THE DISPATCHED TEXT IS PRESERVED VERBATIM**, modulo the Part renumbering and the section renumbering that follows from it; the appended block is byte-identical to the dispatch apart from those numbers (sha256 `60f4c9076f53e09646e0d4782df4c30d520d0477318fb3649e5a5a1874b21c69`). **THE SPEC IS THE LAW, NOT A DESCRIPTION.** Per Part 16 §16.2, this document states what the system MUST be; the code is the compiled artefact and the gap between them is the work. Each of the ten dispatched mandates is therefore written as a MUST against a target state, and the measured present state is recorded separately in §80.3 as the gap against which a build agent measures progress — it is NOT folded into the law, and it does NOT soften it.

v3.28.0 — Added Part 76: The Seam's Actual Boundaries — what Part 75 measured, and what it did not. **PREMISE CORRECTIONS.** Measured against `origin/main` `4c9dabf1`, this dispatch is a **re-issue of FVC 1327**. **Version.** The dispatch requested v3.28.0 and **this release is v3.28.0** — unlike FVC 1327, which had to reject v3.28.0 because v3.27.0 was unclaimed, **v3.27.0 has since been published** (FVC 1327, merged `4c9dabf1`), so the sequence is contiguous again and the dispatch's version is correct for the first time. **Part numbering.** The dispatch requested Part 42, but **Part 42 is "The Trace Atlas"** (line 1124) — a different subject, already deployed and load-bearing — and Part 75 is the last Part in the file, so this is **Part 76**. **The dispatched text is NOT appended again.** The dispatched IR block — from `type IRNode = {` through `globalState: Record<string, any>; // From the Codex` — is **already published verbatim at §75.1**, and a programmatic substring test returns **`True` with exactly 1 occurrence**, at lines 2228-2244. Appending it again would put a second copy of the same IR type definition into the same spec. **The dispatch was TRUNCATED, in both issues, at the same place**: the `--- END SPEC TEXT ---` marker never arrived, so the dispatched text stops mid-§42.1 at the `IRDocument` type — no §42.2, no Emitter contract, no closing clause — and **nothing has been invented to fill that gap, in either issue**. **Part 75's citations re-verified.** All **twelve** of Part 75's line references into the two Generator files are in bounds and non-empty; **eleven still point at the right line and one has drifted by one** — the `children` passthrough is now `generate-react.cjs:268`, not `:267`. The Driver itself moved from `scripts/generate-react.cjs` to `src/modules/generator/src/generate-react.cjs` (`c120fad8`), but Part 75 cites it by **bare filename**, so the move invalidates nothing: **a path-neutral citation survives a file move, a path-bound one does not.** **One stale count.** The per-widget template table is **764 lines** (`react-emitter.cjs:332`-`1095`), not the **588** Part 73 measured and Part 75 carried forward — a drift of 176 lines that UNDERSTATES the work a `styles` field would move. **Three measurements Part 75 did not make.** (1) **Not one shipped recipe declares a `primitive`** — only `retrieval-index.json` and `.index/index.json` mention the key, so the primitive branch of `resolveNode` is live code with **no production caller**. (2) **`adapt()` normalises the CODEX as well as the Recipe** — it is the fallback that makes `codex.behaviour.WorkspaceTab` resolve, since no shipped Codex stores `behaviour` at the top level. (3) The Emitter **asserts its own vocabulary in both directions at module load** and throws on a mismatch, so the vocabulary **cannot drift silently**. **PART 75's CENTRAL STRUCTURAL CLAIM IS CORRECTED.** Part 75 asserts that a node with NEITHER `widget` NOR `primitive` "passes the vocabulary check and is dropped by the Emitter". That is **FALSE for the CLI path**: `validateRecipe` rejects such a node by name — `actual: "undefined"` — and the runner returns 1 **before** the Emitter is ever called (`generate-react.cjs:818` validates, `:840` renders). **The hole IS real, but on the EXPORTED LIBRARY PATH**: `renderComponent` does not call `validateRecipe`, and called directly with the same malformed recipe it returns a **37,517-character** component with the node silently absent — **1,003 characters** shorter than the correct 38,520. **The seam is protected where the build actually runs and unprotected where a library consumer calls it.** Part 75's law in §75.4 is unchanged and correct in all six items; only its **scope** was wrong, so the missing refusal is a **library-time** one rather than a build-time one, and the fix is correspondingly smaller and better located. The measurements are against `origin/main` `4c9dabf1` and every one of them is re-runnable with the commands shown.

v3.27.0 — Added Part 75: The Generator & Emitter Architecture (Exhaustive) — the IR contract at the seam where Part 71 and Part 73 meet. **PREMISE CORRECTIONS.** Measured against `origin/main` `cd2b27dc`, the dispatch's Part number, its version and its subject were all wrong. **Version.** The dispatch requested v3.28.0, but **v3.27.0 is unclaimed** — the spec's versions run contiguously to v3.26.0, the Notion canonical master (`402fc18c-b7ce-81c9-ae63-c3a099d01aad`) is titled `v3.26.0 (Canonical)` and carries `v3.19.0`…`v3.26.0` with Parts 1–74, and all 11 remote branches were checked with the highest spec version on any branch being `v3.26.0` — so this release is **v3.27.0**, and v3.28.0 would have left v3.27.0 a permanent hole. **Part numbering.** The dispatch requested Part 42, but **Part 42 is "The Trace Atlas"** (line 1122) — a different subject, already deployed and load-bearing — so this is **Part 75**, the next free number. **The dispatch's TEXT IS PRESERVED VERBATIM** in §75.1; only the number and the version are corrected. **The dispatch was TRUNCATED.** The `--- BEGIN SPEC TEXT ---` marker was opened and the `--- END SPEC TEXT ---` marker never arrived, so the dispatched text ends mid-§42.1 at the `IRDocument` type — no §42.2, no Emitter contract, no closing clause. §75.1 is therefore the COMPLETE extent of what was dispatched, and **nothing has been invented to fill the gap**; everything from §75.2 onward is measured. **Subject.** "The Generator & Emitter Architecture" is already specified by Part 71 and Part 73, so Part 75 states the one thing neither Part says — the IR contract at the Recipe/Codex seam. **The present is measured, not described.** The tree has **NO IR stage**: the Emitter's entry point takes the RAW RECIPE (`emitComponent(recipe, codex, outPath)`, `react-emitter.cjs:1816`), the Driver's whole call into it is one line (`generate-react.cjs:552`), and the only normaliser is `adapt()` (`generate-react.cjs:215`), which passes a slot's `children` across as the SAME ARRAY REFERENCE (`:267`) — **the Recipe IS the IR and the Codex IS the global state.** The measured node shape is `{widget, props}`; the dispatch's `id`, `type`, `styles`, `behaviors` and node-level `children` are **ABSENT from every node in every recipe**, and the tree's discriminator is `primitive` (one of the eight atoms) with `widget` as the fallback — **not** the dispatch's `type` enum. **Three stale claims in this spec are corrected in place.** Part 73 §73.2's "the eight primitives are not in the tree" is STALE: `emitter.PRIMITIVES` returns all eight (`text, image, box, click, state, repeat, condition, bind`) and `primitiveProgram`/`renderProgram` are exported and used by `resolveNode`. Part 73 §73.2's "the two lists are DUPLICATED SOURCE, NOT A SHARED CONSTANT" is STALE: `KNOWN_WIDGETS` is now `emitter.WIDGET_VOCABULARY` (`generate-react.cjs:136`), the Driver IMPORTS the Emitter's list, and the measured membership of the 23-entry vocabulary and the 23-key template table is IDENTICAL. Part 71 §71.1's Vue and Svelte emitters remain the DESTINATION: `src/modules/generator/src/emitters/` holds exactly ONE file. **The one measured hole.** `resolveNode` answers `null` for a node it cannot resolve and `emitNode` turns that into `return ''` (`react-emitter.cjs:80-83`) — **a node is dropped silently, with no warning and no error** — while the only guard is upstream at the vocabulary (`KNOWN_NODES`), which protects the NAME and not the SHAPE. **The law (§75.4).** The Recipe is the IR until a real one exists; a node that does not resolve must be a NAMED REFUSAL, not an absence; the discriminator ORDER (`primitive` then `widget`) is the contract, because `renderChildren` filters `primitive === 'state'` out of the children list (`:1716`) — a `state` node is a DECLARATION and is lifted, not rendered; styling is NOT a node field; global state is the Codex's NAMED `behaviour`, not an untyped `Record<string, any>`; and a second Emitter must not change the Recipe. The measurements are against `origin/main` at `cd2b27dc` and every one of them is re-runnable with the same commands.

v3.26.0 — Added Part 74: The Reverse Trace Protocol (how to reconstruct a Recipe from working hand-
written code, prove it byte-identical via the
Generator, and migrate the hand-written modules
into the FvW).

v3.17.0 — Added Part 61: Mobile Interaction Models (the Progressive Disclosure Bottom Sheet on mobile: the collapsed full-width input bar, the typing strip showing the last message, the expanded message sheet with a drag handle, and the prohibition on floating window controls). Part 61 is numbered as the dispatch named it; Parts 56-60 are vacant and the gap is recorded in item 13, following PREMISE CORRECTION 1. The Codex for a mobile surface carries mobile_behavior in its responsive block, and the value names the PATTERN (bottom_sheet).

v3.25.0 — Added Part 73: The Universal Generator Doctrine. The Generator's contract should be a PRIMITIVE GRAMMAR of eight irreducible atoms (text, image, box, click, state, repeat, condition, bind) rather than a fixed list of allowed widgets, so that any UI composing legal primitives is legal, and a primitive the grammar lacks is a rare version bump rather than a rejection. **PREMISE CORRECTIONS.** Measured against `origin/main` `33d97730`, every premise in the dispatch was false, and the Part is published with the facts corrected in place rather than as dispatched. **Version.** The dispatch requested v3.24.0, but v3.24.0 is FVC 1273's release, so this release is **v3.25.0**. **Part numbering.** The dispatch requested Part 72, but Part 72 is already "The Two Categories of Modules" (FVC 1273, `d204498c`), so this is **Part 73**. **Scope.** The dispatch described FVC 1276 as the work that rewrites the React Emitter and rewrites every module recipe; FVC 1276 is DOC-ONLY, and the rewrite is recorded as FUTURE work. **The present is measured, not described.** The word `primitive` occurs 0 times in `src/modules/generator/`; the tree has a duplicated 23-entry vocabulary (`KNOWN_WIDGETS` at `generate-react.cjs:118-194`, `WIDGET_TEMPLATES` at `react-emitter.cjs:306-893`, identical membership, duplicated source), 588 lines of widget-specific template, and 3 hand-written widget-name comparisons (`react-emitter.cjs:1055`, `react-emitter.cjs:1203`, `react-emitter.cjs:1222`). The string "unknown widget" occurs 0 times in the Generator SOURCE, and once in prose in `recipe-book/codex.md` as the RULE "unknown widget is an error"; the actual refusal guidance is quoted verbatim in Part 73.1. **The Driver/Emitter split HAS landed** (FVC 1272, `3123800e`, merged `33d97730`), and this corrects Part 71 §71.2's stale "the split is SCHEDULED, not present" in place; Part 71 §71.1's Vue and Svelte emitters do not exist — `src/modules/generator/src/emitters/` holds exactly one file, `react-emitter.cjs`. **Part 73** names the eight primitives as a REQUIREMENT, not a description; states the three-step migration in the order the current code dictates; and draws the boundary on "zero hallucinations" precisely — the Generator does not render a surface it does not have, and a grammar makes the output composable and checkable, not correct. **One stale citation corrected.** The v3.24.0 entry and Parts 45 and 72 cited `generate-react.cjs:3107-3108` for the recipe-book reads; that range is out of bounds for a 903-line file, and the reads are at `generate-react.cjs:823-824`.

v3.24.0 — Added Part 71: The Generator Architecture, and Part 72: The Two Categories of Modules; and CORRECTED three false claims in Parts 45 and 54. **PREMISE CORRECTIONS.** The dispatch that requested these amendments stated the spec was at v3.22.0, that Part 70 was free, that exactly 75 modules shipped markdown-only, that 0.5ms/14ms were current measurements, that the category field was already `kind`, that `handbook.md` existed, that the Generator was already split into a Driver and an Emitter, and that the Validator's scope was unchanged. Measured against `origin/main` `66cd3f8b`, **every one of those premises was false**, and the amendments are published with the facts corrected in place rather than as dispatched. **Version.** The dispatch requested v3.23.0, but v3.23.0 was already consumed by FVC 1269 (Part 70.4), so this release is **v3.24.0**. **Part numbering.** The dispatch requested Part 70 for "The Generator Architecture", but Part 70 is deployed, load-bearing, and recorded in the live receipt; **deployed Part 70 is preserved verbatim** and the two new substantive Parts are **Part 71** and **Part 72**, following PREMISE CORRECTION 1. **Part 45 item 6 corrected.** The validator path was `fvw/validator-engine.js` (which does not exist; the engine is at `src/modules/validator/src/validator-engine.js`) and the rule count was eight (it is **ten** — `module-code-path` and `module-registry-generated` were omitted, and those two are the rules that catch a module that is wrapped but invisible and a registry that has drifted from its generator). The recipe-book rule `codex-structure.js` is also recorded as currently **vacuous**: it scans `pact/<scope>/<module>/`, and `pact/` holds no module directories. **Part 45 item 7 corrected.** The recipe-book is **JSON, not markdown** — the Generator reads `recipe.json` and `codex.json` (`generate-react.cjs:823-824`), while the Validator's recipe-book rule reads `recipe.md` and `codex.md`; the dispatch's "75 modules" is replaced by measured counts of **39 of 40** in `src/modules/`, **160 of 236** in the gallery, and **241 of 433** repo-wide, and `handbook.md` exists in **0** places repo-wide. **Part 54 item 4 rewritten.** The four constitutional artefacts (`module.json`, `recipe.json`, `codex.json`, `handbook.md`). **Part 71.** The Driver/Emitter split, with the monolith measured at `generate-react.cjs` and its hardcoded project-grid family recorded as the coupling the split must remove. **Part 72.** `kind: "compiled"` and `kind: "infrastructure"`, with `kind` recorded as not yet present in any `module.json` in `src/modules/`.

v3.23.0 — Added Part 70: The Dead Header Controls (a control that renders, is clickable and changes nothing is DEAD, and the generated Header's `?.` calls make a missing callback SILENT; the Shell supplies every callback the generated Header calls; the device, the theme and the skin are the APP'S OWN state surfaces, published on the Shell root and the document root and read back by the control, so the control and the app cannot disagree; the two header popovers are mutually exclusive; the menu options are the Codex's, and "default" REMOVES the attribute rather than setting the word "default", because the token library's default IS the `:root` block; a state attribute and an element attribute must not share a name; a dismiss layer must not cover the controls it dismisses; and a control's EFFECT is what proves it alive, never the presence of an onClick attribute). Part 70 records the two MEASURED causes of the eight dead controls — four missing callbacks, and an EMPTY `tabHrefs` on `/` that also killed the Home icon — and the two superseded pre-existing contracts (FVC 1218's "the tabs stay BUTTONS" and FVC 1252's "the tabs fall back to NOTHING"), both updated in their tests with their measurements per Part 68. It records the REJECTED Option B (hiding the tabs on `/` would have made the defect invisible rather than fixed, and would have failed the dispatch's own acceptance). It carries Rule 6 Exception 3: the dispatch named three targets and the fix required one new file (`src/shell/HeaderMenus.tsx`), because the alternative was to write state into a GENERATED artefact that the next generation erases. Part 70 is contiguous with Part 69; the Parts 66-67 gap stays recorded in Part 68.1, following PREMISE CORRECTION 1. Part 70.4 records the measured basis, including the browser harness scoring 8/20 against the unfixed build and 20/20 against the fixed one.

v3.22.0 — Added Part 69: The Panel Layout Reality (the Panel Layout System was split into
panel-shell, panel-floating and panel-dom by FVC 1220 and there is no panel-layout recipe;
the Generator cannot dock panels and emits only in-flow grid areas, with position: fixed
appearing zero times in it; docking is currently achieved by inset, by padding on the Canvas,
and not by a Recipe; the VibeChat panel is a bottom sheet by design and its desktop window
controls are intentional and must not be removed). Part 69 is numbered as the dispatch named
it and is contiguous with Part 68; the Parts 66-67 gap stays recorded in Part 68.1, following
PREMISE CORRECTION 1. Part 69.1 records the measured basis for all four items, measured on
2026-10-27 against the tree at 7f41e2db.

v3.21.0 — Added Part 68: The Test Loop Trap (a test that fails after a fix is a QUESTION, not a verdict: a real regression is repaired in the code, a pre-existing contract is updated in the test with a comment explaining why; and agents are forbidden from writing negative controls for scripts that self-verify, because a self-verifying script is its own proof). Part 68 is numbered as the dispatch named it; Parts 66-67 are vacant and the gap is recorded in Part 68.1, following PREMISE CORRECTION 1 and Part 62.5. The Spec Quality Checklist gains a Verification group with the four Part 68 questions. Rule 4 gains the matching 15-minute STOP boundary under NO AUTONOMY.

v3.20.0 — Added Part 64: The Home Project (the Home Page is not hardcoded; it is a VibeCoder project with ID `vibecoder-home`; the URL `/` loads the `vibecoder-home` Recipe; the Home Project can be edited using the Stencil). The Part also records the two bindings the clause depends on: the project id and the Recipe tree share one identity, and the project grid and the "New Project" button use the shared project reader and the shared create-project action.

v3.19.0 — Added Parts 58, 59, 60 and 63: The Deploy Gate (a dirty submodule pointer is not a source change; a refusal is posted at most once per window), The Registry Generator (the module registry is generated from the local module.json files and the VGM manifest, and the validator checks the output), The CinemaBackground Mandate (the real widget, the gallery owns the declaration and the app owns the rendering, no CSS fakes), and The Stencil Lifecycle (ephemeral UI, persistent recipes, the approval gate is the only way a candidate ships). Part 61 item 13 is updated: the vacant range is now 56-57, since 58-60 exist.

v3.18.0 — Added Part 62: The Handles (every handle carries a vertical text label; the handle has a 24px minimum width for swiping; the text is written vertically and centred). Measured against live production before the change: all four handles measured 16px wide with empty innerText. The size is carried by the token --fv-handle-width in src/styles/tokens.css, and the token and the component's fallback must be changed together. The colour strip is preserved, not replaced. The Part number is the dispatch's verbatim and the 56-61 gap is recorded in Part 62.5. Part 3.1's "thin, narrow strip" description is superseded; the rest of Part 3 is unchanged.

v3.16.0 — Added Part 55: The Background Layers (three background levels — Page, Section, Widget; the 'CinemaBackground' widget; the Codex's 'background' property). Part 45 gains items 15-17 (the Codex's background contract) and the Spec Quality Checklist gains two background items. The registry has no 'background' property and no 'CinemaBackground' entry; both are named as the companion change, not claimed as done.

v3.15.0 — Added Parts 47-51: The Stencil Snapshot Archive, the Decision Graph, the FvW Module Structure, the V-Agent Architecture, and the Five Pillars (fills the Part-numbering gap recorded in PREMISE CORRECTION 1; the spec is now contiguous from Part 41 to Part 54).

v3.14.0 — Added Parts 52-54: The State Engine, the Routing Engine, and the Module Hierarchy (Faces).

v3.13.0 — Added Part 46: The Vision Extractor (image to Widget Registry to Recipe; the registry's gradient, shadow and typography gaps are named).

v3.12.0 — Added Part 45: The Validator Gate.

v3.11.0 — Added Part 41: The Stencil (extended with the sandbox, Candidate Recipe and Proposed Diff rules); Part 42: The Trace Atlas (node-level addresses, Node-scoped diffs); Part 43: The Approval Gate (the diff that halts a non-matching deployment); Part 44: Header Restoration (the legacy PM2 feature set, wired to Nodes).

v3.10.0 — Added Part 40: The FCC Export Contract (export mandate, Revibe runtime dependency).

v3.9.0 — Grand Reconciliation: FvW version fix, Provider-Agnostic pipeline, Part 36 (Matrix), Part 37 (Revibe), Part 38 (Gaps).

v3.8.0 — Added Part 35: The Dual-Recipe State (Suggested vs Actual).

v3.7.0 — Added Part 34: The HQ Routing, Mirroring, and Historic Backfill Rule.

v3.6.0 — Added Part 32: The Execution Protocol (Universal Autonomy).

v3.5.0 — Added Parts 25-29: Validator Engine, Bug Database, Roadmap Scope, Guardian Agent, and Dev Panel UI.

v3.4.0 — Synced Part 7 Audit Checklist with Parts 17-24.

v3.3.0 — Added Part 23: The Tri-Scope Dashboard (Build, App, User data + context filtering).

v3.2.0 — Added Part 22: Mission Control (State of the Lane).

v3.1.0 — Mega-patch: Added Parts 17-20 (Geometry, Docked Panels, VibeChat Auto-Behaviors, Mobile Switcher).

v2.5.0 — Merged Dual-Path Rule from historical page. Added Parts 14, 15, 16.

v2.3.0 — Added Part 13: VibeChat & Agent Architecture (Tag Bundles, Agent Pool, Turn Schema).

v2.2.0 — Added Part 12: The Theme & Styling Engine (CSS standard, three styling tiers, theme architecture).

v2.1.9 — Added Part 11: The Assembly Line and Spec Quality Checklist.

v2.1.8 — Synced Part 7 acceptance criteria with Part 8 (Geometry) and Part 10 (Architecture).

v2.1.7 — Added Part 10: Component Architecture (Modules/Fragments vs Buckets/Slots/Controls).

v2.1.6 — Added Part 9: Canonical Module & Recipe Standards (cms-widgets, recipe-book path, 9.14.0 doctrine).

v2.1.4 — Added Part 8: Geometry & Interaction Rules (Accordions, no overlays, fixed handles, explicit 'Assets' name).

v2.1.3 — Purged 'pill' terminology (replaced with 'Handle'). Finalized naming hierarchy (Rails, Handles, Tabs, Deck, Panels). Updated translation table.

v2.1.2 — Naming overhaul (Rails, Tabs, Decks, Panels). Translation table added.

v2.1.1 — Fixed stale 'Drag' criterion; added acceptance criteria for Swipe Axes and Auto-Center.

v2.1 — Explicit header buttons, swipe axes separation, canvas auto-centering, naming shifts (Dock/Panels/Assets).

## Part 1 — The Identity

FreshVibe Coder is not an IDE. It is a Vibe-to-App Builder. It is a visual composition environment where ideas become applications.<br />The user starts with a vibe — a prompt, a thought, a conversation in VibeChat. The AI refines this into a structured brief. The AI then builds the app using FreshVibe components, following the FreshVibe Way. The visual builder is the stage where the user refines the generated result.<br />FreshVibe Coder is the FreshVibe App Builder. It is where the system meets the user's imagination.

### The Navigation Model

FreshVibe Coder has two states, driven by the <code>projectId</code>.<br />First, the <b>Home State</b>. When no project is open, you see the Home Icon, the Project Dropdown (which says "No project"), and the <code>[ DASHBOARD ]</code> tab. The Home Icon shows the Welcome Page, a beautiful introduction with quick-start templates. The Dashboard shows the Global Dashboard, the master view of all your projects.<br />Second, the <b>Project State</b>. When a project is open, the tabs change to <code>[ PREVIEW ]</code>, <code>[ LIVE ]</code>, and <code>[ DASHBOARD ]</code>. Preview is the default. The Home Icon clears the project and takes you back to the Welcome Page.

### The Workspace Tabs

FreshVibe Coder does not use browser tabs for sub-projects. It uses Workspace Tabs in the header. The main tab is <code>[ Preview ]</code>. When you isolate a module (like the Cinema Editor), a new tab opens next to it. The Preview tab stays open in the background. You can work on multiple tabs, and the AI's context is scoped to the active tab.

### The Drill-Down Model

The Canvas is a set of concentric circles. You start wide and drill down to the exact element.<br />The views are the layers. The <b>Widget Layer</b> shows sections and widgets. The <b>Float Layer</b> shows popups and banners. The <b>Cinema Layer</b> shows glows and shadows. The <b>Meta Layer</b> shows SEO and assets.<br />Every tag, in every layer, responds to two gestures. A <b>single-click</b> opens the properties panel. You edit the content. The page stays in context. The AI sees the whole page. A <b>double-click</b> isolates the node into a new Workspace Tab. The canvas clears. The AI's context is scoped to only that node.

### The Deployment Architecture

FreshVibe Coder is a Desktop App. It runs on the user's machine. It does not host the client's data.<br />There are two tiers. The <b>Local (Free)</b> tier runs the app on [localhost](http://localhost), with data on the user's disk. The <b>Cloud (Subscription)</b> tier deploys the app to Vercel, Netlify, or FreshVibe Host. The data stays with the user.<br />The <code>deployment</code> node in the FC brain tracks the state: the host, the URL, the stage, and the tier.<br />The Publish button changes its behaviour based on the state. A first-time deploy is handled by VibeChat. An update deploy just runs the script. The user pastes their API key in-context, and it is saved as a <code>credential</code> node in the FC brain.

## Part 2 — The Deployment Adapters

### The Deploy Adapter Interface

The bridge must call a standard interface for every host.

- <b>Method:</b> <code>deploy(options)</code>
- <b>Inputs:</b> <code>{ distPath, apiKey, projectId }</code>
- <b>Outputs:</b> <code>{ ok: true, url }</code> or <code>{ ok: false, error }</code>
- <b>Location:</b> <code>bridge/lib/deploy/<host>.cjs</code>

### Where the Adapters Live

The adapters live in <code>vibecoder-standalone/bridge/lib/deploy/</code>. They are standalone Node modules. They do not import from the app.

### The Credential Store

<b>Target Schema:</b> A <code>credential</code> node in the FC brain.

- <b>Fields:</b> <code>id</code>, <code>provider</code> (e.g., 'vercel'), <code>apiKey</code>, <code>scope</code> ('user' \| 'app'), <code>createdAt</code>.
- <b>Write:</b> <code>POST /api/fcc/nodes</code> with <code>kind: 'credential'</code>.
- <b>Read:</b> <code>GET /api/fcc/nodes?kind=credential&provider=vercel</code>.

### The Publish Path

The Publish button calls the deploy adapter. It does not run a shell script directly.

- <b>First Deploy:</b> VibeChat calls the adapter, passing the API key.
- <b>Update Deploy:</b> The adapter is called with the saved <code>projectId</code> from the <code>deployment</code> node.

### The Deploy Edge (Rule 1 v5.11.0)

Every merge to <code>main</code> MUST deploy and pass the live receipt. If a dispatch is docs-only or panel-only, it still deploys, but the <code>/version.json</code> will not change. The receipt check passes if the hash matches <code>origin/main</code>.

## Part 3 — The Panel & Handle System

### 3.1 The Handle System (Global)

- <b>Appearance:</b> Thin, narrow strips on the left or right edge.
- <b>Z-Index:</b> Always above the panels.
- <b>Actions:</b> Tap to open panel. Swipe in to open panel (or cycle if stacked).
- <b>The Deck:</b> The full catalogue. If a panel is closed via the "X", it is removed from the Handles. The <i>only</i> way to reopen it is to find it in the Deck.

### 3.2 The Panel Header (Custom Chrome)

- <b>Standard Header:</b> No OS minimize/maximize.
- <b>Components:</b>
  - <b>Left:</b> Minimize (<code>—</code>) button. Action: Collapses the panel to a Handle.
  - <b>Center:</b> Title (colour-coded). Action: Acts as the drag handle for resizing.
  - <b>Right:</b> Close (<code>✕</code>) button. Action: Destroys the panel (removes from memory and the Panels menu).

### 3.3 The Collection Model

The Deck is populated by Collections, launched from a Tab on the Rail. A Collection groups panels by domain.

- <b>Active Collections:</b> Bright, in-context. Rendered first.
- <b>Available Collections:</b> Greyed out, out-of-context. Rendered after Active.
- <b>Absent Collections:</b> Not in the manifest. Not rendered.<br />The Dock grid is max 2 columns.<br /><b>Sorting:</b> Active first, Available second. Absent is never shown.

### 3.4 Contextual Availability

- <b>The Eye Icon:</b> Toggles the load state of a collection to save memory. Unloaded collections destroy their panel scripts.
- <b>Contextual Activation:</b> The active canvas layer (Widget, Float, Cinema, Meta) determines which collection is active.
- <b>The Absence Rule:</b> Features not shipped in the current context (e.g., Cinema in a CMS app) are completely absent, not greyed out.

### 3.5 Naming & Component Conventions

- <b>Rail:</b> The thin track that holds Handles or Tabs. Rails can be global (screen edge) or internal (inside a Panel).
- <b>Handle:</b> A clickable/swipeable element on a global Rail. It opens a Panel or switches context.
- <b>Tab:</b> A standard horizontal tab bar at the top of a Panel. It switches views.
- <b>Deck:</b> The 2-column launcher grid that opens from a Handle.
- <b>Panels:</b> The quick-switcher menu at the bottom of the screen showing open panels.
- <b>Assets:</b> The left-side panel (Widgets, Scenes, Navigator).

<b>The Universal Tab Component:</b><br />All Tabs (inside panels) MUST be instances of the same base component. Styling a Tab in the theme/skin affects every Tab everywhere. Variations are handled by CSS modifiers.

<b>Translation Table (Spec ↔ Code):</b><br />When writing dispatches, builders MUST map the new spec vocabulary to the current codebase vocabulary.

| Spec Name | Current Code Name | Location |
| --- | --- | --- |
| Deck | <code>edge-panel</code> | <code>src/cms/runtime/edge-panel/edge-panel.js</code> |
| Panels | <code>.fvcms-dock-pill</code> | <code>src/cms/runtime/panel-manager/panel-manager.js</code> |
| Handle | <code>.fvcms-dock-pill</code> (on Rail) | <code>src/cms/runtime/panel-manager/panel-manager.js</code> |
| Rail (Global) | (does not exist yet) | N/A |
| Assets Panel | <code>gallery-panel</code> / <code>navigator</code> | <code>src/cms/runtime/gallery/gallery-panel.js</code>, <code>src/cms/runtime/navigator.js</code> |

## Part 4 — The Asset Panel

The Widgets, Scenes, and Navigator surfaces are not separate panels. They are three tabs of a single "Asset Panel".

- <b>Tab 1: Widgets</b> (icon cards).
- <b>Tab 2: Scenes</b> (PNG cards, or empty state).
- <b>Tab 3: Navigator</b> (the layer tree).
- <b>The Width:</b> Max 3 tabs. Do not cram more than 3 tabs into a 2-column panel. If more functionality is needed, it should be grouped into a drill-down or a new Collection.
- <b>The Rail (Desktop):</b> On desktop, the Asset Panel and the Deck must be structurally attached to the Rail. They CANNOT float.
- <b>The Dock (Mobile):</b> The Asset Panel docks to the left or right side (it is only 2 columns wide, \~30% screen). VibeChat docks to the bottom.

## Part 5 — VibeChat Specific Rules

- <b>The Inner Handle:</b> VibeChat's thread pearl (inside the panel) must be visually distinct (colour/shape) from the outer edge Handles.
- <b>Conditional Hiding:</b> If the app being built has its own chat UI, VibeChat can be closed completely (killing its Handle) to avoid redundancy.

## Part 6 — Mobile Behaviour

- <b>Dock:</b> Panels dock to the <b>bottom</b> (sheet).
- <b>Size:</b> Max 2/3 of screen height. Default 50%. Remembered per panel.
- <b>Content:</b> Inner padding (not outer margin) to clear the edge Handles.
- <b>The Anchors:</b>
  - <b>Left Edge:</b> Assets (Widgets, Scenes, Navigator).
  - <b>Right Edge:</b> Dock (The launcher for all collections).
  - <b>Bottom Edge:</b> VibeChat (the AI) and Panels (the quick switcher).
- <b>The Swipe Axes (Critical):</b>
  - <b>Vertical (Up/Down):</b> Controls accordion detents (VibeChat) and resizing (Panels).
  - <b>Horizontal (Left/Right):</b> Switches panels. A left/right swipe <i>anywhere</i> in the panel (header or body) switches to the next open panel in the queue.
- <b>The Auto-Center Rule:</b> When switching panels via swipe or menu, the canvas automatically pans to center the target tag/node in the visible area above the panel.
- <b>Mobile Views:</b> The Canvas renders a "mobile view" (flowed, single column) on mobile viewports, and a "desktop view" on desktop viewports.

## Part 7 — Audit & Acceptance Criteria

Any build dispatch referencing this spec must verify:

- [ ] Tabs are thin, on the Rail, z-index above panels.
- [ ] Panel header has Minimize (—), Center Title (drag handle), Close (✕).
- [ ] Panel size is remembered.
- [ ] Content uses inner padding, not margin.
- [ ] Deck is attached to the Rail on desktop (no floating).
- [ ] Asset Panel has exactly 3 tabs (Widgets, Scenes, Navigator).
- [ ] Collections are sorted Active (bright) then Available (grey).
- [ ] Mobile: VibeChat has 3 detents.
- [ ] <b>Swipe Axes:</b> Left/Right swipes anywhere on a panel switch to the next open panel. Up/Down swipes scroll or resize.
- [ ] <b>Auto-Center:</b> Switching panels pans the canvas to center the target tag above the panel.
- [ ] <b>Geometry (Rails):</b> Handles are fixed to the screen edges and are at least 24px wide / 96px tall. They are coloured. <i>(The 24px floor is Part 62's, and supersedes the 16px this line previously stated — the measured baseline was 16px and every handle was too narrow to swipe.)</i>
- [ ] <b>Geometry (Dock):</b> The Deck and Assets panels are docked sidebars. They do not use a full-screen dark backdrop.
- [ ] <b>Geometry (Accordion):</b> The Deck and Assets panels use an inline drill-down accordion, not a modal or page navigation.
- [ ] <b>Geometry (Name):</b> The left panel header reads exactly "Assets".
- [ ] <b>Architecture (Modules):</b> UI fragments (like the InputBar) are built as standalone modules with their own recipe-book, and imported by reference.
- [ ] <b>Architecture (Controls):</b> Widget settings use the 13 Buckets and fill Slots with Controls that match by name.
- [ ] <b>Geometry:</b> Panels resize via hover cursors (<code>col-resize</code>/<code>row-resize</code>). No visual corner handles.
- [ ] <b>Geometry:</b> Floating panels have Minimize (<code>—</code>) and Close (<code>✕</code>) on the top right.
- [ ] <b>Geometry:</b> Panels are constrained to <code>.fv-shell-body</code> and never slide under the top header.
- [ ] <b>Docked Panels:</b> When docked left/right, the header disappears and is replaced by a title + Stretch/Cover toggle.
- [ ] <b>VibeChat:</b> The input bar is a strict single row with <code>+</code> (attach), text, mic, and send. No detent buttons in the bar.
- [ ] <b>VibeChat:</b> Sending a prompt auto-expands the Strip. The Strip auto-collapses if the user clicks the canvas.
- [ ] <b>Mobile Sheets:</b> Sheets have a visible drag handle with an <code>X</code> on the far right. Swiping the handle left/right destroys the sheet.
- [ ] <b>The Switcher Menu:</b> Tapping the bottom "Panels" pill opens a menu of active sheets that can be reordered via drag.
- [ ] <b>Mission Control:</b> The Mission Control node exists in the FC Brain and is updated on every dispatch close.
- [ ] <b>Dashboard Scopes:</b> The Dashboard has a segmented control <code>[Build Data] [App Data] [User Data]</code>. The Global scope respects <code>fvc1065</code> (no cross-project bleed).

## Part 8 — Geometry & Interaction Rules

This section dictates the physical CSS layout to prevent misinterpretation.

### 8.1 The Rails and Handles

- <b>Rails:</b> Must be <code>position: fixed</code> on the screen edges (left, right, bottom). They must be visible tracks.
- <b>Handles:</b> Must be at least <code>24px</code> wide and <code>96px</code> long. They must be coloured (Assets = Blue, Deck = Green, VibeChat = Purple). They must never be small squares. <i>(The 24px floor is Part 62's, and supersedes the 16px this line previously stated.)</i>

### 8.2 The Deck & Asset Panels (The Accordion)

- <b>The Layout:</b> The Deck (right) and Assets Panel (left) must be <b>docked sidebars</b>, NOT full-screen overlays.
- <b>The Name:</b> The left panel title must read exactly "Assets".
- <b>No Backdrop:</b> There is no dark full-screen backdrop. The canvas shrinks to fit the remaining space.
- <b>The Accordion Interaction:</b> Both the Deck and the Asset Panel use a drill-down accordion pattern.
  - The panel opens showing a 2-column grid of large, rounded-square category buttons.
  - Tapping a category (e.g., "CMS" or "Layout") expands that specific container inline to show its sub-items (e.g., Widgets, Media, or Section, Grid, Container).
  - It does not open a new page or a modal. It expands vertically within the panel.

### 8.3 The Header

- The header must be a single row. The "hamburger" menu opens the Deck as a second row (Mega Menu style) that pushes the canvas down, not a sidebar that covers the screen.

## Part 9 — Module & Recipe Standards

This section defines where modules live and how their recipes are structured, based on the FVC 1126, FVC 1128, and FVC 1130 audits.

### 9.1 The Canonical Tree

- <b>The code lives in </b><b><code>cms-widgets/</code></b><b>.</b> The <code>app-modules/</code> tree is a legacy metadata registry. The <code>src/</code> tree is for core VC modules.
- <b>The live list</b> is defined by <code>src/cms/data/cms-widgets-index.json</code>.

### 9.2 The Path Structure

- <b>The App Pact (</b><b><code>pact/</code></b><b>)</b> is for the entire application's rules.
- <b>The Module Recipe-Book (</b><b><code><module>/recipe-book/</code></b><b>)</b> is for the module's blueprint.
- <b>Every module MUST have a </b><b><code>recipe-book/</code></b><b> folder.</b> No exceptions.

### 9.3 The Validator Fix

- The FvW validator currently scans <code>pact/</code> for module recipes, causing a 100% vacuous pass (0 modules scanned).
- The validator MUST be updated to scan <code><module>/recipe-book/</code> to enforce module compliance.

### 9.4 The Doctrine Version

- The vendored doctrine (<code>9.13.0</code>) is stale. The fleet adopts <code>9.13.0</code> from the gallery <code>origin/main</code> — the gallery <code>VERSION</code> file reads <code>9.13.0</code> and the doctrine CHANGELOG's latest entry is <code>v9.12.0</code>. The previously recorded <code>9.14.0</code> was a hallucination: <code>9.14.0</code> appears in 0 files in the gallery, as do <code>9.15.0</code> and <code>9.16.0</code>.

## Part 10 — Component Architecture

This section defines how UI surfaces and their settings are built.

### 10.1 The Two Models

- <b>The UI Model (Modules & Fragments):</b> The surface of the app is built from Modules (e.g., VibeChat) which import Fragments (e.g., InputBar, MessageList). Fragments are reusable shared components.
- <b>The Settings Model (Buckets & Slots):</b> The settings panel for a widget is built from 13 fixed Buckets (e.g., background, text). Each bucket contains Slots. Controls fill those slots.

### 10.2 The Bucket Hierarchy

- <b>Bucket:</b> A namespace for slots (e.g., <code>background</code>).
- <b>Slot:</b> A named position inside a bucket (e.g., <code>background.image</code>).
- <b>Control:</b> The UI component that fills a slot (e.g., <code>ImagePicker</code>).
- A control fills a slot by matching its name. (e.g., The <code>color</code> control can fill <code>background.color</code>, <code>text.color</code>, etc.).

### 10.3 The Shared Component Library

- Fragments (like the InputBar) MUST be built as standalone modules with their own recipe-book.
- When a Module (like VibeChat) uses a Fragment, it imports it by reference in its recipe.
- This prevents code duplication and allows a single fix to update the InputBar everywhere it is used.

## Part 11 — The Assembly Line & Spec Quality

This section defines the lifecycle of a project and the standard for writing recipes.

### 11.1 The Assembly Line (The Pipeline)

Every build inside VibeCoder follows this exact sequence. Nothing skips a step.

1. <b>The Vibe:</b> The user starts with a prompt or a conversation in VibeChat.
2. <b>The Brief:</b> The AI refines the vibe into a structured document.
3. <b>The Decisions:</b> The architectural choices are made.
4. <b>The Spec:</b> The decisions are formalized into a Master Spec (the "how-to").
5. <b>The Roadmap:</b> The project is broken down into phases.
6. <b>The Task List:</b> The roadmap is broken into actionable dispatches.
7. <b>The Recipes:</b> The blueprints - <code>recipe.md</code>, <code>codex.md</code> and <code>rules.md</code> - are written.
8. <b>The Build:</b> The Operator (the orchestrating lane) delegates to the FCr engine (build/patch modes) using the configured models.

### 11.2 The Spec Quality Checklist (Pre-Recipe Gate)

Before a lane writes a recipe, the spec section must pass this meta-checklist. If the spec is vague, the recipe will be vague. If the recipe is vague, the code will be broken.

<b>Geometry:</b>

- [ ] Are the exact pixel dimensions or percentages defined?
- [ ] Is the <code>position</code> (fixed, absolute, relative) stated?
- [ ] Are the z-index layers and stacking contexts defined?
- [ ] Are the hover/active/disabled states explicitly described?
- [ ] If the surface paints a BACKGROUND, is the LEVEL named — Page, Section or Widget (Part 55)?
- [ ] If the background is Page-Level, does it state <code>pointer-events: none</code> (Part 55)?

<b>Structure:</b>

- [ ] Is the HTML/JSX tree defined using Semantic Classes?
- [ ] Are the shared fragments explicitly named and imported?
- [ ] Are the CSS tokens (e.g., <code>var(--fv-bg)</code>) mapped for every visual element?

<b>Behaviour:</b>

- [ ] Are the state transitions (C1-C7) defined?
- [ ] Are the API endpoints or FC node writes explicitly named?
- [ ] Is there a clear failure mode defined?

<b>Verification (Part 68):</b>

- [ ] If a test fails after a fix, is the failure CLASSIFIED — a real regression or a pre-existing contract — before anything is changed?
- [ ] If the contract changed, does the updated test carry a comment saying WHY?
- [ ] Is the fix in the CODE, with the test left alone? (A regression is repaired in the code, never in the test that noticed it.)
- [ ] If the check SELF-VERIFIES — it regenerates the artefact and compares it — is it left WITHOUT a hand-written negative control?

## Part 12 — The Theme & Styling Engine

### 12.1 The CSS Standard

- No hard-coded pixels for layout. Use %, vw, vh, dvh.
- No raw hex codes. Use <code>var(--fv-*)</code>.
- No inline styles.

### 12.2 The Three Tiers of Styling

1. Theme (Global CSS variables).
2. Skin (Component recipe CSS).
3. State (Codex C2 variants).

### 12.3 Theme Architecture

Themes are nodes in the FC Brain. Selecting a theme injects variables into :root.

### 12.4 The Icon Rule

- Emojis are forbidden as UI elements. All UI icons must be inline SVGs or icon-fonts.
- Icons must inherit color via <code>currentColor</code> or <code>var(--fv-icon-color)</code> so the active theme or skin can recolor them.

## Part 13 — The VibeChat & Agent Architecture

This section defines the interaction model for VibeChat, Threads, and Agents.

### 13.1 The Two Surfaces

The Right Rail has two distinct tabs:

- <b>The Thread Tab (VibeChat):</b> The conversation. Chronological bubbles. The "talker."
- <b>The Agent Tab (V1, V2, V3):</b> The job sheet. Cards showing status (Running, Done, Failed). The "worker."

### 13.2 The Tag Bundles & Threads

- <b>Tags:</b> Assigned dynamically by a background AI model (the "Librarian") as the conversation moves (e.g., <code>#hero</code>, <code>#mobile</code>).
- <b>Bundles:</b> A view of all messages sharing a single tag.
- <b>Threads:</b> A saved <i>combination</i> of tag bundles (e.g., <code>#hero</code> AND <code>#mobile</code>).
- A Thread is not a folder; it is a dynamic query. If an old message is re-tagged, it instantly appears in the Thread.

### 13.3 The Agent Pool & Sub-Turns

- Agents (V1, V2, V3) are a shared pool. Any thread can claim a free agent.
- VibeChat is the Orchestrator. V1 does not talk to V2 directly. V1 reports to VibeChat, and VibeChat delegates to V2.
- When VibeChat delegates a task, it creates a <b>sub-turn</b>. The Thread view shows the parent turn. The Agent view shows the child (sub) turns.

### 13.4 The Turn Record Schema

Every Turn node in the FC Brain carries the job state. The schema is:

- <code>kind</code>: 'turn'
- <code>agent</code>: 'v1'
- <code>thread</code>: 'daily-planner'
- <code>tags</code>: \['#hero', '#mobile'\]
- <code>git_branch</code>: 'feat/v1-hero'
- <code>commit_sha</code>: 'abc1234'
- <code>exit_code</code>: 0
- <code>status</code>: 'success' \| 'failed' \| 'running' \| 'waiting'
- <code>logs</code>: '...'

### 13.5 Implementation Status (read this before building)

The model above is the <b>target architecture</b>. Three of its elements are <b>specified but not yet implemented</b>, and a lane agent MUST NOT assume they exist:

- <b>The "Librarian" (13.2)</b> — no tagging model or background tag-assignment mechanism exists in the codebase today. The terms <code>Librarian</code> and <code>tag bundle</code> have zero occurrences in <code>src/</code>.
- <b>Sub-turns (13.3)</b> — no sub-turn concept exists in the codebase today.
- <b>The Turn node (13.4)</b> — no <code>Turn</code> node type exists today. The fields <code>kind: 'turn'</code>, <code>git_branch</code>, <code>commit_sha</code> and <code>exit_code</code> have zero occurrences in <code>src/</code>.

<b>What DOES exist today, and must not be broken by this section:</b>

- <b>V1 is the VibeChat seat.</b> <code>src/vcs/agents/rail-seats.js</code> seeds <code>{ identity: 'agent-v1', seat: 'V1', name: 'VibeChat' }</code>, with V2..V6 below it on the Rail. The orchestrator relationship in 13.3 is consistent with that seating.
- <b>Agents are already a shared, project-scoped pool.</b> <code>src/vcs/agents/AgentStore.ts</code> keys every agent by <code>scopedKey(projectId, id)</code>, and the Rail admits up to <code>MAX_AGENTS_IN_RAIL = 8</code>. Seats are a <i>seeding layer</i>, not exclusive ownership — so "any thread can claim a free agent" matches the current model.
- <b>VibeChat already stores threads of messages.</b> <code>src/host/editor/vibechat/types.ts</code> defines <code>VibeChatThread { threadId, title, messages, createdAt, updatedAt }</code> and <code>VibeChatMessage { messageId, role, text, timestamp, streaming? }</code>.
- <b>Agent status already has a vocabulary, and it is NOT the one in 13.4.</b> The real lifecycle states are <code>spawned</code>, <code>active</code>, <code>paused</code>, <code>completed</code>, <code>archived</code>, <code>retired</code>, with the transition map in <code>src/vcs/agents/config.ts</code> (<code>VALID_LIFECYCLE_TRANSITIONS</code>). There is no <code>success</code>, <code>failed</code>, <code>running</code> or <code>waiting</code> state in that map, and no <code>failed</code> state at all.<br /><b>Therefore:</b> the Turn record's <code>status</code> field in 13.4 is a <b>new</b> vocabulary for the Turn node specifically, and it MUST be mapped onto the agent lifecycle when the Turn node is implemented (e.g. <code>running</code> -> <code>active</code>, <code>success</code> -> <code>completed</code>, <code>failed</code> -> a new terminal failure state, <code>waiting</code> -> <code>paused</code>). A lane MUST NOT rename or replace the existing agent lifecycle states to match 13.4.

## Part 14 — Local-First Version Control

- Every VibeCoder project is a local Git repository.
- The agent pool (V1, V2, V3) commits, branches, and merges entirely locally.
- Deploys go directly to the host (Vercel, Netlify, FreshVibe Host).
- If the user wants cloud backup, they add a GitHub PAT to the Credential Store. The agent detects it and offers to sync.

## Part 15 — The Scaffolding & The Self-Contained Product

### 15.1 The Scaffolding (Development Phase)

- The external Mavis Fleet (id 9, id 44, the Panel, the external HQ) is temporary scaffolding.
- It exists only to build VibeCoder. It is not the final product.

### 15.2 The Self-Contained Product

- The production VibeCoder app runs 100% locally (Desktop App or isolated VPS).
- It bundles its own PocketBase/SQLite instance (the FC Brain) on <code>localhost</code>.
- It has an internal HQ (the Agent Rail, the Threads).
- It spawns internal agent processes (V1, V2, V3) locally.
- It requires zero central servers maintained by us.

## Part 16 — The Lane Handover Brief

### 16.1 The Assembly Line

Vibe → Brief → Decisions → Spec → Roadmap → Task List → Recipes → Build (FCr engine).

### 16.2 The Source of Truth

- The Master Spec (this document) is the Law.
- The Recipes (<code>recipe.md</code>, <code>codex.md</code>) live in the FC Brain, mirrored to Notion Quick Notes.
- The Code is just the compiled artifact. If the code is bad, the recipe was bad. If the recipe is bad, the spec was bad.

### 16.3 Current State (As of 2026-10-24)

- The Master Spec (v3.9.0) and FvW (9.13.0) are locked. The previously recorded 9.16.0 was a hallucination; the gallery <code>VERSION</code> file reads <code>9.13.0</code> and the doctrine CHANGELOG's latest entry is <code>v9.12.0</code>. No <code>9.15.0</code> or <code>9.16.0</code> exists anywhere in the gallery.
- The FC Brain and Notion Mirror for the Module Registry are live.
- The old UI code (Deck, Assets, VibeChat) has been audited and mapped.
- The next immediate goal: Write the recipes for <code>frag_input_bar</code>, <code>frag_thread_rail</code>, and <code>mod_vibechat</code>, then rebuild VibeChat from scratch using the configured models via the FCr engine.

## The Dual-Path Rule (Manual Equivalence)

Every action the AI performs must have a manual equivalent.<br />When the AI creates a new visual effect (e.g., a slide transition, a shadow, a texture), it must not hardcode the result. It must:

1. Create a new property in the widget's schema (e.g., <code>slideEffect: 'fade'</code>).
2. Assign a <code>#beta</code> tag to the control.
3. Render the control in the Properties panel.
4. Bind the control to the tree node.

The user can then adjust the AI's work manually. The AI builds the tool, and the tool is always available to the user. The app is alive.

## Part 17 — Geometry, Resizing, & Z-Index

### 17.1 Resizing and Dragging

- No corner handles or drag grips. Hovering near the edge changes the cursor to <code>col-resize</code> / <code>row-resize</code>.
- Floating panels are dragged by their headers. Dragging to the edge docks the panel. Dragging away breaks it free.
- Docked panels resize the canvas around them.

### 17.2 The Header & Z-Index

- Panels must NEVER slide under the top header. They are constrained to the <code>.fv-shell-body</code> container.
- The header is always on top.
- Clicking the canvas minimizes an open panel to a pill (does not destroy it).

### 17.3 Drag-and-Drop Interaction

- When a widget drag begins, the active panel closes to reveal the canvas.
- When the drop completes (or is cancelled), the panel reopens automatically.

### 17.4 The Cinema Workspace

- The Cinema Collection opens 7 specific panels into a Workspace Preset.
- They can be minimized to pills, but cannot be destroyed (no 'X' button in Cinema context).

### 17.5 The Peek Panel

- A lightweight generic panel on the right edge for inspecting card backs. On mobile, it is a slide-up sheet.

## Part 18 — Docked Panels & Fluid Layouts

### 18.1 Docked Panel Chrome

- When docked left or right, panels lose their floating window header. They retain a title bar without minimize/close buttons.
- Next to the title is a toggle: <b>Stretch</b> (pushes the canvas) vs <b>Cover</b> (overlays the canvas).

### 18.2 Fluid Resizing

- When a panel is resized, inner components (Input Bar, Message List) must use Flexbox/Grid to resize.
- If narrow, inner rails (like the Thread Rail) gracefully collapse into icon-only mode.

## Part 19 — VibeChat Auto-Behaviors & Input Bar

### 19.1 The Input Bar (Detent 1)

- Strict single row. Layout (L to R): <code>+</code> (Attach Image), text area, Mic (Whisper), Send.
- No minus or close buttons on the input bar itself. VibeChat is universally toggled via the Dock.

### 19.2 Auto-Expansion & Collapse

- Hitting Send auto-expands the Strip (Detent 2).
- The Strip auto-collapses on canvas click or idle (pauses if user hovers or scrolls).

### 19.3 Desktop Full Sheet (Detent 3)

- No visible drag handle. On hover near top edge, cursor changes to <code>ns-resize</code>.
- <code>+/-</code> detent controls are placed in the top-right corner.

### 19.4 Floating Panels & Window Controls

- All floating panels (and floating VibeChat) have a standard header with Minimize (<code>—</code>) and Close (<code>X</code>) on the top-right.
- Closing floating VibeChat with <code>X</code> does not destroy the chat; it collapses to a dedicated "Chat" handle on the edge.

## Part 20 — Mobile Sheets & The Switcher Menu

### 20.1 Mobile Sheet Controls

- The drag handle has a small <code>X</code> icon on its far right edge.
- <b>Minimize:</b> Swipe sheet down or tap canvas outside.
- <b>Close (Destroy):</b> Tap the <code>X</code> on the handle, or swipe the handle left/right.
- <b>Rotate:</b> Swiping left/right on the sheet body switches between active sheets.

### 20.2 The Panels Switcher Menu

- Clicking the bottom "Panels" pill opens a mini-sheet listing all active sheets in play.
- <b>Tap:</b> Opens the sheet.
- <b>Tap </b><b><code>X</code></b><b> / Swipe Left/Right:</b> Destroys the sheet.
- <b>Drag and Drop:</b> Reorders the list to customize the user's workspace.

## Part 21 — Reconciliation with Earlier Parts (read before implementing)

Parts 17-20 are a mega-patch that supersedes earlier fragmented drafts. Two of their statements<br />conflict with text that was already canonical, and one introduces a container that does not yet<br />exist. This section resolves each of them so a lane agent is never choosing between two rules.

### 21.1 "Pill" vs "Handle" (Parts 17.2 and 17.4)

Part 3.5 (v2.1.3) purged the word <b>pill</b> from the spec vocabulary and established <b>Handle</b> as<br />the term for a clickable/swipeable element on a Rail. Part 17 uses "pill" in two places.<br /><b>Resolution:</b> read "pill" in Parts 17.2 and 17.4 as <b>Handle</b>. The word "pill" survives on this<br />page only inside the real CSS class <code>.fvcms-dock-pill</code> and inside changelog history. A builder<br />MUST use the term <b>Handle</b> in new code and comments.

### 21.2 Close (<code>X</code>) vs Close (<code>✕</code>) and destroy semantics (Part 19.4)

Part 3.2 defines the floating panel header as Minimize (<code>—</code>), Center Title, Close (<code>✕</code>), where<br />Close <b>destroys</b> the panel (removes it from memory and the Panels menu), and Part 3.1 says a<br />panel closed via "X" is removed from the Handles. Part 19.4 says floating panels carry Close<br />(<code>X</code>) and that closing floating VibeChat with <code>X</code> does not destroy the chat.<br /><b>Resolution:</b> the glyph is unified as <b><code>✕</code></b> (the Part 3.2 glyph); Part 19.4's <code>X</code> is the same<br />control written in a different font. The <b>destroy</b> semantics of Part 3.2 stand for every panel<br />EXCEPT floating VibeChat, which is the one deliberate carve-out: closing floating VibeChat<br />collapses it to a dedicated "Chat" <b>Handle</b> on the edge and preserves the conversation. A<br />builder MUST NOT generalise the VibeChat carve-out to other panels.

### 21.3 <code>.fv-shell-body</code> does not exist yet

Part 17.2 constrains panels to the <code>.fv-shell-body</code> container. There is no <code>.fv-shell-body</code> in<br />the codebase today; the nearest existing patterns are <code>.fvcms-pm-body</code> and <code>.fvcms-edge-body</code>.<br /><b>Resolution:</b> <code>.fv-shell-body</code> is a NEW container that this spec introduces. A builder that<br />needs it either introduces it or maps it to the existing body container, and MUST record which<br />mapping it used.

### 21.4 Terms verified against the codebase

- <code>ns-resize</code> is real and in use (<code>src/cms/fvcms-panel-manager/fvcms-panel-manager.css</code>,<br /><code>src/cms/modules/system/panel-system/chrome/panel-chrome.css</code>).
- <code>col-resize</code> and <code>row-resize</code> ARE in the codebase (7 repo-wide hits: <code>src/cms/runtime/styles.css</code>, <code>src/cms/styles.css</code>, <code>src/host/dashboard/DashboardGrid.tsx</code>, <code>src/vcs/vcs-css.js</code>), but on column dividers and a transparent card gutter - not on panel edges. See Part 30.1 for the full audit. (Corrected in v3.4.0: an earlier reading of this line was scoped too narrowly to <code>src/host/dashboard/</code>.)
- <code>fv-input-bar</code> and <code>fv-agent-rail</code> do not exist yet; they are new module classes.
- Part 6 (mobile: "Panels dock to the bottom (sheet)") and Part 20.1 (mobile sheet handle) are<br />consistent. No conflict.

## Part 22 — Mission Control (The State of the Lane)

This section defines the single source of truth for the current state of the fleet.

### 22.1 The Mission Control Node

- Mission Control is a node in the FC Brain (mirrored to Notion) named <code>mission_control</code>.
- It is the <b>first</b> thing any new lane agent must read.

### 22.2 The Dashboard Fields

Mission Control must contain:

- <b>Spec Version:</b> The current Master Spec version (e.g., v3.1.0).
- <b>FvW Version:</b> The current FvW version (e.g., 9.17.0).
- <b>Active Build:</b> What is currently being executed right now (e.g., "FVC 1156 - Rebuilding Shell").
- <b>Latest Ledger:</b> The last 3 completed dispatches with their Verdicts.
- <b>Immediate Next Step:</b> What the operator or lane should do next.

### 22.3 The Update Protocol

- Every dispatch's final step (Phase C) is to update the Mission Control node with its new state.
- If a dispatch fails (STOP), it must update the "Active Build" field to reflect the failure.

## Part 23 — The Tri-Scope Dashboard

The Dashboard is the management surface. It must support three distinct data scopes, filtered by the active context (Global, Project, or App).

### 23.1 The Three Scopes

1. <b>Build Data (The Factory):</b> For the developer. Contains Turns, Agents, Telemetry, Deploy hashes, Roadmaps. (e.g., "Did the Oscar build pass?")
2. <b>App Data (The Products):</b> For the client. Contains CMS content (Posts, Products, Users, Media). (e.g., "Is Oscar's latest blog post published?")
3. <b>User Data (The Operator):</b> For the creator. Contains personal/business OS tools (Calendar, CRM, Notes, Planner, Billing). (e.g., "Do I have a call with the Oscar client on Friday?")

### 23.2 The Context Filter

The active context (Global vs. Project) dictates the filter for every widget.

- <b>Global Dashboard:</b> Sees all data. (All projects, all users, all notes).
- <b>Project Dashboard:</b> Filters the data to that specific project. (Oscar's build, Oscar's CMS, notes tagged <code>#oscar</code>).
- <b>App Dashboard:</b> Filters to the deployed app instance.

### 23.3 The Scope Toggle

The Dashboard must have a segmented control at the top: <code>[ Build Data ] [ App Data ] [ User Data ]</code>.<br />Switching the scope changes the widgets rendered on the grid without leaving the page.

## Part 24 — Reconciliation with the Dashboard Code (read before implementing)

Part 23 is a product specification. The Dashboard code that exists today implements a related<br />but <b>different</b> contract. This section records the difference so a builder does not implement<br />Part 23 literally and break a test that is currently passing.

### 24.1 The Dashboard code today

- <code>src/host/dashboard/DashboardCanvas.tsx</code> exports <code>filterCardsByProject(nodes, projectId)</code>.<br />It is pure and has <b>two</b> states, not three:
  - no <code>projectId</code> -> show ONLY nodes with no <code>projectId</code> (the "Home Dashboard").
  - a <code>projectId</code> -> show ONLY that project's nodes.
- <code>src/host/dashboard/dashboard-layout.ts</code> owns the grid arithmetic: 12 columns,<br /><code>MIN_CARD_WIDTH</code> 1, <code>MAX_CARD_WIDTH</code> 12, <code>DEFAULT_CARD_HEIGHT</code> 180, <code>MIN_CARD_HEIGHT</code> 40,<br />plus explicit <code>order</code> and <code>width</code> on each card so an arrangement survives a reload.
- <code>src/host/dashboard/DashboardGrid.tsx</code> adds drag-to-reorder and resize-to-span over that<br />arithmetic, hand-rolled (no dnd library in the repo).

### 24.2 "Global Dashboard: Sees all data" vs the Home Dashboard

Part 23.2 says the Global Dashboard "Sees all data. (All projects, all users, all notes)".<br />The code does the opposite, and says why in its own words: with no project selected it shows<br />ONLY unprojected nodes. The source records that the tempting alternative - home nodes are<br />always visible - was <b>rejected</b>, because it makes the Home Dashboard a permanent superset of<br />every project, so selecting a project could never narrow the surface.

<b>Resolution:</b> the code's rule stands. Part 23.2's "Global Dashboard" means the <b>Global<br />context</b> (the home scope, no project selected), NOT "a union of every project's data". A<br />builder MUST NOT widen the Home Dashboard to include other projects' cards. The parenthetical<br />"(All projects, all users, all notes)" describes the <b>breadth of the scope's own data</b><br />(turns, agents, CMS content, notes) and not a cross-project union.

### 24.3 The third state (App Dashboard) does not exist yet

Part 23.2 lists three contexts: Global, Project, App. The code has two. There is no app-instance<br />concept in the dashboard: <code>appId</code>, <code>appInstance</code>, <code>instanceId</code> and <code>slug</code> are all absent from<br /><code>src/host/dashboard/</code>. <code>DashboardCanvas</code> also documents that its <code>projectId</code> prop "stays<br />undefined and behaviour is unchanged" until the FVC 1049 Projects Panel ships.

<b>Resolution:</b> the App Dashboard is <b>NEW</b>. A builder implementing it MUST add the third<br />state explicitly and MUST keep <code>filterCardsByProject</code> behaviour intact for the two existing<br />states. The existing test <code>src/host/dashboard/__tests__/fvc1065-project-boundary.test.ts</code><br />(11 tests) is the guard: it asserts that with no project selected the result is ONLY home<br />nodes and that it EXCLUDES every project node.

### 24.4 Scope vocabulary is new

"Build Data", "App Data" and "User Data" do not appear anywhere in <code>src/</code>. The dashboard's<br />existing card vocabulary is <code>kind: 'widget'</code> / <code>kind: 'card'</code> with a <code>cardKind</code> filter, and<br />there is no segmented-control component in the repo (<code>SegmentedControl</code> has 0 hits).

<b>Resolution:</b> the three scopes, the scope toggle, and the widget-to-scope mapping are all<br /><b>new vocabulary</b>. Part 23.3's segmented control is a NEW UI component; a builder SHOULD<br />reuse an existing primitive if one is added before the build starts. A widget MUST declare<br />which scope it belongs to, because Part 23.3's "Switching the scope changes the widgets<br />rendered on the grid" requires a per-card scope field that does not exist yet.

### 24.5 Persistence caveat carried forward

<code>DashboardGrid.tsx</code> records that the graph write succeeds but <code>properties</code> does not survive<br />the wire, so the locally-saved layout is what actually keeps the arrangement. Any scope or<br />filter state stored the same way MUST be persisted locally too, or it will be lost on reload.

## Part 25 — The Validator Engine

- The FvW rules must be executable code in <code>src/validator/</code>, not just prose.
- <b>Zero-Module Failure:</b> If <code>modulesScanned === 0</code>, the validator exits with code 1.
- <b>Guidance Payload:</b> The validator outputs JSON with <code>rule</code>, <code>expected</code>, <code>actual</code>, and <code>guidance</code> so the AI can self-correct.

## Part 26 — The Bug & Feedback Database

- <b>The Nodes:</b> The FC Brain supports <code>kind: bug</code>, <code>kind: feature_request</code>, and <code>kind: pain_point</code>.
- <b>The Escalation Loop:</b> If the Executor fails validation 3 times, it MUST stop and log a <code>bug</code> node.
- <b>External Submission:</b> Users can submit bugs from the UI. The system scrubs proprietary data and logs the Trace Atlas and validator error.

### 26.1 The Trace Atlas Schema

The Trace Atlas schema description MUST explicitly include the dual-recipe state, so that a bug log can name both the intent and what was actually built:

<code>fc_brain_nodes: { recipe_suggested: "...", recipe_actual: "...", codex: "...", rules: "..." }</code>

This is a change from the previous schema, which carried only <code>codex</code> and <code>rules</code> and had no way to record the Suggested/Actual pair introduced in Part 35. The <code>recipe_suggested</code> and <code>recipe_actual</code> entries are the FC-Brain-level encoding of Part 35's dual-recipe state; the <code>kind: bug</code> node's payload MUST reference both so the Guardian Agent (Part 28) can run the Part 35.3 drift check against a logged bug.

## Part 27 — The Roadmap Scope

- The Dashboard Tri-Scope is expanded to: <code>[ Build Data ] [ App Data ] [ User Data ] [ Roadmap ]</code>.
- It aggregates <code>feature_request</code> nodes and shows their status: Accepted, In Development, Shipped, Not Adopted.

## Part 28 — The Guardian Agent (Self-Healing Protocol)

- The Guardian is an operator-level agent tasked with infrastructure maintenance.
- <b>Trigger:</b> It watches for <code>kind: bug</code> nodes logged by the Executor.
- <b>Diagnose & Heal:</b> It reads the bug report, fixes the implementation, and verifies the fix.
- <b>The Iron Rule:</b> The Guardian can fix <i>bugs</i> in the infrastructure, but it CANNOT alter the <i>rules</i> in the Master Spec or FvW doctrine.

## Part 29 — The Dev Panel & Feedback UI

The infrastructure (Validator, Guardian, Bug DB) is invisible to the average user. But it requires two UI surfaces:

### 29.1 The Dev Panel

- A dedicated module in the Deck.
- Shows: Master Spec version, FvW version, FC Brain node count, Validator status (Passing/Failing), recent Changelog, VC Self-Test results, and the Guardian Healing Log.

### 29.2 The Feedback Widget

- A widget in the Dashboard (User Data scope).
- Allows users to submit bugs (auto-capturing the Dev Panel state and scrubbing proprietary data) and feature requests.
- Shows a 'My Tickets' list with statuses (Fixed, Accepted, Not Adopted) and friendly explanations from the operator.

## Part 30 — Verification Notes for the Part 7 Checklist (v3.4.0)

Part 7 now carries 26 criteria: the 16 original plus 10 covering Parts 17-24. These notes record<br />what the codebase actually does today for the criteria that touch existing code, so a builder<br />knows what is already true and what is still to build. Where a criterion is <b>not yet</b> met,<br />that is stated plainly — an unchecked box means "not verified", not "must be broken".

### 30.1 Geometry - hover-cursor resize (checkbox 1)

<code>col-resize</code> and <code>row-resize</code> are <b>not new</b> to the codebase; Part 24.4's earlier note that<br />they were absent was scoped too narrowly to <code>src/host/dashboard/</code> and is corrected here. There<br />are <b>7</b> repo-wide hits:

- <code>src/cms/runtime/styles.css</code> and <code>src/cms/styles.css</code> define <code>.fvcms-col-handle</code>,<br /><code>.fvcms-column-resize-handle</code>, <code>.fvcms-col-split-handle</code> and <code>.fvcms-column-split-handle</code><br />with <code>cursor: col-resize</code> / <code>cursor: row-resize</code>. These are <b>CSS-only</b>: they have <b>zero</b><br />React or TypeScript consumers, so they are orphaned rules for column dividers, not panel<br />resize affordances.
- <code>src/host/dashboard/DashboardGrid.tsx</code> uses <code>cursor: 'col-resize'</code> inline on a <b>10px-wide<br />transparent gutter</b> on a card's right edge (it turns visible only while dragging). This is<br />already the Part 17.1 model: a hover cursor with <b>no visible handle</b>.
- <code>src/vcs/vcs-css.js</code> and <code>src/vcs/vcs-css</code> carry a <code>col-resize</code> rule.

<b>Resolution:</b> the criterion stands. A panel resize MUST be driven by a hover cursor with no<br />persistent visual grip. The existing orphaned <code>.fvcms-col-handle</code> rules are a <b>different</b><br />concern (editor column splits) and MUST NOT be read as permission to give panels a visible<br />handle.

### 30.2 Mission Control (checkbox 9)

<b>Already true.</b> The <code>mission_control</code> node exists in the FC Brain tree <code>vibecoder-self</code><br />(32 nodes, exactly 1 <code>mission_control</code>, verified by read-back after the FVC 1157 write). Its<br />fields are <code>specVersion</code>, <code>fvwVersion</code>, <code>activeBuild</code>, <code>latestLedger</code> and <code>immediateNextStep</code>.<br />A builder updating it MUST use the tree route <code>PUT /api/agent/tree/:treeId</code> with<br /><code>{"nodes":[...]}</code>; the node is top-level, so its <code>parentId</code> is <code>null</code> (read back as <code>""</code>).<br />The <code>fc-in-vc/brain</code> route is a <b>decoy</b> and holds no node graph.

### 30.3 Dashboard Scopes (checkbox 10)

Two parts, at different states:

- The <b>segmented control</b> <code>[Build Data] [App Data] [User Data]</code> is <b>not built</b>. There is no<br /><code>SegmentedControl</code> component in the repo, and "Build Data" / "App Data" / "User Data" appear<br />nowhere in <code>src/</code>. Part 24.4 stands: the toggle and the scope vocabulary are <b>new</b>.
- The <b>fvc1065 boundary</b> is <b>already implemented and tested</b>:<br /><code>filterCardsByProject</code> in <code>src/host/dashboard/DashboardCanvas.tsx</code>, guarded by<br /><code>src/host/dashboard/__tests__/fvc1065-project-boundary.test.ts</code> (11 tests), which asserts<br />that with no project selected the result is ONLY unprojected nodes and EXCLUDES every project<br />node. Per Part 24.2, "no cross-project bleed" means the Global scope shows the home scope,<br /><b>not</b> a union of every project's data.

### 30.4 Still unbuilt among the ten new criteria

The following have no implementation in the codebase today and are the point of the checklist:<br />the panel edge-hover resize model for <b>panels</b> (as distinct from the orphaned column CSS),<br />the <code>.fv-shell-body</code> constraint container, the docked <b>Stretch/Cover</b> toggle, the VibeChat<br />input-bar single-row and auto-expand/auto-collapse behaviours, the mobile sheet handle with<br />its <code>X</code> and destroy swipe, and the Panels <b>Switcher Menu</b> with drag-to-reorder.

## Part 31 — Notes for Parts 25-29 (v3.5.0)

Parts 25-29 are new subsystems. This section records two things a builder needs before<br />starting: how the numbering was settled, and what the codebase actually contains today.

### 31.1 The numbering

Parts 25-29 arrived in one dispatch, but <b>Part 25 was already taken</b> by "Verification Notes<br />for the Part 7 Checklist", which was a meta-section of the same class as Parts 21 and 24.<br />Rather than push the dispatch's five parts out of their dispatched numbers, the verification<br />notes were <b>renumbered to Part 30</b> (its four subsections became 30.1-30.4), and the cross<br />reference in Part 24.4 was updated to "See Part 30.1". All five dispatched parts keep their<br />dispatched numbers and titles.

### 31.2 What exists today (verified)

| Part | Claim | State in the codebase |
| --- | --- | --- |
| 25 | FvW rules are executable in <code>src/validator/</code> | <b>NOT BUILT.</b> There is no <code>src/validator/</code>. The only validator is <code>src/scaffold/validator.ts</code>, which checks scaffold output (appName, file shape, JSON parse) and is unrelated to FvW rule enforcement. |
| 25 | Zero-module failure: <code>modulesScanned === 0</code> exits 1 | <b>NOT BUILT.</b> <code>modulesScanned</code> has <b>0 hits</b> repo-wide. The gallery validator <code>vendor/fv-module-gallery/scripts/validate-buckets.mjs</code> scans <code>TREES = ['modules', 'cms-widgets']</code> and prints a <code>scanned</code> count, but exposes no such guard. The vacuous-pass defect this rule closes is still open. |
| 25 | Guidance payload: <code>rule</code>, <code>expected</code>, <code>actual</code>, <code>guidance</code> | <b>NOT BUILT.</b> No validator emits these fields. The <code>guidance</code> hits in <code>src/</code> belong to an unrelated "show-me" guidance system. |
| 26 | FC kinds <code>bug</code>, <code>feature_request</code>, <code>pain_point</code> | <b>NOT BUILT.</b> The live tree <code>vibecoder-self</code> holds 32 nodes with kinds <code>module</code> (8), <code>recipe</code> (8), <code>codex</code> (8), <code>rules</code> (7), <code>mission_control</code> (1). None of the three new kinds is present. |
| 26 | Scrubbing proprietary data before logging | <b>NOT BUILT.</b> No scrubber exists. The Trace Atlas that the rule references DOES exist, at <code>src/cms/accordion/trace-atlas/index.json</code>. |
| 27 | Tri-Scope expanded with a <code>[ Roadmap ]</code> scope | <b>NOT BUILT.</b> Per Part 24.4 the scope toggle itself is not built; no <code>Roadmap</code> scope exists. |
| 28 | The Guardian agent | <b>NOT BUILT.</b> No file in <code>src/</code> or <code>scripts/</code> mentions a Guardian. |
| 29 | Dev Panel as a Deck module | <b>NOT BUILT as a Deck module.</b> A "Dev Panel" does appear in the codebase, but it is a <b>different thing</b>: the credential-store panel (<code>src/host/fce-integration/credential-store-panel.tsx</code>) and the editor integration (<code>src/host/integration/r208-integration.ts</code>). A builder MUST NOT assume that surface already renders the fields Part 29.1 lists. |
| 29 | Feedback widget, "My Tickets" list | <b>NOT BUILT.</b> "My Tickets" has 0 hits; "Feedback" appears only in non-component files. |

### 31.3 The Iron Rule is the load-bearing rule

Part 28.4 says the Guardian can fix bugs but CANNOT alter the rules in the Master Spec or FvW<br />doctrine. That is the one line in Parts 25-29 that protects the others, because every other<br />part introduces machinery that could, if left unchecked, rewrite the specification it is<br />measured against. A builder MUST implement the Guardian so that a fix to the infrastructure<br />cannot produce an edit to a doctrine file.

## Part 32 — The Execution Protocol (Autonomy within Boundaries)

This section defines how <b>any agent</b> (whether a Mavis fleet agent building VibeCoder, or an internal VibeChat agent building a user's app) must behave when executing a task.

### 32.1 The Hierarchy of Truth

1. <b>The Goal:</b> Absolute. You must achieve the stated outcome (e.g., "Build the Shell").
2. <b>The Boundaries:</b> Absolute. You must not violate the Validator, CSS Tokens, or File Isolation rules.
3. <b>The Steps:</b> Advisory. The steps provided in a dispatch are a suggested path. If a step is mechanically flawed and will break the build or violate a boundary, the agent MUST pivot to a safe alternative.

### 32.2 The Pivot Protocol

- If a step will break the build (e.g., archiving a live dependency), do not execute it blindly.
- Find the safe alternative that achieves the Goal without violating the Boundaries.
- Document the deviation clearly in the final report.

### 32.3 The Escalation Protocol (The Blocker)

- If you pivot and still fail 3 times, STOP.
- Log a <code>bug</code> node in the FC Brain detailing the blocker.
- Do not hallucinate a workaround that violates the Boundaries.

## Part 33 — Notes for Part 32 (v3.6.0)

Part 32 defines how an agent behaves when a dispatch step is flawed. It is consistent with the<br />rest of the spec, and it operationalises two earlier parts rather than replacing them. This<br />section records the cross-references and the one limit on the pivot authority.

### 33.1 Part 32 operationalises Part 26, it does not replace it

Part 32.3 says to log a <code>bug</code> node after three failed pivots. Part 26 already defines the<br />Escalation Loop ("If the Executor fails validation 3 times, it MUST stop and log a <code>bug</code><br />node"), and Part 28 defines the Guardian that consumes those nodes. The three read together:<br />Part 26 is the <b>database</b>, Part 28 is the <b>responder</b>, Part 32 is the <b>agent's own<br />protocol</b>. A <code>bug</code> node is the shared artifact between them.

Note that <code>kind: bug</code> is <b>not implemented yet</b> — see Part 31.2. The live tree <code>vibecoder-self</code><br />holds 32 nodes with kinds <code>module</code> (8), <code>recipe</code> (8), <code>codex</code> (8), <code>rules</code> (7) and<br /><code>mission_control</code> (1). Until the kind exists, Part 32.3's escalation has no destination, and a<br />build agent must log the blocker in its final report instead of silently dropping it.

### 33.2 The Boundaries are real doctrine rules, not new terms

Part 32.1 names "the Validator, CSS Tokens, or File Isolation rules" as absolute. Neither<br />"CSS Tokens" nor "File Isolation" is defined in this document, so a builder must read them in<br />the FvW doctrine:

- <b>CSS Tokens</b> — <code>vendor/fv-module-gallery/gallery-pact/fvw/freshvibe-way-v8/00.12-world-class-ui-standard.md</code><br />(the Theme & Styling Engine that Part 12 of this spec mirrors).
- <b>File Isolation</b> — the four isolation classes (A/B/C/D) declared in<br /><code>02-folder-layout.md</code> §11, with <code>08-anti-drift.md</code> and <code>11-recipe-book.md</code> §11.10-§11.11<br />as the supporting rules.
- <b>The Validator</b> — the executable form of the FvW rules that Part 25 specifies but which is<br /><b>not built</b> (Part 31.2).

### 33.3 The Iron Rule bounds the pivot too

Part 32.1 makes the Goal absolute, and Part 32.2 authorises a pivot when a step is flawed. That<br />authority is <b>bounded by the Boundaries</b>, and it does not extend to the doctrine. Part 28.4's<br />Iron Rule says the Guardian can fix infrastructure bugs but CANNOT alter the rules in the Master<br />Spec or FvW doctrine. Read together: an agent may pivot around a broken step, but it may never<br />pivot around a rule by editing the rule. A deviation that requires changing a doctrine file or<br />this spec is <b>not</b> a permitted pivot — it is an escalation.

### 33.4 Documenting the deviation is mandatory, not optional

Part 32.2 requires the deviation to be documented in the final report. That is the only record<br />that a pivot happened. A report that silently presents a safe-alternative execution as if the<br />dispatched step had been executed as written is a false report, and it defeats the purpose of<br />making the steps advisory: if the deviation is invisible, the dispatch cannot be corrected.

## Part 34 — The HQ Routing & Mirroring Rule

This section defines how agents must publish reports to HQ to ensure no data is lost and no time is wasted trimming text.

### 34.1 The Endpoints

- <code>/api/mavis/bulletins</code> has a hard cap of <b>2,000 characters</b>.
- <code>/api/mavis/docs</code> supports much larger payloads (26KB+).

### 34.2 The Length Rule

- If the report body is > 1,800 characters:
  1. POST the full body to <code>/api/mavis/docs</code>.
  2. POST a bulletin containing ONLY the headline, the verdict, and a pointer to the doc ID.
- If the report body is \< 1,800 characters:
  1. POST the full body directly to <code>/api/mavis/bulletins</code>.

### 34.3 The Notion Mirroring Rule

- If a dispatch requires a full report to be created in Notion, the agent MUST also mirror that exact report text to <code>/api/mavis/docs</code>.
- The HQ must never rely solely on an external Notion URL. The HQ Doc is the permanent, durable record.

### 34.4 The Historic Backfill Protocol

- Historical reports exist only in Notion and are vulnerable to link rot or deletion.
- A background task must iterate through historical Notion report pages, verify if a corresponding <code>/api/mavis/docs</code> entry exists, and backfill any missing documents.
- This backfill must be idempotent (safe to run multiple times) and batched to avoid overwhelming the HQ server.

### 34.5 Efficiency

- Agents MUST NOT spend more than 1 retry trimming a report to fit the 2,000-character bulletin cap. If it doesn't fit, route it to a doc immediately.

## Part 35 — The Dual-Recipe State (Intent vs. Reality)

This section defines the two states of a recipe in the FC Brain, based on FvW §38 (Plan-as-Seed).

### 35.1 The Suggested Recipe (Intent)

- This is the "seed." It is the AI's initial plan for how to build a module, generated before any code is written.
- It is marked with <code>status: 'suggested'</code> in the FC Brain.

### 35.2 The Actual Recipe (Reality)

- This is the "harvest." It reflects exactly what was built on disk and passed the Validator.
- If the agent had to pivot (Part 32) because a step was broken, or if the Validator forced a structural change, the Actual Recipe records that reality.
- It is marked with <code>status: 'actual'</code> in the FC Brain.

### 35.3 The Drift Check

- The Guardian Agent (Part 28) uses this dual-state to diagnose bugs: it compares the <code>suggested</code> recipe against the <code>actual</code> recipe to see where the execution drifted.

## Part 36 — The Model Capability Matrix

- The spec must remain provider-agnostic. Do not hardcode "MiniMax" or "Groq."
- <b>The Roles:</b> <code>chat</code> (quick replies), <code>extract</code> (parsing data), <code>generate</code> (long writing), <code>review</code> (fact-checking), <code>build</code> (writing code), <code>patch</code> (fixing code).
- <b>The Matrix (Data):</b> The FC Brain holds a node list mapping which models (e.g., <code>gpt-4o</code>, <code>claude-3.5</code>, <code>m3</code>) are best for which role.
- <b>The Probe (Logic):</b> The FCr engine runs a suitability probe (e.g., sending a micro-task like "Return JSON") to drop unsuitable tiers before firing a real request.
- <b>The Split:</b> The VC Bridge does NOT build this. It consumes the Matrix from the FC Brain and the Probe from the FCr engine (via the FCC Face).

### 36.1 Existing Implementation (Measured 2026-10-24)

The Probe and the tiering already exist in the bridge, and this Part records their real shape rather than describing them as new:

- <b>The Probe Runner:</b> <code>model-probes.cjs</code> runs a behavioural probe suite against a model and returns a fingerprint. <code>model-fingerprints.cjs</code> defines the probes: <code>jsonStability</code>, <code>shortBlockStability</code>, <code>preambleBleed</code>, <code>planningBleed</code>, <code>truncationRate</code>, <code>loopTendency</code>, <code>fenceCorrectness</code>, <code>pathCorrectness</code>, <code>cdnTendency</code>, <code>latencyStability</code>. The <code>jsonStability</code> probe is exactly the "Return JSON" micro-task named above.
- <b>The Scoring:</b> <code>model-capability-score.cjs</code> turns a fingerprint into a weighted <code>capability_score</code> and a routing tier: <code>primary</code> (≥0.75), <code>single-block</code> (≥0.55), <code>fallback</code> (≥0.30), <code>exclude</code> (below).
- <b>The Contract:</b> <code>model-contract.cjs</code> maps a tier to its allowed capabilities, so an excluded tier cannot be used for content generation.
- <b>The Router:</b> <code>model-router.cjs</code> holds the model registry and resolves candidates per request.

### 36.2 The Two Gaps Between What Exists and What This Part Requires

- <b>The Six Roles Are Not Yet the Routing Vocabulary.</b> The shipped tiers are capability classes (<code>primary</code>, <code>single-block</code>, <code>fallback</code>, <code>exclude</code> with <code>content_generation</code>, <code>small_decisions</code>, <code>json_emission</code>, <code>single_block_output</code>). The six role names above (<code>chat</code>, <code>extract</code>, <code>generate</code>, <code>review</code>, <code>build</code>, <code>patch</code>) are a separate, finer axis. The Matrix MUST map roles onto tiers; the two vocabularies are not interchangeable.
- <b>The Matrix Does Not Exist Yet.</b> No role-to-model node list is held in the FC Brain. The live tree <code>vibecoder-self</code> (32 nodes) carries no such node.

## Part 37 — The Revibe (Patch) Contract

- VC consumes base faces from the FCr library (e.g., the FCC Settings page).
- We do NOT duplicate the UI.
- <b>The Manifest:</b> VC writes a <code>revibe/manifest.json</code> targeting Trace Atlas IDs (e.g., hiding a billing tab, overriding CSS tokens).
- <b>Build-Time Only:</b> Revibe applies the patches during the VC build step (before Vite bundles). It does not run at runtime. The output is a static, self-contained bundle.
- <b>Verification:</b> If <code>revibe.verify()</code> fails the Validator, the build STOPS.

### 37.1 Current State (Measured 2026-10-24)

- <b>No </b><b><code>revibe/</code></b><b> directory exists</b> in the VibeCoder tree, and no <code>revibe.verify()</code> function is defined anywhere in <code>src/</code> or the bridge. This Part is a contract to be built, not a description of shipped behaviour.
- <b>The Validator to gate on exists:</b> the gallery validator at <code>vendor/fv-module-gallery/scripts/validate-buckets.mjs</code> scans the trees <code>TREES = ['modules', 'cms-widgets']</code> and reports a <code>scanned</code> count of <code>module-meta.json</code> files. Its output is the natural input to <code>revibe.verify()</code>. Note that a scan of zero modules must NOT count as a pass; the zero-module vacuous-pass guard is still unbuilt (Part 25).
- <b>The Trace Atlas targets exist:</b> <code>src/cms/accordion/trace-atlas/index.json</code> is a canonical <code>freshvibe-way-v8.trace-atlas</code> document with a <code>component_hierarchy</code> and <code>events_emitted</code>. A manifest targeting Trace Atlas IDs is therefore addressable against the real schema.

## Part 38 — Acknowledged Infrastructure Gaps

- <b>The Backend Routes:</b> 197 route registrations (188 unique paths) in <code>server.cjs</code> (CMS, workers, deploy, VSIL) are live but currently undocumented. 180 of the 188 are under <code>/api/agent</code>. Future dispatches must document them.
- <b>The Missing Widgets:</b> <code>counter</code>, <code>link</code>, <code>list</code>, <code>rating</code>, <code>section</code> exist in the index but are missing from the physical widget trees.
- <b>The Code Debt:</b> There are 2,464 raw hex codes (378 distinct) and 689 inline styles in the current codebase. The Validator will catch these as modules are rebuilt.

### 38.1 Measurement Notes (2026-10-24)

The counts above were measured against the VibeCoder repo at <code>origin/main</code> (<code>11dcbf5</code>), not taken from the Logic Audit summary, because the summary's figures did not reproduce:

| Claim | Audit's number | Measured | How measured |
| --- | --- | --- | --- |
| Routes in <code>server.cjs</code> | 117 | <b>197 registrations / 188 unique paths</b> | \`app |
| Missing widgets | <code>counter</code>, <code>link</code>, <code>list</code>, <code>rating</code>, <code>section</code> | <b>confirmed exactly</b> | in <code>src/cms/data/cms-widgets-index.json</code> (44 entries) but no directory under <code>cms-widgets/</code>; all 5 do exist in <code>vendor/fv-module-gallery/cms-widgets/</code> |
| Raw hex codes | 881 | <b>2,464 (378 distinct)</b> | <code>#[0-9a-fA-F]{6}</code> over git-tracked <code>src/</code> |
| Inline styles | 613 | <b>689</b> | <code>style={{</code> over git-tracked <code>src/</code> |

Three physical widgets are the inverse case — present on disk but absent from the index: <code>menu</code>, <code>theme-presets</code>, <code>tools</code>. The index is therefore not a clean subset of the tree, and the 5-widget gap is not the only drift.

### 38.2 Provider-Agnostic Status of This Section

Part 36 requires the spec to stay provider-agnostic. The "The Code Debt" bullet is retained as an operator-facing acknowledgement rather than a rule, because it describes a count that changes on every commit and would need re-verification to stay true.

## Part 39 — Reconciliation Notes for v3.9.0 (Grand Reconciliation)

This Part records every place where the v3.9.0 reconciliation changed what the dispatch asked for, and why. Each entry is backed by a measurement against the VibeCoder repo at <code>origin/main</code> (<code>11dcbf5</code>) or the gallery at the same ref.

### 39.1 The FvW Version Was Wrong in Three Places, Not Two

The dispatch directed that <code>9.16.0</code> be replaced with <code>9.15.0</code> in "Section 9.4 and Part 16.3", on the premise that <code>9.15.0</code> is "the real highest version found in the gallery". Measurement contradicts all of that:

- <b><code>9.15.0</code></b><b> does not exist in the gallery.</b> A full-tree scan of <code>vendor/fv-module-gallery/</code> for <code>9.15.0</code> returns <b>0 files</b>. So does <code>9.16.0</code>. So does <code>9.14.0</code>. The only 9.x versions present above 9.9.9 are <code>9.12.0</code> and <code>9.13.0</code>.
- <b>The authoritative version is </b><b><code>9.17.0</code></b><b>.</b> The gallery's <code>gallery-pact/fvw/freshvibe-way-v8/VERSION</code> file reads <code>9.17.0</code>. The doctrine CHANGELOG's most recent entry is <code>v9.17.0</code>.
- <b>Section 9.4 never contained </b><b><code>9.16.0</code></b><b>.</b> It read: "The vendored doctrine (<code>9.13.0</code>) is stale. The fleet adopts <code>9.14.0</code> from the gallery <code>origin/main</code>." The hallucination there was <code>9.14.0</code>, not <code>9.16.0</code>.

The reconciliation therefore set the true version <b><code>9.13.0</code></b> in all three places where a version was asserted (Section 9.4, Part 16.3, and the Part 25 Mission Control field example), and did not write <code>9.15.0</code> anywhere. Writing <code>9.15.0</code> would have replaced one fabricated version with another.

### 39.2 Part 26 Had No Trace Atlas Schema to Update

The dispatch directed that the "Trace Atlas schema description" in Part 26 be updated to include the dual-recipe state. Part 26 is <b>"The Bug & Feedback Database"</b> and contains three bullets — kinds, escalation loop, external submission. It has no schema block. The string <code>fc_brain_nodes</code> appears <b>0 times</b> in the entire Master Spec.

Rather than leave the instruction unsatisfied or invent a schema to edit, this reconciliation <b>added Part 26.1 — The Trace Atlas Schema</b>, which states the dispatched schema shape verbatim and records that it is new rather than an edit. This is the Part 35 dual-recipe state expressed at Trace Atlas level: a bug log must reference both the Suggested and the Actual recipe so the Part 35.3 drift check can run against it.

### 39.3 The Logic Audit Numbers Did Not Reproduce

Part 38 acknowledges three audit findings. The <b>missing-widgets finding reproduced exactly</b> — <code>counter</code>, <code>link</code>, <code>list</code>, <code>rating</code>, <code>section</code> are in <code>src/cms/data/cms-widgets-index.json</code> and have no directory under <code>cms-widgets/</code>. The other two did not:

- <b>Routes:</b> the audit said 117; the live <code>server.cjs</code> registers <b>197 route handlers over 188 unique paths</b>. Part 38 records the measured figure, because a gap list that understates its own scope by 40% is not usable as a work backlog.
- <b>Code debt:</b> the audit said 881 raw hex codes and 613 inline styles; measurement over git-tracked <code>src/</code> gives <b>2,464 hex codes (378 distinct)</b> and <b>689 inline styles</b>. The hex count is roughly 2.8x the audited figure.

Part 38.1 records the measurement method for each number so a later dispatch can re-derive or challenge it. It also records the inverse drift the audit did not mention: <code>menu</code>, <code>theme-presets</code>, and <code>tools</code> exist on disk but are absent from the index.

### 39.4 The Pipeline Provider Mentions

Part 11.1, Part 16.1, and Part 16.3 each named a specific provider in an execution step. All three were rewritten to name the FCr engine and the configured models instead, per the dispatch and Part 36's provider-agnostic requirement.

One <code>MiniMax-M3</code> mention was <b>deliberately left in place</b>: it sits inside a trailing <code><page></code> cross-reference footer recording what FVC 1156 actually did on 2026-10-24. That is a historical record of a past event, not a pipeline instruction, and rewriting it would falsify the record. A dispatch may change what the spec <i>requires</i>; it may not retroactively change what <i>happened</i>.

### 39.5 Parts 36 and 37 Are Contracts for Unbuilt Capability

Parts 36 and 37 were appended as dispatched, verbatim. Neither describes shipped behaviour:

- Part 36's Probe exists in the bridge (<code>model-probes.cjs</code>, <code>model-fingerprints.cjs</code>, <code>model-capability-score.cjs</code>, <code>model-contract.cjs</code>, <code>model-router.cjs</code>) and is real — but the <b>six role names are not the shipped routing vocabulary</b> (the shipped vocabulary is tier-based: <code>primary</code> / <code>single-block</code> / <code>fallback</code> / <code>exclude</code>), and the <b>role-to-model Matrix does not exist in the FC Brain</b>. Part 36.1 and 36.2 record both facts.
- Part 37's <code>revibe/</code> directory, <code>revibe/manifest.json</code>, and <code>revibe.verify()</code> <b>do not exist</b>. Part 37.1 records that, and names the validator that should gate the build (<code>vendor/fv-module-gallery/scripts/validate-buckets.mjs</code>, <code>TREES = ['modules', 'cms-widgets']</code>), together with the standing warning that a zero-module scan must not count as a pass.

### 39.6 What This Reconciliation Did Not Do

- It did <b>not</b> soften the acknowledged gaps. Parts 36–38 are written as requirements, not aspirations.
- It did <b>not</b> add a Trace Atlas schema to any other Part. Part 26.1 is the only place the schema is specified, so there is exactly one source of truth for it.
- It did <b>not</b> change any Part number, heading, or ordering. Parts 1–35 are untouched in structure; Parts 36, 37, 38, 39 are appended in order.
- It did <b>not</b> assert a <code>9.14.0</code>, <code>9.15.0</code>, or <code>9.16.0</code> doctrine version anywhere. The spec now names one version, <code>9.17.0</code>, and it is the version the gallery actually ships.

CORRECTED (FVC 1447, read-only audit of the FVW pact): the FVW's live version is 9.17.0, read directly from gallery-pact/fvw/freshvibe-way-v8/VERSION, with the CHANGELOG in agreement. Every occurrence of 9.16.0 in this spec is now corrected to 9.17.0. The FVW is internally inconsistent about its own version — its README header, folder tree, structure heading and parent index each name a different, older version — and this correction follows the VERSION file, which is the authoritative one. Rule 7 §HOW TO CHECK THE VERSION already states that rule: read the file, do not trust a version written in a dispatch or a Notion page.

## Part 40 — The FCC Export Contract

This section records the architectural decisions made during FVC 1170 regarding the FCC Faces (Credential Store, Live Model Catalog) and the Revibe mechanism.

### 40.1 The Export Mandate

- VibeCoder must NOT copy or duplicate FCC faces. It must consume them as primitives.
- The FCr library MUST export its Settings faces (<code>CredentialField</code>, <code>PipelineFaces</code>, <code>ModelCatalog</code>) from its public <code>./ui</code> entry point.
- Until FCr exports these faces, VC will maintain a minimal VC-native write form that writes to the FC Brain (no duplication of the full FCC UI, just the data write).

### 40.2 The Revibe Runtime

- Revibe (FvW §18 <code>patch</code>) is currently doctrine-only with zero implementation in VC.
- Before VC can patch FCC faces to hide billing tabs or change colors, the FCr engine must implement the Revibe runtime (<code>revibe.apply()</code>, <code>revibe.verify()</code>).
- Until the runtime exists, VC must consume the FCC Face as-is (or not at all).

### 40.3 Measured State of the FCr Export Surface (2026-10-24)

The export mandate in 40.1 is not a hypothetical. The published FCr library does not export these faces today.

- <b>Package measured:</b> <code>freshcards</code> v2.21.2, resolved as a dependency of <code>vibecoder-standalone</code> (<code>package.json</code> dependency <code>freshcards</code>).
- <b>Public entry points (the package </b><b><code>exports</code></b><b> map):</b> <code>.</code>, <code>./core</code>, <code>./ui</code>, <code>./mantine</code>, <code>./credentials</code>, <code>./crypto</code>, <code>./adapter</code>, <code>./query</code>, <code>./package.json</code> — 9 entries.
- <b>The </b><b><code>./ui</code></b><b> entry exports 97 names</b>, among them <code>OverlayPicker</code>, <code>SurfaceRenderer</code>, <code>FreshCardsProvider</code>, <code>RichTextEditor</code>, <code>CommandPalette</code>, <code>useDockPin</code>, <code>useVibePanel</code> and the view/layout renderers. It does <b>not</b> export <code>CredentialField</code>, <code>PipelineFaces</code>, or <code>ModelCatalog</code>.
- <b>Zero occurrences in the whole published package:</b> <code>CredentialField</code>, <code>PipelineFaces</code>, and <code>ModelCatalog</code> appear <b>nowhere</b> in <code>dist/</code>, and <b>nowhere</b> in the shipped <code>src/</code>. The only file under <code>src/ui/components/settings/</code> is <code>OverlayPicker.tsx</code>.
- <b>Zero occurrences in VibeCoder:</b> none of the three faces appear anywhere in VC's <code>src/</code>, <code>app-modules/</code>, <code>ui-schema/</code>, or <code>bridge/</code>. VC already imports FCr primitives through public subpaths — <code>freshcards/mantine</code>, <code>freshcards/credentials</code>, <code>freshcards/core</code> — so the import path already exists; only the face exports are missing.

⇒ <b>THE EXPORT MANDATE IS ACHIEVABLE THROUGH THE EXISTING SUBPATH MECHANISM.</b> VC already consumes FCr via <code>freshcards/<subpath></code>. The gap is not a packaging problem; it is that FCr has not authored or exported the Settings faces yet.

### 40.4 Measured State of Revibe in VibeCoder

- <b>Zero implementation.</b> No <code>revibe/</code> directory exists in the VibeCoder tree, and <code>revibe.apply()</code> / <code>revibe.verify()</code> are defined nowhere in <code>src/</code> or <code>bridge/</code>. A repo-wide scan for the token <code>revibe</code> across <code>src/</code> and <code>bridge/</code> returns <b>0 files</b>.
- <b>This supersedes Part 37.1's statement that no </b><b><code>revibe/</code></b><b> directory exists</b> — both records agree; Part 37.1 is confirmed by this measurement.

### 40.5 A Doctrine Precision Note: FvW §18 Is the Revibe Pattern, Not a "patch" Mode

The phrase "FvW §18 <code>patch</code>" in 40.2 needs one correction for accuracy, because a reader will otherwise go looking for a patch mode in §18 and not find it.

- <b>FvW §18 exists and is the right section.</b> <code>gallery-pact/fvw/freshvibe-way-v8/18-revibe-pattern.md</code> is "The Revibe Pattern" — how an app re-uses and customises an external module without forking it. It defines the <code>revibe/</code> folder convention and the structural (not runtime) nature of a revibe.
- <b>But the word "patch" does not appear in §18 at all</b> (0 occurrences), and no file in the FvW doctrine pairs "revibe" with "patch" as a mode (0 co-occurrences across the doctrine).
- <b>What </b><i><b>is</b></i><b> real is a </b><b><code>build</code></b><b> / </b><b><code>patch</code></b><b> mode pair — in the VC bridge, not in the Revibe doctrine.</b> <code>bridge/lib/chat-handler.cjs</code> resolves <code>systemPromptMode</code> to <code>'build' | 'patch' | 'chat'</code>, and <code>system-prompt-patch.txt</code> is the VibeChat patch-mode prompt. These are chat-handler prompt modes for <i>how a model responds</i>, and they are the same modes Part 36 names for the FCr engine.

⇒ <b>DO NOT CONFLATE TWO DIFFERENT THINGS.</b> The Revibe Pattern (§18, structural: which parts of an external module an app re-uses, and how it re-themes them) and the <code>patch</code> prompt mode (bridge: a model's mode of responding) are separate concepts that happen to share a word. Part 40's substance is unaffected: the Revibe <i>runtime</i> — <code>revibe.apply()</code> and <code>revibe.verify()</code> — still does not exist in VC, and the FCr engine still has to implement it before VC can patch an FCC face. Only the citation is tightened.

### 40.6 What VC May Do Today (Decision Summary)

| Capability | Status | Evidence |
| --- | --- | --- |
| Import FCr primitives by public subpath | <b>WORKS</b> | <code>freshcards/mantine</code>, <code>freshcards/credentials</code>, <code>freshcards/core</code> imported across <code>src/</code> |
| Import <code>CredentialField</code> / <code>PipelineFaces</code> / <code>ModelCatalog</code> | <b>BLOCKED</b> | not exported by <code>./ui</code> (97 exports, none of these); absent from the whole package |
| Write VC-native data to the FC Brain | <b>PERMITTED</b> | 40.1's minimal write form; no UI duplication |
| Copy an FCC face into VC | <b>FORBIDDEN</b> | 40.1 export mandate |
| Patch an FCC face via Revibe | <b>BLOCKED</b> | no <code>revibe/</code> dir, no <code>revibe.apply()</code> / <code>revibe.verify()</code>; 0 files in <code>src/</code>  • <code>bridge/</code> |
| Consume an FCC face as-is | <b>PERMITTED</b> | 40.2's fallback |

<page url="https://app.notion.com/p/402fc18cb7ce81e38ef0d33866834adf">
FVC 1117 (round 4) — World-class Rail, thread pearl, canvas dismissal, 50dvh mobile sheet. DEPLOYED, 106/106 live click tests.
</page>

<page url="https://app.notion.com/p/402fc18cb7ce81fb82c2de2c6aa63792">
FVC 1117 — Round 6: the handles, the gap, the chevron, the side panel
</page>

<page url="https://app.notion.com/p/402fc18cb7ce8174be38e5e339073dc3">
FVC 1121 — Recipe & Codex extraction: NO\_RECIPES\_FOUND for the UI modules
</page>

<page url="https://app.notion.com/p/402fc18cb7ce81dba82ef3c061f1e436">
FVC 1121 — Recipe & Codex extraction + Asset Panel interaction (TABS)
</page>

<page url="https://app.notion.com/p/402fc18cb7ce81f3bb92cf0770c06076">
FVC 1128 — The 75 app-modules: list, origin (50 gallery-original / 25 gallery-mirror), and widget overlap (39 live, 0 code duplicates)
</page>

<page url="https://app.notion.com/p/402fc18cb7ce814b82ffcfce591c3717">
FVC 1131 — VibeChat is ORPHANED: no module.json, no recipe, no codex — but 5 module-map entries, 4 surfaces, 8 behaviours and a dangling module id
</page>

<page url="https://app.notion.com/p/403fc18cb7ce81f8a449c993496ac23b">
FVC 1142 - VibeChat structure audit: 68 files, TWO input bars (one retired), settings ABSENT, and the real component tree
</page>

<page url="https://app.notion.com/p/403fc18cb7ce81e9b704c1a5823bf464">
FVC 1149 - UI Chrome audit vs Master Spec v2.5.0 + FvW v9.16.0: PM2 partial, HEADER broken, RAILS broken, 17 chrome orphans
</page>

<page url="https://app.notion.com/p/403fc18cb7ce81958fdccfaf99725ebd">
FVC 1154 - Shell Recipe addendum applied: Bottom Rail + 4 Handles now in the blueprint (FC Brain) and in the Shell codex C1
</page>

<page url="https://app.notion.com/p/403fc18cb7ce81eb94a7e87ad7837ef8">
FVC 1156 - Safe UI Rebuild: legacy chrome archived (committed), Shell + VibeChat generated from the FC Brain with MiniMax-M3, mounted behind ?shell=v2. Production default unchanged.
</page>

<page url="https://app.notion.com/p/404fc18cb7ce81b2aefce3c4566f8b7c">
FVC 1172 — The v2 Shell is the production default
</page>

<page url="https://app.notion.com/p/404fc18cb7ce8127ab6be19812ed222c">
F 478 — every face and the theme are open
</page>

## Part 41: The Stencil

1. The Stencil is a visual-only canvas for AI to show UI mockups to the operator before they are wired to the backend.
2. A Stencil has no database connection, no FC Brain writes, and no real data. It renders from a mock adapter.
3. The Stencil is accessed via a button in the v2 Shell Header. The button only appears when an agent has generated a Stencil component.
4. When the operator approves the Stencil, the agent promotes it to the Live Canvas by swapping the mock adapter for the real FC Brain adapter.
5. The Stencil is a visual-only SANDBOX. It renders the Candidate Recipe with a Mock Adapter. It has no database connection and cannot write to the FC Brain. It is the workbench of the Vibe Loop: the operator views the Candidate and either approves or rejects it.
6. The Stencil must be built from the CURRENT RECIPE (Part 35, the Actual Recipe). When the Candidate and the Actual differ, the Stencil shows the PROPOSED DIFF rather than silently presenting one side as the whole truth.
7. The Stencil's isolation is STRUCTURAL, not merely asserted. The Stencil page is a separate build entry, so the legacy host, the workspace, the PM2 panels and the v2 Shell never boot on it. "No backend" is a property of the build graph, not a promise in a comment.

## Part 42: The Trace Atlas

1. The Trace Atlas maps every piece of code to a NODE. A Node has a unique ID (e.g. <code>header.menu_button</code>) and maps to a specific file and line.
2. The Recipe references NODES, not raw code. The Codex enforces rules on Nodes.
3. The Diff Engine operates on NODES. When a change is made in the Stencil, the AI generates a Diff against the Trace Atlas. It does not rewrite the entire file.
4. THIS PART EXTENDS, AND DOES NOT REPLACE, THE FvW TRACE ATLAS. FvW §04 defines the module-level Trace Atlas as a five-level chain — UI surface to behaviour to module to file to test — held in <code>app-trace-atlas/atlas.json</code>, with the module-level lineage form in each recipe-book's <code>trace-atlas/atlas.json</code>. The Node layer is the node-level refinement of the FILE and TEST levels: a Node is the addressable unit inside a file that a Recipe, a Codex rule, and a Diff can all name. The two levels compose; the module-level Atlas is the container, the Node is its finest addressable entry.
5. A NODE MUST BE RESOLVABLE. An ID that names no file, and no line in that file, is not a Node. The Atlas is the proof that every Node resolves, and a protection test traverses the Atlas to prove it.
6. THE TRACE ATLAS IS THE DIFFERENCE ENGINE'S INPUT. Because the Diff operates on Nodes, a change to one Node produces a diff of that Node, and the surrounding file is untouched. A diff engine that rewrites a whole file cannot be checked against the Atlas, and cannot be reviewed by the operator as a change to a thing they can name.

## Part 43: The Approval Gate

1. When the operator approves a Stencil, the Candidate Recipe becomes the Current Recipe.
2. The Live Canvas rebuilds from the Current Recipe.
3. The system MUST run a code diff between the approved Stencil and the newly generated Live Canvas.
4. If they differ, the deployment HALTS. The AI must rework the code until they match. The operator's approval is a binding contract.
5. THE GATE IS NOT A PROMOTION; IT IS A VERIFICATION. Approving a Stencil does not make the Candidate the Current Recipe unconditionally — it makes the Candidate the PROPOSED Current Recipe, and the gate is the diff in item 3 that decides whether it may become the Current Recipe. The promotion completes only when the diff is empty.
6. A HALT IS A SUCCESS, NOT A FAILURE. When the diff is non-empty the deployment stops and says what differs. A gate that lets a non-matching build through to satisfy a schedule has stopped being a gate, and the operator's approval stops being a contract.
7. THE DIFF MUST BE OVER NODES (Part 42), so the halt can name the Nodes that differ. A whole-file diff reports that "two files differ", which does not tell the operator or the AI what to rework.

## Part 44: Header Restoration

1. The v2 Header must include the full feature set extracted from the legacy PM2 header: Home icon, Preview, Deck, Settings, Theme, and Build number.
2. The Build number is clickable and copies the hash.
3. These features must be wired to Nodes in the Trace Atlas, not hardcoded.
4. THE HEADER'S FEATURE SET IS CARRIED BY THE RECIPE, NOT BY THE COMPONENT. The Header recipe is the declaration of the header's structure; a control that exists in the component but not in the recipe is a control the next regeneration will lose. The Stencil (Part 41) renders from the recipe, so the Stencil is where an incomplete feature set is visible before the Live Canvas is rebuilt.
5. A CLICKABLE BUILD NUMBER COPIES THE HASH, NOT A LABEL. The control copies the bare hash; a label that merely says "build" is a stamp and not a control. The copy is the feature — the stamp is incidental.
6. EVERY CONTROL IS A NODE. Each of the header's controls is a Node (Part 42) with its own ID, and the Trace Atlas carries the mapping. "Not hardcoded" means the control's identity, its target and its rule all resolve through the Atlas, so a Diff against it can say which control changed.

## Part 45: The Validator Gate

1. The AI's role is to write the Recipe (JSON) and the Codex (Schema). It does not write React code.
2. Before the Generator can compile the Recipe into React, the Recipe MUST be validated against the Codex Schema.
3. If the Recipe is missing required fields, properties, or violates any Codex rule, the Validator MUST reject it.
4. On rejection, the AI must be given the exact error message and forced to fix the JSON before retrying. The Validator guarantees the AI is deterministic and world-class.
5. A Recipe that fails validation cannot be rendered in the Stencil or promoted to the Live Canvas.
6. THE GATE IS THE FvW VALIDATOR, AND IT IS ALREADY EXECUTABLE CODE. The rules live in <code>src/modules/validator/src/validator-engine.js</code> with ten rule modules in <code>src/modules/validator/src/rules/</code> (<code>pact-structure</code>, <code>canonical-home</code>, <code>inheritance</code>, <code>lineage</code>, <code>fragment-collisions</code>, <code>codex-structure</code>, <code>vsil-structure</code>, <code>core-invariants</code>, <code>module-code-path</code>, <code>module-registry-generated</code>). This Part does not create a validator; it makes the existing one a GATE on the generation path.

⇒ ⇒⇒ **MEASURED (FVC 1273, against <code>origin/main</code> <code>66cd3f8b</code>): the path and the rule count in the previous text were BOTH wrong, and are corrected in place here.** The engine is at <code>src/modules/validator/src/validator-engine.js</code>; the path <code>fvw/validator-engine.js</code> named by the previous text does not exist anywhere in the tree. The engine's <code>RULES</code> array loads TEN modules; the previous text listed eight and omitted <code>module-code-path</code> and <code>module-registry-generated</code> — the two rules added by FVC 1219 and FVC 1239, and the two that between them catch a module that is wrapped but invisible and a registry that has drifted from its generator. ⇒ Omitting those two rules would have understated the gate: the previous text described a weaker gate than the one that exists.

⇒ ⇒⇒⇒ **⇒⇒⇒⇒ AND THE ONE RULE THAT GOVERNS A RECIPE-BOOK'S SHAPE IS CURRENTLY VACUOUS, WHICH THIS ITEM MUST NOT LEAVE UNSTATED.** The rule <code>codex-structure.js</code> is the one that governs a recipe-book's contents. It finds modules by <code>recipe.md</code> (line 23), requires <code>codex.md</code> and <code>rules.md</code> (lines 27-28), and reads the Recipe's A/B/C <b>markdown</b> sections (line 32). ⇒ ⇒⇒⇒⇒⇒ **⇒⇒⇒⇒⇒⇒ BUT IT SCANS <code>pact/&lt;scope&gt;/&lt;module&gt;/</code>, AND <code>pact/</code> IN THIS REPOSITORY CONTAINS ONLY FILES — <code>vc-master-spec.md</code>, <code>vc-working-notes-10.md</code>, <code>host-map.md</code> and eleven siblings — WITH NO MODULE DIRECTORIES AT ALL.** ⇒ ⇒⇒⇒⇒⇒⇒ **⇒⇒⇒⇒⇒⇒⇒ SO THE RULE DISCOVERS ZERO MODULES AND PASSES VACUOUSLY.** It is not a gate on the recipe-book; it is a gate on a directory shape that does not exist. ⇒ ⇒⇒⇒⇒⇒⇒⇒ **⇒⇒⇒⇒⇒⇒⇒⇒⇒ THIS IS THE CONTRADICTION ITEM 7 AND Part 54 ITEM 4 RESOLVE, AND IT IS NOT COSMETIC: THE GENERATOR AND THE VALIDATOR READ DIFFERENT FORMATS OF THE SAME RECIPE-BOOK, AND THE VALIDATOR'S RECIPE-BOOK RULE CURRENTLY CHECKS NOTHING.** ⇒ ⇒⇒⇒⇒⇒⇒⇒⇒⇒⇒ **⇒⇒⇒⇒⇒⇒⇒⇒⇒⇒⇒ THE GENERATOR READS <code>recipe.json</code> + <code>codex.json</code> (<code>generate-react.cjs:823-824</code>); THE FvW VALIDATOR READS <code>recipe.md</code> + <code>codex.md</code> (<code>rules/codex-structure.js</code>).** ⇒ The amendment in items 6, 7 and 8 and in Part 54 item 4 is what makes the two formats agree, and the gap is recorded so a reader knows the agreement is a REQUIREMENT and not the present state.
7. THE RECIPE AND THE CODEX ARE JSON, NOT MARKDOWN. A recipe-book carries four constitutional artefacts:

- <code>module.json</code> — the identity. Module root, NOT inside <code>recipe-book/</code>. Required.
- <code>recipe.json</code> — the AST. Inside <code>recipe-book/</code>. The Generator's only input. Required.
- <code>codex.json</code> — the schema and behaviour. Inside <code>recipe-book/</code>. The Validator's only input. Required.
- <code>handbook.md</code> — the user-facing manual. Inside <code>recipe-book/</code>. Generated from the three above. Required.

Optional prose (<code>recipe.md</code>, <code>codex.md</code>, <code>rules.md</code>) may sit alongside the JSON for human readers. The Generator never reads them. A change to a <code>.md</code> file alone is invisible to the generation path.

⇒ ⇒⇒ **MEASURED (FVC 1273, against <code>origin/main</code> <code>66cd3f8b</code>): this item SUPERSEDES the previous text, and the code agrees with the correction, not with the previous text.** The Generator's own entry point reads the JSON and nothing else — <code>src/modules/generator/src/generate-react.cjs:3107</code> sets <code>recipePath = path.join(recipeBookDir, 'recipe.json')</code> and <code>:3108</code> sets <code>codexPath = path.join(recipeBookDir, 'codex.json')</code>. ⇒ The previous text was wrong: a markdown-only recipe-book is exactly what the Generator cannot consume.

⇒ ⇒⇒ **THE MARKDOWN-ONLY MODULE COUNT, MEASURED (FVC 1273).** The dispatch that requested this amendment cited "75 modules that shipped with only markdown and no JSON". That figure is NOT reproducible. The correct counts are recorded here so a reader does not inherit a number nobody can check. A module is a directory carrying a <code>module.json</code>; it is markdown-only when it has a <code>recipe-book/recipe.md</code> and no <code>recipe-book/recipe.json</code>:

- <code>src/modules/</code> — 40 modules, <b>39</b> markdown-only, <b>1</b> with <code>recipe.json</code> (<code>layers-panel</code>), <b>0</b> with <code>handbook.md</code>.
- <code>vendor/fv-module-gallery/</code> — 236 modules, <b>160</b> markdown-only, <b>0</b> with <code>recipe.json</code>, <b>0</b> with <code>handbook.md</code>.
- Repo-wide, excluding <code>node_modules/</code> and <code>.git/</code> — 433 modules, <b>241</b> markdown-only.

⇒ The DIRECTION of the dispatch's claim holds — markdown-only modules are the norm, not the exception — but the number was wrong, and the number is what a reader would have checked. ⇒ ⇒⇒ **AT THE TIME OF THIS ITEM, <code>handbook.md</code> EXISTS NOWHERE IN THE REPOSITORY (0 files, repo-wide), and <code>recipe.json</code> exists in 5 places, of which only <b>1</b> is a module (<code>src/modules/layers-panel/</code>).** The four-artefact contract is therefore a REQUIREMENT the tree does not yet satisfy. This item is the requirement, not a description of the present.
8. THE CODEX IS NOT A JSON SCHEMA, SO "VALIDATED AGAINST THE CODEX SCHEMA" MEANS CHECKED AGAINST THE CODEX'S RULES. The Codex is prose organised under C1-C8 headings. The Codex's own rule (<code>src/modules/validator/src/rules/codex-structure.js</code>) forbids NUMBERED sections in a codex document, because numbered sections are rules and belong in <code>rules.md</code>. The Validator therefore checks the SHAPE of a recipe-book (that the three files exist, that the recipe has its A/B/C sections, that the codex has no rules-shaped content) and checks the code against the codex for DRIFT. Where a JSON Schema is genuinely required, it is <code>gallery-pact/fvw/validator-v8.json</code> — draft-07, ten principles P1-P10 under gate G40, plus the FVRE fidelity/alignment clause under G41.
9. THE GENERATOR IS THE SCAFFOLD, AND IT ALREADY HAS ITS OWN VALIDATOR. <code>src/scaffold/validator.ts</code> is a pure deterministic validator (no LLM calls, under 5ms) that checks app-name sanity, non-empty file names and content, the v8 first-file rule (<code>annotation/index.json</code> first), allowed directories, HTML tag balance, JSON parseability, and file-count agreement. <code>build_freshvibe_app</code> runs it BEFORE any write, and on failure the corrector (<code>src/scaffold/corrector.ts</code>) fills the gaps with sub-agents before the write is retried. This is the pattern Part 45 mandates, already working for the scaffold.
10. THE VALIDATOR IS A REPORT TODAY, NOT A GATE. <code>GET /api/agent/fvw/validate</code> returns the report, and <code>GET /api/agent/fvw/mode</code> returns the mode. The mode defaults to <code>warn</code> unless <code>FVW_VALIDATION_MODE</code> is <code>off</code>, <code>warn</code>, or <code>strict</code>. A report that nothing reads does not stop a build, so until the mode is <code>strict</code> on the generation path, this Part is a REQUIREMENT and not a FACT.
11. THE GATE MUST REJECT, NOT WARN. In <code>strict</code> mode the validator promotes critical warnings to errors. The Gate is the strict path, and a Recipe that produces errors is rejected. The <code>codex-structure</code> rule already marks a rules-shaped codex as <code>critical_in_strict</code>, so a Codex that has been corrupted into a rules document is a rejection, not a note.
12. THE ERROR PAYLOAD MUST BE THE GUIDANCE PAYLOAD. Part 25 already requires the validator to output JSON with <code>rule</code>, <code>expected</code>, <code>actual</code>, and <code>guidance</code> so the AI can self-correct. Part 45 adopts that payload unchanged, because a Gate that reports "invalid" without naming the expected value teaches the AI nothing. The Validator does not make the AI deterministic; it makes the AI's failures legible, which is the only way the AI can be made to fix them.
13. A RECIPE THAT FAILS THE GATE CANNOT ENTER THE STENCIL. This is Part 41 item 7 and Part 43 item 5 read together: the Stencil is a structural sandbox and the Approval Gate is a verification, so a Recipe that has not passed the Validator cannot be rendered in the Stencil, cannot be approved, and cannot be promoted to the Live Canvas. The Stencil is where the Proposed Diff is shown, and a diff against a Recipe that was never valid is a diff against nothing.
14. THE GATE MUST NOT BE VACUOUS. Part 25 already requires the validator to exit non-zero when <code>modulesScanned === 0</code>, because a scan that finds nothing is a scan that proved nothing. The same rule applies here: a Gate that validates zero recipes has validated nothing and MUST report that, not pass.
15. THE CODEX MUST ALLOW A <code>background</code> PROPERTY ON ANY PAGE, SECTION, OR WIDGET NODE, AND MUST NAME THE LEVEL (Part 55). The <code>background</code> Bucket and its <code>background.image</code> and <code>background.color</code> Slots are already named in Part 10.2, but a Bucket is a settings-panel namespace — it is NOT a property a node can carry. ⇒ A Codex for a surface that paints a background MUST permit a <code>background</code> property on that node and MUST require the background's LEVEL to be stated, because the level decides the positioning ancestor: Page-Level is <code>position: fixed</code> against the viewport, Section-Level and Widget-Level are <code>position: absolute</code> against their nearest positioned ancestor. A Codex that forbids the property makes the surface unexpressible; a Codex that permits it without naming the level makes the level a guess.
16. THE CODEX FOR A PAGE-LEVEL BACKGROUND MUST STATE <code>pointer-events: none</code> (Part 55). A Page-Level background is scenery behind the content and never a hit target. ⇒ A Codex that permits a Page-Level background MUST also forbid it from intercepting the pointer, or the background silently swallows every click on the page.
17. THE CODEX MAY DESCRIBE THE 'CinemaBackground' WIDGET, BUT THE WIDGET ITSELF IS A REGISTRY ENTRY (Part 55). The gallery's <code>background-gradient</code> and <code>background-image</code> modules are NOT registry entries; the registry's 44 names contain no <code>CinemaBackground</code> and no <code>background</code> widget. ⇒ A Codex that names <code>CinemaBackground</code> describes a widget the registry does not yet carry, and the Extractor's output MUST report it as unmapped (Part 46 item 11) rather than resolve it.

## Part 46: The Vision Extractor

1. The operator can upload an image (a website screenshot, a design mockup, an AI-generated concept). The Vision Extractor uses an AI model to analyze the image.
2. The Extractor outputs a structured JSON map of visual elements: colours (hex), gradients, shadows/glares, typography, and layout structure.
3. The AI then maps these extracted elements to the Widget Registry. It does not write raw CSS. It assigns visual properties to the world-class widgets.
4. The output is a Recipe that generates a buildable React app that matches the image's vibe.
5. THE WIDGET REGISTRY IS <code>src/cms/data/cms-widgets-index.json</code>, AND IT IS THE NAMED TARGET. It holds 44 widgets, 40 of which declare a schema, totalling 265 declared properties, with 12 marked required. The Extractor's output is a Recipe whose every visual property resolves to a property in that index. A property that resolves to nothing in the index is not a mapping and MUST be reported, not invented.
6. THE REGISTRY'S PROPERTY TYPES ARE THE EXTRACTOR'S OUTPUT TYPES, NOT FREE-FORM CSS. Measured across the 265 properties: <code>select</code> 80, <code>string</code> 72, <code>boolean</code> 46, <code>number</code> 23, <code>array</code> 16, <code>color</code> 10, <code>url</code> 5, <code>link</code> 4, <code>object</code> 4, <code>image</code> 3, <code>border</code> 1, <code>spacing</code> 1. The Extractor's map MUST use these types. A colour is a <code>color</code>; a spacing value is a <code>spacing</code>; a choice is a <code>select</code> with its declared <code>options</code>.
7. THREE OF THE EXTRACTOR'S FIVE CATEGORIES HAVE NO TARGET IN THE REGISTRY YET, AND THAT IS THE REAL CONSTRAINT. Measured: the registry has 10 <code>color</code> properties (<code>button.color</code>, <code>cta.color</code>, <code>divider.color</code>, <code>heading.color</code>, <code>icon.color</code>, <code>icon-list.iconColor</code>, <code>paragraph.color</code>, <code>rating.colour</code>, <code>rating.inactiveColour</code>, <code>social-icons.color</code>) and layout properties (<code>layout</code>, <code>width</code>, <code>maxWidth</code>, <code>fullWidth</code>, <code>columns</code>, <code>gap</code>, <code>drawerWidth</code>) — but it has <b>ZERO</b> properties whose type or name is <code>gradient</code>, <b>ZERO</b> for <code>shadow</code>, and <b>ZERO</b> for typography (<code>font</code>, <code>fontSize</code>, <code>fontFamily</code>, <code>lineHeight</code>, <code>letterSpacing</code>). ⇒ The Extractor CANNOT yet express a gradient, a shadow, or a typeface as a Recipe, because the Recipe has nowhere to put them. This is the Single Property Rule (Part 15) biting from the other side: a new visual effect must become a property in a widget's schema before it can be extracted. Building the Extractor before closing this gap produces a Recipe that drops the image's most distinctive qualities.
8. THE VISION MODEL PATH ALREADY EXISTS AND IS ALREADY PROVEN. The bridge routes any request carrying image attachments to a Gemini-only cascade — <code>gemini-flash-latest</code> on <code>GEMINI_API_KEY</code> then <code>gemini-3.5-flash-lite</code> on <code>GEMINI_API_KEY_2</code> — because Groq and NVIDIA return HTTP 400 on image payloads. The client side already exists too: <code>src/vcs/image-paste.js</code> installs a paste handler on any <code>.vcs-input-field</code>, accepts <code>image/png</code>, <code>image/jpeg</code>, <code>image/jpg</code> and <code>image/webp</code>, caps an image at 5 MB, and passes <code>[{kind:"image", mime, data_base64, name}]</code>. ⇒ Phase 4 of the Build Plan does not need to invent a model path; it needs to add the EXTRACTION step to a path that already carries the image to a vision model.
9. THE EXTRACTOR IS THE ONLY COMPONENT IN THE PIPELINE THAT IS ALLOWED TO BE NON-DETERMINISTIC, AND IT IS THE ONLY ONE WHOSE OUTPUT IS NOT FINAL. The Extractor's JSON is a Candidate Recipe (Part 35) — a Proposed, not an Actual. It is a Stencil input (Part 41), it is subject to the Validator Gate (Part 45), and it is approved through the Approval Gate (Part 43) before it may become a Current Recipe. ⇒ The Extractor proposes; the Validator disposes; the operator approves. An Extractor output that has not passed the Validator and has not been approved cannot be promoted to the Live Canvas.
10. THE EXTRACTOR MUST NOT WRITE CSS, AND THAT IS A BOUNDARY, NOT A STYLE PREFERENCE. Part 46 item 3 says the Extractor assigns visual properties to widgets. The registry is the entire permitted vocabulary of visual properties, and the 13 Buckets and Slots and Controls (Part 10) are the model for how a property becomes a control. A control that exists in the component but not in the recipe is lost at the next regeneration (Part 44 item 4), so an Extractor output that names a property the recipe does not carry is not a mapping, it is a loss.
11. THE EXTRACTOR MUST REPORT WHAT IT COULD NOT MAP. An image is a whole; a Recipe is a set of widgets with declared properties. The Extractor's output therefore carries, alongside the Recipe, the parts of the image that the registry could not express — the gradients, the shadows, the typefaces, the spacing rhythm. Those are not errors and MUST NOT be silently dropped. They are the operator's evidence for the next registry change, and they are what the Stencil shows when the Candidate is compared against the Actual.

## Part 47: The Stencil Snapshot Archive

1. Every Stencil generation must be bound to a VC Turn.
2. The FC Brain archives the JSON Recipe Diff, the user's<br />prompt, and a visual screenshot of the Stencil.
3. The user can browse historical Snapshots and restore<br />a previous Candidate Recipe.

## Part 48: The Decision Graph

1. A Decision records the Turn, the Recipe Diff, the operator's<br />prompt, and the rationale for the decision.
2. Decisions have lifecycle states: <code>proposed</code>, <code>accepted</code>,<br /><code>rejected</code>, <code>superseded</code>.
3. When a new Decision supersedes an old one, the old one<br />is marked <code>superseded</code>, not deleted.
4. A Decision carries four fields the base entity does not:<br /><code>turnId</code>, <code>prompt</code>, <code>recipeDiff</code>,<br /><code>rationale</code>.
5. <code>turnId</code>, <code>prompt</code> and <code>recipeDiff</code> are ADDITIVE<br />extension fields. The entity still satisfies <code>isDecision</code>,<br />and <code>supersede()</code> still works on it.
6. A Decision that fails to record MUST NOT fail the Recipe write.<br />The Recipe is the product; the Decision is the record. The failure<br />is REPORTED to the caller, never swallowed.

## Part 49: The FvW Module Structure

1. Every piece of the system (UI, Engines, Layouts) must<br />be an FvW Module.
2. Every Module must have a module.json, a recipe-book/,<br />and a codex.json.
3. The FC Brain can only trace and manage Modules.

## Part 50: The V-Agent Architecture

1. VibeChat is powered by V-Agents (LLMs).
2. V-Agents take user prompts and generate JSON Recipes.
3. V-Agents are wrapped as FvW Modules.

## Part 51: The Five Pillars

1. Extractor: Image to JSON.
2. Validator: JSON to Schema Check.
3. Generator: JSON to React.
4. Display Engine: Multi-device iframes.
5. Cinema Engine: Timeline, paint, animations.<br />All five are core Engines and must be FvW Modules.

## Part 52: The State Engine

1. VibeCoder requires a central State Engine to manage the<br />active tab, the active project, and the UI conditions.
2. The State Engine holds the truth, so the Header and the<br />Canvas do not drift.
3. The State Engine is a core module with its own recipe<br />and codex.

## Part 53: The Routing Engine

1. Every view in VibeCoder (Preview, Stencil, Dashboard)<br />must have a unique, bookmarkable URL.
2. The URL is the source of truth. The State Engine reads<br />the URL to determine which view to render.
3. The Header tabs must be actual links (\<a href="...">),<br />not just local state buttons.

## Part 54: The Module Hierarchy (Faces)

1. Every UI element is a Module, and every Module is a Face.
2. The Engines (Generator, Validator, Extractor) are Modules.
3. The Layout System (Panels) is a Module.
4. ALL MODULES MUST CARRY THE FOUR CONSTITUTIONAL ARTEFACTS.

- <code>module.json</code> — the identity. Module root, NOT inside <code>recipe-book/</code>. Required.
- <code>recipe.json</code> — the AST. Inside <code>recipe-book/</code>. Required.
- <code>codex.json</code> — the schema and behaviour. Inside <code>recipe-book/</code>. Required.
- <code>handbook.md</code> — the manual. Inside <code>recipe-book/</code>. Generated, not hand-written. Required.

A module without any of the four is not a completed module. It is a folder. The four artefacts are the minimum contract that makes a module addressable by the Generator, the Validator, the Stencil, and the Approval Gate.

The format of each artefact is defined by the FvW, not by this spec. This spec enforces that the factory produces them. The two categories of modules (Part 72) both carry the same four artefacts; only the reader of <code>recipe.json</code> differs.

⇒ ⇒⇒ **MEASURED (FVC 1273, against <code>origin/main</code> <code>66cd3f8b</code>): at the time of this item the tree does NOT yet satisfy this contract, and the size of the gap is the size of the task.** <code>src/modules/</code> carries 40 modules and 40 <code>module.json</code> files, but only <b>1</b> <code>recipe.json</code> (<code>layers-panel</code>) and <b>0</b> <code>handbook.md</code>. ⇒ ⇒⇒⇒ **⇒⇒⇒⇒ AND THE GALLOGY IS THE SAME SHAPE: <code>vendor/fv-module-gallery/</code> carries 236 modules, 160 of them markdown-only, and <b>0</b> with <code>recipe.json</code> and <b>0</b> with <code>handbook.md</code>.** ⇒ ⇒⇒⇒⇒ **⇒⇒⇒⇒⇒ REPO-WIDE THE NUMBERS ARE 433 MODULES AND 241 MARKDOWN-ONLY, AND <code>handbook.md</code> EXISTS IN ZERO PLACES IN THE ENTIRE REPOSITORY.** ⇒ This item is a REQUIREMENT, not a description of the present, and it is the same requirement the dispatch named.


## Part 55: The Background Layers

1. Backgrounds are not a single layer. They exist at<br />three distinct levels:<br />- Page-Level: Fixed to the viewport, behind all content.<br />(e.g., a starfield, a 3D canvas).<br />- Section-Level: Absolute to a specific section.<br />(e.g., a tinted glass panel behind a Hero text).<br />- Widget-Level: Absolute inside a widget.<br />(e.g., a frosted glass blur on a panel).
2. The Cinema Engine must support a 'CinemaBackground'<br />widget. This is a canvas animation pinned to<br />the Page-Level, with pointer-events: none.
3. The Codex must allow a 'background' property on any<br />Page, Section, or Widget node.
4. THE THREE LEVELS ARE NOT INTERCHANGEABLE, AND THE POSITIONING IS WHAT MAKES THEM SO. Page-Level is <code>position: fixed</code> against the viewport and therefore scrolls independently of the content. Section-Level and Widget-Level are <code>position: absolute</code> against their nearest positioned ancestor and therefore move with it. ⇒ A background authored at the wrong level cannot be rescued by a different <code>z-index</code>: the level decides which ancestor the background is positioned against, and <code>z-index</code> only decides the paint order within that ancestor. ⇒ The Extractor MUST name the level when it maps a background, and a background with no named level is not a mapping.
5. THE LEVEL IS A PROPERTY OF THE NODE, AND THE CODEX IS WHERE IT IS DECLARED. A <code>background</code> property on a Page, Section, or Widget node carries the level with it — Page, Section, or Widget — and the level is the node's own, not a separate global setting. ⇒ A Recipe that sets a background on a Section cannot silently paint it Page-Level, and one that sets it on a Widget cannot silently promote it out of the widget.
6. THE WIDGET REGISTRY HAS NO <code>background</code> PROPERTY AT ALL, AND THAT IS THE REAL CONSTRAINT. Measured against the generated registry (<code>src/cms/data/cms-widgets-index.json</code>, 44 widgets, 40 with a schema, 265 declared properties): <b>ZERO</b> properties are named <code>background</code>. ⇒ The Extractor CANNOT yet express ANY background as a Recipe, at any level, because the Recipe has nowhere to put it. This is the same Single Property Rule (Part 15) constraint that Part 46 item 7 names for gradients, shadows and typography: a new visual effect must become a property in a widget's schema before it can be extracted. ⇒ Adding Part 55 to the Spec does not by itself make the background extractable; the registry property is the companion change and is NOT part of this Part.
7. THE 'CinemaBackground' WIDGET IS A NEW WIDGET, AND THE REGISTRY IS WHERE WIDGETS LIVE. The registry's 44 names are <code>accordion</code>, <code>blog-list</code>, <code>blog-post-card</code>, <code>blog-post-list</code>, <code>breadcrumb</code>, <code>button</code>, <code>carousel</code>, <code>contact-form</code>, <code>content-card</code>, <code>counter</code>, <code>cta</code>, <code>cta-box</code>, <code>divider</code>, <code>filters</code>, <code>form</code>, <code>gallery</code>, <code>heading</code>, <code>icon</code>, <code>icon-list</code>, <code>image</code>, <code>info-box</code>, <code>link</code>, <code>list</code>, <code>listing-grid</code>, <code>map</code>, <code>media-strip</code>, <code>modal</code>, <code>nav-menu</code>, <code>pagination</code>, <code>paragraph</code>, <code>pricing-table</code>, <code>product-grid</code>, <code>query-loop</code>, <code>rating</code>, <code>recipe-detail</code>, <code>search-bar</code>, <code>section</code>, <code>social-icons</code>, <code>sort-controls</code>, <code>spacer</code>, <code>tabs</code>, <code>testimonial</code>, <code>toggle</code>, <code>video</code>. There is <b>NO</b> <code>CinemaBackground</code> among them, and no <code>background</code> widget of any name. ⇒ The CinemaBackground is a NEW registry entry, and the gallery's <code>background-gradient</code> and <code>background-image</code> modules are NOT registry entries — they are gallery modules, and a gallery module is not a widget until the registry names it.
8. A CINEMABACKGROUND IS PAGE-LEVEL BY DEFINITION AND MUST NOT INTERCEPT THE POINTER. It is a canvas animation behind all content, so it carries <code>pointer-events: none</code> and never becomes a hit target. ⇒ A background that swallows clicks is a regression at the Page level, not a styling choice, and a Codex for the CinemaBackground MUST state the <code>pointer-events: none</code> rule. It is the background's whole reason for existing: it is scenery.
9. THE CODEX ALLOWS THE PROPERTY; THE REGISTRY CARRIES ITS SHAPE. The Codex is prose under C1-C8 (Part 45 item 8) and is what a Gate reads; the registry's schema is what the Extractor's output must resolve to (Part 46 item 5). ⇒ Part 55 item 3 says the Codex must ALLOW a <code>background</code> property on a Page, Section, or Widget node — that is a rule about what a Codex may forbid or require, not a declaration of the property's type. The property's type, its options and its default belong to the registry entry, and until that entry exists the property is allowed but unresolvable, which the Extractor MUST report (Part 46 item 11) rather than silently drop.
10. THE GEMINI MOCKUP'S GLOWING ORBS AND CANVAS ANIMATIONS ARE THE PROBLEM THIS PART EXISTS TO SOLVE, AND THEY ARE PAGE-LEVEL. An orb field that parallaxes behind the whole page, and a canvas animation that runs behind the content, are Page-Level backgrounds. ⇒ The Extractor's mapping for them is a Page node carrying a Page-Level <code>background</code>, and the rendered result is the CinemaBackground widget. ⇒ A mockup whose orbs sit BEHIND one Hero section is Section-Level and MUST NOT be mapped as Page-Level, because the two look identical in a still image and behave differently on scroll. ⇒ The Extractor resolves the level from the orb's EXTENT relative to the content, not from its appearance.


## Part 61: Mobile Interaction Models

1. Complex panels must use a Progressive Disclosure<br />Bottom Sheet on mobile.
2. Collapsed state: Full-width input bar docked to<br />the bottom.
3. Typing state: A strip slides up showing the last<br />message.
4. Expanded state: Swiping up opens the full message<br />sheet with a drag handle.
5. Floating window controls (minimize, close, drag)<br />are forbidden on mobile.

6. THE MEASURED DEFECT THIS PART EXISTS TO FIX. On live production at a<br />430x932 viewport, the VibeChat sheet opened at its <code>bar</code><br />detent and rendered as a <b>desktop floating window</b>: a rounded card<br />with a title bar reading "VibeChat", a drag pill, and FOUR window<br />controls - <code>Minimize VibeChat</code>, <code>Close VibeChat</code><br />(twice) and <code>Expand VibeChat</code> - squeezed into 430px. The<br />same surface at 1440x900 rendered the identical four controls, so<br />there was <b>one surface and no mobile variant at all</b>. Item 5 is<br />therefore not a style preference; it is the description of a measured<br />fault.
7. A PROGRESSIVE-DISCLOSURE SHEET HAS THREE STATES, AND EACH ONE IS<br />A DIFFERENT AMOUNT OF THE SURFACE, NOT A DIFFERENT COLOUR OF<br />THE SAME SURFACE. The collapsed state shows an input bar and nothing<br />else; the typing state adds a strip carrying the last message; the<br />expanded state carries the full message sheet. ⇒ A surface that<br />renders its title bar, its window buttons and its rail in EVERY state<br />is a window, not a disclosure, and the operator has to read the whole<br />thing to find the one control they wanted.
8. THE SHEET IS DOCKED, NOT FLOATING. The collapsed state is a<br />full-width bar against the bottom edge of the viewport, so the canvas<br />above it stays usable. ⇒ A panel that floats free of the bottom edge<br />with rounded corners on all four sides is a desktop window that<br />happened to be scaled down, and the rounded bottom corners alone prove<br />it: a bottom-docked bar has no bottom corners to round.
9. THE INPUT MUST ACCEPT TEXT IN EVERY MOBILE STATE, AND THAT IS<br />SEPARATE FROM WHERE IT SITS. The measured mobile input already<br />accepted text - a typed probe landed in the field verbatim - so the<br />"cannot type" symptom is not an input defect but a LAYOUT defect<br />where the field is rendered somewhere the operator cannot reach it, or<br />is covered by a control that sits on top of it. ⇒ Fix the reachability<br />and the geometry; do not rewrite a working input.
10. THE WINDOW CONTROLS ARE FORBIDDEN, NOT MERELY SMALLER. A minimize<br />button, a close button and a drag affordance are the vocabulary of a<br />window an operator moves around a desktop. On a phone the sheet is<br />ALREADY at the bottom of the screen, so "minimize" is the gesture<br />everybody knows, and "drag" is answered by the sheet's own detent<br />gesture. ⇒ Keep exactly one affordance on mobile: the drag handle<br />that changes the detent. A second way to do the same thing is a<br />duplicate, and a duplicate control on a phone is a mis-tap waiting to<br />happen.
11. THE DETENT IS THE STATE, AND THE GESTURE IS THE TRANSITION. The<br />sheet's height is the state: collapsed, typing, expanded. A swipe up<br />from the collapsed bar opens the expanded sheet; a swipe down returns<br />to the collapsed bar. ⇒ The state must be REACHABLE BY GESTURE ALONE,<br />because a phone operator's first hand is already holding the sheet, and<br />a state that needs a button is a state that a phone operator will
never find.
12. THE CODEX DECLARES THE MOBILE BEHAVIOUR, AND THE SPEC DOES NOT<br />LEAVE IT TO A COMPONENT. The Codex for a mobile surface carries<br /><code>mobile_behavior</code> in its <code>responsive</code> block, and the<br />value names the PATTERN (<code>bottom_sheet</code>), not a sentence<br />about it. ⇒ The Codex says WHICH pattern; the component implements it;<br />the Spec says what the pattern MEANS. All three are needed, and none<br />of the three can do the work of the other two.
13. THE GAP IN THE PART NUMBERING IS RECORDED, NOT PAPERED OVER.<br />This Part is numbered <b>61</b> as the dispatch named it. The numbering<br />is PRESERVED VERBATIM because the dispatch named it, following the<br />precedent set by PREMISE CORRECTION 1 (Parts 52-54 were appended as<br />dispatched, and the gap was recorded rather than silently renumbered).<br />⇒ A reader must not assume the Part sequence is contiguous.<br /><br /><b>RESOLVED IN v3.19.0 (FVC 1244):</b> Parts 58, 59 and 60 were added by a later<br />dispatch, so the vacant range is now 56-57 only. Parts 61, 62 and 63<br />carry their dispatched numbers. The sequence is contiguous 1-55, then<br />58-63; 56 and 57 remain vacant, and this note is the record of that.

## Part 62: The Handles

1. Every side handle (Assets, Deck, VibeChat) must display
   a vertical text label.
2. The handle must have a minimum width of 24px to be
   easily swipeable on mobile.
3. The text must be written vertically (writing-mode: vertical-rl)
   and centered.

### 62.1 The Measured Baseline This Part Replaces

⇒ **⇒⇒ MEASURED ON LIVE PRODUCTION, 2026-10-27, BEFORE THIS PART.** A Playwright
measurement of <code>https://vibecoder.freshvibeapps.com/</code> found exactly
four <code>.fv-handle</code> elements, and EVERY ONE of them:

| handle | side | measured w x h | innerText | computed writing-mode | colour strip |
|---|---|---|---|---|---|
| Assets | left | 16 x 96 | **empty (0 chars)** | horizontal-tb | rgb(59, 130, 246) |
| Deck | right | 16 x 96 | **empty (0 chars)** | horizontal-tb | rgb(34, 197, 94) |
| VibeChat | bottom | 96 x 16 | **empty (0 chars)** | horizontal-tb | rgb(124, 58, 237) |
| Panels | bottom | 96 x 16 | **empty (0 chars)** | horizontal-tb | rgb(74, 222, 128) |

⇒ So items 1 and 2 above describe a real, measured gap and not a preference:
the default was <code>var(--fv-handle-width, 16px)</code> and not one handle
carried any text at all.

⇒ ⇒⇒ **AND THE TOKEN IS WHERE THE SIZE LIVES, NOT THE FALLBACK.** The
first implementation of this Part changed the component's fallback from
<code>var(--fv-handle-width, 16px)</code> to <code>var(--fv-handle-width,
24px)</code> — and the live handles STAYED 16px. ⇒ The reason: the fallback
is only reached when the custom property is UNDEFINED, and
<code>src/styles/tokens.css</code> DEFINES <code>--fv-handle-width:
16px</code>. ⇒ So the fallback was dead code and the component change was
a no-op.

⇒ ⇒⇒ **⇒⇒ ⇒⇒ A FALLBACK IS NOT A DEFAULT.** A token that is always
defined makes every <code>var(--token, fallback)</code> in the codebase a
lie. ⇒ ⇒⇒ ⇒⇒ THE TOKEN FILE IS THE SOURCE OF TRUTH FOR A DIMENSION, and a
component that consumes a token MUST NOT be where the size is decided.
⇒ The token is <code>--fv-handle-width: 24px</code> and the component's
fallback is <code>24px</code> too, so the two AGREE — and they must be
changed TOGETHER, because a change to one that leaves the other behind is
exactly the half-fix this caught.

⇒ ⇒⇒ **⇒⇒ ⇒⇒ THIS IS THE SAME SHAPE AS FVC 1236.** There, a layout's
column count changed and the panel's width — DERIVED from the tiles — was
left stale, so the CSS and the geometry contradicted each other. ⇒ Here, a
dimension changed and the TOKEN that carries it was left stale, so the
component and the rendered handle contradicted each other. ⇒ ⇒⇒ ⇒⇒ **WHEN
A DIMENSION CHANGES, EVERY TOKEN THAT CARRIES IT MUST BE RE-DERIVED FROM
IT, AND THE PLACE THAT CARRIES IT MUST BE FOUND FIRST.**

### 62.2 The Colour Strip Is Preserved, Not Replaced

⇒ **⇒⇒ THE LABEL IS AN ADDITION TO THE STRIP, NOT A SUBSTITUTE FOR IT.** Each
handle's identity is carried by its colour — Assets blue, Deck green,
VibeChat purple, Panels teal — and the strip is how that identity is read at
a glance. A handle that gains a label and loses its colour is a DIFFERENT
handle, and the four would become indistinguishable.

⇒ ⇒ The strip and the label occupy the same box and the strip is drawn BEHIND
the text, so both are visible at once. The strip's colour remains the
handle's <code>color</code>, and the label inherits it.

### 62.3 The Orientation Rule Is Per-Handle, Not Global

⇒ **⇒⇒ "VERTICAL TEXT" IS A PROPERTY OF THE HANDLE'S OWN ORIENTATION, NOT OF
THE WORD "SIDE".** The dispatch names Assets, Deck and VibeChat together as
"side handles", but the Shell mounts VibeChat as a <code>bottom</code> handle
whose long axis is horizontal (96 x 16 measured). ⇒ A handle whose long axis
is vertical writes its label with <code>writing-mode: vertical-rl</code>; a
handle whose long axis is horizontal writes it with <code>horizontal-tb</code>.
The RULE is "the label runs ALONG the handle"; the two writing modes are the
two cases of it.

⇒ ⇒ Applying <code>vertical-rl</code> to a 96 x 16 bottom handle would set the
text along the SHORT axis and overflow the strip, which is the defect this
Part exists to remove.

### 62.4 The Minimum Width Is A Floor, Not A Target

⇒ Item 2 sets **24px** as a MINIMUM. Measured against the common touch-target
guidance — Apple HIG's 44 x 44 pt and Material's 48 x 48 dp — 24px is a
narrower guarantee than those standards ask for. ⇒ ⇒ The 24px floor is a real
and measured improvement over the 16px default, and this Part does NOT claim
it satisfies a full accessibility target. ⇒ A handle MUST NOT be rendered
narrower than 24px along its SHORT axis; it MAY be wider, and a wider handle
is not a violation of this Part.

### 62.5 The Numbering Gap

⇒ **⇒⇒ THE PART NUMBER IS THE DISPATCH'S, VERBATIM.** The dispatch named
"Part 62", and that name is what appears above. ⇒ The dispatch's own
numbering is PRESERVED rather than rewritten to 56, because renumbering
would silently rewrite the dispatch's text — and the gap is recorded here so
that no reader assumes the numbering is contiguous. ⇒ This follows the
precedent already set by PREMISE CORRECTION 1 in this spec, which recorded
the same kind of gap the same way.

⇒ ⇒⇒ **THE GAP IS NOW 56 TO 60, NOT 56 TO 61.** When this Part was written
the spec's headings ran contiguously from Part 41 to Part 55, and Parts 56
through 61 were all unallocated. ⇒ Part 61 was subsequently added by FVC
1242 (the mobile VibeChat Progressive Disclosure Bottom Sheet), which also
took v3.17.0 — so this Part took v3.18.0, and the spec's numbering is now
contiguous from Part 41 to Part 55, then Part 61, then Part 62. ⇒ Parts 56
through 60 remain unallocated, and NO file anywhere in the repository
references them.

### 62.6 The Relationship To Part 3

⇒ Part 3.1 describes the Handle as a "Thin, narrow strip on the left or right
edge". ⇒ **⇒⇒ THIS PART SUPERSEDES THAT DESCRIPTION.** A 24px handle carrying a
vertical text label is neither thin nor narrow in the sense Part 3.1 meant, and
the later Part governs. ⇒ The rest of Part 3 — the Z-Index rule, the tap and
swipe actions, the Deck's behaviour, the Panel Header, the Collection Model,
the Contextual Availability rules and the Translation Table — is UNCHANGED.


## Part 58: The Deploy Gate

1. The deploy gate refuses to start the bridge when there are<br />uncommitted SOURCE changes.
2. Runtime state (<code>*.bak-*</code>, <code>.state/</code>,<br /><code>.soak-state.json</code>) is ignored by <code>.gitignore</code><br />and does not count as dirty.
3. A DIRTY SUBMODULE POINTER IS NOT A SOURCE CHANGE. A submodule<br />gitlink carries mode 160000 on BOTH sides of a diff, and<br /><code>git diff --quiet</code> cannot tell a gitlink from an<br />edited file. ⇒ The gate MUST inspect <code>git diff --raw</code><br />and refuse ONLY when a real source file changed. ⇒ A gate that<br />refuses on a pointer move refuses on a fact that is not a fault, and<br />a gate that refuses for a reason that is not a fault gets ignored.
4. THE GATE MUST SAY WHICH IT FOUND. A refusal names the source<br />change or names the pointer move; a gate that says "uncommitted<br />changes" and means something else is a gate that teaches its operator<br />to disbelieve it.
5. A REFUSAL IS POSTED AT MOST ONCE PER WINDOW. The gate writes a<br />timestamp BEFORE it posts, under an atomic lock, so a crash-looping<br />restart cannot re-post inside the window. ⇒ Eleven identical permanent<br />bulletins is not eleven pieces of information; it is one piece of<br />information and ten pieces of noise.

## Part 59: The Registry Generator

1. The module registry (<code>app-registry/modules.index.json</code>)<br />is GENERATED, not maintained by hand.
2. It is generated from the two authoritative populations:<br />- <code>src/modules/&lt;name&gt;/module.json</code> — the LOCAL modules,<br />each with a <code>codePath</code>;<br />- <code>app-vgm/vgm-manifest.json</code> — the GALLERY MIRRORS,<br />each with <code>codePath: null</code>, because the gallery is a<br />private repo and a mirror has no source on this disk.
3. THE REGISTRY IS A PROJECTION, NOT A LIST. The gallery mirrors'<br />identity lives in the VGM manifest — the same source the FC Brain's<br />identity API already reads — so the registry is that manifest plus<br />the local modules, and nothing else. ⇒ A hand-maintained registry<br />drifts the moment a module is added, and the drift surfaces in<br />PRODUCTION as validator errors.
4. A MODULE THAT IS NOT IN THE REGISTRY IS INVISIBLE, AND A MODULE IN<br />IT WITH A DEAD <code>codePath</code> IS A BROKEN POINTER. ⇒ Both<br />states are generated, so both are impossible by construction.
5. THE GENERATOR RUNS IN CI, AND THE VALIDATOR CHECKS THE OUTPUT. The<br /><code>module-registry-generated</code> rule compares the committed<br />registry against a fresh generation, so a hand-edited row is a failed<br />build rather than a production error.
6. MEASURED: the drift was caught by FVC 1219's <code>module-code-path</code><br />rule as 30 production errors, 29 of them "wrapped but invisible", and<br />the repair meant hand-editing 29 rows. The registry is now 115 rows:<br />40 local + 75 gallery mirrors.

## Part 60: The CinemaBackground Mandate

1. A Page-Level background is rendered by the REAL widget. A CSS<br />gradient, a <code>::before</code> pseudo-element or an inline<br /><code>background-image</code> that imitates a scene is NOT a<br />CinemaBackground, and a surface that substitutes one is a surface<br />that has DISPLAYED A FAKE.
2. THE GALLERY OWNS THE DECLARATION AND THE REFERENCE<br />IMPLEMENTATION; THE APP OWNS THE RENDERING. The gallery holds<br /><code>module.json</code> — the four controls
(<code>animation_type</code>, <code>colors</code>, <code>speed</code>,<br /><code>blur</code>) — and the reference scene model and painter; the app<br />holds the renderer. ⇒ This is the split every other widget already<br />lives with, and a renderer that reads its controls from anywhere<br />else has a second source of truth.
3. THE CONTROLS ARE READ FROM THE GALLERY REGISTRY ENTRY, NOT FROM A<br />LOCAL COPY. The renderer reads them through<br /><code>getModuleDef('cinema-background')</code> — the gallery's own<br /><code>fieldSchema</code> projection — and passes no palette of its own.
4. THE SCENE IS SCENERY AND NEVER A HIT TARGET. A Page-Level<br />background sits behind ALL content, so it carries<br /><code>pointer-events: none</code>. ⇒ A background that swallows clicks<br />is a regression at the Page level, not a styling choice.
5. THE SCENE IS ANIMATED, AND A STILL SCENE IS NOT THE SCENE. The<br />renderer's resize rebuilds the SAME scene from a seed — an unseeded<br />generator makes every resize a different picture, and a picture that<br />changes under the operator's hand is not the scene they were shown.
6. THE PAGE OWNS THE BACKGROUND, AND THE LEVEL DECIDES THE<br />ANCESTOR. Page-Level is <code>position: fixed</code> against the<br />viewport and scrolls independently of the content; Section-Level and<br />Widget-Level are <code>position: absolute</code> against their<br />nearest positioned ancestor and move with it. ⇒ A background authored<br />at the wrong level cannot be rescued by a different <code>z-index</code>.
7. MEASURED: the Page module shipped with ZERO importers and the live<br />bundle carried 0 occurrences of <code>fv-cinema-background</code>, so<br />the widget never ran. The Dashboard route now mounts it and the<br />preview canvas mounts it, and both paint the real scene.

## Part 63: The Stencil Lifecycle

1. THE STENCIL'S UI IS EPHEMERAL AND ITS RECIPE IS PERSISTENT. A<br />Stencil is a working surface: it is opened, examined, and either<br />approved or discarded. Nothing about the surface survives the<br />session.
2. A CANDIDATE RECIPE IS A PERSISTED ARTEFACT, NOT A RENDERING. The<br />Stencil's output is the Recipe and the diff; the UI is how they are<br />reviewed. ⇒ A Stencil that persists its own markup persists a<br />rendering instead of a recipe, and the pipeline loses its input.
3. THE APPROVAL GATE IS THE ONLY WAY A CANDIDATE BECOMES SHIPPPED.<br />Approve or discard, and nothing else. ⇒ A Stencil that can write<br />itself into the live surface has skipped the gate that exists to<br />stop exactly that.
4. THE STENCIL IS EPHEMERAL IN THE SENSE THAT IT LEAVES NO SURFACE<br />BEHIND. A closed Stencil is not a hidden Stencil: it is not in the<br />DOM, it holds no listener, and it keeps no timer. ⇒ A surface that<br />is merely invisible is still a surface, and it still costs.
5. THE RECIPE AND THE DIFF ARE THE TWO THINGS A REVIEWER READS. The<br />Stencil's value is the pair — what the Recipe says, and what would<br />change — and a surface that shows one without the other is a<br />half-measure.

## Part 64: The Home Project

1. THE HOME PAGE IS NOT HARDCODED; IT IS A VIBECODER PROJECT WITH ID<br /><code>vibecoder-home</code>. ⇒ The Home Page is an ordinary project that<br />happens to be the entry point, and a rule that holds for every other<br />project holds for it: the same record, the same Recipe, the same<br />Stencil, the same authority. ⇒ A Home Page written as a component is a<br />surface that cannot be edited the way a project is edited, and an<br />operator who cannot edit the entry page has no way to fix it.
2. WHEN THE URL IS <code>/</code>, THE SHELL LOADS THE<br /><code>vibecoder-home</code> RECIPE. ⇒ The route table's <code>home</code><br />view resolves to a project id, and the Shell renders that project's<br />Recipe through the same reader every project view uses. ⇒ A route that<br />resolves to anything else is a second Home Page wearing the first<br />Home Page's URL, and the operator edits one of them.
3. THE HOME PROJECT CAN BE EDITED USING THE STENCIL. ⇒ The Home<br />Project's Recipe is a persisted, recipe-book-shaped artefact that the<br />Stencil can open, examine and propose a diff against, and it passes the<br />same approval gate every other candidate passes (Part 63). ⇒ A Home<br />Project that is editable only by editing code has one editing model,<br />not the model the product promises.
4. THE PROJECT ID AND THE RECIPE TREE SHARE ONE IDENTITY. A project's<br />page tree is addressed by the project's own id — the browser reads<br /><code>/api/agent/tree/&lt;projectId&gt;</code> — and the project's record<br />is addressed by <code>project:&lt;projectId&gt;</code>. ⇒ One id names<br />the project, its tree and its Recipe, and a reader needs no mapping<br />table to find them.
5. A PROJECT'S RECIPE MUST BE REACHABLE BY THE SURFACE THAT RENDERS<br />IT. A tree that exists in the FC Brain but that the renderer cannot<br />fetch is not a Recipe; it is a record. ⇒ The canvas reads the tree for<br />the project the route resolved, and a route that resolves to an<br />unreadable project renders an explicit empty state rather than a<br />silent blank.
6. THE HOME PAGE'S PROJECT GRID READS THE USER'S PROJECTS THROUGH THE<br />SHARED PROJECT READER, AND ITS "NEW PROJECT" BUTTON OPENS THE<br />SHARED CREATE-PROJECT ACTION. ⇒ The Grid and the Projects panel read one<br />source and cannot disagree about what the user has, and the Home Page<br />carries no second project-creation path. ⇒ A Grid with its own fetch is a<br />list that can differ from the one the user manages their work in.
7. MEASURED: the FC Brain held no tree at <code>vibecoder-home</code>, and<br />the canvas's tree reader hydrated only the eighteen bundle page keys at<br />boot — so a tree written at a project's own id was unreachable by the<br />surface meant to render it. The Home Project's tree is now written<br />through the FC adapter and read by the same route every project view<br />uses.

## Part 65: The FCr Dependency

1. VibeCoder pins freshcards to a TAGGED RELEASE THAT CARRIES A
   <code>dist/</code> FOLDER. ⇒ A tag that resolves to source gives the
   consumer a tree it must build; a tag that carries <code>dist/</code>
   gives it the published package. ⇒ A pin without a <code>dist/</code> is
   a pin that asks every consumer to be a build system.
2. THE WORKSPACE USES A REAL <code>node_modules</code> DIRECTORY, NOT A
   SYMLINK FARM. ⇒ npm installs INTO the directory it is pointed at; a
   <code>node_modules</code> that is a symlink to another repo's is a
   directory the installer did not create and does not own. ⇒ A symlink
   farm makes <code>npm install</code> write into somebody else's tree.
3. A PREFLIGHT CHECK FAILS THE BUILD IF THE PIN IS BROKEN OR THE
   <code>dist</code> IS MISSING. ⇒ The check reads the INSTALLED package,
   not the declared range: the declared range and the installed artefact
   are two different claims, and only the second one is what the build
   consumes.
4. THE PIN IS A PAIR: <code>package.json</code> AND
   <code>package-lock.json</code>. ⇒ npm resolves a git dependency from
   the LOCKFILE's <code>resolved</code> commit and honours it even when
   <code>package.json</code> names a different tag — and it says NOTHING.
   ⇒ A bump applied to <code>package.json</code> alone is a silent no-op,
   and a no-op that prints no warning is the kind that gets believed.
5. MEASURED: the installed freshcards was <code>2.21.2</code> while
   <code>package.json</code> named <code>v2.25.0</code>, because the
   lockfile resolved <code>6be98b00</code> (the v2.21.2 tag) and npm
   reported "up to date". ⇒ The lockfile entry had to be removed and
   regenerated before npm would move. ⇒ A pin is a lockfile entry, not a
   range.

## Part 68: The Test Loop Trap

1. WHEN A TEST FAILS AFTER A FIX, THE AGENT MUST DETERMINE WHETHER THE
   FAILURE IS A REAL REGRESSION OR A PRE-EXISTING CONTRACT. ⇒ The two
   demand OPPOSITE actions — one is repaired in the code, the other in the
   test — and a failure that is not classified is a failure that is about to
   be "fixed" in the wrong place.
2. IF THE TEST IS A PRE-EXISTING CONTRACT — e.g. it was written to enforce
   a rule that the fix is changing — THE AGENT MUST UPDATE THE TEST, WITH A
   COMMENT EXPLAINING WHY. ⇒ The comment is not decoration: it is the only
   thing that tells the next reader that the test's expectation was
   deliberately changed rather than accidentally broken. ⇒ A test updated
   without a reason is indistinguishable from a test weakened to make a
   build go green.
3. IF THE TEST IS A REAL REGRESSION, THE AGENT MUST FIX IT. ⇒ Not the
   test. The code. ⇒ A regression is the fix having broken something that
   worked, and editing the test that noticed it is how a regression becomes
   permanent.
4. AGENTS ARE FORBIDDEN FROM WRITING NEGATIVE CONTROLS FOR SCRIPTS THAT
   SELF-VERIFY — e.g. a manifest check that confirms the manifest matches
   the source. ⇒ SELF-VERIFYING SCRIPTS ARE THEIR OWN PROOF. ⇒ A check
   that regenerates the artefact and compares it byte-for-byte already
   proves what a hand-written test of that check would assert; a negative
   control for it needs a deliberately-broken fixture, which is a second
   source of truth about what "broken" means, maintained to be wrong.
5. MEASURED: the shipped registry check
   `scripts/build-module-index.mjs --check` regenerates
   `app-registry/modules.index.json` from the module manifests and compares
   it byte-for-byte. ⇒ It is its own proof, and **no test of it exists**
   — deliberately, under clause 4. ⇒ A negative control would have to
   commit a deliberately-stale registry to be broken against, which is a
   second, permanently-wrong description of the thing the check verifies.
6. MEASURED: the two classifications above are not hypothetical. A
   dashboard test pinned the OLD contract — "a card with NO widget says so
   rather than go blank" — and the fix made that contract false. The
   contract was updated, and the reason was written into the test with the
   measurement that justified it. ⇒ A second test pinned the OLD CARRIER
   for a set of values (the CSS custom properties that carried a CSS-only
   approximation), and was updated the same way when the values moved to
   the widget that actually reads them. ⇒ In both cases the INTENT was
   preserved and the CARRIER changed, and the reason was recorded so that a
   later reader could tell a deliberate change from a quiet weakening.
7. ⇒ ⇒⇒ **A TEST THAT FAILS AFTER A FIX IS A QUESTION, NOT A VERDICT.**
   The question is which of the two it is. ⇒ An agent that answers the
   question by editing whichever file is easiest to edit is not solving
   the problem; it is moving the evidence.
8. ⇒ ⇒⇒ **THE 15-MINUTE BOUNDARY IS IN RULE 4, AND THIS PART IS ITS
   REASON.** A classification that cannot be made in fifteen minutes is
   not a classification the agent is going to make; it is a STOP
   condition. ⇒ The agent reports the failure, names what it could not
   determine, and does not write a new test to chase it.

### 68.1 The Numbering Gap

⇒ **⇒⇒ THE PART NUMBER IS THE DISPATCH'S, VERBATIM.** The dispatch named
"Part 68", and that name is what appears above. ⇒ The dispatch's own
numbering is PRESERVED rather than rewritten to 66, because renumbering
would silently rewrite the dispatch's text — and the gap is recorded here
so that no reader assumes the numbering is contiguous. ⇒ This follows the
precedent already set by PREMISE CORRECTION 1 in this spec, and by
Part 62.5, which recorded the same kind of gap the same way.

⇒ ⇒⇒ **PARTS 66 AND 67 ARE VACANT.** When this Part was written the
spec's last Part was 65, and Parts 66 and 67 were unallocated. ⇒ NO file
anywhere in the repository references them. ⇒ The spec's numbering runs
contiguously from Part 41 to Part 55, then Part 61, Part 62, Parts 58 to
60, Parts 63 to 65, then this Part.

## Part 69: The Panel Layout Reality

1. The Panel Layout System was split into panel-shell,
   panel-floating, and panel-dom by FVC 1220. There is
   no 'panel-layout' recipe.
2. The Generator cannot dock panels. It only emits
   in-flow grid areas (no position: fixed).
3. Docking is currently achieved by inset (padding) on
   the Canvas, not by a Recipe.
4. The VibeChat panel is a bottom sheet by design. The
   window controls are intentional on desktop. Do not
   remove them.

### 69.1 The Measured Basis

Every item above was MEASURED on 2026-10-27 against the repository at
<code>7f41e2db</code>. It is not inferred from a name.

- MEASURED: <code>src/modules/</code> contains <code>panel-shell</code>,
  <code>panel-floating</code>, <code>panel-dom</code>,
  <code>panel-registry</code>, <code>layers-panel</code> and
  <code>properties-panel</code>. There is no
  <code>src/modules/panel-layout/</code> directory, and of the five
  <code>recipe.json</code> files in the repository none mentions a panel.
  ⇒ The split is real and the recipe does not exist.
  ⇒ <b>ONE NUANCE, RECORDED SO A LATER READER IS NOT MISLED:</b>
  <code>src/cms/cms-local.panel-layout.schema.json</code> EXISTS — it is a CMS
  schema, not a Recipe, and it is not a layout model. The module registry
  also still records <code>"parentModuleId": "panel-layout"</code> for
  <code>panel-shell</code>, <code>panel-floating</code> and
  <code>panel-dom</code>. ⇒ The name survives as a PARENT ID and a schema
  name, which is exactly why a search for "panel-layout" returns hits that
  are not a layout model.
- MEASURED: <code>src/modules/generator/src/generate-react.cjs</code> emits
  <code>grid-template-columns</code> and <code>grid-template-areas</code>, and
  the string <code>position: fixed</code> appears ZERO times in that file;
  <code>position</code> appears only as <code>relative</code> and as
  <code>absolute</code>. ⇒ The Generator can lay a panel out IN FLOW and
  cannot dock one.
- MEASURED: <code>src/shell/Shell.tsx:638-644</code> defines
  <code>.fv-shell[data-fv-deck-open='true'] .fv-shell-canvas</code> with
  <code>padding-right: var(--fv-deck-outer-width)</code>, and the assets
  equivalent with <code>padding-left</code>. ⇒ Docking is an INSET on the
  Canvas, driven by state on the shell root, and no Recipe positions a
  panel. ⇒ The same idea appears in the panel's own squeeze mode, which
  pads the BODY — <code>src/modules/panel-floating/src/panel-floating.css:736-762</code>.
- MEASURED: <code>src/vibechat/VibeChat.tsx:232-238</code> states that the
  desktop sheet keeps its window controls and the mobile sheet renders none
  of them, and the file defines <code>DETENTS</code> and
  <code>MOBILE_DETENTS</code>. ⇒ The four desktop controls are a DESIGN
  DECISION, and removing them would delete working controls.
- ⇒ <b>THE PART NUMBER IS CONTIGUOUS.</b> Part 69 follows Part 68 directly.
  Parts 66 and 67 remain vacant, and that gap is already recorded in
  Part 68.1 — it is not repeated here, following PREMISE CORRECTION 1.

## Part 70: The Dead Header Controls

1. A CONTROL THAT RENDERS, IS CLICKABLE, AND CHANGES NOTHING IS DEAD. ⇒
   The generated Header's `?.` calls make a missing callback SILENT: the
   button draws, the pointer lands on it, and nothing happens. ⇒ A dead
   control is not a cosmetic defect; it is a promise the app breaks
   silently.
2. THE SHELL SUPPLIES EVERY CALLBACK THE GENERATED HEADER CALLS. ⇒ The
   generated Header declares eleven optional callbacks. ⇒ The Shell
   passes eleven. ⇒ A callback the Shell has no honest value for is not
   passed as a lie — it is IMPLEMENTED, because a control that is rendered
   must be a control that works.
3. THE DEVICE, THE THEME AND THE SKIN ARE THE APP'S OWN STATE SURFACES. ⇒
   The device is `data-fv-device` on the Shell root, the theme is
   `data-fv-theme` on the document root, and the skin is `data-fv-skin` on
   the document root. ⇒ The Header reads the same values back through its
   props, so the control and the app cannot disagree. ⇒ The Shell
   OBSERVES these attributes with a MutationObserver rather than keeping a
   second copy, exactly as it observes the theme and the deployment flag.
4. THE TWO MENUS ARE MUTUALLY EXCLUSIVE. ⇒ The theme menu and the skin
   menu are both popovers under one header. ⇒ Opening one closes the
   other, because two open popovers under one header is a menu that
   opened twice. ⇒ And a click on the canvas closes whichever is open.
5. THE MENU OPTIONS ARE THE CODEX'S. ⇒ The Header's Codex names
   `default, cyberpunk` for the ThemeSelector and `default, glass,
   brutalist` for the SkinSelector. ⇒ The menu renders exactly those, and
   `default` REMOVES the attribute rather than setting it to the word
   "default" — because the token library's default IS the `:root` block
   itself, and a "default" that set the attribute would make the
   library's own default theme unreachable.
6. A STATE ATTRIBUTE AND AN ELEMENT ATTRIBUTE MUST NOT SHARE A NAME. ⇒
   The Shell root publishes `data-fv-theme-menu="true"` to say WHICH
   MENU IS OPEN, and the menu element is named
   `data-fv-theme-menu-panel`. ⇒ A menu element named
   `data-fv-theme-menu` would be matched by the very query that asks "is
   the theme menu open?", and the query would answer about the root's
   state and the panel at once. ⇒ MEASURED: a harness counting
   `[data-fv-theme-menu]` counted TWO elements and reported a menu that
   had closed as still open.
7. A DISMISS LAYER MUST NOT COVER THE CONTROLS IT DISMISSES. ⇒ The
   dismiss layer starts BELOW the header's own height (56px, the
   Recipe's `layout.style.height`). ⇒ MEASURED: the first version
   covered the whole shell, and the Skin Selector became unclickable
   while the theme menu was open — the layer intercepted the pointer.
8. A CONTROL'S EFFECT IS WHAT PROVES IT ALIVE. ⇒ Every assertion about
   a Header control is about the URL that changed, the attribute that
   changed, the panel that opened, or the menu that appeared — never
