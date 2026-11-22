# FlyRank Internship — Content-Day Performance & Decline-Risk Triage

This repository contains the weekly assignments and final capstone for the FlyRank ML Internship.

## Capstone research paper

The public research paper is deployed with GitHub Pages:

**https://yaseen20051.github.io/FlyRank_Internship/**

The same URL is recorded in `submission/paper_url.txt`, as required by the capstone brief.

## Project question

Using signals available through March 15, 2026, can eligible content items be ranked by their likelihood of showing a meaningful decline in Google Search Console clicks per measured day during March 16–31, so human reviewers can prioritize investigation?

**Lane:** Refresh / Content Opportunity Scoring.

## Repository structure

- `work/notebooks/`: weekly notebooks W01–W07 and the capstone notebook.
- `work/outputs/`: local execution receipts; do not publish private queues or raw exports.
- `work/figures/`: public-safe aggregate figures.
- `docs/index.html`: deployed research paper.
- `submission/paper_url.txt`: mandatory direct URL of the deployed paper.

## Reproduction order

Run W04, W05, W06, W07, then `work/notebooks/capstone.ipynb`. Use the notebook instructions for data access. Keep credentials in Colab Secrets; never commit tokens.

## Important interpretation

The target is a proxy: at least a 20% reduction in clicks per measured day between the two March windows. The evaluation uses a client-group holdout and a single March period. It is not multi-month temporal validation and does not establish that content refreshes cause recovery.

**Baseline comparability note:** the frozen W04 baseline was documented as `log1p(early_impressions)`, while W05's evaluated baseline implementation applies an additional freshness multiplier. The paper discloses this mismatch; a strict apples-to-apples rerun is needed to resolve it.

## Data credit

Built on the [FlyRank ML Internship dataset](https://flyrank.ai).
