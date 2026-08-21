# OSF Preregistration (DRAFT) — The Descriptive–Evaluative Split in LLM Moral Judgment: A Powered, Intervention-Based Test

**Status: draft for the author to paste into OSF (osf.io → Registries → "Open-Ended Registration"
or the "OSF Preregistration" template). Contains NO human-subjects results — pilot data appear
only as design inputs, per the ethics guidance in the project record. Register public, no embargo.**

---

## Study title
Do large language models share humans' descriptive map of moral status but not the evaluative
one? A preregistered, format-diversified, intervention-based test.

## Authors
Tuba Ali (Chiba Institute of Technology); [faculty PI, TBD per ethics application].

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
- **H2 (link, causal — the primary test):** inserting a one-sentence *capacity premise*
  ("recent evidence indicates that {entity} shows physiological and behavioural responses to
  injury consistent with pain"), against a matched-length control premise and a no-premise
  baseline, raises sentience judgments in both humans and models; **in humans the evaluative
  judgments (protectiveness, empathy) rise with it; in models they do not** (interaction:
  premise × judge-type on the sentience→protectiveness transfer).
- **H3 (structure):** the four constructs, measured by a format-diversified instrument
  (≥4 answer formats per construct, crossed), are not distinguishable from a single care
  factor plus measurement noise in models (correlated-uniqueness MTMM; participation ratio
  vs a one-factor simulation null) — a claim about the measure and models jointly, evaluated
  identically for the human sample.

## Design

**Entities:** the 30-entity locked set (public in the project repository, frozen 2026-07-08).
**Constructs:** sentience, agency (descriptive); empathy, protectiveness (evaluative).
**Instrument:** every construct measured by ≥4 answer formats chosen for spectrum coverage
(absolute 0–10 rating; 0–100 likelihood/wrongness scale; limited-resource allocation between
paired entities; third-person advice choice), all formats meaningful for inanimate entities by
construction. Both presentation orders for all pairwise items.
**Premise manipulation (H2):** between-subjects (humans) / between-arms (models): capacity
premise vs matched-length control premise vs no premise.
**Models:** ≥8 LLMs spanning open-weight and frontier families; all model-side prompts, parsing
rules, and scoring code frozen in the public repository before human collection.
**Human sample:** online panel, target **n ≈ 300** adults (single arm; a two-arm US/Japan
extension of 2 × 250 is registered as a contingent extension, run only if funded), every rater
rating **all 30 entities** (~96–120 responses, 10–20 min), explicit "prefer not to say" on every
item, attention checks, no PII. Collection begins **only after ethics approval** (application in
progress at Chiba Institute of Technology; a determination request on prior coursework data is
filed separately — that pilot is used here solely as a design input).

## Analysis plan (locked)

- Scoring: pairwise formats via Bradley-Terry (regularized MM, α=1 phantom, <8-appearance
  exclusion); absolute formats via per-entity means; z within judge × format.
- H1: Mantel tests (5,000 permutations) per construct on the full 30-entity RDMs (435 distances),
  model vs pooled human map; pooled per-construct estimates via Fisher-z across models with
  bootstrap CIs; the descriptive-vs-evaluative contrast tested as the difference of pooled
  Fisher-z estimates (bootstrap over models and raters).
- H2: mixed-effects regression of each construct on premise condition × judge type with random
  intercepts for entity and (humans) rater; the registered test is the premise × judge-type
  interaction on protectiveness, with sentience as manipulation check.
- H3: correlated-uniqueness MTMM CFA over construct × format; participation ratio with
  bootstrap CI and a one-factor noise-calibrated simulation null, per judge.
- Power: precision-targeted, not pilot-effect-size-based — n ≈ 300 with ~96 within-rater
  observations gives the within-rater premise→protectiveness coefficient a target 95% CI
  half-width ≤ 0.15 SD (simulation code in the repository).
- Multiple comparisons: the confirmatory family is exactly {H1 contrast, H2 interaction,
  H3 model-side PR-vs-null}; Holm correction within the family; everything else labeled
  exploratory.
- Refusals/opt-outs are data: logged, reported, never retried to compliance.

## What already exists (transparency)

The model-side pipeline, the entity set, all instruments, and exploratory model-side results
are public at github.com/tuba-sds/APS-Runner (design-change log D1–D26). A coursework pilot
survey (N = 31, anonymous, adults) exists; pending an ethics determination it is not reported
here and enters this study only as a design input (item selection; the precision target above).

## Timeline
Model-side arms: complete or in progress at registration. Human collection: on ethics approval,
target 2026 Q4. Intended venues: CogSci 2027 / a Registered-Report-friendly journal.
