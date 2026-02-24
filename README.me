# ioPool Spa Monitoring Dashboard Cards for Home Assistant

Beautiful, color-coded Home Assistant dashboard cards for monitoring **spa water Temperature, pH, and ORP** from an **ioPool** sensor.

This project includes a complete set of Lovelace cards for each metric:

- **Compact status row**
- **270° SVG gauge card** (aligned needle + threshold bands)
- **24-hour ApexCharts history graph**
- **Range legend markdown card**

Designed for quick at-a-glance water chemistry checks with clean visuals and easy customization.

---

## Features

- ✅ **Temperature, pH, and ORP** dashboard cards
- ✅ **270° SVG gauges** with aligned threshold arcs and needle
- ✅ **Color-coded target zones** (red / yellow / green / yellow / red)
- ✅ **Compact status row cards** for a quick summary
- ✅ **24h ApexCharts history graphs** with threshold shading
- ✅ **Markdown range legend cards** for on-dashboard reference
- ✅ **Button-card / ApexCharts-card compatible**
- ✅ Easy to customize **ranges, icons, colors, labels, and entities**

---

## Screenshots

> Replace or update the screenshot paths/filenames below as needed to match your repo.

### Dashboard Overview
![Dashboard Overview](docs/screenshots/dashboard-overview.png)

### Temperature Gauge
![Temperature Gauge](docs/screenshots/temperature-gauge.png)

### pH Gauge
![pH Gauge](docs/screenshots/ph-gauge.png)

### ORP Gauge
![ORP Gauge](docs/screenshots/orp-gauge.png)

---

## Prerequisites

You will need:

- **Home Assistant** (Lovelace dashboard)
- Working **ioPool** entities in Home Assistant
- **[custom:button-card]** (via HACS)
- **[custom:apexcharts-card]** (via HACS)
- *(Optional)* **card-mod** (for styling markdown range cards)

---

## Entities Used

This project currently uses these entities:

- `sensor.iopool_saluspa_bahama_temperature`
- `sensor.iopool_saluspa_bahama_ph`
- `sensor.iopool_saluspa_bahama_orp`

If your entity names are different, just replace them in the YAML files.

---

## Threshold Ranges

> These are the ranges currently used in the cards. Adjust to match your spa chemistry targets and sanitizer strategy.

### Temperature (°F)

- 🔴 **< 59.0** = Low
- 🟡 **59.0 to < 68.9** = Cool
- 🟢 **68.9 to ≤ 84.2** = Target
- 🟡 **> 84.2 to ≤ 89.6** = Warm
- 🔴 **> 89.6** = High

### pH

- 🔴 **< 6.8** = Low
- 🟡 **6.8 to < 7.1** = Low-OK
- 🟢 **7.1 to ≤ 7.7** = Target
- 🟡 **> 7.7 to ≤ 8.1** = High-OK
- 🔴 **> 8.1** = High

### ORP (mV)

- 🔴 **< 550** = Low
- 🟡 **550 to < 650** = Fair
- 🟢 **650 to ≤ 800** = Good
- 🟡 **> 800 to ≤ 1000** = High
- 🔴 **> 1000** = Very High

### Boundary Notes (important)

The cards use `if / else if` logic, so **boundary values land in one exact bucket**.  
For example (pH):

- `7.10` → **Target**
- `7.70` → **Target**
- `7.71` → **High-OK**

This avoids overlap and keeps the **gauge needle**, **threshold arcs**, and **status text** aligned.

---

## Quick Start

1. **Install required custom cards** (via HACS):
   - `button-card`
   - `apexcharts-card`
   - *(optional)* `card-mod`

2. **Verify your ioPool entities** exist in:
   - **Developer Tools → States**

3. **Copy the YAML cards** from this repository into your dashboard (or YAML files)

4. **Replace entity IDs** with your own entity names

5. **Add cards to Lovelace**
   - Use as a `vertical-stack`
   - Or place each card individually wherever you want

---

## Included Card Types (per metric)

Each metric (**Temperature**, **pH**, **ORP**) includes:

- **Status row card**  
  A compact color-coded summary row with icon, label, status, and current value.

- **270° gauge card**  
  SVG-based gauge with:
  - aligned threshold bands
  - aligned pointer needle
  - optional inner progress arc
  - center icon + status text

- **24h ApexCharts card**  
  Historical trend chart with threshold shading for context.

- **Markdown range card**  
  Small legend/reference card listing the configured target ranges.

---

## Why a 270° SVG Gauge?

A full 360° circular gauge looks nice, but it can create visual confusion when trying to align:

- threshold color bands
- progress arc
- pointer needle

This project uses a **270° gauge sweep**, which makes the reading feel more natural and easier to interpret.

### How it works (high level)

The gauge code uses the same mapping for *everything*:

1. `minV` / `maxV` define the displayed value range
2. Current value is normalized to a percent (`0..1`)
3. Percent is mapped to **gauge-local degrees** (`0..270`)
4. A helper function maps gauge-local angle → on-screen angle
5. Threshold breakpoints are converted into matching SVG arc segments
6. Needle uses the **exact same angle mapping** (critical for alignment)

That shared coordinate system is what keeps the gauge visually accurate.

---

## File Structure

```text
.
├── cards/
│   ├── temperature/
│   │   ├── temperature_status_row.yaml
│   │   ├── temperature_gauge_card.yaml
│   │   ├── temperature_apexchart_24h.yaml
│   │   └── temperature_ranges_markdown.yaml
│   ├── ph/
│   │   ├── ph_status_row.yaml
│   │   ├── ph_gauge_card.yaml
│   │   ├── ph_apexchart_24h.yaml
│   │   └── ph_ranges_markdown.yaml
│   └── orp/
│       ├── orp_status_row.yaml
│       ├── orp_gauge_card.yaml
│       ├── orp_apexchart_24h.yaml
│       └── orp_ranges_markdown.yaml
├── docs/
│   └── screenshots/
├── LICENSE
└── README.md
