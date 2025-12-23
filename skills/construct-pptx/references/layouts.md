# Construct Digital Slide Layouts

Template slide mappings for **00 CD Deck Template 2022 v1.0.pptx** (66 slides).

## Quick Reference

| Index | Layout | Background | Use For |
|-------|--------|------------|---------|
| 0 | Title | Blue | Cover page (title, subtitle, author/date) |
| 2 | Title | Green | Section opener |
| 3 | Title | Red | Section opener |
| 4 | Title | Image Right | Visual opener |
| 5 | Title | Image Left | Alternative visual opener |
| 6 | Title | Purple | Section opener |
| 7 | Section | Blue | Section divider (title + subtitle) |
| 8 | Section | Green | Section divider |
| 9 | Section | Red | Section divider |
| 10 | Section | Purple | Section divider |
| 11 | Big Concept | White | Statement slide (large text) |
| 12 | Content | White | Paragraph with image placeholder |
| 13 | Content | White | Paragraph with image placeholder (alt) |
| 14 | Two Column | White | Headers + body text (4 shapes) |
| 15 | Content Bullets | White | Bullet list + statement |
| 16-18 | Image | White | Title only with image placeholder |
| 19-20 | Image Left | White | Title with image placeholder left |
| 21 | Image Right | White | Title with image placeholder right |
| 22 | Image Full | White | Big image with caption |
| 23 | Quote | White | Quotation (centered) |
| 24 | Big Number | White | Single large stat + description |
| 25 | Principles | White | Number + 4 text blocks |
| 26 | Capabilities | White | Title + 3 capability areas |
| 27 | Channels | White | Channel rationale + bullets |
| 28 | Funnel | White | Conversion funnel diagram |
| 29 | Campaign Flow | White | Campaign flow diagram |
| 30 | Content Architecture | White | Title only (diagram placeholder) |
| 31 | Team | White | Full team grid (20+ slots) |
| 32 | Team Alt | White | Smaller team grid |
| 33 | Team Headshots | White | Reference slide (do not use) |
| 34-40 | Team Variants | White | Different team configurations |
| 41 | Persona | White | Consumer landscape/persona |
| 42 | Persona Detail | White | Detailed persona card |
| 43 | Timeline | White | Timeline with months |
| 44-45 | Mockup | White | Device mockups |
| 46 | Content | White | Standard content slide |
| 47 | Budget Table | White | Budget breakdown table |
| 48 | ABM Targeting | White | ABM targeting parameters |
| 49 | Case Study | White | Case study with logo |
| 50 | Closing | Blue | Thank you / closing slide |
| 51-59 | Style Guide | White | Template reference (do not use) |
| 60-65 | Icon Library | White | Icon reference (do not use) |

## Section Dividers (7-10)

Section dividers for chapter breaks:
- **Slide 7**: Blue section divider
- **Slide 8**: Green section divider
- **Slide 9**: Red section divider
- **Slide 10**: Purple section divider

**Layout structure:**
- shape-0: Section title (36pt)
- shape-1: Section subtitle (24pt)

## Title Slides (0, 2-6)

Opening slides with brand colors:
- **Slide 0**: Blue (primary cover)
- **Slide 2**: Green
- **Slide 3**: Red
- **Slide 4**: Blue with image right
- **Slide 5**: Blue with image left
- **Slide 6**: Purple

**Layout structure:**
- shape-0: Title (42pt)
- shape-1: Subtitle (24pt)
- shape-2: Author/date (10pt)

## Two Column (14)

Side-by-side content layout:
- shape-0: Slide title (28pt)
- shape-1: Column 1 header (16pt)
- shape-2: Column 1 body (16pt)
- shape-3: Column 2 header (16pt)
- shape-4: Column 2 body (16pt)

## Content Bullets (15)

Bullet list with key statement:
- shape-0: Slide title (28pt)
- shape-1: Bullet list (18pt, bulleted)
- shape-2: Key statement (20pt, bold)

## Big Number (24)

Large statistic display:
- shape-0: Big number (74pt)
- shape-1: Description (20pt)

## Quote (23)

Centered quotation:
- shape-0: Quote text (34pt, centered)

## Funnel (28)

Marketing funnel diagram:
- shape-0: Title (28pt)
- shape-1: Funnel intro text
- shape-2-7: Funnel stages (Awareness, Consideration, Decision)

## Case Study (49)

Client case study:
- shape-0: Title "Case Study" (28pt)
- Additional shapes for challenge, solution, results

## Closing (50)

Thank you slide:
- shape-0: Tagline text (18pt, gray)

## Common Deck Structures

### Client Proposal
```
0, 7, 15, 14, 8, 24, 27, 28, 31, 50
```
Title → Section → Bullets → TwoCol → Section → Stats → Channels → Funnel → Team → Close

### QBR / Campaign Review
```
0, 7, 24, 24, 15, 8, 47, 50
```
Title → Section → Stats → Stats → Bullets → Section → Budget → Close

### Workshop
```
0, 7, 15, 14, 14, 8, 15, 50
```
Title → Section → Bullets → TwoCol → TwoCol → Section → Bullets → Close

### Annual Planning
```
0, 7, 15, 14, 8, 15, 43, 50
```
Title → Section → Bullets → TwoCol → Section → Bullets → Timeline → Close

### Pitch Deck
```
0, 11, 7, 15, 8, 24, 9, 49, 50
```
Title → Big Concept → Section → Bullets → Section → Stats → Section → Case Study → Close

## Usage Notes

1. **Do not use slides 33, 51-65** - These are reference/style guide slides
2. **Team slides (31-40)** - Multiple configurations available, choose based on team size
3. **Image slides (16-22)** - Add images manually after generation
4. **Funnel/Campaign Flow (28-29)** - Complex diagrams, may need manual adjustment
