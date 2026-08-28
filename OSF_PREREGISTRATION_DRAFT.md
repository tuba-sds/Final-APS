# OSF Preregistration (DRAFT v2, 2026-08-28) — The Descriptive–Evaluative Split in LLM Moral Judgment: A Powered, Intervention-Based Test

**Status: draft for Joe's review, then for the author to paste into OSF (osf.io → Registries →
"Open-Ended Registration" or the "OSF Preregistration" template). Contains NO human-subjects
results — pilot data appear only as design inputs, per the ethics guidance in the project record.
Register public, no embargo. v2 (2026-08-28) replaces the declarative capacity premise with the
novel-entity factorial per the PI's 2026-08-27 design decision (shared record M2–M6): the
manipulated construct is now DESCRIBED CAPACITY, not asserted evidence about real entities.**

---

## Study title
Do large language models share humans' descriptive map of moral status but not the evaluative
one? A preregistered, format-diversified, intervention-based test.

## Authors
Joe Austerweil (Chiba Institute of Technology; PI) [pending his review of this draft];
Tuba Ali (Chiba Institute of Technology).

## Background and prediction being registered

Mind-perception research holds that perceived experience is close to constitutive of moral
patiency in humans (Gray, Young & Waytz, 2012): judging that a thing can *feel* is tightly
linked to feeling concern and acting protectively toward it. Exploratory work by the authors
(course project, 2026; model-side results public in the project repository) suggests a
**descriptive–evaluative split** in LLMs: models appear to track human judgments of what an
entity *is* (sentience, agency) while diverging on what to *feel* or *do* about it (empathy,
protectiveness). That evidence is exploratory and under-powered on the human side; **this
registration states the split as the prediction to be tested**, together with a causal test of
the link it implies is broken.

## Hypotheses

- **H1 (split, correlational):** across a 30-entity spectrum (humans at the edges of moral
  status, animals, plants, monuments, rivers-as-legal-persons, institutions, AI systems),
  model–human map correspondence (Mantel r on representational distance matrices) is higher
  for the descriptive constructs (sentience, agency) than for the evaluative constructs
  (empathy, protectiveness).
- **H2 (link, causal — the primary test; novel-entity factorial):** for described entities the
  judge has no priors about, varying the entity's **described capacity** (capacity-present vs
  capacity-absent descriptions; ~6 novel entities spanning animal-like, plant-like,
  artifact-like, and computational classes; all four constructs measured) raises sentience
  judgments in both humans and models; **in humans the evaluative judgments (protectiveness,
  empathy) rise with it; in models they do not** (registered test: capacity × judge-type
  interaction on protectiveness, with sentience as the manipulation check). The manipulated
  construct is described capacity — nothing is asserted about any real entity, and every cell
  is equally credible by construction (no priors to contradict).
- **H2b (secondary causal test — true-framing contrast; conditional):** for ~8–10 real entities
  from the spectrum, two factually accurate descriptions each — one foregrounding functional
  properties, one experiential properties (e.g., a honeybee that navigates by polarized light
  vs one that avoids sources of injury) — shift sentience and, in humans but not models,
  protectiveness. Included only if the measured session budget holds it (decision rule: the
  block is dropped, before launch, if the measured end-to-end session exceeds ~32 minutes with
  it included); its inclusion status will be stated in a registration addendum before
  collection begins. If included it is analyzed as a secondary confirmatory test outside the
  Holm family; if dropped on the session-budget rule, the human-side causal claim rests on H2
  alone.
- **H3 (structure):** the four constructs, measured on the model side by a format-diversified
  instrument (≥4 answer formats per construct, crossed), are not distinguishable from a single
  care factor plus measurement noise in models (correlated-uniqueness MTMM; participation ratio
  vs a one-factor simulation null). The human sample's dimensionality is assessed on the rating
  format (a one-format estimate, reported as such).

- **Correlational anchor (not a hypothesis test):** the within-rater regression of
  protectiveness on sentience across the 30 real entities, humans vs models, is reported
  alongside H2/H2b as the correlational baseline; the three measures are reported together
  (convergence, not ranking).

## Design

**Entities:** the 30-entity locked set (public in the project repository, frozen 2026-07-08),
untouched by any manipulation — the 120 rating items stay character-identical to the prompts
answered by the models.
**Constructs:** sentience, agency (descriptive); empathy, protectiveness (evaluative).
**Novel-entity factorial (H2):** a separate block; ~6 described entities × capacity-present /
capacity-absent, between-subjects in humans, between-arms in models; descriptions frozen with
the instrument (target 2026-09-11) and included verbatim in the registration attachments.
**Framing contrast (H2b, conditional):** ~8–10 real entities × functional / experiential
framing, both factually accurate; inclusion decided by the measured-session rule above.
**Models-only cell:** the original declarative capacity premise is additionally run against
models only (no human sees it), as a converging measure of sensitivity to assertion strength.
**Model instrument:** every construct measured by ≥4 answer formats chosen for spectrum
coverage (absolute 0–10 rating; 0–100 likelihood/wrongness scale; limited-resource allocation
between paired entities; third-person advice choice), all formats meaningful for inanimate
entities by construction; both presentation orders for all pairwise items.
**Human instrument:** 0–10 ratings, 30 entities × 4 constructs (order randomized) + 19
forced-choice dilemmas, "prefer not to say" on every item; individual-difference scales —
speciesism (Caviola, Everett & Faber, 2019) and IDAQ-short (Waytz, Cacioppo & Epley, 2010) —
administered **after** all ratings and dilemmas, immediately before demographics, and analyzed
as moderators **with a preregistered randomization check** (if scale scores differ by
condition, they are treated as outcomes, not moderators). The Moral Expansiveness Scale is not
administered (criterion contamination with the protectiveness DV; Crimston et al., 2016 cited
as construct precedent only).
**Attention checks & exclusion rule (preregistered):** two checks (one instructed-response,
one mid-battery). Fail both → excluded; fail one → retained, with a sensitivity analysis
reported.
**Models:** ≥8 LLMs spanning open-weight and frontier families; all model-side prompts, parsing
rules, and scoring code frozen in the public repository before human collection.
**Human sample:** two-arm cross-cultural online panel — **250 analyzed per arm** (US via
Prolific, Japan via CrowdWorks; funded), recruiting ~275 US / ~300 JP against the exclusion
rule (asymmetric overage per the Japanese crowdsourcing literature, Majima 2017). Session
length ~25–32 minutes (measured end-to-end before launch and again in a soft launch of
n=20/arm; the measured range governs). Platform entered as covariate; measurement invariance
across arms is assessed before any pooled analysis. No PII. Collection begins **only after
ethics approval** (application in progress at Chiba Institute of Technology). A prior classroom
exercise informed the instrument design; its data are not part of this protocol and will not be
reported as findings.

## Analysis plan (locked)

- Scoring: pairwise formats via Bradley-Terry (regularized MM, α=1 phantom, <8-appearance
  exclusion); absolute formats via per-entity means; z within judge × format.
- H1: Mantel tests (5,000 permutations) per construct on the full 30-entity RDMs (435 distances),
  model vs pooled human map; pooled per-construct estimates via Fisher-z across models with
  bootstrap CIs; the descriptive-vs-evaluative contrast tested as the difference of pooled
  Fisher-z estimates (bootstrap over models and raters).
- H2: mixed-effects regression of each construct on described-capacity condition × judge type
  with random intercepts for novel entity and (humans) rater; the registered test is the
  capacity × judge-type interaction on protectiveness, with sentience as manipulation check.
- H2b (if included): the same model over framing condition × judge type on the framed real
  entities; secondary confirmatory, reported alongside H2 and the correlational anchor
  (convergence across the three measures is the argument; they are reported together, not
  ranked).
- H3: correlated-uniqueness MTMM CFA over construct × format (model side); participation ratio
  with bootstrap CI and a one-factor noise-calibrated simulation null, per judge; human-side
  dimensionality on the rating format reported as a one-format estimate.
- Moderators: speciesism and IDAQ-short as cross-level moderators of the H2 interaction and the
  within-rater sentience→protectiveness slope, conditional on the randomization check passing.
- Power: precision-targeted, not pilot-effect-size-based — 250 analyzed per arm with ~120
  within-rater observations gives the within-rater capacity→protectiveness coefficient a target
  95% CI half-width ≤ 0.15 SD (simulation code in the repository). The power analysis does not
  use pilot data.
- Multiple comparisons: the confirmatory family is exactly {H1 contrast, H2 interaction,
  H3 model-side PR-vs-null}; Holm correction within the family; H2b secondary; everything else
  labeled exploratory.
- Refusals/opt-outs are data: logged, reported, never retried to compliance.

## What already exists (transparency)

The model-side pipeline, the entity set, all instruments, and exploratory model-side results
are public at github.com/tuba-sds/APS-Runner (design-change log D1–D27). A coursework pilot
survey (N = 31, anonymous, adults) exists; under the institution's rules it is not reportable as
findings and enters this study only as a design input (item selection; the precision target above
is independent of it).

## Timeline
Model-side arms: complete or in progress at registration. Instrument freeze (English) target
2026-09-11; ethics application 2026-10-15 round (committee ~mid-November). Human collection: on
ethics approval, target 2026 Q4. Intended venues: CogSci 2027 / a Registered-Report-friendly
journal.
