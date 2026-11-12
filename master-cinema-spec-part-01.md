# The Master Cinema Spec

**The blueprint for the World-Class Flash Alternative.**

The Cinema Editor is VibeCoder's visual authoring tool — the replacement for the Flash IDE. It is
where a creator builds a *scene*: lays out geometry, paints it, lights it, and sequences it over
time, and it is a first-class surface of the application rather than a panel bolted onto one.

This document is the normative blueprint for that surface. It defines the Cinema's identity, the
VSIL substrate it reads and writes, the layer stack it composes, the renderer pipeline that
compiles it, the rule that separates procedural work from generative work, and the editor UI that
manipulates it.

**A note on what this document is — its status, stated up front.** Parts 81.1–81.6 state what the
system MUST be. They are requirements, not descriptions. Where a construct does not exist in VSIL
today, this document says so and specifies it as new work; it does not pretend. §81.7 records the
measured gap against the tree as of the writing, so a build agent knows the size of the work and
can measure progress against it. **Nothing in Parts 81.1–81.6 is weakened, qualified, or satisfied
by anything recorded in §81.7.**

**This Part is a PROPOSAL, not a ratified standard.** The VSIL specification it builds on describes
itself as *"Provisional — a draft awaiting formal ratification"*, and its Pact §5 reserves the
creation and evolution of profiles to the operator: *"New profiles require operator ratification
before they may be used in production."* Part 81 therefore **proposes** a Cinema architecture. It
does not enact one, it does not carry the authority of a ratified profile, and it MUST NOT be cited
as though it did. The mandates are real mandates **of this document**; ratification is a separate
step that this document does not perform. Two things follow, and both are binding on a reader:

- **A requirement in Part 81 is a requirement to BUILD, not a requirement that is already met.**
  Where §81.7 records a gap as OPEN, the gap is open.
- **A construct this Part specifies into existence — VSIL-P's field list, masks, post-processing —
  remains UNRATIFIED until the operator ratifies it.** The spec says what the construct must
  contain; it does not confer the standing to emit it. §81.2 and §81.3 make that boundary explicit
  where it matters.

---

## 81.1 The Cinema Identity

The Cinema Editor MUST be the visual authoring tool of VibeCoder and MUST be reachable as a
first-class surface on a real route. It is the successor to the Flash authoring environment: a
single workspace in which a creator composes a timeline, arranges layers, inspects and edits
properties, and previews the result, with every authoring action persisted as data rather than as
pixels.

The Cinema's document type MUST be the `movieClip` construct, which the VSIL `cinema` profile
already owns for cinematic sequencing. A Cinema document MUST be a VSIL document: it MUST satisfy
`vsil:core` — `id`, `version`, `scene`, `assets`, `render:options`, `animation`, `audio` — and it
MUST declare the profile namespaces it uses.

The identity obliges the platform to provide:

- **A route.** The Cinema Editor MUST be mounted on a route a user can navigate to. A surface that
  no route reaches is not a surface.
- **A document type.** A `.movieClip`-shaped VSIL document MUST be the unit of authorship, and the
  platform MUST be able to open, edit and save one.
- **A save path.** Edits MUST persist as VSIL, not as renderer state. The renderer's output MUST
  be reproducible from the document alone.
- **An undo model.** Every authoring action MUST be reversible, and the undo stack MUST be scoped
  to the Cinema document.

**The gap, stated plainly.** The Cinema Editor's implementation exists in the tree but is not
mounted on any live route, so none of it can be exercised by a user. A Recipe carries no VSIL
document at all — the string `vsil` occurs zero times in a Recipe, and the generator reads only
`recipe.json` and `codex.json`. The VSIL implementation itself lives at the repository root and in
`bridge/` and is imported by backend sites only; the application entry imports none of it. The
Cinema's identity is therefore **specified but unbuilt at the platform level**, and §81.7 records
the measurements.

---

## 81.2 The VSIL Foundation — Core, VSIL-A, VSIL-P

The Cinema Editor MUST read and write VSIL, and MUST do so through the profile system:
`VSIL v1.0 = vsil:core + vsil:profile:<surface>`. The core namespace is mandatory in every
document and every profile extends it. A Cinema document that omits the core is invalid.

**Core.** Every Cinema document MUST carry the core constructs: `id` (a globally unique,
URI-encoded identifier), `version` (semantic, required), `scene` (the coordinate system and
bounding volume), `assets` (the asset reference model), `render:options` (rendering flags),
`animation` and `audio`. Geometry MUST come from the core's geometry and transform constructs, and
the style of every renderable primitive MUST come from the core Style profile, which is itself
mandatory in every document.

**VSIL-A (animation).** VSIL-A is fully specified and the Cinema MUST read and write animation
against its contract, not against a private dialect. Animation MUST use the global `time` axis in
seconds with a positive `duration`, and every track MUST be bounded within `[0, duration]`. A
keyframe MUST carry `time` and `value` and MAY carry `in:tangent` and `out:tangent`; a track MUST
carry a `type` drawn from the seven defined types — `float`, `vec2`, `vec3`, `colour`, `path`,
`string`, `discrete`. Interpolation MUST be `linear` (the default), `bezier` or `hold`, and easing
MUST be one of `easeIn`, `easeOut`, `easeInOut`, `linear`, or a custom cubic-bézier of four control
points, and MUST be continuous and monotonic.

**VSIL-P (paint).** VSIL-P is declared, registered and validator-recognised, and it is
**unspecified**: its entire definition is one sentence in the Pact — *"Adds procedural texture
definitions, compositing layers, and material properties."* There is no field list, no schema and
no operational semantics. **This document therefore specifies VSIL-P as new work.** Before any
paint field is emitted into a Cinema document, the following MUST exist:

1. **A ratified VSIL-P specification.** The profile MUST have a specification document in the VSIL
   repository on the same footing as VSIL-A, defining its fields, their types, their defaults and
   their validation rules.
2. **A registry entry.** VSIL-P MUST be registered in the profile registry and in the extension
   validator's known-profile set *with* its field definitions — not merely by name.
3. **A closure of the governance hole.** The validators currently accept the `vsil-p` profile
   identifier **structurally**, so a document that claims a paint profile passes validation while
   nothing defines its fields. The validator MUST reject a profile that is registered by name but
   whose field list is absent or unratified.

Two adjacent inconsistencies MUST be resolved by the same work. The `material` profile — which
`diffuse`, `specular`, `shininess` and `emissive` are attributed to — is invoked by the cinema
profile but is **not among the registered profile names** and has no specification document; it MUST
be registered and specified. And the core Style profile already owns fill, stroke, opacity and
blend, so **VSIL-P MUST extend the core Style profile and MUST NOT replace it** — profiles extend,
they do not replace.

---

## 81.3 The Layer Stack — Geometry, Animation, Paint, Light, Interface

The Cinema MUST compose a scene from an ordered layer stack. Each layer MUST be a VSIL node with
its own style, and style MUST be inherited by children unless explicitly overridden. The stack
MUST be composited bottom-up in the order below.

**1 — The Base Image.** The base layer carries the scene's assets. Assets MUST use the core asset
reference model: `{id, kind, uri}` with `kind` drawn from `image`, `texture`, `font`, `gradient`
and `svg`. Inline data URIs MUST be used only for `image` and `svg`. Bitmap embedding MUST appear
only in the `vibecoder-container` profile. An asset reference that cannot be resolved MUST produce
a deterministic error and a predefined placeholder — never a silent omission.

**2 — Geometry.** The shapes of the scene, from the core's geometry and transform constructs,
carrying their own style.

**3 — Animation.** VSIL-A tracks applied to any layer above. Animation is a property of the layer
it animates, not a separate band in the stack, and a layer MUST be able to carry several
simultaneous tracks of different types.

**4 — Paint.** The paint layer — specified by VSIL-P (§81.2) — carries compositing layers. Its
fields MUST compose with the core Style profile: a fill is a solid RGBA colour or a gradient
(`linear`, `radial` or `conical`) with a `stops` array; opacity is a scalar in `[0,1]` applied
after colour blending and before compositing; the blend mode is one of `normal`, `multiply`,
`screen`, `overlay`, `darken`, `lighten`, defaulting to `normal`, and is applied after opacity and
before the primitive is written to the framebuffer.

**5 — The Lighting / Filter overlays.** The cinema profile's illumination, plus post-processing.
Lights MUST use the cinema profile's own definitions: ambient light carries a single RGBA `colour`
whose alpha is ignored; directional light carries a normalised `direction`, `colour` and
`intensity`; point light carries `position`, `colour`, `intensity` and a positive `range`, with
quadratic falloff `attenuation = 1 / (1 + (d/range)^2)`; area light carries `position`, two
orthogonal axes `u` and `v`, a `size`, `colour` and `intensity`, and its contribution MUST be
computed by sampling the rectangle, defaulting to a uniform grid and overridable through a
`sample` field. A light MAY carry a `shadow` object — `enabled`, `resolution`, `bias`, and an
ascending `cascade` of split distances. The camera MUST use the cinema profile's camera
construct: `position`, `look:at` and `up` (with `up` non-zero and not colinear with the view
direction, and `position` and `look:at` distinct), a `projection` that is either `perspective`
(`fov`, `aspect`, `near`, `far`) or `orthographic` (`left`, `right`, `bottom`, `top`, `near`,
`far`) with `near` < `far` and all clipping planes positive, and a `FrameState` capturing the view
matrix, the projection matrix and the viewport dimensions, with `frame:state(t)` returning the
interpolated camera state.

**6 — The UI floats.** The interface layer that rides above the scene — panels, handles, and the
overlay chrome of the authoring tool itself. The UI floats MUST NOT be composited into the scene
graph; they are a presentation layer over it, and they MUST be excludable from a render.

**Two constructs the stack requires that VSIL does not have.** There is **no mask construct**
anywhere in the VSIL specification, and **no post-processing**. The Cinema's layer stack requires
both. Therefore:

- A **mask** MUST be specified as a VSIL-P field, and MUST define its own resolution order against
  the layer stack.
- **Post-processing** MUST be specified as a cinema-profile filter pass, with its own ordered
  application relative to the lighting overlays.

Neither may be smuggled in as an undeclared field. Until both are ratified, the Cinema MUST refuse
to emit them rather than emit something the validator cannot check.

---

## 81.4 The Renderer Pipeline — DOM/CSS, Canvas, WebGL

The Generator MUST compile a Cinema document into a running scene through a **tiered renderer**, and
the tier MUST be chosen by a single declared rule rather than by ad-hoc judgment at each call site.

**Tier 1 — DOM/CSS.** The default tier, and the tier the Generator already implements: a
Recipe is compiled into DOM with inline styles. CSS can express fills, gradients, opacity and the
six blend modes, which is exactly the subset the core Style profile specifies. The DOM/CSS tier
MUST be used whenever the scene is expressible in the core Style profile alone.

**Tier 2 — Canvas 2D.** For procedural work that CSS cannot express. The repository contains
**exactly one** real Canvas 2D implementation, and it establishes the discipline the Cinema MUST
adopt:

- The canvas MUST be created imperatively and MUST carry a stable class and `data-*` attributes
  describing its animation type, so it is identifiable in the DOM.
- The 2D context MUST be taken as a **parameter**, never acquired internally by the painting
  function. A test environment returns `null` from `getContext('2d')`, and a painter that acquired
  its own context would take a bail-out branch and "pass" while asserting that nothing rendered.
- The device-pixel ratio MUST be capped. A background that drops frames has failed at its only job.
- **A missing context MUST be reported in the DOM** — `data-fvcms-cinema-state="no-context"` — and
  MUST NOT be silently swallowed. A renderer that fails invisibly looks exactly like a renderer
  that succeeded and drew nothing.

That last rule is the pipeline's honesty contract and applies to every canvas surface.

**Tier 3 — WebGL.** The repository contains **zero** WebGL today. WebGL MUST be the tier for the
camera and lighting model: perspective and orthographic projection, the four light types with
quadratic attenuation, and shadow maps are GPU work that CSS cannot express and that DOM cannot
compose. The WebGL tier MUST provide:

- A real canvas surface with an explicit, handled **context-loss** event. A lost context that is
  not handled is a black screen with no error.
- A **shader-per-pass** model, so that each lighting and filter pass is a discrete, testable unit.
- A **DOM fallback** for the case where WebGL is unavailable or the context is lost, so that the
  scene still renders.

**The tier-selection rule.** A scene MUST be compiled to the **lowest tier that can express it**:
DOM/CSS when the core Style profile suffices; Canvas 2D when procedural computation is required;
WebGL when the camera or lighting model is present. A scene MUST NOT be promoted to a higher tier
for convenience, and a scene MUST NOT be demoted below what its content requires.

---

## 81.5 Procedural vs. AI

The Cinema MUST distinguish work that is computed from work that is generated, and MUST route each
to the mechanism that can carry it honestly.

**Procedural — CSS and Canvas mathematics.** Fog, grain, glows, gradients, bloom, starfields,
light attenuation and shadow softness are all *mathematics over a known parameter set*. They MUST
be computed, not generated: they are reproducible, they are parameterised, and they cost no
network call. The core Style profile's gradients and six blend modes, the cinema profile's shadow
descriptors and attenuation model, and the one real procedural canvas implementation all belong
here.

**Generative — an AI image generator.** An AI image generator MUST be called only when the
requested result is *not derivable from parameters* — an original illustration, a photoreal
backdrop, a texture that does not exist in any registry.

**The constraint that governs the choice.** The widget registry measures **45 widgets and 269
declared properties**, and it has **zero** properties of type or name `gradient`, `shadow`, `font`,
`fontSize`, `fontFamily`, `lineHeight` or `letterSpacing`. **The Recipe has nowhere to put a
gradient, a shadow or a typeface.** This is precisely why the Vision Extractor cannot emit them: its
artefact carries one widget where three were asked for, and mentions no cinema, glow, shadow or
blur at all. The registry, not the model, is the binding constraint.

Therefore the following workflow is MANDATORY, and the order is the rule:

1. **The effect becomes a registry property.** A visual effect MUST be added to a widget's schema
   *before* any generative model may emit it. The schema is the permitted vocabulary.
2. **The schema is validated.** The new property MUST pass the schema validation, or the effect is
   not available to the model.
3. **Only then may the AI generator target it.** The generator maps extracted visual properties
   onto registry properties, and a property that resolves to nothing in the registry is not a
   mapping.
4. **What could not be mapped MUST be reported, not silently dropped.** An image is a whole; a
   Recipe is a set of widgets with declared properties. The unmappable parts — the gradients, the
   shadows, the typefaces — are the operator's evidence for the next registry change, and they
   MUST appear in the output rather than vanish from it.

**Cost, latency and caching.** A generative call is the only part of the pipeline with material
latency and marginal cost, so it MUST be bounded. The Cinema MUST cache every generation by the
hash of its prompt plus its seed, so that a re-render of an unchanged scene issues **no** new
generative call. A scene MUST declare its generative assets, so the cost is visible before it is
incurred, and a failed generation MUST leave the scene renderable with a deterministic placeholder —
the same honesty rule §81.4 imposes on a missing canvas context.

---

## 81.6 The Editor UI — Timeline, Properties Panel, Layers Panel

The Cinema's editor UI has three surfaces, and they MUST agree with each other about what is
selected, because the selection is the single thread that runs through all three.

**The Timeline.** The timeline **exists and is substantial** — sixteen files and 3,828 lines, with a
scrubber, keyframe tracks, playback controls, a scene switcher, sub-thread panels, keyframe
markers and a curve preview. It is, however, bound to the **DNA document** rather than to VSIL-A:
the module contains **zero** `vsil-a` references, the panel reads `node.animation` off a tree node,
and the keyframe controller wraps a DNA animation API.

That binding is **debt**, and the Cinema MUST pay it. The timeline MUST be re-bound to the VSIL-A
keyframe contract:

- A keyframe MUST carry `time` and `value` and MAY carry `in:tangent` and `out:tangent` — not the
  current `t`/`value`/`easing` shape.
- A track MUST carry a `type` drawn from the seven defined types. **Today exactly one of the seven
  is representable**, because the current shape admits only a scalar-or-string value.
- Easing MUST be the four named easings **plus** a custom cubic-bézier, and MUST be continuous and
  monotonic. The current four hardcoded easing names are a subset, and they are not the contract.

**The Properties Panel.** The properties panel is live and is a **group/field** model — a
`fieldSchema` mapping properties to field specs, plus an `inspector` mapping group names to
property lists. The strings `bucket` and `slot` occur **zero times** in all four live recipe-books,
while the Master Specification's Part 10 defines a thirteen-bucket, slot-and-control model. The
Cinema's inspector MUST therefore:

- **Expose the cinema profile's own fields** — camera, lights, materials, blend — and MUST NOT
  invent a parallel vocabulary for them.
- **Resolve by both id spaces.** The selection state carries a **region** id, because selecting a
  node delegates to the region setter; a lookup that matches only the **node** id silently fails to
  resolve a widget that is plainly on screen. The Cinema MUST resolve a selection by **both** the
  node id and the region id. This is a known failure mode that has already been fixed once; the
  Cinema MUST NOT repeat it.

**The Layers Panel.** The layers panel is live, interactive, and selects on the region axis. The
Cinema's layers panel MUST show the layer stack of §81.3 — not a flat list of widgets — and MUST be
the **single selection source** for both the timeline and the properties panel. Two panels that
each hold their own selection are two contracts that drift.

**The mount requirement.** The Cinema Editor MUST be mounted on a real route. Its
`DocumentSurface` is currently imported **only by test files**; no production module imports it.
An unreachable editor cannot be exercised by a user, and nothing in this Part may be considered
delivered until the surface is reachable.

---

## 81.7 The Gap Against the Blueprint (measured, not law)

The mandates in Parts 81.1–81.6 state what the Cinema MUST be. This section records what the tree
measured **at the time of writing**, so a build agent knows the size of the gap and can measure
progress against it. **This section is a measurement, not a requirement. Nothing in Parts 81.1–81.6
is weakened, qualified, or satisfied by anything recorded here.** A mandate that is already met is
still a mandate.

Measured against `origin/main` `5b047fb0`.

| # | The mandate | The tree, measured | Gap |
| --- | --- | --- | --- |
| 1 | §81.1 the Cinema Editor is mounted on a route | `src/modules/cinema-viewport/src/editor/VSILEditor.tsx` (724 lines) and `DocumentSurface.tsx` exist; `DocumentSurface` is imported **only** by `__tests__` files — **zero** production importers | **OPEN** — the editor is unreachable |
| 2 | §81.1 a Recipe carries a VSIL document | the generator reads `recipe.json` and `codex.json` only (`generate-react.cjs:561-569`, `:823-824`); a Recipe is `{component, version, layout, slots}`; the string `vsil` occurs **0** times | **OPEN** |
| 3 | §81.1 `movieClip` is the document type | the `cinema` profile owns the `movieClip` construct in the VSIL spec; the tree has **0** references to it | **OPEN** |
| 4 | §81.2 VSIL-P has a ratified field list | `vsil-p` is registered in `spec.md` §14, `rules.md:151` and both validators' `KNOWN_PROFILES`; its entire definition is `pact/pact.md:53` — one sentence; there is **no** `vsil-p.md` | **OPEN** — new spec work |
| 5 | §81.2 the validator rejects an unratified profile | `schema-validator.js`'s `PROFILE_REGEX` accepts `vsil-p` **structurally**, so a document claiming a paint profile passes validation with no fields defined | **OPEN** — a governance hole |
| 6 | §81.2 the `material` profile is registered | `spec.md` §10.6 attributes `diffuse`, `specular`, `shininess`, `emissive` to it; it is **not** among the nine registered names and has no spec document | **OPEN** |
| 7 | §81.3 the layer stack has masks | there is **no** mask construct anywhere in `spec.md` | **OPEN** — new spec work |
| 8 | §81.3 the layer stack has post-processing | there is **no** post-processing construct in `spec.md` | **OPEN** — new spec work |
| 9 | §81.4 the DOM/CSS tier renders the core Style profile | the generator emits **raw inline styles** (`react-emitter.cjs:906-974`) and a bare `<img>` (`:1342-1345`); it is a literal AST builder, not a component emitter | **PARTIAL** — styles, not VSIL |
| 10 | §81.4 the Canvas tier follows the honesty contract | **exactly one** real Canvas 2D, `src/modules/page/src/page/CinemaBackground.tsx` (475 lines): context taken as a parameter, DPR capped at 2, `data-fvcms-cinema-state="no-context"` reported | **MET** — for one surface |
| 11 | §81.4 the WebGL tier exists | **zero** WebGL hits repo-wide | **OPEN** |
| 12 | §81.5 a gradient can be expressed in a Recipe | the registry measures **45 widgets / 269 properties** with **zero** properties of type/name `gradient`, `shadow`, `font`, `fontSize`, `fontFamily`, `lineHeight`, `letterSpacing` | **OPEN** — the registry is the binding constraint |
| 13 | §81.5 the Vision Extractor emits the widgets it was asked for | `tools/fvc1249-extract.cjs` produces a real Recipe (`component: "VibeCoderUI"`) with **exactly one** widget (`Hero`) where the prompt named three, and **zero** mentions of cinema/glow/shadow/blur | **OPEN** |
| 14 | §81.5 the extractor consults the registry | `grep` for `cms-widgets-index` / registry in the extractor = **0** hits | **OPEN** |
| 15 | §81.6 the timeline is bound to VSIL-A | the timeline is 16 files / 3,828 lines with **zero** `vsil-a` references; it is bound to the DNA document; its keyframe is `{t, value, easing}` against VSIL-A's `{time, value, type}` plus tangents | **OPEN** — the re-binding is the work |
| 16 | §81.6 the properties inspector exposes the cinema fields | the live Codex is a **group/field** model; `bucket` and `slot` occur **0** times in all four live recipe-books, against Part 10's thirteen-bucket model | **OPEN** |
| 17 | §81.6 a selection resolves on both id axes | the region/node mismatch is **fixed** — `findWidget` now matches `w.id` or `w.regionId`, and the live Properties panel reports `data-fvc-properties-state="ready"` | **MET** — and the Cinema MUST NOT regress it |
| 18 | §81.6 the layers panel is the single selection source | the Layers panel is live and selects on the region axis | **MET** |

**Three notes of fact, so the table is not misread.**

**The VSIL specification's own counts are stale in the same way.** The `cinema` profile is the most
complete profile in the VSIL repository, and it defines camera and lighting and `movieClip` — and
**no paint, no texture, no mask, no post-processing, no compositing layer, no layer stack and no
UI**. Every part of the stack in §81.3 above the geometry band is new specification work, not an
implementation gap in an existing spec. That distinction matters for planning: §81.3 is mostly a
*writing* task, while §81.4–81.6 are mostly *building* tasks.

**The Cinema Editor is a substantial but UNMOUNTED implementation.** This is the single most
important measurement in the table, and it is not a gap in capability. The editor, the timeline, the
layers panel and the properties panel all exist. They are simply not reachable, and the id-axis
mismatch that made the properties panel useless has now been fixed. **Mounting the editor is
therefore a smaller task than it appears** — and it is the gate that converts everything else in this
Part from specification into product. Note the limit of the measurement: it establishes that the
implementation EXISTS and is NOT REACHABLE. It does not establish that the editor is feature-
complete, and a build agent should not read it that way.

**The FC Brain write path for `mission_control` is already established.** The write route is
`PUT /api/agent/tree/:treeId` with `{"nodes":[...]}`, and the Master Specification's Part 26
already mandates it for the `mission_control` node. **No new API is to be invented, because none
has been.**

---

## 81.8 The Specification Sources

The measurements and definitions this Part rests on, and where they came from.

**The VSIL specification** lives in its own repository, `vsil-way-v1`, at `VERSION 1.1.0`, and its
README records its status as *"Provisional — this is a draft awaiting formal ratification."* Its
documents are `pact/pact.md` (the governance Pact, whose §5 is the profile registry),
`spec/spec.md` (core plus the abstract profile shapes), `spec/vsil-a.md` (the VSIL-A implementation
guide — node semantics, engine bindings, the canonical `PLATFORM` fragment id registry),
`rules/rules.md` (the validation rules) and the `validator/` CLI and library.

**The VibeCoder tree** was measured at `origin/main` `5b047fb0`. The Cinema's implementation lives
in `src/modules/cinema-viewport/` (the editor and the `VSILEditor`), `src/modules/cinema-timeline/`
(the timeline), `src/modules/cinema-core/` (the selection hook), `src/modules/cinema-tree/` (the
tree model, including the `AnimationKeyframe` shape), `src/modules/page/` (the one real Canvas 2D
surface) and `src/modules/properties-panel/` and `src/modules/layers-panel/` (the inspector and the
layer list).

**The FC Brain tree** `vibecoder-self` was read live and holds **42** nodes — `module` 9, `recipe`
9, `codex` 9, `rules` 8, `mission_control` 1, `credential` 6 — exactly one of them a
`mission_control` node. *Every measurement in §81.7 is re-runnable* with the commands shown in the
dispatch report for this release.
