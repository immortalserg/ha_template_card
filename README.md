# ha_template_card

Custom Home Assistant Lovelace cards with a visual editor.

**Version:** 0.1.0 (initial prototype). Two cards: **Plant Monitor Card** and **Flower BLE Card**. No dependency on `custom:button-card`.

## Installation

### HACS (custom repository)
In HACS, add `https://github.com/immortalserg/ha_template_card` as a **Dashboard** custom repository, install it and refresh Home Assistant's frontend.

### Manual
Copy `ha-template-card.js` to `/config/www/ha_template_card/ha-template-card.js`, then add a JavaScript module under **Settings → Dashboards → Resources**:

```text
/local/ha_template_card/ha-template-card.js?v=0.1.0
```

## Plant Monitor Card

```yaml
type: custom:plant-monitor-card
entity: plant.fikus
signal_entity: sensor.3_signal
battery_entity: sensor.flower3_battery
gauge_columns: 3
show_soil_temperature: true
show_air_temperature: false
show_moisture: true
show_humidity: false
show_conductivity: true
show_illuminance: true
show_dli: true
dli_use_24h: true
```

Seven individually switchable gauges: soil and air temperature, soil and air humidity, conductivity, current illuminance and DLI. Gauge layout: 2 or 3 columns, configurable in the visual editor. Values and min/max thresholds are discovered from the plant's device; manually select entity IDs in the editor if automatic discovery fails. When required values or thresholds are missing the gauge turns gray.

## Flower BLE Card

```yaml
type: custom:flower-ble-card
name: Фикус
signal_entity: sensor.3_signal
battery_entity: sensor.flower3_battery
```

Both cards have built-in visual configuration. The plant card provides an advanced section to select sensors and min/max thresholds manually. DLI defaults to rolling 24h when available.

## Status

This is an initial prototype and has **not yet been tested in a real Home Assistant installation**. Please report any issues with entity discovery or the visual editor in this repository.

## Scope

This is a **Lovelace frontend extension**, not a backend Home Assistant integration. It reads existing Home Assistant entities, including those from the separate Plant Monitor integration.
