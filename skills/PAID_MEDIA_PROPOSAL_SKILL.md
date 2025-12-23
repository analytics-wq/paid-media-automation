# PAID MEDIA PROPOSAL GENERATION SKILL

## 1. SKILL PURPOSE & SCOPE

### 1.1 Purpose
This skill transforms paid media strategy outputs into production-grade Construct Digital proposal presentations. It is a **deterministic content-to-slide mapping system**, not a creative generation tool.

### 1.2 Scope
- **IN SCOPE**: Paid media campaign proposals, QBRs, media plans
- **OUT OF SCOPE**: Brand strategy decks, creative pitches, annual planning, workshop decks
- **NON-NEGOTIABLE**: All outputs must prevent text-dump slides through mandatory visual abstraction

### 1.3 System Architecture
```
Strategy Input → Visual Pattern Matching → Layout Selection → Content Compression → Replacement JSON
```

---

## 2. INPUT INTERPRETATION RULES

### 2.1 Mandatory Input Fields
The following fields MUST be present. Halt execution if missing:

```json
{
  "client_name": "string (required)",
  "campaign_objective": "string (required)",
  "target_audience": "array of persona objects (required, min 1, max 3)",
  "channels": "array of channel objects (required)",
  "budget_total": "number (required)",
  "campaign_duration": "string (required)",
  "funnel_stages": "array (required, must be 3-4 stages)"
}
```

### 2.2 Optional Input Fields
```json
{
  "media_plan": "array of tactic objects",
  "timeline_milestones": "array",
  "budget_breakdown": "object",
  "kpis": "array",
  "landing_page_specs": "object",
  "reporting_cadence": "string"
}
```

### 2.3 Inference Prohibition
**NEVER INFER**:
- Budget allocations across channels
- Persona demographics without explicit data
- Funnel stage names (use client's terminology)
- Timeline dates
- KPI targets
- Channel rationale

**IF DATA IS MISSING**: Flag with `[CLIENT INPUT REQUIRED]` in output JSON.

---

## 3. VISUAL ABSTRACTION LAYER (CRITICAL)

### 3.1 Core Principle
**Before populating ANY slide, content must pass through visual abstraction**. Text paragraphs are REJECTED. All content must be transformed into one of the approved visual patterns below.

### 3.2 Visual Pattern Catalog

#### Pattern: FUNNEL DIAGRAM
**Use when**: Describing customer journey, conversion stages, or awareness-to-decision flow

**Visual structure**:
```
Awareness (Blue)    ← Stage 1: Traffic, Learn More
Consideration (Green)  ← Stage 2: Download Brochure, SQL
Decision (Purple)      ← Stage 3: Apply Now, Application
```

**Layout mapping**: Slide 28 (Funnel)
**Max text per stage**: 3 bullet points, 5 words each
**Required elements**: Stage label, primary action, tactic descriptor

**Reference**: NUS AIDF page 7

---

#### Pattern: CAMPAIGN FLOW DIAGRAM
**Use when**: Mapping channel tactics to funnel stages

**Visual structure**:
```
[Stage Column] → [Channel Boxes] → [Action Diamonds] → [Conversion]
```

**Layout mapping**: Slide 29 (Campaign Flow)
**Max boxes per stage**: 4
**Box content limit**: Channel name + 1 descriptor (max 4 words)

**Reference**: NUS AIDF page 8

---

#### Pattern: PERSONA CARDS
**Use when**: Defining 2-3 target audience segments

**Visual structure** (per card):
```
[Stock photo]
Persona Title (max 4 words)
---
About: 2 sentences max
Goals: 3 bullets, 8 words each
Expectations: 3 bullets, 8 words each
Demographics: Age, Location, Industry, Seniority (table format)
```

**Layout mapping**: Slide 41-42 (Persona, Persona Detail)
**Max personas**: 3
**Card arrangement**: Side-by-side for 2, stacked for 3

**Reference**: NUS AIDF page 4

---

#### Pattern: CHANNEL RATIONALE GRID
**Use when**: Justifying channel selection

**Visual structure**:
```
[Channel Logo Grid on Left]
[Rationale Column on Right]:
  - Why multichannel? (4 bullets, 3 words each)
  - What channels? (List with 1-line rationale each)
```

**Layout mapping**: Slide 27 (Channels)
**Max channels**: 8
**Rationale per channel**: 12 words maximum

**Reference**: NUS AIDF page 5

---

#### Pattern: MEDIA PLAN TABLE
**Use when**: Presenting budget allocation and projections

**Visual structure**:
```
| Funnel | Tactic | Budget | Budget % | Impressions | CTR | Clicks | CPC | Conversions | CPA |
```

**Layout mapping**: Slide 47 (Budget Table)
**Max rows**: 12 (including subtotals)
**Formatting rules**:
- Currency: SGD with comma separators
- Percentages: 1 decimal place
- CTR/CPC: 2 decimal places
- Highlight total row with blue background

**Reference**: NUS AIDF page 14

---

#### Pattern: TIMELINE GANTT
**Use when**: Showing campaign phases or milestones

**Visual structure**:
```
[Month headers across top]
[Activity rows with colored bars showing duration]
[Milestone markers as vertical lines]
```

**Layout mapping**: Slide 43 (Timeline)
**Max activities**: 6
**Max duration**: 12 months
**Color coding**: Match funnel stage colors

**Reference**: NUS AIDF page 19

---

#### Pattern: INVESTMENT SUMMARY TABLE
**Use when**: Breaking down pricing

**Visual structure**:
```
| Item | Description | Investment | After Discount |
[Section headers in blue]
[Line items in white]
[Total row in blue]
```

**Layout mapping**: Slide 47 (Budget Table)
**Max line items**: 15
**Description limit**: 60 characters

**Reference**: NUS AIDF page 20

---

#### Pattern: TWO-COLUMN COMPARISON
**Use when**: Explaining concepts with visual + text balance

**Visual structure**:
```
[Left: Diagram/Logos/Visual]  |  [Right: Bullets or short paragraphs]
```

**Layout mapping**: Slide 14 (Two Column)
**Text limit per column**: 80 words
**Bullets per column**: Max 5

**Reference**: NUS AIDF page 10

---

#### Pattern: SECTION DIVIDER
**Use when**: Transitioning between major deck sections

**Visual structure**:
```
[Full-bleed colored background rotating through brand colors]
Section Title (max 3 words)
Section Subtitle (max 8 words)
[Construct Digital logo and iconography]
```

**Layout mapping**: Slides 7-10 (Section dividers)
**Color rotation**: Blue → Red → Green → Purple → Yellow
**Text color**: White (except yellow background = black)

**Reference**: NUS AIDF page 3

---

### 3.3 Pattern Selection Logic

```
IF content type == "audience segmentation":
  → Use PERSONA CARDS pattern

ELIF content type == "channel selection":
  → Use CHANNEL RATIONALE GRID pattern

ELIF content type == "user journey" OR "conversion stages":
  → Use FUNNEL DIAGRAM pattern

ELIF content type == "channel-to-funnel mapping":
  → Use CAMPAIGN FLOW DIAGRAM pattern

ELIF content type == "budget with projections":
  → Use MEDIA PLAN TABLE pattern

ELIF content type == "pricing breakdown":
  → Use INVESTMENT SUMMARY TABLE pattern

ELIF content type == "project phases":
  → Use TIMELINE GANTT pattern

ELIF content type == "concept explanation":
  → Use TWO-COLUMN COMPARISON pattern

ELSE:
  → REJECT. Flag for manual review.
```

---

## 4. SLIDE MAPPING RULES

### 4.1 Mandatory Slide Sequence for Paid Media Proposals

```
Position  Layout Index  Content Type                    Visual Pattern
--------  ------------  ------------------------------  ---------------------------
1         0             Cover                           Title slide (blue)
2         29            Agenda                          Numbered section blocks
3         7             Section: Brief Recap            Section divider (blue)
4         15            Client brief summary            Content bullets
5         8             Section: Audiences              Section divider (green)
6         41-42         Target personas                 PERSONA CARDS
7         9             Section: Our Approach           Section divider (red)
8         27            Channel rationale               CHANNEL RATIONALE GRID
9         28            Funnel approach                 FUNNEL DIAGRAM
10        29            Campaign flow                   CAMPAIGN FLOW DIAGRAM
11        [varies]      Landing page mockup             Image slide (16-22)
12        [varies]      Ad format examples              Two-column (14)
13        10            Section: Media Plan             Section divider (purple)
14        47            Media plan table                MEDIA PLAN TABLE
15        43            Timeline                        TIMELINE GANTT
16        6             Section: Investment             Section divider (purple)
17        47            Investment summary              INVESTMENT SUMMARY TABLE
18        50            Closing                         Thank you slide (blue)
```

### 4.2 Slide Overflow Rules

**IF** persona count > 2:
- Use 2 slides (Slide 41 + Slide 42)

**IF** media plan rows > 12:
- Split into "Prospecting" and "Retargeting + Converting" tables across 2 slides

**IF** timeline > 6 months:
- Use quarterly grouping

**IF** investment line items > 15:
- Create "Summary" slide + "Detailed Breakdown" slide

### 4.3 Slide Deletion Rules

**NEVER include these slides in final sequence**:
- Slides 33, 51-65 (style guide and reference slides)
- Slides 34-40 (team slides) unless team introduction explicitly requested
- Slide 49 (case study) unless past work showcase requested

---

## 5. CONTENT COMPRESSION RULES

### 5.1 Text Limits by Element Type

| Element Type          | Max Characters | Max Words | Max Bullets | Max Lines |
|-----------------------|----------------|-----------|-------------|-----------|
| Slide title           | 60             | 8         | -           | 1         |
| Section subtitle      | 80             | 12        | -           | 1         |
| Bullet point          | 100            | 15        | -           | 1         |
| Bullet list per slide | -              | -         | 5           | -         |
| Table cell            | 50             | 8         | -           | 1         |
| Persona "About"       | 200            | 30        | -           | 2         |
| Channel rationale     | 80             | 12        | -           | 1         |

### 5.2 Compression Techniques

**Eliminate**:
- Filler words: "very", "really", "actually", "basically"
- Transition phrases: "moving forward", "as mentioned"
- Politeness qualifiers: "we believe that", "it is our opinion"

**Transform**:
- "We recommend a multichannel strategy" → "Multichannel strategy"
- "The campaign will run for 4 months" → "4-month campaign"
- "Target audience consists of mid-career professionals" → "Mid-career professionals"

**Abbreviate** (approved list only):
- FB/IG/LI (Facebook/Instagram/LinkedIn)
- CTA (Call to Action)
- SQL (Sales Qualified Lead)
- CPC/CPM/CPA (Cost Per Click/Mille/Action)
- KPI (Key Performance Indicator)
- QBR (Quarterly Business Review)

### 5.3 Shape Boundary Safety

All text MUST fit within shape boundaries defined in `layouts.md`. Apply these safety margins:

```
Top margin: 12pt
Bottom margin: 12pt
Left margin: 20pt
Right margin: 20pt
```

**Overflow detection**: Run `inventory.py --issues-only` after JSON generation. If overflow detected, apply aggressive compression or split content across slides.

---

## 6. BRAND & LAYOUT ENFORCEMENT

### 6.1 Brand Configuration Source
All brand rules are defined in `references/brand-config.json`. Do NOT deviate.

**Fonts**:
- Heading: Arial Bold
- Body: Arial Regular

**Colors** (from brand-config.json):
```json
{
  "primary_blue": "#1E5AA8",
  "primary_red": "#CC0000",
  "primary_green": "#00852B",
  "primary_yellow": "#FAC80A",
  "primary_purple": "#901F76",
  "text_dark": "#000000",
  "text_light": "#FFFFFF",
  "text_muted": "#434343"
}
```

**Section divider color rotation**:
Slide 7 (Blue) → Slide 8 (Green) → Slide 9 (Red) → Slide 10 (Purple) → Slide 6 (Yellow)

### 6.2 Layout Configuration Source
All layouts are defined in `references/layouts.md`. Shape indices are **zero-based**.

**Example**: Layout 28 (Funnel)
```
shape-0: Title (28pt)
shape-1: Intro text
shape-2-7: Funnel stages
```

### 6.3 Forbidden Actions
- **NO** custom layouts
- **NO** font substitutions
- **NO** color deviations
- **NO** free-form text boxes
- **NO** manual shape creation

---

## 7. OUTPUT CONTRACT

### 7.1 Replacement JSON Schema

```json
{
  "slide-0": {
    "shape-0": {
      "paragraphs": [
        {
          "text": "Campaign Plan Title",
          "font_name": "Arial",
          "font_size": 42,
          "bold": true,
          "alignment": "LEFT"
        }
      ]
    },
    "shape-1": {
      "paragraphs": [
        {
          "text": "Subtitle text",
          "font_name": "Arial",
          "font_size": 24,
          "bold": false
        }
      ]
    }
  },
  "slide-7": {
    "shape-0": {
      "paragraphs": [
        {
          "text": "Section Title",
          "font_size": 36,
          "color": "#FFFFFF"
        }
      ]
    }
  }
}
```

### 7.2 Paragraph Property Schema

**Required fields**:
- `text` (string)

**Optional fields**:
- `font_name` (string, default: "Arial")
- `font_size` (number, default: inherits from layout)
- `bold` (boolean, default: false)
- `italic` (boolean, default: false)
- `color` (hex string, default: "#000000")
- `bullet` (boolean, default: false)
- `level` (integer, 0-2, default: 0)
- `alignment` ("LEFT"|"CENTER"|"RIGHT", default: "LEFT")

### 7.3 Slide Index Array

In addition to replacement JSON, output a slide sequence array:

```json
{
  "slide_sequence": [0, 29, 7, 15, 8, 41, 9, 27, 28, 29, 16, 14, 47, 43, 10, 47, 50],
  "metadata": {
    "total_slides": 17,
    "sections": 4,
    "estimated_duration": "20 minutes",
    "template_version": "2022 v1.0"
  }
}
```

### 7.4 Validation Flags

Include validation metadata:

```json
{
  "validation": {
    "overflow_warnings": [],
    "missing_inputs": ["kpi_targets"],
    "pattern_usage": {
      "PERSONA_CARDS": 1,
      "FUNNEL_DIAGRAM": 1,
      "MEDIA_PLAN_TABLE": 1
    }
  }
}
```

---

## 8. INVOCATION INSTRUCTIONS

### 8.1 How to Invoke This Skill

**From Claude Chat**:
```
User: "I need to create a paid media proposal for [Client Name].
Here's the strategy: [paste strategy document or JSON]"

Claude: [Activates this skill, processes input, returns replacement JSON + slide sequence]
```

**From Claude Projects**:
Add this skill to project knowledge. Reference in system prompt:
```
"When user requests a paid media proposal, invoke PAID_MEDIA_PROPOSAL_GENERATION_SKILL"
```

### 8.2 Expected Behavior

1. **Validate inputs** against mandatory field requirements (Section 2.1)
2. **Parse content types** and assign visual patterns (Section 3.3)
3. **Map patterns to layouts** using layout index from `layouts.md` (Section 4)
4. **Compress content** to fit shape boundaries (Section 5)
5. **Generate replacement JSON** conforming to schema (Section 7.1)
6. **Generate slide sequence array** (Section 7.3)
7. **Return validation flags** (Section 7.4)

### 8.3 Expected Outputs

**Primary output**: `replacement.json`
- Ready to pass to `replace.py` script

**Secondary output**: `slide-sequence.txt`
- Comma-separated list for `rearrange.py` script

**Tertiary output**: Validation report (human-readable)
```
VALIDATION REPORT
-----------------
✓ All mandatory inputs present
✓ Visual patterns assigned: 6/6
✓ No text overflow detected
⚠ Missing optional field: kpi_targets
✓ Ready for deck generation

NEXT STEPS:
1. Run: python rearrange.py "assets/00 CD Deck Template.pptx" output.pptx "0,29,7,15,8,41..."
2. Run: python replace.py output.pptx replacement.json final-proposal.pptx
```

---

## 9. QUALITY BENCHMARKS

### 9.1 Visual Quality Standard
**Reference deck**: `sample-proposals/[EXT] 202503 NUS AIDF x CD - Exec Master Programme Campaign Plan - 26 Mar.pdf`

All outputs must match or exceed:
- Visual hierarchy clarity
- Text-to-visual ratio (max 30% text coverage per slide)
- Color consistency with brand palette
- Diagram clarity and flow logic

### 9.2 Rejection Criteria

**Reject and flag for manual intervention if**:
- Any slide has >100 words of body text
- Funnel diagram has >4 stages
- Persona cards have >3 personas
- Media plan table has >15 rows without split
- Timeline exceeds 12 months without grouping
- Any pattern matching fails with <80% confidence

---

## 10. SYSTEM CONSTRAINTS

### 10.1 Template Compatibility
This skill is **LOCKED** to:
- Template: `assets/00 CD Deck Template.pptx`
- Template version: 2022 v1.0
- Slide count: 66 slides

**Do NOT** attempt to use with other templates.

### 10.2 Script Dependencies
This skill outputs data for:
- `scripts/rearrange.py` (slide sequencing)
- `scripts/replace.py` (content population)
- `scripts/inventory.py` (validation)

Ensure scripts are executable before invoking skill.

### 10.3 Non-Generative Nature
This is **NOT** a creative AI system. It is a **deterministic mapping engine**.

**It WILL**:
- Map strategy data to visual patterns
- Compress text to fit layouts
- Enforce brand consistency

**It WILL NOT**:
- Generate new content ideas
- Create custom visuals
- Write persuasive copy
- Recommend strategy changes

---

## APPENDIX A: Pattern-to-Layout Quick Reference

| Visual Pattern              | Layout Index | Slide Reference (NUS AIDF) |
|-----------------------------|--------------|----------------------------|
| FUNNEL DIAGRAM              | 28           | Page 7                     |
| CAMPAIGN FLOW DIAGRAM       | 29           | Page 8                     |
| PERSONA CARDS               | 41, 42       | Page 4                     |
| CHANNEL RATIONALE GRID      | 27           | Page 5                     |
| MEDIA PLAN TABLE            | 47           | Page 14                    |
| TIMELINE GANTT              | 43           | Page 19                    |
| INVESTMENT SUMMARY TABLE    | 47           | Page 20                    |
| TWO-COLUMN COMPARISON       | 14           | Page 10                    |
| SECTION DIVIDER             | 6-10         | Page 3                     |

---

## APPENDIX B: Compression Examples

**Before**:
"We recommend implementing a comprehensive multichannel digital marketing strategy that leverages both paid social media platforms such as Facebook, Instagram, and LinkedIn, as well as search engine marketing through Google Ads."

**After** (using CHANNEL RATIONALE GRID pattern):
```
Multichannel Strategy
• Paid Social: FB/IG/LI
• Search: Google Ads
```

**Character reduction**: 231 → 52 (77% reduction)

---

END OF SKILL SPECIFICATION
