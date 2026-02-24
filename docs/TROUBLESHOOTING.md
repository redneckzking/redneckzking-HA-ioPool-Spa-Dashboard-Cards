# Troubleshooting

Common issues and fixes for the ioPool spa dashboard cards.

---

## 1) Gauge Pointer Does Not Match Colored Bands

### Symptoms
- Pointer appears in a green zone while status says yellow/red
- Colored ring sections look offset from where the needle points

### Common Causes
- Thresholds changed in one card but not others
- `minV` / `maxV` mismatch between pointer mapping and threshold mapping
- Old 360° gauge logic mixed with new 270° gauge logic

### Fix
Make sure the gauge uses the same mapping for:
- pointer (`gNeedle`)
- threshold segment boundaries (`valToG(...)`)
- arc drawing (`arcPathGauge(...)`)

Also confirm the same threshold values are used in:
- status row card
- gauge
- ApexCharts annotations
- markdown legend card

---

## 2) Gauge Looks “Backwards” or Rotated

### Symptoms
- Low values point to the wrong side
- Needle sweep direction feels reversed

### Cause
The gauge-local angle mapping (`gToDeg`) was changed incorrectly.

### Fix
Use the same gauge-local to screen-angle mapping throughout the gauge:

- Gauge local: `0..270`
- Screen mapping: `gToDeg(g) => 225 - g`

This keeps the arc sweep consistent across:
- threshold arcs
- progress arc
- needle angle

---

## 3) Card Shows `NO DATA`

### Check These First
- Entity ID is correct
- Sensor exists in **Developer Tools → States**
- Sensor value is numeric
- Sensor is not `unknown` / `unavailable`

### Tip
The templates use `Number(...)` and `Number.isFinite(...)`, so any non-numeric state will fall back to `NO DATA`.

---

## 4) ApexCharts Card Is Blank

### Possible Reasons
- `custom:apexcharts-card` not installed
- Resource not added to HA
- Recorder/history is disabled for the sensor
- No historical data yet
- YAML indentation issue

### Checks
- Confirm the sensor has history in **History** view
- Confirm ApexCharts is installed through HACS
- Reload the dashboard after saving
- Check browser console for card/resource errors

---

## 5) Markdown Bullet List Shows as One Line

### Cause
Markdown usually needs a blank line before a bullet list.

### Fix
Ensure your markdown content includes:

- a normal text line
- a blank line
- then bullet lines

If using a Jinja template, also make sure indentation does not collapse the list formatting.

---

## 6) Card YAML Saves But Card Doesn’t Render Properly

### Common Cause
A missing backtick / quote / brace in `button-card` JavaScript templates.

### What to Check
- Matching backticks in template strings (`` `...` ``)
- Matching braces `{}` inside JS
- Matching `${...}` interpolations
- Closing `]]]` for button-card JS blocks

### Tip
When editing the SVG gauge, make one small change at a time and save.

---

## 7) Threshold Colors Do Not Match Chart Shading

### Cause
Threshold boundaries in ApexCharts annotations don’t match the gauge/status thresholds.

### Fix
Compare the exact values used in:
- status row thresholds
- gauge `valToG(...)` boundaries
- ApexCharts `annotations.yaxis`
- markdown legend ranges

Even small differences (example: `68.9` vs `69`) can create visual mismatches.

---

## 8) Performance Feels Slow (Dashboard Lag)

### Possible Reasons
- Several `button-card` templates on one page
- Multiple ApexCharts cards with short update intervals
- Heavy dashboard with many custom cards

### Ideas to Improve
- Increase chart `update_interval`
- Increase `group_by.duration`
- Reduce number of charts shown on one view
- Move detailed charts to a separate tab/page

---

## 9) “Looks Fine Yesterday, Wrong Today”

This is often caused by one of these:

- Copy/paste into the wrong card (pH code pasted into ORP or Temperature)
- Partial paste accidentally leaving old thresholds behind
- Edited one card version while dashboard is using another

### Best Practice
Keep each card in a separate YAML file and name them clearly:

- `temperature_gauge_card.yaml`
- `ph_gauge_card.yaml`
- `orp_gauge_card.yaml`

That makes mistakes much easier to spot and fix.

---

## 10) Still Stuck?

If something still looks off, compare these in order:

1. **Sensor value** (actual state)
2. **Status row** (text + color)
3. **Gauge needle**
4. **Gauge colored bands**
5. **Chart shading**
6. **Markdown legend ranges**

If #1 and #2 agree but #3/#4 do not, the problem is in the gauge mapping.

If #2 and #3/#4 agree but chart doesn’t, the problem is ApexCharts annotations.

If the legend text is different from the others, the markdown ranges need updating.
