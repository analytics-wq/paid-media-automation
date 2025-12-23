# PAID MEDIA PROPOSAL GENERATION SKILL

**Skill Purpose**: Transform paid media strategy outputs into production-grade Construct Digital proposal presentations through deterministic content-to-slide mapping, visual abstraction enforcement, and automated deck assembly.

**Scope**: Paid media campaign proposals, media plans, investment summaries, and campaign architecture documentation.

**System Type**: Deterministic intelligence layer (not a creative generation system).

---

## CORE ARCHITECTURE

### System Flow
```
Strategy Input → Content Classification → Visual Pattern Assignment → Layout Mapping →
Content Compression → Replacement JSON → Slide Sequencing → Validation
```

### Processing Layers

**Layer 1: Input Interpretation**
- Parse strategy document structure
- Validate mandatory fields
- Extract content types
- Flag missing data

**Layer 2: Visual Abstraction**
- Map content to approved visual patterns
- Reject text-dump candidates
- Enforce pattern constraints
- Assign layout indices

**Layer 3: Content Transformation**
- Compress text to fit shape boundaries
- Apply brand formatting rules
- Generate replacement JSON
- Validate overflow

**Layer 4: Assembly**
- Generate slide sequence
- Apply template constraints
- Output automation files

---

## INPUT SCHEMA

### Mandatory Strategy Components

The skill requires these inputs from the paid media strategy:

```json
{
  "campaign_overview": {
    "client_name": "string (required)",
    "campaign_objective": "string (required)",
    "campaign_mode": "Budget-Driven | KPI-Driven (required)",
    "markets": "array (required)",
    "campaign_duration": "string (required)"
  },

  "audience_segmentation": {
    "segments": [
      {
        "segment_name": "string (required)",
        "demographics": "object (required)",
        "professional_context": "string (required)",
        "motivations": "array (required)",
        "pain_points": "array (required)",
        "decision_barriers": "array (required)",
        "intent_behaviors": "array (required)",
        "messaging_triggers": "array (required)"
      }
    ]
  },

  "channel_mix": [
    {
      "channel_name": "string (required)",
      "strategic_role": "string (required)",
      "audience_fit": "string (required)"
    }
  ],

  "conversion_funnel": {
    "prospecting": {
      "objective": "string (required)",
      "mindset_shift": "string (required)",
      "cta": "string (required, single CTA only)",
      "kpi_type": "string (required)",
      "campaign_type": "Prospecting"
    },
    "retargeting": {
      "objective": "string (required)",
      "mindset_shift": "string (required)",
      "cta": "string (required, single CTA only)",
      "kpi_type": "string (required)",
      "campaign_type": "Retargeting"
    },
    "nurturing": {
      "objective": "string (required)",
      "mindset_shift": "string (required)",
      "cta": "string (required, single CTA only)",
      "kpi_type": "string (required)",
      "campaign_type": "Nurturing"
    }
  },

  "messaging_structure": {
    "umbrella_message": "string (required)",
    "prospecting_messages": {
      "segment_1": ["string", "string"],
      "segment_n": ["string", "string"]
    },
    "retargeting_message": "string (required)",
    "nurturing_message": "string (required)"
  },

  "campaign_flow": {
    "tactics_list": {
      "prospecting": ["string"],
      "retargeting": ["string"],
      "nurturing": ["string"]
    },
    "real_flow": "string (hierarchical bullet structure)"
  },

  "media_plan": {
    "headers": ["Funnel", "Tactic", "Budget", "Budget %", "Impressions", "CTR", "Clicks", "CPC", "Leads", "Acquisitions", "CPA", "CPL"],
    "rows": [
      {
        "funnel": "Prospecting | Retargeting | Nurturing",
        "tactic": "string (with ' Ad' suffix if not email)",
        "budget": "number",
        "budget_pct": "number",
        "impressions": "number",
        "ctr": "number",
        "clicks": "number",
        "cpc": "number",
        "leads": "number",
        "acquisitions": "number",
        "cpa": "number",
        "cpl": "number"
      }
    ],
    "total_row": {
      "budget": "number",
      "impressions": "number",
      "clicks": "number",
      "weighted_ctr": "number",
      "weighted_cpc": "number",
      "leads": "number",
      "acquisitions": "number",
      "overall_cpa": "number",
      "overall_cpl": "number"
    }
  },

  "budget_breakdown": {
    "content_production": "number",
    "professional_fees": "number",
    "media_investment": "number",
    "total": "number",
    "line_items": [
      {
        "item": "string",
        "description": "string",
        "investment": "number"
      }
    ]
  },

  "timeline": {
    "milestones": [
      {
        "phase": "string",
        "activities": ["string"],
        "duration": "string"
      }
    ]
  }
}
```

### Optional Inputs

```json
{
  "landing_page_specs": "object",
  "ads_production_specs": "object",
  "reporting_dashboard_specs": "object",
  "kpi_targets": "object",
  "competitor_analysis": "object"
}
```

### Inference Prohibition

**NEVER INFER**:
- Budget allocations not explicitly provided
- Persona demographics beyond what's stated
- Channel rationale not in the strategy
- Timeline dates not in the input
- KPI targets not specified
- CTAs different from the conversion funnel

**IF DATA IS MISSING**:
```json
{
  "missing_field": "[CLIENT INPUT REQUIRED]",
  "validation_flag": true
}
```

---

## VISUAL ABSTRACTION CATALOG

### Pattern Classification Logic

```
INPUT: Strategy content block
↓
CLASSIFY content type:
  - Campaign brief summary → BRIEF SUMMARY TABLE
  - Audience segments → PERSONA CARDS
  - Channel justification → CHANNEL RATIONALE GRID
  - Funnel stages → FUNNEL DIAGRAM
  - Tactic-to-stage mapping → CAMPAIGN FLOW DIAGRAM
  - Media plan table → MEDIA PLAN TABLE
  - Timeline/phases → TIMELINE GANTT
  - Budget breakdown → INVESTMENT BREAKDOWN TABLE
  - Messaging hierarchy → MESSAGING PYRAMID
  - Ad format examples → TWO-COLUMN SHOWCASE
↓
ASSIGN visual pattern
↓
MAP to layout index
↓
COMPRESS content to fit
↓
OUTPUT replacement JSON
```

---

### PATTERN 1: BRIEF SUMMARY TABLE

**Use when**: Presenting campaign overview, markets, budget, duration

**Visual structure**:
```
| Parameter | Details |
|-----------|---------|
| Market    | Primary: [list], Secondary: [list] |
| Budget    | [amount] |
| Channels  | [summary] |
| Duration  | [timeframe] |
| Assets    | [summary] |
```

**Layout mapping**: Slide 15 (Content Bullets) adapted as table

**Content limits**:
- Max 6 rows
- Details column: 100 characters max
- No paragraphs

**Compression rules**:
- "Primary: Hongkong, PRC (China) diaspora, Indonesia, Malaysia, Singapore"
- "~$99,000"
- "Social media channels + others proposed by CD"

**Reference**: NUS AIDF page 3

---

### PATTERN 2: PERSONA CARDS

**Use when**: Presenting 1-3 audience segments

**Visual structure** (per card):
```
[Image placeholder]

Persona Title (max 4 words)
Role descriptor (max 6 words)

About
[2 sentences, 30 words total]

Goals
• [8 words max]
• [8 words max]
• [8 words max]

Expectations from Programme
• [10 words max]
• [10 words max]
• [10 words max]
• [10 words max]

Demographics
• Age: [range]
• Locations: [list]
• Industries: [list]
• Seniority: [level]
```

**Layout mapping**:
- 1 persona: Slide 41 (Persona)
- 2 personas: Slide 14 (Two Column) with persona structure
- 3 personas: Slide 41 + Slide 42

**Content extraction from strategy**:
- Persona Title ← segment_name
- About ← professional_context (compressed)
- Goals ← motivations (top 3, compressed)
- Expectations ← messaging_triggers (top 4, compressed)
- Demographics ← demographics object

**Compression technique**:
```
BEFORE (from strategy):
"A mid-career technology professional responsible for driving AI adoption and digital transformation initiatives within their organization. They are working closely with senior executives, translating technical advancements into business value. Their goal is to get themselves ready for a future innovation role and lead the organization's AI transformation journey."

AFTER (for slide):
"Mid-career technology professional responsible for driving AI adoption and digital transformation initiatives. Working with senior executives to translate technical advancements into business value."
```

**Messaging alignment**:
- Use prospecting messages from messaging_structure
- Extract headline from first prospecting message
- Use as card subtitle or callout

**Reference**: NUS AIDF page 4

---

### PATTERN 3: CHANNEL RATIONALE GRID

**Use when**: Justifying channel selection and mix strategy

**Visual structure**:
```
[LEFT COLUMN]
[Channel logos stacked vertically]
• Google Ads logo + icon
• LinkedIn logo
• Facebook logo
• Instagram logo
• Email icon

[RIGHT COLUMN]
Why multichannel strategy?
• [3-word benefit]
• [3-word benefit]
• [3-word benefit]
• [3-word benefit]

What channels?
• Channel Name: [12-word rationale max]
• Channel Name: [12-word rationale max]
• Channel Name: [12-word rationale max]
...
```

**Layout mapping**: Slide 27 (Channels)

**Content extraction**:
- Channel list ← channel_mix array
- Rationale per channel ← strategic_role + audience_fit (compressed to 12 words)

**Multichannel benefits** (generic, always include):
- Reduce Risk
- Reduce Budget
- Audience Diversity
- Data-Driven

**Compression example**:
```
BEFORE (from strategy):
"Google Search: Targets high-intent professionals actively seeking education in AI and digital transformation"

AFTER (for slide):
"Targets high-intent professionals actively seeking AI education"
```

**Reference**: NUS AIDF page 5

---

### PATTERN 4: FUNNEL DIAGRAM

**Use when**: Explaining conversion journey architecture

**Visual structure**:
```
[AWARENESS - Blue trapezoid]
Stage objective (1 line)
CTA: [Action]
Tactics: [Type of campaigns]

[CONSIDERATION - Green trapezoid]
Stage objective (1 line)
CTA: [Action]
Tactics: [Type of campaigns]

[DECISION - Purple trapezoid]
Stage objective (1 line)
CTA: [Action]
Tactics: [Type of campaigns]
```

**Layout mapping**: Slide 28 (Funnel)

**Content extraction**:
- Awareness ← conversion_funnel.prospecting
- Consideration ← conversion_funnel.retargeting
- Decision ← conversion_funnel.nurturing
- Stage objective ← objective field (compressed to 8 words)
- CTA ← cta field (exactly as stated)
- Tactics ← campaign_type descriptor

**Shape mapping**:
```
shape-0: Title "Recommended Funnel Approach"
shape-1: Intro text (optional)
shape-2: Awareness label
shape-3: Awareness content
shape-4: Consideration label
shape-5: Consideration content
shape-6: Decision label
shape-7: Decision content
```

**CTA consistency rule**:
**The CTA in this diagram MUST match exactly with**:
- Conversion Funnel Architecture (strategy)
- Campaign Flow Real Flow (strategy)
- Landing Page actions (if specified)
- Ads Production CTAs (if generated)

**Reference**: NUS AIDF page 7

---

### PATTERN 5: CAMPAIGN FLOW DIAGRAM

**Use when**: Mapping tactics to funnel stages and showing user journey

**Visual structure**:
```
[AWARENESS Column - Blue]
Persona 1 | Persona 2

[Tactic Box]
[Tactic Box]
[Tactic Box]

↓

[CONSIDERATION Column - Green]
[Action Diamond: Drop-off]
[Action Diamond: Download Brochure]

[Tactic Box]
[Tactic Box]
[Tactic Box]

↓

[DECISION Column - Purple]
[Action Diamond: Apply Now]

[Tactic Box]
[Tactic Box]
[Tactic Box]
```

**Layout mapping**: Slide 29 (Campaign Flow)

**Content extraction**:
- Tactic boxes ← campaign_flow.tactics_list (Prospecting, Retargeting, Nurturing)
- Action diamonds ← conversion_funnel CTAs
- Flow arrows ← campaign_flow.real_flow logic

**Tactic box format**:
```
Channel: Tactic Name
(max 4 words total)

Example:
Google Performance Max Ads → Google Performance Max
Paid Social (FB/IG/LI) Traffic Video Ads → Paid Social Traffic Video
```

**Action diamond format**:
```
[Drop-off]
[CTA Text]
[Admission Team] (if nurturing stage)
```

**Compression rules**:
- Remove "Ad" suffix from tactic names in this view
- Use abbreviations: FB/IG/LI, eDM
- Max 4 tactic boxes per stage

**Reference**: NUS AIDF page 8

---

### PATTERN 6: MEDIA PLAN TABLE

**Use when**: Presenting budget allocation and performance projections

**Visual structure**:
```
| Funnel | Tactic | Budget | Budget % | Impressions | CTR | Clicks | CPC | Leads | Acquisitions | CPA | CPL |
|--------|--------|--------|----------|-------------|-----|--------|-----|-------|--------------|-----|-----|
| Prospecting | FB/IG Traffic Ads | $7,500 | 15% | 524,476 | 1.10% | 5,769 | $1.30 | 115 | 3 | $2,167 | ... |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |
| **TOTAL** | - | **$50,000** | **100%** | **2,557,795** | **1.30%** | **33,308** | **$1.50** | **649** | **22** | **$2,252** | ... |
```

**Layout mapping**: Slide 47 (Budget Table)

**Content extraction**:
- Direct pass-through from media_plan object
- Preserve exact column order
- Preserve total row formatting

**Formatting rules**:
- Currency: Include currency symbol from brief (SGD, USD, etc.)
- Thousands separator: Comma
- Percentages: 1-2 decimal places
- CTR: 2 decimal places
- CPC/CPA/CPL: 2 decimal places
- Total row: Bold, blue background

**Shape boundary safety**:
- If > 12 rows: Split into two tables
  - Table 1: Prospecting + Retargeting
  - Table 2: Nurturing + Total
- Max column width: Auto-adjust in template
- Font size: 10pt for body, 11pt for headers

**Reference**: NUS AIDF page 14

---

### PATTERN 7: BUDGET ALLOCATION BY COUNTRY

**Use when**: Multi-market campaigns with country-specific allocation

**Visual structure**:
```
| Country | Budget Allocation % |
|---------|---------------------|
| Singapore | 20% |
| Hong Kong | 15% |
| Indonesia | 11% |
| Malaysia | 11% |
| Taiwan | 15% |
| ... | ... |
```

**Layout mapping**: Slide 47 (Budget Table)

**Content extraction**:
- If budget_breakdown includes country_allocation, use it
- Otherwise, skip this slide

**Formatting**:
- Sort by allocation % (descending)
- Include note about platform grouping logic

**Reference**: NUS AIDF page 15

---

### PATTERN 8: TIMELINE GANTT

**Use when**: Showing campaign phases, milestones, or project plan

**Visual structure**:
```
[Month headers: Mar | Apr | May | Jun | Jul | Aug | Sep]

Campaign Plan
  [Bar from Mar to Mar]

Campaign Preparation
  [Bar from Apr to Apr]

Campaign Management
  [Bar from May to Aug]

Reporting
  [Bar from Sep to Sep]

[Milestone marker: Application deadline]
```

**Layout mapping**: Slide 43 (Timeline)

**Content extraction**:
- Phase names ← timeline.milestones.phase
- Activities ← timeline.milestones.activities (as sub-bullets)
- Duration bars ← timeline.milestones.duration

**Color coding**:
- Campaign Plan: Pink
- Campaign Preparation: Purple
- Campaign Management: Green
- Reporting: Blue

**Max phases**: 6
**Max duration**: 12 months (if longer, use quarterly grouping)

**Reference**: NUS AIDF page 19

---

### PATTERN 9: INVESTMENT BREAKDOWN TABLE

**Use when**: Presenting quotation or cost breakdown

**Visual structure**:
```
| Item | Description | Investment | After Discount |
|------|-------------|------------|----------------|
| Content to be produced | 2x short videos...<br>1x ad copy...<br>1x landing page | $27,055 | $26,919.73 |
| Professional fees | Campaign Plan (one-time)<br>Campaign Setups (one-time)<br>Campaigns Management (4.5x months)<br>Reporting (4.5x months) | $22,820 | $22,705.90 |
| Media investment | Media Buy Budget (3rd party cost) | $50,000 | $49,750.00 |
| **TOTAL** | - | **$99,875** | **$99,375.63** |
```

**Layout mapping**: Slide 47 (Budget Table)

**Content extraction**:
- Line items ← budget_breakdown.line_items
- Subtotals by category
- Grand total

**Formatting**:
- Section headers: Blue background
- Line items: White background
- Total row: Blue background, bold
- Use `<br>` for multi-line descriptions
- Description column: Max 60 characters per line

**Reference**: NUS AIDF page 20

---

### PATTERN 10: PAYMENT MILESTONES TABLE

**Use when**: Showing payment schedule by month

**Visual structure**:
```
| Item | Description | Mar | Apr | May | Jun | Jul | Aug | Sep | Total |
|------|-------------|-----|-----|-----|-----|-----|-----|-----|-------|
| Content | ... | $26,919.73 | - | - | - | - | - | - | $26,919.73 |
| Professional fees | Campaign Plan | $4,895.40 | - | - | - | - | - | - | $4,895.40 |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |
| **TOTAL (SGD)** | - | **$31,815.13** | **$8,736.10** | **$7,353.05** | **$14,706.10** | **$14,706.10** | **$14,706.10** | **$7,353.05** | **$99,375.63** |
```

**Layout mapping**: Slide 47 (Budget Table)

**Content extraction**:
- Distribute line items across timeline
- Match timeline.milestones to payment phases

**Reference**: NUS AIDF page 23

---

### PATTERN 11: LANDING PAGE MOCKUP

**Use when**: Showing landing page design or UX flow

**Visual structure**:
```
[Title: Landing Page]

Key Features:
• High-Performing Landing Page: Clear lead form & compelling messaging
• Dual CTAs: [CTA1] & [CTA2]
• Aligned Messaging: Uses topline message for both personas
• Easy Implementation: HTML file provided

[Screenshot/mockup placeholder]
[Link to demo if available]
```

**Layout mapping**: Slide 16-22 (Image slides)

**Content extraction**:
- CTAs ← conversion_funnel CTAs (must match exactly)
- Messaging ← messaging_structure.umbrella_message

**Reference**: NUS AIDF page 9

---

### PATTERN 12: AD FORMAT SHOWCASE

**Use when**: Explaining ad formats (e.g., Lead Gen Ads, Conversation Ads)

**Visual structure**:
```
[LEFT COLUMN]
Format Name

Description (2-3 sentences explaining the format)

Key Benefits:
• [Benefit 1]
• [Benefit 2]
• [Benefit 3]

[RIGHT COLUMN]
[Visual mockup or screenshot]
[Callout highlighting key feature]
```

**Layout mapping**: Slide 14 (Two Column)

**Content extraction**:
- If ads_production_specs provided, extract format types
- Generic descriptions for standard formats

**Reference**: NUS AIDF pages 11-12

---

### PATTERN 13: SECTION DIVIDER

**Use when**: Separating major proposal sections

**Visual structure**:
```
[Full-bleed colored background]

Section Title (max 3 words, 36pt, bold, white/black)
Section Subtitle (max 8 words, 24pt, white/black)

[Construct Digital logo]
[Brand iconography]
```

**Layout mapping**: Slides 6-10

**Color rotation by section**:
1. Brief Recap → Blue (Slide 7)
2. Our Media Approach → Red (Slide 9)
3. Investments & Timeline → Purple (Slide 10)

**Text color rule**:
- Blue/Red/Green/Purple background → White text
- Yellow background → Black text

**Content limits**:
- Title: 20 characters max
- Subtitle: 50 characters max

**Reference**: NUS AIDF page 2 (Agenda structure)

---

### PATTERN 14: MESSAGING PYRAMID

**Use when**: Presenting messaging hierarchy

**Visual structure**:
```
[Top - Umbrella Message]
"[Campaign-wide human truth]"

[Middle - Segment Messages]
Persona 1:
• "[Aspirational message 1]"
• "[Aspirational message 2]"

Persona 2:
• "[Aspirational message 1]"
• "[Aspirational message 2]"

[Bottom - Stage-Specific Messages]
Retargeting: "[Programme-specific hook]"
Nurturing: "[Urgent action message]"
```

**Layout mapping**: Slide 15 (Content Bullets)

**Content extraction**:
- Umbrella ← messaging_structure.umbrella_message
- Prospecting ← messaging_structure.prospecting_messages
- Retargeting ← messaging_structure.retargeting_message
- Nurturing ← messaging_structure.nurturing_message

**Formatting**:
- Umbrella message: 24pt, bold, centered
- Segment messages: 18pt, bulleted
- Stage messages: 18pt, italic

---

### PATTERN 15: REPORTING DASHBOARD PREVIEW

**Use when**: Showing automated reporting capabilities

**Visual structure**:
```
[Title: Report & Dashboard Samples]

[LEFT: Screenshot of Google Sheet report]

Automated GSheet Report
• Real-time data (24-hour updates)
• Overview Metrics: Progress against milestones
• In-Depth Metrics: Granular performance visualization
• Dynamic Filters: Timeline analysis
• Detailed Breakdown: By country, programme, channel

[RIGHT: Screenshot of Looker Studio dashboard]

Looker Studio Dashboard
• Monthly dashboard with insights
• Data highlights
• Comprehensive analysis
• Recommendations

[Links to interactive samples]
```

**Layout mapping**: Slide 14 (Two Column) with image placeholders

**Reference**: NUS AIDF pages 17-18

---

## SLIDE MAPPING RULES

### Mandatory Slide Sequence for Paid Media Proposals

```
Position  Layout  Content                              Visual Pattern                    Source Data
--------  ------  -----------------------------------  --------------------------------  ---------------------
1         0       Cover Slide                          Title slide (blue)                campaign_overview
2         29      Agenda                               Section blocks                    [Generated]
3         7       Section: Brief Recap                 Section divider (blue)            [Fixed]
4         15      Your Brief                           Brief summary table               campaign_overview
5         8       Section: Audiences                   Section divider (green)           [Fixed]
6         41/42   Target Personas                      Persona cards (1-3)               audience_segmentation
7         9       Section: Our Approach                Section divider (red)             [Fixed]
8         27      Channel Rationale                    Channel rationale grid            channel_mix
9         28      Conversion Funnel                    Funnel diagram                    conversion_funnel
10        29      Campaign Flow                        Campaign flow diagram             campaign_flow
11        [opt]   Landing Page                         Image + description               landing_page_specs
12        [opt]   Ad Formats                           Two-column showcase               ads_production_specs
13        10      Section: Media Plan                  Section divider (purple)          [Fixed]
14        47      Media Plan Table                     Media plan table                  media_plan
15        [opt]   Country Allocation                   Budget table                      budget_breakdown
16        43      Timeline                             Timeline Gantt                    timeline
17        6       Section: Investment                  Section divider (purple)          [Fixed]
18        47      Investment Summary                   Investment breakdown table        budget_breakdown
19        [opt]   Payment Milestones                   Payment schedule table            budget_breakdown + timeline
20        [opt]   Reporting Samples                    Two-column showcase               reporting_dashboard_specs
21        50      Closing                              Thank you slide (blue)            [Fixed]
```

### Slide Overflow Rules

**IF** audience segments > 2:
- Use Slide 41 for segments 1-2
- Use Slide 42 for segment 3
- If > 3 segments, compress to 3 or flag for manual review

**IF** media plan rows > 12:
- Split into two tables:
  - Table 1 (Slide 47): Prospecting + Retargeting
  - Table 2 (Slide 47 duplicate): Nurturing + Total row

**IF** timeline > 6 months:
- Use quarterly grouping
- If > 12 months, use semester grouping

**IF** investment line items > 15:
- Create Investment Summary (high-level)
- Create Detailed Breakdown (additional slide)

**IF** country allocation > 10 countries:
- Show top 8 countries individually
- Group remaining as "Other Markets"

### Optional Slide Inclusion Logic

```
Include Landing Page slide IF:
  landing_page_specs exists OR
  campaign_flow.real_flow mentions landing page

Include Ad Formats slide IF:
  ads_production_specs exists AND
  unique_ad_formats >= 2

Include Country Allocation slide IF:
  budget_breakdown.country_allocation exists AND
  markets.length >= 3

Include Payment Milestones slide IF:
  budget_breakdown.payment_schedule exists OR
  timeline.milestones includes payment phases

Include Reporting Samples slide IF:
  reporting_dashboard_specs exists OR
  brief mentions reporting requirements
```

### Slide Deletion Rules

**NEVER include**:
- Slides 33, 51-65 (style guide, reference slides)
- Slides 34-40 (team slides) unless explicitly requested
- Slide 49 (case study) unless past work requested
- Duplicate content slides

**ALWAYS include**:
- Cover (Slide 0)
- Agenda (Slide 29)
- At least 3 section dividers (Slides 7, 9, 10 minimum)
- Core strategy slides (Personas, Channels, Funnel, Flow)
- Media Plan (Slide 47)
- Investment Summary (Slide 47)
- Closing (Slide 50)

---

## CONTENT COMPRESSION RULES

### Text Limits by Element Type

| Element Type | Max Characters | Max Words | Max Bullets | Max Lines | Font Size |
|--------------|----------------|-----------|-------------|-----------|-----------|
| Slide title | 60 | 8 | - | 1 | 28pt |
| Section title | 40 | 4 | - | 1 | 36pt |
| Section subtitle | 80 | 12 | - | 1 | 24pt |
| Bullet point | 100 | 15 | - | 1 | 18pt |
| Bullet list per slide | - | - | 5 | - | - |
| Table cell (header) | 30 | 5 | - | 1 | 11pt bold |
| Table cell (body) | 50 | 8 | - | 1 | 10pt |
| Persona "About" | 200 | 30 | - | 2 | 14pt |
| Channel rationale | 80 | 12 | - | 1 | 16pt |
| Funnel stage objective | 60 | 8 | - | 1 | 16pt |
| CTA text | 40 | 5 | - | 1 | 16pt bold |
| Messaging line | 120 | 18 | - | 1 | 18pt |

### Compression Techniques

#### Technique 1: Eliminate Filler

**Remove**:
- "very", "really", "actually", "basically", "essentially"
- "moving forward", "as mentioned", "as we discussed"
- "we believe that", "it is our opinion", "we recommend"
- "in order to", "for the purpose of"

**Examples**:
```
BEFORE: "We believe that it is very important to implement a comprehensive multichannel strategy"
AFTER: "Implement multichannel strategy"

BEFORE: "Moving forward, we recommend focusing on high-intent professionals"
AFTER: "Focus on high-intent professionals"
```

#### Technique 2: Verb-First Transformation

**Pattern**: Convert passive descriptions to active directives

```
BEFORE: "The campaign will be running for 4 months"
AFTER: "4-month campaign"

BEFORE: "Target audience consists of mid-career professionals"
AFTER: "Mid-career professionals"

BEFORE: "We recommend a multichannel strategy"
AFTER: "Multichannel strategy"
```

#### Technique 3: Noun Stacking

**Pattern**: Stack related nouns without connectors

```
BEFORE: "Professionals who are in mid-career and working in technology"
AFTER: "Mid-career technology professionals"

BEFORE: "A campaign that focuses on digital transformation and AI"
AFTER: "AI & digital transformation campaign"
```

#### Technique 4: Approved Abbreviations

Use these abbreviations ONLY:

| Full Form | Abbreviation | Context |
|-----------|--------------|---------|
| Facebook/Instagram/LinkedIn | FB/IG/LI | Channel names only |
| Email Direct Marketing | eDM | Tactic names |
| Call to Action | CTA | Funnel, flow, messaging |
| Sales Qualified Lead | SQL | KPI descriptions |
| Marketing Qualified Lead | MQL | KPI descriptions |
| Cost Per Click | CPC | Media plan table |
| Cost Per Mille | CPM | Media plan table |
| Cost Per Acquisition | CPA | Media plan table |
| Click-Through Rate | CTR | Media plan table |
| Quarterly Business Review | QBR | Proposal types |
| Key Performance Indicator | KPI | General usage |
| Search Engine Marketing | SEM | Channel references |

**Do NOT abbreviate**:
- Client names
- Programme names
- Country names
- Persona titles
- Channel platforms (spell out "Google", "LinkedIn", "Meta")

#### Technique 5: Bullet-to-Table Conversion

**When**: Content has repeating structure across multiple items

```
BEFORE (bullets):
• Google Search: Targets high-intent professionals actively seeking education
• Performance Max: Expands reach beyond Search to engage professionals researching
• LinkedIn: Focuses on aspiring leaders looking to gain competitive edge

AFTER (table):
| Channel | Role |
|---------|------|
| Google Search | Targets high-intent education seekers |
| Performance Max | Expands reach to researching professionals |
| LinkedIn | Engages aspiring leaders seeking competitive edge |
```

### Shape Boundary Safety

#### Safety Margins

All text MUST respect these shape margins (from `layouts.md` + `brand-config.json`):

```
Top margin: 12pt
Bottom margin: 12pt
Left margin: 20pt (40pt for slide-level padding)
Right margin: 20pt (40pt for slide-level padding)
Line spacing: 1.2x font size (default)
Paragraph spacing: 10pt after
```

#### Overflow Detection Workflow

1. **Pre-generation estimate**:
   - Count total characters in content block
   - Calculate estimated lines: `total_chars / (chars_per_line)`
   - Calculate estimated height: `lines * (font_size * 1.2) + (lines * 10)`
   - Compare to shape height from `layouts.md`

2. **Post-generation validation**:
   - Run `inventory.py --issues-only` on generated deck
   - Parse overflow warnings
   - If any overflow detected → trigger compression

3. **Compression cascade**:
   - Level 1: Apply Techniques 1-4 (eliminate filler, transform, abbreviate)
   - Level 2: Reduce bullet count (keep top 3-4 most important)
   - Level 3: Convert bullets to table (if applicable)
   - Level 4: Split content across two slides (with continuation marker)
   - Level 5: Flag for manual review

#### Overflow Prevention Rules

**For bullet lists**:
- Max 5 bullets per slide
- If 6-8 bullets → split across two slides
- If > 8 bullets → compress to top 5 or convert to table

**For persona cards**:
- Max 3 goals
- Max 4 expectations
- Max 2 sentences for "About"
- Demographics as table (not bullets)

**For tables**:
- Max 12 rows per table (excluding header and total)
- If > 12 rows → split into multiple tables
- Font size reduction: 10pt body, 11pt headers (min allowed)

---

## BRAND & LAYOUT ENFORCEMENT

### Brand Configuration Source

**File**: `references/brand-config.json`

**Non-negotiable rules**:
1. All color values must come from this file
2. All font names must come from this file
3. All spacing values must come from this file
4. No deviations allowed

### Typography Rules

**Fonts**:
```json
{
  "heading": "Arial",
  "body": "Arial",
  "style": "Bold for headings, Regular for body"
}
```

**Application**:
- Slide titles: Arial Bold, 28pt
- Section titles: Arial Bold, 36pt
- Body text: Arial Regular, 16-18pt
- Table headers: Arial Bold, 11pt
- Table body: Arial Regular, 10pt
- Captions: Arial Regular, 12pt

### Color Palette

**Primary Colors** (from brand-config.json):
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

**Usage Rules**:

| Element | Background Color | Text Color |
|---------|------------------|------------|
| Section divider 1 (Brief) | #1E5AA8 (Blue) | #FFFFFF (White) |
| Section divider 2 (Approach) | #CC0000 (Red) | #FFFFFF (White) |
| Section divider 3 (Media Plan) | #901F76 (Purple) | #FFFFFF (White) |
| Section divider 4 (Investment) | #901F76 (Purple) | #FFFFFF (White) |
| Funnel - Awareness | #1E5AA8 (Blue) | #FFFFFF (White) |
| Funnel - Consideration | #00852B (Green) | #FFFFFF (White) |
| Funnel - Decision | #901F76 (Purple) | #FFFFFF (White) |
| Table header row | #1E5AA8 (Blue) | #FFFFFF (White) |
| Table total row | #1E5AA8 (Blue) | #FFFFFF (White) |
| Table body rows | #FFFFFF (White) | #000000 (Black) |
| Callout boxes | #F2F2F2 (Alt bg) | #000000 (Black) |

**Color Rotation for Section Dividers**:
```
Slide 7 (Blue) → Slide 9 (Red) → Slide 10 (Purple) → Slide 6 (Yellow)
```

If > 4 sections, rotate back to Blue.

### Layout Configuration Source

**File**: `references/layouts.md`

**Slide index mapping** (zero-based):
- 0: Title slide (blue)
- 6-10: Section dividers (blue, purple, red, green, purple)
- 14: Two-column layout
- 15: Content bullets
- 16-22: Image slides
- 27: Channels layout
- 28: Funnel layout
- 29: Campaign flow / Agenda layout
- 41-42: Persona layouts
- 43: Timeline layout
- 47: Budget/table layout
- 50: Closing slide (blue)

**Shape index mapping** (examples):

**Slide 0 (Title)**:
```
shape-0: Title (42pt, Arial Bold)
shape-1: Subtitle (24pt, Arial Regular)
shape-2: Author/Date (10pt, Arial Regular, muted color)
```

**Slide 7-10 (Section Dividers)**:
```
shape-0: Section title (36pt, Arial Bold, white)
shape-1: Section subtitle (24pt, Arial Regular, white)
```

**Slide 28 (Funnel)**:
```
shape-0: Slide title (28pt, Arial Bold)
shape-1: Intro text (optional)
shape-2: Awareness stage label
shape-3: Awareness stage content
shape-4: Consideration stage label
shape-5: Consideration stage content
shape-6: Decision stage label
shape-7: Decision stage content
```

**Slide 47 (Table)**:
```
shape-0: Table title (28pt, Arial Bold)
shape-1: Table element (PowerPoint table object)
```

### Forbidden Actions

**NEVER**:
- Create custom slide layouts
- Substitute fonts (even "similar" ones like Helvetica)
- Use colors outside brand-config.json
- Create free-form text boxes outside defined shapes
- Manually create shapes or connectors
- Use gradients, shadows, or effects not in template
- Change aspect ratio (locked to 16:9)
- Modify master slides
- Use images without placeholders

**ALWAYS**:
- Use exact shape indices from layouts.md
- Use exact color hex codes from brand-config.json
- Use Arial only
- Respect shape boundaries
- Validate with inventory.py before finalizing

---

## OUTPUT CONTRACT

### Primary Output: Replacement JSON

**Schema version**: 1.0
**Target scripts**: `replace.py`

**Structure**:
```json
{
  "slide-0": {
    "shape-0": {
      "paragraphs": [
        {
          "text": "NUS AIDF Executive Master in AI and Digital Transformation",
          "font_name": "Arial",
          "font_size": 42,
          "bold": true,
          "color": "#FFFFFF",
          "alignment": "LEFT"
        }
      ]
    },
    "shape-1": {
      "paragraphs": [
        {
          "text": "Campaign Plan",
          "font_name": "Arial",
          "font_size": 24,
          "bold": false,
          "color": "#FFFFFF",
          "alignment": "LEFT"
        }
      ]
    },
    "shape-2": {
      "paragraphs": [
        {
          "text": "MAR 2025",
          "font_name": "Arial",
          "font_size": 10,
          "bold": false,
          "color": "#FFFFFF",
          "alignment": "LEFT"
        }
      ]
    }
  },

  "slide-7": {
    "shape-0": {
      "paragraphs": [
        {
          "text": "Brief Recap",
          "font_size": 36,
          "bold": true,
          "color": "#FFFFFF"
        }
      ]
    },
    "shape-1": {
      "paragraphs": [
        {
          "text": "",
          "font_size": 24
        }
      ]
    }
  },

  "slide-15": {
    "shape-0": {
      "paragraphs": [
        {
          "text": "Your Brief",
          "font_size": 28,
          "bold": true
        }
      ]
    },
    "shape-1": {
      "paragraphs": [
        {
          "text": "The Asian Institute of Digital Finance invite us to quote for a Digital Marketing Campaign to promote a new Executive Master degree programme created in collaboration with NUS Computing.",
          "font_size": 18
        }
      ]
    }
  },

  "slide-28": {
    "shape-0": {
      "paragraphs": [
        {
          "text": "Conversion Funnel",
          "font_size": 28,
          "bold": true
        }
      ]
    },
    "shape-2": {
      "paragraphs": [
        {
          "text": "AWARENESS",
          "font_size": 20,
          "bold": true,
          "color": "#FFFFFF"
        }
      ]
    },
    "shape-3": {
      "paragraphs": [
        {
          "text": "Stage 1: Traffic",
          "font_size": 16,
          "bold": true,
          "color": "#000000"
        },
        {
          "text": "Learn More",
          "font_size": 16,
          "bold": false,
          "color": "#000000"
        },
        {
          "text": "Tactics: Prospecting campaigns",
          "font_size": 14,
          "italic": true,
          "color": "#434343"
        }
      ]
    }
  }
}
```

### Paragraph Property Reference

**Required field**:
- `text` (string)

**Optional fields** (with defaults):
```json
{
  "font_name": "Arial",           // Default: Arial
  "font_size": 16,                // Default: inherited from layout
  "bold": false,                  // Default: false
  "italic": false,                // Default: false
  "underline": false,             // Default: false
  "color": "#000000",             // Default: black (use hex from brand-config.json)
  "bullet": false,                // Default: false
  "level": 0,                     // Default: 0 (for bullets: 0, 1, 2)
  "alignment": "LEFT",            // Options: LEFT, CENTER, RIGHT, JUSTIFY
  "space_before": 0,              // In points
  "space_after": 10,              // In points (default paragraph spacing)
  "line_spacing": 1.2             // Multiplier of font_size
}
```

**Bullet formatting example**:
```json
{
  "text": "Reduce Risk",
  "font_size": 18,
  "bullet": true,
  "level": 0,
  "alignment": "LEFT"
}
```

**Sub-bullet example**:
```json
{
  "text": "Diversify channel exposure",
  "font_size": 16,
  "bullet": true,
  "level": 1,
  "alignment": "LEFT"
}
```

### Secondary Output: Slide Sequence Array

**Schema version**: 1.0
**Target scripts**: `rearrange.py`

**Structure**:
```json
{
  "slide_sequence": [0, 29, 7, 15, 8, 41, 9, 27, 28, 29, 16, 14, 47, 43, 10, 47, 50],
  "sequence_string": "0,29,7,15,8,41,9,27,28,29,16,14,47,43,10,47,50",
  "metadata": {
    "total_slides": 17,
    "template_version": "2022 v1.0",
    "template_file": "assets/00 CD Deck Template.pptx",
    "sections": [
      {
        "name": "Brief Recap",
        "start_index": 3,
        "slide_count": 2
      },
      {
        "name": "Audiences & Messaging",
        "start_index": 5,
        "slide_count": 2
      },
      {
        "name": "Our Approach",
        "start_index": 7,
        "slide_count": 6
      },
      {
        "name": "Media Plan & Timeline",
        "start_index": 13,
        "slide_count": 3
      },
      {
        "name": "Investment",
        "start_index": 16,
        "slide_count": 2
      }
    ],
    "estimated_duration": "20 minutes",
    "slide_notes": {
      "11": "Landing page mockup - insert actual screenshot",
      "12": "Ad format showcase - insert platform screenshots"
    }
  }
}
```

### Tertiary Output: Validation Report

**Human-readable summary**:

```
========================================
PAID MEDIA PROPOSAL GENERATION REPORT
========================================

INPUT VALIDATION
✓ All mandatory fields present
✓ Campaign mode: Budget-Driven
✓ Personas: 2 segments detected
✓ Funnel: 3 stages with CTAs defined
✓ Media plan: 10 tactics, $50,000 budget
⚠ Missing optional field: landing_page_specs
⚠ Missing optional field: ads_production_specs

VISUAL PATTERN ASSIGNMENT
✓ Brief Summary Table → Slide 15
✓ Persona Cards (2) → Slide 41
✓ Channel Rationale Grid → Slide 27
✓ Funnel Diagram → Slide 28
✓ Campaign Flow Diagram → Slide 29
✓ Media Plan Table → Slide 47
✓ Timeline Gantt → Slide 43
✓ Investment Breakdown → Slide 47

CONTENT COMPRESSION
✓ All text within shape boundaries
✓ Persona "About" compressed: 85 words → 28 words
✓ Channel rationale compressed: 18 words max per channel
✓ Funnel objectives compressed: 8 words max per stage
✓ No overflow warnings detected

BRAND COMPLIANCE
✓ Fonts: Arial only
✓ Colors: All from brand-config.json
✓ Layouts: All from approved template
✓ No custom shapes created

OUTPUT GENERATION
✓ Replacement JSON: 17 slides, 127 shape replacements
✓ Slide sequence: 0,29,7,15,8,41,9,27,28,29,14,47,43,10,47,50
✓ Total slides: 16 (excluding duplicate layouts)

FINAL STATUS
✓ Ready for deck generation

NEXT STEPS
1. Run: python rearrange.py "assets/00 CD Deck Template.pptx" temp.pptx "0,29,7,15,8,41,9,27,28,29,14,47,43,10,47,50"
2. Run: python replace.py temp.pptx replacement.json final-proposal.pptx
3. Run: python inventory.py final-proposal.pptx --issues-only (validation)
4. If no issues: Deliver final-proposal.pptx
5. If issues detected: Review overflow warnings and re-compress

WARNINGS & RECOMMENDATIONS
• Landing page slide skipped (no specs provided)
• Ad format showcase slide skipped (no specs provided)
• Consider adding reporting dashboard preview (Slide 14)
• Estimated presentation time: 20 minutes
• Recommended delivery format: PDF + editable PPTX

========================================
```

### Quaternary Output: Metadata JSON

**For automation pipelines**:

```json
{
  "generation_timestamp": "2025-01-XX 14:32:15 UTC",
  "skill_version": "1.0",
  "template_version": "2022 v1.0",
  "input_source": "paid-media-strategist-construct output",
  "client_name": "NUS AIDF",
  "campaign_name": "Executive Master in AI and Digital Transformation",
  "campaign_mode": "Budget-Driven",
  "total_budget": 50000,
  "currency": "SGD",
  "slide_count": 16,
  "sections": 5,
  "personas": 2,
  "tactics": 10,
  "validation_status": "PASS",
  "overflow_warnings": 0,
  "missing_optional_inputs": ["landing_page_specs", "ads_production_specs"],
  "visual_patterns_used": [
    "BRIEF_SUMMARY_TABLE",
    "PERSONA_CARDS",
    "CHANNEL_RATIONALE_GRID",
    "FUNNEL_DIAGRAM",
    "CAMPAIGN_FLOW_DIAGRAM",
    "MEDIA_PLAN_TABLE",
    "TIMELINE_GANTT",
    "INVESTMENT_BREAKDOWN"
  ],
  "compression_stats": {
    "total_chars_before": 12450,
    "total_chars_after": 4820,
    "compression_ratio": 0.61
  },
  "files_generated": [
    "replacement.json",
    "slide-sequence.json",
    "validation-report.txt",
    "metadata.json"
  ]
}
```

---

## INVOCATION INTERFACE

### How to Invoke This Skill

**Method 1: From Claude Chat**

```
User: "I have a paid media strategy ready. Generate the proposal deck."

[Paste strategy output from paid-media-strategist-construct skill]

Claude: [Activates PAID_MEDIA_PROPOSAL_SKILL]
        [Validates inputs]
        [Assigns visual patterns]
        [Generates replacement JSON + slide sequence]
        [Returns validation report]
```

**Method 2: From Claude Projects**

Add this skill to project knowledge. System prompt:
```
"When user requests proposal deck generation, invoke PAID_MEDIA_PROPOSAL_SKILL with the latest strategy output."
```

**Method 3: Direct File Input**

```
User: "Generate proposal deck from this strategy file: strategy.json"

Claude: [Reads strategy.json]
        [Validates schema]
        [Executes skill workflow]
        [Outputs automation files]
```

### Execution Workflow

**Step 1: Input Validation** (30 seconds)
- Load strategy JSON or structured output
- Validate against mandatory schema (Section 2)
- Flag missing fields
- Confirm campaign mode (Budget-Driven vs KPI-Driven)

**Step 2: Content Classification** (60 seconds)
- Parse strategy sections
- Identify content types
- Map to visual patterns (Section 3)
- Calculate slide count

**Step 3: Visual Pattern Assignment** (90 seconds)
- For each content block:
  - Select pattern from catalog
  - Assign layout index
  - Calculate shape requirements
  - Estimate content overflow

**Step 4: Content Compression** (120 seconds)
- Apply compression techniques (Section 5)
- Fit text to shape boundaries
- Validate character limits
- Handle overflow (split or flag)

**Step 5: JSON Generation** (60 seconds)
- Build replacement JSON structure
- Populate paragraph objects
- Apply brand formatting
- Validate JSON schema

**Step 6: Slide Sequencing** (30 seconds)
- Generate slide sequence array
- Apply ordering rules (Section 4)
- Handle optional slides
- Output sequence string

**Step 7: Validation** (60 seconds)
- Run overflow detection logic
- Check brand compliance
- Verify CTA consistency
- Generate validation report

**Step 8: Output Delivery** (30 seconds)
- Write replacement.json
- Write slide-sequence.json
- Write validation-report.txt
- Write metadata.json

**Total execution time**: ~8 minutes

### Expected Outputs

**In Claude Chat**:
1. Validation summary (inline)
2. Slide sequence (inline, copyable)
3. JSON downloads (via file export)
4. Next-step instructions (inline)

**In File System** (if integrated):
1. `output/replacement.json`
2. `output/slide-sequence.json`
3. `output/validation-report.txt`
4. `output/metadata.json`

**Instructions for User**:
```
NEXT STEPS TO GENERATE DECK:

1. Copy the slide sequence below:
   0,29,7,15,8,41,9,27,28,29,14,47,43,10,47,50

2. Run rearrange.py:
   python rearrange.py "assets/00 CD Deck Template.pptx" temp.pptx "0,29,7,15,8,41,9,27,28,29,14,47,43,10,47,50"

3. Save the replacement JSON to a file:
   [JSON content provided above]

4. Run replace.py:
   python replace.py temp.pptx replacement.json final-proposal.pptx

5. Validate the output:
   python inventory.py final-proposal.pptx --issues-only

6. If validation passes, your proposal is ready:
   final-proposal.pptx
```

---

## QUALITY BENCHMARKS

### Visual Quality Standard

**Reference deck**: `sample-proposals/[EXT] 202503 NUS AIDF x CD - Exec Master Programme Campaign Plan - 26 Mar.pdf`

All outputs must match or exceed:

**Visual hierarchy clarity**:
- Section dividers clearly separate major sections
- Slide titles are immediately scannable
- Content flows logically from top to bottom
- Visual weight guides eye to primary message

**Text-to-visual ratio**:
- Max 30% text coverage per content slide
- Max 50% text coverage per table slide
- Section dividers: <10% text coverage
- Diagrams: 60% visual, 40% labels/text

**Color consistency**:
- All colors from brand-config.json
- Section dividers rotate through brand palette
- Funnel stages use consistent color coding
- Tables use consistent header/body/total styling

**Diagram clarity**:
- Flow direction is obvious (left-to-right or top-to-bottom)
- Connectors don't cross unnecessarily
- Labels are legible at 100% zoom
- Relationship between elements is clear

**Information density**:
- Each slide communicates 1 primary idea
- Supporting details are 3-5 bullets max
- Tables are scannable in 10 seconds
- No cognitive overload

### Rejection Criteria

**Reject and flag for manual intervention if**:

**Content violations**:
- Any slide has >100 words of body text (excluding tables)
- Funnel diagram has >4 stages
- Persona cards attempt to show >3 personas
- Media plan table has >15 rows without splitting
- Timeline exceeds 12 months without grouping
- Bullet list has >6 bullets

**Visual violations**:
- Text overflow detected by inventory.py
- Font other than Arial used
- Color not in brand-config.json
- Custom layout created
- Shape boundaries violated

**Consistency violations**:
- CTA mismatch between funnel and campaign flow
- Tactic name mismatch between strategy and media plan
- Budget total mismatch between media plan and investment
- Messaging misalignment between strategy and slides

**Pattern violations**:
- Pattern matching confidence <80%
- Content type cannot be classified
- Visual pattern doesn't fit content structure
- Layout index unavailable for pattern

**When rejection occurs**:
1. Generate detailed error report
2. Identify specific violation(s)
3. Recommend fix (compression, split, manual review)
4. Halt JSON generation
5. Prompt user for corrective action

---

## SYSTEM CONSTRAINTS

### Template Compatibility

**Locked to**:
- Template file: `skills/construct-pptx/assets/00 CD Deck Template.pptx`
- Template version: 2022 v1.0
- Slide count: 66 slides
- Aspect ratio: 16:9
- Dimensions: 720pt × 405pt

**Do NOT**:
- Use different templates
- Modify template master slides
- Change aspect ratio
- Add custom slide layouts
- Use slides 33, 51-65 (reference only)

**Template dependencies**:
- Brand colors defined in template theme
- Layout structure in template master
- Logo placement in template placeholders
- Font embedding in template file

### Script Dependencies

**This skill outputs data for**:

1. **rearrange.py** (slide sequencing)
   - Input: Template PPTX + slide sequence string
   - Output: Rearranged PPTX with selected slides
   - Dependency: Slide indices must exist in template

2. **replace.py** (content population)
   - Input: Rearranged PPTX + replacement JSON
   - Output: Final PPTX with populated content
   - Dependency: Shape indices must match layouts.md

3. **inventory.py** (validation)
   - Input: Final PPTX
   - Output: Overflow warnings, shape boundary issues
   - Dependency: PIL, pptx library, font files

**Ensure scripts are executable**:
```bash
chmod +x scripts/rearrange.py
chmod +x scripts/replace.py
chmod +x scripts/inventory.py
```

**Verify dependencies installed**:
```bash
pip install python-pptx Pillow
```

### Reference File Dependencies

**Required files**:
- `references/brand-config.json` (brand rules)
- `references/layouts.md` (layout documentation)
- `references/department-configs.md` (deck structure patterns)

**Optional files**:
- `sample-proposals/*.pdf` (visual reference only, do NOT copy content)

**File validation**:
- Before execution, verify brand-config.json is readable
- Before execution, verify layouts.md is available
- If files missing, halt and request files

### Non-Generative Nature

**This is a DETERMINISTIC MAPPING ENGINE, not a creative AI.**

**It WILL**:
- Map strategy data to predefined visual patterns
- Compress text using algorithmic rules
- Enforce brand consistency mechanically
- Validate against known constraints
- Generate automation-ready JSON

**It WILL NOT**:
- Generate new creative ideas
- Write persuasive copy from scratch
- Create custom visual diagrams
- Recommend strategy changes
- Infer missing data creatively
- Make subjective design decisions

**Principle**:
> "Given the same strategy input, the skill should produce the same proposal output every time. Determinism ensures quality, consistency, and predictability."

---

## APPENDIX A: Pattern-to-Layout Quick Reference

| Visual Pattern | Layout Index | Primary Use | Max Content | Overflow Handling |
|----------------|--------------|-------------|-------------|-------------------|
| BRIEF_SUMMARY_TABLE | 15 | Campaign overview | 6 rows × 100 chars | Split into 2 slides if > 6 rows |
| PERSONA_CARDS | 41, 42 | Audience segments | 3 personas max | Slide 41 (2), Slide 42 (1) |
| CHANNEL_RATIONALE_GRID | 27 | Channel justification | 8 channels, 12 words/channel | Reduce to top 8 channels |
| FUNNEL_DIAGRAM | 28 | Conversion stages | 3-4 stages, 8 words/stage | Max 4 stages, compress objectives |
| CAMPAIGN_FLOW_DIAGRAM | 29 | Tactic-to-stage map | 12 tactics, 4 words/tactic | Group similar tactics |
| MEDIA_PLAN_TABLE | 47 | Budget & projections | 12 rows | Split: Prosp+Retarg / Nurt+Total |
| BUDGET_ALLOCATION | 47 | Country breakdown | 10 countries | Top 8 + "Other" |
| TIMELINE_GANTT | 43 | Project phases | 6 phases, 12 months | Quarterly grouping if > 6 months |
| INVESTMENT_BREAKDOWN | 47 | Quotation | 15 line items | Summary + Detailed Breakdown |
| PAYMENT_MILESTONES | 47 | Payment schedule | 8 months | Group into quarters if > 8 |
| MESSAGING_PYRAMID | 15 | Message hierarchy | 3 levels, 2 messages/level | Top 2 messages per persona |
| TWO_COLUMN_SHOWCASE | 14 | Concept + visual | 80 words/column | Max 5 bullets per column |
| SECTION_DIVIDER | 6-10 | Section breaks | 3 words title, 8 words subtitle | Shorten title if needed |
| LANDING_PAGE_MOCKUP | 16-22 | Landing page preview | 4 features | Reduce to 3-4 key features |
| AD_FORMAT_SHOWCASE | 14 | Ad format explanation | 3 benefits, 2 sentences description | Max 3 formats per slide |
| REPORTING_DASHBOARD | 14 | Dashboard preview | 5 features per column | Show overview only |

**Usage notes**:
- Layout index refers to template slide position (0-based)
- Max content = recommended limits to avoid overflow
- Overflow handling = automatic adjustment strategy

---

## APPENDIX B: Compression Examples

### Example 1: Persona "About" Section

**Input** (from strategy, 85 words):
```
A mid-career technology professional responsible for driving AI adoption and digital transformation initiatives within their organization. They are working closely with senior executives, translating technical advancements into business value. Their goal is to get themselves ready for a future innovation role and lead the organization's AI transformation journey. They want to gain executive-level AI knowledge to guide business strategy, operations, and transformation initiatives. While they don't have hands-on AI expertise, they must understand AI, automation, and digital transformation to make informed business decisions and stay competitive in a digital-first economy.
```

**Output** (for slide, 28 words):
```
Mid-career technology professional responsible for driving AI adoption and digital transformation initiatives. Working with senior executives to translate technical advancements into business value.
```

**Compression ratio**: 67% reduction
**Techniques applied**:
- Eliminate redundancy ("their organization" implied)
- Remove future goals (covered in "Goals" section)
- Remove rationale (covered in "Motivations")
- Keep core identity only

---

### Example 2: Channel Rationale

**Input** (from strategy, 22 words):
```
Google Search: Targets high-intent professionals actively seeking education in AI and digital transformation
```

**Output** (for slide, 11 words):
```
Targets high-intent professionals actively seeking AI education
```

**Compression ratio**: 50% reduction
**Techniques applied**:
- Remove channel name (shown in logo)
- Abbreviate "digital transformation" to "AI" (context clear)
- Remove "in" (unnecessary)

---

### Example 3: Funnel Stage Objective

**Input** (from strategy, 18 words):
```
Achieve efficient reach through a cross-platform campaign targeting an addressable audience, while capturing leads and applications at every stage
```

**Output** (for slide, 8 words):
```
Efficient reach via cross-platform targeting, capturing leads
```

**Compression ratio**: 56% reduction
**Techniques applied**:
- "Achieve" → implied
- "campaign" → implied by context
- "addressable audience" → "targeting"
- "while capturing leads and applications at every stage" → "capturing leads" (applications covered in Decision stage)

---

### Example 4: Messaging Line

**Input** (from strategy, 25 words):
```
We recommend using the following aspirational message: "Lead AI-driven transformation with world-class expertise and global industry insights"
```

**Output** (for slide, 14 words):
```
"Lead AI-driven transformation with world-class expertise and global industry insights"
```

**Compression ratio**: 44% reduction
**Techniques applied**:
- Remove meta-language ("We recommend using the following aspirational message:")
- Keep actual message only
- Preserve quotation marks for clarity

---

### Example 5: Timeline Phase Description

**Input** (from strategy, 32 words):
```
Campaign Preparation phase will include landing page design and development, video production for ads, creation of all ad assets, and campaign setup across all platforms
```

**Output** (for slide, 8 words):
```
Landing page, video production, ads creation, campaign setups
```

**Compression ratio**: 75% reduction
**Techniques applied**:
- Remove "Campaign Preparation phase will include"
- Noun stacking: "video production for ads" → "video production"
- Parallel structure: "design and development" → implied
- "across all platforms" → implied

---

### Example 6: Table Cell (Tactic Name)

**Input** (from strategy):
```
Paid Social (Facebook/Instagram/LinkedIn) Traffic Ads targeting Persona 1
```

**Output** (for slide):
```
FB/IG/LI Traffic Ad
```

**Compression ratio**: 83% reduction
**Techniques applied**:
- Abbreviate platform names
- Add "Ad" suffix (per tactic column rule)
- Remove persona reference (shown in flow diagram)
- Singular "Ad" not "Ads"

---

## APPENDIX C: CTA Consistency Matrix

This matrix ensures CTAs are identical across all proposal sections:

| Funnel Stage | Strategy CTA | Slide 28 (Funnel) | Slide 29 (Flow) | Landing Page | Ads Specs | Media Plan KPI |
|--------------|--------------|-------------------|-----------------|--------------|-----------|----------------|
| Prospecting | Learn More | Learn More | Learn More → Landing Page | [Learn More button] | CTA: Learn More | Traffic |
| Retargeting | Download Brochure | Download Brochure | Download Brochure → Lead Capture | [Download Brochure button] | CTA: Download Brochure | SQL |
| Nurturing | Apply Now | Apply Now | Apply Now → Application | [Apply Now button] | CTA: Apply Now | Application |

**Validation rule**:
```
IF Strategy CTA != Slide 28 CTA:
  → REJECT, flag inconsistency

IF Slide 28 CTA != Slide 29 CTA:
  → REJECT, flag inconsistency

IF Landing Page CTA != Strategy CTA:
  → REJECT, flag inconsistency

IF Ads Spec CTA != Strategy CTA:
  → REJECT, flag inconsistency
```

**Example violation**:
```
Strategy: "Download Brochure" (Retargeting)
Slide 29: "Get Brochure" (Retargeting)
→ REJECT: CTA mismatch detected
→ Fix: Change Slide 29 to "Download Brochure"
```

---

## APPENDIX D: Error Handling & Recovery

### Error Types & Responses

| Error Type | Cause | Response | Recovery |
|------------|-------|----------|----------|
| MISSING_MANDATORY_FIELD | Input missing required field | Halt execution, list missing fields | Prompt user to provide missing data |
| INVALID_JSON_STRUCTURE | Input JSON doesn't match schema | Halt execution, show schema violation | Provide example valid structure |
| PATTERN_MATCH_FAILURE | Content type cannot be classified | Skip slide, log warning | Flag for manual review |
| OVERFLOW_DETECTED | Text exceeds shape boundaries | Trigger compression cascade | Apply Levels 1-4, then flag if needed |
| LAYOUT_INDEX_MISSING | Required layout not in template | Halt execution | Update template or use alternative layout |
| CTA_INCONSISTENCY | CTAs don't match across sections | Halt execution, show matrix | Fix source data, regenerate |
| BUDGET_MISMATCH | Media plan total != investment total | Halt execution, show discrepancy | Reconcile numbers in strategy |
| TACTIC_NAME_MISMATCH | Tactic in flow not in media plan | Log warning, proceed | Flag for review |
| COLOR_CODE_INVALID | Color not in brand-config.json | Halt execution | Use approved color or update brand config |
| FONT_SUBSTITUTION_ATTEMPTED | Non-Arial font requested | Reject, use Arial | Log warning |

### Recovery Workflows

**Workflow 1: Missing Field Recovery**
```
1. Identify missing field from schema
2. Check if field is in optional or mandatory list
3. If mandatory:
   a. Halt execution
   b. Generate error report
   c. Provide example of required structure
   d. Wait for user to provide data
4. If optional:
   a. Log warning
   b. Skip related slides
   c. Continue execution
   d. Note omission in validation report
```

**Workflow 2: Overflow Recovery**
```
1. Detect overflow via character count estimate
2. Apply compression Level 1 (eliminate filler)
3. Re-estimate, if still overflow → Level 2 (reduce bullets)
4. Re-estimate, if still overflow → Level 3 (convert to table)
5. Re-estimate, if still overflow → Level 4 (split slide)
6. If still overflow → flag for manual review
7. Log all compression attempts in metadata
```

**Workflow 3: Pattern Match Recovery**
```
1. Attempt primary pattern match
2. If confidence < 80%:
   a. Try secondary pattern (e.g., PERSONA_CARDS → TWO_COLUMN)
   b. If still < 80% → try tertiary (e.g., → BULLETS)
3. If all attempts fail:
   a. Use generic CONTENT_BULLETS layout
   b. Log warning
   c. Flag slide for manual design review
4. Continue with next content block
```

---

## APPENDIX E: Integration with Paid Media Strategist Skill

This skill is designed to consume outputs from the `paid-media-strategist-construct` skill seamlessly.

### Data Flow

```
User → Paid Media Strategist Skill
  ↓
  Generates:
  - Strategy sections (6 parts)
  - Media Plan (table)
  - Ads Production Specs (optional)
  - Estimator (optional)
  ↓
User → "Generate proposal deck"
  ↓
Paid Media Proposal Skill
  ↓
  Reads:
  - Latest strategy output from session
  - Latest media plan from session
  - Latest ads specs if available
  - Latest estimator if available
  ↓
  Processes:
  - Validates schema
  - Assigns visual patterns
  - Generates replacement JSON
  - Outputs slide sequence
  ↓
User → Runs automation scripts
  ↓
Final Proposal Deck (PPTX)
```

### Schema Mapping

| Strategist Output | Proposal Skill Input | Slide Pattern |
|-------------------|----------------------|---------------|
| Campaign Overview | campaign_overview | BRIEF_SUMMARY_TABLE |
| Audience Segmentation | audience_segmentation | PERSONA_CARDS |
| Recommended Channel Mix | channel_mix | CHANNEL_RATIONALE_GRID |
| Conversion Funnel Architecture | conversion_funnel | FUNNEL_DIAGRAM |
| Messaging Structure | messaging_structure | MESSAGING_PYRAMID |
| Campaign Flow (Layer 1 + 2) | campaign_flow | CAMPAIGN_FLOW_DIAGRAM |
| Media Plan (table) | media_plan | MEDIA_PLAN_TABLE |
| Estimator (quotation) | budget_breakdown | INVESTMENT_BREAKDOWN |
| (Inferred from media plan) | timeline | TIMELINE_GANTT |

### Session Context Requirements

**For seamless integration**:
1. User must run Strategist Skill first in same session
2. Strategist outputs remain in context (not cleared)
3. User can run Proposal Skill with simple command: "Generate proposal deck"
4. Proposal Skill auto-detects latest strategy structure
5. No manual copy-paste of JSON required

**If session context is lost**:
1. User must provide strategy.json file
2. Proposal Skill validates file structure
3. Proceeds with file input instead of session context

---

## END OF SKILL SPECIFICATION

**Version**: 1.0
**Last Updated**: 2025-01-XX
**Compatible With**: paid-media-strategist-construct v1.0
**Template Version**: CD Deck Template 2022 v1.0
**Maintainer**: Construct Digital Strategy Team
