# DealFlow — Image Overlays & Property Graphics

## Before Starting
Open `assets/overlay-examples/` and study every file there. Match the established style exactly — gradient depth, font sizes, positioning, color usage.

---

## Python Setup

```bash
pip install Pillow --break-system-packages
```

---

## Asset Paths (all local)

```python
import os

SKILL_DIR    = os.path.dirname(os.path.abspath(__file__))
FONTS_DIR    = os.path.join(SKILL_DIR, "assets", "fonts")
LOGOS_DIR    = os.path.join(SKILL_DIR, "assets", "logos")
BADGES_DIR   = os.path.join(SKILL_DIR, "assets", "badges")
EXAMPLES_DIR = os.path.join(SKILL_DIR, "assets", "overlay-examples")

def font(name, weight, size):
    """Load brand font with fallback."""
    from PIL import ImageFont
    path = os.path.join(FONTS_DIR, f"{name}-{weight}.ttf")
    if os.path.exists(path):
        return ImageFont.truetype(path, size)
    # Fallback
    fallback = os.path.join(FONTS_DIR, f"{name}-Regular.ttf")
    if os.path.exists(fallback):
        return ImageFont.truetype(fallback, size)
    return ImageFont.load_default()

def logo(variation="horizontal-color"):
    """Return path to logo file. variation = 'horizontal-color' | 'horizontal-white' | etc."""
    for ext in ["png", "svg", "jpg"]:
        p = os.path.join(LOGOS_DIR, f"logo-{variation}.{ext}")
        if os.path.exists(p):
            return p
    # Try any file matching variation name
    for f in os.listdir(LOGOS_DIR):
        if variation in f.lower():
            return os.path.join(LOGOS_DIR, f)
    raise FileNotFoundError(f"No logo found for variation: {variation}")
```

---

## Brand Colors

```python
DUSTY_PINE   = (63, 107, 85)    # #3F6B55
TAUPE        = (99, 87, 82)     # #635752
HARVEST_GOLD = (229, 169, 77)   # #E5A94D
WARM_WHITE   = (255, 254, 246)  # #FFFEF6
SOFT_IVORY   = (246, 244, 227)  # #F6F4E3
LEMON_GRASS  = (217, 205, 37)   # #D9CD25
```

---

## Canvas Sizes

| Format | Dimensions |
|--------|-----------|
| Instagram Post | 1080 × 1080 |
| Instagram Story / Reel | 1080 × 1920 |
| Facebook Post | 1200 × 630 |
| Facebook Cover | 1640 × 924 |
| LinkedIn Banner | 1584 × 396 |
| Email Header | 600 × 200 |
| Property Flyer (print) | 2550 × 3300 |
| Property Card | 1200 × 800 |
| Blog Header | 1600 × 900 |
| Video Thumbnail | 1280 × 720 |

---

## Text Overlay

```python
from PIL import Image, ImageDraw

def add_text_overlay(image_path, headline, subtext=None,
                     tagline="River of Deals", output_path="output.png"):
    img = Image.open(image_path).convert("RGBA")
    W, H = img.size

    # Dusty Pine gradient — bottom 55%
    ov = Image.new("RGBA", (W, H), (0, 0, 0, 0))
    d = ImageDraw.Draw(ov)
    grad_h = int(H * 0.55)
    for i in range(grad_h):
        alpha = int(210 * (i / grad_h))
        y = H - grad_h + i
        d.rectangle([(0, y), (W, y + 1)], fill=(*DUSTY_PINE, alpha))
    img = Image.alpha_composite(img, ov)
    draw = ImageDraw.Draw(img)

    margin = int(W * 0.055)
    rule_y  = int(H * 0.63)

    # Harvest Gold rule
    draw.rectangle([(margin, rule_y), (margin + int(W*0.35), rule_y + 4)],
                   fill=(*HARVEST_GOLD, 255))

    # Headline — Ethereal Bold
    fh = font("Ethereal", "Bold", int(W * 0.067))
    draw.text((margin, rule_y + 16), headline, font=fh, fill=(*WARM_WHITE, 255))

    # Subtext — Neue Montreal Regular, Harvest Gold
    if subtext:
        fs = font("NueMontreal", "Regular", int(W * 0.033))
        hh = draw.textbbox((0,0), headline, font=fh)
        draw.text((margin, rule_y + 16 + (hh[3]-hh[1]) + 10),
                  subtext, font=fs, fill=(*HARVEST_GOLD, 255))

    # Tagline — bottom right, small italic
    ft = font("NueMontreal", "Italic", int(W * 0.022))
    tb = draw.textbbox((0,0), tagline, font=ft)
    draw.text((W - margin - (tb[2]-tb[0]), H - margin),
              tagline, font=ft, fill=(*HARVEST_GOLD, 200))

    img.convert("RGB").save(output_path, quality=95)
    return output_path
```

---

## Logo Overlay

```python
def add_logo_overlay(image_path, position="top-left",
                     variation="horizontal-white", size_pct=0.18,
                     output_path="output.png"):
    """
    variation: 'horizontal-white' for photos, 'horizontal-color' for light BGs
    position: 'top-left' | 'top-right' | 'bottom-left' | 'bottom-right' | 'center'
    """
    from PIL import Image
    img  = Image.open(image_path).convert("RGBA")
    lgp  = logo(variation)
    lg   = Image.open(lgp).convert("RGBA")
    W, H = img.size

    lw = max(int(W * size_pct), 120)
    lh = max(int(lg.height * (lw / lg.width)), 15)
    lg = lg.resize((lw, lh), Image.LANCZOS)

    m = int(W * 0.04)
    positions = {
        "top-left":     (m, m),
        "top-right":    (W - lw - m, m),
        "bottom-left":  (m, H - lh - m),
        "bottom-right": (W - lw - m, H - lh - m),
        "center":       ((W - lw) // 2, (H - lh) // 2),
    }
    img.paste(lg, positions.get(position, (m, m)), lg)
    img.convert("RGB").save(output_path, quality=95)
    return output_path
```

---

## Brand Color Tint

```python
def apply_brand_tint(image_path, color="dusty-pine",
                     opacity=0.45, output_path="output.png"):
    from PIL import Image
    tints = {"dusty-pine": DUSTY_PINE, "taupe": TAUPE}
    img = Image.open(image_path).convert("RGBA")
    r, g, b = tints.get(color, DUSTY_PINE)
    tint = Image.new("RGBA", img.size, (r, g, b, int(255 * opacity)))
    Image.alpha_composite(img, tint).convert("RGB").save(output_path, quality=95)
    return output_path
```

---

## Full Property Listing Post

```python
def create_property_post(bg_image_path, property_name, price, details,
                         output_path="property_post.png", size=(1080, 1080)):
    from PIL import Image, ImageDraw
    W, H = size
    bg = Image.open(bg_image_path).convert("RGBA").resize((W, H), Image.LANCZOS)

    # Deep Dusty Pine gradient — bottom 60%
    ov = Image.new("RGBA", (W, H), (0,0,0,0))
    d  = ImageDraw.Draw(ov)
    gs = int(H * 0.40)
    for i in range(H - gs):
        d.rectangle([(0, gs+i),(W, gs+i+1)], fill=(*DUSTY_PINE, int(230*(i/(H-gs)))))
    img  = Image.alpha_composite(bg, ov)
    draw = ImageDraw.Draw(img)
    m    = 65

    # Harvest Gold rule
    rule_y = int(H * 0.62)
    draw.rectangle([(m, rule_y), (m + 320, rule_y + 5)], fill=(*HARVEST_GOLD, 255))

    # Property name
    fn = font("Ethereal", "Bold", 68)
    draw.text((m, rule_y + 18), property_name, font=fn, fill=(*WARM_WHITE, 255))
    nh = draw.textbbox((0,0), property_name, font=fn)

    # Price — Harvest Gold
    fp = font("Ethereal", "SemiBold", 54)
    py = rule_y + 18 + (nh[3]-nh[1]) + 8
    draw.text((m, py), price, font=fp, fill=(*HARVEST_GOLD, 255))
    ph = draw.textbbox((0,0), price, font=fp)

    # Details
    fd = font("NueMontreal", "Regular", 30)
    draw.text((m, py + (ph[3]-ph[1]) + 10), details,
              font=fd, fill=(*SOFT_IVORY, 230))

    # Tagline
    ft = font("NueMontreal", "Italic", 22)
    draw.text((m, H - 55), "River of Deals", font=ft, fill=(*HARVEST_GOLD, 200))

    # Logo — top right, white variant
    try:
        lg = Image.open(logo("horizontal-white")).convert("RGBA")
        lw = 190
        lh = max(int(lg.height * (lw / lg.width)), 15)
        lg = lg.resize((lw, lh), Image.LANCZOS)
        img.paste(lg, (W - lw - m, 45), lg)
    except FileNotFoundError:
        pass

    img.convert("RGB").save(output_path, quality=95)
    return output_path
```

---

## Badge Overlay

```python
def add_badge(image_path, badge_filename, position="bottom-right",
              size_px=150, output_path="output.png"):
    """
    badge_filename: name of file inside assets/badges/
    e.g. add_badge("photo.jpg", "badge-road-access.png")
    """
    from PIL import Image
    img   = Image.open(image_path).convert("RGBA")
    badge = Image.open(os.path.join(BADGES_DIR, badge_filename)).convert("RGBA")
    W, H  = img.size
    ratio = size_px / max(badge.width, badge.height)
    bw, bh = int(badge.width*ratio), int(badge.height*ratio)
    badge = badge.resize((bw, bh), Image.LANCZOS)
    margin = 30
    pos = {
        "bottom-right": (W - bw - margin, H - bh - margin),
        "bottom-left":  (margin, H - bh - margin),
        "top-right":    (W - bw - margin, margin),
        "top-left":     (margin, margin),
    }
    img.paste(badge, pos.get(position, pos["bottom-right"]), badge)
    img.convert("RGB").save(output_path, quality=95)
    return output_path
```
