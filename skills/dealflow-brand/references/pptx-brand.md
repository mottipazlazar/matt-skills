# DealFlow Brand — PowerPoint / Presentation Guide

Read `/mnt/skills/public/pptx/SKILL.md` for technical pptxgenjs implementation.

## Assets
- Logos for slides: `assets/logos/` — use `logo-horizontal-white.*` on dark slides, `logo-horizontal-color.*` on light slides

- Social media templates for layout inspiration: `assets/social-media-templates/`

---

## Slide Color System ("Sandwich")

| Slide Type | Background | Primary Text |
|---|---|---|
| Title | Dusty Pine `#3F6B55` | Warm White `#FFFEF6` |
| Content | Soft Ivory `#F6F4E3` | Taupe `#635752` |
| Divider / Section | Taupe `#635752` | Warm White `#FFFEF6` |
| Closing / CTA | Dusty Pine `#3F6B55` | Warm White + Harvest Gold |
| Stat cards | Dusty Pine `#3F6B55` | Harvest Gold numbers, Warm White labels |

---

## Typography

```javascript
const title    = { fontFace:"Ethereal", bold:true,  fontSize:40, color:"FFFEF6" };
const subtitle = { fontFace:"Ethereal", fontSize:24, color:"E5A94D" };
const heading  = { fontFace:"Ethereal", bold:true,  fontSize:28, color:"3F6B55" };
const body     = { fontFace:"Neue Montreal", fontSize:16, color:"635752" };
const caption  = { fontFace:"Neue Montreal", fontSize:11, color:"635752", italic:true };
const price    = { fontFace:"Ethereal", bold:true,  fontSize:36, color:"E5A94D" };
```
Fallbacks: Ethereal → `"Garamond"` | Neue Montreal → `"Calibri"`

---

## Slide Templates

### Title Slide
```javascript
slide.background = { color:"3F6B55" };
slide.addImage({ path:"assets/logos/logo-horizontal-white.png", x:0.4, y:0.3, w:2.5, h:0.8 });
slide.addShape(pptx.ShapeType.rect, { x:0.4, y:3.9, w:9.2, h:0.05, fill:{color:"E5A94D"} });
slide.addText(title,    { x:0.4, y:4.1, w:9.2, fontFace:"Ethereal", bold:true, fontSize:44, color:"FFFEF6" });
slide.addText(subtitle, { x:0.4, y:5.5, w:9.2, fontFace:"Neue Montreal", fontSize:20, color:"E5A94D" });
slide.addText("River of Deals", { x:0.4, y:6.8, w:9.2, fontFace:"Neue Montreal", italic:true, fontSize:13, color:"F6F4E3", align:"right" });
```

### Content Slide (Light)
```javascript
slide.background = { color:"F6F4E3" };
slide.addShape(pptx.ShapeType.rect, { x:0, y:0, w:0.1, h:7.5, fill:{color:"3F6B55"} });
slide.addText(header, { x:0.35, y:0.3, w:9.3, fontFace:"Ethereal", bold:true, fontSize:32, color:"3F6B55" });
slide.addShape(pptx.ShapeType.rect, { x:0.35, y:0.95, w:2.5, h:0.04, fill:{color:"E5A94D"} });
slide.addText(body,   { x:0.35, y:1.15, w:9.3, fontFace:"Neue Montreal", fontSize:16, color:"635752" });
slide.addImage({ path:"assets/logos/logo-horizontal-color.png", x:8.5, y:6.9, w:1.2, h:0.4 });
```

### Property Listing Slide (Two-Column)
```javascript
slide.background = { color:"F6F4E3" };
slide.addImage({ path:propertyPhoto, x:0.3, y:1.0, w:5.0, h:4.8 });
slide.addShape(pptx.ShapeType.roundRect, { x:5.6, y:1.0, w:4.0, h:4.8, fill:{color:"3F6B55"} });
slide.addText(propName, { x:5.8, y:1.3, w:3.6, fontFace:"Ethereal", bold:true, fontSize:24, color:"FFFEF6" });
slide.addShape(pptx.ShapeType.rect, { x:5.8, y:2.1, w:2.0, h:0.04, fill:{color:"E5A94D"} });
slide.addText(price,    { x:5.8, y:2.3, w:3.6, fontFace:"Ethereal", bold:true, fontSize:32, color:"E5A94D" });
slide.addText(details,  { x:5.8, y:3.1, w:3.6, fontFace:"Neue Montreal", fontSize:14, color:"F6F4E3" });
// Optional badge
slide.addImage({ path:"assets/badges/badge-road-access.png", x:8.2, y:5.3, w:0.9, h:0.9 });
```

### Stat Cards
```javascript
["$45K","5.2 Acres","Luna County"].forEach((val, i) => {
  slide.addShape(pptx.ShapeType.roundRect, {
    x:0.5+i*3.0, y:2.0, w:2.7, h:2.5,
    fill:{color:"3F6B55"}, line:{color:"E5A94D", width:2}
  });
  slide.addText(val, { x:0.5+i*3.0, y:2.2, w:2.7, h:1.0, align:"center",
    fontFace:"Ethereal", bold:true, fontSize:40, color:"E5A94D" });
  slide.addText(labels[i], { x:0.5+i*3.0, y:3.2, w:2.7, h:0.6, align:"center",
    fontFace:"Neue Montreal", fontSize:13, color:"FFFEF6" });
});
```

### Closing / CTA Slide
```javascript
slide.background = { color:"635752" };
slide.addText("Claim Your Land.", { x:0.4, y:2.0, w:9.2, align:"center",
  fontFace:"Ethereal", bold:true, fontSize:52, color:"FFFEF6" });
slide.addText("River of Deals",   { x:0.4, y:3.3, w:9.2, align:"center",
  fontFace:"Neue Montreal", italic:true, fontSize:22, color:"E5A94D" });
slide.addShape(pptx.ShapeType.rect, { x:3.5, y:3.9, w:3.0, h:0.05, fill:{color:"E5A94D"} });
slide.addText(contactInfo, { x:0.4, y:4.2, w:9.2, align:"center",
  fontFace:"Neue Montreal", fontSize:16, color:"F6F4E3" });
slide.addImage({ path:"assets/logos/logo-horizontal-white.png", x:3.5, y:5.8, w:3.0, h:1.0 });
```
