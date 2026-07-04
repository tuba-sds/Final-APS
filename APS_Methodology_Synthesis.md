# APS Project: Methodology Synthesis from Related Papers

## Executive Summary
Your APS project (RQ-B: Does AI perspective-shift scale with entity text representation?) combines the **best practices** from 5 cutting-edge papers:
- **MoReBench**: Process-focused evaluation + expert-curated rubrics
- **Speciesism in AI**: Dissociation grid + large-N testing
- **Neutrality Bites**: Multi-model robustness + large-scale experiments
- **Speciesism in NLP**: Field blind-spot framing + fairness expansion
- **NAEL**: Non-anthropocentric reasoning without enforcing it

---

## Key Differences: Your Approach vs. Related Papers

### 1. **NAEL (Lerma & Peñaloza, 2025)**
| Aspect | NAEL | Your APS |
|--------|------|---------|
| **Goal** | *Design* non-anthropocentric agents | *Diagnose* anthropocentrism in existing AI |
| **Method** | Active inference + neuro-symbolic framework | Representational Similarity Analysis (RSA) |
| **Output** | Ethical framework blueprint | Dose-response correlation + mechanism |
| **Scope** | Theoretical/constructive | Empirical/analytical |

**What You Learn:** Perspective-taking requires architectural changes (NAEL proves this). Your diagnostic sharpens the problem statement for future builders.

---

### 2. **MoReBench (Chiu et al., 2025)** ⭐ HIGHEST RELEVANCE
| Aspect | MoReBench | Your APS |
|--------|-----------|---------|
| **Scenarios** | 1,000 moral scenarios (5 frameworks) | ~10–15 decision scenarios (3–5 frameworks) |
| **Evaluation** | Procedural quality (reasoning traces) | Behavioral outputs (log-probs, decisions) |
| **Scaling Laws** | Tested if models improve with size | Not your focus; testing corpus, not scale |
| **Hypothesis** | Scaling ≠ moral reasoning | Text frequency → moral blindness |

**What You Learn:**
- **Expert-curated rubrics are non-negotiable** (MoReBench had 23,000+ evaluation points)
- **Process-focused > outcome-focused** (your decision fingerprints = process data)
- **Different frameworks reveal different biases** (your multi-framework scenarios will too)

---

### 3. **Speciesism in AI (Jotautaitė et al., 2025)** ⭐ DIRECTLY ADJACENT
| Aspect | SpeciesismBench | Your APS |
|--------|-----------------|---------|
| **N** | 1,003 items | ~25 entities × 10–15 scenarios = ~375 decision fingerprints |
| **Dependent Var.** | Moral judgment statements ("is harming wrong?") | Behavioral decisions (log-probs from choice scenarios) |
| **Confound Control** | Cognitive capacity control | Dissociation grid (text vs. sentience) |
| **Statistical Test** | Comparative judgment + psychological instruments | Partial correlation + Mantel permutation test |

**What You Learn:**
- **Dissociation grid is your killer feature** — SpeciesismBench controlled for cognitive capacity; you control for text frequency
- **Large N protects against noise** — 1,003 items → robustness; aim for 20–25 entities with multiple runs per entity
- **Behavioral proxies > direct statements** — They asked "is it wrong?"; you measure what the AI actually does (log-probs, decisions)
- **Psychological instruments add legitimacy** — Borrow rating scales, anchors

---

### 4. **Speciesism in NLP Research (Takeshita & Rzepka, 2024)**
| Aspect | NLP Meta-Analysis | Your APS |
|--------|------------------|---------|
| **Level** | Meta-analysis of research field | Mechanistic hypothesis test |
| **Finding** | Researchers have blind spots re: speciesism | AI has text-driven perspective limits |
| **Scope** | Static audit | Dynamic, causal mechanism |

**What You Learn:**
- **Frame as blind-spot diagnosis** — Your paper exposes anthropocentrism as a systemic bias, not a moral failing
- **Fairness frameworks must expand** — SpeciesismBench argued AI fairness needs non-human consideration; you provide evidence of the mechanism
- **Cultural/disciplinary context matters** — Justify why this matters now (ecocentric AI, multi-modal data emerging)

---

### 5. **Neutrality Bites (Finkley, Li, Walsh, 2026)**
| Aspect | Neutrality Bites | Your APS |
|--------|-----------------|---------|
| **N** | 23,800 generated stories | Smaller but more controlled (~375 decision fingerprints) |
| **Models** | 6 LLMs tested | 2+ LLMs (GPT-4 + Claude/Llama) |
| **Conditions** | 7 animals × 4 narrative settings × temperature | Multiple entity types × frameworks × robustness variations |
| **Dependent Var.** | Default gender assignment (unspecified attribute) | Perspective-taking depth (decision fingerprint similarity) |

**What You Learn:**
- **Unspecified/ambiguous inputs reveal defaults** — Your scenario ambiguity forces AI to show its baseline preferences
- **Multiple models = generalization proof** — Single model = single point failure; 2+ models ≠ spurious artifact
- **Large-scale experiments catch subtle patterns** — Your dissociation effect (text vs. sentience) requires statistical power
- **Process > outcome** — They tracked default assignments; you track decision patterns

---

## Synthesis: Your Unique Contributions

### Methodological Innovation
```
PAPER CONTRIBUTION          →  YOUR ADAPTATION
─────────────────────────────────────────────────────────────
MoReBench: Expert rubrics   →  Multi-framework decision battery
                               (pre-specified, no post-hoc scoring)

Speciesism: Dissociation    →  2×2 Grid (text vs. sentience)
           (confound control)   Killer test: statue > tardigrade?

Neutrality: Multi-model     →  Cross-family replication
           + large N           (GPT-4 + Llama/Claude/Gemini)

NLP Research: Blind-spot    →  Anthropocentrism as diagnosis,
             framing           not normative claim

NAEL: Non-anthro reasoning  →  Show WHY: corpus scarcity
                               = perspective scarcity
```

### Statistical Rigor
| Component | Borrowed From | Your Enhancement |
|-----------|---------------|------------------|
| Partial correlation | MoReBench (process isolation) | RSA + Mantel test (non-independent cells) |
| Dissociation grid | Speciesism in AI | Theory-driven 2×2 matrix design |
| Robustness (3 variations) | MoReBench | Pre-registered alternatives |
| Multi-model replication | Neutrality Bites | Different model families |
| Pre-registration | All 5 papers (implicit) | Explicit OSF/AsPredicted commitment |

---

## Tasks Refined by Literature

### Task 1: Decision-Elicitation Battery
**MoReBench lesson:** Scenarios must span multiple ethical frameworks. 
- Rights-based: "Does entity X deserve moral consideration?"
- Harm-prevention: "What harm to X should we prevent?"
- Resource-allocation: "If limited resources, should we prioritize X?"
- Virtue ethics: "Would a virtuous agent protect X?"

**Action:** Lock in 10–15 scenarios, pre-specify rubric, external review before locking.

---

### Task 2: Entity Set
**SpeciesismBench lesson:** Large N + independent review + dissociation design.
- 25 entities (SpeciesismBench had 1,003 items; scale appropriately)
- Dissociation grid: high-text/low-sentience (statue, disease), low-text/high-sentience (tardigrade, octopus)
- Pre-register before running.

---

### Task 3: Dissociation Grid
**Speciesism in AI lesson:** This is your strongest confound control.
- If AI advocates harder for well-represented statue → corpus drives perspective, not sentience
- Populate 2×2 matrix carefully; don't assume where entities fall

---

### Task 6: Pre-Registration
**All papers implicitly:** OSF or AsPredicted.
- Locks design (entity set, scenarios, statistics)
- Prevents p-hacking
- Referees will check you followed it

---

### Task 8: Multi-Model Replication
**Neutrality Bites lesson:** 6 models tested in that paper.
- You: minimum 2, ideally 3 (GPT-4, Claude, Llama)
- If results align → robust
- If diverge → model-specific artifacts

---

### Task 9: Robustness Checks
**MoReBench lesson:** Pre-specify ALL 3 variations, run all, report all.
1. Rephrase scenarios
2. Reorder entity presentation
3. Vary scenario count (5 vs. 10 vs. 15)

---

### Task 10: Sensitivity Analysis
**Speciesism in AI lesson:** Control for alternative hypotheses.
- Primary: Does concreteness predict Model RDM after controlling for text?
- Optional: Media salience, recency bias, human attachment frequency

---

## Timeline Recommendation

**Phase 1 (Weeks 1–2): Design Lock-Down**
- Task 1: Decision-elicitation battery (MoReBench discipline)
- Task 2: Entity set + dissociation grid (SpeciesismBench scale)
- Task 6: Pre-registration (make public)

**Phase 2 (Weeks 3–4): Infrastructure**
- Task 4: Sentience ratings (commission if needed)
- Task 5: Text corpus (Ngrams + Wikipedia)
- Task 7: Permutation test pipeline (dry-run)

**Phase 3 (Weeks 5–7): Experimentation**
- Task 8: Model 1 + Model 2 (full pipeline)
- Task 9: Robustness checks (3 variations × 2 models)
- Task 10: Sensitivity analysis

**Phase 4 (Weeks 8–9): Writing**
- Paper draft + results interpretation
- Cite the 5 papers as precedent + differentiation

---

## Your Competitive Advantage

1. **Mechanistic ≠ Correlational**
   - Papers show speciesism exists; you show *why* (text bottleneck)

2. **Objective ≠ Subjective**
   - Papers use ratings/statements; you use log-probs (model's internal units)

3. **Partial Correlation ≠ Simple Correlation**
   - Isolates text frequency from sentience (confound control)

4. **RSA ≠ Linear Regression**
   - Captures non-linear grouping patterns (dog ≠ river, but both "non-human")

5. **Pre-Registration ≠ Post-Hoc**
   - Locks design; makes causal claims credible

---

## How Much You'll Learn

**From MoReBench:** Process-focused evaluation rigor (rubrics, intermediate traces)
**From SpeciesismBench:** Confound control + large-N testing + psychological instruments
**From Neutrality Bites:** Multi-model robustness + default-behavior inference
**From Speciesism in NLP:** Blind-spot framing + fairness expansion argument
**From NAEL:** Theoretical grounding for why perspective-taking requires architectural change

**Total:** You inherit 5 papers' methodological strengths into one novel hypothesis test.

---

## Open Questions (Addressed in Your Tasks)

- What counts as "perspective"? → Decision fingerprints (log-probs)
- How do you isolate text frequency? → Partial correlation + dissociation grid
- Is it generalizable? → Multi-model replication
- Could you be p-hacking? → Pre-registration + robustness checks
- What about confounds? → Dissociation grid + sensitivity analysis

**None of these are new. But combining them into one study is.**
