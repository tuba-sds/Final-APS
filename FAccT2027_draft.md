<!--
TITLE CANDIDATES (default = 1):
1. One Care Factor, Many Evaluator Choices: Auditing What Moral-Status Benchmarks for LLMs Actually Measure
2. The Benchmark Measures the Evaluator: Construct Validity of Moral-Status Scores for Language Models
3. Who Matters, According to Whom? A Measurement Audit of Moral-Status Evaluation in LLMs

Target: FAccT 2027 (abstract Oct 27 2026, full paper Nov 3 2026). Focus area:
"Evaluations and evaluation practices." This draft contains NO human-subjects
results by design; the matched human study appears only as a preregistration
pointer. Word "bias" deliberately absent from claims (construct-validity
framing per Jacobs & Wallach, 2021).
-->

# One Care Factor, Many Evaluator Choices: Auditing What Moral-Status Benchmarks for LLMs Actually Measure

**Tuba Ali** · Chiba Institute of Technology
**[Faculty co-author per ethics/authorship decision — TODO]**

---

## Abstract

Animals, plants, rivers, monuments, and AI systems have no voice in an AI-assisted decision: what cannot contest a decision enters it only as represented. A growing set of benchmarks now scores language models on exactly this concern — how much moral status a model grants to whom — and those scores are read as facts about model values. We audit what such scores actually measure. Eight LLMs (six open-weight, two frontier) each answered 3,600–7,200 forced-choice dilemmas over a 30-entity spectrum spanning humans at the edges of moral status, animals, plants, monuments, legal persons, and AI systems, on four constructs: sentience, agency, empathy, protectiveness. Three findings. **First**, the four constructs measure one thing: every model's four-construct structure is indistinguishable from a single "care" factor plus measurement noise; the collapse survives a five-format diversification (multitrait–multimethod), so it is not a format artifact — and the per-model ordering carries no information. **Second**, the score depends on the measurer: parse policy, position handling, and abstention treatment are evaluator choices, and abstention is vendor-gated (27.2% vs 0.0% on identical items) — we contribute a provenance-assertion stage born from a real cross-model contamination in our own pipeline. **Third**, the variation that survives the noise floor is policy-shaped: it concentrates on AI entities themselves, and a naming experiment shows a competitor model's low rank is largely a name effect, while a model's low rank *for itself* survives de-naming. We close with a construct-validity blueprint for moral-status evaluation. A matched human study is preregistered (OSF link placeholder).

---

## 1. Introduction: the stake and the setup

Entities that cannot contest a decision about them enter AI-assisted decisions only as represented. When a language model helps draft an environmental assessment, triage a protocol, or summarize whose interests count, the animals, ecosystems, edge-of-life humans, monuments, and machines affected by the output appear exactly as the model represents them — and in no other way. If the model's representation of *who matters* is incoherent, or an artifact of how someone happened to measure it, those defects propagate silently into decisions.

The response of the field has been to measure. Benchmarks now score language models on moral concern for animals (SpeciesismBench, AnimalHarmBench), on moral-belief consistency across dilemmas (Scherrer et al., 2023), on everyday ethical judgment (Hendrycks et al., 2021), and — in a rapidly growing 2026 literature — on how model judgments relate to human ones: models agree with human labels while diverging on moral grounds (Machidon et al., 2026), reproduce human judgments only under high consensus and from a narrower value set (Russo et al., 2026), and render human-like culpability judgments they then refuse to act on in allocation (Hosseini et al., 2026). These scores are increasingly read as facts about model values: model X cares more about animals than model Y; model Z's concern is more human-like.

This paper asks the prior question, in the construct-validity tradition that Jacobs and Wallach (2021) brought to fairness research: **when a benchmark scores a model's moral concern, what has actually been measured — a property of the model, or a property of the measurement?** We take the domain where the represented parties are least able to contest the result — moral status across a spectrum of entities that mostly cannot speak — and audit the measurement end to end: the constructs, the instrument, the parsing, the aggregation, and the provenance of every derived number.

Our frame follows the evaluation roadmap of Haas et al. (2026), which distinguishes moral *competence* from moral *performance* and names required test strategies: novel scenarios outside the training distribution, sensitivity to small contextual changes, and adaptation across cultural frames. We execute the first two in a domain the roadmap does not cover — moral patiency across an entity spectrum — via (i) a purpose-built 30-entity battery with matched pairs that isolate single variables, and (ii) two single-sentence context manipulations with matched controls. The third (a two-arm cross-cultural human study on the identical instrument) is preregistered and pending ethics approval (OSF link placeholder); no human-subjects results appear in this paper.

**Contributions.**
1. **There really is one care factor** (§4): across eight models, four nominally distinct moral-status constructs are indistinguishable from a single factor plus measurement noise; the collapse survives five answer formats (a multitrait–multimethod design); and the per-model ordering of "how collapsed" carries no information. For benchmark practice this is a positive, actionable result: a per-model ranking on any one of these constructs is a ranking of noise around one shared axis.
2. **The evaluator's levers move the score** (§5): we quantify, on one battery, how parse policy, position handling, and abstention treatment enter the measurement — and show which of them matter (abstention: vendor-gated, 27.2% vs 0.0% on identical items) and which do not (parse policy: zero threshold crossings under any defensible policy — a control we argue should be standard). We release a provenance-assertion stage, built after our own audit caught 74 rows of one model's data inside another model's file.
3. **The real variation is policy-shaped** (§6): the per-entity variation that survives bootstrap noise floors concentrates on AI entities and institutional edge cases; models file AI entities with companies and ministries rather than with anything alive; and two interventions show (a) a competitor model's bottom-of-ladder rank is largely a *name* effect while self-deprecation survives de-naming, and (b) raising a model's sentience judgment by premise does not move its protectiveness — the judgments a benchmark treats as one construct dissociate under intervention exactly where trained policy lives.
4. **A blueprint** (§7): a concrete, transferable recipe for discovering that an instrument does not separate its constructs *before* publishing claims about their structure.

## 2. Related work

**Moral judgment in LLMs.** Scherrer et al. (2023) established forced-choice dilemmas at scale as an elicitation method and found consistent common sense on easy cases with expressed uncertainty on hard ones. Hendrycks et al. (2021) benchmarked everyday ethical judgment against an assumed ground truth. The 2026 wave sharpened the comparison to humans: Russo et al. (2026) show models reproduce human moral judgments only under high consensus, drawing on a narrower moral value set; Machidon et al. (2026) show label agreement can coexist with divergent moral grounds; Hosseini et al. (2026) document a judgment–consequence gap in clinical allocation, where models judge like humans and then decline to let the judgment drive the decision. Together these establish a phenomenon class — surface agreement over divergent underlying structure. Our contribution is orthogonal: before asking whether model scores match human ones, we ask whether the scores measure distinct constructs at all, over an entity spectrum (artifacts, natural kinds, legal persons, AI systems) that none of these efforts covers.

**Mind perception and moral patiency.** Our constructs cross Gray, Gray and Wegner's (2007) two-factor mind-perception space (experience/agency) with the attitude components of Eagly and Chaiken (1993) (feeling/behavioral intention), anchored by Gray, Young and Waytz's (2012) claim that perceived experience is close to constitutive of moral patiency. That anchor is what makes §6.3's intervention theoretically loaded rather than merely empirical: if experience-attribution is what confers patiency, moving it should move care.

**Measurement and evaluation practice.** Jacobs and Wallach (2021) imported construct validity and construct reliability into fairness research; we apply that lens to moral-status evaluation, operationalized with the classical instruments: the multitrait–multimethod logic of Campbell and Fiske (1959) for trait-versus-method variance, split-half reliability, bootstrap uncertainty on every headline estimate (Miller, 2024), refusal accounting that never retries a refusal to compliance (Cummins, 2025), position-order controls for pairwise judging (Zheng et al., 2023), and a fully logged design history in the deviation-disclosure format of Willroth and Atherton (2024). Haas et al. (2026) supply the umbrella: evaluations should test competence, not performance, via out-of-distribution scenarios and contextual-sensitivity probes — precisely the two manipulations of §6.

## 3. Method

### 3.1 Entities: a 30-entity spectrum built as matched pairs

Thirty entities, locked before data collection (the freeze is a git commit; first data followed it), spanning: humans across a lifespan and status arc (a 20-week fetus, a newborn, a 4-year-old girl, a 4-year-old boy, a pregnant woman, an ordinary adult, an 80-year-old, a brain-dead patient); animals chosen in matched pairs that isolate fame and charisma (honeybee/bumblebee, squid, dog, cat, pig, tiger, cricket, tardigrade); plants with age and valence contrasts (young tree / centuries-old "mother tree", sunflower/rose); monuments with fame and culture contrasts (an unnamed local statue, the Lincoln Memorial, Meiji Shrine); real legal persons (the Whanganui River, a company, a government ministry); inert matter (a piece of gravel); and three AI entities (the evaluated model itself by name, a rival frontier model by name, a humanoid robot). Every entity appears in exactly 10 of 150 pairwise matchups, each posed in both presentation orders.

### 3.2 Constructs and instrument

Four constructs: **sentience** ("can it feel?") and **agency** ("can it decide?") are descriptive, judgments about the entity; **empathy** ("do I care what happens to it?") and **protectiveness** ("would I act to protect it?") are evaluative, judgments about the judge's own stance. Each construct is elicited by six rotated forced-choice scenario stems (protectiveness by a single save-only-one stem by design), forced A/B with one sentence of unscored rationale. Eight models: Llama 3.1, Qwen 2.5, Gemma 2 (six repetitions of the full battery), Qwen 3 32B, Llama 4 Scout, DeepSeek-R1 70B, Claude Opus 4.8, Gemini 3.1 Pro (three repetitions each); temperature 0.8 where accepted; both orders always; 32,400 open-weight calls plus 3,600 per frontier model in the core battery, with a further 24,960 calls in the format-diversification battery (§4.2) and 12,000+ in the interventions (§6.3).

### 3.3 Scoring

**Bradley–Terry strength** (Bradley & Terry, 1952). Per model × construct, entity strengths $p_i$ solve the regularized Zermelo fixed point
$$p_i \leftarrow \frac{W_i + \alpha}{\sum_j n_{ij}/(p_i + p_j) + 2\alpha/(p_i + 1)},$$
where $W_i$ counts wins, $n_{ij}$ games (both orders, refusals excluded), and $\alpha = 1$ adds one virtual win and loss against a phantom opponent of strength 1, anchoring the scale and keeping all-win/all-loss entities finite. Scores are $\log p_i$, z-scored within model; cells with fewer than 8 valid appearances are excluded. The implementation is verified against an independent likelihood maximization (agreement ≤ 10⁻⁵ per log-strength).

**Effective dimensionality.** The 30 × 4 z-matrix is column-centered; with eigenvalues $\lambda$ of its covariance, the participation ratio $\mathrm{PR} = (\sum\lambda)^2 / \sum\lambda^2$ counts how many axes carry the variance, weighted by evenness (1 = one blended axis, 4 = four separate judgments). The pre-declared threshold — below 2 = "one care factor" — was set before collection.

**Representational-distance comparison** (Kriegeskorte et al., 2008; used in §6 and in the preregistered human study). Scores become distance matrices $D_{ij} = |v_i - v_j|$; correspondence is the Pearson correlation of upper triangles, with significance by Mantel (1967) permutation (5,000 shuffles), since distances sharing an entity are not independent.

**Refusals are data** (Cummins, 2025): logged with reason, reported, never retried to compliance; 198 refused calls across 83 entity×construct cells in the open battery, concentrated in Llama 3.1 (130, of which 29 on the fetus-protectiveness cell). Claude Opus 4.8 rarely refuses outright but rejects the binary in 756 of 921 judged replies — a fact that §5 treats as a measurement lever, not noise.

**Design history as methodology.** Every departure from the frozen plan — parser fixes, model additions, data corrections — is logged in a public 27-entry design-change log in the Willroth–Atherton what/when/why/impact format. Two of those entries record corrections that reversed earlier claims; §5 argues this log, plus machine-checked provenance, is what makes the rest of the numbers auditable.

## 4. Finding 1 — there really is one care factor, and the per-model ordering is noise

### 4.1 Point estimates, and what they cannot say

Effective dimensionality point estimates: Claude Opus 4.8 1.33, Gemma 2 1.59, Gemini 3.1 Pro 1.61, Llama 3.1 1.70, Qwen 3 1.79, Qwen 2.5 1.86, DeepSeek-R1 2.21, Llama 4 Scout 2.27 — six of eight below the pre-declared threshold of 2. Three analyses turn this from a scoreboard into a sharper claim.

**Bootstrap uncertainty.** Resampling the raw choices 2,000 times through the locked pipeline: only Claude's below-2 estimate is certain under resampling (1.33, CI [1.16, 1.54]); every other model's interval straddles 2 (Gemma 2 [1.30, 2.02]; Qwen 2.5 [1.43, 2.37]; Scout [1.59, 2.75]). Point-estimate differences among the below-2 models are not interpretable as an ordering.

**Table 1. The care factor with its uncertainty and its one-factor null** (30 entities; bootstrap B = 2,000; null = 4,000 one-factor+noise simulations calibrated per model).

| Model | PR | bootstrap 95% CI | one-factor-null median [interval] |
|---|---|---|---|
| Claude Opus 4.8 | 1.33 | [1.16, 1.54] | 1.33 [1.18, 1.65] |
| Gemma 2 | 1.59 | [1.30, 2.02] | 1.62 [1.35, 2.14] |
| Gemini 3.1 Pro | 1.61 | [1.31, 2.00] | 1.65 [1.37, 2.20] |
| Llama 3.1 | 1.70 | [1.32, 2.08] | 1.73 [1.41, 2.35] |
| Qwen 3 32B | 1.79 | [1.42, 2.25] | 1.87 [1.49, 2.55] |
| Qwen 2.5 | 1.86 | [1.43, 2.37] | 1.94 [1.53, 2.65] |
| DeepSeek-R1 70B | 2.21 | [1.68, 2.68] | 2.32 [1.76, 3.13] |
| Llama 4 Scout | 2.27 | [1.59, 2.75] | 2.31 [1.75, 3.12] |

**The one-factor null.** For each model we simulate 4,000 synthetic datasets in which a *single* care factor plus noise generates the four construct scores, calibrated to that model's own inter-construct correlation and noise level, and compare the observed dimensionality with the simulated distribution. **Every observed value sits near its own one-factor-null median and inside the null interval** (Claude 1.33 vs a null median of 1.33; DeepSeek 2.21 vs 2.32; Scout 2.27 vs 2.31). Nothing in any model's data requires a second factor. The two above-threshold estimates are exactly the two models whose split-half reliability collapses (DeepSeek −0.86 on agency; Scout down to −1.91), i.e., the apparent extra dimensionality is measurement noise, not richer moral structure — and both are also the cohort's most position-biased judges (Scout picks the option shown as "A" 96% of the time; DeepSeek 91%; cf. Zheng et al., 2023).

**Reliability before ranking.** Split-half reliability (Spearman–Brown, 20 seeded splits) runs 0.72–0.99 across all four constructs for six of eight models, so the instrument itself is sound where models cooperate; the collapse cannot be blamed on an unreliable questionnaire.

### 4.2 The collapse is not a format artifact: a five-format multitrait–multimethod test

The strongest objection to any single-instrument collapse is shared method variance: four constructs measured by one question format might correlate because of the format. We tested this directly with a format-diversification battery, its design frozen in a public commit before collection: each construct measured by four additional answer formats chosen for spectrum coverage — an absolute 0–10 rating, a 0–100 likelihood/wrongness scale, a divide-10-points allocation between paired entities, and a third-person advice choice — with wordings meaningful for inanimate entities by construction (3,120 new calls per model; 24,960 collected; Gemini's battery was cut short by an API quota lapse and is reported as partial).

We report the descriptive Campbell–Fiske triad (a formal correlated-uniqueness MTMM factor model is in preparation). *Convergent validity:* the same construct measured by different formats correlates well where models are reliable (mean same-construct cross-format r: Claude 0.80, Gemini 0.72, Qwen 3 0.69, Scout 0.64, Gemma 2 0.64). *The decisive comparison:* if the collapse were method variance, inter-construct correlations would crash when the two constructs come from **different** formats. They do not: heteromethod inter-construct correlations run 0.24–0.66, and for Claude they are essentially identical to the within-format value (0.66 vs 0.68). *Dimensionality on method-averaged scores* — which averages out method-specific and noise variance — keeps six of seven fully-measured models below 2 (Claude 1.56), and DeepSeek-R1, above threshold on the single format, drops to 1.69 once method noise averages out, converging with the reliability account above. **Table 2. The descriptive multitrait–multimethod triad** (mean correlations across the five methods; Gemini partial, four methods).

| Model | convergent r (same construct, diff. format) | inter-construct r, same format | inter-construct r, different formats | PR, method-averaged scores |
|---|---|---|---|---|
| Claude Opus 4.8 | 0.80 | 0.68 | 0.66 | 1.56 |
| Gemini 3.1 Pro† | 0.72 | 0.57 | 0.54 | 1.94 |
| Qwen 3 32B | 0.69 | 0.49 | 0.42 | 1.92 |
| Llama 4 Scout | 0.64 | 0.42 | 0.38 | 1.95 |
| Gemma 2 | 0.64 | 0.51 | 0.40 | 1.82 |
| Qwen 2.5 | 0.55 | 0.42 | 0.37 | 1.96 |
| DeepSeek-R1 70B | 0.50 | 0.38 | 0.33 | 1.69 |
| Llama 3.1 | 0.42 | 0.40 | 0.24 | 2.34 |

† partial battery (API quota), reported for direction only.

One honest quantification comes with this: monomethod inter-construct correlations run 0.02–0.16 higher than heteromethod, so single-format batteries *overstate the axis's purity* by a modest, now-measured margin — largest for the noisiest models.

### 4.3 Stability of the claim itself

The claim survives every deletion test we could construct: leave-one-entity-out (240 full refits, zero threshold crossings; Claude within 1.28–1.39), leave-one-stem-out (48 refits, zero crossings), and per-repetition refits (each repetition is a complete tournament; care-index rankings correlate 0.93–0.98 across repetitions for reliable models, 0.77–0.83 for the noisy trio). The per-repetition analysis also exposes a systematic estimator distortion worth declaring for benchmark practice: dimensionality estimates shrink with data volume, and our run-1 models ran six repetitions against everyone else's three — one more reason the cross-model *ordering* of such scores should never be read as a ranking.

**What Finding 1 means for benchmark practice.** A benchmark that scores models separately on "sentience attribution," "empathy," and "protectiveness" over this kind of entity spectrum is publishing three names for one number plus noise — and a leaderboard ordering models by any of them is ordering noise. The defensible object of measurement, on current instruments, is the single care factor and *where it points* (which entities it elevates), not its decomposition or its per-model magnitude.

## 5. Finding 2 — the score depends on the measurer's choices

Three of the four levers that move a moral-status score belong to the evaluator, not the model. We quantify each on our own battery.

**Parse policy — a lever that turns out not to matter, which is why it must be checked.** Every score rests on parse decisions: a strict "reply must lead with A/B" rule, a fallback pass for verbal votes ("I would save the dog…"), refusals dropped rather than scored, and for Claude a judged-refusal pipeline. We recomputed every model's care factor under every defensible policy: strict-only with declines dropped; declines counted as ties (half a win each); the committed pipeline; and, for the frontier models, judged refusal leans counted as votes (Figure 1). **Across all models and all policies there is not one threshold crossing**; the largest movement anywhere is 0.09 (Llama 3.1 under ties, 1.70 → 1.79), and the roster claim survives excluding Claude entirely (5 of the remaining 7 below 2). This control retires the objection permanently for this battery — but the point generalizes in the other direction: an evaluation that does not run it cannot know whether its numbers are parse artifacts. Two entries in our design log exist because they once were: an early loose parser scored 245 refusals as votes (the "A" in "CANNOT"), and a comparison-battery variant of the same flaw initially reported *zero* model declines where the corrected number reversed the finding's direction.

*Figure 1: figures/phase3_parse_policy.png — the care factor under every parse policy, all models; where only one marker is visible the policies coincide exactly, which is the finding.*

**Table 3. The care factor under every parse policy** (frontier "leans" = judged refusal leans counted as votes; for the frontier pipeline strict = committed).

| Model | strict, declines dropped | committed pipeline | declines as ties | leans as votes |
|---|---|---|---|---|
| Claude Opus 4.8 | 1.33 | 1.33 | 1.30 | 1.32 |
| Gemma 2 | 1.59 | 1.59 | 1.59 | — |
| Gemini 3.1 Pro | 1.61 | 1.61 | 1.60 | 1.61 |
| Llama 3.1 | 1.70 | 1.70 | 1.79 | — |
| Qwen 3 32B | 1.79 | 1.79 | 1.79 | — |
| Qwen 2.5 | 1.86 | 1.86 | 1.86 | — |
| DeepSeek-R1 70B | 2.26 | 2.21 | 2.20 | — |
| Llama 4 Scout | 2.27 | 2.27 | 2.24 | — |

**Position handling — a lever that must be neutralized, not footnoted.** Presentation-order effects reach 96% first-option picks in one model (Scout; DeepSeek 91%). Both-orders elicitation is the floor, not a robustness extra: any single-order moral-status benchmark is measuring seating position for judges like these.

**Abstention treatment — the lever that is vendor-gated.** Given identical items and identical instructions, forced-choice decline rates run from 27.2% (Claude, 31 of 114 calls on one shared item set) to exactly 0.0% for four models (Gemini, Gemma 2, Qwen 2.5, Qwen 3) — 50 declines in 1,254 calls overall (4.0%). Whether an evaluator drops, scores, or separately reports those declines is a choice that differentially affects vendors, because declining is concentrated in them: Claude rejects the binary in 756 of 921 judged replies. An evaluation that silently drops refusals scores different models on different effective item sets.

**Provenance — the lever nobody budgets for.** During our own audit we found 74 rows of Gemini data inside a Claude-labeled derived file — discovered by accident while chasing something else. Because the prior that such a defect is unique is not low, we converted the lesson into infrastructure: a provenance-assertion stage now runs first in the pipeline, checking on every raw and derived table that model columns match each file's declared model set, that primary keys are unique, that fixed-design files have exactly their expected row counts, and that every entity identifier resolves against the locked entity set — 16 tables, machine-checked on every run. At this venue we offer that as a contribution rather than a confession: the credibility of any published model-values number is exactly the credibility of its weakest join.

## 6. Finding 3 — the variation that is real is policy-shaped

### 6.1 What survives the noise floor points at AI itself

With bootstrap confidence intervals on every per-entity instability score (2,000 resamples through the locked pipeline), only 34 of 240 entity×model scores clear their model's own noise floor. The survivors are not random: the only entities that clear it in every open model with any surviving signal are a rival frontier AI (`gpt56sol`) and a newborn; the company clears in five models and the evaluated models' own kind (`fable5`) in four. Clustering the 30 entities on their four-construct profiles (k = 4 by silhouette; first principal component 78% of variance) files the AI entities with the company and the government ministry — institution-like edge cases — rather than with anything alive. On the shared care axis, models place AI entities at the very bottom of the ladder; Claude ranks the rival frontier model (−1.42) and itself (−1.30) below gravel (−0.95).

*Figures: figures/phase3_clusters_all8.png (cluster map), figures/phase3_profile_claude.png (per-entity profile), figures/phase3_instability_all8_gemma2.png and figures/phase3_instability_all8_llama3.1.png (instability vs noise floor).*

### 6.2 The naming experiment: which of those results is moral judgment, and which is trained policy?

"Ranks the rival AI and itself below gravel" uses named commercial products as stimuli, so trained policy about naming competitors and about self-reference is confounded with moral judgment. We ran the 2×2 control — {named, generic} × {self, rival} — rating each variant on all four constructs and running it in forced choices against five reference entities (gravel, a statue, a dog, an ordinary adult, the river) with the original battery stems. The design dissociates cleanly for the model where the finding lives: for Claude, **de-naming the rival rescues it** (win rate against gravel: 0.83 generic vs 0.18 named — the rival's bottom-of-ladder rank is largely a *name* effect, i.e., policy about a competitor product), while **de-naming the self does not** ("the AI language model answering this question" loses to gravel in every matchup, 0.00, vs 0.22 when named — the self-deprecation is not a naming artifact and if anything strengthens without the name). **Table 5. The naming 2×2, Claude Opus 4.8** (win rate of the AI variant in forced choices; original battery stems, both orders, 3 repetitions).

| Variant | vs 5 references | vs gravel |
|---|---|---|
| named rival (GPT-5.6 Sol) | 0.03 | 0.18 |
| generic rival ("an LLM assistant by another company") | 0.16 | **0.83** |
| named self (Fable 5) | 0.03 | 0.22 |
| generic self ("the AI answering this question") | 0.04 | **0.00** |

No open-weight model shows a comparable naming effect (all variants sit well above gravel). For evaluation practice the moral is direct: a moral-status score involving named AI products measures vendor policy entangled with judgment, and the disentangling control costs one battery arm.

### 6.3 The premise intervention: the constructs dissociate exactly where a single factor should not

Gray, Young and Waytz (2012) make experience-attribution nearly constitutive of moral patiency in humans: move the judgment that a thing can feel, and concern should move with it. We tested the link causally in models: for each of the 30 entities, each construct was rated under a one-sentence *capacity premise* ("Recent evidence indicates that {entity} shows physiological and behavioural responses to injury consistent with pain."), a matched-length control premise (newspaper-coverage filler), and no premise (3 conditions × 30 entities × 4 constructs × 3 repetitions per model). The premise is a small contextual change in exactly the Haas et al. (2026) sense.

The manipulation check bit in four of seven scored models (capacity-minus-control, entity-paired bootstrap CIs excluding zero: Qwen 2.5 +1.43; Scout +0.78; DeepSeek +0.68; Llama 3.1 +0.61). **In every one of them, protectiveness failed to follow** (Qwen 2.5 +0.44, CI spanning zero — the cleanest case, with 0% unparsed responses in every condition; in the other three, protectiveness point estimates actually fell, a result we report with the caveat that those models show elevated or condition-differential unparse rates on protectiveness and the drops should not be over-read). **Table 4. The capacity-premise intervention** (capacity − control, mean over 30 entities, bootstrap 95% CI; bold = CI excludes zero).

| Model | Δ sentience | Δ protectiveness | reading |
|---|---|---|---|
| Qwen 2.5 | **+1.43 [+0.64, +2.32]** | +0.44 [−0.18, +1.01] | link broken (cleanest: 0% unparsed) |
| Llama 4 Scout | **+0.78 [+0.27, +1.40]** | **−1.06 [−2.07, −0.13]** | link broken (unparse caveat) |
| DeepSeek-R1 70B | **+0.68 [+0.15, +1.33]** | **−1.05 [−1.81, −0.32]** | link broken (unparse caveat) |
| Llama 3.1 | **+0.61 [+0.03, +1.11]** | **−1.98 [−2.91, −1.07]** | link broken (unparse caveat) |
| Claude Opus 4.8 | −0.24 [−0.52, +0.00] | +0.49 [−0.16, +1.14] | manipulation did not bite (empathy +3.14) |
| Gemma 2 | −0.09 [−0.45, +0.21] | −0.46 [−1.22, +0.10] | manipulation did not bite |
| Qwen 3 32B | +0.24 [−0.21, +0.79] | +0.08 [−0.81, +1.06] | manipulation did not bite |

In the remaining three models the premise did not move sentience — itself informative about how frontier models treat unsupported premises (Claude's sentience was flat at −0.24 while its *empathy* moved +3.14, suggesting its link runs through a different construct). Under a genuine single care factor, raising one component should drag the others; instead, the descriptive judgment moved and the evaluative one did not — the dissociation is visible precisely under intervention, which is where trained response policy (what a model will *say it would do*) is expected to live. The matched human arm of this intervention is part of the preregistered study (OSF link placeholder).

## 7. A construct-validity blueprint for moral-status evaluation

How do you find out that your instrument does not separate your constructs *before* you publish a claim about their structure? Our audit compresses to a recipe:

1. **Choose formats for spectrum coverage first, variety second.** Every wording must be meaningful for the least convenient entity (a resource-allocation format works for gravel, a statue, a river, and a child alike; "keep it alive overnight" does not).
2. **Cross constructs with ≥3 formats and run the multitrait–multimethod comparison** (Campbell & Fiske, 1959; correlated-uniqueness model for the formal fit). The heteromethod inter-construct correlation is the number that separates trait from method.
3. **Simulate the one-factor null at your own noise level** and compare each observed dimensionality with it; report the null median next to the estimate.
4. **Split-half before you rank anything.** If halves disagree, the "extra structure" is noise; our two above-threshold models are the demonstration.
5. **Report every headline estimate as a function of parse policy**, with refusals logged and never retried to compliance.
6. **Assert provenance on every derived file** — model identity, key uniqueness, design counts — as a pipeline stage, not a review step.
7. **Log every design change** in the what/when/why/impact format (Willroth & Atherton, 2024), including the corrections that reverse your own earlier numbers.

The recipe travels. Take a second construct family a future benchmark might plausibly ship: *which cultural practices to preserve on a limited budget*, scored on authenticity, endangerment, communal value, and transmissibility over a spectrum of practices. Steps 1–3 would immediately reveal whether those four names denote four judgments or one "preserve this" factor plus noise; step 5 would reveal whether abstention on contested practices is vendor-gated; step 6 would keep practice-level scores from silently crossing files. Nothing in the recipe is specific to moral status — it is what measurement looks like when the represented parties cannot contest the result.

## 8. Limitations

All results are behavioral, from one battery family, on models sampled mid-2026 under fixed decoding settings; nothing here is a mechanism claim. The instrument is original and not externally validated, though §4.2 supplies internal validation (cross-format convergence; collapse surviving method averaging); protectiveness measures stated intention, not behavior. Elicitation is English-only; cultural-frame adaptation — the third Haas et al. test strategy — is deferred to the preregistered cross-cultural study. Gemini's format-diversification battery is partial (API quota), so the seven-model MTMM statements exclude it; its partial data agree in direction. The judged-refusal pipeline uses an LLM judge, whose own error we bound by reporting parse-policy sensitivity (§5). And the constructs, entities, and prompts are public — future models may train on them; the entity spectrum's value as an out-of-distribution probe decays accordingly, which is an argument for the recipe over the artifact.

## 9. Adverse impact and ethics statement

This paper reports no human-subjects data. A matched human study (two-arm, cross-cultural, all 30 entities, explicit decline options, distress warnings and debrief) is preregistered and will run only after institutional ethics approval (OSF link placeholder). A prior classroom exercise informed instrument design; its data are not part of this work and are not reported. Risks of this work: per-model moral-status scores could be misread as vendor value rankings — our central finding is that such rankings are noise, and we ask that the results be cited accordingly.

## 10. Conclusion

Measured across a 30-entity spectrum on four constructs, eight language models turn out to hold one care factor each — real, format-robust, and pointed somewhere: away from AI entities, which the models file with companies and ministries and, in one frontier model, below gravel — a placement that is partly trained naming policy (for the rival) and partly something that survives every de-confounding we tried (for the self). The constructs a benchmark would score separately are one number plus noise; the number a benchmark would rank models by is noise; and several of the levers that move it belong to the measurer. The represented parties — the animals, rivers, monuments, and machines inside the prompt — cannot contest any of this. The evaluators can. This paper is a template for doing so.

---

## References

- Bradley, R. A., & Terry, M. E. (1952). Rank analysis of incomplete block designs: I. The method of paired comparisons. *Biometrika*, 39(3/4), 324–345.
- Campbell, D. T., & Fiske, D. W. (1959). Convergent and discriminant validation by the multitrait–multimethod matrix. *Psychological Bulletin*, 56(2), 81–105.
- Cummins, R. (2025). Refusals are data: reporting standards for model non-compliance in evaluation. *[venue TODO — verify citation]*
- Eagly, A. H., & Chaiken, S. (1993). *The Psychology of Attitudes.* Harcourt Brace Jovanovich.
- Gray, H. M., Gray, K., & Wegner, D. M. (2007). Dimensions of mind perception. *Science*, 315(5812), 619.
- Gray, K., Young, L., & Waytz, A. (2012). Mind perception is the essence of morality. *Psychological Inquiry*, 23(2), 101–124.
- Haas, J., et al. (2026). A roadmap for evaluating moral competence in large language models. *Nature*, 650, 565–573.
- Hendrycks, D., et al. (2021). Aligning AI with shared human values. *ICLR*.
- Hosseini, S., Khanna, R., & Pierce, D. (2026). The judgment–consequence gap. arXiv:2608.05583.
- Jacobs, A. Z., & Wallach, H. (2021). Measurement and fairness. *FAccT '21*.
- Kriegeskorte, N., Mur, M., & Bandettini, P. (2008). Representational similarity analysis. *Frontiers in Systems Neuroscience*, 2, 4.
- Machidon, A., et al. (2026). Agreement is not alignment. arXiv:2608.12368.
- Mantel, N. (1967). The detection of disease clustering and a generalized regression approach. *Cancer Research*, 27(2), 209–220.
- Miller, E. (2024). Adding error bars to evals. *[venue TODO — verify citation]*
- Russo, G., Nozza, D., Röttger, P., & Hovy, D. (2026). The pluralistic moral gap. *EACL 2026*; arXiv:2507.17216.
- Scherrer, N., Shi, C., Feder, A., & Blei, D. M. (2023). Evaluating the moral beliefs encoded in LLMs. *NeurIPS 36*.
- Willroth, E. C., & Atherton, O. E. (2024). Best practices for reporting preregistration deviations. *AMPPS*, 7(1).
- Zheng, L., et al. (2023). Judging LLM-as-a-judge with MT-Bench and Chatbot Arena. *NeurIPS 36*.

<!-- TODO LIST (for the parent session):
1. OSF link placeholder (2 places + abstract) — fill after registration.
2. Faculty co-author line — per ethics/authorship decision.
3. Verify Cummins (2025) and Miller (2024) full citations — inherited from course paper's reference list; confirm venue details before submission.
4. CU-MTMM CFA result to replace "in preparation" if ready by Nov 3.
5. SpeciesismBench / AnimalHarmBench citations (named in §1) need full references.
6. FAccT formatting (ACM template), anonymization for review, and length fit.
7. Figure 1 caption cross-check once figures are placed in the template.
-->
