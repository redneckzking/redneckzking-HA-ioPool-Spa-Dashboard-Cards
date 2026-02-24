# Notes / Design Decisions

This file documents the design choices behind the ioPool spa dashboard cards.

---

## Why These Cards Exist

The goal was a dashboard that makes spa chemistry easy to scan quickly, with:

- consistent thresholds
- clear status colors
- gauge visualization
- historical trends
- compact “what do the ranges mean?” reference

---

## Why a 270° SVG Gauge Was Used

A 360° ring gauge looks nice, but it can be confusing to align:

- threshold bands
- pointer
- progress ring

This project switched to a **270° SVG gauge** so all visual elements use the same angle mapping and coordinate system.

### Benefits
- easier threshold alignment
- easier debugging
- more intuitive pointer movement
- cleaner top-arc presentation

---

## Gauge Mapping Concept (Important)

Each gauge follows this pipeline:

1. Start with a sensor value (`v`)
2. Clamp it to the gauge display range (`minV`, `maxV`)
3. Normalize to a percent (`0..1`)
4. Convert to gauge-local degrees (`0..270`)
5. Convert gauge-local degrees to screen angle (`gToDeg`)
6. Draw:
   - threshold arcs
   - optional progress arc
   - pointer needle

This keeps the pointer and colored ranges aligned.

---

## “Keep Thresholds in Sync” Rule

A recurring source of problems is inconsistent thresholds across components.

Each metric has thresholds defined in multiple places:

- status row logic
- gauge thresholds / segment boundaries
- ApexCharts background annotations
- markdown range legend text

If you change one, change all of them.

---

## Why the Gauge Center Value Was Made Optional

The gauge originally displayed:

- icon
- numeric value
- status text

After adding a compact status/value row card above the gauge, the numeric value in the gauge became redundant.

Current preference:
- top row shows value + status
- gauge shows icon + status only (cleaner)

This is optional and easy to change back.

---

## Why Markdown Range Cards Are Included

Even with good colors, it’s useful to have a quick reference showing:

- what each color/range means
- the current status
- the current reading

The markdown card acts as a compact legend and makes the dashboard easier to understand at a glance.

---

## ApexCharts Notes

ApexCharts cards are configured for:

- 24-hour history
- grouped averaging (typically 10 min)
- threshold background shading
- readable y-axis labels
- current value in header

These are chosen for readability over raw point density.

---

## Copy/Paste Lessons Learned (Real-World)

When iterating on multiple similar cards (Temperature / pH / ORP), it’s easy to accidentally:

- paste pH thresholds into ORP
- update one card but not another
- leave one old boundary value behind

To reduce this:
- keep each card in its own file
- use clear file names
- test one metric at a time

---

## Future Ideas (Optional)

Potential future improvements:

- package as a reusable blueprint-like card collection (documentation only)
- add optional tick labels on SVG gauges
- support Celsius version of temperature cards
- add theme-aware colors (light/dark tuning)
- add a single combined dashboard example layout
