# DealFlow Brand — Spreadsheet / Excel Guide

Read `/mnt/skills/public/xlsx/SKILL.md` for technical openpyxl implementation.

## Assets


---

## Colors (ARGB — FF = full opacity)

```python
from openpyxl.styles import PatternFill, Font, Alignment, Border, Side

DUSTY_PINE_FILL   = PatternFill("solid", fgColor="FF3F6B55")
TAUPE_FILL        = PatternFill("solid", fgColor="FF635752")
HARVEST_GOLD_FILL = PatternFill("solid", fgColor="FFE5A94D")
SOFT_IVORY_FILL   = PatternFill("solid", fgColor="FFF6F4E3")
WARM_WHITE_FILL   = PatternFill("solid", fgColor="FFFFFEF6")
LEMON_GRASS_FILL  = PatternFill("solid", fgColor="FFD9CD25")

def hdr_font(size=12, white=True):
    return Font(name="Calibri", bold=True, size=size,
                color="FFFFFEF6" if white else "FF635752")
def body_font(size=11):
    return Font(name="Calibri", size=size, color="FF635752")
def gold_font(size=12):
    return Font(name="Calibri", bold=True, size=size, color="FFE5A94D")

GOLD_BORDER = Border(bottom=Side(style='medium', color='E5A94D'))
THIN_BORDER = Border(bottom=Side(style='thin',   color='635752'))
```

---

## Sheet Header

```python
from openpyxl.utils import get_column_letter

def apply_brand_header(ws, title, subtitle=None, num_cols=8):
    ws.merge_cells(f"A1:{get_column_letter(num_cols)}1")
    ws.row_dimensions[1].height = 48
    c = ws['A1']
    c.value = f"DealFlow OH  |  {title}"
    c.fill  = DUSTY_PINE_FILL
    c.font  = Font(name="Calibri", bold=True, size=18, color="FFFFFEF6")
    c.alignment = Alignment(horizontal='left', vertical='center', indent=1)

    ws.row_dimensions[2].height = 4
    ws.merge_cells(f"A2:{get_column_letter(num_cols)}2")
    ws['A2'].fill = HARVEST_GOLD_FILL

    next_row = 3
    if subtitle:
        ws.row_dimensions[3].height = 24
        ws.merge_cells(f"A3:{get_column_letter(num_cols)}3")
        s = ws['A3']
        s.value = subtitle
        s.fill  = SOFT_IVORY_FILL
        s.font  = Font(name="Calibri", italic=True, size=11, color="FF635752")
        s.alignment = Alignment(horizontal='left', vertical='center', indent=1)
        next_row = 4
    return next_row
```

---

## Column Headers

```python
def apply_column_headers(ws, row, headers):
    ws.row_dimensions[row].height = 28
    for col, text in enumerate(headers, 1):
        c = ws.cell(row=row, column=col, value=text)
        c.fill      = TAUPE_FILL
        c.font      = hdr_font(11)
        c.alignment = Alignment(horizontal='center', vertical='center', wrap_text=True)
        c.border    = GOLD_BORDER
```

---

## Data Rows & Price Cells

```python
def apply_data_row(ws, row, values, highlight=False):
    fill = HARVEST_GOLD_FILL if highlight else (
           SOFT_IVORY_FILL if row % 2 == 0 else WARM_WHITE_FILL)
    for col, val in enumerate(values, 1):
        c = ws.cell(row=row, column=col, value=val)
        c.fill = fill; c.font = body_font()
        c.alignment = Alignment(vertical='center', indent=1)
        c.border = THIN_BORDER

def apply_price_cell(ws, row, col, value):
    c = ws.cell(row=row, column=col, value=value)
    c.font = gold_font(12)
    c.number_format = '$#,##0'
    c.alignment = Alignment(horizontal='right', vertical='center')
```

---

## Status Conditional Formatting

```python
from openpyxl.formatting.rule import CellIsRule

def apply_status_colors(ws, col_letter, start_row, end_row):
    rng = f"{col_letter}{start_row}:{col_letter}{end_row}"
    ws.conditional_formatting.add(rng, CellIsRule(
        operator='equal', formula=['"Active"'],
        fill=DUSTY_PINE_FILL, font=Font(color="FFFFFEF6", bold=True)))
    ws.conditional_formatting.add(rng, CellIsRule(
        operator='equal', formula=['"Sold"'],
        fill=HARVEST_GOLD_FILL, font=Font(color="FF635752", bold=True)))
    ws.conditional_formatting.add(rng, CellIsRule(
        operator='equal', formula=['"Pending"'],
        fill=LEMON_GRASS_FILL, font=Font(color="FF635752", bold=True)))
```

---

## Deal Tracker Template

```python
from openpyxl import Workbook

def create_deal_tracker(output_path):
    wb = Workbook()
    ws = wb.active
    ws.title = "Deal Tracker"
    widths = [22,14,8,10,14,16,12,22]
    for i, w in enumerate(widths, 1):
        ws.column_dimensions[get_column_letter(i)].width = w
    next_row = apply_brand_header(ws, "Deal Tracker", "River of Deals — Active Inventory")
    headers  = ["Property Name","County","State","Acreage","Ask Price",
                "Acquisition Cost","Status","Notes"]
    apply_column_headers(ws, next_row, headers)
    ws.freeze_panes = ws.cell(row=next_row+1, column=1)
    fr = next_row + 25
    ws.merge_cells(f"A{fr}:H{fr}")
    f = ws[f"A{fr}"]
    f.value = "DealFlow OH  |  River of Deals  |  dealflowoh.com"
    f.font  = Font(name="Calibri", italic=True, size=9, color="FF635752")
    f.alignment = Alignment(horizontal='center')
    wb.save(output_path)
    return output_path
```
