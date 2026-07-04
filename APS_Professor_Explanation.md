# APS Project: Simple Explanation for Your Professor

---

## THE PROBLEM (In 1 Minute)

**Imagine:** You teach a robot to understand the world by only showing it Wikipedia articles and books written by humans.

The robot learns about dogs (millions of articles), rivers (thousands of articles), and microbes (barely mentioned).

**Question:** When you ask the robot to make decisions "on behalf of" these things, will it care about them equally?

**Our guess:** No. The robot will care much more about dogs because dogs are everywhere in human writing. Rivers will get medium attention. Microbes? Forgotten.

**Why?** The robot can only know what humans wrote about. If humans didn't write much about microbes, the robot has nothing to learn.

**Our project:** We'll prove this is true. And show that you can't fix it just by prompting the robot differently—it's a data problem, not a prompt problem.

---

## THE SIMPLE HYPOTHESIS

### What We Think is Happening:

```
CORPUS REPRESENTATION  →  AI's PERSPECTIVE-TAKING ABILITY
(how much humans wrote  →  (how well AI can think from
 about entity X)           that entity's point of view)

DOG:      Lots of books   →  AI understands dogs well
RIVER:    Some books      →  AI understands rivers OK
MICROBE:  Almost nothing  →  AI has no clue about microbes
```

### The Test Case (Our "Killer Example"):

Imagine two things:
1. **A statue** (thousands of Wikipedia articles, photos, poems) → Non-living, can't feel anything
2. **A rare tardigrade** (barely mentioned in human writing) → Actually alive, can suffer

If AI cares more about protecting the statue than the tardigrade, that proves the AI is just copying what humans wrote—not actually thinking about what's real or important.

---

## HOW WE'LL TEST IT (The Experiment in 3 Steps)

### Step 1: Ask the AI to Decide Things

We'll give AI ~10 scenarios like:

- "A forest is being cut down. A mountain is in the way. What should we prioritize?"
- "We have medicine for one: a dog or a river. Who gets it?"
- "Who deserves protection from harm: a bee or a rock?"

We'll ask these about 20–25 different entities (dogs, rivers, mountains, statues, microbes, plants, etc.).

**Why?** The AI's choices reveal what it actually cares about.

---

### Step 2: Look at Patterns

The AI made thousands of choices. We'll organize them into a "decision fingerprint" for each entity:

- Dog's fingerprint: Always gets protection, always prioritized, high urgency
- River's fingerprint: Sometimes gets protection, medium urgency
- Microbe's fingerprint: Rarely protected, low urgency

**Then:** We compare these fingerprints. How similar is dog to river? How different is river from microbe?

---

### Step 3: Compare to Three Sources of Truth

We'll compare the AI's fingerprints to three things humans can measure:

**A) Text Frequency** (What did humans write about?)
- Google Books data: How many times is each entity mentioned?
- Wikipedia: How many articles about each?

**B) Actual Sentience** (What's actually alive and can feel?)
- We'll ask real scientists/philosophers: "On a scale 0–100, how sentient is this?"
- Dog = 95/100 (clearly alive, suffers)
- Statue = 0/100 (not alive, can't suffer)
- Microbe = 30/100 (alive but minimal consciousness)

**C) The AI's Actual Choices** (What did we measure?)
- Our experiment results

---

### Step 4: The Magic Question (Partial Correlation)

We ask: **"Does the AI's behavior match TEXT FREQUENCY, even after we account for actual SENTIENCE?"**

```
ANALOGY:
You notice tall people are faster runners.
But taller people also have longer legs.
Is it BEING TALL that makes them fast? Or LONG LEGS?

To find out: Compare tall people WITH LONG LEGS vs. tall people with SHORT LEGS.
If short-leg tall people are NOT fast, then legs matter more than height.

SAME FOR US:
If AI cares about STATUE (high-text, zero-sentience) more than TARDIGRADE (low-text, high-sentience),
then TEXT matters more than actual sentience.
```

**If YES** → Confirms our hypothesis: Text is the bottleneck
**If NO** → Our hypothesis is wrong; something else drives AI decisions

---

## WHAT MAKES THIS STUDY STRONG

### 1. **We Don't Just Measure Words; We Measure Behavior**
- Other studies ask: "Is this bias wrong?" (Yes/no answers)
- We measure: "What does AI actually choose?" (Log-probabilities, real decisions)
- Why better? Behavior doesn't lie the way words can

### 2. **The Dissociation Grid (Our Trick)**
We strategically pick entities where text frequency and sentience don't match:

| Entity | Text | Sentience | Prediction |
|--------|------|-----------|------------|
| Statue | HIGH | ZERO | If text drives, AI cares about statue |
| Tardigrade | LOW | HIGH | If text drives, AI ignores tardigrade |
| Dog | HIGH | HIGH | Both text and sentience say "care" |
| Microbe | LOW | LOW | Both text and sentience say "don't care" |

**If statue > tardigrade in AI's choices → TEXT is the bottleneck**

This is our smoking gun.

### 3. **We Test Multiple AI Models**
- AI Model 1: GPT-4
- AI Model 2: Claude or Llama

If both show the same pattern, it's real. If different, maybe it's just one model's quirk.

### 4. **We Lock Everything in Advance**
Before running the experiment, we write down:
- Exactly which entities we'll test
- Exactly which decisions we'll ask
- Exactly how we'll analyze the data

Why? So a critic can't say "You cherry-picked the results."

---

## WHAT WE EXPECT TO FIND

### Most Likely Result:
AI's choices match **Text Frequency**, not actual **Sentience**.

**Translation:**
- AI advocates harder for well-written-about entities (dog, mountain, city)
- AI ignores poorly-written-about entities (microbe, rare species, tree)
- This happens **even when** we control for actual sentience

### What This Means:
**The AI is anthropocentric by design.** Not because it's programmed to be mean to animals. But because it only learned from human data, which is human-centric.

**You can't fix this with better prompts.** You need better data—data from animals, plants, ecosystems.

---

## WHY THIS MATTERS (The "So What?")

### Today's Problem:
- Companies deploy AI to make environmental decisions
- AI reads Wikipedia (written by humans)
- AI decides which species to protect, which forests to cut
- **Result:** AI makes decisions like humans do—biased toward what humans care about

### Why That's Bad:
- A river can't write Wikipedia articles
- A forest can't lobby for its own interests
- So AI ignores them—not because they don't matter, but because they weren't written about

### Our Contribution:
We **measure and prove** this problem exists. Once it's measured, people can fix it:
- Collect data from animal communication
- Listen to bioacoustics (whale songs, bird calls)
- Train AI on diverse data sources, not just Wikipedia

---

## THE RESEARCH QUESTION (In Plain English)

**Simple version:**
"Do AI systems care about things just because humans wrote a lot about them?"

**Our version:**
"Does the depth of an LLM's non-human perspective-shift scale with how much that entity is represented in human text?"

**What we're testing:**
The hypothesis that **text frequency → perspective capacity**.

---

## OUR TIMELINE

| Phase | What | Duration |
|-------|------|----------|
| **Design** | Lock in decisions, entities, statistics | 2 weeks |
| **Setup** | Get sentience ratings, prepare data | 2 weeks |
| **Run** | Test on AI models, collect data | 3 weeks |
| **Analysis** | Correlate fingerprints, run statistics | 1 week |
| **Write** | Paper draft + results | 1 week |

---

## KEY INNOVATIONS (Why It's New)

### What Others Did:
- ✅ Showed AI is biased (Speciesism in AI paper)
- ✅ Showed AI can't reason well (MoReBench paper)
- ✅ Showed AI makes mistakes on unspecified inputs (Neutrality Bites paper)

### What We'll Do:
- ✅ **Measure** how much text frequency causes bias (not just that bias exists)
- ✅ **Isolate** text as the mechanism (not just correlation, but partial correlation)
- ✅ **Test across 2+ models** (prove it's not one model's quirk)
- ✅ **Use objective metrics** (log-probs, not subjective ratings)

---

## THE CLAIM (What We're Arguing)

### We're NOT claiming:
- ❌ "AI is immoral" (it's not trying to be)
- ❌ "We can fix this with better prompts" (you can't prompt around a data problem)
- ❌ "Ecocentric AI is easy to build" (it's not—we're just diagnosing the problem)

### We ARE claiming:
- ✅ "AI's moral circle is shaped by its training data"
- ✅ "Text frequency is a bottleneck for perspective-taking"
- ✅ "To get ecocentric AI, we need multi-species data, not just better prompting"
- ✅ "This is the first step toward fixing it"

---

## WHY YOUR PROFESSOR SHOULD CARE

1. **Novel:** No one has tested this exact hypothesis before
2. **Rigorous:** Multiple models, pre-registered, confound-controlled
3. **Practical:** Matters for AI deployment in real environmental decisions
4. **Publishable:** Clear methodology, falsifiable hypothesis, measurable outcome
5. **Timely:** Ecocentric AI is an emerging field; this paper could shape it

---

## ONE-SENTENCE SUMMARY

"We're measuring whether AI's ability to consider non-human perspectives is bottlenecked by how often humans wrote about them—and showing that's a data problem, not a prompt problem."

---

## QUESTIONS YOUR PROFESSOR MIGHT ASK

**Q: "Can you just prompt the AI to care more about microbes?"**
A: We think no—we predict prompting won't matter much because the AI has no internal representation of microbes. It's like trying to teach someone about a species they've never seen. Prompts shift language, not understanding.

**Q: "Why not just ask the AI 'Do you care about rivers?' directly?"**
A: Because the AI will say "Yes, I care" even if it doesn't really understand. Behavioral choices (what it actually decides in trade-offs) reveal understanding better than words.

**Q: "How is this different from Speciesism in AI?"**
A: They showed speciesism exists. We're showing WHY—the mechanism is text frequency. They measured judgments; we measure decisions. They didn't isolate text as the cause; we do (via partial correlation).

**Q: "What if you're wrong and AI does understand microbes?"**
A: Then our partial correlation will be weak, and Sentience RDM will predict AI behavior better than Text RDM. That would falsify our hypothesis—which is what we want. Either way, we learn something.

**Q: "How do you know your entities are representative?"**
A: We pre-register them publicly before running the experiment. We include dissociation cases (statue, tardigrade) to check our logic. We test 2+ models to ensure generalization.

---

## FINAL PITCH TO YOUR PROFESSOR

*"We're diagnosing a fundamental limit in how AI systems think about non-human perspectives. Not to blame AI, but to show that solving this requires multi-species data—not better prompts. If we're right, this paper defines the problem that future ecocentric AI systems will need to solve. If we're wrong, we'll learn something surprising about how LLMs actually form perspectives."*
