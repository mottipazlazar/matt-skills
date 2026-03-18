# DealFlow Brand — Word Document Guide

Read `/mnt/skills/public/docx/SKILL.md` for technical python-docx implementation.

## Assets
- Logo for header: `assets/logos/logo-horizontal-color.png`


---

## Style Map

| Style | Font | Size | Color | Use |
|-------|------|------|-------|-----|
| Title | Ethereal Bold | 36pt | `#3F6B55` | Document title |
| Heading 1 | Ethereal SemiBold | 24pt | `#3F6B55` | Major sections |
| Heading 2 | Ethereal Medium | 18pt | `#635752` | Subsections |
| Body | Neue Montreal Regular | 11pt | `#635752` | All body text |
| Caption | Neue Montreal Light Italic | 9pt | `#635752` | Image captions |
| Price | Neue Montreal Bold | 11pt | `#E5A94D` | Prices, key stats |
| Tagline | Ethereal Light Italic | 14pt | `#3F6B55` | Pull quotes |

---

## Colors

```python
from docx.shared import RGBColor
DUSTY_PINE   = RGBColor(0x3F, 0x6B, 0x55)
TAUPE        = RGBColor(0x63, 0x57, 0x52)
HARVEST_GOLD = RGBColor(0xE5, 0xA9, 0x4D)
WARM_WHITE   = RGBColor(0xFF, 0xFE, 0xF6)
SOFT_IVORY   = RGBColor(0xF6, 0xF4, 0xE3)
```

---

## Header & Footer

```python
from docx.shared import Inches, Pt
from docx.enum.text import WD_ALIGN_PARAGRAPH

def apply_brand_header(doc):
    header = doc.sections[0].header
    table  = header.add_table(1, 2, width=Inches(6.5))
    # Logo left
    lp  = table.cell(0,0).paragraphs[0]
    run = lp.add_run()
    run.add_picture("assets/logos/logo-horizontal-color.png", width=Inches(1.6))
    # Tagline right
    rp  = table.cell(0,1).paragraphs[0]
    rp.alignment = WD_ALIGN_PARAGRAPH.RIGHT
    run = rp.add_run("River of Deals")
    run.font.color.rgb = HARVEST_GOLD
    run.font.italic    = True
    run.font.size      = Pt(10)
    run.font.name      = "Neue Montreal"

def apply_brand_footer(doc):
    footer = doc.sections[0].footer
    p      = footer.paragraphs[0]
    p.alignment = WD_ALIGN_PARAGRAPH.CENTER
    run = p.add_run("DealFlow OH  |  River of Deals  |  dealflowoh.com")
    run.font.color.rgb = TAUPE
    run.font.size      = Pt(8)
    run.font.name      = "Neue Montreal"
```

---

## Harvest Gold Divider

```python
from docx.oxml.ns import qn
from docx.oxml import OxmlElement

def add_gold_divider(doc):
    p   = doc.add_paragraph()
    pPr = p._p.get_or_add_pPr()
    pBdr = OxmlElement('w:pBdr')
    bot  = OxmlElement('w:bottom')
    bot.set(qn('w:val'),   'single')
    bot.set(qn('w:sz'),    '6')
    bot.set(qn('w:space'), '1')
    bot.set(qn('w:color'), 'E5A94D')
    pBdr.append(bot)
    pPr.append(pBdr)
    return p
```

---

## Callout Box (Dusty Pine)

```python
def add_callout_box(doc, text):
    table = doc.add_table(rows=1, cols=1)
    cell  = table.cell(0, 0)
    shd   = OxmlElement('w:shd')
    shd.set(qn('w:val'),   'clear')
    shd.set(qn('w:color'), 'auto')
    shd.set(qn('w:fill'),  '3F6B55')
    cell._tc.get_or_add_tcPr().append(shd)
    p   = cell.paragraphs[0]
    run = p.add_run(text)
    run.font.color.rgb = WARM_WHITE
    run.font.name      = "Neue Montreal"
    run.font.size      = Pt(12)
    run.font.bold      = True
    p.paragraph_format.space_before = Pt(8)
    p.paragraph_format.space_after  = Pt(8)
    p.paragraph_format.left_indent  = Inches(0.15)
```

---

## Property Description Template

```
[Logo — assets/logos/logo-horizontal-color.png]
━━━━━━━━━━━━━━━━━━ [Gold divider]

PROPERTY NAME          [Title — Ethereal Bold, 36pt, Dusty Pine]
Location • Acres • Zoning  [Neue Montreal Italic, 12pt, Taupe]

━━━━━━━━━━━━━━━━━━ [Gold divider]

Overview               [Heading 1]
[Body text]

Property Details       [Heading 1]
Price: $XX,XXX         [Harvest Gold for price value]
Acreage / County / Zoning / APN

Why This Property?     [Heading 1]
[Aspirational copy — warm, legacy/freedom tone]

[Callout box — key highlight]

━━━━━━━━━━━━━━━━━━
River of Deals | DealFlow OH   [Footer]
```
