# Daniel's Home Assistant Configuration

## About

Quote from [niro1987](https://github.com/niro1987/homeassistant-config)
> This is my Home Assistant configuration inspired by [Frenck's methodology](https://github.com/frenck/home-assistant-config) of having each file doing only one thing.
>
> I chose this methodology because I like the way how the integrations are organized. I don't have to spend time looking through long files to find what I'm looking for. To add or to remove an integration is as easy as creating or removing a file.

Both configuration repos were used as reference during the setup of my own configuration.

## Structure

`configuration.yaml` only loads `integrations/` as packages, one file per integration. Those files pull in the folders below.

| Folder | Contents |
| --- | --- |
| `integrations/` | One package per integration (logger, recorder, KNX, EMHASS, ...) |
| `entities/` | Template sensors, input booleans, groups, notify targets |
| `entity_controller/` | One motion lighting controller per room |
| `knx/` | KNX lights, covers, sensors, switches and exposes |
| `esphome/` | ESPHome device configs |
| `automations/` | YAML automations, next to the UI-managed `automations.yaml` |
| `blueprints/` | Automation and template blueprints |
| `www/` | Images and static files for the dashboards |

Integrations set up through the UI live in `.storage` and are not part of this repo.

## Highlights

### Energy

- `integrations/electricity_pricing.yaml`: landed import and export price from network
  tariffs plus the wholesale spot price, battery grid-charge advice, and forecast accuracy
  tracking for solar (Solcast, Helios, Forecast.Solar) and price
- `integrations/emhass.yaml`: EMHASS battery schedule optimised against wholesale prices.
  Advisory only, it does not control the inverter
- `integrations/utility_meter.yaml`: 30 minute and monthly grid import/export from the Alpha ESS

### ESPHome devices

- [Centurion D5 Evo](https://github.com/dan-s-github/centurion-d5-evo): gate motor control
- [Zehnder ComfoAir](https://github.com/dan-s-github/zehnder-comfoair-can): ventilation over CAN bus
- AAP Alarm Interface: Arrowhead alarm panel through the `crow_alarm_panel`
  [external component](https://github.com/dan-s-github/esphome-components)

### Lighting

- KNX lights and covers, with Home Assistant states exposed back to the KNX bus
- Entity Controller for motion lighting, with per-room override groups and sleep/guest modes

## Additional Integrations used

### Apps (Add-ons)

- Advanced SSH & Web Terminal
- EMHASS
- ESPHome Device Builder
- Glances
- Grafana
- InfluxDB v1
- Let's Encrypt (started weekly by an automation)
- Mosquitto broker
- Network UPS Tools
- OpenThread Border Router
- SMART Sniffer
- Signal Messenger
- Studio Code Server

### Custom Components

Installed through [HACS](https://hacs.xyz/).

- **Energy:** Alpha ESS, Electricity Info, EM6, Helios Forecast, Solcast Solar
- **Weather:** MetService Weather, WeatherFlow Forecast
- **Temperature and humidity sensors:** Jaalee, KBeacon
- **Lighting:** Entity Controller
- **Security:** Frigate, Hikvision NEXT
- **Media:** Triad AMS, Yamaha YNCA
- **Other:** Daily, F1 Sensor, Shopping List Manager, Smart Sniffer, UniFi MQTT,
  Waste Collection Schedule, Watercare

### Lovelace Cards

- **Layout:** auto-entities, layout-card, stack-in-card, vertical-stack-in-card,
  tabbed-card, simple-tabs, sections-to-tabs, hui-element, kiosk-mode
- **Styling and templates:** card-mod, config-template-card, template-entity-row,
  fold-entity-row, custom-brand-icons, ha-knx-uf-iconset
- **Entities:** Mushroom, light-entity-card, rgb-light-card, status-card
- **Graphs:** apexcharts-card, mini-graph-card, bar-card, history-explorer-card,
  tempometer-gauge-card
- **Weather:** clock-weather-card, weather-forecast-card, weather-station-card,
  compass-card, Helios
- **Media:** mini-media-player, maxi-media-player, yet-another-media-player,
  mediocre-hass-media-player-cards
- **Other:** surveillance-card, formulaone-card, f1-sensor-live-data-card,
  shopping-list-manager-card, ha-shopping-list-improved, wheelie-bin-card

### Themes

- Custom Square
- Oxford Blue
- Sweet Pink
