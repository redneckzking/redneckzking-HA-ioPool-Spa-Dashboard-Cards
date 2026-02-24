# Contributing

Thanks for your interest in improving this project.

This repo is primarily a Home Assistant dashboard card collection, so contributions are welcome in the form of:

- bug fixes
- YAML cleanup / readability improvements
- documentation improvements
- new example layouts
- alternate color themes
- Celsius temperature variants
- compatibility notes for different setups

---

## Before You Submit Changes

Please try to keep changes:

- focused
- easy to review
- consistent with the project style

If changing thresholds or visual logic, make sure the update stays synchronized across:

- status row cards
- gauge cards
- ApexCharts cards
- markdown legend cards

---

## Suggested Contribution Workflow

1. Fork the repo
2. Create a branch
   - Example: `fix/ph-gauge-threshold-alignment`
3. Make your changes
4. Test in Home Assistant
5. Commit with a clear message
6. Open a pull request

---

## Testing Checklist (Recommended)

Before submitting, check:

- [ ] Card renders without YAML/template errors
- [ ] `NO DATA` fallback still works
- [ ] Pointer aligns with colored gauge bands
- [ ] Status row matches gauge status
- [ ] ApexCharts shading matches thresholds
- [ ] Markdown legend ranges are accurate
- [ ] YAML indentation is valid

---

## Style Notes

- Prefer readable YAML over “clever” compact YAML
- Keep threshold values explicit (easy to audit)
- Use consistent naming for files and sections
- Add comments where logic is non-obvious (especially gauge math)

---

## Documentation Contributions

Documentation improvements are especially appreciated:

- setup steps
- screenshots
- troubleshooting fixes
- wording clarity
- examples for different entity names / installations

If you notice something confusing, that’s a great contribution.

---

## Issues

If you open an issue, please include:

- which card (Temperature / pH / ORP)
- what looks wrong (status, gauge, chart, markdown)
- current sensor value(s)
- screenshot if possible
- what you expected to see

This makes troubleshooting much faster.

---

## Thanks

Thanks for helping improve the project and make it easier for other Home Assistant users to set up.
