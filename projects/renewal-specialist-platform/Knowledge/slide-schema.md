# Renewal Specialist Platform: Slide Schema Definition

**Purpose:** Source of truth for Prompt Builder Agent slide structure, required fields, and consistency constraints.

**Used By:**
- Prompt Builder Agent (runtime reference in Copilot Studio knowledge base)
- QA/Evaluation (validation of generated slide structure)
- Architecture documentation

**Last Updated:** 2026-07-28  
**Version:** 1.1

---

## Complete Slide Schema

```json
{
  "presentation_metadata": {
    "audience": "K-12 District Leadership",
    "role": "Microsoft Renewals Specialist",
    "objective": "Support Microsoft 365 Education renewal and evidence-based growth discussion",
    "tone": "Professional, consultative, education-focused",
    "template_instruction": "Use the approved Microsoft Education K-12 template for styling, layout, fonts, colors",
    "institution_verification": {
      "type": "K-12 district",
      "size_band": "small/medium/large (by enrollment or staff)",
      "rural_urban": "rural/suburban/urban (from verified public source)",
      "sources": ["CIR if provided", "web verification for classification only"]
    }
  },
  "slides": [
    {
      "slide_number": 1,
      "slide_type": "title",
      "title": "[Organization Name] — Microsoft 365 Education Renewal",
      "subtitle": "Strategic Opportunity & Renewal Discussion",
      "speaker_intent": "Establish context and tone for consultative renewal conversation",
      "presenter_notes": "[Include date, participant names, prior engagement context if available]"
    },
    {
      "slide_number": 2,
      "slide_type": "content",
      "title": "About [Organization Name]",
      "subtitle": "Section 1 - Organization & Agreement Context",
      "speaker_intent": "Establish organization profile and current agreement status",
      "required_fields": {
        "institution_table": {
          "type": "data table",
          "fields": ["Institution Type", "Size", "Location", "Number of Students", "Number of Staff"],
          "source": "CIR only",
          "rule": "Do not estimate; use only verified data from CIR"
        },
        "agreement_details": {
          "type": "text box adjacent to institution table",
          "fields": ["Agreement Type", "Agreement Number", "Exp Date"],
          "source": "CIR (authoritative)",
          "rule": "Current agreement from CIR is ground truth; place this text box next to the institution table"
        },
        "microsoft_org_message": {
          "type": "narrative paragraph",
          "structure": "[Organization mission/priorities] → [Microsoft enables this] → [Together, stronger impact]",
          "source_priority": [
            "Organization website mission statement (if URL provided)",
            "CIR organizational context (if website unavailable)",
            "Internal sales guidance (if neither available)"
          ],
          "rule": "Synthesize; never fabricate. If mission unavailable, note explicitly: 'Organization mission under review'",
          "critical_for": "Website grounding feature (2026.07.28+)"
        }
      },
      "presenter_notes": "[Include: data sources used, any gaps noted ('under review' or 'to confirm'), website source attribution if applicable]"
    },
    {
      "slide_number": 3,
      "slide_type": "content",
      "title": "Current State to Optimized Value",
      "subtitle": "Strategic Opportunities",
      "speaker_intent": "Surface 2-3 aligned focus areas where Microsoft portfolio adds value",
      "required_fields": {
        "current_portfolio": {
          "type": "3 key points",
          "items": ["Key point 1: Current licensed workload(s)", "Key point 2: Current adoption signal", "Key point 3: Current infrastructure state"],
          "source": "CIR owned licenses",
          "rule": "State only what CIR confirms; avoid estimates"
        },
        "strategic_opportunities": {
          "type": "3 key points (aligned to selected strategy A or B)",
          "items": [
            "Opportunity 1: Value enhancement area (e.g., security, compliance, AI readiness, device management)",
            "Opportunity 2: Capability gap area (if evidence supports)",
            "Opportunity 3: Growth pathway (if evidence supports)"
          ],
          "source": "CIR adoption signals + compliance context + sales guidance alignment",
          "rule": "Support each opportunity with evidence; avoid speculation"
        }
      },
      "presenter_notes": "[Include: strategy selected (A=Adoption-Led or B=Capability Gap), key discovery questions to explore, risks noted]"
    },
    {
      "slide_number": 4,
      "slide_type": "content",
      "title": "Recommended Most Valuable Product",
      "subtitle": "Strategic Fit & Use Cases",
      "speaker_intent": "Propose primary recommended product with clear value rationale",
      "required_fields": {
        "product_recommendation": {
          "type": "product name + value rationale",
          "content": "Select most valuable product for customer scenario based on evidence",
          "rule": "One product; supported by evidence from CIR and strategy"
        },
        "aligned_use_cases": {
          "type": "3 use cases",
          "content": [
            "Use case 1: How product addresses customer priority",
            "Use case 2: How product enhances current state",
            "Use case 3: How product supports education mission (if applicable)"
          ],
          "rule": "Concrete, education-focused; avoid jargon"
        }
      },
      "presenter_notes": "[Include: product value rationale, success metrics, likely adoption timeline]"
    },
    {
      "slide_number": 5,
      "slide_type": "content",
      "title": "Next Steps",
      "subtitle": "Collaborative Renewal Roadmap",
      "speaker_intent": "Propose immediate, mid-term, and pre-renewal actions",
      "required_fields": {
        "immediate_actions": {
          "type": "1-2 collaborative actions",
          "content": "[Action 1: Discovery validation, stakeholder alignment, etc.]",
          "rule": "Non-blocking, collaborative tone"
        },
        "mid_term_actions": {
          "type": "1-2 mid-term actions",
          "content": "[Action 2: Proof of value, pilot deployment, etc.]",
          "rule": "Aligned to selected strategy"
        },
        "pre_renewal_actions": {
          "type": "1-2 renewal-focused actions",
          "content": "[Action 3: Contract review, licensing alignment, expansion decision, etc.]",
          "rule": "Support renewal process; no pressure language"
        }
      },
      "presenter_notes": "[Include: timeline, stakeholders involved, success criteria, upsell/cross-sell opportunities if applicable]"
    }
  ]
}
```

---

## Field Validation Rules

### Slide 2: Institution Table
- **Source:** Customer Intelligence Report only
- **Fields required:** Institution Type | Size | Location | Number of Students | Number of Staff
- **Rule:** Do NOT estimate missing fields. Mark as "under review" or "to confirm" if data unavailable.

### Slide 2: Agreement Details Text Box
- **Source:** Customer Intelligence Report (authoritative)
- **Fields required:** Agreement Type | Agreement Number | Exp Date
- **Placement rule:** Must be shown in a text box adjacent to the Slide 2 institution table.
- **Rule:** Current agreement from CIR is ground truth; never infer from website or assumptions.

### Slide 2: Microsoft + Org Message (CRITICAL for Website Grounding)
- **Source Priority:**
  1. Organization website mission statement (if URL provided via orchestrator)
  2. CIR organizational context (if website unavailable)
  3. Internal sales guidance (fallback)
- **Structure:** `[Organization mission] → [Microsoft enables this] → [Together, impact]`
- **Rule:** Synthesize authentic narrative; never fabricate. Document source in presenter notes.
- **Fallback:** If mission unavailable, note explicitly: `"Organization mission under review"` (no fabrication).
- **Website grounding example:** 
  > "Lincoln High School District is dedicated to equitable STEM access for all students. Microsoft 365 Education enables this by providing secure, collaborative tools for STEM curriculum delivery and teacher professional development. Together, Lincoln can scale STEM impact and measure adoption outcomes with Microsoft analytics."

### Slide 3: Current Portfolio (3 Points)
- **Source:** CIR owned licenses only
- **Rule:** State only confirmed workloads and adoption signals; no estimates.

### Slide 3: Strategic Opportunities (3 Points)
- **Source:** CIR adoption signals + compliance context + sales guidance
- **Rule:** Each opportunity must be evidence-based; avoid speculation.
- **Strategy alignment:** Match to selected strategy (A=Adoption-Led or B=Capability Gap).

### Slides 1, 4, 5: Non-Negotiable Constraints
- **Slide 1 (Title):** Organization name must match CIR exactly
- **Slide 4 (Product):** No pricing, discounting, or negotiation language
- **Slide 5 (Next Steps):** Collaborative tone; no pressure language

---

## Consistency Checks (For QA/Validation)

Before finalizing generated presentation, verify:

| Check | Validation Rule | Pass/Fail |
|-------|-----------------|-----------|
| **Slide Count** | Exactly 5 slides in order | [ ] |
| **Slide 1** | Title + subtitle present | [ ] |
| **Slide 2 Institution** | All 5 table fields present; no estimates | [ ] |
| **Slide 2 Agreement** | Agreement Type + Agreement Number + Exp Date present in adjacent text box | [ ] |
| **Slide 2 Microsoft + Org** | Narrative synthesizes org mission + Microsoft role; source documented | [ ] |
| **Slide 3 Portfolio** | 3 key points from owned licenses | [ ] |
| **Slide 3 Opportunities** | 3 key points aligned to strategy; evidence-based | [ ] |
| **Slide 4 Product** | 1 product + 3 use cases; no pricing | [ ] |
| **Slide 5 Next Steps** | Immediate + mid-term + pre-renewal; collaborative tone | [ ] |
| **No JSON in Output** | Zero JSON/schema/internal reasoning in user output | [ ] |
| **No Fabrication** | No estimated fields; all gaps marked "under review" | [ ] |

---

## Version History

### v1.1 (2026-07-28)
- Enforced Slide 2 agreement details as adjacent text box
- Added required fields: Agreement Type, Agreement Number, Exp Date
- Updated Slide 2 validation checklist for placement + fields

### v1.0 (2026-07-28)
- Initial schema definition
- Website grounding integration (Slide 2 Microsoft + Org message)
- Explicit fallback rules for unavailable data
- Full consistency validation checklist
- QA-ready schema for evaluation testing
