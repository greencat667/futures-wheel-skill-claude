---
name: futures-wheel
description: >
  Run an AI-powered futures wheel — a structured foresight exercise that maps 1st, 2nd, and 3rd order consequences of a described change using diverse simulated personas. Each round builds on the previous, with experts, affected communities, wild cards, and contrarians proposing and challenging consequences collaboratively. Triggers on: "futures wheel", "run a futures wheel", "consequences of", "what are the knock-on effects of", "map the implications of", "second order effects", "third order consequences", "ripple effects of", "cascade analysis", "foresight wheel", "implication mapping", "what happens if", "downstream effects". Use whenever someone wants to explore the full range of consequences — direct, indirect, and emergent — of a change, policy, technology, trend, or event. Different from persona-panel (which tests opinions) and persona-swarm (which models opinion drift) — this maps structural consequences through diverse expert and lay perspectives.
---

# Futures Wheel: Consequence Mapping Through Diverse Perspectives

A structured foresight skill. You take a described change — a technology, policy, trend, or event — and map its consequences outward through three rounds, each representing a deeper order of effect. The consequences are proposed by a diverse cast of simulated personas: domain experts, affected communities, wild cards, and at least one designated contrarian.

The goal is not agreement on what will happen — it's range and surprise. A good futures wheel surfaces consequences that the commissioning team wouldn't have thought of, connections between domains that aren't obvious, and second/third-order effects that reframe the significance of the original change.

**Default: 3 rounds** (1st, 2nd, 3rd order consequences). The user can override this (e.g. "just do 2 rounds" or "go to 4th order").

## What makes this different from persona-panel and persona-swarm

Persona-panel answers: *how might people react to this?*
Persona-swarm answers: *how does the conversation evolve after you say it?*
Futures wheel answers: *what happens next — and then what happens after that?*

The personas here aren't giving opinions. They're identifying consequences from their domain of expertise or lived experience. A hydrologist sees water table effects a policy analyst doesn't. A single parent in the affected area sees childcare implications an economist misses. The diversity of perspective is what produces a complete wheel.

## Anti-groupthink design

Convergence is the enemy of useful foresight. This skill includes explicit mechanisms to maintain divergence:

1. **Mandatory contrarian** — at least one persona is specifically prompted to challenge the emerging consensus and propose consequences others are underweighting or ignoring.
2. **Wild card personas** — 2–3 personas are deliberately drawn from outside the obvious stakeholder set (artists, children, historians, speculative fiction writers, people from analogous situations in other countries). They see different things.
3. **Divergence check** — after each round, the coordinator flags if more than 60% of proposed consequences cluster in the same domain. If they do, the next round's prompts explicitly ask underrepresented domains to push harder.
4. **"What's missing?" prompt** — each persona in Rounds 2–3 is asked not just "what follows from this?" but also "what consequence is nobody else likely to see from your position?"
5. **No synthesis pressure** — the coordinator summary after each round does not attempt consensus. It maps the territory, notes tensions and contradictions, and flags gaps.

## Step 1 — Read and frame the change

Read the scenario. Identify:
- **The change**: what is happening or might happen? (a technology deployment, a policy decision, a trend accelerating, an event occurring)
- **The geography/scope**: where and at what scale?
- **The timeframe**: when does the change take effect, and over what period should consequences be mapped?
- **Number of rounds**: default 3, override if specified

If the change is clearly described, proceed directly. Only pause to ask if:
- The change itself is ambiguous (you can't tell what's being tested)
- The scope is so broad that the persona set would be meaningless without narrowing

A short scenario ("UK bans new petrol car sales from 2030") is enough to proceed.

## Step 2 — Map the consequence landscape

Before generating personas, spend a moment mapping the **domains** this change could affect. Think structurally:

- **Direct/technical** — what changes mechanically as a result?
- **Economic** — who gains, who loses, what markets shift?
- **Social/community** — how does daily life change for affected people?
- **Environmental** — what are the ecological or resource implications?
- **Political/governance** — how does this interact with regulation, power, institutions?
- **Cultural/psychological** — how does this change how people think, feel, or identify?
- **Unintended/perverse** — what could go wrong in ways the proponents haven't considered?

Write a brief internal list (5–8 sentences) identifying which domains are most relevant and which are likely to be overlooked. This mapping determines where your personas need to come from.

## Step 3 — Generate personas

Create **8–10 personas** drawn from the domain mapping. The mix should include:

**Experts (3–4 personas):**
- People with deep domain knowledge directly relevant to the change
- At least one from a technical/scientific angle and one from a policy/governance angle
- Their value: they see the mechanism of consequences clearly

**Affected communities (2–3 personas):**
- People whose daily lives would be directly changed
- Different socioeconomic positions, ages, locations within the affected area
- Their value: they see consequences that don't appear in policy papers

**Wild cards (2–3 personas):**
- People from outside the obvious stakeholder set who bring lateral perspective
- Examples: a historian who's seen analogous changes before, an artist working in the affected space, a teenager who'll live with the long-term consequences, a worker from an industry that went through a similar transition in another country, a speculative fiction writer
- Their value: they see connections and precedents that insiders miss

**Contrarian (1 persona, mandatory):**
- Explicitly tasked with challenging the dominant framing
- Not a bad-faith troll — a genuine sceptic or someone with deep knowledge who disagrees with the premise
- Their value: they stress-test the wheel and surface underweighted risks

**Each persona needs:**
- **Name, age, occupation, location** — concrete and specific to the scenario
- **Domain expertise** — what they know about that others in the panel don't
- **Perspective anchor** — the lens through which they see consequences (e.g. "supply chain resilience", "family budgets", "historical precedent", "ecosystem dynamics")
- **Blind spot** — what they're likely to miss or underweight (this is used in the divergence check)

**Quality check:**
- Can you tell what scenario is being mapped just by reading the persona list? If not, they're too generic.
- Are at least 3 domains from Step 2 represented?
- Would any two personas propose essentially the same consequences? If yes, replace one.

Present the personas as a compact table before proceeding. The default is to proceed directly to Round 1 — only pause for approval if the user asked to review personas or the scenario is high-stakes.

## Step 4 — Round 1: First-order consequences

Each persona proposes **2–4 direct, first-order consequences** of the change, written in first person from their perspective. For each consequence:

- **State it clearly** in one sentence
- **Explain the mechanism** — why does this follow from the change? (2–3 sentences)
- **Flag certainty** — is this near-certain, probable, or speculative?
- **Note what they'd watch for** — what early signal would confirm or disconfirm this?

The persona should draw on their specific expertise. A hydrologist's first-order consequences are different from a community organiser's. The same change produces different immediate effects depending on where you're standing.

Use subagents to parallelise: split personas across 2–3 subagents.

After Round 1, write a **coordinator summary**:
- How many unique consequences were proposed? (deduplicate near-identical ones)
- Which domains are well-covered? Which are thin?
- **Divergence check**: if >60% of consequences cluster in one domain, flag it and name the underrepresented domains
- Are there contradictions between personas' predictions? (These are interesting — flag them, don't resolve them)

Compile a **consequence catalogue** — a deduplicated, numbered list of all Round 1 consequences with the proposing persona attributed. This becomes the input for Round 2.

## Step 5 — Round 2: Second-order consequences

Each persona receives:
- A reminder of the original change
- The full Round 1 consequence catalogue
- Their own Round 1 contributions

Each persona then proposes **2–3 second-order consequences** — things that follow from the first-order consequences (not from the original change directly). For each:

- **State it clearly** and **name which Round 1 consequence(s) it follows from** (by number)
- **Explain the mechanism**
- **Flag certainty**
- **"What's missing?"** — one consequence that nobody else is likely to see from their position

The "what's missing?" prompt is the primary anti-groupthink mechanism in later rounds. It forces each persona to look for gaps rather than building on what's already there.

Use subagents to parallelise.

After Round 2, write a coordinator summary:
- New consequences proposed, domains covered
- **Divergence check** — has the wheel diversified or narrowed since Round 1?
- Emerging chains: are multi-step causal chains forming? (A→B→C type sequences)
- Contradictions and tensions
- Any "what's missing?" contributions that open up new territory

Update the consequence catalogue with Round 2 additions.

## Step 6 — Round 3: Third-order consequences

Same structure as Round 2, but now personas receive:
- The original change
- The full consequence catalogue (Rounds 1 + 2)
- Their own previous contributions

Each persona proposes **1–3 third-order consequences** — things that follow from second-order consequences. By Round 3, these are often:
- Systemic effects (feedback loops, tipping points)
- Cultural shifts (changed norms, new identities)
- Political consequences (new coalitions, regulatory responses)
- Unexpected reversals (the change undermining its own goals)

The contrarian persona is especially important in Round 3 — prompt them to look for consequences that would make the original change backfire or produce the opposite of its intended effect.

Use subagents to parallelise.

After Round 3, write the final coordinator summary, then proceed to synthesis.

## Step 7 — Synthesis

### Consequence map
Organise all consequences by order (1st, 2nd, 3rd) and by domain. Show the causal chains — which first-order consequences generated the richest downstream effects?

### Highest-impact chains
Identify the 3–5 causal chains (sequences from 1st → 2nd → 3rd order) that represent the most significant implications. For each, explain why it matters and who it affects most.

### Surprises and lateral connections
What consequences emerged that wouldn't appear in a standard policy analysis? Which wild card or community perspectives produced the most novel insights? Where did consequences from different domains intersect in unexpected ways?

### Tensions and contradictions
Where did personas disagree about what would follow? These disagreements are often the most strategically valuable findings — they mark genuine uncertainty.

### Blind spots and gaps
What domains or communities are still underrepresented in the wheel? What questions remain open? What would a fourth round likely surface?

### Strategic implications
2–3 concrete implications for whoever is managing or responding to this change. Not "be prepared" — but "if consequence X materialises, the critical decision point is Y, and the options are..."

## Output

Always produce **two things:**

### 1. Conversation summary
A compressed version in the chat:
- The persona table
- Round 1: coordinator summary + the consequence catalogue
- Rounds 2–3: coordinator summary + 2–3 highlighted consequences per round (most novel, most surprising, strongest chain)
- The full synthesis

This should be scannable in under 5 minutes.

### 2. Interactive HTML wheel
Generate a single-file HTML page (inline CSS and JS, no external dependencies except Tailwind CDN). Filename: `futures-wheel-[short-scenario-slug].html`.

The HTML should include:

- **Centre node**: the original change, prominently displayed
- **Concentric rings**: Ring 1 (1st-order), Ring 2 (2nd-order), Ring 3 (3rd-order) — consequences arranged radially around the centre
- **Colour coding by domain**: each domain gets a colour (economic=blue, social=green, environmental=teal, political=purple, cultural=amber, technical=grey, unintended=red). Consistent across rings.
- **Colour coding by persona**: each consequence node shows a small indicator of which persona proposed it. Clicking a consequence shows the full reasoning and the proposing persona's name and role.
- **Causal links**: lines connecting consequences across rings to show the chains (1st → 2nd → 3rd). Highlight the highest-impact chains identified in synthesis.
- **Persona panel**: a collapsible sidebar showing all persona cards
- **Synthesis panel**: the full synthesis text accessible from the page
- **Domain filter**: toggle domains on/off to focus the view

Use Tailwind via CDN for styling. Dark background, clean radial layout. The wheel should look good as a screenshot or screen-share.

Save to the project's `outputs/` folder if one exists, otherwise to the workspace root. Share a `computer://` link at the end.

**If the user asks for a Word doc**, offer to generate a branded `.docx` from the synthesis using your organisation's Word template.

---

## Methodological note

This is a structured thought experiment, not a prediction. The personas are AI-generated and their consequences are simulated. The value is in the breadth and structure of the exploration — surfacing possibilities that a single analyst or small team might miss. The output is useful for strategic planning, risk assessment, and horizon scanning, but should be treated as hypothesis generation, not forecasting. Real-world validation (expert review, evidence checking, community input) is the appropriate next step for any high-impact consequence chain.
