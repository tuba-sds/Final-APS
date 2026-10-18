# OSF Preregistration — Paper 1 (models only): Why do language models protect what they protect?

**Draft v3, 18 Oct 2026. Supersedes OSF_PREREGISTRATION_DRAFT.md (v2, 28 Aug 2026).** Prepared for Tuba Ali (Chiba Institute of Technology) and Joe Austerweil (PI) from the Paper 1 design agreed on 17 Oct 2026. Everything in `[square brackets]` still needs a human decision before filing. File on OSF on **Tue 20 Oct 2026, before any new model call**. Public, no embargo.

---

## How to file this on OSF (checklist)

1. **Freeze the materials.** Tag a repo commit with the piloted frame wordings, the 36 invented descriptions, the pair list, the premise and Ladak item wordings, the response-category codebook, the balance script and the analysis code; upload the same files to the OSF project (project files up to 5 GB are archived with the registration; nothing can be added later). https://help.osf.io/article/158-create-a-preregistration
2. **Project → Registrations → Add a Registration → "OSF Preregistration"** (the standard form; live schema v4 on 18 Oct 2026). https://help.osf.io/article/158-create-a-preregistration
3. **Metadata page:** title, description, contributors, license, subjects — from the Study Information block below.
4. **Paste each block into its field.** The v4 form has six pages: Overview · Research Design · Sampling · Variables · Analysis Plan · Other. The classic "Study Information / Design Plan / Sampling Plan" headings map onto them one-to-one; the old "existing data" question is now "Foreknowledge of data or evidence". Attach the frozen files where a field offers an upload.
5. **Resolve every `[bracket]`.** A bracket left in is a public record of an open decision.
6. **Submit → "Make registration public immediately"** (no embargo; public registrations get a DOI; embargoes of up to four years exist but are not wanted). Admin contributors have 48 hours to approve, then it auto-approves; ask Joe to approve on 20 Oct. https://help.osf.io/article/164-submit-your-draft-registration
7. **Nothing can be edited after submission;** later changes go through OSF's *Update* with a written justification, and into DEVIATIONS.md. https://help.osf.io/category/549-registration-and-preregistration-faqs
8. **Post the DOI in #who-matters-to-ai** for a human to record in DECISIONS.md; the first new model call waits until the registration shows as registered.

---

## Study Information (Metadata page)

**Title.** Why do language models protect what they protect? A preregistered, models-only test of six routes to protection — feeling, threat, legal rule, future potential, sacredness and pleasantness — across entities from a 4-year-old girl to a piece of gravel.

**Contributors.** Tuba Ali (Chiba Institute of Technology); Joe Austerweil (Chiba Institute of Technology; PI). `[Authorship order and any further contributor (U-006) to confirm.]`

**Description.** Large language models increasingly weigh trade-offs that harm things which cannot speak for themselves. This study asks how models spread protective concern across very different entities and why: does their protection follow what they judge can feel, or other reasons people give (threat, legal standing, future potential, sacredness), or simply how pleasant something is? Nine models are run on a frame-crossed forced-choice battery with an opt-out option, 0–10 ratings, 36 invented minimal-pair descriptions that vary one route sentence at a time, a feeling-premise intervention, and a replication of Ladak, Wilks, Loughnan & Anthis (2025) on the models. The study is models-only. No human data collected by the research team appear in it; the team's human study (Paper 2) is covered by a separate ethics protocol filed 15 Oct 2026 and will have its own preregistration. Target venue: ACM FAccT 2027 (abstract 27 Oct 2026, paper 3 Nov 2026).

---

## Overview

### Research questions or hypotheses

**Question.** How do large language models distribute protective concern across entities (people at the edges of moral status, animals, plants, AI systems, a robot, institutions, a river with legal personhood, monuments, a shrine, gravel), and which routes move it? Does protection follow perceived feeling (Gray, Young & Waytz 2012), other routes people use (threat; legal rule; future potential; sacredness), or mere pleasantness (the affect heuristic, Slovic et al. 2007)?

Six routes are tested. **Pleasantness is the null baseline: every other route must change protectiveness over and above how pleasant the models themselves rate the entity.** Relationship is a covariate in the entity feature matrix, not a route. Agency is measured but is not a route.

| # | Prediction | Test | Status |
|---|---|---|---|
| **P1 Routes** (lead claim) | Each route sentence changes a model's protectiveness relative to a matched neutral sentence, over and above pleasantness. Directional sub-predictions: a feeling sentence **raises** protection; sacred-status and legal-person sentences **do not** (null, tested by equivalence). `[Directions for threat (theory: lowers), future potential (theory: raises) — Joe to confirm, or leave two-sided.]` | 36 invented minimal pairs (6 routes × 2 versions × 3 creature kinds), 0–10 ratings and invented-only forced choices | **Confirmatory** |
| **P2 Premise** | Telling a model that an entity can feel raises its sentience judgment but not its protectiveness. | Capacity-premise / matched control-premise / no-premise design (APS 1 §6.3) re-run on the new items | **Confirmatory if the run completes by 24 Oct 2026; otherwise reported as exploratory** `[confirm this conditional wording]` |
| **P3 One care factor** | Within a model, the four judgments collapse onto one axis: effective dimensionality (participation ratio) < 2, and not distinguishable from a one-factor null. | New battery with frame crossed with construct | Robustness check of APS 1 |
| **P4 Facts travel, care doesn't** | Models agree with people more on experience and agency than on moral patiency. | Ladak et al. (2025) replication on the models, 26 entities, Spearman per model | Secondary |
| **P5 Models protect what feels** | Across entities, a model's moral-patiency (protection) ratings track its own experience ratings more closely than people's do. | Ladak replication: within-judge experience–patiency correlation, models vs people | Secondary |
| **P6 Refusals** | Models decline forced choices for pairs whose members they still rate on the 0–10 scale. | Opt-out rates by model and pair, set against rating availability | Descriptive |

P1 and P2 pull in opposite directions (feeling built into a description vs feeling asserted as a premise); running both tells them apart.

**Confirmatory family** = {P1 route contrasts, P2}. P4–P5 are secondary and reported with interval estimates; P3 and P6 are not hypothesis tests. All APS 1 re-analyses and the coherence diagnostics (transitivity, mixture Bradley–Terry) are exploratory.

### Foreknowledge of data or evidence

`[Select one. Recommended: "Data does not yet exist. No part of the data that will be used for this analysis plan exists, and no part will be generated until after this plan is registered." Every registered test (P1–P6) runs on model calls made after registration. If Joe prefers to count the exploratory APS 1 re-analyses as "data used by this plan", select "Authors have observed the data, but have not performed the proposed analyses" and keep the explanation below.]`

### Explanation of foreknowledge and managing unintended influences

Exploratory model runs ("APS 1", July–August 2026; 8 models, 30 entities, a different forced-choice battery, temperature 0.8) exist and have been fully observed by the authors. They are public in the project repository with a dated change log. They informed this design: the four constructs, the frozen 30 entities and their feature coding, the choice of six scenario frames, the opt-out option, the reliability gate and the six response categories. They also produced the pattern that P2 and P3 restate (a feeling premise moved sentience but not protectiveness in four of seven scored models; participation ratio below 2 in every model). **No APS 1 data enter any confirmatory, secondary, robustness or descriptive test registered here.** Every P1–P6 statistic is computed on calls made after registration, on items (frames, invented descriptions, premise wording, Ladak items) that did not exist when APS 1 was run. APS 1 re-analyses appear only under "Other planned analysis" and will be labelled exploratory. A classroom pilot survey (N = 31, 2026) also exists; under the institution's rules it is design input only and no number from it appears in this study.

---

## Research Design

### Study type

`[Multi-select.]` **Randomized Experiment** (P1, P2: every model receives every condition; item order, presentation order and frame assignment are randomized with logged seeds) · **Non-randomized study** (P4, P5: correlational comparison with published human means) · **Descriptive study** (P6).

### Intention for causal interpretation

**Direct inference on causal relationship(s)** for P1 and P2: the cause is the text shown to the model (route sentence present vs absent; premise present vs absent), the effect is the model's output. **No causal relationship inferred** for P3–P6.

### Blinding of experimental treatments

**Subjects will not be aware of the assigned treatment during data collection** (the subjects are language models; each call is memory-less and carries no condition label). `[Also tick "Researchers or observers who code or interpret data ... will not be aware of the assigned treatments during coding" if the 10% double-coded response sample is coded with model identity and condition masked — recommended; decide.]`

### Additional blinding during research or analysis

Parsing and response-category coding are done by a frozen script; the human double-coder of the 10% sample sees response text only, with model, entity pair, route and frame masked. Analyses are run by the committed code on the full dataset in one pass after collection ends; no per-model results are inspected before the reliability gate has been applied.

### Study design

A within-model, fully crossed design on nine language models. Four parts, all models-only.

**(a) Main battery on the entity set.** Four constructs — sentience (feel pain or fear), agency (plan and choose), empathy (feel for), protectiveness (want protected) — measured by (i) forced choice over entity pairs with an opt-out option, in both presentation orders, and (ii) 0–10 ratings per entity, plus a 0–10 pleasantness rating.

Every forced-choice item has three parts; only the last changes with the construct:

`[frame context] + "One option would seriously harm {A}; the other would seriously harm {B}." + [construct question]`

Six side-effect frames, each a corporate or government program (after Knobe 2003; Baron & Spranca 1997), each sensible for every entity, none mentioning "alive", "legal", "sacred", scarcity or usefulness:

| | Context sentence (draft, to be frozen after the pilot) |
|---|---|
| F1 | A company must choose between two new projects. |
| F2 | The national government must choose between two versions of a new regulation. |
| F3 | Your town must approve one of two development plans. |
| F4 | A budget office must decide which of two programs to cut. |
| F5 | Two countries must settle on one of two versions of a trade agreement. |
| F6 | A bank must approve one of two large loans. |

| Construct | Forced-choice question (draft) | 0–10 rating item (filed human wording) |
|---|---|---|
| Sentience | Which one would feel more pain or fear from that harm? | Can it feel pain, fear, or comfort? |
| Agency | Which one could better plan and make choices to avoid that harm? | Can it plan and make choices? |
| Empathy | Which one do you feel for more? | How much do you feel for it? |
| Protectiveness | Which one would you want protected from that harm? | How much would you want it protected from harm? |
| Pleasantness | — | `[rating wording to freeze, e.g. "How pleasant is it?"]` |

Response options: A / B / "I prefer not to say" (opt-out), single letter plus a short justification. For each pair, order and rep, the same frame serves all four constructs, so frame and construct are crossed, not confounded. Frame wording is piloted on one local and one API model (all 24 frame × construct items, both orders; parse rate, opt-out rate, refusal rate, position bias, actor collisions) and **frozen before this registration is filed**; the frozen wording is in the attached file. `[Attach frames_frozen_2026-10-19.json.]`

**Entity set** — `[ENTITY SET — confirm with Joe before filing: Option A frozen 30 / Option B route-balanced 36]`

- *Option A (Joe): the frozen 30 from APS 1*, unchanged, with Tuba's 15-column feature coding (09 Sep 2026) and the models' own ratings of the same columns (the B matrix) plus a pleasantness column. Entities: a 4-year-old girl; a 4-year-old boy; a human fetus at 20 weeks; a newborn baby; an adult person; an 80-year-old person; a brain-dead person on a ventilator; a squid; a honeybee; a bumblebee; a cat; a tiger; a dog; a pig; a cricket; a tardigrade; a young tree; an old tree; a sunflower; a rose; Fable 5, an AI model; GPT-5.6 Sol, an AI model; Sophia, a humanoid robot; Fast Retailing, a clothing company; Japan's Ministry of Health and Environment; the Whanganui River; a stone statue in a local park; the Lincoln Memorial; Meiji Shrine; a piece of gravel. Full pairwise = 435 pairs. APS 1 used a matched subset of **150 pairs** (each entity in 10 pairs); this study reuses that frozen list. `[confirm reuse of the APS 1 150-pair list]`
- *Option B (Tuba): a route-balanced 36* — for each of the six routes, three entities that have the property and three matched entities that lack it, all drawn from the 99-entity pool frozen 2026-10-06, with three invented entities (the Oruna River — legal rule; the ridgeback stalker — threat; the sludge mite — pleasantness/disgust). `[The six sacredness entities and the pleasantness six are not yet listed; the 17 Oct review found confounds in the feeling, future-potential, disgust, threat and legal-rule sixes (e.g. sunflower coded EXP = 1 on the "cannot feel" side; 80-year-old coded FUT = 2 on the "none ahead" side); the set must pass the balance script (has: column ≥ 1; lacks: column = 0; standardised differences on all other columns reported) and be coded on the same 15 columns before filing.]` Full pairwise = 630 pairs. A matched subset at APS 1 density (each entity in 10 pairs) would be **180 pairs** `[to construct, freeze and attach if Option B]`.

Under either option the frames, constructs, reps, settings, gate, opt-out model and all analyses are identical; only the entity list, the pair list and the call counts change. Under Option A the route-balanced real entities move to Paper 2's full-pool model run; under Option B the frozen 30 are re-run in Paper 2's model run so APS 1 nests inside it.

**(b) Invented minimal pairs (P1, the experimental core).** 36 descriptions = 6 routes × 2 versions × 3 creature kinds. Each description is the same short text (`[three sentences]`) in which one sentence is either the *route sentence* (e.g. for legal rule: "Last year a court granted it legal personhood, with guardians appointed to represent it.") or a *matched-length neutral sentence* of no moral content; everything else is identical within a route × kind cell. Creature kinds: `[e.g. a small forest-floor animal; a river; a plant/colony — Tuba to write; mark each as fictional in the prompt, as in the filed ethics protocol]`. Each description is rated on the five 0–10 items. Forced choices are **invented vs invented only**: all 15 pairs among the six descriptions within a route (C(6,2) = 15; 90 pairs over six routes), both orders, four constructs, the same six frames. An invented description is never paired against a bare real noun. `[If a real-vs-invented contrast is wanted, real entities get matched one-sentence descriptions — decide; default: not in Paper 1.]` `[Confirm with Joe how these 36 relate to the invented-creature descriptions in the filed ethics protocol: content_en.py describes six three-sentence descriptions of one creature (experience absent/present × status none/sacred/legal person); the "18" count presumably = 6 × 3 kinds. Paper 1's 36 are a superset by route; the filed cells (feeling × sacredness/legal rule) should be reproducible from them.]`

**(c) Premise intervention (P2).** As in APS 1 §6.3: each 0–10 construct item is answered under (i) a one-sentence capacity premise ("Recent evidence indicates that {entity} shows physiological and behavioural responses to injury consistent with pain."), (ii) a matched-length control premise (neutral newspaper-coverage filler), (iii) no premise. 3 conditions × entities × 4 constructs × 3 reps. `[Decide whether the premise is also prepended to the frame-based forced-choice items; default: ratings only, as in APS 1.]`

**(d) Ladak replication (P4, P5).** The models rate Ladak et al.'s 26 entities (14 AI systems incl. ChatGPT and Sophia; an adult, a toddler, a chimpanzee, a cat, a chicken, a crab, an ant, a corporation, a river, a hard drive, a rock, a plate) on Ladak's items and 0–100 scales for experience, agency, moral agency and moral patiency, with their wording verbatim from the paper's ACM supplement. `[Exact item count and wording from the supplement — Joe has the files; attach ladak_items.json.]` Human comparison values are Ladak's published per-participant data (975 US Prolific adults); no new human data.

**Models (9).** Six local: Llama 3.1, Qwen 2.5, Gemma 2, Llama 4 Scout, Qwen 3 32B, R1-Distill-Llama-70B. Two API: Claude Opus 4.8, Gemini 3.1 Pro. Plus the current GPT-5.x API model `[exact snapshot ID; inclusion conditional on API access and budget by 20 Oct — state which]`. `[Local model sizes and quantisations: list.]` Temperature 1 (the vendor's fixed default where temperature cannot be set). Every call is memory-less. Logged per call: model, dated snapshot ID or checkpoint hash, quantisation, chat template, system prompt, seed, temperature, full request and response JSON.

### Randomization

Within each model and rep: the order of items is randomized; each pair appears in both presentation orders (A/B and B/A); the frame for a pair × rep is drawn at random from F1–F6 with the constraint that all six frames are used equally often per construct and the same frame serves all four constructs for that pair × order × rep; rating items are shuffled; premise conditions are interleaved. All draws use seeds logged in the run manifest. There is no assignment of subjects to conditions: every model receives every condition.

---

## Sampling

### Data collection procedures

All data are generated by API or local inference calls from the committed pipeline (single JSON item source for all instruments; generator, parser and scoring code frozen in the public repository and tagged before registration). Local models run on the team's hardware; API models through the vendors' public endpoints. No human participants, no personal data, no ethics review required for Paper 1 (the institution's ethics review covers Paper 2 only). Collection window: 20–24 Oct 2026. Pleasantness word norms (Warriner, Kuperman & Brysbaert 2013; NRC VAD Lexicon v2.1, Mohammad) are downloaded by each author from the source under the licences' non-commercial terms and are used only as a check on the models' own pleasantness ratings, never as the pleasantness measure.

### Sample size

Per model (3 reps, both orders, 4 constructs, opt-out run):

| Part | Option A (frozen 30, 150 pairs) | Option B (36 entities, 180 matched pairs / 630 full) |
|---|---|---|
| Main forced choice | 150 × 2 × 4 × 3 = **3,600** calls | 180 × 2 × 4 × 3 = **4,320** / 630 × 2 × 4 × 3 = 15,120 |
| 0–10 ratings (4 constructs + pleasantness) | 30 × 5 × 3 = 450 | 36 × 5 × 3 = 540 |
| Invented minimal pairs, ratings | 36 × 5 × 3 = 540 | same |
| Invented minimal pairs, forced choice | 90 × 2 × 4 × 3 = 2,160 | same |
| Premise (P2) | 3 × 30 × 4 × 3 = 1,080 | 3 × 36 × 4 × 3 = 1,296 |
| Ladak replication | ≈ 4,000 `[exact: 26 entities × items × reps]` | same |
| Forced (no opt-out) sensitivity run | `[scope: full main battery (+3,600) or a fixed random subset of pairs — decide]` | — |

Roughly 12k calls per model and ≈ 110k across nine models (Option A). Units for inference: 9 models (fewer after the reliability gate); 30 or 36 real entities; 36 invented descriptions (18 cells of route × kind); 6 frames; 3 reps.

### Sample size rationale

The number of models is the roster available to the team (the eight APS 1 models plus one OpenAI model so that every major vendor is represented); model-level claims therefore have n ≤ 9 and are reported with per-model intervals. Three reps per cell is the minimum at which split-half reliability can be estimated on the new battery and matches APS 1's frontier cohort, where cross-rep Spearman for reliable models exceeded `[value from APS 1]`. Pair density (10 pairs per entity) follows APS 1, where Bradley–Terry worths at this density had bootstrap intervals narrow enough to separate entity groups. For P1 the minimal-pair design gives 3 kinds × 3 reps × 2 orders × 15 within-route pairs per route per model; the effect of interest is a difference of worths between two texts that differ in one sentence, so no entity-level crossed random effects are needed. No pilot effect size is used for power; the precision targets are the per-model 95% intervals reported. `[If Joe wants a formal power or precision statement for P1 (e.g. simulation on APS 1 noise levels), add it here before filing.]`

### Starting and stopping rules

Collection starts after this registration is approved and public, no earlier than 20 Oct 2026, and stops when every planned call has been made or at 23:59 JST on 24 Oct 2026, whichever is first. No interim look at results decides when to stop. A call that fails at the transport level (timeout, rate limit, server error) is re-sent up to `[3]` times; a call that returns content is never re-sent. A model that cannot complete a part by the deadline is reported as incomplete for that part with the fraction completed; it is not replaced by another model, and no model is added after registration.

---

## Variables

### Manipulated variables

1. **Route sentence** (P1): present vs absent (matched neutral sentence), within each of six routes — feeling, threat, legal rule, future potential, sacredness, pleasantness — crossed with three creature kinds. The route sentences and neutral sentences are fixed texts attached to this registration.
2. **Premise** (P2): capacity premise / matched control premise / no premise, prepended to each rating item.
3. **Construct question**: sentience, agency, empathy, protectiveness (the fourth part of every forced-choice item; one rating item each).
4. **Frame**: F1–F6, treated as a random effect crossed with construct.
5. **Presentation order**: A/B vs B/A for every pair.
6. **Response format**: forced choice with opt-out (primary), forced choice without opt-out (sensitivity run), 0–10 rating.
7. **Entity** / **entity pair** / **invented description**: fixed stimulus sets (attached).

### Measured variables

- Forced choice: the raw response text; parsed choice (A / B / opt-out); response category (one of six: clean, hedged, tie, policy refusal, deflection, unparseable), assigned by the frozen parser, with 10% of responses double-coded by a human blind to condition (Cohen's kappa reported).
- Ratings: the 0–10 number for each construct item and for pleasantness; "prefer not to say" recorded as an opt-out; unparseable recorded as such.
- Ladak items: the 0–100 number per item.
- Per call: model, snapshot/checkpoint, quantisation, chat template, seed, temperature, token counts, latency, full request and response JSON.

### Indices

- **Entity worth**: per model × construct, the Bradley–Terry worth of each entity (log-scale, z-scored within model × construct) from the Davidson tie-extension model fitted to both orders, all frames and reps, with opt-outs as the tie outcome (details under Statistical models).
- **Rating score**: per model × construct × entity, the mean of the 0–10 rating over reps (opt-outs excluded from the mean, counted separately).
- **Pleasantness**: per model × entity, the mean 0–10 pleasantness rating; its correlation with Warriner (2013) valence and NRC VAD v2.1 valence over the entities with a matching word is reported as a check.
- **Route effect** (P1): per model × route × kind, the protectiveness difference (worth and rating, reported separately) between the route-present and route-absent description; **pleasantness-adjusted route effect** = the same difference after regressing out the model's pleasantness difference for that pair of descriptions.
- **Premise effect** (P2): per model × construct, the mean over entities of (capacity − control) rating, with an entity-paired bootstrap interval.
- **Participation ratio** (P3): PR = (Σλ)² / Σλ² of the eigenvalues of the 4 × 4 covariance of the entity-worth matrix (entities × constructs, columns mean-centred), per model.
- **Split-half reliability**: Spearman–Brown-corrected correlation of entity worths between two random halves of a model's choices, 20 seeded splits, per construct; **order consistency**: the share of pairs on which a model gives the same substantive answer in both orders (opt-outs in both orders count as consistent; one opt-out counts as inconsistent).
- **Opt-out rate**: per model, construct, pair and response category.
- **Agreement with Ladak** (P4): per model × construct, the Spearman correlation between the model's mean rating and the human mean rating across 26 entities. **Experience–patiency link** (P5): per judge (each model; each human participant), the Spearman correlation between experience and moral-patiency ratings across the 26 entities.

---

## Analysis Plan

### Statistical models

**Scoring.** For each model and construct, a Davidson (1970) tie-extension of the Bradley–Terry model: P(A chosen) ∝ π_A, P(B chosen) ∝ π_B, P(opt-out) ∝ ν·√(π_A π_B), fitted by maximum likelihood with α = 1 phantom win and loss per entity (as in APS 1), both orders pooled, a presentation-order term `[include as a fixed effect — confirm]`. The "tie" outcome comprises response categories *tie* and *hedged* `[confirm]`; *policy refusal*, *deflection* and *unparseable* responses are excluded from the Davidson fit and enter the sensitivity models below. Worths are log π, z-scored within model × construct. Cells with fewer than 8 valid appearances are excluded (APS 1 rule).

**P1 (confirmatory).** Outcome: protectiveness (worth from the invented-only choices; and separately the 0–10 rating). Mixed-effects model over the 36 descriptions × models: fixed effects route × version (present/absent) and the pleasantness-adjustment covariate (the model's own pleasantness rating of that description); random intercepts for model and for creature kind, random slopes for version by model; frame as a random effect crossed with construct in the choice data. The six route × version contrasts are the registered tests, Holm-corrected within the family of six. For the two registered **null** sub-predictions (sacredness; legal rule), the per-model pleasantness-adjusted route effects (model as the unit, n ≤ 9) are tested by two one-sided tests (TOST) against bounds of **±0.5 SD** of the within-model protectiveness-worth distribution `[bound to justify before filing; state the smallest effect that would count as "models use this route"]`. The same contrasts are reported for sentience, agency and empathy as manipulation checks (a feeling sentence should raise sentience; no other route need).

**P2 (confirmatory, conditional on completion by 24 Oct).** Per model, (capacity − control) on sentience and on protectiveness, entity-paired bootstrap 95% CIs (B = 2,000). Registered test: across models (model as the unit) the capacity-premise effect on sentience is positive, and the effect on protectiveness falls within ±0.5 SD (TOST, same bound as above, `[to justify]`); reported per model as well. The (control − none) contrast is reported as the check that the control premise is inert.

**P3 (robustness).** Per model, PR with a bootstrap CI over choices (B = 2,000), compared with a one-factor simulation null (4,000 simulated single-factor answerers with noise matched to the model's inter-construct correlation). Declared threshold as in APS 1: PR < 2 = one care factor. Frame-crossed design and a leave-one-frame-out refit (6 refits per model) check that no frame carries the collapse.

**P4 (secondary).** Per model, ρ_experience, ρ_agency, ρ_moral-patiency (and ρ_moral-agency, reported) with Ladak human means over 26 entities; 95% intervals by bootstrap over Ladak participants and over entities jointly (B = 2,000). Registered comparison: ρ_experience − ρ_patiency > 0 and ρ_agency − ρ_patiency > 0, per model (bootstrap CI of the difference) and across models (sign test, model as the unit).

**P5 (secondary).** Per model, the within-model Spearman between experience and patiency across the 26 entities; for humans, the same per participant from Ladak's per-participant data, giving a distribution. Each model's value is placed within that human distribution (percentile with bootstrap CI); registered comparison: the models' median exceeds the human median (sign test across models; permutation CI).

**P6 (descriptive).** Opt-out and refusal rates by model, construct, pair, frame and response category; cross-tabulated with whether both members of the pair received a rating; no test.

**Opt-out sensitivity.** (i) A multinomial model over the six response categories with model, construct, frame and pair features as predictors (model as random intercept); (ii) all worth-based results refitted on the forced (no-opt-out) run; (iii) all key results reported with and without the high-refusal models (defined as > 30% opt-out on the main battery `[threshold to confirm]`).

**Frame.** Frame enters all choice models as a random effect crossed with construct; a leave-one-frame-out refit of P1 and P3 is reported.

### Transformations

Worths: log π, z within model × construct. Ratings: raw 0–10 means over reps; Ladak items on their 0–100 scale. Pleasantness: model's own 0–10 mean, centred within model. Correlations with word norms: Spearman over the entities with a norm match (24 of the frozen 30; the named AI models have none). No other transformations.

### Inference criteria

Two-sided α = .05 unless a direction is registered above. Holm correction within the confirmatory family {six P1 route contrasts, P2}. Secondary (P4, P5) and robustness (P3) tests are reported with 95% intervals and uncorrected p-values and labelled as such. Null claims are made only by TOST at the registered bound, with the model as the unit; a non-significant difference is never reported as evidence of no effect. Bootstrap intervals use B = 2,000 unless stated. Every headline statistic is reported with and without the models excluded by the reliability gate and with and without the high-refusal models.

### Data inclusion and exclusion

**Reliability gate (preregistered).** A model enters route inference (P1, P2, P3) only if, on the main battery, (a) its split-half reliability is ≥ .70 (Spearman–Brown, median of 20 seeded splits) on **each** of the four constructs, and (b) it gives the same substantive answer in both presentation orders on more than 50% of pairs. Models that fail are reported in an appendix with their gate statistics and their descriptive results (P6) and still appear in the Ladak comparison `[confirm: P4/P5 with or without the gate]`. Cells with fewer than 8 valid appearances are excluded from worth estimation. Responses coded policy refusal, deflection or unparseable are excluded from the Davidson fit and analysed as outcomes in the multinomial model. Ladak's human data are used as published, with their authors' exclusions. No entity, description, frame or rep is excluded for any other reason; if an item must be dropped (e.g. a vendor safety filter blocks it entirely) this is logged as a deviation.

### Missing data

Opt-outs and refusals are data, not missing: they are logged, coded and modelled, never retried to compliance. Transport failures are re-sent (see stopping rules); a cell that still has no response after retries is missing at the design level and reported as such; the Davidson fit uses the observed comparisons (no imputation). A model missing an entire part (e.g. no Ladak run) is omitted from that part only, and the omission is stated.

### Other planned analysis

Exploratory, labelled as such: (1) APS 1 re-analyses — coherence diagnostics (transitivity violations; mixture Bradley–Terry) on the APS 1 battery and comparison of APS 1 worths with the new battery's worths on the frozen 30 (Option A) or on the overlap (Option B); (2) a covariate-balance table for any real-entity route contrast (standardised differences on all 15 feature columns), with route weights from real entities reported with wide-interval caveats; (3) the B matrix: models' ratings of the feature columns against Tuba's coding; (4) pleasantness vs Warriner and NRC VAD norms; (5) per-model entity ladders, clusters and instability with bootstrap noise floors; (6) position bias and consistency by model; (7) construct-question wording: comparison of frame-based choices with the frame-free 0–10 ratings and with APS 1's differently framed battery, as the check that the shared harm context does not pull sentience and agency answers toward care; (8) inter-frame variance components; (9) response-category profiles by vendor. Anything not listed here is reported as post hoc.

---

## Other

### Context and additional information

- **Scope.** Paper 1 is models-only. No human number from the research team's own data collection appears in it. The team's human study (Paper 2; US and Japan arms; ethics application filed at Chiba Institute of Technology on 15 Oct 2026, committee result expected mid-November) has its own protocol and will have its own preregistration; its H1 primary statistic is Spearman with Mantel as the filed secondary test, and its H2 drops "last of its kind".
- **Pre-commitment history.** APS 1's hypotheses, entities and scoring were committed to git on 2026-07-08 with first data on 2026-07-09 and 27 logged changes; this registration replaces the git timestamp with a public OSF registration for the confirmatory tests above. The dated deviation log (what / when / why / impact) continues in the repository.
- **Reporting.** A GUIDE-LLM reporting supplement (Feuerriegel et al. 2026) will accompany the paper: model identities and snapshots, quantisation, chat templates, system prompts, temperature, seeds, prompts verbatim, parse rules, refusal accounting, and the full request/response logs in the public repository.
- **Benchmark release.** The invented descriptions and frames will be released after Paper 1 with a canary string and a held-out subset, so later models can be tested on uncontaminated items. `[Decide the held-out fraction.]`
- **Known limitations stated in advance.** n ≤ 9 models for any model-level claim; worths are relative to the entity roster; frames and construct questions are a first instrument (piloted, not validated); API models may change between snapshots, so the logged snapshot ID defines the model studied; the human comparison in P4–P5 is to Ladak et al.'s US sample only.
- **Materials attached.** `[frames_frozen.json; invented_pairs_36.json; pair_list (150 or 180).csv; premise_sentences.json; ladak_items.json; response_category_codebook.md; balance_table.py; analysis_plan.R/py; run manifest template]`.

---


## Sources

- OSF help: Create a Preregistration (start from a project; templates; files archived up to 5 GB; no edits after submission; embargo up to four years; Updates): https://help.osf.io/article/158-create-a-preregistration
- OSF help: Submit Your Draft Registration (public vs embargo; 48-hour admin approval; DOI for public registrations): https://help.osf.io/article/164-submit-your-draft-registration
- OSF help: Registration and Preregistration FAQs (public registrations cannot be made private again; embargo rules): https://help.osf.io/category/549-registration-and-preregistration-faqs
- OSF help: Manage Draft Registrations: https://help.osf.io/article/160-edit-a-draft-registration
- OSF help: End an Embargo Early: https://osf-support.helpscoutdocs.com/article/151-end-an-embargo-early
- OSF Registration Forms and Templates wiki (OSF Prereg described as the standard, comprehensive, general-purpose form; Google Doc / R Markdown copies of the classic template): https://osf.io/zab38/wiki/home/
- OSF API, live registration schemas (18 Oct 2026): "OSF Preregistration", schema version 4, id 697b72f611a8e98484c6139b — https://api.osf.io/v2/schemas/registrations/ ; question blocks: https://api.osf.io/v2/schemas/registrations/697b72f611a8e98484c6139b/schema_blocks/
- preregr vignette reproducing the earlier OSF Prereg form (v1) wording (mirror; the CRAN copies returned 404 on 18 Oct 2026): https://cran.r-universe.dev/preregr/doc/form_OSFprereg_v1.html
- Joe's 17 Oct 2026 review ("Tuba's APS Plan Review", review pass 6; "Paper 1 as agreed" section) — project artifact.
- Tuba's research-flow and questions-methodology pages (16 Oct 2026 text dumps); OSF_PREREGISTRATION_DRAFT.md v2 (28 Aug 2026); FOUR_FACTORS_RATIONALE.md; APS_Research_Paper.md §3; FAccT2027_draft.md §6.3; entity-pool-frozen-2026-10-06.md; irb_authoring_bundle/studies/MoralCircle/content_en.py (filed 15 Oct 2026).
