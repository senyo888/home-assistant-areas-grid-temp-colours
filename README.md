# home-assistant-areas-grid-temp-colours
Mobile-first Home Assistant Areas grid with temperature-reactive outlines + quick control chips (layout-card + button-card).

# Home Assistant Areas Grid • Temp Colours (Mobile)

A mobile-first **Areas grid** for Home Assistant that uses **temperature-reactive tile outlines + icons**, plus **badges** (motion/door) and **quick-control chips** (lights/fans/etc).

This repo ships as a **privacy-safe public template**:
- No real entity IDs
- All integrations are user-supplied via `variables:` placeholders

---

## Preview

- 2-column mobile layout (layout-card grid)
- Each room is a tile:
  - Name + icon
  - Temp (main)
  - Humidity (sub, optional)
  - Optional badge (motion / door-open)
  - Optional chips row (fan/light/etc)

---

## Requirements (HACS)

Install via HACS:
- **layout-card**
- **button-card**

---

## Install (Manual Card)

1. Copy `helpers/input_numbers.yaml` into your Home Assistant config (see SETUP.md).
2. Restart Home Assistant.
3. In Lovelace:
   - Edit Dashboard → Add Card → **Manual**
   - Paste `lovelace/areas_grid_temp_reactive.mobile.yaml`
4. Replace placeholders like:
   - `[REPLACE_ME] sensor.kitchen_temperature`
   - `[REPLACE_ME] binary_sensor.kitchen_motion`
   - `[REPLACE_ME] /dashboard/areas-kitchen`

---

## How the temp colours work

Tile border + icon colour is determined by the room temperature compared to UI-editable thresholds:

- `< t1` = cold
- `< t2` = cool
- `< t3` = ok
- `< t4` = warm
- `>= t4` = hot

Edit thresholds live using helpers:
- `input_number.cv_t1..cv_t4`

---

## Extending

Duplicate the “Example Area Tile” block per room and only change:
- `name`
- `icon`
- `variables:` (temp/humidity/motion/navigation + chip entities)

---

## Safety / Privacy

Before publishing your own config, search for:
- sensor names that include addresses/rooms
- alarm entities
- dashboard URLs you don’t want public
- any personally identifying strings

This repo intentionally uses placeholders only.

---

## License

MIT (see LICENSE)
