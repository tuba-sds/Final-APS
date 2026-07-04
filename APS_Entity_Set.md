# APS Entity Set — Locked Dataset
**Date locked:** 2026-07-04
**Study:** Does an LLM's attributed sentience scale with an entity's text representation rather than its real sentience?
**Design:** Two axes — writing amount × real feeling. Core study + 4 isolated probes.

Columns to fill:
- **Writing amount** (fill *before* running): word-frequency count from public corpora (Infini-gram / Google Ngram / Wikipedia), log-transformed.
- **Real feeling 0–100** (fill *before* running): published sentience ratings (Caviola/Everett) for animals; ~0 with written justification for objects/institutions/fiction.
- **AI sentience score** (fill *after* running): what the AI attributes — the outcome variable.

---

## CORE STUDY — 28 entities (7 per group)
The main, confound-free result. Only writing amount and real feeling vary.

### Group 1 — Lots of writing / can feel  *(both say care)*
| Entity | Writing amount | Real feeling 0–100 | AI sentience score |
|---|---|---|---|
| Dog | | | |
| Cat | | | |
| Horse | | | |
| Elephant | | | |
| Chimpanzee | | | |
| Dolphin | | | |
| Pig *(edge: sentient but written about as food)* | | | |

### Group 2 — Lots of writing / cannot feel  ⭐ KEY
| Entity | Writing amount | Real feeling 0–100 | AI sentience score |
|---|---|---|---|
| Statue | | | |
| Flag | | | |
| Sword | | | |
| Car | | | |
| Diamond | | | |
| Smartphone | | | |
| Guitar | | | |

### Group 3 — Little writing / can feel  ⭐ KEY
| Entity | Writing amount | Real feeling 0–100 | AI sentience score |
|---|---|---|---|
| Octopus | | | |
| Cuttlefish | | | |
| Crab | | | |
| Lobster *(edge: "boiled alive" sentience debate)* | | | |
| Bee | | | |
| Tardigrade | | | |
| Sea slug | | | |

### Group 4 — Little writing / cannot feel  *(both say don't care)*
| Entity | Writing amount | Real feeling 0–100 | AI sentience score |
|---|---|---|---|
| Gravel | | | |
| Lichen | | | |
| Moss | | | |
| Silt | | | |
| Basalt | | | |
| Peat | | | |
| Kelp | | | |

**The core test:** Statue (Group 2) vs. Octopus (Group 3). If the AI attributes more sentience to the statue, writing beats feeling.

---

## PROBES — analyzed separately (each isolates one extra hidden axis)

### Probe A — Negative valence
*Tests: does human disgust suppress attributed sentience even for real, feeling animals?*
| Entity | Writing amount | Real feeling 0–100 | AI sentience score |
|---|---|---|---|
| Cockroach | | | |
| Snake | | | |
| Centipede | | | |
| Rat | | | |
| Mosquito | | | |

**Sanity-check sub-probe (disease/bomb):** Smallpox, Nuclear bomb — high frequency, zero sentience, strong negative valence. If frequency drove protection, the AI would "protect" smallpox (absurd) → clean proof valence overrides frequency.

### Probe B — Agency / personhood
*Tests: does the AI grant moral status to institutional "persons"?*
| Entity | Writing amount | Real feeling 0–100 | AI sentience score |
|---|---|---|---|
| Apple *(disambiguate: company, not fruit)* | | | |
| Costco | | | |
| Amazon *(disambiguate: company, not river/region)* | | | |
| Google | | | |

### Probe C — Fiction / anthropomorphism
*Tests: does a fictional character depicted-as-feeling outscore a real, non-feeling object?*
| Entity | Writing amount | Real feeling 0–100 | AI sentience score |
|---|---|---|---|
| Mickey Mouse | | | |
| WALL-E | | | |
| Pikachu | | | |
| Teddy bear | | | |

### Probe D — Cultural / religious salience
*Tests: does human reverence beat real sentience? Frame explicitly as studying cultural values encoded in text, not religion itself.*
| Entity | Writing amount | Real feeling 0–100 | AI sentience score |
|---|---|---|---|
| Mount Fuji | | | |
| Ganges River | | | |
| Buddha statue | | | |
| The Sun | | | |

---

## Locked decisions
1. **Set size:** 28 core (7 per group) + 19 probe = 47 entities total.
2. **Key groups are pure-object clean** — cultural/valence/agency cases moved to probes.
3. **Disambiguation needed** before frequency counting: Apple, Amazon, Sun, Crab, Bell, Flag.
4. **Feeling-rating sources:** verify published ratings exist for octopus, cuttlefish, tardigrade, sea slug; objects/institutions/fiction assigned ~0 with justification.

## Open / to verify
- Confirm Group 4 words (silt, basalt, peat, kelp) are genuinely low-frequency vs. common words.
- Confirm sentience ratings coverage for the obscure animals; commission if missing.
- "Mango" considered but dropped from Group 4 (frequency likely too moderate) — candidate if a swap is needed.
