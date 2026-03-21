# Dealflow Website Field Reference - DealflowLand.com

Every field below maps to a WordPress/Elementor field on the listing page.
All HTML outputs must be inside code blocks so tags are visible and copyable.
All outputs must use hyphens (-) never em dashes or en dashes.

---

## Field Order (Full Website Formatting Workflow)

When formatting a complete listing, output ALL fields in this exact order:

1. Title
2. Sub Title (always with `<br>` between lines)
3. Price
4. GeekPay-URL
5. Location (GPS coordinates)
6. Listing Location (County, State)
7. Location Single Box (same as Listing Location)
8. Size
9. short-description (3 creative hooks)
10. Highlights (4x heading + paragraph)
11. Google Map (same GPS as Location)
12. "Here's A Special Chance For You!" section - FIRST HALF of copy
    (Left Title, Left Paragraph, Right Paragraph, Mobile Combined)
13. What to Know Before You Make It Yours (9 DD bullets, always includes Lot Size)
14. Finance Terms (6 blocks)
15. Next Paragraphs - SECOND HALF of copy
    Reply order: Left Title 1, Left Title 2, Paragraph 1, Paragraph 2
    (titles grouped together, then paragraphs - easier for WP paste workflow)
16. CTA Text (Paragraph 3 - escalating format)
17. Slug
18. Filter Attributes (State, County, Property Type, Land Use - each separate)

**Excluded from output (never changes):**
- CTA Box (4 points) - static values, no need to output each time

---

## 1. Title

**Field name:** Edit product (title)
**Format:** Max 3 words per line, 2 lines, `<br>` break-line tag between lines
**Rules:** Keep it short and impactful. Use the hero image title or a shortened version
of the listing title that fits the 3-word-per-line constraint.

**Example:**
```
One Street<br>Crown Lake
```

---

## 2. Sub Title

**Field name:** Product description (short-description)
**Format:** 2-3 words per line, always use `<br>` between lines.
**Rules:** Matches the hero subtitle or a punchy descriptor.
Switch to "Code" tab in WordPress to use `<br>` tags.

**Example:**
```
Two Lots.<br>Your Move.
```

---

## 3. Price

**Field name:** Product data - Regular price ($)
**Format:** Plain number only. No "$" sign, no commas.

**Example:**
```
7880
```

---

## 4. Location (GPS Coordinates)

**Field name:** Location
**Format:** Latitude, Longitude in decimal degrees with comma-space between
**Rules:** Same value as Google Map field. Copied from exact location on Google Maps
or Land.Id.

**Example:**
```
36.2128, -91.7337
```

---

## 5. Listing Location

**Field name:** Listing Location
**Format:** `<County>, <State abbreviation>`

**Example:**
```
Izard, AR
```

---

## 6. Location Single Box

**Field name:** Location Single Box
**Format:** Exactly same as Listing Location: `<County>, <State abbreviation>`

**Example:**
```
Izard, AR
```

---

## 7. Size

**Field name:** Size
**Format:** `<number>-acre`

**Example:**
```
1.8-acre
```

---

## 8. short-description

**Field name:** short-description
**Format:** 3 short creative hooks, 2-5 words each, with `<br>` between.
**Rules:** These are like a sub-sub-title for the hero image and listing titles.
Must be creative, punchy, and match the emotional direction of the listing copy.
Not a factual summary - more like tagline fragments that pull the reader in.

**Example:**
```
True Arkansas freedom.<br>Two lots, one lake.<br>Your move starts here.<br>
```

---

## 9. GeekPay-URL

**Field name:** GeekPay-URL
**Format:** Down payment GeekPay link. Controls 3 buttons on the page
(SECURE YOUR LAND, START YOUR JOURNEY, MAKE IT YOURS).
**Rules:** Use the exact GeekPay down payment link provided by the user.

**Example:**
```
https://secure.geekpay.io/to/dealflow-oh-llc/down-payment-800-07252-000-and-800-07253-000-down-payment
```

---

## 10. Google Map

**Field name:** Google Map
**Format:** Latitude, Longitude in decimal degrees with comma-space between.
Same value as Location field (#4).

**Example:**
```
36.2128, -91.7337
```

---

## 11. Highlights

**Field names:** Highlights-heading-1 through 4, Highlights-paragraph-1 through 4
**Heading format:** Text, max 4-5 words, 1 liner, CamelCase
**Paragraph format:** Max 5-6 words, 1 liner, no CamelCase
**Rules:** Exactly 4 highlights. Focus on lifestyle, pricing, or location.
Never repeat the main Title or Sub Title.

**Example:**
```
Highlights-heading-1:
Two Lots - Two Homes

Highlights-paragraph-1:
Side by side living - one home per lot.

Highlights-heading-2:
1.8 Acre - Rare Size

Highlights-paragraph-2:
Bigger than typical Izard parcels.

Highlights-heading-3:
Near the Lake & Amenities

Highlights-paragraph-3:
Golf, kayak, boating, fishing - weekend ready.

Highlights-heading-4:
Wooded Lakeside Setting

Highlights-paragraph-4:
Quiet dirt road and tall trees surround you.
```

---

## 12. "Here's A Special Chance For You!" Section

**This is where the FIRST HALF of the main ad copy goes.**

The approved copy from the land-listing-copy skill does NOT go into a single "Listing Text"
field. Instead, it gets distributed across this section AND the Next Paragraphs section (#15).

Split the copy like this:
- **"Special Chance" section (this section):** The emotional opening, hook, storytelling,
  and the "why this lot" argument. Left Paragraph = emotional story. Right Paragraph =
  logical case / why it matters.
- **Next Paragraphs section (#15):** The added value details, lifestyle benefits,
  MRID/pricing explanation, and final pitch before CTA.

This section has 4 parts that must all be output separately:

### (1) Left Title
**Field name:** A-Special-Chance-for-you-section-title
**Format:** `text <br>Text <b>text</b>`
**Rules:** 2-3 lines. Conversational, avatar-focused hook. Ends with a bold phrase.

**Example:**
```
Hey there, let me guess...<br>One street from the lake, <b>and you are still thinking?</b>
```

### (1) Left Paragraph
**Field name:** A-Special-Chance-for-you-section-description-1
**Format:** Text, max 8 lines. Use `<br>` for line breaks.
**Rules:** Emotive story about the land. Speaks to the avatar's internal dialogue.
Uses `<b>` for emphasis on key phrases. `<br><br>` for paragraph spacing.

### (2) Right Paragraph
**Field name:** A-Special-Chance-for-you-section-description-2
**Format:** Text, max 10 lines.
**Rules:** Explains pain points, opportunities, or "why it matters."
More logical/analytical than the left paragraph. Uses `<b>` for emphasis.

### (1+2) Mobile Combined
**Field name:** A-Special-Chance-for-you-section-description-for-mobile-devices
**Format:** Combines both Left and Right paragraphs into one block.
**Rules:** Same content but different spacing and line breaking optimized for
mobile screen width. Use more `<br>` breaks for narrower screen.

---

## 13. What to Know Before You Make It Yours

**Field names:** What-to-Know-Before-You-Make-It-Yours-1 through 9
**Format:** `<b>Key:</b> Value`
**Rules:** Exactly 9 bullets. All CamelCase keys. Text values 1-3 words.

### Order Rules
1. Zoning (always first)
2. Buildable
3. Minimum Size For Building (if known)
4. HOA or MRID (MRID only for Izard County)
5. RVs
6. Camping, Mobile or Tiny Homes (can be separate bullets if needed)
7. Utilities
8. Lot Size (always include)
9. Road Access
10. APNs (always last)

Note: Exactly 9 bullets total. If all 10 items apply, combine related items
(e.g. merge Camping/Mobile/Tiny into one bullet) to stay at 9.
Lot Size should always be included - preferably as bullet #8.

### Izard County Special Rules
- Always include MRID Annual
- If no HOA, do not include HOA bullet - use the slot for something else
- Adjust bullet content to fit exactly 9

### Example (Izard County)
```
What-to-Know-Before-You-Make-It-Yours-1:
<b>Zoning:</b> Residential

What-to-Know-Before-You-Make-It-Yours-2:
<b>Buildable:</b> Yes, Single Family Home

What-to-Know-Before-You-Make-It-Yours-3:
<b>Minimum Size For Building:</b> 850sqft

What-to-Know-Before-You-Make-It-Yours-4:
<b>MRID Annual:</b> $80 Per Lot

What-to-Know-Before-You-Make-It-Yours-5:
<b>RVs:</b> Not Allowed

What-to-Know-Before-You-Make-It-Yours-6:
<b>Camping, Mobile or Tiny Homes:</b> Not Allowed

What-to-Know-Before-You-Make-It-Yours-7:
<b>Utilities:</b> Electricity On Street

What-to-Know-Before-You-Make-It-Yours-8:
<b>Lot Size:</b> 1.8 Acres

What-to-Know-Before-You-Make-It-Yours-9:
<b>APNs:</b> 800-07252-000, 800-07253-000
```

---

## 14. Finance Terms

**Field names:** HERE'S-THE-DEAL-Cash-Price, HERE'S-THE-DEAL-Down-Payment,
HERE'S-THE-DEAL-Monthly-Payment, HERE'S-THE-DEAL-Terms,
HERE'S-THE-DEAL-Monthly-Note-Fee, HERE'S-THE-DEAL-Document-Fee

**Format:** Exactly 6 blocks. Each block has the field name and value.
**Rules:** Annual Property Tax is skipped (not shown on website).
Input order from user: Down Payment, Terms, Cash Price, Monthly Payment,
Annual Tax, Note Fee, Doc Fee. Output ignores Annual Tax.

**Example:**
```
Cash (HERE'S-THE-DEAL-Cash-Price)
Value:
<b>Cash Price: </b>$7,880

Down Payment (HERE'S-THE-DEAL-Down-Payment)
Value:
<b>Down Payment: </b>$197

Monthly Payment (HERE'S-THE-DEAL-Monthly-Payment)
Value:
<b>Monthly Payment: </b>$199

Terms (HERE'S-THE-DEAL-Terms)
Value:
<b>Terms: </b>40 Months

Monthly Note Fee (HERE'S-THE-DEAL-Monthly-Note-Fee)
Value:
<b>Monthly Note Fee: </b>$10

Document Fee (HERE'S-THE-DEAL-Document-Fee)
Value:
<b>Document Fee: </b>$180
```

---

## 15. Next Paragraphs

**This is where the SECOND HALF of the main ad copy goes.**

The "Special Chance" section (#12) carries the emotional hook and opening argument.
This section carries the added value, lifestyle details, pricing explanation, and
final pitch before the CTA.

### (3) Left Title 1
**Field name:** One Added Value List Item
**Format:** 3 lines, 5-6 words per line
**Rules:** Lifestyle-driven title. Think "Added Value. No HOA Restrictions" style.

### (3) Paragraph 1
**Field name:** Added-Value-No-HOA-Restrictions
**Format:** 5-10 lines of text
**Rules:** Storytelling + facts. Lifestyle-driven, mention amenities or location.
Use `<br>` for line breaks, `<b>` for emphasis.

### (4) Left Title 2
**Field name:** You Might Wonder List Item
**Format:** 3 lines, 5-6 words per line
**Rules:** Addresses a question or concern. Think "You might wonder..." style.

### (4) Paragraph 2
**Field name:** You-might-wonder
**Format:** 5-10 lines of text
**Rules:** Story-driven value. Focus on retirement, family, peace, investment,
or MRID benefits. Use `<br>` for line breaks, `<b>` for emphasis.

---

## 16. CTA Text (Paragraph 3)

**Field name:** CTA Text
**Format:** Max 16 lines. Switch to "Text Tab" in WordPress editor.
**Rules:** Uses HTML span tags for font sizing and strong tags for bold.
The CTA must visually ESCALATE - start soft and build to bold, urgent, emotional.

**Key principles:**
- Font sizes increase as you go: start at normal text, build through 14pt, 16pt, 18pt
- Individual words within sentences can be wrapped in larger font spans for emphasis
- Short punchy lines - one thought per line
- Build a crescendo: soft opening -> question -> action -> urgency -> emotional close
- The last 3-4 lines should be the biggest and boldest
- Use `<strong>` for bold within spans
- Every line ends with `<br>` and empty `<br>` between lines for spacing

**Structure (escalating):**

```html
Opening emotional line (normal text)<br>
<br>
Second emotional line with one <span style="font-size: 16pt;"><strong>KEY WORD</strong></span> bigger<br>
<br>
<span style="font-size: 14pt;">Invitation or question line</span><br>
<br>
Do you have questions or want to talk about <strong>this property</strong>?<br>
<br>
<span style="font-size: 14pt;"><strong>Call to action line</strong></span><br>
<br>
<span style="font-size: 14pt;">Supportive CTA line</span><br>
<br>
<span style="font-size: 16pt;"><strong>Urgency or scarcity line (bigger)</strong></span><br>
<br>
<span style="font-size: 18pt;"><strong>Final emotional hook (biggest)</strong></span><br>
```

**Example (Crown Lake):**

```html
Picture waking up one street from the <span style="font-size: 16pt;"><strong>lake.</strong></span><br>
<br>
Feel the <span style="font-size: 16pt;"><strong>freedom</strong></span> of owning land on your own terms.<br>
<br>
<span style="font-size: 14pt;">Ready to claim your 1.8 acres near Crown Lake?</span><br>
<br>
Do you have questions or want to talk about <strong>this property</strong>?<br>
<br>
<span style="font-size: 14pt;"><strong>Reach out today - we guide every step</strong></span><br>
<br>
<span style="font-size: 14pt;">Simple process, clear terms, no surprises</span><br>
<br>
<span style="font-size: 16pt;"><strong>Two lakeside lots like this do not wait</strong></span><br>
<br>
<span style="font-size: 18pt;"><strong>This is your lake life waiting</strong></span><br>
```

---

## 17. CTA Box (4 Points)

**Field names:** It-Feels-Right-Make-the-Move-point-1 through 4
**Format:** ALL CAPITALS, max 2 lines each
**Rules:** Usually do not change unless there is something property-specific.
Update the money-back guarantee to 35 days.

**Default values:**
```
Point 1: 35-DAY MONEY-BACK GUARANTEE - YOU'RE FULLY PROTECTED
Point 2: LIMITED AVAILABILITY - DON'T LET THIS OPPORTUNITY PASS
Point 3: LET THIS GO - AND SOMEONE ELSE WON'T
Point 4: TAKE THE FIRST STEP TOWARD SOMETHING REAL
```

---

## 18. Slug

**Field name:** Slug
**Format:** `<county>_<state>_<description-or-APN>_<size>`
**Rules:** Lowercase only. Words separated by hyphens (-).
No dots, slashes, or extra characters.

**Example:**
```
izard_ar_crown-lake-2-lots_1-8-acre
```

---

## 19. Filter Attributes

### State
**Field name:** Select States
**Format:** Select from existing list or add new
**Available values:** Arizona, Arkansas, Colorado, Florida, New Mexico

### County
**Field name:** Select Counties
**Format:** Select from existing list or add new
**Available values:** Cochise, Costilla, Izard, Jefferson, Putnam, Sharp, Union, Valencia

### Property Type
**Field name:** Listing
**Format:** Select from closed list
**Available values:** Agricultural, Commercial, Recreational, Residential

### Land Use (Product Tags)
**Field name:** Product tags
**Format:** Select from existing list
**Available values:**
Camping, Cleared, Close to Lake, Desert, Farming, Hunting, Livestock,
Manufactured, Mobile Home, No HOA, Residential, Rural, RVs, Tiny Home,
Trailers, Unrestricted, Wooded

**Rules:** Always include Residential unless property is not residential.
Only include what zoning/land use actually allows.
Exclude Camping/Mobile/RVs/Tiny if not allowed.

---

## Cover/Main Image Specs

Not generated by this skill, but for reference:
- Format: jpg, jpeg, or png
- Dimensions: 1456 x 901
- Resolution: 72 x 72 dpi
- Must include badge icon (Lifestyle, Surrounding Area, Distance, or Street View)
- Font for badge text: Neue Montreal, Medium Italic
- Icons and text in white color on listing images

---

## General Rules

- Never invent facts - only use info from the approved listing
- No em dashes or en dashes - hyphens with spaces only
- All HTML outputs inside code blocks
- `<br>` for line breaks, no space after `<br>`
- `<b>` for bold, `<strong>` for meaningful emphasis
- Never bold titles or subtitles - only within body copy
- Always end questions with "?"
- All content in English
- Check final output for any AI long dashes and replace with hyphens
