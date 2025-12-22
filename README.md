# Paid Media Automation (Claude Skill)

## Overview

This repository contains a fully automated **Claude Skill** for Paid Media campaign development at Construct Digital. It orchestrates end-to-end campaign workflows from strategy through media planning to quotation generation.

The Skill provides:

- **Automated workflow orchestration** across Strategy → Media Plan → Estimator
- **Structured reference data** (benchmarks, tactics, pricing, ad specs)
- **Standardized outputs** based on Construct Digital's methodology
- **Session-based context management** with cascading revisions
- **Non-hallucinated recommendations** grounded in real agency data

Unlike a passive knowledge base, this is an **active automation system** that Claude uses to autonomously generate campaign deliverables through conversational workflows.

---

## Core Workflows

### Workflow 1: Strategy
**Generates:** Campaign strategy, funnel design, channel mix, tactical recommendations

**Process:**
1. Analyzes brief requirements
2. Designs 3-stage funnel (Prospecting → Retargeting → Nurturing)
3. Selects channels and tactics from tactic_library.csv
4. Maps tactics to funnel stages
5. Outputs structured campaign strategy

### Workflow 2: Media Plan
**Generates:** Media plan with budget allocation and performance projections

**Process:**
1. Allocates budget across channels and tactics
2. Pulls performance benchmarks from benchmark.csv
3. Calculates impressions, clicks, conversions, CPL
4. Outputs formatted media plan table

### Workflow 3: Estimator
**Generates:** Campaign quotation (pricing estimate) for client

**Process:**
1. Classifies campaign (Essential vs Custom)
2. Identifies line items (Fixed, Variable, Optional)
3. Looks up pricing from ratecard.csv
4. Integrates media budget from Media Plan
5. Outputs 3-column quotation table

**Dependencies:** Strategy → Media Plan → Estimator (sequential)

---

## Repository Structure

```
/
├── schema/
│   ├── benchmark.csv           # Performance benchmarks (CTR, CPC, CR, CPM)
│   ├── brief.txt               # Input brief schema
│   ├── country_tier.csv        # Market tier classifications
│   ├── media_plan.csv          # Media plan output schema
│   ├── ratecard.csv            # Construct Digital pricing (300KB+)
│   └── tactic_library.csv      # Approved tactics and channels
│
├── skills/
│   ├── paid-media-strategist-construct.md    # Main Skill file (workflows + logic)
│   └── SKILL_USAGE_GUIDE.md                  # Usage documentation
│
├── ads-production-template/    # Ad specifications templates
├── prompts/                    # Workflow prompts
├── sample-proposals/           # Reference outputs
└── README.md
```

---

## Key Files

### `/skills/paid-media-strategist-construct.md`
**The core Skill file** that defines:
- Workflow orchestration logic (Strategy → Media Plan → Estimator)
- Command interface ("Generate strategy", "Generate media plan", "Generate estimator")
- Revision behaviors (cascading vs non-cascading)
- Output format specifications
- Execution sequencing rules
- Schema integration points

This is what Claude loads to become a Paid Media Strategist.

### `/skills/SKILL_USAGE_GUIDE.md`
Comprehensive documentation covering:
- All workflow triggers and commands
- Input requirements for each workflow
- Output formats and examples
- Dependency rules
- Revision behaviors
- File structure and dependencies

### `/schema/ratecard.csv`
**Construct Digital's pricing database** with:
- 3,100+ lines of detailed resource allocation
- Cost rates and sell rates by role (Strategist, Creative, Developer, etc.)
- Deliverable pricing (Essential vs Custom campaigns)
- Resource effort breakdowns
- Internal cost/sell calculations

Used by Workflow 3 (Estimator) for quotation generation.

### `/schema/tactic_library.csv`
**Master tactics reference** containing:
- Funnel stage mappings
- Channel and platform combinations
- Ad types and objectives
- Default budget weights
- Tactic descriptions

Prevents hallucinated tactics — all recommendations must exist in this library.

### `/schema/benchmark.csv`
**Performance benchmarks** across:
- Channels (Meta, Google, LinkedIn, etc.)
- Objectives (Leads, Traffic, Conversions)
- Funnel stages (Prospecting, Retargeting, Nurturing)
- Markets and tiers
- Performance levels (Low / Avg / High)

Used by Workflow 2 (Media Plan) for projections.

### `/schema/brief.txt`
Schema defining required brief inputs:
- Market and audience
- Objective and KPI mode
- Budget or target KPI
- Constraints and notes

Ensures consistent brief interpretation.

### `/schema/country_tier.csv`
Market tier classifications (Tier 1/2/3) used for:
- Benchmark adjustments
- Cost assumptions
- Budget weighting logic

### `/ads-production-template/`
Contains platform-specific ad specification templates:
- Meta (Facebook/Instagram)
- Google (Search, Display, YouTube)
- LinkedIn
- TikTok

Used to generate ad production specs after Media Plan is finalized.

---

## How It Works

### 1. Session-Based Context
Workflows operate within a conversation session. Claude maintains context across multiple workflow executions, allowing:
- Sequential dependencies (Strategy feeds into Media Plan)
- Cascading revisions (updating Strategy recalculates Media Plan)
- Reference to prior outputs

### 2. Explicit Commands
Users trigger workflows with explicit commands:
- `"Generate strategy"`
- `"Generate media plan"` / `"Media plan only"`
- `"Generate estimator"` / `"Generate quotation"`

### 3. Cascading Revisions
Workflow updates cascade forward, not backward:
- **Revise strategy** → Recalculates Media Plan + Estimator
- **Revise media plan** → Recalculates Estimator only
- **Revise estimator** → No cascade (standalone)

### 4. Data-Grounded Outputs
All outputs are grounded in repository data:
- Tactics must exist in `tactic_library.csv`
- Benchmarks pulled from `benchmark.csv`
- Pricing from `ratecard.csv`
- No hallucinated channels, metrics, or pricing

---

## Usage

### Quick Start
1. Load the Skill: `/skills/paid-media-strategist-construct.md`
2. Provide campaign brief
3. Run workflows in sequence:
   - `"Generate strategy"`
   - `"Generate media plan"`
   - `"Generate estimator"`

### Revision Workflow
- `"Revise the strategy"` → Full recalculation
- `"Revise the media plan"` → Partial recalculation
- `"Revise the estimator"` → Standalone update

### Documentation
See `/skills/SKILL_USAGE_GUIDE.md` for:
- Complete command reference
- Workflow examples
- Dependency rules
- Output format specifications

---

## Design Philosophy

This repository embodies Construct Digital's approach to campaign automation:

### 1. **Deterministic Over Creative**
Workflows follow strict logic, not subjective interpretation. Tactics, benchmarks, and pricing are predefined — Claude orchestrates, not invents.

### 2. **Minimal Hallucination**
Every recommendation must have a source:
- Tactics from `tactic_library.csv`
- Benchmarks from `benchmark.csv`
- Pricing from `ratecard.csv`

If data doesn't exist, Claude asks rather than guesses.

### 3. **Workflow Orchestration**
Not a chatbot — a workflow automation system. Clear inputs, deterministic processing, structured outputs.

### 4. **Agency Standards**
Outputs match Construct Digital's:
- Lead generation philosophy
- 3-stage funnel model
- Channel role definitions
- Budget allocation principles
- Pricing structure

### 5. **Maintainable Truth**
Repository data is the single source of truth. Update tactics, benchmarks, or pricing here — workflows adapt automatically.

---

## Maintenance

### Adding New Tactics
Edit `/schema/tactic_library.csv`:
- Define funnel stage, channel, platform, objective
- Set default budget weight
- Add description

### Updating Benchmarks
Edit `/schema/benchmark.csv`:
- Add rows for new channel/objective/market combinations
- Set CTR, CPC, CR, CPM values
- Define performance tier (Low/Avg/High)

### Updating Pricing
Edit `/schema/ratecard.csv`:
- Update resource cost/sell rates
- Modify deliverable pricing
- Adjust effort allocations

### Modifying Workflows
Edit `/skills/paid-media-strategist-construct.md`:
- Update workflow logic in respective sections
- Modify command interface if needed
- Update revision behaviors
- Maintain execution sequencing rules

**Note:** After modifying the Skill, update `/skills/SKILL_USAGE_GUIDE.md` accordingly.

---

## What This Repository Is NOT

- ❌ A passive knowledge base (it's an active automation system)
- ❌ A prompt library (it's a structured Skill with workflows)
- ❌ A template repository (it's executable logic)
- ❌ A documentation site (it's operational code)

This is a **production automation system** that Claude executes to deliver campaign strategies, media plans, and quotations.

---

## Related Resources

- **Skill File:** `/skills/paid-media-strategist-construct.md`
- **Usage Guide:** `/skills/SKILL_USAGE_GUIDE.md`
- **Tactic Library:** `/schema/tactic_library.csv`
- **Benchmarks:** `/schema/benchmark.csv`
- **Pricing:** `/schema/ratecard.csv`

---

## Version

**Current Workflows:** 3 (Strategy, Media Plan, Estimator)
**Last Updated:** December 2024
**Maintained By:** Construct Digital
