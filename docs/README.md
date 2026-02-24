# ioPool Spa Dashboard Cards for Home Assistant

Custom Lovelace dashboard cards for monitoring **spa water Temperature, pH, and ORP** in **Home Assistant** using ioPool sensor data (or equivalent entities).

This project provides a clean, at-a-glance dashboard set for each metric with:

- **compact status row**
- **270° SVG gauge card** (aligned colored ranges + pointer)
- **24h ApexCharts history**
- **compact markdown range legend**

---

## Features

- ✅ **Temperature, pH, and ORP** card sets
- ✅ Consistent **red / yellow / green / yellow / red** threshold logic
- ✅ **270° SVG gauges** with correctly aligned:
  - threshold arcs
  - progress arc
  - pointer needle
- ✅ Compact status row cards for quick scanning
- ✅ 24-hour ApexCharts history cards with threshold shading
- ✅ Compact markdown legend cards with current status + range bullets
- ✅ Easy to customize entity IDs, ranges, labels, icons, and colors

---

## Screenshots

> Add your screenshots to `docs/screenshots/` and keep these filenames (or update the paths below).

### Dashboard Overview
![Dashboard Overview](docs/screenshots/dashboard-overview.png)

### Temperature Gauge
![Temperature Gauge](docs/screenshots/temperature-gauge.png)

### pH Gauge
![pH Gauge](docs/screenshots/ph-gauge.png)

### ORP Gauge
![ORP Gauge](docs/screenshots/orp-gauge.png)

---

## Requirements

- **Home Assistant** (Lovelace)
- **ioPool integration** (or equivalent HA sensors)
- **custom:button-card** (recommended via HACS)
- **custom:apexcharts-card** (recommended via HACS)
- *(Optional)* **card-mod** (used for markdown card styling)

---

## Entities Used

The example YAML in this repo uses the following entities:

- `sensor.iopool_saluspa_bahama_temperature`
- `sensor.iopool_saluspa_bahama_ph`
- `sensor.iopool_saluspa_bahama_orp`

If your entity names are different, do a **search/replace** in the YAML files.

---

## Threshold Ranges (Current Defaults)

These ranges are used across the status rows, gauges, chart shading, and legend cards.

### Temperature (°F)

- 🔴 **< 59.0** = Low
- 🟡 **59.0 – < 68.9** = Cool
- 🟢 **68.9 – 84.2** = Target
- 🟡 **> 84.2 – 89.6** = Warm
- 🔴 **> 89.6** = High

### pH

- 🔴 **< 6.8** = Low
- 🟡 **6.8 – < 7.1** = Low-OK
- 🟢 **7.1 – 7.7** = Target
- 🟡 **> 7.7 – 8.1** = High-OK
- 🔴 **> 8.1** = High

### ORP (mV)

- 🔴 **< 550** = Low
- 🟡 **550 – < 650** = Fair
- 🟢 **650 – 800** = Good
- 🟡 **> 800 – 1000** = High
- 🔴 **> 1000** = Very High

> **Important:** Keep these thresholds synchronized across:
>
> - status row card logic
> - gauge threshold arc segments
> - ApexCharts annotations
> - markdown legend cards
>
> If one is changed but the others are not, the UI can look “wrong” even though the code is working.

---

## Quick Start

1. **Install required custom cards**
   - `button-card`
   - `apexcharts-card`
   - *(optional)* `card-mod`

2. **Verify entities in Home Assistant**
   - Go to **Developer Tools → States**
   - Confirm temperature / pH / ORP entities exist and update

3. **Copy the YAML cards from this repo**
   - status row card(s)
   - gauge card(s)
   - ApexCharts card(s)
   - markdown legend card(s)

4. **Replace entity IDs**
   - Update the example entity IDs to match your system

5. **Add to Lovelace**
   - Use **vertical-stack**, **grid**, or place as individual cards

---

## Card Types Included (Per Metric)

Each metric (Temperature / pH / ORP) includes four card styles:

### 1) Compact Status Row
A quick summary row with:
- metric label
- live value
- color-coded status

### 2) 270° SVG Gauge Card
A custom gauge using SVG arcs and a pointer with:
- threshold band arcs
- aligned pointer needle
- status label + icon
- optional progress arc styling

### 3) 24h ApexCharts History
A time-series card with:
- 24-hour trend
- threshold background shading
- current reading in the header
- smoothing/grouping for readability

### 4) Range Legend Markdown Card
A compact legend showing:
- current value
- current status
- threshold bullets for quick reference

---

## Why This Gauge Uses 270° Instead of 360°

A full circular gauge looks good, but it can be harder to keep the **pointer** and **colored threshold bands** perfectly aligned.

This project uses a **270° SVG gauge** so the:

- threshold arcs
- progress arc
- pointer needle

all share the **same angle mapping**.

That makes the gauge easier to reason about and prevents the “needle points to one range but looks like another” issue.

### Gauge mapping concept (high level)

1. Define the display range (`minV`, `maxV`)
2. Normalize the value to `0..1`
3. Convert that to **gauge-local degrees** `0..270`
4. Convert gauge-local angle to screen angle
5. Convert threshold values using the exact same mapping
6. Draw arcs + pointer from the same coordinate system

Result: **the scale and pointer agree**.

---

## Repository Structure

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
├── examples/
│   ├── vertical_stack_example.yaml
│   └── dashboard_section_example.yaml
├── docs/
│   ├── screenshots/
│   │   ├── dashboard-overview.png
│   │   ├── temperature-gauge.png
│   │   ├── ph-gauge.png
│   │   └── orp-gauge.png
│   ├── INSTALLATION.md
│   ├── CUSTOMIZATION.md
│   ├── TROUBLESHOOTING.md
│   └── CONTRIBUTING.md
├── LICENSE
└── README.md
