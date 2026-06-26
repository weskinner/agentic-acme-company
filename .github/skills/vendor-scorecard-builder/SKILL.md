---
name: vendor-scorecard-builder
description: 'Use when comparing print-on-demand providers (for example Printify providers and backup vendors) across cost, SLA, quality, geography, and branding options before setup or routing decisions.'
argument-hint: 'Provide candidate providers, target countries, monthly order volume, SKU mix, and margin goals.'
user-invocable: true
---

# Vendor Scorecard Builder

## Overview

Build a consistent vendor comparison scorecard for POD printing and shipping decisions. Use this skill to pick primary and backup providers with clear, evidence-based tradeoffs.

## When to Use

Use this skill when:
- Choosing between multiple Printify print providers
- Comparing Printify against a backup vendor (for example Printful or Gelato)
- Re-evaluating provider mix after SLA or quality issues
- Preparing launch-readiness decisions for new SKUs or markets

Do not use this skill when:
- You only need legal clause review (use commercial agreement workflow)
- You are handling a single failed order incident (use incident SOP workflow)

## Required Inputs

Collect these before scoring:
- Store platform
- Target shipping countries/regions
- Monthly order volume forecast
- SKU count and top SKU list
- Target gross margin
- Expected delivery promise to customers
- Candidate providers list

If any required input is missing, state assumptions explicitly and mark confidence as medium or low.

## Scoring Model

Score each provider from 1 to 5 in each category, then apply weights.

| Category | Weight | What to Evaluate |
|---|---:|---|
| Cost | 30% | Unit cost, shipping cost, surcharge risk, margin fit |
| SLA/Speed | 25% | Production time, delivery consistency, peak-season behavior |
| Quality | 20% | Print consistency, defect/reprint rate, sample results |
| Geography/Coverage | 15% | Coverage in target markets, local production proximity |
| Branding Options | 10% | Pack-ins, labels, packaging, white-label features |

### Rating Scale
- 5: Excellent, low risk, strongly exceeds target
- 4: Good, meets target with minor caveats
- 3: Acceptable, usable but notable tradeoffs
- 2: Weak, likely operational risk
- 1: Unacceptable for planned use

## Procedure

1. Confirm context and constraints.
2. Build a candidate list (Printify providers plus backup vendors).
3. Score each provider by category using available data and assumptions.
4. Calculate weighted total score.
5. Rank providers and recommend:
- Primary provider by SKU cluster and destination market
- Backup provider for failover
6. Define activation triggers for failover routing.
7. Call out data gaps and next validation actions.

## Failover Trigger Defaults

Use these defaults unless better thresholds are provided:
- On-time delivery below 92% for 2 consecutive weeks
- Defect/reprint rate above 2.5% for 2 consecutive weeks
- Average production time misses stated SLA by more than 1.5 business days

## Output Format

Return results in this structure:

1. Comparison Context
- Scope, assumptions, and missing inputs

2. Provider Scorecard Table
- Provider
- Cost score and notes
- SLA/Speed score and notes
- Quality score and notes
- Geography score and notes
- Branding score and notes
- Weighted total

3. Recommendation
- Primary provider and why
- Backup provider and why
- Best-fit SKU clusters and destination markets

4. Risk and Controls
- Top risks by provider
- Required safeguards before launch

5. Next Validation Steps
- Sample tests required
- SLA checks required
- Data to collect before final approval
