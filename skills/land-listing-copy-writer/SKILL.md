---
name: land-listing-copy
description: >
  Write high-conversion vacant land listing copy using Hormozi marketing psychology
  and the Slippery Slide copywriting framework for Dealflow OH LLC. Trigger this skill
  whenever the user wants to create, write, rewrite, or improve a land listing ad, generate
  listing titles, write ad copy for any platform, create a LandSearch compliant version,
  get image suggestions, or do avatar/buyer research for a property.
  Also trigger for any mention of "listing copy", "ad copy", "land ad", "write a listing",
  "listing for [county/state]", "LandSearch version", "Landmodo", or "image suggestions".
  Always trigger when the user shares property details and wants marketing output.
  For website formatting commands ("highlights", "5 paragraphs", "dd bullets", "give me
  terms", "suggest a slug", "filter tags"), use the dealflow-website-listing skill instead.
---

# Land Listing Copy Skill - Dealflow OH LLC

## Purpose

Engineer high-conversion land listing copy that reduces buyer risk and increases certainty.
Combines Hormozi marketing psychology (dominant engine) with the Slippery Slide copywriting
structure. Every listing is an offer, not a description.

## Core Philosophy

**People do not buy land. They buy certainty + optionality.**

Every line must answer three internal buyer questions:
1. Is this safe?
2. Is this flexible?
3. Am I making a mistake?

If the copy does not answer those - it will not convert.

**Stop describing land. Start reducing risk and increasing certainty.**

---

## Before Writing Anything

Read the relevant reference files based on the task:

| Task | Read first |
|------|-----------|
| Full listing workflow (new property) | `references/hormozi-framework.md` then `references/copywriting-playbook.md` |
| Avatar/buyer research | `references/avatar-categories.md` |
| Platform-specific version | `references/platform-rules.md` |
| Website formatting / quick commands | `references/website-format.md` |
| Quick command only (highlights, dd bullets, terms, slug, tags) | `references/website-format.md` |

---

## Quick Commands

These are copy-related shortcuts handled by this skill:

| Command | What it does |
|---------|-------------|
| "create LandSearch version" | Generate LandSearch compliant title + description |
| "image suggestions" | Suggest photo sequence for the listing |
| "Landmodo buckets" | Recommend buyer-intent bucket categories |

Website formatting commands ("I need the highlights", "improve this copy and give it
in 5 paragraphs", "give me 9 dd bullets", "give me terms", "suggest a slug",
"filter tags") are handled by the **dealflow-website-listing** skill.

These always reference the current listing context from the conversation.
If no listing context exists yet, ask for property details first.

---

## Full Listing Workflow

When the user wants to create a new listing from scratch, follow these phases in order.
Each phase requires user input before moving to the next. Do not skip ahead.

### Phase 1: Collect Property Details

Ask for:
- County and State
- Lot size and APN
- Zoning and land use rules
- Utilities status
- Road access (paved/dirt)
- HOA / MRID fees
- Any known property flaws ("dirty laundry")
- Proximity to towns, lakes, attractions
- Any unique selling points
- Deal type: Cash, Terms, or Both

If the user provides links to existing listings, read them and extract details.
Never invent facts. If something is missing, ask.

**County-Specific Defaults:**
- **Izard County, AR:** Electricity typically on street. Water and sewer are not promised -
  most lots require septic and a well when building. This is standard for the area.
  MRID applies ($80/lot/year). No HOA.
- **MRID** stands for Municipal Recreation Improvement District - a special district
  established by municipalities in Arkansas to fund, enhance, and manage recreational
  facilities and infrastructure. Common in areas like Horseshoe Bend, AR - covers
  parks, golf course, kayaking, boating, and similar amenities. Always use the full
  name "Municipal Recreation Improvement District" when first referencing MRID in any
  listing copy.

### Phase 2: Avatar Research

Read `references/avatar-categories.md` for the full avatar framework.

Based on county, state, price range, and deal type:
1. Research the area online (use web search if available)
2. Identify emotional drivers, fears, desires, and dreams of likely buyers
3. Assign 1-3 avatar categories with reasoning
4. Present the avatar options and let the user choose which to focus on

The chosen avatar drives all copy decisions from here forward.

### Phase 3: Generate Titles (10-15)

Ask for property highlights if not already collected (large lot, lake proximity, utilities,
unrestricted use, RV allowed, etc.).

Generate 10-15 titles grouped into these creative directions:

- **Curiosity** - makes the reader need to know more
- **Pattern Interrupt** - breaks expectations, surprises
- **Storytelling** - paints a scene or moment
- **Visual** - creates a vivid picture in the mind
- **Bold / Provocative** - challenges, confronts, dares
- **Poetic / Magnetic** - rhythm, cadence, beauty in few words

Mix and match across these categories. Not every listing needs all six - pick the
directions that fit the property and avatar best. Minimum 3 different directions per batch.

**CRITICAL TITLE RULES:**

Titles must be creative, unexpected, and scroll-stopping. Every title should feel like
it was written by a human copywriter, not a real estate bot.

- Lead with emotion, dream, curiosity, or the avatar's desire - NEVER with property specs
- Property details (acreage, zoning, lot count) belong in the body copy, not the headline
- Use curiosity gaps, storytelling, pattern interrupts, bold provocations, visual language
- Never generic. Never template-sounding. Never boring.
- 5-15 words each
- Include a one-line explanation for each
- All titles in English regardless of conversation language

**What makes a bad title:** "1.8 Acres on Two Connected Lots Near Crown Lake"
(This is a description, not a title. It reads like a spreadsheet row.)

**What makes a good title:** "The Only Thing Between You and Crown Lake Is One Street and a Decision"
(This creates curiosity, positions the offer, and speaks to the avatar's desire.)

Ask the user to select one title to build the ad around.

### Phase 3.5: Hero Image Title + Subtitle

After the user selects a listing title, generate 4-5 hero image text options.

This text goes as an overlay on the first listing image (the hero image). Each option has:
- **Title:** 3-5 strong words
- **Subtitle:** 3-5 strong words

Both must match the emotional direction of the chosen listing title. They are not a
summary of the property - they are a visual hook that pulls the viewer in.

Present options and let the user choose.

### Phase 4: Collect Pricing

Confirm deal type (Cash, Terms, or Both), then collect:

**For Terms:** Down Payment, Terms (months), Monthly Payment, Annual Property Tax,
Monthly Note Fee, Document Fee, HOA (monthly or annually)

**For Cash:** Full Cash Price, Down Payment, Document Fee, Annual Property Tax,
HOA (monthly or annually)

Remember: when the user pastes numbers, the order is always:
Down Payment Amount, Terms (months), Cash Price, Monthly Payment, Annual Property Tax,
Monthly Note Fee, Document Fee (one time).

Also collect: APN, Lot Size, and confirm all property highlights are complete.

The money-back guarantee is always 35 days. Do not ask the user for the period -
it is fixed at 35 days for all counties. This covers the first monthly payment plus
five days after.

### Phase 5: Write the Ad Copy

This is the core output. Read both reference files before writing:
1. `references/hormozi-framework.md` - for the persuasion engine
2. `references/copywriting-playbook.md` - for the structural framework

#### Copy Architecture

The copy MUST strictly follow the full Slippery Slide structure powered by Hormozi
psychology. No shortcuts. No lazy summaries. Every sentence earns the next sentence.
Storytelling and emotion dominate. Property specs appear only as logical justification
AFTER the emotional case is built.

**The copy should be long-form, creative, and immersive.** Think magazine article, not
classified ad. The reader should feel like they are being told a story, not reading a
spec sheet. Vary sentence length dramatically - one word, then fifteen. Create rhythm.
Create momentum. Make them unable to stop reading.

**Opening (Hook):**
- First sentence exists ONLY to get them to read the second sentence
- Short, punchy, impossible to ignore
- Create a curiosity gap - hint at a benefit revealed later
- Address the avatar's internal dialogue immediately
- NEVER open with property specs or location facts

**Body (The Slide):**
- Many short paragraphs - most are 1-3 sentences each
- Some paragraphs can be 5-10 sentences when building momentum
- Sentences: 1-15 words each, dramatically varied rhythm
- Short sentences create punch. Longer ones paint pictures.
- Emotion and storytelling FIRST - make the reader feel something
- Specs and details only AFTER emotional investment is built
- Every paragraph must leave the reader with a question in their mind
- Every paragraph must compel the reader to read the next
- Use bucket brigades sparingly and naturally ("But here is the thing -", "And here is
  what most people miss.")
- Address dirty laundry honestly in the middle section - builds massive trust
- The transition from storytelling to specs should feel seamless, not abrupt

**Visual Formatting:**
- The output must be ready for direct copy-paste into a listing platform
- Use bold (**text**) for key emotional lines, transition phrases, and pricing highlights
- Mix bold and regular paragraphs for visual rhythm - not everything is bold
- Each sentence or short group of sentences gets its own line/paragraph
- The copy should look open, airy, and scannable - not a wall of text
- No HTML tags in the main ad copy output (save HTML for website-format commands only)

**Apply all Hormozi tools in every listing:**
- Value Equation: increase dream outcome + certainty, decrease risk + friction
- Answer the 5 Questions: What can I do with it? Why is this safe? Why this lot?
  Why now? What is the easiest way to buy?
- Price Anchoring: show the original/market price vs your price
- Ethical Scarcity: real, believable scarcity - not fake urgency
- Risk Reversal: 35-day money-back guarantee, "verify with county", clear disclosures
- "Use Now / Build Later" framing when applicable
- Positioning over Features: sell control, time, optionality
- Remove Fear over Adding Hype: address confusion, uncertainty, hidden risks
- Clarity over Cleverness: 7th-9th grade reading level

**Apply Slippery Slide techniques:**
- Every sentence must make the next sentence irresistible to read
- Address dirty laundry honestly - builds trust and lowers guard
- Sell the Concept (future lifestyle), not the Product (dirt)
- Use Specific Knowledge - real details, not generic claims
- Features serve as logical justification for the emotional decision already made
- Sensory language from the Environment Palette (only if authentic)
- Curiosity gaps between paragraphs - leave open loops

**Pricing Section (comes AFTER the full story):**
- Transition naturally from the emotional case to the offer
- Present terms clearly and simply
- Apply price anchoring
- Include the 35-day money-back guarantee as risk reversal

**Closing (CTA):**
- Assumptive close - natural progression, not a plea
- Clear CTA to contact the seller
- Final urgency line (ethical, believable)
- End with an emotional callback to the hook or the avatar's dream

**CTA Buttons (Required):**
Include exactly 2 CTA button texts in the copy. These are bold, bracketed action lines
that the user will turn into clickable buttons with a down payment hyperlink behind them.

- **First CTA button:** Place just after the pricing section, before the closing questions.
  Direct and clear - tells the buyer exactly what happens when they click.
  Example: **[ Secure Your Lot - Pay $197 Down Payment Now ]**

- **Second CTA button:** Place at the very end of the listing, after the final emotional line.
  More urgent or emotional - reinforces the offer one last time.
  Example: **[ Claim These Two Lots - $197 Gets You Started ]**

Rules for CTA button text:
- Always include the specific down payment dollar amount
- Action-oriented verb first (Secure, Claim, Lock In, Start, Reserve)
- Keep under 10 words
- Never generic ("Click Here" or "Buy Now") - always specific to this deal
- Vary the two buttons - do not repeat the same text

#### Pricing Summary Format

Always include at the end:

Pricing Summary:
- Down Payment: $___
- Monthly Payment: $___ for ___ months
- Cash Price: $___
- Doc Fee: $___
- Property Tax: $___/year
- HOA: $___ (monthly/annually) [if applicable]
- MRID: $___ [if applicable]

#### Style Rules

- Sentences 1-15 words, dramatically varied rhythm
- Short sentences punch. Longer ones paint the picture.
- Most paragraphs are 1-3 sentences - keep it open and airy
- Some paragraphs can be longer (5-10 sentences) for momentum sections
- Bold key emotional lines, transitions, and pricing highlights
- Total copy: long-form storytelling - not a classified ad
- Every sentence must earn the next sentence
- Every paragraph must leave an open question in the reader's mind
- Output must be ready for direct copy-paste into listing platforms
- Use empowerment words: Freedom, Legacy, Roots, Simplicity, Escape
- Neutralize fear words: address Regret, Instability, Failure, Uncertainty head-on
- Never invent facts
- No em dashes - use hyphens with spaces or rephrase
- Natural human writing - no marketing oversell, no cliches, no filler
- All ad content in English regardless of conversation language
- Write like a human copywriter, not a real estate bot
- 35-day money-back guarantee is the default for all counties
- Always include 2 CTA buttons with specific down payment amount

#### After Presenting the Ad

Add this note:
> "This version is optimized for unrestricted listing platforms (Land.com, Landmodo, Landflip,
> Landwatch). It is not suitable for LandSearch.com - you can request a compliant version."

### Phase 6: Image Suggestions (Two Steps)

After presenting the ad, ask:
> "Would you like image suggestions for this listing?"

If yes, deliver in TWO SEPARATE STEPS. Do not combine them.

#### Step 1: Hero Image Brief

Provide everything needed to build the hero image in the Social Post Builder
(image.dealflowland.com). Output all of the following:

**Hero Title:** (remind the user of the chosen title from Phase 3.5)
**Hero Subtitle:** (remind the user of the chosen subtitle from Phase 3.5)

**AI Image Prompt:** Write a descriptive prompt for Nano Banana / Gemini image generation.
Describe the scene, mood, lighting, angle, and atmosphere. Match the avatar's dream and
the listing's emotional direction. Be specific and visual.

**Suggested Land Type Tags:** Pick the relevant tags from this list:
Desert, Wooded, Mountain, Hilltop, Lakefront, Riverfront, Waterfront, Coastal, Rural,
Farmland, Pasture, Recreational, Off-grid, Hunting, Camping, Cleared, Flat, Sloped,
Forested, Valley, Creekfront, Ocean-view, Red rock, Timberland, Corner lot

**Suggested Land Use Tags:** Pick the relevant tags from this list:
Residential, Agricultural, Recreational, Commercial, Industrial, RV Use, Camping,
Mobile home, Manufactured Home, Tiny house, Livestock, Hunting, Trailers, Off Grid,
Road access, Utilities Nearby

**US State:** The state for this listing

**Badge:** Recommend which badge to apply on the hero image. Choose one:
- **Surrounding** - image shows the surrounding area, not the actual lot
- **Street** - image is from Google Street View or actual road/lot photo
- **Lifestyle** - image is an atmosphere/aspirational scene, not the real property
- **Distance** - image shows distance from the lot to a specific place

Wait for the user to confirm or adjust before moving to Step 2.

#### Step 2: Remaining Images (Images 2+)

After the hero image is confirmed, provide the rest of the image list.
The hero image is NOT repeated here. Start from image 2.

Provide concrete, specific photo suggestions in this storytelling sequence:

- **Images 2-3** - Satellite or map views showing parcel shape, location, and
  proximity to key features (lake, town, etc.)
- **Images 4-5** - On-ground shots of the land and surrounding area (terrain,
  tree coverage, road frontage, lot boundaries, scale)
- **Image 6** - Neighborhood context (nearby homes or built lots - proves
  people already chose this spot)
- **Images 7-8** - Local attractions and points of interest (lake, parks, trails,
  recreation, town amenities)
- **Last image** - Aspirational lifestyle photo matching the avatar's dream
  (home on wooded lot, family porch scene, lake evening, etc.)
- If more slots available, add from any category

Each suggestion should be specific to this property and avatar, not generic.

#### Step 3: AI Video Brief

After the image list is confirmed, provide a video generation brief with two parts:

**Part 1 - Starting Point Image:**
Describe which image from the listing set (hero, satellite, on-ground, lake, lifestyle)
should be used as the starting frame for the AI video generator. Explain why this image
works best as a starting point - it should be the most cinematic and emotionally rich
image available, with enough visual depth for motion to feel natural.

**Part 2 - Video Prompt:**
Write a detailed AI video generation prompt that:
- ALWAYS starts with: "Photo-realistic, ultra-realistic cinematic drone footage."
- Describes camera movement as drone movement (slow aerial drift, low-altitude
  forward glide, sweeping reveal, ascending pull-back, etc.)
- The video must look indistinguishable from real drone footage - no AI artifacts,
  no painterly look, no fantasy elements
- Describes what changes in the scene (light shifts, wind in trees, water movement, etc.)
- Sets the mood and atmosphere (time of day, weather, feeling)
- Keeps it grounded and realistic - real-world physics, real lighting, real textures
- Targets 5-10 seconds of generated video
- Is specific to this property's location, terrain, and avatar dream

The video should feel like professional real estate drone footage capturing
a cinematic moment from the buyer's future life on this land.

### Phase 7: Platform Variants

After the main ad, offer platform-specific versions in this order:

1. **LandSearch** - ask: "Would you like a LandSearch.com compliant version?"
   Read `references/platform-rules.md` for compliance rules. Push creative edge.
2. **Landmodo Buckets** - ask: "Would you like Landmodo bucket suggestions?"
   Recommend which of the 4 buckets apply with reasoning.
3. **Facebook Marketplace** - shorter, more casual version (if requested)
4. **SMS version** - ultra-short hook for outbound (if requested)

Work through each variant the user requests before moving to Phase 8.

### Phase 8: Full Listing Compilation

This is the final step of the listing copy workflow. Before moving to website formatting,
compile ALL approved outputs from the entire workflow into ONE single reply.

Present everything in order, word for word, exactly as approved - do not change,
edit, rephrase, or summarize anything. This is a clean reference document of every
deliverable produced during the workflow.

**Compilation order:**

1. **Listing Title** - the chosen title from Phase 3
2. **Hero Image Title + Subtitle** - from Phase 3.5
3. **Main Ad Copy** - the full approved listing copy from Phase 5 (with CTA buttons)
4. **Pricing Summary** - as presented in Phase 5
5. **Hero Image Brief** - AI prompt, tags, badge, and state from Phase 6 Step 1
6. **Remaining Image Suggestions** - from Phase 6 Step 2
7. **AI Video Brief** - starting image + video prompt from Phase 6 Step 3
8. **LandSearch Version** - title + description from Phase 7 (if created)
9. **Landmodo Buckets** - from Phase 7 (if created)
10. **Any other platform variants** - from Phase 7 (if created)

After presenting the full compilation, ask:
> "Everything is compiled. Ready to format this for the Dealflow website?"

If yes, this triggers the **dealflow-website-listing** skill, which takes the compiled
copy and distributes it into the WordPress/Elementor field format for DealflowLand.com.
Pass all listing context from this conversation to that skill.

---

## Signing

All listing-related messages sign off as "Dealflow" - not "Matt" or the full LLC name.

---

## What This Skill Does NOT Do

- Does not offer land improvements - buyers are responsible for them
- Does not include improvement details in listings - only available use and zoning
- Does not fabricate property details - asks for clarification instead
- Does not use fake urgency or hype tactics
