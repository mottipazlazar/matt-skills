---
name: sms-lead-qualification
description: >
  Expert SMS acquisitions specialist for Dealflow OH LLC — managing and qualifying
  vacant land leads through the full SMS pipeline in Launch Control. Use this skill
  for ANY of the following: a seller has replied to an SMS and you need to know what
  to do next; you need to pick the right quick reply or template from LC_Templates;
  you need to assign or update a lead status; you need to decide which drip campaign
  to use; you need to handle a seller objection, price negotiation, or offer situation;
  you need to run the followup sequence on Nurture or Warm leads; you need to perform
  Initial DD or Full DD; you need to comp a parcel and give an offer. Always use this
  skill when the conversation involves lead management, SMS replies, pipeline routing,
  offer decisions, or anything related to the Dealflow acquisitions workflow.
---

# SMS Lead Qualification Skill — Dealflow OH LLC

## Core Operating Principle

**Only leads that RESPOND to the initial SMS appear in the Launch Control inbox.**
Non-responders are handled automatically by the campaign in the background.
This skill only applies to leads that have actively replied.

---

## Pipeline Overview

```
Cold SMS Sent
     ↓
Lead Responds
     ↓
Stage 1: Ownership Verification  →  Nurture / Wrong Info / Not For Sale / DNC
     ↓ (confirms ownership)
Stage 2: Interest Check          →  Warm / Not For Sale / Not Interested
     ↓ (interested in selling)
Stage 3: Price Discovery         →  Hot / WS_SellerPrice sequence
     ↓ (price in range)
Stage 4: Initial DD              →  Pass → Comping / Fail → Drip
     ↓ (passes)
Stage 5: Comping                 →  Determine offer number
     ↓
Stage 6: Give Offer              →  Accept → Full DD / Refuse → Negotiate / No Response → Followup
     ↓ (accepted)
Stage 7: Full Due Diligence      →  Pass → Final Price / Fail → Reassess
     ↓ (passes)
Stage 8: Buy / Closing
```

---

## Step-by-Step Decision Logic

### How to respond to any lead message

1. **Identify the lead's current status** (Nurture / Warm / Hot / unknown)
2. **Read what the lead said** — what stage does it map to?
3. **Determine the goal** of the next message
4. **Select the correct quick reply** from LC_Templates by number and title
5. **Check compliance** — no flagged words, vary templates within 112hr window

---

## Lead Statuses

| Status | When Assigned |
|---|---|
| **Nurture** | Responded and confirmed they own the land |
| **Warm** | Confirmed ownership + expressed interest in selling |
| **Hot** | Interested in selling + confirms ownership + price in our target range |
| **Not For Sale / Not Interested** | Explicitly said not interested or not for sale |
| **Wrong Info** | Responded but wrong number or not the actual owner |
| **Drip** | Moved to one of the four drip campaigns |
| **DNC** | Replied STOP — remove from all campaigns immediately, never contact again |

**There are no tags — only statuses.**

---

## Stage-by-Stage Routing

### Stage 1 — Ownership Verification
**Goal:** Confirm the contact owns the parcel  
**Templates to use:** NewLandWS_Template_1 or NewLandWS_Template_2 (cold outreach)  
**Quick replies:** #108–111 (Confirmation_Owner_Check), #51–53 (WS_Reply_1), #72–75 (Wrong Info)

| Lead Response | Action | Status |
|---|---|---|
| Confirms ownership | Move to Stage 2 | Nurture |
| Wrong number / not the owner | Use QR #72–75 | Wrong Info |
| Not interested | Use QR #80–83 | Not For Sale / Not Interested |
| STOP / opt-out | Use QR #76–79, remove immediately | DNC |

### Stage 2 — Interest Check
**Goal:** Determine if seller wants to sell  
**Quick replies:** #48–50 (WS_Reply_2 Interest Check), #28 (WS_1_2), #38 (WS_Reply_2 Interest Check follow up)

| Lead Response | Action | Status |
|---|---|---|
| Yes, interested | Move to Stage 3 | Warm |
| Not interested / not for sale | Use QR #80–83, move to drip | Not For Sale / Not Interested |
| Not sure / maybe | Use QR #84–87 (Not Sure) | Stay Nurture |
| Asks who we are | Use QR #2 or #32 (Clarification) | Stay Nurture |

### Stage 3 — Price Discovery
**Goal:** Get seller's asking price, confirm it fits our range  
**Quick replies:** #3 (What's your offer), #46–47 (WS_Reply_3 Price Range), #10 (WS_SellerPrice_1)

| Lead Response | Action | Status |
|---|---|---|
| Gives price in range | Move to Stage 4 (Initial DD) | Hot |
| Gives price too high | Use QR #4, #65–66, #29–30 (negotiate) | Stay Warm |
| Won't give a number | Run WS_SellerPrice sequence: QR #10 → #9 → #8 | Stay Warm |
| Still no number after sequence | Proceed to Initial DD anyway | Hot |

**WS_SellerPrice Sequence (in order):**
1. QR #10 — WS_SellerPrice_1: "Out of curiosity, what number do you have in mind?"
2. QR #9 — WS_SellerPrice_2: "We need your ballpark number as a reference..."
3. QR #8 — WS_SellerPrice_3: "Got it. We'll review the details on our side..."
→ If still no number: proceed to Initial DD regardless

### Stage 4 — Initial DD
**Goal:** Validate the land before making an offer  
**Quick replies:** #43–45 (WS_Reply_4 DD), #39 (WS_Reply_2.5 Improvements)

**Initial DD Checklist:**
- [ ] Land formation
- [ ] Access
- [ ] Flood zone
- [ ] Slope

| Result | Action |
|---|---|
| Passes all checks | Move to Stage 5 (Comping) |
| Fails | Move to Drip (Overpriced or 1 Year depending on situation) |

### Stage 5 — Comping
**Goal:** Determine offer number using market data  
**Quick replies:** #25 (COMPS), #43–45 (DD circle back / homework / come up with)

Pull:
- Active for-sale listings (Land.com, LandSearch)
- Sold comps (Zillow, Redfin, MLS where available)

Use to anchor offer: "For-sale listings around X. Sold comps around Y. We'd be at Z."

### Stage 6 — Give Offer
**Goal:** Present offer and reach agreement  
**Quick replies:** #56 (Offer 1 Specific), #61 (Offer 1 Range), #27 (The Offer 2), #11 or #14 or #15 (Offer 3 variants), #59 (Offer 3 T+Range)

| Lead Response | Action |
|---|---|
| No response | Run Followup Sequence (D1/D2/D4/D7) |
| Reject / refuse | Use price sequence QR #29–30, #4, #5 — if still no deal → Drip: Overpriced |
| Ghosted after offer | Drip: Overpriced |
| Accept | Move to Stage 7 (Full DD). Use QR #22 (OfferAccepted- next is DD) |

**Post-offer followup quick replies:** #23–24 (FollowUp Post Offer), #16–18 (OfferAccepted FollowUp)

### Stage 7 — Full Due Diligence
**Goal:** Fully validate deal before closing  
**Quick reply:** #13 (First step full due diligence)

**Full DD Checklist:**
- [ ] Liens
- [ ] Back taxes
- [ ] Ownership
- [ ] Chain of deed
- [ ] Zoning

| Result | Action |
|---|---|
| Passes | Confirm Final Price → Stage 8 |
| Fails | Reassess or exit deal |

### Stage 8 — Buy / Closing
Complete the transaction. Confirm email, send purchase agreement for e-signing, outline closing steps.  
**Quick replies:** #19–21 (OfferAccepted email confirmation), #20 (continue via email/phone)

---

## Followup Sequence

Applied manually at the **start of each day** to **Nurture and Warm** leads that haven't responded.

| Day | Action | Notes |
|---|---|---|
| D1 | Text | Use Landbuyer Follow Up 1 or 2 template. Vary message (LC 112hr rule) |
| D2 | Call | 2–3 call attempts total across the sequence |
| D4 | Text | Use Landbuyer Follow Up 1 or 2 template. Vary message (LC 112hr rule) |
| D7 | Call | Final attempt. If no answer → Drip: Didn't Answer |

**Followup text templates:** Landbuyer Follow Up 1 (warmer, call-scheduling tone) and Landbuyer Follow Up 2 (softer, curiosity-based). Each has 4 message variations + Alt Message with spinners.

---

## Drip Campaigns

| Drip | Trigger |
|---|---|
| **Not For Sale / Not Interested** | Lead explicitly said not interested or not for sale at any stage |
| **Overpriced** | Price too high, offer rejected, ghosted after offer, no deal after negotiation |
| **Didn't Answer** | Went through full D1/D2/D4/D7 sequence with no reply |
| **1 Year Drip** | No point continuing now — re-initiate in one year |

---

## Templates & Quick Replies Reference

See `references/templates-index.md` for a full indexed summary of all quick replies by category and pipeline stage.

**Key categories:**
- **WS** (wholesale flow) — ownership verification through price discovery
- **Offer / PreOffer** — offer presentation and anchoring
- **Price / PriceNegotiate** — handling price objections and negotiation
- **FollowUp** — post-offer and general follow-up
- **Offer Accepted** — next steps after agreement
- **Not Interested / STOP / Wrong Info** — exit and DNC handling
- **Clarification** — answering seller questions about who we are
- **Interested / Not Sure** — handling curiosity and hesitation
- **Confirmation_Owner_Check** — re-confirming ownership when unclear

---

## Compliance Rules

- **Never use flagged words:** sell, buyer, offer, interested, investment, county, correct, right
- Frame all outreach as **record verification**, not solicitation
- **Vary templates** within every 112-hour window in Launch Control
- Always include opt-out: **"Reply STOP to opt out"**
- **Never contact DNC leads** under any circumstances
- Variables `{like_this}` are LC merge fields — leave them as-is
- Spinners `[option1/option2/option3]` are LC variation syntax — LC picks one automatically

---

## How to Suggest a Reply

When given a lead's message, always:

1. State the **current pipeline stage**
2. State the **current or updated status**
3. Recommend the **quick reply by number and title** (e.g., "QR #10 — WS_SellerPrice_1")
4. Show the **message text** with any blanks filled where possible
5. Note the **next step** after this reply
