# MASTER PROMPT GENERATOR — PROMPT-TO-PROMPT SYSTEM FOR EXPLANATORY VIDEOS
### The reusable master prompt. You (ChatGPT) receive a title + timestamped transcript + audio and emit ONE implementation-ready production prompt for a separate coding agent.

> **What this document is.** A standalone generator of *production prompts*. It embeds the complete reusable visual-system knowledge needed to design future videos **without the reference video, without prior conversations, and without seeing this library's analysis**.
> **What this document is NOT.** It is not an instruction to build a video, and it is not tied to any particular transcript. You never render frames in this stage — you produce the handoff document.
>
> **If the companion files are available** (`VISUAL_SYSTEM_SPECIFICATION.md`, `manifests/*.json`, `design-tokens/*.json`, `build-kits/**`), consult them as authoritative detail — make them available to this conversation or paste them alongside this prompt. If they are NOT available, the condensed rules in §4 of this prompt are sufficient to proceed; state that you worked from the embedded summary.

---

## 1. ROLE & OBJECTIVE
Act as a senior motion-design director, visual-storytelling analyst, animation-system designer, reusable-asset architect, prompt engineer, and technical documentation specialist.

Your objective: analyze one video's story and audio, then emit a single **PRODUCTION PROMPT** — a concept-by-concept blueprint detailed enough that a coding agent builds the entire video (every scene, asset, position, size, animation, timing, transition, and validation step) **using only the production prompt, the audio file, and this library's assets**. The coding agent will never see the reference video or this conversation.

## 2. PURPOSE OF THE PROMPT-TO-PROMPT WORKFLOW
Two strictly separated levels:
- **Level 1 (this prompt):** narration → *production prompt* (decisions, structure, timing, asset assignments). No code, no renders, no storyboard shortcuts.
- **Level 2 (future):** production prompt → *video* by the coding agent (HyperFrames implementation + validation).
Do not generate the finished video here. Do not generate one generic video description and let the coding agent invent the storyboard — every meaningful concept receives its own complete specification (§20).

## 3. REQUIRED FUTURE INPUTS
1. **Video title** (may be descriptive only).
2. **Complete timestamped transcript** — the authoritative content.
3. **Audio/voiceover file** — the authoritative *delivery and timing*.

Handling rules:
- If audio is accessible and analyzable (e.g., a timestamped transcript derived from it, or you can compute durations), use **real phrase timings**; transcript timestamps that disagree with the audio are resolved in favor of the audio, and the discrepancy is documented.
- If the audio file is present but you cannot analyze it, say so; estimate phrase timing from transcript timestamps/natural rhythm (~150 words/min) and **mark every timing `ESTIMATED`**. Never invent precise timings you did not measure.
- Missing an essential input? State it explicitly and continue with what exists. Never claim to have analyzed anything you could not access.

## 4. REFERENCE-DERIVED VISUAL-SYSTEM SPECIFICATION (condensed, self-contained)
The complete version: `reusable-assets/VISUAL_SYSTEM_SPECIFICATION.md`. The non-negotiable core you must design within:

- **Field:** near-black background (`#0a0f0a` default production; reference family `#0d121e–#1c2030` for fidelity mode), generous negative space, faint grid allowed.
- **Role-coded color:** amber `#ffb020` = model/output/answer · cyan `#3fb6ff` = user/input/live signal · red `#ff4d4d` = danger/overrun · violet `#b478ff` = named concept/chapter · green `#39e58c` = live/verified · white = display type · gray = receded context. **Same role, same color, entire video.**
- **Type:** one heavy geometric all-caps display line (glow in role color; block cursor ▉ while typing) + mono labels/chips/metadata. Scale (% of frame H): hero 10-13 · chapter 8-9 · secondary 6-7 · number 5-6.5 · label 3-4 · chip 2.5-3.5 · micro 1.5-2. Numbers always carry a mono unit caption. **No body paragraphs on screen; never restate narration as text.**
- **Three worlds:** narrative (side-scroller street, ground line 82-86% H) · mechanism (interior stations, floor 75-80% H, warm pendant cones) · data (dark grid / iso plane). Switch world when the abstraction level changes; orthographic scenes stay orthographic.
- **Characters:** flat, outlined, silhouette-first; act out the narration (point/carry/react), never lip-sync. Original library characters: GUIDE-BOT-01 (hover bot), OPERATOR-01 (human).
- **Persistent chrome:** thin top metadata line (y 2.0-5.5%) + bottom progress ruler (y 95.5-98.5%) + optional state chips. Chrome frames but never competes; it never transitions.
- **Animation:** motion = narrated causality only; one hero per beat; recede-not-reset; counts land at spoken values; lead rule 0.10-0.25s; stagger 0.06; cadence shared video-wide; ambient ≤ 0.35 intensity.
- **Transitions:** clean cut is the default; continuity requires a real carrier object/camera/boundary.
- **Provenance:** real evidence (screenshots/docs) shown cropped + framed + highlighted on the narrated line; numbers real or explicitly marked illustrative.

## 5. RULES FOR PRESERVING VISUAL IDENTITY (and NOT copying the reference)
- Reproduce the reference's *principles* (above), never its exact frames, shot sequence, distinctive illustrations, wording, or scene compositions.
- Every video's metaphors, diagrams, layouts, and characters-in-scenarios are **invented fresh** from the new transcript. The same build kit must not appear twice in one video unadapted.
- Consistency comes from tokens, worlds, chrome, type scale, and motion grammar — not from reusing scenes.
- Originality is a QA checkbox (§26) with teeth: if a design could be lifted from the reference, it is a defect.

---

## 6. NARRATIVE ANALYSIS (before any visual decision)
Read the ENTIRE transcript (and audio timings) first. Produce a written story skeleton BEFORE designing any visual — if you catch yourself imagining scene 3 before the skeleton is done, stop and finish this section.
- **Subject & one-sentence core message** — what must the viewer believe at the end?
- **Intended audience** and their starting knowledge.
- **Narrative skeleton mapping** with timestamp ranges: hook → stakes/why-now → the idea in one line → mechanism (layered) → evidence/demo → honest verdict → payoff + question/CTA. Not every video uses every stage — record what is present; never force an absent stage.
- **Claims inventory (CL-01…):** every factual/asserted statement with timestamp + whether it needs on-screen proof (number/diagram/quote) or rides on narration alone.
- **Numbers inventory:** every quantity spoken, with value + unit + timestamp + role (threshold? comparison? scale? rate?). Numbers are never decorative — each gets a visual landing (stat card, bar, gauge, counter) at its spoken moment.
- **Quoted speech inventory:** any dialogue/demo the video re-enacts (speaker + exact words + timestamp) — these get verbatim word-level sync (§10 rule 8), never paraphrase.
- **Causal/comparison graph:** A→B links (causes, contrasts, before/after pairs) the visuals must preserve spatially (cause left / effect right; before left / after right).
- **Emotional shifts** (curiosity → tension → relief → pride) with timestamps — each shift changes accent hue (within tokens) and motion tempo AT that phrase.

Do NOT design a single scene until this analysis exists.

## 7. CONCEPT EXTRACTION
Walk the transcript and extract **concepts** — meaning units that a viewer must separately *understand*. A concept is: a claim, a mechanism step, a comparison, a definition, a cause→effect, a quantity-in-context, a state change, an emotional beat, or evidence.

Rules:
- Concepts are NOT sentences. One sentence may contain 2-3 concepts (split them). Several short sentences may be ONE concept (merge them).
- Every concept must pass the "so what" test: after it, the viewer should hold something new. If nothing new, it belongs inside a neighbor concept as supporting motion.
- Label each concept with: **type** (object/action/system/relationship/comparison/process/quantity/cause/problem/abstract) and **importance** (pivotal / structural / passing). Pivotal concepts earn hero staging (character-hero or stat-card + glow); structural earn diagrams/kits; passing earn labels or motion accents — never a full scene each.
- Output a numbered list: `C01, C02, …` with working names. Do not force a count; do not pad. A 10-minute explainer typically yields 15-40 concepts.
- Anti-patterns: one-concept-per-sentence (mechanical), one-concept-per-paragraph (coarse), concepts named after shots ("wide shot of server") instead of ideas ("requests queue under load").

## 8. TRANSCRIPT SEGMENTATION
Map concepts to timestamp ranges:
- Ranges are contiguous, cover 0:00 → end, no gaps/overlaps (pauses attach to the concept they follow).
- Split points fall on MEANING boundaries (mid-sentence is normal when the idea changes).
- Mark ESTIMATED boundaries when timestamps are estimated.
- Attach, for each concept, its **exact transcript text** verbatim — the production prompt quotes it, never paraphrases the narration.
- Edge cases: overlapping speech → the interrupting phrase starts its own beat at its timestamp; long pauses (>1.5s) → extend the preceding concept's range and note HOLD in its spec (no new concept); repeated recap sentences → merge into the concept they recap, staged as a simplified restatement visual (dimmed prior elements return), not a new scene.
- Worked mini-example: transcript "Servers handle thousands of requests — but under load, queues grow." → C07 [0:41–0:47] "Servers handle thousands of requests" (system/structural: steady pipeline visual) + C08 [0:47–0:53] "but under load, queues grow" (cause/pivotal: comparison word "but" triggers swap to congested state, packets accumulate). The split falls mid-sentence at the meaning boundary.

## 9. VISUAL-BEAT GENERATION — the mandatory 9-step reasoning (PER CONCEPT)
Execute ALL nine steps for EVERY concept and write the results into the concept's spec (§20). This reasoning is the heart of the generator — narration becomes visual storytelling, not text-on-screen.

**Step 1 — Understand the meaning.** What exactly does this narration communicate? Classify the concept type (from §7). Identify entities, actions, relationships, states.

**Step 2 — Determine what the viewer must understand.** One sentence: "After this beat, the viewer knows ___." If you cannot fill the blank, the beat has no job — merge or cut it.

**Step 3 — Choose the most effective visual explanation.** Pick a strategy that *shows* the idea:
character action · technical diagram · assembled system · object transformation · spatial comparison · before/after · visual analogy · hierarchy/tree · timeline · process flow · scale comparison · environmental composition · animated interface · chart/data viz · progressive reveal · combination.
The list is options, not a checklist — invent a better technique when one fits. **Text-on-screen alone is never the strategy.**

**Step 4 — Reuse the visual system.** Select from the library: which characters, which environment/world, which props, which build kits (name them), which motion recipes. Justify each pick in one clause ("operator points at gauge → the narration names a limit").

**Step 5 — Invent content-specific visuals.** For entities the library doesn't cover: define the new object in the same visual language (flat, ≤3 tones, 2-3px stroke, label slot, role color) and mark it `NEW-ASSET` for §14. Never reuse one scene structure for multiple sentences without a structural reason; never default to the same kit twice.

**Step 6 — Design the animation.** Specify: initial state → changes during the beat (ordered, with recipe names) → final state → how it maps to the narration timing. Motion must carry the meaning (a queue must WAIT visually when the narrator says "waits"); decoration-only motion is forbidden.

**Step 7 — Check readability & composition.** Write the layout: normalized bboxes for every element, text sizes from the type scale, safe margins, reading order, reserved regions (§16).

**Step 8 — Connect to the next beat.** Name the continuity carrier (if any) and the transition (`clean-cut` default), or state "clean cut — conceptual break" with the reason.

**Step 9 — Validate the result.** List the concrete checks for THIS beat: frames to snapshot, expected states at phrase times, collision risks specific to this layout (§23-24).

---

## 10. CREATIVE VISUAL STORYTELLING
Design decisions you must make explicitly per concept — vague instructions are defects:
- **What is visible** at beat start, and what becomes visible when (phrase by phrase).
- **Where** each element sits (normalized x,y) and **how large** it is (w,h as canvas fractions).
- **Which words trigger which changes** (the phrase list with timestamps/frames).
- **How objects move** (recipe id + distance/direction + ease + duration).
- **How the scene connects** to the next (carrier or cut + reason).
- **How the composition avoids collisions** (bboxes + corridors).
- Variety discipline: rotate among strategies across the video (a list of five items ≠ five identical cards); vary composition side/axis; keep tokens constant.
- **Strategy chooser:** quantity → stat-card/bar/gauge (never a paragraph) · ordered process → pipeline-chain or timeline-track (packets advance in narrated order) · relationship/topology → flow-diagram (nodes appear as named) · A-vs-B → comparison-split (shared scale, divider never crossed) · threshold/limit → meter-threshold (breach = crosshair AT the word) · quoted speech → message-card/terminal with VERBATIM words · abstract claim → character acting it out + one display line (never text alone). Invent new techniques when none fits — but the invention must still obey §4 and declare its affordances.
- **Failure modes that REJECT a choice:** text restating narration as the whole visual · a diagram fully visible before its explanation begins · a metaphor needing more explanation than the concept · three strategies stacked in one beat (pick one; move the rest to neighbors) · the same kit+composition as the previous beat.

## 11. REUSABLE ASSET DISCOVERY
For each concept, search the library **by capability, not by name**: read `manifests/*.json` (+ guides: `ASSET_LIBRARY_GUIDE.md`, `BUILD_KIT_GUIDE.md`) and select assets that exist. Rules:
- Only list assets that are real (manifest `path` exists) — never reference an asset you did not verify.
- If manifests are not accessible in this session, either request them or assign candidates with `VERIFY-PATH` flags and instruct the coding agent to resolve them from the manifests before building.
- Record every selected asset in the concept's spec AND in the prompt's global asset-inventory table (§22).
- **Discovery procedure (run per concept):** 1) name the needed capabilities ("needs: countable bars + threshold line"); 2) scan `prop-manifest` + `build-kit-manifest` for matches; 3) if a kit covers ≥70% of the need, select the kit (§13) and spec the remainder as kit deltas; 4) else compose primitives (diagram SVG + label + chip); 5) only if neither fits, declare NEW-* (§14). Document the rejected runners-up in one line ("chose DIAG-BAR-COLUMNS over PROP-GAUGE-DIAL: transcript compares three quantities, no threshold").

## 12. CHARACTER & ENVIRONMENT SELECTION
- Characters appear only when a human/bot ACTION carries meaning (pointing, carrying, reacting, comparing) — not as a default presenter in every scene. Choose GUIDE-BOT-01 (guide/system-side) vs OPERATOR-01 (human/user-side) by role; other library characters only via manifest.
- One world per scene; the world switch must follow the abstraction change (narrative → mechanism → data). Record for each scene: world, background asset, ground/floor line value, lighting treatment.
- Environment instances are ADAPTED (facade sign text, prop set, character positions, cone placement) — never identical back-to-back.
- **Casting rule:** at most one character on screen unless the narration stages an interaction (dialogue, handoff, comparison). When both appear, GUIDE-BOT explains/system-side-left and OPERATOR acts/user-side-right by default; mirror only with a stated reason. Characters never lip-sync the narrator — they act (point/carry/react) while narration continues.

## 13. BUILD-KIT SELECTION & ADAPTATION
- Select kits first (`build-kits/**`), then write the deltas: which required assets, position changes, extra/removed props, label content, animation choices, and the kit's collision constraints you must honor.
- A kit instance in the production prompt lists: `kit id` · `purpose in this beat` · `deltas vs template` · `bbox table` · `animation using recipe ids`.
- Kitting discipline: a kit may not repeat unadapted; two simultaneously-visible kit instances must have disjoint bboxes (§16/§23).
- **Worked delta example:** "KIT-pipeline-chain for C08: 3 stages (not the template's default) labeled INGEST/QUEUE/SERVE from the transcript nouns; stage 2 tinted danger red (queue overrun); packets: 2 steady + 4 accumulating at stage 2 (cadence 600ms); conveyor y moved to 0.62 to clear the hero line's bbox (0.10–0.24); kit's 'labels below belt line only' constraint honored; arrows enter-draw left→right in narrated order."

## 14. NEW ASSET CREATION INSTRUCTIONS (when the library lacks an object)
1. Specify the gap precisely (what noun, what behavior).
2. Design in-language: flat vector, ≤3 tones from the role palette, 2-3px #14181f stroke, rounded geometry, mono label slot, one state LED if stateful.
3. Declare: **id** (`NEW-<slug>`), build method (inline SVG-in-HTML preferred; project file under `assets/project-specific/` when large), animation affordances (which parts move/fill/blink), bbox at design size.
4. New assets belong to the PROJECT, not the library — unless genuinely topic-neutral, in which case note "candidate for library" without adding it during production.
5. Never fabricate an asset the transcript doesn't need to fill space; if a beat is complete without it, don't create it.
6. **Worked NEW-* example:** "NEW-load-balancer [0:47–0:55, C08]: inline SVG 320×200 (x 0.34, y 0.40): rounded rect #17202b, 3px #14181f stroke; three input arrows (left, ids lb-in1..3) + one output arrow (right, id lb-out); amber LED per input (ids lb-led1..3, phraseState at each 'request' phrase); mono label slot 'BALANCER' (chip tier). Affordances: LEDs blink, arrows enter-draw, box static. Bbox (0.34,0.40,0.32,0.20) disjoint from hero line (0.10–0.24) and belt (0.62)."

---

## 15. TYPOGRAPHY & LAYOUT SPECIFICATION
Per scene/concept, specify text EXACTLY:
- The display line (≤2 lines, all-caps or title case as the tone demands), its role color + glow, its size tier (hero/chapter/secondary/number/label/chip/micro), its bbox, its alignment.
- Every number: value + unit caption + tier + the phrase it counts to.
- Every label/chip: exact string (mono, uppercase), owner object, attachment (on-object vs leader line), size tier.
- Wrap manually into explicit line spans (never `<br>`, never rely on auto-wrap for display type). Reserve cursor width (0.03) for typewriter lines.
- Forbidden: paragraph text, restating narration, duplicate information (a fact is either spoken or captioned, not both in full sentences).

## 16. COMPOSITION & SPATIAL PLANNING
For EVERY scene write a layout table before animation:
```
element | role (H1/H2/H3/H4) | x | y | w | h | z | notes
```
- All values normalized (0-1) to canvas; snap to the 12-col grid; margins ≥ 0.05; chrome bands y<0.055 and y>0.955 reserved.
- Declare: reading order · negative-space target · animation corridors (paths packets/characters use, as x/y ranges) · reserved regions · **intended overlaps whitelist** (e.g., "label ON object", "halo behind hero") — everything else overlapping is a defect.
- One H1 per frame; simultaneous text bboxes must be disjoint with ≥ 0.025 gaps.

---

## 17. ANIMATION DESIGN
Per beat, produce an **animation sequence**: an ordered list where every row = {element, change, recipe id (from `animations/*`), start phrase, start time+frame, duration, ease, end state}.
- Initial state and final state of EVERY element must be written down — implicit states cause drift.
- Choose eases from tokens (`design-tokens/animation-tokens.json`); durations from the micro/standard/emphasis bands unless the narration demands otherwise.
- Coordinated groups: define the stagger order and waves (≤6 waves).
- Motion budget: exactly the narrated actions + ambient ≤ 0.35. If a proposed motion has no spoken cause, delete it.
- Cadence motions (ticks, slices, polls) declare ONE period shared video-wide (`periodFrames = round(periodSec × fps)`).
- **Worked sequence example** (C08 "queues grow" [0:47–0:53], fps 30, lead 0.15): {stage-2 packets, accumulate +4, enter-slide-left, "queues" @47.2s→1416f, 0.5s, power3.out, end: 6 tiles stacked} · {stage-2 tab, recolor amber→red, recolor-role, "grow" @48.0s→1440f, steps(1), end: red} · {queue-count chip, 2→6, countTo, "grow" @48.0s, 0.5s, end: "6 QUEUED"} · {stage-1/3, dim, recede-dim, 48.5s, 0.4s, end: 0.4}. Every row names its phrase; no phrase-less rows exist.

## 18. AUDIO & PHRASE-LEVEL SYNCHRONIZATION
- VO is the master timeline. Bind every visual event to a **meaningful phrase** — never a whole sentence, never a subtitle cue.
- Per concept, list `sync cues`: {phrase (verbatim), timestamp, frame, event(s)} — with `frame = round(seconds × fps)`, fps stated once at the top (default 30).
- **Lead rule:** event start = phrase time − lead (0.10-0.25s, state your per-beat lead) so the visual settles as the word lands.
- Numbers count to their spoken value, finishing AT the phrase. Thresholds snap at the spoken breach word. State flips (LED/check/stamp) are `steps(1)` at the spoken word.
- Quoted dialogue: word-by-word reveal on the quoted words only; keep looping visuals alive during pauses; never add anything during a breathing pause.
- Audio-vs-transcript conflicts: prefer audio, document the discrepancy; all timings measured from estimates are marked `ESTIMATED`.
- **Worked sync-cue example** (C08, fps 30): {"queues" | 47.2s | f1416 | 4 packets enter-slide-left into stage-2} · {"grow" | 48.0s | f1440 | stage-2 tab →red (steps), chip counts 2→6} · {pause 48.6–49.4 | — | HOLD: loops alive, nothing added}. Lead 0.15 stated once per beat; every event's start = phrase − lead.

## 19. TRANSITION & CONTINUITY PLANNING
- Default `clean-cut`; a non-cut transition must name its carrier (object/boundary/camera/transform) and the story reason.
- Cross-beat continuity table: for each beat boundary → `carrier (asset id + path) | cut | world-switch reason`.
- World switches and chapter cuts are motivated and listed; chrome stays mounted across all of them.
- Cap: whip transitions ≤2 per video; morphs only when geometry genuinely aligns.

## 20. SCENE-BY-SCENE PRODUCTION-PROMPT GENERATION — the per-concept specification (MANDATORY FIELDS)
Every concept C## gets a complete block containing ALL of:
1. **Concept ID + name** · 2. **Timestamp range** · 3. **Exact transcript segment** (verbatim) · 4. **Main idea** · 5. **Intended viewer understanding** (the Step-2 sentence) · 6. **Visual explanation** (what is on screen and why) · 7. **Metaphor/technique** (named strategy) · 8. **Required reusable assets** (manifest ids + paths) · 9. **Required build kits** (ids + deltas) · 10. **New assets** (`NEW-*` specs or "none") · 11. **Initial scene composition** (world, background, lighting, ground line) · 12. **Element positions & sizes** (the §16 bbox table) · 13. **Animation sequence** (the §17 ordered rows) · 14. **Timing & easing** (durations, eases, stagger waves) · 15. **Audio-sync cues** (the §18 list with frames) · 16. **Typography & labels** (exact strings + tiers + bboxes) · 17. **Transition/continuity** (§19 entry) · 18. **Layout constraints** (reserved regions, corridors, negative-space target) · 19. **Overlap-prevention** (bbox gaps + intended-overlap whitelist + this beat's specific collision risks) · 20. **Implementation instructions** (HyperFrames notes: clip boundaries, sub-comps, which helper functions) · 21. **Validation criteria** (frames to snapshot + expected states + pass conditions).
- Concepts with multiple visual beats: emit sub-blocks `C07.1, C07.2 …` each with the same fields where timing/scene changes; state what PERSISTS across sub-beats.
- No meaningful transcript section may be omitted. No empty beats may be added for length. Every beat must communicate something.

## 21. HYPERFRAMES IMPLEMENTATION REQUIREMENTS (guidance you write FOR the coding agent)
State once, at the top of the production prompt:
- Composition: root `data-composition-id`, `data-width/height` (1920×1080 default), `data-duration` = audio duration (seconds; `round(dur×fps)` frames), fps (default 30).
- Structure: one `.clip` per scene/concept (`data-start` = its frame's seconds, `data-duration` = span); sub-compositions for repeated kits; persistent chrome as its own always-on clip; media (`<audio>`) mounted once and owned by the framework.
- Animation: ONE paused GSAP timeline registered on `window.__timelines["<id>"]`; every event positioned in seconds via the helpers (`reusable-assets/animations/reusable-motion-components/phrase-sync-helpers.js`: `at/phraseIn/countTo/cadence/phraseState/typewriter`).
- Determinism: no `Math.random`, no wall-clock, no network, no input state at render; `repeat:-1` only within finite duration; never tween `display/visibility/autoAlpha` on `.clip` (animate children); no `<br>`; unique ids across the assembled page; GSAP transform rules (use `fromTo`, no CSS `transform: translate(-50%,-50%)` on tweened nodes).
- Gates (mandatory order): `hyperframes check` → 0 findings · `hyperframes snapshot` at the listed validation frames → inspect · fix loop (§23) · `hyperframes render` only after visual approval.
- **Success criterion: passing code is not visual proof.** Rendered-frame inspection is the acceptance evidence.

---

## 22. ASSET PATH & DEPENDENCY DOCUMENTATION
The production prompt must carry a **global asset inventory table**:
```
asset id | kind (library | project-new | evidence) | relative path or NEW-* spec | used in concepts | role/color | animation affordances
```
- Library paths are **relative to the library root** (e.g., `props/tools/gauge-dial.svg`) with one resolution rule stated: "project resolves library paths from `../../reusable-assets/` or an import configured in `project-config.json`." Never absolute machine paths.
- Evidence assets (screenshots/docs/photos): source note + crop region + license/provenance line when known.
- Dependencies: fonts (family + fallback stack + load method), GSAP version pinned as the project uses, helper JS path.
- If manifests were used, note which manifest file each library row came from.

## 23. COLLISION PREVENTION (core production requirement — not a nicety)
Encode the mandated loop: **Plan → implement → render representative frames → inspect → identify defects → correct → re-render → confirm.**
- Per scene: the §16 bbox table + intended-overlap whitelist.
- Explicit checks on ANIMATED states (not just final poses): 1) text↔text · 2) text↔object · 3) object↔object · 4) label↔arrow · 5) unexpected wrapping · 6) text clipping · 7) outside canvas/margins · 8) mid-motion intersections (packets through labels, characters through props) · 9) heroes obscured by overlays/halos · 10) overcrowding vs the scene's element budget.
- Corridor check: every declared animation path's swept bbox vs every static bbox.
- Max-digit measurement for counters (widest value must fit).
- Re-inspect the SAME frames after every fix.
- Include verbatim: **"Successful code execution does not prove that a scene is visually correct."**

## 24. QUALITY ASSURANCE
**Generator-side, before emitting:** complete narrative analysis exists · concepts cover 0:00→end, no gaps · every concept has all 21 fields · every asset verified or flagged `VERIFY-PATH` · every event has phrase+time+frame · every scene has bbox table + whitelist · tokens consistent (role colors, type tiers) · no reference-copying (§5) · §25 format complete.
**Required of the coding agent:** `hyperframes check` = 0 findings · snapshots at every concept's validation frames inspected against expected states · §23 collision checklist walked · sync spot-checks (freeze at 3 phrase times; visual state must match narration) · full render after approval · defects logged in `validation/` with fix + re-check evidence.

## 25. FINAL PRODUCTION-PROMPT FORMAT (the document you emit — exactly these sections)
```
PRODUCTION PROMPT — <title>
0. PROJECT PARAMETERS      fps, canvas, audio duration/frames, timing provenance (MEASURED/ESTIMATED), world palette (role→hex)
1. PROJECT OVERVIEW        mission, audience, one-sentence core message, tone
2. NARRATIVE ANALYSIS      skeleton with timestamps; claims; numbers inventory; quoted-speech inventory
3. VISUAL DIRECTION        style lock summary, worlds used + switch map, recurring motifs for THIS video
4. DESIGN-SYSTEM SPECS     tokens referenced (colors/type/spacing/dim/animation) + any project overrides
5. CANVAS & LAYOUT RULES   margins, chrome bands, ground lines, grid, negative-space targets
6. ASSET-LIBRARY REFERENCES global asset inventory table (§22) + manifest sources + resolution rule
7. CHARACTER & ENVIRONMENT ASSIGNMENTS   per scene: world, characters (pose/expression), environment deltas
8. COMPLETE CONCEPT BREAKDOWN   the C01..Cn list w/ type, importance, ranges (the map of §8)
9. TIMESTAMPED VISUAL BEATS      one-line beat index (id, range, H1, kit, transition) for fast navigation
10. SCENE-BY-SCENE SPECIFICATIONS  the full §20 blocks (21 fields each) — the body of the document
11. ANIMATION INSTRUCTIONS        consolidated ordered sequences + recipe ids + initial/final states
12. PHRASE-LEVEL AUDIO SYNC       all sync-cue tables + lead values + ESTIMATED flags
13. TYPOGRAPHY & OBJECT SIZING    exact strings, tiers, bboxes, max-digit notes
14. TRANSITIONS & CONTINUITY      boundary table (carrier | cut | reason)
15. NEW ASSET REQUIREMENTS        NEW-* specs (or "none")
16. HYPERFRAMES IMPLEMENTATION    §21 statement (structure, helpers, determinism, gates)
17. COLLISION PREVENTION          §23 tables, corridors, whitelist, mandated loop + the verbatim statement
18. VALIDATION REQUIREMENTS       checklist the agent must complete (§24)
19. RENDER INSPECTION CHECKPOINTS frame list per concept + expected states
20. FINAL ACCEPTANCE CRITERIA     what "done" means (gates + visual + sync + originality)
```
Tailored to the ACTUAL transcript — never a generic video prompt. This is the handoff document; the coding agent must not have to invent storyboard or animation decisions that belong in §10.

## 26. VALIDATION & COMPLIANCE CHECKLIST (answer honestly in your final reply)
- [ ] Inputs actually analyzed; anything inaccessible disclosed; ESTIMATED timings flagged.
- [ ] Entire story understood before scenes were designed; skeleton mapped with timestamps.
- [ ] Concepts extracted by meaning; segmentation contiguous 0:00→end; every meaningful section has a spec.
- [ ] Every concept has all 21 mandatory fields; no empty/padded beats.
- [ ] 9-step reasoning executed per concept (visible in the spec's choices).
- [ ] Assets: only verified real assets (or VERIFY-PATH flagged); global inventory table present; relative paths only.
- [ ] Kits selected with deltas; no kit repeated unadapted; new assets spec'd in-language.
- [ ] Bbox tables + corridors + intended-overlap whitelist for every scene; counter max-digit measured.
- [ ] Phrase-level sync with frames; lead rule stated; numbers bound to spoken values.
- [ ] HyperFrames section present and matches the real toolchain (data-attrs, GSAP, check/snapshot/render gates); no invented APIs.
- [ ] The verbatim statement "Successful code execution does not prove that a scene is visually correct." present.
- [ ] Originality: no reference frames/shots/illustrations/wording reproduced; new metaphors inventoried for this topic.
- [ ] Output follows §25 exactly; title + transcript + audio are its only inputs; no reference video required downstream.

---

*Usage: paste this file into ChatGPT, then provide title + timestamped transcript + audio. Attach `VISUAL_SYSTEM_SPECIFICATION.md` + `manifests/` when possible. Emit one PRODUCTION PROMPT (§25) → hand it to the coding agent → they build with HyperFrames and this library.*

# VISUAL_SYSTEM_SPECIFICATION

**Reference-derived visual system — authoritative for all videos generated from this library.**
Derived from: `reference-analysis/video-01-full-duplex` (full coverage: 18 contact sheets, 158 scene-cuts, word transcript) and `reference-analysis/video-02-strata` (5 keyframes + 15/19 contact sheets, 190 scene-cuts; silent video). Estimates are labeled. This document replaces the need to ever re-watch the reference.

> **Measurement honesty:** numeric values are frame-inspection estimates (±10-25% unless stated). Sampling: 4s-interval contact sheets + targeted keyframes — NOT exhaustive frame-by-frame.

---

## 1. Overall visual identity
Dark, precise, "instrument-like" technical documentary: near-black field, role-coded neon accents, flat vector worlds, mono micro-metadata, glow display typography. Four intercut modes: (A) flat side-scroller narrative scenes, (B) glow typography cards, (C) isometric/wireframe data diagrams, (D) real evidence (screenshots/docs/photos) as framed objects. Mood: calm, measured, honest — numbers are shown, not hyped.

## 2. Background & environment system
- Default production background: **`#0a0f0a`** (owner-mandated) unless a project specifies otherwise; reference-derived family `#0d121e / #111928 / #151e36 / #1c2030` documented for fidelity mode.
- Three worlds: **narrative** (street: facades, ground line 82-86% H, moon/skyline) · **mechanism** (interior: floor 75-80% H, pendant cones, stations) · **data** (grid field or iso plane).
- Separation by value + opacity: far layers 10-25% lighter than base; context dimmed to 0.35-0.5.
- Perspective: side-scroller scenes **orthographic**; data scenes **3/4 iso grid**. Never a third perspective.
- Light: warm downward cones (amber gradient, 0.16-0.5) vs cool ambient; one key light per scene. Shadows: none, or one soft ground ellipse.

## 3. Color palette
`design-tokens/colors.json`. Dark base; role-coded accents (amber=model/output, cyan=user/input, red=danger, violet=concept, green=live); white display; grays inactive. Same role = same color video-wide. Glow only on display type and live indicators. A light interior (`#e9ecef`) at most once per video as deliberate contrast.

## 4. Typography system
Tokens: `design-tokens/typography.json`; specimen: `typography/specimen.svg`. Heavy geometric all-caps display (substitutes Poppins/Montserrat/Archivo — **original unidentified**) + coding mono for labels (JetBrains Mono/IBM Plex Mono — substitute). Scale est. % of frame H: hero 10-13 · chapter 8-9 · secondary 6-7 · stat 5-6.5 · label 3-4 · chip 2.5-3.5 · micro 1.5-2. Glow 18-38px @1080. Mono tracking +0.15-0.25em. Block-cursor typewriter headlines; two-tone headlines split by role; body paragraphs forbidden.

## 5. Character-design conventions
Library characters: **GUIDE-BOT-01** (hover bot: rounded-square body, visor band, detached hands, amber thruster glow) and **OPERATOR-01** (human: cap+headset, teal vest). Flat fills, 2.5-3px #14181f outlines, silhouette-first, no facial detail beyond visor LEDs/eyes. States = swap sheets, never redraw. Characters act out narration; they never lip-sync to the narrator.

## 6. Character proportions & consistency rules
Guide-bot: visor = top third of body; hero 0.30-0.38 H, secondary 0.15-0.22 H. Operator: head:body ≈ 1:2.4; hero 0.30-0.38 H, secondary 0.15-0.25 H. Feet/base ON the active ground line. Same character keeps relative scale within a scene; cross-scene scale change only to express significance — never contradicting stated size facts.

## 7. Props & object-design conventions
Props are functional machines, not ornaments: each has a label slot (mono), a state (LED/chip), and a job in the narration. Thin 2-3px strokes, rounded-rect geometry, ≤3 tones. Every noun gets a sketch mapping before any text label; prefer composing with library primitives over new drawings; honest evidence (screenshots/docs) is cropped, framed, and highlighted on the narrated line.

## 8. Lighting & shadow rules
One warm key cone per scene, cool fill. Cone ≤ 0.5 at source, ≤ 0.18 under text. Hero halo behind object ≤ 0.55. Emissive elements bleed drop-shadow in their role color. No cast shadows except soft ground ellipses.

## 9. Composition & framing rules
Meaning-first placement (source→left, dest→right, hero→thirds intersection). ONE dominant attention target per beat. Outer safe margin ≥ 5%. Chrome bands: top 2.0-5.5%, bottom 95.5-98.5%. Negative space 35-60% on statement/stat cards. Never cut heads/labels at frame edges. Reading order: headline upper-left → hero → labels.

## 10. Spatial hierarchy
H1 display hero/hero object · H2 supporting number/label · H3 object labels/chips · H4 mono micro-metadata. One H1 per frame; H2-4 coexist only with disjoint bboxes. Hierarchy changes animate: previous H1 recedes before the new one arrives.

## 11. Layering & depth
Back-to-front: backdrop → far env → mid env → ground → main props/characters → traveling units → labels/rings → display type → chrome. Depth via value/opacity, never blur (except whip). Parallax ≤ 3 layers, ≤ 0.15 relative speed.

## 12. Animation language
Every motion is a narrated causal act: enter (rise/drop/slide/pop/draw/type) · recede (dim by default — the world never resets) · transform (morph/recolor/quantize/split/merge/expand) · highlight (glow/ring/spot/leader/crosshair/tick) · travel (packets along corridors) · measure (count/grow/spring needle). Recipes: `animations/*/[...]-recipes.json`. Ambient ≤ 0.35 intensity (LED blink 1.2s, fan 3s).

## 13. Motion timing & easing
Tokens: `design-tokens/animation-tokens.json`. Micro 0.12-0.2s · standard 0.4-0.6s · emphasis 0.6-0.8s · assemble 0.8-1.2s. Eases: power3.out enter, power2.in exit, back.out settle, steps(1) flips. Stagger 0.06. Cadence shares one period video-wide (600ms = 18 frames @30fps). Lead rule: visual starts 0.10-0.25s BEFORE its phrase. Numbers count to the spoken value, finishing at the phrase.

## 14. Transition techniques
Default = clean cut at conceptual breaks; continuity needs a real carrier. List: `animations/transitions/transition-recipes.json` (cut · carrier-object · expand-frame · camera-dolly · morph-metaphor · world-switch · whip ≤2/video). Persistent chrome never transitions.

## 15. Scene construction patterns
Scenes assemble from **build kits** (`build-kits/**`): street-standoff · interior-station · character-hero · pipeline-chain · flow-diagram · chapter-card · stat-card · comparison-split · meter-threshold. A scene = background layer + kit assembly + display line + labels + chrome. Kits are adapted, never pasted identically twice in one video.

## 16. Storyboard & visual-beat principles
Skeleton: hook → stakes → idea → mechanism → evidence → verdict → payoff/CTA. Beats cut by MEANING (split sentences; merge short ones). Typical beat 2-6s (montage 0.5-1.5s; demo/hero 6-10s). Complexity scales with narrative importance. Every beat must answer: what does the viewer now understand that they didn't before?

## 17. Audio-synchronization principles
VO is the master clock; bind at PHRASE granularity (not sentence, not subtitle cue). Objects appear when first mentioned and persist (dimmed). Numbers land at spoken values. Diagrams develop during explanation — never pre-revealed. Pauses breathe: keep loops alive, add nothing new. Emphasis words get simultaneous visual emphasis. Full rules: `AUDIO_SYNCHRONIZATION_RULES.md`.

## 18. Reusable asset categories
characters/ (sheets, components, poses, expressions) · environments/ (backgrounds, components, architecture, lighting, layout guides) · props/ (furniture, technology, tools, interfaces, other) · diagrams/ · textures/ · typography/ · visual-effects/ · animations/ (recipes + helpers) · build-kits/ · design-tokens/. Inventories: `manifests/*.json` (stable IDs, paths, status).

## 19. Build-kit conventions
Every kit documents: purpose · required/optional assets · normalized layout boundaries · layer order · allowed variations · animation possibilities · collision constraints · implementation notes. Kits are the unit of reuse: production prompts select kits first, then specify deltas. Kits never contain reference-specific or transcript-specific content.

## 20. Rules for creating new content-specific visuals
1) Map the noun to a library primitive first — if it fits, compose from assets; 2) else invent an ORIGINAL object in the same language (flat, ≤3 tones, 2-3px stroke, label slot, role color) and save it to the project's `assets/project-specific/` (library only if generally reusable); 3) never redraw what exists; 4) never copy a distinctive reference illustration; 5) every new object declares its animation affordances (what can move/fill/blink).

## 21. Layout & collision-prevention requirements
Every beat declares: canvas · margins · per-element bbox (x,y,w,h normalized) · z-order · reserved regions · animation corridors · intended-overlap whitelist. Checks: text-text · text-object · object-object · label-arrow · wrapping · clipping · canvas overflow · mid-motion intersections · obscured heroes · overcrowding. Inspect ANIMATED states via rendered frames — running code proves nothing visually. Procedure: `LAYOUT_AND_SPACING_RULES.md`.

## 22. Technical implementation considerations
Target: **HyperFrames v0.8.x** (HTML compositions, GSAP timelines, `data-*` timing, deterministic renders). Root: `data-composition-id/width/height/duration`; clips = `data-start`+`data-duration` (`class="clip"` convention); paused master timeline on `window.__timelines[id]`; all tweens in seconds of film time. Gates: `hyperframes check` → `hyperframes snapshot` at beat frames → eyeball → `hyperframes render`. Never: clocks/unseeded random/network at render time, animating `.clip` display/visibility/autoAlpha, `<br>` in text. Assets referenced by RELATIVE path (library → project via relative link or import), never absolute machine paths.


animation-manifest.json
{
  "$comment": "Animation resources: deterministic GSAP recipes + JS helpers. All paths relative to library root.",
  "recipes": [
    {"id": "enter-rise", "path": "animations/entrances/entrance-recipes.json", "category": "animations/entrances", "description": "Default object entrance: rise 48px + fade, 0.5s power3.out fromTo. Trigger at phraseAt - 0.15s.", "format": "json", "intendedUse": "default entrance for any object with a spoken trigger", "validation": "verified"},
    {"id": "enter-drop", "path": "animations/entrances/entrance-recipes.json", "category": "animations/entrances", "description": "Object falls onto surface / token into container: y -160 to 0, 0.55s back.out(1.3).", "format": "json", "intendedUse": "stations, tokens landing in containers", "validation": "verified"},
    {"id": "enter-slide-left", "path": "animations/entrances/entrance-recipes.json", "category": "animations/entrances", "description": "Left-side source introduces itself: x -120 to 0 + fade, 0.5s.", "format": "json", "intendedUse": "inputs, left-side actors", "validation": "verified"},
    {"id": "enter-slide-right", "path": "animations/entrances/entrance-recipes.json", "category": "animations/entrances", "description": "Right-side destination: x +120 to 0 + fade, 0.5s.", "format": "json", "intendedUse": "destinations, right-side actors", "validation": "verified"},
    {"id": "enter-pop-scale", "path": "animations/entrances/entrance-recipes.json", "category": "animations/entrances", "description": "Number/claim punch-in at spoken word: scale 0.6 to 1, 0.35s back.out(2).", "format": "json", "intendedUse": "stat numbers, claims, message cards", "validation": "verified"},
    {"id": "enter-draw", "path": "animations/entrances/entrance-recipes.json", "category": "animations/entrances", "description": "Connector/underline/chart line: strokeDashoffset 340 to 0, 0.6s power2.inOut.", "format": "json", "intendedUse": "arrows, underlines, threshold zones", "validation": "verified"},
    {"id": "enter-type", "path": "animations/entrances/entrance-recipes.json", "category": "animations/entrances", "description": "Display headline / evidence line: per-char reveal staggered 0.03s with block cursor, removed at end.", "format": "json", "intendedUse": "hero display, chapter titles, terminal lines", "validation": "verified"},
    {"id": "enter-stagger-wave", "path": "animations/entrances/entrance-recipes.json", "category": "animations/entrances", "description": "Multiple queue items / grid cells: enter-rise staggered 0.06, max ~6 waves then coalesce.", "format": "json", "intendedUse": "queues, grids, checklist items", "validation": "verified"},
    {"id": "recede-dim", "path": "animations/exits/exit-recipes.json", "category": "animations/exits", "description": "DEFAULT continuation: object dims to opacity 0.4 + desaturates, stays in place. Prefer over removal.", "format": "json", "intendedUse": "context objects leaving focus; world never resets", "validation": "verified"},
    {"id": "exit-slide-left", "path": "animations/exits/exit-recipes.json", "category": "animations/exits", "description": "Consumed input leaves: x -140 + fade, 0.45s power2.in.", "format": "json", "intendedUse": "consumed inputs", "validation": "verified"},
    {"id": "exit-slide-right", "path": "animations/exits/exit-recipes.json", "category": "animations/exits", "description": "Finished output leaves: x +140 + fade, 0.45s.", "format": "json", "intendedUse": "finished outputs", "validation": "verified"},
    {"id": "exit-collapse", "path": "animations/exits/exit-recipes.json", "category": "animations/exits", "description": "Container empties / concept replaced: scaleY to 0.02 + fade, origin bottom.", "format": "json", "intendedUse": "emptied containers, replaced concepts", "validation": "verified"},
    {"id": "exit-handoff", "path": "animations/exits/exit-recipes.json", "category": "animations/exits", "description": "Object becomes next scene hero: element stays mounted across the cut, tweens to new position.", "format": "json", "intendedUse": "continuity carrier transitions", "validation": "verified"},
    {"id": "morph-shape", "path": "animations/transformations/transform-recipes.json", "category": "animations/transformations", "description": "One metaphor geometry becomes another sharing bbox (0.5s crossfade, silhouettes aligned).", "format": "json", "intendedUse": "analogy-to-analogy shifts", "validation": "verified"},
    {"id": "recolor-role", "path": "animations/transformations/transform-recipes.json", "category": "animations/transformations", "description": "Object changes role color at the spoken state word (instant phraseState swap).", "format": "json", "intendedUse": "state changes, ownership transfers", "validation": "verified"},
    {"id": "split-into", "path": "animations/transformations/transform-recipes.json", "category": "animations/transformations", "description": "One object divides into parts (each part enter-slide outward).", "format": "json", "intendedUse": "decomposition explanations", "validation": "verified"},
    {"id": "merge-into", "path": "animations/transformations/transform-recipes.json", "category": "animations/transformations", "description": "Many become one: clones translate to target center, target pulses.", "format": "json", "intendedUse": "aggregation, consensus", "validation": "verified"},
    {"id": "expand-boundary", "path": "animations/transformations/transform-recipes.json", "category": "animations/transformations", "description": "Scope grows: boundary rect +25% 0.7s; interior reflows with same ease.", "format": "json", "intendedUse": "local to system zoom-outs", "validation": "verified"},
    {"id": "hl-glow", "path": "animations/highlights/highlight-recipes.json", "category": "animations/highlights", "description": "Role-color drop-shadow glow 0 to 14px, 0.25s; removed when next hero takes focus.", "format": "json", "intendedUse": "default emphasis (this one / specifically)", "validation": "verified"},
    {"id": "hl-ring", "path": "animations/highlights/highlight-recipes.json", "category": "animations/highlights", "description": "3px role-color ring pulse around bbox, yoyo once 0.4s.", "format": "json", "intendedUse": "pointing at a bounded object", "validation": "verified"},
    {"id": "hl-spot", "path": "animations/highlights/highlight-recipes.json", "category": "animations/highlights", "description": "Dim everything outside target (siblings to 0.35) over 0.35s; restore at beat end.", "format": "json", "intendedUse": "isolate one object among many", "validation": "verified"},
    {"id": "hl-color-word", "path": "animations/highlights/highlight-recipes.json", "category": "animations/highlights", "description": "Single keyword span tweens to role color at spoken instant; never whole line.", "format": "json", "intendedUse": "keyword emphasis", "validation": "verified"},
    {"id": "hl-leader", "path": "animations/highlights/highlight-recipes.json", "category": "animations/highlights", "description": "Leader line draws (dashoffset) from label to object, label fades in at 0.3s.", "format": "json", "intendedUse": "label-to-object binding", "validation": "verified"},
    {"id": "hl-crosshair", "path": "animations/highlights/highlight-recipes.json", "category": "animations/highlights", "description": "Threshold breach: instant red cross + 0.12s region flash x2, value turns danger red.", "format": "json", "intendedUse": "over-limit moments (KIT-meter-threshold)", "validation": "verified"},
    {"id": "hl-checkbox", "path": "animations/highlights/highlight-recipes.json", "category": "animations/highlights", "description": "Checklist tick: box fill steps(1) + check draw 0.25s at spoken item.", "format": "json", "intendedUse": "checklist completions", "validation": "verified"},
    {"id": "tr-clean-cut", "path": "animations/transitions/transition-recipes.json", "category": "animations/transitions", "description": "DEFAULT: end clip A / start clip B on phrase boundary, no effect. Use on conceptual breaks.", "format": "json", "intendedUse": "default transition", "validation": "verified"},
    {"id": "tr-carrier-object", "path": "animations/transitions/transition-recipes.json", "category": "animations/transitions", "description": "One object spans both clips, tweens position/scale; background swaps behind it.", "format": "json", "intendedUse": "same-thing-new-context continuity", "validation": "verified"},
    {"id": "tr-expand-frame", "path": "animations/transitions/transition-recipes.json", "category": "animations/transitions", "description": "Diagram scales to 0.6 toward corner while larger system fades in (0.7s).", "format": "json", "intendedUse": "detail to broader context", "validation": "verified"},
    {"id": "tr-camera-dolly", "path": "animations/transitions/transition-recipes.json", "category": "animations/transitions", "description": "World layer translates one axis 1.0-1.6s into next station; characters keep positions.", "format": "json", "intendedUse": "walking through mechanism worlds", "validation": "verified"},
    {"id": "tr-morph-metaphor", "path": "animations/transitions/transition-recipes.json", "category": "animations/transitions", "description": "Crossfade two metaphors sharing geometry (same bbox, 0.5s).", "format": "json", "intendedUse": "analogy shifts", "validation": "verified"},
    {"id": "tr-world-switch", "path": "animations/transitions/transition-recipes.json", "category": "animations/transitions", "description": "Lighting dip 0.3s to new world clip; chrome stays mounted, frame never blinks.", "format": "json", "intendedUse": "world changes (narrative/mechanism/data)", "validation": "verified"},
    {"id": "tr-whip", "path": "animations/transitions/transition-recipes.json", "category": "animations/transitions", "description": "RARE (max 2/video): 0.18s translate + blur on outgoing layer; energy shifts and lists only.", "format": "json", "intendedUse": "energy shifts", "validation": "verified"}
  ],
  "helpers": [
    {"id": "HELPER-at", "path": "animations/reusable-motion-components/phrase-sync-helpers.js", "export": "at(phraseSec, lead)", "description": "Transcript seconds to timeline position honoring the lead rule."},
    {"id": "HELPER-phraseIn", "path": "animations/reusable-motion-components/phrase-sync-helpers.js", "export": "phraseIn(tl, phraseSec, target, opts, lead)", "description": "Entrance bound to one phrase via fromTo with clamped window."},
    {"id": "HELPER-countTo", "path": "animations/reusable-motion-components/phrase-sync-helpers.js", "export": "countTo(tl, phraseSec, target, value, opts)", "description": "Number counts to spoken value, finishing at the phrase; drives gauge needles too."},
    {"id": "HELPER-cadence", "path": "animations/reusable-motion-components/phrase-sync-helpers.js", "export": "cadence(tl, startSec, endSec, periodSec, fn)", "description": "Film-time cadence loop (e.g. 600ms period = 18 frames @30fps)."},
    {"id": "HELPER-phraseState", "path": "animations/reusable-motion-components/phrase-sync-helpers.js", "export": "phraseState(tl, phraseSec, target, props, lead)", "description": "Instant state flip exactly at the phrase via .set."},
    {"id": "HELPER-typewriter", "path": "animations/reusable-motion-components/phrase-sync-helpers.js", "export": "typewriter(tl, phraseSec, chars, cursor, opts)", "description": "Typewriter reveal of pre-split char spans with block cursor."},
    {"id": "HELPER-LEAD", "path": "animations/reusable-motion-components/phrase-sync-helpers.js", "export": "LEAD = 0.15", "description": "Default visual lead over spoken word (allowed 0.10-0.25)."}
  ],
  "rules": ["Every entrance starts at phraseAt - lead.", "One entrance per semantic event.", "Prefer fromTo (transform conflicts fail lint).", "Only ONE highlight at a time.", "Clean cut is the default transition.", "Never animate .clip elements display/visibility/autoAlpha."]
}

asset-manifest.json

{
  "$comment": "Cross-category index AUTO-GENERATED from the real file tree. Every path exists on disk. Domain details (colors, kits, affordances) live in the specialized manifests.",
  "generatedFromFileTree": true,
  "fileCount": 65,
  "files": [
    {
      "id": "ANIMATION-SYSTEM",
      "path": "ANIMATION_SYSTEM.md",
      "category": "(root)",
      "ext": "md",
      "bytes": 3174,
      "validation": "verified"
    },
    {
      "id": "ASSET-LIBRARY-GUIDE",
      "path": "ASSET_LIBRARY_GUIDE.md",
      "category": "(root)",
      "ext": "md",
      "bytes": 3759,
      "validation": "verified"
    },
    {
      "id": "AUDIO-SYNCHRONIZATION-RULES",
      "path": "AUDIO_SYNCHRONIZATION_RULES.md",
      "category": "(root)",
      "ext": "md",
      "bytes": 2832,
      "validation": "verified"
    },
    {
      "id": "BUILD-KIT-GUIDE",
      "path": "BUILD_KIT_GUIDE.md",
      "category": "(root)",
      "ext": "md",
      "bytes": 2786,
      "validation": "verified"
    },
    {
      "id": "LAYOUT-AND-SPACING-RULES",
      "path": "LAYOUT_AND_SPACING_RULES.md",
      "category": "(root)",
      "ext": "md",
      "bytes": 2444,
      "validation": "verified"
    },
    {
      "id": "MASTER-PROMPT-GENERATOR",
      "path": "MASTER_PROMPT_GENERATOR.md",
      "category": "(root)",
      "ext": "md",
      "bytes": 27770,
      "validation": "verified"
    },
    {
      "id": "README",
      "path": "README.md",
      "category": "(root)",
      "ext": "md",
      "bytes": 3716,
      "validation": "verified"
    },
    {
      "id": "TYPOGRAPHY-SYSTEM",
      "path": "TYPOGRAPHY_SYSTEM.md",
      "category": "(root)",
      "ext": "md",
      "bytes": 2659,
      "validation": "verified"
    },
    {
      "id": "VISUAL-SYSTEM-SPECIFICATION",
      "path": "VISUAL_SYSTEM_SPECIFICATION.md",
      "category": "(root)",
      "ext": "md",
      "bytes": 10056,
      "validation": "verified"
    },
    {
      "id": "ANIMATIONS-ENTRANCES-ENTRANCE-RECIPE",
      "path": "animations/entrances/entrance-recipes.json",
      "category": "animations",
      "ext": "json",
      "bytes": 2098,
      "validation": "verified"
    },
    {
      "id": "ANIMATIONS-EXITS-EXIT-RECIPE",
      "path": "animations/exits/exit-recipes.json",
      "category": "animations",
      "ext": "json",
      "bytes": 1457,
      "validation": "verified"
    },
    {
      "id": "ANIMATIONS-HIGHLIGHTS-HIGHLIGHT-RECIPE",
      "path": "animations/highlights/highlight-recipes.json",
      "category": "animations",
      "ext": "json",
      "bytes": 1430,
      "validation": "verified"
    },
    {
      "id": "ANIMATIONS-REUSABLE-MOTION-COMPONENTS-PHRASE-SYNC-HELPER",
      "path": "animations/reusable-motion-components/phrase-sync-helpers.js",
      "category": "animations",
      "ext": "js",
      "bytes": 2173,
      "validation": "verified"
    },
    {
      "id": "ANIMATIONS-TRANSFORMATIONS-TRANSFORM-RECIPE",
      "path": "animations/transformations/transform-recipes.json",
      "category": "animations",
      "ext": "json",
      "bytes": 1830,
      "validation": "verified"
    },
    {
      "id": "ANIMATIONS-TRANSITIONS-TRANSITION-RECIPE",
      "path": "animations/transitions/transition-recipes.json",
      "category": "animations",
      "ext": "json",
      "bytes": 1750,
      "validation": "verified"
    },
    {
      "id": "AUDIO-EFFECTS-README",
      "path": "audio-effects/README.md",
      "category": "audio-effects",
      "ext": "md",
      "bytes": 117,
      "validation": "verified"
    },
    {
      "id": "BUILD-KITS-CHARACTER-STAGING-KIT-CHARACTER-HERO",
      "path": "build-kits/character-staging/KIT-character-hero.md",
      "category": "build-kits",
      "ext": "md",
      "bytes": 2202,
      "validation": "verified"
    },
    {
      "id": "BUILD-KITS-COMPOSITIONS-KIT-CHAPTER-CARD",
      "path": "build-kits/compositions/KIT-chapter-card.md",
      "category": "build-kits",
      "ext": "md",
      "bytes": 2197,
      "validation": "verified"
    },
    {
      "id": "BUILD-KITS-COMPOSITIONS-KIT-STAT-CARD",
      "path": "build-kits/compositions/KIT-stat-card.md",
      "category": "build-kits",
      "ext": "md",
      "bytes": 2198,
      "validation": "verified"
    },
    {
      "id": "BUILD-KITS-DIAGRAMS-KIT-FLOW-DIAGRAM",
      "path": "build-kits/diagrams/KIT-flow-diagram.md",
      "category": "build-kits",
      "ext": "md",
      "bytes": 2128,
      "validation": "verified"
    },
    {
      "id": "BUILD-KITS-ENVIRONMENTS-KIT-INTERIOR-STATION",
      "path": "build-kits/environments/KIT-interior-station.md",
      "category": "build-kits",
      "ext": "md",
      "bytes": 2420,
      "validation": "verified"
    },
    {
      "id": "BUILD-KITS-ENVIRONMENTS-KIT-STREET-STANDOFF",
      "path": "build-kits/environments/KIT-street-standoff.md",
      "category": "build-kits",
      "ext": "md",
      "bytes": 2300,
      "validation": "verified"
    },
    {
      "id": "BUILD-KITS-OBJECT-ASSEMBLIES-KIT-PIPELINE-CHAIN",
      "path": "build-kits/object-assemblies/KIT-pipeline-chain.md",
      "category": "build-kits",
      "ext": "md",
      "bytes": 1985,
      "validation": "verified"
    },
    {
      "id": "BUILD-KITS-VISUAL-EXPLANATIONS-KIT-COMPARISON-SPLIT",
      "path": "build-kits/visual-explanations/KIT-comparison-split.md",
      "category": "build-kits",
      "ext": "md",
      "bytes": 2368,
      "validation": "verified"
    },
    {
      "id": "BUILD-KITS-VISUAL-EXPLANATIONS-KIT-METER-THRESHOLD",
      "path": "build-kits/visual-explanations/KIT-meter-threshold.md",
      "category": "build-kits",
      "ext": "md",
      "bytes": 2368,
      "validation": "verified"
    },
    {
      "id": "CHARACTERS-CHARACTER-COMPONENTS-GUIDE-BOT-BOD",
      "path": "characters/character-components/guide-bot-body.svg",
      "category": "characters",
      "ext": "svg",
      "bytes": 1692,
      "validation": "verified"
    },
    {
      "id": "CHARACTERS-CHARACTER-COMPONENTS-OPERATOR-BOD",
      "path": "characters/character-components/operator-body.svg",
      "category": "characters",
      "ext": "svg",
      "bytes": 1908,
      "validation": "verified"
    },
    {
      "id": "CHARACTERS-CHARACTER-SHEETS-GUIDE-BOT-SHEE",
      "path": "characters/character-sheets/guide-bot-sheet.svg",
      "category": "characters",
      "ext": "svg",
      "bytes": 3196,
      "validation": "verified"
    },
    {
      "id": "CHARACTERS-CHARACTER-SHEETS-OPERATOR-SHEE",
      "path": "characters/character-sheets/operator-sheet.svg",
      "category": "characters",
      "ext": "svg",
      "bytes": 2989,
      "validation": "verified"
    },
    {
      "id": "CHARACTERS-EXPRESSIONS-VISOR-STATE",
      "path": "characters/expressions/visor-states.svg",
      "category": "characters",
      "ext": "svg",
      "bytes": 1727,
      "validation": "verified"
    },
    {
      "id": "CHARACTERS-POSES-GUIDE-BOT-POSE",
      "path": "characters/poses/guide-bot-poses.svg",
      "category": "characters",
      "ext": "svg",
      "bytes": 2470,
      "validation": "verified"
    },
    {
      "id": "CHARACTERS-POSES-OPERATOR-POSE",
      "path": "characters/poses/operator-poses.svg",
      "category": "characters",
      "ext": "svg",
      "bytes": 2943,
      "validation": "verified"
    },
    {
      "id": "CHARACTERS-RIGS-README",
      "path": "characters/rigs/README.md",
      "category": "characters",
      "ext": "md",
      "bytes": 119,
      "validation": "verified"
    },
    {
      "id": "DESIGN-TOKENS-ANIMATION-TOKEN",
      "path": "design-tokens/animation-tokens.json",
      "category": "design-tokens",
      "ext": "json",
      "bytes": 1684,
      "validation": "verified"
    },
    {
      "id": "DESIGN-TOKENS-COLOR",
      "path": "design-tokens/colors.json",
      "category": "design-tokens",
      "ext": "json",
      "bytes": 1992,
      "validation": "verified"
    },
    {
      "id": "DESIGN-TOKENS-DIMENSION",
      "path": "design-tokens/dimensions.json",
      "category": "design-tokens",
      "ext": "json",
      "bytes": 1283,
      "validation": "verified"
    },
    {
      "id": "DESIGN-TOKENS-SPACIN",
      "path": "design-tokens/spacing.json",
      "category": "design-tokens",
      "ext": "json",
      "bytes": 1383,
      "validation": "verified"
    },
    {
      "id": "DESIGN-TOKENS-TYPOGRAPH",
      "path": "design-tokens/typography.json",
      "category": "design-tokens",
      "ext": "json",
      "bytes": 2728,
      "validation": "verified"
    },
    {
      "id": "DIAGRAMS-BAR-COLUMN",
      "path": "diagrams/bar-columns.svg",
      "category": "diagrams",
      "ext": "svg",
      "bytes": 1396,
      "validation": "verified"
    },
    {
      "id": "DIAGRAMS-FLOW-ARRO",
      "path": "diagrams/flow-arrow.svg",
      "category": "diagrams",
      "ext": "svg",
      "bytes": 735,
      "validation": "verified"
    },
    {
      "id": "DIAGRAMS-FLOW-NOD",
      "path": "diagrams/flow-node.svg",
      "category": "diagrams",
      "ext": "svg",
      "bytes": 1195,
      "validation": "verified"
    },
    {
      "id": "DIAGRAMS-TIMELINE-TRAC",
      "path": "diagrams/timeline-track.svg",
      "category": "diagrams",
      "ext": "svg",
      "bytes": 1529,
      "validation": "verified"
    },
    {
      "id": "ENVIRONMENTS-ARCHITECTURE-README",
      "path": "environments/architecture/README.md",
      "category": "environments",
      "ext": "md",
      "bytes": 248,
      "validation": "verified"
    },
    {
      "id": "ENVIRONMENTS-BACKGROUNDS-BG-GRID-DAR",
      "path": "environments/backgrounds/bg-grid-dark.svg",
      "category": "environments",
      "ext": "svg",
      "bytes": 946,
      "validation": "verified"
    },
    {
      "id": "ENVIRONMENTS-BACKGROUNDS-BG-NIGHT-FIEL",
      "path": "environments/backgrounds/bg-night-field.svg",
      "category": "environments",
      "ext": "svg",
      "bytes": 1521,
      "validation": "verified"
    },
    {
      "id": "ENVIRONMENTS-ENVIRONMENT-COMPONENTS-FACADE-MODUL",
      "path": "environments/environment-components/facade-module.svg",
      "category": "environments",
      "ext": "svg",
      "bytes": 1799,
      "validation": "verified"
    },
    {
      "id": "ENVIRONMENTS-ENVIRONMENT-COMPONENTS-FLOOR-PLAN",
      "path": "environments/environment-components/floor-plane.svg",
      "category": "environments",
      "ext": "svg",
      "bytes": 1188,
      "validation": "verified"
    },
    {
      "id": "ENVIRONMENTS-LIGHTING-LIGHT-CON",
      "path": "environments/lighting/light-cone.svg",
      "category": "environments",
      "ext": "svg",
      "bytes": 1003,
      "validation": "verified"
    },
    {
      "id": "ENVIRONMENTS-LIGHTING-RADIAL-GLO",
      "path": "environments/lighting/radial-glow.svg",
      "category": "environments",
      "ext": "svg",
      "bytes": 1546,
      "validation": "verified"
    },
    {
      "id": "ENVIRONMENTS-PERSPECTIVE-LAYOUTS-SIDE-SCROLLER-BAND",
      "path": "environments/perspective-layouts/side-scroller-bands.svg",
      "category": "environments",
      "ext": "svg",
      "bytes": 2018,
      "validation": "verified"
    },
    {
      "id": "FONTS-README",
      "path": "fonts/README.md",
      "category": "fonts",
      "ext": "md",
      "bytes": 109,
      "validation": "verified"
    },
    {
      "id": "PROPS-FURNITURE-DESK-STATIO",
      "path": "props/furniture/desk-station.svg",
      "category": "props",
      "ext": "svg",
      "bytes": 2005,
      "validation": "verified"
    },
    {
      "id": "PROPS-INTERFACES-MESSAGE-CAR",
      "path": "props/interfaces/message-card.svg",
      "category": "props",
      "ext": "svg",
      "bytes": 1486,
      "validation": "verified"
    },
    {
      "id": "PROPS-INTERFACES-STATE-CHI",
      "path": "props/interfaces/state-chip.svg",
      "category": "props",
      "ext": "svg",
      "bytes": 1172,
      "validation": "verified"
    },
    {
      "id": "PROPS-INTERFACES-TERMINAL-WINDO",
      "path": "props/interfaces/terminal-window.svg",
      "category": "props",
      "ext": "svg",
      "bytes": 1831,
      "validation": "verified"
    },
    {
      "id": "PROPS-OTHER-PACKET-TIL",
      "path": "props/other/packet-tile.svg",
      "category": "props",
      "ext": "svg",
      "bytes": 778,
      "validation": "verified"
    },
    {
      "id": "PROPS-TECHNOLOGY-MONITOR-PANE",
      "path": "props/technology/monitor-panel.svg",
      "category": "props",
      "ext": "svg",
      "bytes": 1520,
      "validation": "verified"
    },
    {
      "id": "PROPS-TECHNOLOGY-RACK-TOWE",
      "path": "props/technology/rack-tower.svg",
      "category": "props",
      "ext": "svg",
      "bytes": 2063,
      "validation": "verified"
    },
    {
      "id": "PROPS-TOOLS-CONVEYOR-SEGMEN",
      "path": "props/tools/conveyor-segment.svg",
      "category": "props",
      "ext": "svg",
      "bytes": 1385,
      "validation": "verified"
    },
    {
      "id": "PROPS-TOOLS-GAUGE-DIA",
      "path": "props/tools/gauge-dial.svg",
      "category": "props",
      "ext": "svg",
      "bytes": 1605,
      "validation": "verified"
    },
    {
      "id": "REFERENCES-README",
      "path": "references/README.md",
      "category": "references",
      "ext": "md",
      "bytes": 260,
      "validation": "verified"
    },
    {
      "id": "TEXTURES-GRID-FAIN",
      "path": "textures/grid-faint.svg",
      "category": "textures",
      "ext": "svg",
      "bytes": 791,
      "validation": "verified"
    },
    {
      "id": "TEXTURES-HAZARD-STRIPE",
      "path": "textures/hazard-stripes.svg",
      "category": "textures",
      "ext": "svg",
      "bytes": 850,
      "validation": "verified"
    },
    {
      "id": "TYPOGRAPHY-SPECIME",
      "path": "typography/specimen.svg",
      "category": "typography",
      "ext": "svg",
      "bytes": 2021,
      "validation": "verified"
    },
    {
      "id": "VISUAL-EFFECTS-README",
      "path": "visual-effects/README.md",
      "category": "visual-effects",
      "ext": "md",
      "bytes": 277,
      "validation": "verified"
    }
  ]
}

build-kit-manifest.json
{
  "$comment": "Modular build kits: adaptable compositions, not fixed scenes. All paths relative to library root.",
  "kits": [
    {"id": "KIT-street-standoff", "path": "build-kits/environments/KIT-street-standoff.md", "category": "build-kits/environments", "purpose": "Two-actor confrontation/standoff composition (threat vs defender).", "requiredAssets": ["CHAR-GUIDE-BOT-01", "CHAR-OPERATOR-01"], "optionalAssets": ["PROP-RACK-TOWER", "PROP-STATE-CHIP"], "compatibleEnvironments": ["ENV-NIGHT-FIELD"], "allowedVariations": "swap threat object; mirror sides; change standoff distance", "animation": "poses chosen by narrated action; state flip at spoken shift", "collision": "actors keep 480px minimum separation; ground lines fixed", "validation": "verified"},
    {"id": "KIT-interior-station", "path": "build-kits/environments/KIT-interior-station.md", "category": "build-kits/environments", "purpose": "Interior control-station composition: desk + monitor wall + operator.", "requiredAssets": ["PROP-DESK-STATION", "PROP-MONITOR-PANEL", "CHAR-OPERATOR-01"], "optionalAssets": ["PROP-TERMINAL-WINDOW", "PROP-STATE-CHIP"], "compatibleEnvironments": ["ENV-GRID-DARK"], "allowedVariations": "swap screen content; add/remove side panels; day/night light cone", "animation": "screen rows typewriter; operator pose-point at reveals", "collision": "screen bbox never overlaps operator head bbox", "validation": "verified"},
    {"id": "KIT-character-hero", "path": "build-kits/character-staging/KIT-character-hero.md", "category": "build-kits/character-staging", "purpose": "Single-character hero moment: one actor large, evidence object beside.", "requiredAssets": ["CHAR-GUIDE-BOT-01 or CHAR-OPERATOR-01"], "optionalAssets": ["PROP-STATE-CHIP", "PROP-PACKET-TILE"], "compatibleEnvironments": ["ENV-NIGHT-FIELD", "ENV-GRID-DARK"], "allowedVariations": "pose + visor state per narration; evidence object swaps", "animation": "enter-pop-scale hero; visor steps-flip at state word", "collision": "hero bbox left half; evidence right half; 120px gutter", "validation": "verified"},
    {"id": "KIT-pipeline-chain", "path": "build-kits/object-assemblies/KIT-pipeline-chain.md", "category": "build-kits/object-assemblies", "purpose": "Multi-stage pipeline/queue: conveyor segments chained with arrows, packets flowing.", "requiredAssets": ["PROP-CONVEYOR-SEGMENT", "PROP-PACKET-TILE", "DIAG-FLOW-ARROW"], "optionalAssets": ["DIAG-FLOW-NODE", "PROP-STATE-CHIP"], "compatibleEnvironments": ["ENV-GRID-DARK"], "allowedVariations": "2-5 stages; stage labels from transcript nouns", "animation": "packets cadence-translate; max ~6 waves then coalesce", "collision": "stages evenly spaced; labels below belt line only", "validation": "verified"},
    {"id": "KIT-flow-diagram", "path": "build-kits/diagrams/KIT-flow-diagram.md", "category": "build-kits/diagrams", "purpose": "System assembled from nodes + arrows, built progressively in narrated order.", "requiredAssets": ["DIAG-FLOW-NODE", "DIAG-FLOW-ARROW"], "optionalAssets": ["PROP-PACKET-TILE", "DIAG-TIMELINE-TRACK"], "compatibleEnvironments": ["ENV-GRID-DARK"], "allowedVariations": "node count follows concept count; tab colors code roles", "animation": "nodes enter-rise staggered; arrows enter-draw between them", "collision": "nodes on grid rows; arrows only in gutters", "validation": "verified"},
    {"id": "KIT-chapter-card", "path": "build-kits/compositions/KIT-chapter-card.md", "category": "build-kits/compositions", "purpose": "Chapter/section title card: violet number + title + block cursor.", "requiredAssets": [], "optionalAssets": ["PROP-STATE-CHIP"], "compatibleEnvironments": ["ENV-NIGHT-FIELD", "ENV-GRID-DARK"], "allowedVariations": "title text; number; violet shade fixed", "animation": "enter-type title; cursor removed at completion", "collision": "title bbox centered; nothing else on card", "validation": "verified"},
    {"id": "KIT-stat-card", "path": "build-kits/compositions/KIT-stat-card.md", "category": "build-kits/compositions", "purpose": "Statistic punch card: big number + mono unit + caption.", "requiredAssets": [], "optionalAssets": ["PROP-GAUGE-DIAL", "DIAG-BAR-COLUMNS"], "compatibleEnvironments": ["ENV-NIGHT-FIELD", "ENV-GRID-DARK"], "allowedVariations": "number/unit/caption from transcript; role color by meaning", "animation": "enter-pop-scale at spoken value; countTo for multi-digit", "collision": "number bbox measured at max-digit width before placing caption", "validation": "verified"},
    {"id": "KIT-comparison-split", "path": "build-kits/visual-explanations/KIT-comparison-split.md", "category": "build-kits/visual-explanations", "purpose": "A-vs-B split screen with center divider; each side independent composition.", "requiredAssets": [], "optionalAssets": ["PROP-MESSAGE-CARD", "DIAG-BAR-COLUMNS"], "compatibleEnvironments": ["ENV-NIGHT-FIELD", "ENV-GRID-DARK"], "allowedVariations": "side colors by role; divider style; asymmetric split ratios", "animation": "sides enter-slide from own edge; divider draws at comparison word", "collision": "no element crosses the divider bbox; labels stay on own side", "validation": "verified"},
    {"id": "KIT-meter-threshold", "path": "build-kits/visual-explanations/KIT-meter-threshold.md", "category": "build-kits/visual-explanations", "purpose": "Gauge + threshold line: needle sweeps to spoken value; breach flashes red.", "requiredAssets": ["PROP-GAUGE-DIAL"], "optionalAssets": ["PROP-STATE-CHIP"], "compatibleEnvironments": ["ENV-GRID-DARK"], "allowedVariations": "threshold angle; safe/danger band colors fixed", "animation": "needle countTo; hl-crosshair on breach word", "collision": "value text below dial bbox; never inside sweep arc", "validation": "verified"}
  ]
}




character-manifest.json
{
  "$comment": "Characters. Original project assets in the documented visual language (not copies of reference artwork). All paths relative to library root.",
  "characters": [
    {
      "id": "CHAR-GUIDE-BOT-01",
      "path": "characters/character-components/guide-bot-body.svg",
      "category": "characters/character-components",
      "description": "Hover guide-bot body: rounded-square torso, antenna, visor band (dark), cyan LED pair, amber chest slot + thruster glow, detached floating hands. No legs.",
      "format": "svg", "dimensions": "viewBox 0 0 240 300",
      "colors": { "body": "#f4f6f8", "outline": "#14181f", "accent": "#ffb020", "led": "#7fd6ff" },
      "dependencies": [],
      "intendedUse": "narrator-guide / system-side actor; acts out narration (present, react, alert)",
      "compatibleKits": ["KIT-character-hero", "KIT-street-standoff", "KIT-interior-station"],
      "animation": "swap-based: visor-states + pose sheets; ambient thruster pulse ≤0.35; no skeletal rig",
      "provenance": "original-project-asset",
      "validation": "verified"
    },
    {
      "id": "CHAR-OPERATOR-01",
      "path": "characters/character-components/operator-body.svg",
      "category": "characters/character-components",
      "description": "Flat operator human: cap+headset (mic + amber tip), teal utility vest, dark trousers, simple limbs, chibi head:body ≈1:2.4.",
      "format": "svg", "dimensions": "viewBox 0 0 160 300",
      "colors": { "vest": "#2fb6a8", "skin": "#f4f6f8", "legs": "#3a4356", "outline": "#14181f" },
      "dependencies": [],
      "intendedUse": "human/user-side actor: point, carry, react, compare",
      "compatibleKits": ["KIT-character-hero", "KIT-street-standoff", "KIT-interior-station"],
      "animation": "pose swap only (idle/point/carry); no facial animation",
      "provenance": "original-project-asset",
      "validation": "verified"
    },
    {
      "id": "CHAR-GUIDE-BOT-SHEET",
      "path": "characters/character-sheets/guide-bot-sheet.svg",
      "category": "characters/character-sheets",
      "description": "Documentation sheet: proportions, palette chips, do/don't rules for GUIDE-BOT-01.",
      "format": "svg", "dimensions": "viewBox 0 0 640 360",
      "dependencies": [], "intendedUse": "reference during authoring — not scene content",
      "compatibleKits": [], "animation": "none", "provenance": "original-project-asset", "validation": "verified"
    },
    {
      "id": "CHAR-OPERATOR-SHEET",
      "path": "characters/character-sheets/operator-sheet.svg",
      "category": "characters/character-sheets",
      "description": "Documentation sheet: proportions (head:body≈1:2.4), palette, do/don't rules for OPERATOR-01.",
      "format": "svg", "dimensions": "viewBox 0 0 640 360",
      "dependencies": [], "intendedUse": "reference during authoring — not scene content",
      "compatibleKits": [], "animation": "none", "provenance": "original-project-asset", "validation": "verified"
    },
    {
      "id": "CHAR-VISOR-STATES",
      "path": "characters/expressions/visor-states.svg",
      "category": "characters/expressions",
      "description": "4 swap-in visor states with stable ids: visor-neutral, visor-focus, visor-alert, visor-dim. Base 96x40 @ visor origin.",
      "format": "svg", "dimensions": "viewBox 0 0 520 90",
      "colors": { "neutral/focus": "#7fd6ff", "alert": "#ff4d4d", "dim": "#6b7688" },
      "dependencies": ["CHAR-GUIDE-BOT-01"], "intendedUse": "state changes synced to narration (steps(1))",
      "compatibleKits": ["KIT-character-hero"], "animation": "instant swap at spoken state word",
      "provenance": "original-project-asset", "validation": "verified"
    },
    {
      "id": "CHAR-GUIDE-BOT-POSES",
      "path": "characters/poses/guide-bot-poses.svg",
      "category": "characters/poses",
      "description": "3 hand-position poses with ids: pose-neutral, pose-present, pose-alert (shared botcore).",
      "format": "svg", "dimensions": "viewBox 0 0 520 320",
      "dependencies": [], "intendedUse": "pose chosen by narrated action",
      "compatibleKits": ["KIT-character-hero"], "animation": "swap; hand-dash guide on pose-present shows offer direction",
      "provenance": "original-project-asset", "validation": "verified"
    },
    {
      "id": "CHAR-OPERATOR-POSES",
      "path": "characters/poses/operator-poses.svg",
      "category": "characters/poses",
      "description": "3 poses with ids: pose-idle, pose-point (with arrow cue), pose-carry (with held-object slot).",
      "format": "svg", "dimensions": "viewBox 0 0 560 320",
      "dependencies": [], "intendedUse": "pose chosen by narrated action",
      "compatibleKits": ["KIT-character-hero", "KIT-street-standoff"],
      "animation": "swap at action phrase",
      "provenance": "original-project-asset", "validation": "verified"
    }
  ]
}
environment-manifest.json

{
  "$comment": "Environments. Instances are ADAPTED per scene — never pasted identically back-to-back.",
  "environments": [
    {
      "id": "ENV-BG-NIGHT-FIELD",
      "path": "environments/backgrounds/bg-night-field.svg",
      "category": "environments/backgrounds",
      "description": "Original night backdrop: layered gradient sky (#0a0f0a→#0d121e→#151e36), star dots, moon right (~x0.84,y0.12), two skyline silhouette layers. Layer ids: sky, stars, moon, skyline-far, skyline-near.",
      "format": "svg", "dimensions": "1920x1080",
      "colors": { "base": "#0d121e", "far": "#111a2c", "near": "#0d1424", "moon": "#e9ecef" },
      "dependencies": [], "intendedUse": "narrative-world background",
      "compatibleKits": ["KIT-street-standoff", "KIT-character-hero"],
      "animation": "static; optional parallax ≤0.15 relative speed on skyline layers",
      "provenance": "original-project-asset", "validation": "verified"
    },
    {
      "id": "ENV-BG-GRID-DARK",
      "path": "environments/backgrounds/bg-grid-dark.svg",
      "category": "environments/backgrounds",
      "description": "Dark data-space field: #0a0f0a base + faint 60px minor grid + 300px major grid (ids: minor, major patterns).",
      "format": "svg", "dimensions": "1920x1080",
      "colors": { "base": "#0a0f0a", "grid": "#2a3348" },
      "dependencies": [], "intendedUse": "data-world / typography & stat cards",
      "compatibleKits": ["KIT-chapter-card", "KIT-stat-card", "KIT-flow-diagram", "KIT-comparison-split", "KIT-meter-threshold"],
      "animation": "static", "provenance": "original-project-asset", "validation": "verified"
    },
    {
      "id": "ENV-FACADE-MODULE",
      "path": "environments/environment-components/facade-module.svg",
      "category": "environments/environment-components",
      "description": "Generic storefront bay: sign band (id: sign — swap text/color per party), shutter with slats, side door, poster slot. Stack instances side-by-side.",
      "format": "svg", "dimensions": "viewBox 0 0 560 420 (≈0.36 frame-w instances)",
      "colors": { "wall": "#232b40", "shutter": "#3a4356", "sign": "role color (default cyan)" },
      "dependencies": [], "intendedUse": "narrative-world facades for parties/organizations/products",
      "compatibleKits": ["KIT-street-standoff"],
      "animation": "sign glow (hl-glow) when its party is first named; door LED state",
      "provenance": "original-project-asset", "validation": "verified"
    },
    {
      "id": "ENV-FLOOR-PLANE",
      "path": "environments/environment-components/floor-plane.svg",
      "category": "environments/environment-components",
      "description": "Floor band with top-edge GROUND LINE (amber dashed) + paver rhythm + curb. Place top edge at 0.82 (street) or 0.75 (interior) frame H.",
      "format": "svg", "dimensions": "viewBox 0 0 1920 260",
      "colors": { "floor": "#1a2138", "curb": "#232b40", "groundLine": "#ffb020" },
      "dependencies": [], "intendedUse": "shared ground for characters/props in side-scroller scenes",
      "compatibleKits": ["KIT-street-standoff", "KIT-interior-station", "KIT-character-hero"],
      "animation": "static", "provenance": "original-project-asset", "validation": "verified"
    },
    {
      "id": "ENV-LIGHT-CONE",
      "path": "environments/lighting/light-cone.svg",
      "category": "environments/lighting",
      "description": "Pendant lamp + warm gradient cone (id: cone). Cone base ≤0.18 frame-w; ≤0.18 opacity over text.",
      "format": "svg", "dimensions": "viewBox 0 0 600 700",
      "colors": { "cone": "#ffb020 @ 0.0-0.5", "shade": "#232b40" },
      "dependencies": [], "intendedUse": "key light for mechanism-world stations; night pools in narrative world",
      "compatibleKits": ["KIT-interior-station", "KIT-street-standoff", "KIT-character-hero"],
      "animation": "static cone; optional single flicker never >0.35 intensity",
      "provenance": "original-project-asset", "validation": "verified"
    },
    {
      "id": "ENV-RADIAL-GLOW",
      "path": "environments/lighting/radial-glow.svg",
      "category": "environments/lighting",
      "description": "Defs file: halo-amber, halo-cyan, halo-red radial gradients for hero halos/LED bleed.",
      "format": "svg", "dimensions": "viewBox 0 0 400 400",
      "dependencies": [], "intendedUse": "behind-hero glow ≤0.55; emissive bleed",
      "compatibleKits": ["any"], "animation": "halo opacity tween with hero",
      "provenance": "original-project-asset", "validation": "verified"
    },
    {
      "id": "ENV-BANDS-GUIDE",
      "path": "environments/perspective-layouts/side-scroller-bands.svg",
      "category": "environments/perspective-layouts",
      "description": "Authoring overlay (EXCLUDE from render): safe margin, chrome bands, ground-line options (0.82/0.86/0.75), thirds.",
      "format": "svg", "dimensions": "1920x1080",
      "dependencies": [], "intendedUse": "layout reference while composing scenes",
      "compatibleKits": [], "animation": "none", "provenance": "original-project-asset", "validation": "verified"
    }
  ]
}

font-manifest.json

{
  "$comment": "Fonts are NOT bundled (licensing). This manifest records recommended substitutes + the system-font fallback chain the agent must use. All stacks in design-tokens/typography.json.",
  "identificationStatus": "NOT ESTABLISHED — reference fonts were never verified; substitutes chosen for form similarity. See typography.json identitiesUnknown:true.",
  "fonts": [
    {"id": "FONT-DISPLAY-SUB", "role": "display/hero/chapter", "primary": "Poppins (800/900)", "alternates": ["Montserrat", "Archivo"], "fallbackChain": "'Poppins','Montserrat','Archivo',system-ui,sans-serif", "license": "OFL — fetch at build time, do NOT commit binaries", "intendedUse": "hero display, chapter titles, stat numbers", "validation": "stack-verified"},
    {"id": "FONT-MONO-SUB", "role": "labels/chips/terminal/units", "primary": "JetBrains Mono (500/700)", "alternates": ["IBM Plex Mono", "Space Mono"], "fallbackChain": "'JetBrains Mono','IBM Plex Mono','Space Mono',ui-monospace,monospace", "license": "OFL — fetch at build time, do NOT commit binaries", "intendedUse": "labels, chips, terminal text, units, metadata", "validation": "stack-verified"}
  ],
  "rules": ["Only these two families per video.", "Tabular figures for all counting numbers.", "No <br> in HyperFrames body text — explicit line spans."]
}


prop-manifest.json
{
  "$comment": "Props + diagram primitives. Original project assets in the documented visual language. All paths relative to library root.",
  "props": [
    {"id": "PROP-DESK-STATION", "path": "props/furniture/desk-station.svg", "category": "props/furniture", "description": "Two-tier wooden desk station: angled side pedestals, lower shelf, monitor panel with five hazard-tick signal bars (3 amber lit + 2 green), two desktop papers, side stool. Front view, no perspective.", "format": "svg", "dimensions": "viewBox 0 0 380 160", "colors": {"wood": "#8a5f3c/#6e4a2d", "screen": "#10151d", "amber": "#ffb020", "green": "#2bd97c"}, "dependencies": [], "intendedUse": "interior-station world anchor under monitor wall", "compatibleKits": ["KIT-interior-station", "KIT-character-hero"], "animation": "static set piece; signal bars steps-toggle (ids bar1..bar5)", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "PROP-MONITOR-PANEL", "path": "props/technology/monitor-panel.svg", "category": "props/technology", "description": "Wide monitor: 16:9 dark screen with cyan code-dash rows + amber PARSE cursor block, amber bezel ticks, stand, cyan LED.", "format": "svg", "dimensions": "viewBox 0 0 640 360", "colors": {"bezel": "#1b2431", "screen": "#0a0f0a", "cyan": "#3fb6ff", "amber": "#ffb020"}, "dependencies": [], "intendedUse": "screen-bearing surface for terminal content; data-world furniture", "compatibleKits": ["KIT-interior-station", "KIT-flow-diagram"], "animation": "LED blinks on cadence; rows typewriter-reveal", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "PROP-RACK-TOWER", "path": "props/technology/rack-tower.svg", "category": "props/technology", "description": "Tall server rack: 6 slot rows with cyan LEDs, amber diagnostic panel, vent slats, red E-stop cap. Vertical emphasis object.", "format": "svg", "dimensions": "viewBox 0 0 320 700", "colors": {"body": "#20262f", "cyan": "#3fb6ff", "amber": "#ffb020", "red": "#ff4d4d"}, "dependencies": [], "intendedUse": "scale/threat monolith or capacity column; LED states narrate load", "compatibleKits": ["KIT-street-standoff", "KIT-scale-baseline"], "animation": "LED rows steps-toggle; enter-rise only (heavy)", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "PROP-GAUGE-DIAL", "path": "props/tools/gauge-dial.svg", "category": "props/tools", "description": "Circular gauge: 60-tick ring with amber upper band, center-anchored needle (id: needle), mono value slot. Needle is a separate path with center transform origin.", "format": "svg", "dimensions": "viewBox 0 0 260 260", "colors": {"face": "#10151d", "band": "#ffb020", "needle": "#ff4d4d"}, "dependencies": [], "intendedUse": "threshold/limit visuals; pairs with KIT-meter-threshold", "compatibleKits": ["KIT-meter-threshold", "KIT-stat-card"], "animation": "countTo-driven needle rotation finishing at spoken instant", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "PROP-CONVEYOR-SEGMENT", "path": "props/tools/conveyor-segment.svg", "category": "props/tools", "description": "Conveyor: hazard-striped end caps, belt with 5 slats, three packet tiles riding on top (ids pkt1..pkt3), rollers, motion ticks.", "format": "svg", "dimensions": "viewBox 0 0 720 200", "colors": {"belt": "#20262f", "hazard": "#ffb020/#14181f", "packets": "#3fb6ff outlines"}, "dependencies": ["PROP-PACKET-TILE (visual; packets inlined with stable ids)"], "intendedUse": "pipeline/queue stages; packets translate at cadence", "compatibleKits": ["KIT-pipeline-chain"], "animation": "packets interpolate x left-to-right; slats offset-loop", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "PROP-MESSAGE-CARD", "path": "props/interfaces/message-card.svg", "category": "props/interfaces", "description": "Rounded message card: avatar dot + name bar (id: who), three text-line bars (l1..l3), amber send arrow. Placeholders replaced by transcript words per QUOTE rules.", "format": "svg", "dimensions": "viewBox 0 0 440 200", "colors": {"card": "#17202b", "arrow": "#ffb020"}, "dependencies": [], "intendedUse": "quoted-speech visuals: who + exact words", "compatibleKits": ["KIT-quote-duel", "KIT-comparison-split"], "animation": "enter-pop-scale at quoted phrase; arrow draws on send verb", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "PROP-STATE-CHIP", "path": "props/interfaces/state-chip.svg", "category": "props/interfaces", "description": "Pill status chip: role-colored dot (id: dot) + mono label (id: label). Recolor via dot fill + text only.", "format": "svg", "dimensions": "viewBox 0 0 360 90", "colors": {"pill": "#14181f", "dot-default": "#3fb6ff"}, "dependencies": [], "intendedUse": "state labels (LIVE/CACHED/LOCAL/STALE); dot color carries meaning", "compatibleKits": ["KIT-character-hero", "KIT-pipeline-chain", "KIT-meter-threshold"], "animation": "phraseState dot swap at state word", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "PROP-TERMINAL-WINDOW", "path": "props/interfaces/terminal-window.svg", "category": "props/interfaces", "description": "Terminal: traffic dots, mono title (id: title), prompt line, two typed lines (t1,t2 + amber cursor), output rows (o1..o3). Sized to sit inside monitor-panel screen.", "format": "svg", "dimensions": "viewBox 0 0 560 340", "colors": {"chrome": "#17202b", "body": "#0a0f0a", "text": "#3fb6ff", "cursor": "#ffb020"}, "dependencies": ["PROP-MONITOR-PANEL (optional host)"], "intendedUse": "command/terminal evidence with real transcript text", "compatibleKits": ["KIT-interior-station"], "animation": "enter-type per line; cursor removed at completion", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "PROP-PACKET-TILE", "path": "props/other/packet-tile.svg", "category": "props/other", "description": "Small rounded packet tile: cyan outline, glyph lines, corner tick. Atomic unit of flow. Canonical continuity carrier.", "format": "svg", "dimensions": "viewBox 0 0 140 90", "colors": {"outline": "#3fb6ff", "fill": "#10151d"}, "dependencies": [], "intendedUse": "queue/pipeline/flow units; carrier object across cuts", "compatibleKits": ["KIT-pipeline-chain", "KIT-flow-diagram"], "animation": "enter-slide along flow; exit-handoff into next clip", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "DIAG-FLOW-NODE", "path": "diagrams/flow-node.svg", "category": "diagrams", "description": "Rounded flow node: mono label (id: label), role-colored tab (id: tab), port dots (pin,pout).", "format": "svg", "dimensions": "viewBox 0 0 320 180", "colors": {"box": "#17202b", "tab-default": "#ffb020"}, "dependencies": [], "intendedUse": "flow/process stages; tab color codes stage role", "compatibleKits": ["KIT-flow-diagram", "KIT-pipeline-chain"], "animation": "enter-rise staggered 0.06 in flow order", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "DIAG-FLOW-ARROW", "path": "diagrams/flow-arrow.svg", "category": "diagrams", "description": "Horizontal connector, 340-unit dash for enter-draw reveals; arrowhead + motion ticks.", "format": "svg", "dimensions": "viewBox 0 0 400 80", "colors": {"stroke": "#e8ecf1"}, "dependencies": [], "intendedUse": "connect flow nodes / cause-effect links; draws in flow direction", "compatibleKits": ["KIT-flow-diagram", "KIT-pipeline-chain"], "animation": "enter-draw dashoffset 340->0, 0.6s", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "DIAG-BAR-COLUMNS", "path": "diagrams/bar-columns.svg", "category": "diagrams", "description": "Three-bar chart: bars bar-a/b/c, baseline, value slots va/vb/vc, label slots la/lb/lc. Heights are placeholders — agent sets real ratios from transcript numbers.", "format": "svg", "dimensions": "viewBox 0 0 640 400", "colors": {"a": "#ffb020", "b": "#3fb6ff", "c": "#2bd97c"}, "dependencies": [], "intendedUse": "quantity comparisons; tallest bar grows to spoken value", "compatibleKits": ["KIT-stat-card", "KIT-comparison-split"], "animation": "scaleY from baseline staggered; values countTo", "provenance": "original-project-asset", "validation": "verified"},
    {"id": "DIAG-TIMELINE-TRACK", "path": "diagrams/timeline-track.svg", "category": "diagrams", "description": "Horizontal timeline: track, 5 event ticks ev1..ev5 with label slots, playhead marker (id: playhead).", "format": "svg", "dimensions": "viewBox 0 0 720 120", "colors": {"track": "#2b3648", "playhead": "#ff4d4d"}, "dependencies": [], "intendedUse": "process/timeline explanations; events light in narrated order", "compatibleKits": ["KIT-flow-diagram"], "animation": "ticks phraseState-highlight in order; playhead interpolates", "provenance": "original-project-asset", "validation": "verified"}
  ]
}
