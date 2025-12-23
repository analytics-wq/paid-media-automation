# Department Deck Configurations

Pre-defined structures for common deck types by department.

## Leadership

### Annual Planning
```json
{
  "type": "annual-planning",
  "structure": [
    {"slide": 1, "layout": "title"},
    {"slide": 6, "layout": "section", "title": "The Gap"},
    {"slide": 10, "layout": "content", "title": "Current State"},
    {"slide": 21, "layout": "comparison", "title": "Current vs Target"},
    {"slide": 28, "layout": "table", "title": "Financial Targets"},
    {"slide": 7, "layout": "section", "title": "Strategy"},
    {"slide": 10, "layout": "content", "title": "Key Shifts"},
    {"slide": 11, "layout": "twoColumn", "title": "Levers"},
    {"slide": 8, "layout": "section", "title": "Accountability"},
    {"slide": 28, "layout": "table", "title": "Who Owns What"},
    {"slide": 30, "layout": "closing"}
  ]
}
```

### Quarterly Rocks
```json
{
  "type": "quarterly-rocks",
  "structure": [
    {"slide": 1, "layout": "title"},
    {"slide": 16, "layout": "bigNumber", "title": "Scorecard"},
    {"slide": 28, "layout": "table", "title": "Rock Status"},
    {"slide": 10, "layout": "content", "title": "Issues"},
    {"slide": 10, "layout": "content", "title": "Next Quarter"},
    {"slide": 30, "layout": "closing"}
  ]
}
```

### Board Update
```json
{
  "type": "board-update",
  "structure": [
    {"slide": 1, "layout": "title"},
    {"slide": 16, "layout": "bigNumber", "title": "Key Metrics"},
    {"slide": 10, "layout": "content", "title": "Highlights"},
    {"slide": 10, "layout": "content", "title": "Challenges"},
    {"slide": 28, "layout": "table", "title": "Financials"},
    {"slide": 27, "layout": "timeline", "title": "Roadmap"},
    {"slide": 30, "layout": "closing"}
  ]
}
```

### Townhall
```json
{
  "type": "townhall",
  "structure": [
    {"slide": 1, "layout": "title"},
    {"slide": 29, "layout": "agenda"},
    {"slide": 16, "layout": "bigNumber", "title": "Company Scorecard"},
    {"slide": 10, "layout": "content", "title": "Wins"},
    {"slide": 10, "layout": "content", "title": "Challenges"},
    {"slide": 10, "layout": "content", "title": "What's Next"},
    {"slide": 30, "layout": "closing"}
  ]
}
```

## Client-Delivery

### Proposal
```json
{
  "type": "proposal",
  "structure": [
    {"slide": 1, "layout": "title"},
    {"slide": 29, "layout": "agenda"},
    {"slide": 6, "layout": "section", "title": "Understanding"},
    {"slide": 10, "layout": "content", "title": "Your Challenge"},
    {"slide": 7, "layout": "section", "title": "Our Approach"},
    {"slide": 10, "layout": "content", "title": "Methodology"},
    {"slide": 27, "layout": "timeline", "title": "Timeline"},
    {"slide": 8, "layout": "section", "title": "Investment"},
    {"slide": 28, "layout": "table", "title": "Pricing"},
    {"slide": 22, "layout": "team", "title": "Your Team"},
    {"slide": 30, "layout": "closing"}
  ]
}
```

### QBR
```json
{
  "type": "qbr",
  "structure": [
    {"slide": 1, "layout": "title"},
    {"slide": 29, "layout": "agenda"},
    {"slide": 6, "layout": "section", "title": "Performance"},
    {"slide": 16, "layout": "bigNumber", "title": "Key Metrics"},
    {"slide": 10, "layout": "content", "title": "Campaign Results"},
    {"slide": 7, "layout": "section", "title": "Insights"},
    {"slide": 10, "layout": "content", "title": "What Worked"},
    {"slide": 10, "layout": "content", "title": "Learnings"},
    {"slide": 8, "layout": "section", "title": "Next Quarter"},
    {"slide": 10, "layout": "content", "title": "Recommendations"},
    {"slide": 30, "layout": "closing"}
  ]
}
```

## Strategy

### Workshop
```json
{
  "type": "workshop",
  "structure": [
    {"slide": 1, "layout": "title"},
    {"slide": 29, "layout": "agenda"},
    {"slide": 6, "layout": "section", "title": "Context"},
    {"slide": 10, "layout": "content"},
    {"slide": 7, "layout": "section", "title": "Workshop 1"},
    {"slide": 10, "layout": "content"},
    {"slide": 8, "layout": "section", "title": "Workshop 2"},
    {"slide": 10, "layout": "content"},
    {"slide": 9, "layout": "section", "title": "Next Steps"},
    {"slide": 10, "layout": "content"},
    {"slide": 30, "layout": "closing"}
  ]
}
```

### Brand Strategy
```json
{
  "type": "brand-strategy",
  "structure": [
    {"slide": 1, "layout": "title"},
    {"slide": 29, "layout": "agenda"},
    {"slide": 6, "layout": "section", "title": "Discovery"},
    {"slide": 10, "layout": "content", "title": "Market Context"},
    {"slide": 24, "layout": "personas", "title": "Target Audiences"},
    {"slide": 7, "layout": "section", "title": "Strategy"},
    {"slide": 10, "layout": "content", "title": "Positioning"},
    {"slide": 11, "layout": "twoColumn", "title": "Brand Framework"},
    {"slide": 8, "layout": "section", "title": "Execution"},
    {"slide": 27, "layout": "timeline", "title": "Roadmap"},
    {"slide": 30, "layout": "closing"}
  ]
}
```

## Creative

### Pitch Deck
```json
{
  "type": "pitch-deck",
  "structure": [
    {"slide": 4, "layout": "title", "note": "Image background"},
    {"slide": 6, "layout": "section", "title": "The Brief"},
    {"slide": 10, "layout": "content", "title": "Challenge"},
    {"slide": 7, "layout": "section", "title": "The Idea"},
    {"slide": 10, "layout": "content", "title": "Concept"},
    {"slide": 8, "layout": "section", "title": "Execution"},
    {"slide": 11, "layout": "twoColumn"},
    {"slide": 11, "layout": "twoColumn"},
    {"slide": 9, "layout": "section", "title": "Investment"},
    {"slide": 28, "layout": "table", "title": "Budget"},
    {"slide": 30, "layout": "closing"}
  ]
}
```

### Campaign Review
```json
{
  "type": "campaign-review",
  "structure": [
    {"slide": 1, "layout": "title"},
    {"slide": 6, "layout": "section", "title": "Campaign Overview"},
    {"slide": 10, "layout": "content", "title": "Objectives"},
    {"slide": 7, "layout": "section", "title": "Results"},
    {"slide": 16, "layout": "bigNumber", "title": "Key Metrics"},
    {"slide": 25, "layout": "caseStudy", "title": "Highlights"},
    {"slide": 8, "layout": "section", "title": "Learnings"},
    {"slide": 10, "layout": "content", "title": "What Worked"},
    {"slide": 10, "layout": "content", "title": "Recommendations"},
    {"slide": 30, "layout": "closing"}
  ]
}
```
