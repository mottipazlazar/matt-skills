# DealFlow — Social Media Templates

## Assets to Study First
- `assets/social-media-assets/` — real examples of published posts
- `assets/social-media-templates/` — template files and layouts
- `assets/social-media-style-guide/` — design style rules
- `assets/overlay-examples/` — text/logo overlay reference

Review these before creating any social content to match the established style precisely.

---

## Platform Specs

| Platform | Format | Dimensions |
|----------|--------|-----------|
| Instagram | Feed (square) | 1080 × 1080 |
| Instagram | Feed (landscape) | 1080 × 566 |
| Instagram | Story / Reel Cover | 1080 × 1920 |
| Facebook | Feed Post | 1200 × 630 |
| Facebook | Cover Photo | 1640 × 924 |
| LinkedIn | Post | 1200 × 627 |
| LinkedIn | Banner | 1584 × 396 |
| YouTube | Thumbnail | 1280 × 720 |

---

## Post Templates

### 1. Property Listing Post
```
[Full-bleed landscape photo]
[Dusty Pine gradient — bottom 55%]
━━━━━━━━━━━━━━ [Harvest Gold rule, 35% width]
PROPERTY NAME     [Ethereal Bold, ~62px, Warm White]
$XX,XXX           [Ethereal SemiBold, ~50px, Harvest Gold]
X Acres | County  [Neue Montreal Regular, ~28px, Soft Ivory]
[Logo top-right — assets/logos/logo-horizontal-white.*]
River of Deals    [bottom-left, Neue Montreal Italic, Harvest Gold]
```

### 2. Educational / Tip Post
```
[Soft Ivory background]
[Dusty Pine left border — 8px]
"Did You Know?"   [Neue Montreal Medium, ~22px, Harvest Gold]
━━━━━━━━━━━━━━ [Gold rule]
HEADLINE          [Ethereal Bold, ~52px, Dusty Pine]
Body text...      [Neue Montreal Regular, ~18px, Taupe]
[Logo bottom-right — assets/logos/logo-horizontal-color.*]
```

### 3. Testimonial Post
```
[Dusty Pine full background]
❝                 [Large, Harvest Gold, Ethereal]
"Quote text..."   [Ethereal Light Italic, ~36px, Warm White]
— Customer Name   [Neue Montreal Regular, ~18px, Harvest Gold]
━━━━━━━━━━━━━━
[Logo centered — assets/logos/logo-horizontal-white.*]
```

### 4. Stats / Deal Value Post
```
[Taupe background]
[Stat cards — Dusty Pine fill, Harvest Gold border]
  ┌───────────┐
  │  $45,000  │  [Ethereal Bold, Harvest Gold]
  │ Sale Price│  [Neue Montreal, Warm White]
  └───────────┘
HEADLINE          [Ethereal Bold, Warm White]
[Logo bottom]
```

### 5. Story / Reel Cover (Portrait 1080×1920)
```
[Full-bleed photo — top 60%]
[Dusty Pine solid panel — bottom 40%]
[Harvest Gold rule at join]
HEADLINE          [Ethereal Bold, ~72px, Warm White]
Subtext           [Neue Montreal, ~32px, Soft Ivory]
[Logo top-left — white, small]
CTA text          [Harvest Gold, bottom]
```

### 6. Blog Promo Post
```
[Blog hero image + Dusty Pine tint ~40%]
NEW POST          [Neue Montreal Bold, ~22px, Harvest Gold — label]
BLOG TITLE        [Ethereal Bold, ~60px, Warm White]
Short description [Neue Montreal Regular, ~24px, Soft Ivory]
[CTA: Harvest Gold fill button → "Read More"]
[Logo bottom]
```
Blog images: `assets/blog-images/`

---

## Python: Build Any Social Post

```python
from PIL import Image, ImageDraw
import os, sys
sys.path.insert(0, os.path.join(os.path.dirname(__file__), ".."))
from references.image_overlays import (
    font, logo, DUSTY_PINE, TAUPE, HARVEST_GOLD, WARM_WHITE, SOFT_IVORY
)

SIZES = {
    "instagram":       (1080, 1080),
    "instagram-story": (1080, 1920),
    "facebook":        (1200, 630),
    "linkedin":        (1200, 627),
    "youtube":         (1280, 720),
}

def build_listing_post(bg_path, name, price, details,
                       platform="instagram", output_path="post.png"):
    from references.image_overlays import create_property_post
    return create_property_post(bg_path, name, price, details,
                                output_path=output_path,
                                size=SIZES.get(platform, (1080,1080)))
```

---

## Caption Voice

**Structure:** Hook → Details → CTA → Hashtags

**Example:**
```
Your next chapter starts here. 🌿

5 pristine acres in Luna County, NM — wide open skies,
road access, and priced to make ownership real.

💰 $18,500 | 5.03 Acres | APN: 3062-024-005

Ready to claim your land? DM us or tap the link in bio.

#DealFlowOH #RiverOfDeals #LandForSale #VacantLand #LandInvesting
#BuyLand #OwnYourLand #NewMexicoLand #LandDeal #RealEstate
```
