# Final Presentation Tracker — APS Phase 3

**Talk:** July 14, 2026 (25-min slot: ~15 min present + ~10 min Q&A). **Today:** 2026-07-13 — **one day out.**
**Goal:** A+ = *working build + evidence that genuinely differentiates the hypotheses + metacognitive reflection on frame, process, and AI collaboration.*
**Weighting reminder:** Product ×5 (largest), Presentation ×1.5, Peer Review ×0.5. Spend ~2/3 of the talk on Sections 3–4 (build + findings).

This doc tracks the assignment's six sections + two rubrics against what actually exists on disk, and lists the gap-to-A+ work prioritized for the time left. Status legend: ✅ done · 🟡 partial · 🔴 not started · ⏳ decision needed.

---

## 0. One-paragraph status

The **build exists and runs** (Phase-3 pipeline, the deck, and the "You vs. the AI" dashboard on Render), and **H1 and H2 are both executed and committed** (`f2946bb`). H2 (dissociation) is a clean, reproducing *supported* result. H1 (AI-vs-human match) is the interesting one — the **preregistered instrument found no match for any open model, but the same-instrument robustness check found a partial match** (sentience + agency track humans; empathy + protectiveness don't). That split *is* a hypothesis-differentiating finding and a good honesty story. The project also has a genuine **"turn"** the rubric explicitly rewards: the original text-is-the-bottleneck thesis was demoted from core hypothesis to exploratory appendix. The three biggest A+ risks are all in **Evidence & Honesty**: (1) the internal audit found three serious rigor bugs (parser, Claude retries, stale bootstrap) that some appendix slides still rest on; (2) the human sample is N≈18 < the preregistered 30 minimum; (3) there is no consolidated deviations doc or AI-collaboration/takeaways narrative in the deck yet.

---

## 1. The competing hypotheses (ground truth, from `phase3/PREREGISTRATION.md`)

| ID | Statement | Test | Status of evidence |
|---|---|---|---|
| **H1** (primary) | AI's entity-similarity structure **matches humans'** per construct | Mantel(Model-RDM, Human-RDM), 5k perms, Bonferroni (`rsa.py`) | **Executed.** Preregistered path: 3 open models, **0/12 match** (all `matches_humans=False`). Robustness path (`rsa_comparison.py`): **partial match** — sentience & agency track humans across most models (Claude sentience r=.80 p=.0008), empathy & protectiveness do not. |
| **H2** (primary) | AI **collapses the 4 measures to ~1 axis** (participation ratio < 2) | `dimensionality.py` | **Supported & reproduces** (PR ≈ 1.59 / 1.84 / 1.86). |
| **H3** (exploratory) | AI judgment also tracks corpus text-representation | partial Mantel, `RUN_TEXT_TEST` OFF | Correctly off; appendix-only. **This is the demoted original thesis — see the turn below.** |

**The turn (Section 1 gold):** the June-23 framing was *"corpus representation drives perspective-taking — text is the bottleneck."* In Phase 3 that was **demoted to a secondary/exploratory appendix** (prereg §1: "This is no longer a core hypothesis"), and the question narrowed to (a) does AI match humans and (b) is the AI internally coherent. Explain *why you turned* — that's what the rubric rewards.

---

## 2. Section-by-section readiness (the six required sections)

| # | Section | What exists | Status | Gap to close |
|---|---|---|---|---|
| 1 | Issue, frame, question, **the turn** | Deck slide "Our Research Question — Then and Now"; prereg documents the demotion | 🟡 | Make the *turn* explicit and reasoned (what evidence/argument demoted the text hypothesis). |
| 2 | Methodology & **AI collaboration** | Method slides + flow chart exist; prereg is real | 🟡 | **No AI-collaboration slide.** The internal audit is perfect evidence of "AI as skeptic + verification." Add 1 slide: partner/builder/debugger/skeptic + how you verified (audit, re-parsing, adversarial checks). |
| 3 | **What you built** (demo) | Dashboard on Render ("You vs. the AI"); pipeline; deck | 🟡 | Pick the demo artifact (recommend the dashboard). Rehearse once; **capture screenshot fallback**. State real-vs-mocked clearly. |
| 4 | **What you found** (featured result) | H1 + H2 committed; radars; comparison layer | 🟡 | Choose ONE featured result (recommend: H2 "one care slider," or the H1 preregistered-vs-robustness split). Show which pattern points which way. Report the negative result (open models don't match humans) as a finding. |
| 5 | Limits & what's next | "Next Steps" / "Road Ahead" slides exist | 🟡 | Add the honest limits: N≈18<30, the three audit bugs, BT-relative-to-opponent-set. State the first thing you'd do with 6 more weeks. |
| 6 | Takeaways | — | 🔴 | **Missing.** Add: what the project taught you about the issue + antidisciplinary work; how AI collaboration evolved MP1→now; advice to next year's students. |

---

## 3. Product rubric (×5 — largest component)

| Criterion (20 pts) | Where we stand | Status |
|---|---|---|
| **The Build** | Pipeline runs; dashboard deployed; deck built. Artifact = the thing proposed (with a documented pivot). | ✅ strong |
| **Inquiry & Evidence** | Methods executed & committed; H1/H2 collected systematically; evidence *does* differentiate (H2 supported, H1 nuanced). **But** parser bug + stale bootstrap threaten some numbers. | 🟡 fix audit #1–2 |
| **Mechanism Understanding** | Can explain BT scoring, participation ratio, RDM/Mantel, why sentience tracks but protectiveness doesn't. | ✅ / 🟡 tighten the "why" for the empathy/protectiveness divergence |
| **AI Collaboration** | Session logs exist; hypotheses-before-prompts pattern; the audit shows verification. Not yet *narrated*. | 🟡 surface it (Section 2 slide) |
| **Synthesis & Documentation** | Deck + prereg. **No consolidated write-up** updating the proposal with findings/limits/real-world; no DEVIATIONS.md. | 🔴 write synthesis + DEVIATIONS.md |

## 4. Presentation rubric (×1.5)

| Criterion | Stand | Status |
|---|---|---|
| **Story Clarity** | Arc exists issue→question→evidence; the *turn* needs to be legible. | 🟡 |
| **Evidence & Honesty** | Biggest risk. Claims must match shown data; the stale-bootstrap slides + N=18 + audit bugs must be disclosed, not hidden. | 🔴 highest priority |
| **Demo & Visuals** | Deck is visually strong (radars); JA toggle dict not updated for new slides. | 🟡 |
| **Discussion** | Prepped answers exist in `APS_Conversation_Summary.md`. | ✅ rehearse Q&A |

---

## 5. Gap-to-A+ action list (prioritized for one day left)

**Tier 1 — do before the talk (protects Evidence & Honesty, the A+ differentiator):**
- [x] ✅ **Reconciled the appendix instability slides (2026-07-13).** Rewrote `phase3/bootstrap.py` to resample the A/B trials through the locked Bradley-Terry pipeline (point estimates match `score.py` to 4 dp); regenerated `results/bootstrap_ci.csv` and the three CI figures via new `phase3/plot_instability_ci.py`. Result overturned the old headline: **12 of 90** clear the noise floor (not 6) *(correction 2026-07-16: this entry originally said 13; the committed `bootstrap_ci.csv` contains exactly 12 rows with `clears_noise_floor=True` — gemma2 6, qwen2.5 4, llama3.1 2)*; the ordinary adult survives in **0/3** models; true all-model survivors are **gpt56sol + human_newborn**. Per user decision, **cut the "Most Incoherent Case" slide entirely**, updated "Instability — Now With Error Bars" with new figures, and trimmed the false "ordinary adult" clause from the main-deck story card. JA dictionary entries updated/removed to match. *Note: locked BT scoring still covers only the 3 confirmatory models; run-2/Claude/Gemini BT extension remains open (audit Table 5).*
- [ ] ⏳ **Decide the human-sample story (N≈18 < 30).** Either present H1 explicitly as *exploratory* given the under-min sample, or state the deviation plainly. Pick one and say it on the limits slide.
- [ ] 🔴 **Add the AI-collaboration slide (Section 2)** — the audit is your best evidence of "AI as skeptic + verification."
- [ ] 🔴 **Add the Takeaways slide (Section 6).**
- [ ] 🟡 **Make the "turn" explicit (Section 1)** — text hypothesis demoted, with the reason.
- [ ] 🟡 **Rehearse the demo + capture screenshot fallback** (dashboard on Render).

**Tier 2 — strengthens Product ×5 if time allows (or "what's next" if not):**
- [ ] 🔴 Re-parse run-1/2 with the strict frontier parser; regenerate `refusals.csv`; check if any headline shifts (audit fix #1). *(refusals.csv currently empty.)*
- [ ] 🔴 Rewrite `bootstrap.py` to resample BT strengths per §7 (audit fix #2).
- [ ] 🔴 Dedup `raw_results_claude.csv` + declare the retry episode (audit fix #3).
- [ ] 🔴 Add the <8-appearances exclusion to `score.py` (audit fix #4, currently a no-op).
- [ ] 🔴 Write `DEVIATIONS.md` (Willroth–Atherton format) + post prereg to OSF (audit fix #5). **Feeds Synthesis & Documentation.**
- [ ] 🟡 Update the JA toggle dictionary for the new slides.
- [ ] 🟡 Commit the uncommitted phase-3 working tree (`AUDIT_PREREG_ALIGNMENT.md` + scripts/results).

**Note:** if Tier 2 items don't get done, they are legitimate **Section 5 "what I'd do next"** content — but the audit bugs that touch *shown* slides (Tier 1, item 1) must be handled either way.

---

## 6. Where we are / how much is left — summary

- **Done:** the build; H1 + H2 executed and committed; deck with results, 8-model radar, run-2, Gemini; Q&A prep; the internal rigor audit.
- **Left (Tier 1, ~1 day):** reconcile stale-bootstrap slides, decide the N=18 framing, add AI-collaboration + takeaways slides, make the turn explicit, rehearse the demo.
- **Left (Tier 2, nice-to-have or "next"):** the six audit fixes, DEVIATIONS.md/OSF, JA toggle, commit working tree.
- **Single biggest lever for A+:** honesty about the evidence — present the H1 preregistered-vs-robustness split and the negative result as findings, disclose the limits, and don't show numbers that don't reproduce.
