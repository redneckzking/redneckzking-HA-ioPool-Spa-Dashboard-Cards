# Installation

This project provides Home Assistant Lovelace dashboard cards for monitoring ioPool spa values (Temperature, pH, and ORP).

## Requirements

- Home Assistant (Lovelace dashboard)
- ioPool integration (or equivalent entities)
- `custom:button-card`
- `custom:apexcharts-card`
- *(Optional)* `card-mod`

## Install Custom Cards

### HACS (recommended)

Install these frontend cards from HACS:

- **button-card**
- **apexcharts-card**

Optional:
- **card-mod**

After installing, reload your browser / clear cache if needed.

## Verify Entities

In Home Assistant:

- Go to **Developer Tools → States**
- Confirm these entities exist (or note your own names):
  - `sensor.iopool_saluspa_bahama_temperature`
  - `sensor.iopool_saluspa_bahama_ph`
  - `sensor.iopool_saluspa_bahama_orp`

## Add the Cards

Copy the YAML cards from this repo into your dashboard (Manual card / YAML mode), including:

- compact status row cards
- 270° gauge cards
- ApexCharts history cards
- markdown range legend cards

You can place them in:
- a `vertical-stack`
- a `grid`
- or as individual cards

## Update Entity IDs

If your entities use different names, search/replace the example IDs in the YAML.

## Notes

Keep threshold values synchronized across:
- status row logic
- gauge thresholds / arc segments
- ApexCharts annotations
- markdown range legend cards

This prevents mismatches between gauge colors, status labels, and chart shading.
