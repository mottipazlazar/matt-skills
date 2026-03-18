---
name: dealflow-brand
description: "Apply DealFlow OH brand guidelines to ANY output. Trigger this skill whenever the user asks to create or edit a presentation, document, spreadsheet, social media post, image overlay, property flyer, banner, badge, video thumbnail, blog image, or any visual or written asset for DealFlow OH — even if they don't say 'brand' or 'guidelines'. Always trigger when an image is uploaded (ask what they want done with it). Always trigger for decks, reports, flyers, posts, templates, email graphics, or anything that will appear under the DealFlow name. This skill encodes the full visual identity: colors, typography, logo rules, imagery style, social media templates, badge icons, and layout principles so every output is professional and on-brand."
---

# DealFlow OH — Brand Skill

## Asset Folders (all bundled locally in this skill)

| # | Asset | Folder Path |
|---|-------|-------------|
| 1 | Fonts (Ethereal + Neue Montreal) | `assets/fonts/` |
| 2 | Logo files (all sizes & variations) | `assets/logos/` |
| 3 | Social media assets & graphic examples | `assets/social-media-assets/` |
| 4 | Social media templates guideline | `assets/social-media-templates/` |
| 5 | Social media design style guideline | `assets/social-media-style-guide/` |
| 6 | Blog / website style images | `assets/blog-images/` |
| 7 | Video examples | `assets/videos/` |
| 8 | Overlay examples (study these first!) | `assets/overlay-examples/` |
| 9 | Badge icons | `assets/badges/` |

---

## When an Image Is Uploaded — ALWAYS Do This First

**Step 1:** Use `ask_user_input` to ask what they want:
- Add text overlay (headline, property details, caption)
- Add DealFlow logo overlay
- Both text + logo
- Apply brand color tint/filter
- Add badge icon
- Crop/resize for a specific format
- Create full property listing graphic

**Step 2:** Open `assets/overlay-examples/` and study the files there — match font sizing, gradient depth, color usage, and positioning exactly.

**Step 3:** Apply treatment per [references/image-overlays.md](references/image-overlays.md).

---

## Reference Files by Task

| Task | Reference |
|------|-----------|
| Image overlays, property graphics | [references/image-overlays.md](references/image-overlays.md) |
| Social media posts & templates | [references/social-media.md](references/social-media.md) |
| Badge icons | [references/badges.md](references/badges.md) |
| PowerPoint / presentations | [references/pptx-brand.md](references/pptx-brand.md) |
| Word documents | [references/docx-brand.md](references/docx-brand.md) |
| Excel spreadsheets | [references/xlsx-brand.md](references/xlsx-brand.md) |
| Blog / website images | [references/blog-images.md](references/blog-images.md) |
| Video thumbnails & covers | [references/video-thumbnails.md](references/video-thumbnails.md) |

---

## Color Palette

| Role | Name | HEX | RGB |
|------|------|-----|-----|
| Primary | Taupe | `#635752` | 99 / 87 / 82 |
| Primary | Dusty Pine | `#3F6B55` | 63 / 107 / 85 |
| Secondary | Harvest Gold | `#E5A94D` | 229 / 169 / 77 |
| Secondary | Warm White | `#FFFEF6` | 255 / 254 / 246 |
| Accent | Lemon Grass | `#D9CD25` | 217 / 205 / 37 — **critical highlights only** |
| Accent | Soft Ivory | `#F6F4E3` | 246 / 244 / 227 — backgrounds & text only |

**Usage:** Dusty Pine + Taupe = 60–70% visual weight. Harvest Gold = primary accent. Lemon Grass = reserved for truly critical callouts only.

---

## Typography

### Display / Headlines: **Ethereal**
- Files: `assets/fonts/Ethereal-*.ttf`
- 9 weights: Extra Light → Black
- Use for: titles, headlines, hero text, slide headers, overlay text
- Mixing weights within display: ✅ allowed

### Body / Secondary: **Neue Montreal**
- Files: `assets/fonts/NueMontreal-*.ttf`
- 8 styles: Light through Bold Italic
- Use for: body copy, captions, labels, data, footnotes
- ❌ Do NOT mix styles within body text

### Fallbacks (if TTF files missing)
| Brand Font | Substitute |
|---|---|
| Ethereal | Cormorant Garamond / Playfair Display / Georgia |
| Neue Montreal | DM Sans / Inter / Calibri |

---

## Logo Rules

**Files:** `assets/logos/`

| File | Use When |
|------|----------|
| `logo-horizontal-color.*` | Default — headers, banners, light backgrounds |
| `logo-horizontal-white.*` | Dark or photo backgrounds |
| `logo-horizontal-grey.*` | B&W print |
| `logo-vertical-color.*` | Square formats, social profile |
| `logo-vertical-white.*` | Vertical on dark backgrounds |
| `logo-icon-color.*` | Watermarks, favicons, tiny placements |
| `logo-icon-white.*` | Small icon on dark backgrounds |

**Hard rules:**
- ❌ No distortion, recoloring, rearranging, resizing parts, effects, rotation
- ✅ Minimum 15px height (digital) / 6mm (print)
- ✅ Clear exclusion zone = icon height on all 4 sides

---

## Imagery Style

- Wide, open landscapes — fields, sky, vacant land
- Natural light, golden-hour tones
- Aspirational, spacious — freedom, legacy, possibility
- When tinting: Dusty Pine 40–60% opacity or Taupe 30–50% opacity
- Reference: `assets/overlay-examples/` and `assets/blog-images/`

---

## Badge Icons

**Files:** `assets/badges/`  
See [references/badges.md](references/badges.md) for placement rules.

---

## Brand Voice

**Tagline:** River of Deals  
**Tone:** Trustworthy, aspirational, warm  
**Themes:** Ownership · Legacy · Freedom · Opportunity  
**Avoid:** Corporate coldness, pushy sales language, jargon overload

---

## Pre-Delivery Checklist

- [ ] Colors match exact HEX values
- [ ] Headlines use Ethereal (or approved substitute)
- [ ] Body uses Neue Montreal — no mixing
- [ ] Logo: correct variation for background, exclusion zone respected
- [ ] Lemon Grass used ONLY for truly critical callouts
- [ ] Imagery: wide, natural, aspirational
- [ ] Voice: warm, legacy/freedom-oriented
- [ ] "DealFlow" and "River of Deals" spelled and capitalized correctly
