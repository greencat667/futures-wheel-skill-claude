# Futures Wheel

A skill for [Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview) and [Cowork](https://claude.ai) that runs a structured foresight exercise — a futures wheel — mapping the 1st, 2nd, and 3rd-order consequences of a described change (a technology, policy, trend, or event) through a diverse cast of simulated personas.

## What it does

You describe a change. The skill maps it outward through three rounds, each a deeper order of effect:

- **Round 1 — direct consequences**, proposed by domain experts, affected communities, wild-card perspectives, and a mandatory contrarian
- **Round 2 — second-order consequences** that follow from Round 1, with each persona also asked "what's nobody else seeing from your position?"
- **Round 3 — third-order consequences**, often systemic effects, cultural shifts, or the change undermining its own goals

It's built with explicit anti-groupthink mechanisms: a divergence check that flags when consequences are clustering in one domain, wild-card personas drawn from outside the obvious stakeholder set, and no pressure toward synthesis or consensus during the rounds themselves.

Output is a conversation summary plus a self-contained interactive HTML wheel: a centre node (the change), concentric rings for each order of consequence, colour-coded by domain, with causal links tracing the highest-impact chains.

Different from a persona panel (which tests how people react to something) or a persona swarm (which models how opinions evolve over a conversation) — a futures wheel maps what happens next, structurally, regardless of anyone's opinion about it.

## Installation

**Ask Claude to set it up for you.** If you're using Claude Code or Claude Cowork, you can just say something like *"install the futures-wheel skill from github.com/greencat667/futures-wheel-skill-claude"* and Claude will clone the repo and put it in the right place — you don't need to do this by hand.

Or do it yourself: copy the `futures-wheel/` folder into your project's `.claude/skills/` directory:

```bash
git clone https://github.com/YOUR_USERNAME/futures-wheel-skill-claude.git
cp -r futures-wheel-skill-claude/futures-wheel/ your-project/.claude/skills/futures-wheel/
```

Claude will pick it up automatically from `available_skills` next time you start a session.

## Example prompt

Once installed, just ask Claude something like:

> "Run a futures wheel on a national ban on new petrol car sales from 2030 — what are the second and third-order consequences?"

## A note on what this is

The personas are AI-generated and their proposed consequences are simulated, not predicted. The value is breadth and structure — surfacing possibilities a single analyst or small team might miss — not forecasting accuracy. Treat the output as hypothesis generation for further investigation, not as a forecast to act on directly.

## Repository structure

```
futures-wheel-skill-claude/
├── futures-wheel/
│   └── SKILL.md    # Copy this folder to .claude/skills/
├── README.md
├── CONTRIBUTING.md
└── LICENSE
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) — note this repo isn't actively maintained, so response times on issues and PRs will be slow to nonexistent.

## License

MIT — see [LICENSE](LICENSE).
