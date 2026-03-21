---
name: dealflow-website-listing
description: >
  Format approved land listing copy into the WordPress/Elementor field structure for
  DealflowLand.com. Trigger this skill when the user wants to format a listing for the
  Dealflow website, asks for "website version", "WordPress version", "Elementor version",
  "Dealflow website format", "5 paragraphs", "highlights", "dd bullets", "give me terms",
  "suggest a slug", or "filter tags". Also trigger when the land-listing-copy skill
  completes Phase 8 (compilation) and the user is ready to format for the website.
  This skill takes existing approved listing copy and distributes it across the specific
  fields and HTML format required by the DealflowLand.com WordPress/Elementor site.
  Always trigger when the user mentions "dealflow website", "website listing", or any
  reference to formatting copy for the Dealflow site. Can also be triggered standalone
  for quick commands like "give me 9 dd bullets" or "give me terms".
---

# Dealflow Website Listing Skill - DealflowLand.com

## Purpose

Take approved listing copy (from the land-listing-copy skill or user-provided text)
and distribute it into the exact WordPress/Elementor field structure needed for
DealflowLand.com. Every output maps to a named field on the website.

## Before Doing Anything

Read `references/website-format.md` for the complete field reference with exact
field names, formats, constraints, and examples.

---

## How It Works

This skill is typically triggered after the land-listing-copy skill completes its
full workflow (Phase 8 compilation). All listing data from that workflow flows in.

It can also be triggered standalone when the user has copy ready or wants quick commands.

---

## Full Website Formatting Workflow

When formatting a complete listing, read `references/website-format.md` and output
ALL 18 field groups in order. Each output must be inside a code block so HTML tags
are visible and directly copyable into WordPress fields.

The 18 output field groups are (in this exact order):

1. **Title** - max 3 words per line, 2 lines, `<br>` between
2. **Sub Title** - 2-3 words per line, always `<br>` between lines
3. **Price** - plain number, no $ or commas
4. **GeekPay-URL** - down payment link (controls 3 buttons)
5. **Location** - GPS coordinates (lat, long with comma-space)
6. **Listing Location** - County, State abbreviation
7. **Location Single Box** - same as Listing Location
8. **Size** - number-acre format
9. **short-description** - 3 creative hooks, 2-5 words each, `<br>` between
10. **Highlights** - 4x heading + paragraph (each in separate copy block)
11. **Google Map** - same GPS coordinates as Location (#5)
12. **"Here's A Special Chance For You!" section** - FIRST HALF of copy
    (Left Title, Left Paragraph, Right Paragraph, Mobile Combined)
13. **What to Know** - 9 DD bullets (always includes Lot Size, each separate block)
14. **Finance Terms** - 6 blocks (each separate)
15. **Next Paragraphs** - SECOND HALF of copy
    Reply order: Left Title 1, Left Title 2, then Paragraph 1, Paragraph 2
16. **CTA Text** - Paragraph 3, escalating font sizes
17. **Slug** - county_state_description_size format
18. **Filter Attributes** - State, County, Property Type, Land Use (each separate block)

**Excluded from output (static, never changes):**
- CTA Box (4 points) - always the same values, no need to output

**IMPORTANT:** There is no standalone "Listing Text" field. The main ad copy from
the land-listing-copy skill gets SPLIT across fields #12 (emotional hook / story)
and #15 (added value / details / pitch).

---

## Quick Commands

These can be triggered standalone without the full workflow:

| Command | What it does | Reference section |
|---------|-------------|-------------------|
| "I need the highlights" | 4 highlights with heading + paragraph | Section 11 |
| "improve this copy and give it in 5 paragraphs" | Sections 12 + 15 + 16 combined | Sections 12, 15, 16 |
| "give me 9 dd bullets" | 9 due diligence bullets | Section 13 |
| "give me terms" | 6 pricing blocks | Section 14 |
| "suggest a slug" | URL slug | Section 18 |
| "filter tags" | Land use product tags | Section 19 (Land Use) |

Quick commands always reference current listing context. If none exists, ask first.

---

## Key Formatting Rules

- All HTML outputs inside code blocks (visible and copyable)
- `<br>` for line breaks, no space after `<br>`
- `<b>Bold</b>` for bold emphasis
- `<strong>meaningful emphasis</strong>` for strong emphasis
- Never bold titles or subtitles - only within body copy
- No em dashes or en dashes anywhere - only hyphens with spaces
- All content in English regardless of conversation language
- Always do a final check for AI-generated long dashes and replace with hyphens
- 35-day money-back guarantee is the standard (update CTA Box Point 1 accordingly)

## Output Presentation Rules

When presenting website fields to the user, follow these rules for easy copy-paste:

- **Each field gets its own separate code block** - never combine multiple fields
  into one code block
- **Field name/key goes OUTSIDE the code block** as a label/title above it
- **Only the value goes INSIDE the code block** - ready to copy in 1 click
- For fields with multiple sub-items (like DD bullets 1-9, Highlights 1-4,
  CTA Box points 1-4), put EACH sub-item in its own separate code block
  with its field name as a label above
- For Finance Terms, each of the 6 blocks gets its own code block
- For the "Here's A Special Chance" section, each part (Left Title, Left Paragraph,
  Right Paragraph, Mobile Combined) gets its own code block
- This makes it fast to copy each value and paste it directly into the
  corresponding WordPress field without selecting or trimming

---

## What This Skill Does NOT Do

- Does not write new copy from scratch (use land-listing-copy skill for that)
- Does not invent facts - only uses approved listing data
- Does not offer land improvements - buyers are responsible
- Does not include improvement details - only available use and zoning
