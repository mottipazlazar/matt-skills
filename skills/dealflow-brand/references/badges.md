# DealFlow — Badge Icons

## Asset Location
All badge files are in: `assets/badges/`

List available badges before using:
```python
import os
badges = os.listdir("assets/badges/")
print(badges)
```

---

## When to Use Badges
- Property feature callouts (road access, flat terrain, utilities, views)
- Deal quality signals (Best Value, New Listing, Price Reduced)
- Trust markers (Verified, Owner Financed, No HOA)

---

## Placement by Format

| Format | Position | Size |
|--------|----------|------|
| Instagram Post (1080×1080) | Bottom-right or top-left | ~150px |
| Property Flyer | Corner or beside key stat | ~200px |
| Story (1080×1920) | Corner | ~180px |
| Word document | Inline / sidebar | ~80px |
| Slide (pptx) | Corner or stat card | ~1.0" |
| Email header | Right of logo | ~60px |

Maintain at least 20px clearance from edges and other elements.

---

## Color Rules
- Use badges in Dusty Pine `#3F6B55` or Taupe `#635752`
- On dark backgrounds: use white variant if available
- ❌ Never recolor to non-brand colors

---

## Python: Single Badge

```python
from references.image_overlays import add_badge

add_badge(
    image_path="photo.jpg",
    badge_filename="badge-road-access.png",  # filename inside assets/badges/
    position="bottom-right",
    size_px=150,
    output_path="output.png"
)
```

---

## Python: Badge Strip (multiple features)

```python
from PIL import Image
import os

def add_badge_strip(image_path, badge_filenames, output_path="output.png"):
    """Centered horizontal strip of badges along the bottom."""
    BADGES_DIR = "assets/badges/"
    img = Image.open(image_path).convert("RGBA")
    W, H = img.size
    badge_size = int(W * 0.10)
    spacing = 20
    margin  = 40

    badges = []
    for fn in badge_filenames:
        b = Image.open(os.path.join(BADGES_DIR, fn)).convert("RGBA")
        b = b.resize((badge_size, badge_size), Image.LANCZOS)
        badges.append(b)

    total_w = len(badges) * badge_size + (len(badges)-1) * spacing
    x = (W - total_w) // 2
    y = H - badge_size - margin

    for b in badges:
        img.paste(b, (x, y), b)
        x += badge_size + spacing

    img.convert("RGB").save(output_path, quality=95)
    return output_path

# Example:
# add_badge_strip("photo.jpg",
#     ["badge-road-access.png", "badge-flat.png", "badge-utilities.png"])
```

---

## In Presentations

```javascript
// pptxgenjs
slide.addImage({
    path: "assets/badges/badge-verified.png",
    x: 8.5, y: 6.2, w: 0.9, h: 0.9
});
```

## In Word Documents

```python
from docx.shared import Inches
p = doc.add_paragraph()
run = p.add_run()
run.add_picture("assets/badges/badge-verified.png", width=Inches(0.5))
run.add_text("  Owner Financed Available")
```
