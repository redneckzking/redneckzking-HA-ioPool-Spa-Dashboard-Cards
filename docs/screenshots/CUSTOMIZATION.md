
---

## 2) `docs/CUSTOMIZATION.md`

```md
# Customization Guide

This project is designed to be easy to adapt to your own Home Assistant setup.

---

## 1) Change Entity IDs

Search/replace these example entities in the YAML files:

- `sensor.iopool_saluspa_bahama_temperature`
- `sensor.iopool_saluspa_bahama_ph`
- `sensor.iopool_saluspa_bahama_orp`

You can use your own entity IDs from:

- **Developer Tools → States**

---

## 2) Adjust Target Ranges

If you want different target ranges, update the thresholds in **all** places below:

- status row card logic
- gauge card thresholds / arc segments
- ApexCharts annotations
- markdown range legend card

> Keep these in sync so colors, status text, chart shading, and gauge bands all agree.

### Example

If you change pH target from `7.1–7.7` to `7.2–7.8`, update:

- status conditions in row card
- gauge segment boundaries (`valToG(...)`)
- ApexCharts annotation bands
- markdown bullet list text

---

## 3) Change Labels / Icons

You can customize labels and icons inside the `button-card` JavaScript templates.

### Examples

- `🌡️ Temperature`
- `🧪 pH`
- `⚡ ORP`

Material Design Icons are referenced like:

- `mdi:check-decagram`
- `mdi:alert-circle`
- `mdi:thermometer`

---

## 4) Change Colors

The cards use a red/yellow/green scheme for quick status visibility.

Typical colors used:

- Red: `#EF5350`
- Yellow: `#FFD54F`
- Green: `#66BB6A`

You can also change the rgba band colors used in the SVG gauge arcs and chart annotations.

---

## 5) Gauge Display Range (`minV` / `maxV`)

Each gauge uses a display range to map sensor values to the 270° arc.

Examples:

- Temperature gauge: `minV = 40`, `maxV = 110`
- pH gauge: `minV = 6.4`, `maxV = 8.4`
- ORP gauge: `minV = 0`, `maxV = 1100`

Changing these values changes how the pointer spreads across the dial.

### Tip
Use a range that:
- comfortably includes your normal readings
- leaves some room for out-of-range values
- matches your chart scale expectations

---

## 6) Remove/Restore Gauge Center Value

If you prefer a cleaner gauge, you can remove the numeric value from the gauge center and leave only:

- status icon
- status text

If you later want the value back, restore the center value `<div>` in the gauge `custom_fields.gauge` template.

---

## 7) Adjust Card Size / Layout

Common things to tweak:

- card height (e.g. `height: 300px`)
- gauge SVG size (`190x190`)
- font sizes
- footer padding
- border radius

These are all in the `styles:` block of each `custom:button-card`.

---

## 8) ApexCharts Tuning

You can customize:

- `graph_span` (e.g. 12h, 24h, 48h)
- `group_by.duration` (e.g. 5min, 10min, 15min)
- line width and smoothing
- y-axis tick count
- threshold background shading

### Tip
If your sensor updates frequently, a `group_by` average can make the chart easier to read.

---

## 9) Markdown Legend Card Formatting

The markdown legend cards can be made:

- more compact
- more detailed
- bullet-based or plain text
- with/without current status line

If bullets do not render correctly, make sure there is a blank line before the bullet list in the markdown content template.

---

## 10) Vertical Stack vs Individual Placement

These cards work in:

- `vertical-stack`
- `grid`
- individual dashboard sections

If building a compact dashboard, a grid can look great:
- top row = status rows
- middle row = gauges
- bottom row = charts / legends

---

## Recommended Workflow for Safe Changes

1. Duplicate the original YAML card
2. Rename the copy (e.g. `temperature_gauge_card_test.yaml`)
3. Make one change at a time
4. Verify:
   - status row color/text
   - gauge band alignment
   - chart shading
   - markdown legend values

This helps avoid “looks right in one card but wrong in another” problems.
