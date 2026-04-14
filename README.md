# Scoring Rubrics

Centralized scoring criteria for Better Ventures deal flow. These YAML files are the single source of truth for company and founder evaluation across all BV pipelines.

## Overview

All deal flow bots (AcceleratorBot, DealBot, StealthBot) and BV Pipeline fetch their scoring criteria from this repo at runtime via GitHub raw URLs. Edit a YAML file here and commit — all tools pick up changes on their next run. No deployment needed.

## Files

| File | Purpose | Consumers |
|------|---------|-----------|
| `company-scoring.yaml` | Investment thesis, 3 themes, keywords, exclusions, scoring scale | AcceleratorBot, DealBot |
| `founder-scoring.yaml` | Holistic founder scoring prompt and scale (1-10) | DealBot, StealthBot |
| `investors.yaml` | Rick/Wes/Lyndsey routing: themes, keywords, Affinity person IDs | AcceleratorBot, DealBot |
| `prestigious-lists.yaml` | ~92 top VCs, 30 accelerators, 40 angels for signal boosting | AcceleratorBot, DealBot |

## Scoring Scale

| Score | Meaning |
|-------|---------|
| 9-10 | Exceptional — top 5% |
| 7-8 | Strong — clear positive signal |
| 5-6 | Average — meets baseline |
| 3-4 | Weak — below expectations |
| 1-2 | Red flag — significant concern |

## Company Scoring (`company-scoring.yaml`)

Three independent themes, each scored 1-10:

- **Climate & Sustainability**: Electrification, food/ag, bioeconomy, circular economy
- **Human Health**: Behavioral health, personalized health, food as medicine, longevity
- **Tomorrow's Workforce**: Personalized learning, reskilling, workforce augmentation, AI for SMBs

Key rules:

- **Core Business Test**: Thesis area must be the PRIMARY value proposition (not a side benefit) to score 5+
- **Filter threshold**: 5 (any theme >= 5 passes)
- **Exclusions**: Financial services, entertainment, gaming, crypto always score 1-3

## Founder Scoring (`founder-scoring.yaml`)

Single holistic 1-10 score evaluating:

- Built and shipped things before
- Deep domain expertise
- Elite credentials
- Authentic connection to the problem
- Strong network

## Investor Routing (`investors.yaml`)

Maps thesis fit to BV team members:

- **Rick Moss** (ID: 2999193): Climate, Sustainability, Electrification
- **Wes Selke** (ID: 2999192): Health, Food, Nutrition, Bioeconomy
- **Lyndsey Boucherle** (ID: 5794280): Workforce, Education, Circular Economy

## Consumer Repos

These repos fetch rubrics at runtime via raw GitHub URL with local cache fallback:

- [acceleratorbot](https://github.com/BV-Eng/acceleratorbot) — Accelerator company scoring
- [dealbot](https://github.com/BV-Eng/dealbot) — PitchBook company + founder scoring
- [stealthbot](https://github.com/BV-Eng/stealthbot) — Founder scoring from LinkedIn data
- [bv-pipeline](https://github.com/BV-Eng/bv-pipeline) — AI deal evaluation dashboard

## How to Edit

1. Log into GitHub with `eng@better.vc`
2. Click on the file you want to edit
3. Click the pencil icon (or use the "Edit on GitHub" links from the [BV Hub](https://bv-engineering-hub.vercel.app/deal-flow/rubrics))
4. Make your changes
5. Click **"Commit changes..."** (green button, top right)
6. All bots pick up the new rubric on their next run

## How Changes Propagate

Bots fetch rubrics at runtime using this priority:

1. GitHub raw URL (`raw.githubusercontent.com/BV-Eng/bv-rubrics/main/...`)
2. GitHub API fallback
3. Local `.rubrics-cache/` directory (last resort)

No build, deployment, or restart needed.

---

## Important Notes

- **Git identity**: All commits must use `eng@better.vc` or Vercel deploys will fail.
  ```bash
  git config user.email "eng@better.vc"
  git config user.name "Better Ventures Bot"
  ```
- **Scoring rubrics** are centralized in [bv-rubrics](https://github.com/BV-Eng/bv-rubrics). Never duplicate scoring logic.
- **BV Engineering Hub**: [bv-engineering-hub.vercel.app](https://bv-engineering-hub.vercel.app) — central dashboard for all tools.
- **Full documentation**: [bv-engineering-docs](https://github.com/BV-Eng/bv-engineering-docs)
