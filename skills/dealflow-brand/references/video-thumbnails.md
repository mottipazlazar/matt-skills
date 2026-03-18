# DealFlow — Video Thumbnails & Covers

## Assets to Study First
- `assets/videos/` — real video examples to match thumbnail style
- `assets/overlay-examples/` — overlay style reference

---

## Specs

| Platform | Dimensions |
|----------|-----------|
| YouTube Thumbnail | 1280 × 720 |
| Facebook / LinkedIn Video | 1280 × 720 |
| Instagram Reel Cover | 1080 × 1920 |
| Instagram Video Post | 1080 × 1080 |

---

## YouTube Thumbnail — Split Panel Layout

```
[Left panel — Dusty Pine solid, ~42% width]
  [Harvest Gold vertical accent bar — 8px, left edge]
  HEADLINE          [Ethereal Bold, Warm White]
  ━━━━━━━━━━━━━━━━  [Harvest Gold rule]
  $XX,XXX           [Ethereal SemiBold, Harvest Gold]
  [Logo bottom-left — white variant]
[Right panel — property photo with light Dusty Pine tint]
```

```python
from PIL import Image, ImageDraw
import os, sys
sys.path.insert(0, os.path.join(os.path.dirname(__file__), ".."))
from references.image_overlays import font, logo, DUSTY_PINE, HARVEST_GOLD, WARM_WHITE

def create_youtube_thumbnail(photo_path, headline, price, output_path="thumb.jpg"):
    W, H = 1280, 720
    canvas = Image.new("RGB", (W, H), DUSTY_PINE)

    # Right photo panel
    photo   = Image.open(photo_path).convert("RGBA").resize((int(W*0.58), H), Image.LANCZOS)
    tint    = Image.new("RGBA", photo.size, (*DUSTY_PINE, 80))
    photo   = Image.alpha_composite(photo, tint)
    canvas.paste(photo.convert("RGB"), (W - photo.width, 0))

    draw = ImageDraw.Draw(canvas)
    lw   = W - photo.width
    m    = 50

    # Gold left accent
    draw.rectangle([(0,0),(8,H)], fill=HARVEST_GOLD)

    # Headline with word-wrap
    fh    = font("Ethereal", "Bold", 64)
    words = headline.split()
    lines, line = [], []
    for w in words:
        test = " ".join(line + [w])
        bbox = draw.textbbox((0,0), test, font=fh)
        if (bbox[2]-bbox[0]) < lw - m*2:
            line.append(w)
        else:
            lines.append(" ".join(line))
            line = [w]
    lines.append(" ".join(line))
    y = 160
    for ln in lines:
        draw.text((m, y), ln, font=fh, fill=WARM_WHITE)
        bbox = draw.textbbox((0,0), ln, font=fh)
        y += (bbox[3]-bbox[1]) + 6

    # Gold rule + price
    draw.rectangle([(m, y+16),(lw-m, y+20)], fill=HARVEST_GOLD)
    fp = font("Ethereal", "SemiBold", 52)
    draw.text((m, y+30), price, font=fp, fill=HARVEST_GOLD)

    # Logo bottom-left
    try:
        lg = Image.open(logo("horizontal-white")).convert("RGBA")
        lw2 = 160
        lh2 = max(int(lg.height*(lw2/lg.width)), 15)
        lg  = lg.resize((lw2, lh2), Image.LANCZOS)
        canvas.paste(lg.convert("RGB"), (m, H-lh2-40), mask=lg.split()[3])
    except FileNotFoundError:
        pass

    canvas.save(output_path, quality=94)
    return output_path
```

---

## Instagram Reel Cover (1080×1920)

```python
def create_reel_cover(photo_path, title, output_path="reel_cover.jpg"):
    from PIL import Image, ImageDraw
    from references.image_overlays import font, logo, DUSTY_PINE, HARVEST_GOLD, WARM_WHITE, SOFT_IVORY
    W, H = 1080, 1920
    img  = Image.open(photo_path).convert("RGBA").resize((W, H), Image.LANCZOS)

    ov = Image.new("RGBA", (W, H), (0,0,0,0))
    d  = ImageDraw.Draw(ov)
    for i in range(960):
        d.rectangle([(0,960+i),(W,961+i)], fill=(*DUSTY_PINE, int(220*(i/960))))
    img  = Image.alpha_composite(img, ov)
    draw = ImageDraw.Draw(img)
    m    = 70

    draw.rectangle([(m,1020),(m+380,1026)], fill=(*HARVEST_GOLD,255))
    ft = font("Ethereal", "Bold", 80)
    draw.text((m,1045), title, font=ft, fill=(*WARM_WHITE,255))
    fta = font("NueMontreal", "Italic", 34)
    draw.text((m,1820), "River of Deals", font=fta, fill=(*HARVEST_GOLD,200))

    try:
        lg = Image.open(logo("horizontal-white")).convert("RGBA")
        lw = 180
        lh = max(int(lg.height*(lw/lg.width)),15)
        lg = lg.resize((lw,lh),Image.LANCZOS)
        img.paste(lg,(W-lw-m,55),lg)
    except FileNotFoundError:
        pass

    img.convert("RGB").save(output_path, quality=93)
    return output_path
```

---

## Text-on-Video Rules
- Minimum 4.5:1 contrast ratio (Warm White on Dusty Pine ✅)
- Text in lower third or left panel — clear of main subject
- Ethereal for any text in video graphics
- Neue Montreal for captions and lower-thirds body text
