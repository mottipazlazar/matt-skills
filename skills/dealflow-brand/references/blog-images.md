# DealFlow — Blog & Website Images

## Assets to Study First
- `assets/blog-images/` — real published blog image examples
- `assets/overlay-examples/` — overlay style reference

---

## Specs

| Type | Dimensions | Use |
|------|-----------|-----|
| Hero / Featured | 1600 × 900 | Top of blog post |
| Thumbnail | 800 × 450 | Blog listing grid, social sharing |
| In-post wide | 1200 × 675 | Mid-article full-width |
| Email image | 600 × 338 | Newsletter content block |

---

## Blog Hero Image

```
[Full-bleed landscape photo]
[Dusty Pine tint — 35–45% opacity]
[Category label top-left — Neue Montreal Bold, Harvest Gold]
[Title — Ethereal Bold, large, Warm White, lower third]
[Harvest Gold rule beneath title]
[Logo — top-right, small, white variant]
```

```python
from PIL import Image, ImageDraw
import os, sys
sys.path.insert(0, os.path.join(os.path.dirname(__file__), ".."))
from references.image_overlays import font, logo, DUSTY_PINE, HARVEST_GOLD, WARM_WHITE

def create_blog_hero(photo_path, title, category=None, output_path="blog_hero.jpg"):
    img = Image.open(photo_path).convert("RGBA").resize((1600, 900), Image.LANCZOS)
    W, H = 1600, 900

    # Dusty Pine tint
    tint = Image.new("RGBA", (W, H), (*DUSTY_PINE, int(255 * 0.40)))
    img  = Image.alpha_composite(img, tint)
    draw = ImageDraw.Draw(img)
    m    = 80

    # Category label
    if category:
        fc = font("NueMontreal", "Bold", 24)
        draw.text((m, 60), category.upper(), font=fc, fill=(*HARVEST_GOLD, 255))

    # Title (with basic word-wrap)
    ft = font("Ethereal", "Bold", 72)
    words = title.split()
    lines, line = [], []
    for w in words:
        test = " ".join(line + [w])
        bbox = draw.textbbox((0,0), test, font=ft)
        if (bbox[2] - bbox[0]) < W - m*2:
            line.append(w)
        else:
            lines.append(" ".join(line))
            line = [w]
    lines.append(" ".join(line))

    ty = 560
    for ln in lines:
        draw.text((m, ty), ln, font=ft, fill=(*WARM_WHITE, 255))
        bbox = draw.textbbox((0,0), ln, font=ft)
        ty += (bbox[3] - bbox[1]) + 8

    # Gold rule
    draw.rectangle([(m, ty+12), (m+500, ty+16)], fill=(*HARVEST_GOLD, 255))

    # Logo top-right
    try:
        lg = Image.open(logo("horizontal-white")).convert("RGBA")
        lw = 160
        lh = max(int(lg.height*(lw/lg.width)), 15)
        lg = lg.resize((lw, lh), Image.LANCZOS)
        img.paste(lg, (W - lw - m, 40), lg)
    except FileNotFoundError:
        pass

    img.convert("RGB").save(output_path, quality=92)
    return output_path
```

---

## Blog Thumbnail

```python
def create_blog_thumbnail(photo_path, title, output_path="thumbnail.jpg"):
    from PIL import Image, ImageDraw
    from references.image_overlays import font, DUSTY_PINE, WARM_WHITE
    img  = Image.open(photo_path).convert("RGBA").resize((800, 450), Image.LANCZOS)
    W, H = 800, 450

    ov = Image.new("RGBA", (W, H), (0,0,0,0))
    d  = ImageDraw.Draw(ov)
    for i in range(250):
        d.rectangle([(0, 200+i),(W,201+i)], fill=(*DUSTY_PINE, int(200*(i/250))))
    img  = Image.alpha_composite(img, ov)
    draw = ImageDraw.Draw(img)
    fn   = font("Ethereal", "Bold", 38)
    draw.text((40, 300), title, font=fn, fill=(*WARM_WHITE, 255))
    img.convert("RGB").save(output_path, quality=90)
    return output_path
```

---

## In-Post Image Treatments

**Option A — Clean photo:** Use as-is; add subtle Dusty Pine tint (15–20%) if colors clash.

**Option B — Caption bar:**
```python
draw.rectangle([(0, H-60),(W, H)], fill=(*DUSTY_PINE, 200))
draw.text((20, H-45), caption, font=font("NueMontreal","Regular",18),
          fill=(*WARM_WHITE, 255))
```

**Option C — Pull quote:**
```python
bx, by = W//4, H//3
draw.rectangle([(bx,by),(W-bx,H-by)], fill=(*TAUPE, 180))
draw.text((bx+30, by+20), f'"{quote}"',
          font=font("Ethereal","LightItalic",36), fill=(*WARM_WHITE, 255))
```

---

## Image Style Rules
- Wide, open landscapes — never generic office / people stock photos
- Mood: expansive, peaceful, full of possibility
- Color harmony: natural greens and warm earthy tones
- All blog images should feel like they belong to the same visual world
- Reference: `assets/blog-images/` for established style
