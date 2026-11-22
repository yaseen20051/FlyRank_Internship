# FlyRank Internship — Content-Day Performance & Decline-Risk Triage

This repository contains the weekly assignments and final capstone for the FlyRank ML Internship.

## Capstone research paper

**Published paper:** https://yaseen20051.github.io/FlyRank_Internship/  
**Required submission pointer:** `submission/paper_url.txt`

## Research question and lane

**Lane:** Refresh / Content Opportunity Scoring.

Using signals available through March 15, 2026, can eligible content items be ranked by their likelihood of showing a meaningful decline in Google Search Console clicks per measured day during March 16–31, so human reviewers can prioritize investigation?

## Repository structure

- `work/notebooks/`: weekly notebooks W01–W07 and the capstone notebook.
- `work/outputs/`: generated local receipts; private by default.
- `work/outputs/public/`: aggregate, public-safe capstone receipts only.
- `work/figures/`: aggregate charts reviewed for public release.
- `docs/index.html`: deployed research paper.
- `submission/paper_url.txt`: exactly one line containing the deployed paper URL.

## Reproduction order

1. Run W04 to create the March eligibility snapshot and frozen baseline.
2. Run W05 to train the models and create `w05_metrics.json` plus the private held-out predictions file.
3. Run W06 using the W05 metrics and predictions to audit validation and inspect errors.
4. Run W07 using the W05 receipts to build the human-review action playbook.
5. Run `work/notebooks/capstone.ipynb` after the W05 and W07 receipts are available. Its final cell creates aggregate-only metrics and charts under `work/outputs/public/` and `work/figures/`.

Use Colab Secrets for Hugging Face credentials. Never paste tokens into notebooks or commit credentials.

## Privacy and publication rules

- Keep `w05_test_predictions.csv`, `w07_private_action_queue.csv`, page/client identifiers, raw exports, private queries, client names, domains and URLs out of public commits and the paper.
- The repository's `.gitignore` excludes generated private outputs by default. Review `git status` before every commit.
- Only commit aggregate summaries and charts after checking that they contain no identifiers or row-level records.
- The anonymized starter CSV under `data/raw/` is retained for the early W01/W02 starter exercises; do not add further warehouse extracts or client-level exports.

## Method and interpretation

The target is a proxy: at least a 20% reduction in clicks per measured day between the two March windows. The headline evaluation uses a client-group holdout and one March period. It is not multi-month temporal validation and does not establish that content refreshes cause recovery.

**Baseline comparability:** W04 documents the frozen rule as `log1p(early_impressions)`. The executed W05 comparison uses a freshness-adjusted baseline score. The reported W05 metrics are preserved as actually executed, and the paper discloses the mismatch. They must not be described as a strict comparison against the exact frozen W04 rule. A future apples-to-apples rerun should evaluate the frozen rule on the identical held-out rows.

## Data credit

Built on the [FlyRank ML Internship dataset](https://flyrank.ai).
