# Paid Media Knowledge Base (for Claude Agents)

## Overview

This repository contains the structured reference data and skills required for Claude to generate accurate Paid Media campaign strategies, channel mixes, tactics, and media plans.

Claude reads this repository to ensure outputs are:

- Consistent  
- Non-hallucinated  
- Based on Construct Digital’s actual benchmarks and tactic structures  
- In line with our internal media planning philosophy  

This repository does not contain prompts or workflow files.  
It is purely a knowledge base that Claude and n8n use as source-of-truth.

---

## Repository Structure

/
├─ schema/
│ ├─ benchmark.csv
│ ├─ brief.csv
│ ├─ country_tier.csv
  ├─ media_plan.csv
│ └─ tactic_library.csv
│
├─ skills/
│ └─ paid-media-strategist-construct.md
│
└─ README.md


---

## Folder & File Descriptions

### `/schema/`

Contains all structured data Claude must reference during strategy, tactics, and media plan generation.

#### `benchmark.csv`
Performance benchmarks used for estimation:
- CTR  
- CPC  
- CR  
- CPM  

Across:
- Channel  
- Platform  
- Objective  
- Funnel stage  
- Market  
- Performance level (Low / Avg / High)

Used by Claude to calculate impressions, clicks, conversions, and CPL.

#### `brief.csv`
Schema defining required input fields for proposal briefs:
- Market  
- Objective  
- KPI mode (budget or KPI driven)  
- Budget or target KPI  
- Audience  
- Constraints  
- Notes  

Ensures consistent interpretation of all briefs.

#### `country_tier.csv`
Defines tier classifications for markets (e.g., Tier 1, Tier 2, Tier 3), which Claude may use for:
- Benchmark adjustments  
- Cost assumptions  
- Budget weighting logic  

#### `tactic_library.csv`
Master list of allowed tactics Claude may recommend.  
Includes:
- Funnel stage  
- Channel  
- Platform  
- Ad type  
- Objective  
- Human-readable label  
- Description  
- Default budget weight  

Prevents hallucinated channels or invalid tactics.

---

### `/skills/`

Contains Claude’s core persona and strategic framework.

#### `paid-media-strategist-construct.md`
Defines how Claude should think as a senior Construct Digital Paid Media Strategist.

Includes:
- Lead generation philosophy  
- Funnel design principles  
- Channel roles  
- Tactical mapping rules  
- How to use benchmark data  
- How to reason about budgets and KPIs  
- Required structure of outputs  

Ensures all strategies match the Construct Digital methodology.

---

## How Claude Uses This Repository

Claude will:

1. Load the **paid-media-strategist-construct.md** skill  
2. Read files in `/schema/`:
   - `brief.csv`  
   - `tactic_library.csv`  
   - `benchmark.csv`  
   - `country_tier.csv`
3. Generate:
   - Campaign strategy  
   - Funnel structure  
   - Channel mix  
   - Tactic plan  
   - Media plan with numbers  

This ensures outputs are grounded in real data and agency standards.

---

## Purpose of This Repository

This repo provides a stable, non-changing source of truth for Claude.

It is designed to standardize:
- How Claude reads input data  
- How Claude selects tactics  
- How Claude calculates media plans  

This repo **does not** contain:
- Prompts  
- n8n workflows  
- Deck templates  
- JSON transformation scripts  

Those are maintained separately.
