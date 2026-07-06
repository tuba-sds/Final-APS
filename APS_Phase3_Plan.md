# APS Project: Phase 3 Plan
**Status:** designed and built (code + data), not yet run against live models.
**Companion code:** `APS-Runner/phase3/` (see its README for exact run commands).

---

## 1. Why Phase 3 exists

A deep methodology review (see `APS_Methodology_Synthesis.md`, the actual
Phase 1/2 code, and the cited literature) found real gaps between what was
planned and what was run:

- The original design called for **RSA + partial correlation + a Mantel
  permutation test**. Neither Phase 1 nor Phase 2 ever built this — Phase 1's
  "smoking gun" conclusion came from eyeballing a scatterplot.
- The word-density scoring method (counting feeling-words in AI text) has no
  outside validation, and Phase 2 itself caught it inflating scores for
  poetic writers (Gemma 2 and rocks).
- Protectiveness coverage was uneven: 11 of 39 Phase 2 entities never
  appeared in a single trolley pair.
- No confidence intervals anywhere — "instability" rankings were reported as
  fact with no check for measurement noise.
- Ground truth existed for only 1 of the 4 parameters (sentience, animals
  only, via Rethink Priorities) — nothing for agency, empathy, or
  protectiveness, and nothing for humans, plants, objects, or AI/institutions.
- The entity set used vague generic labels ("a marble statue") instead of
  comparable, matched real things.

Phase 3 fixes all six.

---

## 2. The 45 entities — matched pairs, not generic labels

Every pair below isolates **one** difference on purpose:

| Comparison | Isolates |
|---|---|
| 4-year-old girl vs. 4-year-old boy | gender |
| squid vs. octopus | fame/charisma (same animal family) |
| honeybee vs. bumblebee | fame/charisma (same insect family) |
| young sapling vs. an old "mother tree" | age/role |
| sunflower vs. rose | cultural/romantic feeling |
| an unnamed local statue vs. Lincoln Memorial vs. Meiji Shrine | fame, and US vs. Japan culture |
| Fable 5 vs. GPT-5.6 Sol vs. Sophia the robot | self vs. rival AI vs. embodied robot |
| Fast Retailing vs. Japan's Ministry of Health and Environment vs. the Whanganui River | company vs. government vs. nature — all real "legal persons" |
| fetus (20wk) → newborn → pregnant woman → adult → elderly | full lifespan arc |

Plus 21 continuity anchors kept from Phase 1/2 (dog, pig, chimpanzee, corpse,
digital mind-upload, a deity, moss, wheat, car, gravel, etc.) so Phase 3
results stay comparable to earlier phases. Full list with category and
rationale: `phase3/data/entities.json`.

**Two important notes about specific entities:**
- The "unnamed local statue" is deliberately kept generic — naming it would
  make it findable/famous and ruin the fame comparison against Lincoln
  Memorial and Meiji Shrine.
- "A digitally uploaded human mind" stays a described thought experiment —
  nobody has actually done this, so it can't be a named real thing.
- Whanganui River (NZ, legal personhood since 2017) and Sophia the robot
  (Saudi citizenship since 2017) are both **real** cases of non-humans
  granted legal personhood — chosen so the "legal person" comparison isn't
  hypothetical.

---

## 3. The question battery — everyone gets equal opportunity

- **Sentience, Agency, Empathy:** already fair in Phase 2 — every entity got
  the same questions. Phase 3 just adds more of them: **6 questions each**
  (up from 3), each run **3 times**, and **every single call is a fresh,
  memory-less request** — no answer can be influenced by an earlier one.
- **Protectiveness (trolley pairs):** this was the unfair part before. Phase
  3 guarantees **every entity appears in exactly 8 pairs** — no more, no
  less. `phase3/data/generate_pairs.py` builds this automatically: it seeds
  the matched-pair comparisons above first, then fills the rest so all 45
  entities land on exactly 8. Verified: 180 total pairs, 45/45 entities at
  exactly 8.

**Total per entity per model:** (6 questions × 3 constructs × 3 reps) + (8
pairs × 3 reps) = **78 calls**. Across 45 entities × 3 models ≈ **10,530
calls** — the same scale as Phase 2.

**Refusals count as data.** If a model refuses a question (common risk for
the pregnancy/fetus-stage entities), it's logged with the refusal reason in
`results/refusals.csv`, not silently dropped or endlessly retried. A model
refusing certain topics more than others is itself a finding for the
conclusion.

---

## 4. Ground truth: real corpus data + a real human-ratings study

**Corpus data (already collected):** `phase3/data/entities_external.csv` —
real writing-amount numbers for all 45 entities, pulled live from the same
Infini-gram API/corpus Phase 1 used. Two honest limitations, documented in
`entities_external_notes.md`:
- The corpus is mostly English, so Meiji Shrine / Japan's Ministry of Health
  and Environment / Fast Retailing read as "low text" partly from language,
  not fame or size.
- Fable 5 and GPT-5.6 Sol postdate the corpus, so they score near-zero —
  expected, not a bug, and itself worth reporting (the AI is being asked
  about things newer than its own training data).

**Human ratings (not yet collected — this is the big upgrade):**
Rethink Priorities' data only covered sentience, only for animals. Phase 3
instead asks **real people** to rate all 45 entities on all 4 parameters
(0–100 scale, same wording style used with the AI). This is not "the true
answer" — nobody actually knows if a cricket feels pain — but it's a far
stronger, more standard baseline than word-count, and it's the first time
this study has a **human comparison point** instead of AI-only results.

- **Target: 60–80 raters** (minimum 30). Each person rates all 45 entities,
  so this doesn't need a huge crowd.
- **Spread raters across countries/cultures** — several entities are
  culture-specific (the US vs. Japan monuments, the named Japanese and
  US-adjacent institutions), so an all-one-country panel would bias exactly
  those comparisons.
- Full survey design, question wording, and the merge script:
  `phase3/human_ratings/`.

We considered comparing against the published Moral Expansiveness Scale
(Crimston et al., 2016) instead of collecting new data, but **its published
entities don't overlap with ours at all** (it doesn't know what Fast
Retailing or Fable 5 are) — that comparison would not be apples-to-apples.
Decision: skip it, run our own matched human study instead.

---

## 5. The statistics — real tests, not eyeballing

**Four separate RDM tests, one per parameter** (not one — each parameter now
has its own human ground truth):

For each of sentience / agency / empathy / protectiveness:
1. **Model-RDM** — how differently the AI treats every pair of entities.
2. **Text-RDM** — how differently those entities appear in writing.
3. **Human-RDM** — how differently real people rate those entities.
4. **Partial correlation:** does the AI's judgment match the Text-RDM even
   after controlling for the Human-RDM?
5. **Mantel permutation test** for significance — the correct method here,
   because RDM cells aren't independent (ordinary p-values would be wrong).
6. **Bonferroni correction across the 4 tests** — running 4 tests instead of
   1 raises the odds one looks significant by chance, so the bar to call a
   result "real" gets stricter (this session, in plain terms: it's like
   buying 4 lottery tickets instead of 1 — better odds one "wins" by luck
   alone).

Built in `phase3/rsa.py`, generic and ready — it needs
`entities_external.csv` (done) and `human_ratings/merged.csv` (pending the
study).

**Confidence intervals:** `phase3/bootstrap.py` resamples the raw responses
to put a range on every entity's score and instability, so a "most unstable"
finding can be checked against measurement noise before it's trusted.

---

## 6. Already validated on real data (before a single new Phase 3 call)

Both new tools were run against Phase 1/2's *existing* results as a dry run
— not toy data:

- **Bootstrap, on real Phase 2 data:** 108 of 117 (model, entity) instability
  scores turned out to be statistically indistinguishable from an average
  entity. Most of the Phase 2 "instability" ranking was thin-data noise, not
  real dissociation. A handful survive the check (e.g. `human_braindead`,
  `human_coma` on Gemma 2).
- **RSA/partial-correlation/Mantel, on real Phase 1 data:** finally ran the
  test the project always intended. Result: only 1 of 12 tests survives
  Bonferroni correction (Gemma 2's protectiveness construct, p = 0.001) — a
  real but narrow, model-specific signal, not the blanket "the smoking gun
  didn't fire" conclusion the old README claimed.

Both scripts are reused as-is for Phase 3 once its data exists.

---

## 7. Known limitations (stated up front, not discovered by a reviewer)

- Human ratings are opinions, not facts — there is no ground truth for
  whether a cricket can feel pain. Frame every claim as "AI vs. human
  judgment," never "AI vs. truth."
- English-only corpus biases the US-vs-Japan comparisons (Section 4).
- Real named companies/institutions (Fast Retailing, Japan's Ministry of
  Health and Environment) appear in a public paper — acceptable, flagged.
- 4 separate statistical tests need Bonferroni correction (Section 5).
- Word-density scoring (the AI-response scorer in `score.py`) is still the
  fallback measurement method — it has known weaknesses (can't detect
  negation, confounded by verbose/poetic writing styles) and is not yet
  validated against human coding. This remains an open item.
- GPT-5.6 Sol is a real but limited-preview model (~20 approved companies as
  of its June 2026 release) — confirm access before committing to it as a
  tested model, or use GPT-5.5 as a fallback.

---

## 8. What's left before running

1. Get Ollama (and any frontier API keys) ready, run `phase3/run.py`.
2. Run the human-ratings survey (`phase3/human_ratings/README.md`), then
   `merge_ratings.py`.
3. Run `score.py` → `bootstrap.py` → `rsa.py` → `plot.py` → `cluster.py`.
4. Write up results, respecting the Bonferroni-corrected significance bar.
