# BV Rubrics

Centralized scoring rubrics for Better Ventures deal flow automation. These YAML files are the single source of truth for company and founder evaluation criteria across all BV pipelines.

## Files

| File | Purpose |
|------|---------|
| `company-scoring.yaml` | Investment thesis, 3 themes, keywords, exclusions, scoring scale |
| `founder-scoring.yaml` | Holistic founder scoring prompt and scale (single 1-10 score) |
| `investors.yaml` | Rick/Wes/Lyndsey routing: themes, keywords, specializations |
| `prestigious-lists.yaml` | Top VCs, accelerators, and notable angels |

## Scoring Scale (same for companies and founders)

| Score | Meaning |
|-------|---------|
| 9-10 | Exceptional — top 5% |
| 7-8 | Strong — clear positive signal |
| 5-6 | Average — meets baseline expectations |
| 3-4 | Weak — below expectations |
| 1-2 | Red flag — significant concern |

## Consumer Repos

These repos fetch rubrics at runtime via raw GitHub URL with local cache fallback:

- [pitchbook-pipeline](https://github.com/BV-Eng/pitchbook-pipeline) — PitchBook company + founder scoring
- [BV-Acceleratorbot](https://github.com/BV-Eng/BV-Acceleratorbot) — Accelerator company scoring
- [affinity-sync](https://github.com/BV-Eng/affinity-sync) — Founder scoring from LinkedIn data

## How to Edit

1. Edit the YAML file directly in GitHub (click the pencil icon)
2. Commit the change
3. All pipelines will pick up the new rubric on their next run

No packages to publish, no deploys needed.
