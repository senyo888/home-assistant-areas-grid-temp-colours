# Setup

## 1) Install HACS requirements
In HACS → Frontend:
- layout-card
- button-card

Restart Home Assistant if prompted.

---

## 2) Add helper input_numbers

Copy `helpers/input_numbers.yaml` into your config.

Common options:
- merge into an existing helpers file, OR
- include via `configuration.yaml`:

```yaml
input_number: !include helpers/input_numbers.yaml

Restart Home Assistant.

3) Add the Lovelace card (manual)
Dashboard → Edit → Add Card → Manual → paste:
lovelace/areas_grid_temp_reactive.mobile.yaml

4) Replace placeholders
Every room tile uses variables: to keep things clean.

Example:

variables:
  navigate_path: "/dashboard/areas-kitchen"
  motion_entity: "binary_sensor.kitchen_motion"
  temp_entity: "sensor.kitchen_temperature"
  humidity_entity: "sensor.kitchen_humidity"

Chips are normal button-card entities:

entity: "fan.kitchen_fan"
entity: "light.kitchen_lights"

Troubleshooting

Tile border not changing:
confirm variables.temp_entity is a valid sensor with a numeric state

Humidity not showing:
remove/blank variables.humidity_entity or point it to a numeric sensor

Badges not showing:
confirm your motion/door entities are binary_sensors with on/off


---

## `CHANGELOG.md`

```md
# Changelog

## v1.0.0
- Initial public template release
- Temp-reactive area tiles + motion/door badges + chip examples
- UI-editable thresholds via input_numbers
