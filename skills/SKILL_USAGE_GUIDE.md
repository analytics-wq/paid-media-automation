# Paid Media Strategist Skill — Usage Guide

This guide explains how to use the **paid-media-strategist-construct** Claude Skill for automated paid media strategy, media planning, and ads production specification generation.

---

## Overview

The **paid-media-strategist-construct** Skill is an intelligent automation system that transforms campaign briefs into complete, executive-ready paid media deliverables. It combines strategic thinking, analytical rigor, and workflow automation to eliminate repetitive prompt engineering.

### What It Does

The Skill automates three core workflows:

1. **Strategy Generation** — Strategic interpretation, audience segmentation, channel mix, funnel architecture, messaging, and campaign flow
2. **Media Plan Generation** — Budget allocation, performance forecasting, and Google Sheets-ready media plan tables
3. **Ads Production Specifications** — Creative briefing templates for LinkedIn, Meta, and Google ads

### How It Works

Once uploaded to Claude, the Skill:
- Auto-detects when you paste a campaign brief
- Executes the appropriate workflow based on your command
- Maintains session context for iterative revisions
- Supports both full workflows and granular section updates

---

## Required Files

### Schema Files (Input Data)

These files must be available in your Claude project or GitHub repository:

| File | Purpose | Location |
|------|---------|----------|
| `brief.txt` | Campaign objectives, audience, constraints | `/schema/brief.txt` |
| `tactic_library.csv` | Approved paid media tactics | `/schema/tactic_library.csv` |
| `benchmark.csv` | Performance benchmarks (CTR, CPC, CR1, CR2) | `/schema/benchmark.csv` |
| `country_tier.csv` | Market-to-tier mapping | `/schema/country_tier.csv` |
| `media_plan.csv` | Media plan template structure | `/schema/media_plan.csv` |

### Ads Production Templates

These CSV files define creative specifications for each platform:

| File | Platform | Location |
|------|----------|----------|
| `linkedin_ads_production.csv` | LinkedIn | `/ads-production-template/linkedin_ads_production.csv` |
| `meta_ads_production.csv` | Meta | `/ads-production-template/meta_ads_production.csv` |
| `google_ads_production.csv` | Google | `/ads-production-template/google_ads_production.csv` |

---

## Installation

### Option 1: Upload to Claude Projects

1. Go to your Claude Project settings
2. Navigate to **Custom Instructions** or **Skills**
3. Upload `/skills/paid-media-strategist-construct.md`
4. Ensure all schema files and templates are accessible in the project

### Option 2: Use with Claude Code

1. Ensure the repository structure is intact:
   ```
   paid-media-automation/
   ├── schema/
   │   ├── brief.txt
   │   ├── tactic_library.csv
   │   ├── benchmark.csv
   │   ├── country_tier.csv
   │   └── media_plan.csv
   ├── ads-production-template/
   │   ├── linkedin_ads_production.csv
   │   ├── meta_ads_production.csv
   │   └── google_ads_production.csv
   └── skills/
       └── paid-media-strategist-construct.md
   ```
2. Load the Skill in your Claude session
3. Begin working with your brief

---

## Available Commands

### Auto-Triggered Workflows

The Skill automatically detects when you paste content from `brief.txt` and runs the full workflow unless instructed otherwise.

### Explicit Commands

| Command | What It Does | Output |
|---------|--------------|--------|
| **"Generate media strategy"** | Generate strategy + media plan | Strategy (6 sections) + Media Plan table |
| **"Run full workflow"** | Same as above | Strategy + Media Plan |
| **"Generate ads production template"** | Generate creative brief | Ads Production Specs (all funnel stages) |
| **"Generate ads specs"** | Same as above | Ads Production Specs |
| **"Strategy only"** | Generate strategy without media plan | Strategy (6 sections) only |
| **"Media plan only"** | Generate media plan using existing strategy | Media Plan table only |
| **"Ads specs only"** | Generate ads specs using existing media plan | Ads Production Specs only |

### Revision Commands

#### Full Revisions

| Command | What It Does | Cascade Behavior |
|---------|--------------|------------------|
| **"Revise the strategy"** | Regenerate Strategy + Media Plan | **Cascades forward**: Also regenerates Ads Specs if they were previously generated |
| **"Revise the media plan"** | Regenerate Media Plan only | **Cascades forward**: Also regenerates Ads Specs if they were previously generated. **Does NOT cascade backward** (keeps existing Strategy) |
| **"Revise the ads specs"** | Regenerate Ads Specs only | **No cascade**: Keeps existing Strategy and Media Plan |

#### Granular Section Revisions

| Command | What It Does |
|---------|--------------|
| **"Revise Campaign Overview"** | Regenerate only the Campaign Overview section |
| **"Revise Audience Segmentation"** | Regenerate only the Audience Segmentation section |
| **"Revise Channel Mix"** | Regenerate only the Recommended Channel Mix section |
| **"Revise Conversion Funnel"** | Regenerate only the Conversion Funnel Architecture section |
| **"Revise Messaging"** | Regenerate only the Messaging Structure section |
| **"Revise Campaign Flow"** | Regenerate only the Campaign Flow section (Layer 1 + Layer 2) |

**Important:** After granular revisions, the Skill will ask if you want to regenerate the Media Plan to reflect changes. If the revision affects CTAs or tactics, regenerating downstream outputs (Media Plan, Ads Specs) is recommended.

---

## How Workflows Run

### Workflow 1: Strategy & Media Plan

**Trigger:** Auto-detection of brief content OR explicit command ("Generate media strategy")

**Inputs:**
- `brief.txt`
- `tactic_library.csv`
- `benchmark.csv`
- `country_tier.csv`
- `media_plan.csv`

**Process:**
1. Read and interpret brief
2. Generate **Strategy** (6 sections):
   - Campaign Overview
   - Audience Segmentation & Personas
   - Recommended Channel Mix
   - Conversion Funnel Architecture (with single CTA per stage)
   - Messaging Structure
   - Campaign Flow (Layer 1: Tactics + Layer 2: Real Flow)
3. Generate **Media Plan**:
   - Map tactics to benchmarks
   - Allocate budget (Budget-Driven or KPI-Driven)
   - Forecast performance (Impressions, Clicks, Leads, Acquisitions, CPA, CPL)
   - Output Google Sheets-ready table

**Output:** Strategy narrative + Media Plan table

---

### Workflow 2: Ads Production Specifications

**Trigger:** Explicit command ("Generate ads production template")

**Prerequisite:** Media Plan must exist in the current session

**Inputs:**
- Latest Media Plan output from session
- `linkedin_ads_production.csv`
- `meta_ads_production.csv`
- `google_ads_production.csv`

**Process:**
1. Extract tactics from Media Plan (in order: Prospecting → Retargeting → Nurturing)
2. Detect platform for each tactic (LinkedIn, Meta, Google)
3. Match tactic to appropriate CSV spec template
4. Generate creative specifications with Google Doc-safe formatting
5. Include CTAs from Strategy Funnel Architecture

**Output:**
- Campaign Asset Overview (list of assets by funnel stage)
- Prospecting Specs (per-tactic creative fields)
- Retargeting Specs (per-tactic creative fields)
- Nurturing Specs (per-tactic creative fields)
- Missing Specs (unmapped tactics requiring manual scoping)

---

## Workflow Dependencies

```
┌─────────────┐
│   Strategy  │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Media Plan  │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  Ads Specs  │
└─────────────┘
```

### Dependency Rules

1. **Media Plan requires Strategy**
   - Uses tactics from Campaign Flow
   - Uses CTAs from Conversion Funnel Architecture
   - Cannot run without Strategy in session

2. **Ads Specs require Media Plan**
   - Uses tactic list and order from Media Plan
   - Inherits CTAs from Strategy
   - Cannot run without Media Plan in session

3. **Session Context**
   - Workflows operate within the current conversation
   - "Media plan only" or "Ads specs only" require prerequisites in the same session
   - If prerequisites are missing, Skill will prompt you to run the full workflow

---

## Revision Logic

### Cascading Behavior

Revisions cascade **forward** but not **backward**:

| Revision | Regenerates | Rationale |
|----------|-------------|-----------|
| Strategy | Strategy + Media Plan + Ads Specs (if previously generated) | Strategy changes affect everything downstream |
| Media Plan | Media Plan + Ads Specs (if previously generated) | Media Plan changes affect Ads Specs, but Strategy remains valid |
| Ads Specs | Ads Specs only | Ads Specs are terminal output; no downstream dependencies |

### Granular Revisions

When you revise a specific section (e.g., "Revise Messaging"), the Skill:
1. Regenerates only that section
2. Preserves all other sections unchanged
3. Maintains consistency with unchanged sections
4. Asks if you want to regenerate Media Plan to reflect changes

**Best practice:** If granular revision affects CTAs or tactics, regenerate Media Plan and Ads Specs to maintain consistency.

---

## Example Usage Scenarios

### Scenario 1: Generate Everything from Scratch

**You:**
```
[Paste content from brief.txt]
```

**Skill:**
- Auto-detects brief
- Generates Strategy (6 sections)
- Generates Media Plan table
- Outputs both

**Result:** Complete Strategy + Media Plan ready for review

---

### Scenario 2: Generate Strategy, Then Add Ads Specs After Approval

**You:**
```
[Paste content from brief.txt]
```

**Skill:**
- Generates Strategy + Media Plan

**You (after reviewing):**
```
Generate ads production template
```

**Skill:**
- Generates Ads Production Specs using the Media Plan from the session

**Result:** Complete Strategy + Media Plan + Ads Specs

---

### Scenario 3: Revise Only the Messaging

**You:**
```
Revise Messaging
```

**Skill:**
- Regenerates Messaging Structure section only
- Asks: "Would you like to regenerate the Media Plan to reflect these changes?"

**You:**
```
Yes
```

**Skill:**
- Regenerates Media Plan using updated Strategy
- Asks: "Would you like to regenerate the Ads Specs to reflect these changes?"

**You:**
```
Yes
```

**Skill:**
- Regenerates Ads Specs using updated Media Plan

**Result:** Updated Messaging + Media Plan + Ads Specs, with all other Strategy sections preserved

---

### Scenario 4: Revise Media Plan Without Changing Strategy

**You:**
```
Revise the media plan
```

**Skill:**
- Regenerates Media Plan only
- Keeps existing Strategy unchanged
- If Ads Specs were previously generated, regenerates them automatically

**Result:** New Media Plan + updated Ads Specs, with Strategy preserved

---

### Scenario 5: Revise Entire Strategy After Client Feedback

**You:**
```
Revise the strategy
```

**Skill:**
- Regenerates entire Strategy (6 sections)
- Regenerates Media Plan
- If Ads Specs were previously generated, regenerates them automatically

**Result:** Completely new Strategy + Media Plan + Ads Specs

---

## Campaign Modes

The Skill supports two campaign modes, determined from `brief.txt`:

### Budget-Driven Mode

- Total budget is fixed
- Skill distributes budget across tactics
- Forecasts performance outcomes (Leads, Acquisitions)
- Optimizes allocation for funnel balance

### KPI-Driven Mode

- Target KPI is fixed (e.g., 500 Leads)
- Skill refines budget allocation until KPI is within ±10%
- Calculates required budget to achieve target
- Ensures realistic forecasting

---

## Output Formats

### Strategy Output

Structured narrative with 6 sections:
1. Campaign Overview (mode, objective, audience, markets)
2. Audience Segmentation & Personas (demographics, motivations, barriers)
3. Recommended Channel Mix (strategic role per channel)
4. Conversion Funnel Architecture (3 stages, single CTA per stage)
5. Messaging Structure (umbrella, prospecting, retargeting, nurturing messages)
6. Campaign Flow (tactic listing + real user flow)

**Format:** Clean, executive-ready narrative

---

### Media Plan Output

Google Sheets-ready table with columns:
- Funnel (Prospecting / Retargeting / Nurturing)
- Tactic
- Budget
- Budget Allocation %
- Impressions
- Clicks
- CTR
- CPC
- Leads
- Acquisitions
- CPA
- CPL

**Final row:** Totals (aggregated metrics + weighted averages)

**Format:** Table ready to copy-paste into Google Sheets

---

### Ads Production Specs Output

Structured creative brief with:
- Campaign Asset Overview (list of assets by funnel stage)
- Per-tactic specifications (grouped by Prospecting / Retargeting / Nurturing)
  - Text fields with character limits
  - Image fields with aspect ratios and resolutions
  - CTAs from Strategy Funnel Architecture

**Format:** Google Doc-safe (blank lines before placeholders to prevent collapse)

**Placeholders:**
- Text fields: `xxx`
- Image fields: `[LINK]`

**No file formats or sizes included** — only aspect ratios and resolutions.

---

## Best Practices

### 1. Always Start with a Complete Brief

Ensure `brief.txt` contains:
- Campaign objective
- Target audience details
- Programme/product description
- Markets (with country names matching `country_tier.csv`)
- Budget or KPI target
- Timeline and constraints

**Incomplete briefs** will result in incomplete or low-quality outputs.

---

### 2. Review Strategy Before Generating Ads Specs

The workflow is sequential:
1. Generate Strategy + Media Plan
2. **Review and approve**
3. Generate Ads Production Specs

This ensures Ads Specs are based on approved strategy and tactics.

---

### 3. Use Granular Revisions for Iterative Refinement

Instead of regenerating everything, use granular revisions:
- "Revise Campaign Flow" → if you want to change tactics
- "Revise Messaging" → if you want to adjust tone or hooks
- "Revise Audience Segmentation" → if personas need refinement

This preserves approved sections and speeds up iteration.

---

### 4. Cascade Forward When CTAs or Tactics Change

If you revise:
- **Conversion Funnel Architecture** (CTAs change) → regenerate Media Plan + Ads Specs
- **Campaign Flow** (tactics change) → regenerate Media Plan + Ads Specs

This ensures consistency across all outputs.

---

### 5. Validate Benchmarks Against Actual Performance

The Skill uses benchmarks from `benchmark.csv`. If your actual performance differs significantly:
- Update `benchmark.csv` with real data
- Regenerate Media Plan to reflect updated forecasts

---

## Troubleshooting

### Issue: "No Strategy found in session"

**Cause:** You requested "Media plan only" or "Ads specs only", but no Strategy exists in the current conversation.

**Solution:** Run "Generate media strategy" first.

---

### Issue: "Tactic not found in tactic_library.csv"

**Cause:** The Strategy referenced a tactic that doesn't exist in `tactic_library.csv`.

**Solution:**
- Check `tactic_library.csv` for available tactics
- Update the brief or constraints to match available tactics
- Regenerate Strategy

---

### Issue: "Spec not found — requires manual scoping"

**Cause:** A tactic in the Media Plan couldn't be mapped to `linkedin_ads_production.csv`, `meta_ads_production.csv`, or `google_ads_production.csv`.

**Solution:**
- Check if the tactic name matches expected patterns (contains "LinkedIn", "Meta", "Google", etc.)
- Add the missing spec to the appropriate CSV
- Manually scope the creative requirements

---

### Issue: Media Plan totals don't match budget

**Cause:** Rounding errors or budget allocation logic

**Solution:**
- Skill automatically adjusts to ensure totals match
- If issue persists, regenerate Media Plan
- Check if KPI-Driven mode is causing budget recalculation

---

### Issue: Ads Specs missing CTAs

**Cause:** CTAs weren't defined in Conversion Funnel Architecture

**Solution:**
- Revise Conversion Funnel to include single CTA per stage
- Regenerate Media Plan
- Regenerate Ads Specs

---

## Advanced Usage

### Changing Campaign Mode Mid-Session

If you need to switch from Budget-Driven to KPI-Driven (or vice versa):
1. Update `brief.txt`
2. Run "Revise the strategy"
3. Skill will detect new mode and regenerate accordingly

---

### Using Custom Benchmarks

If you have client-specific or historical benchmarks:
1. Update `benchmark.csv` with custom values
2. Ensure `tactic_name` and `tier` match exactly
3. Regenerate Media Plan

---

### Supporting New Platforms

To add support for new ad platforms (e.g., TikTok, Pinterest):
1. Create new CSV template (e.g., `tiktok_ads_production.csv`)
2. Add platform detection logic to Skill (or request update)
3. Ensure tactics in `tactic_library.csv` include platform name

---

## File Structure Summary

```
paid-media-automation/
├── schema/
│   ├── brief.txt                    # Campaign brief (input)
│   ├── tactic_library.csv           # Approved tactics (input)
│   ├── benchmark.csv                # Performance benchmarks (input)
│   ├── country_tier.csv             # Market tier mapping (input)
│   └── media_plan.csv               # Template structure (reference)
├── ads-production-template/
│   ├── linkedin_ads_production.csv  # LinkedIn specs (reference)
│   ├── meta_ads_production.csv      # Meta specs (reference)
│   └── google_ads_production.csv    # Google specs (reference)
├── prompts/
│   ├── media-strategy-prompt.txt    # Original strategy prompt (archived)
│   └── ads-production-prompt.txt    # Original ads prompt (archived)
└── skills/
    ├── paid-media-strategist-construct.md  # Main Skill file
    └── SKILL_USAGE_GUIDE.md               # This guide
```

---

## Command Quick Reference

| What You Want | Command | Prerequisite |
|---------------|---------|--------------|
| Full strategy + media plan | `Generate media strategy` | None (auto-detects brief) |
| Strategy only (no media plan) | `Strategy only` | None |
| Media plan only | `Media plan only` | Strategy in session |
| Ads specs | `Generate ads production template` | Media Plan in session |
| Revise everything | `Revise the strategy` | Strategy in session |
| Revise media plan only | `Revise the media plan` | Strategy + Media Plan in session |
| Revise ads specs only | `Revise the ads specs` | Media Plan + Ads Specs in session |
| Revise specific section | `Revise [Section Name]` | Strategy in session |

---

## Support & Feedback

For issues, questions, or feature requests:
- Check this guide first
- Review the Skill file (`paid-media-strategist-construct.md`) for detailed logic
- Contact the Construct Digital team for strategic guidance
- Submit GitHub issues for technical bugs

---

**Last Updated:** December 2025
**Skill Version:** 1.0
**Maintained by:** Construct Digital Strategy Team
