# Mini Met Station 🌦️

A low-power remote weather station built on an **Adafruit Feather M0 Adalogger** with cellular (Blues Notecard) uplink. The station wakes every 10 minutes, records a suite of environmental sensors, logs the data locally to microSD, transmits it to the cloud, and then cuts its own power until the next cycle to conserve battery in the field.

The system is **solar powered**, running on a solar panel and rechargeable battery pack, allowing it to operate autonomously off-grid.

**Measured parameters:** air temperature & humidity, barometric pressure, rainfall, and solar radiation.

A companion Python script pulls the station's data from Notehub and cross-validates it against official Israel Meteorological Service (IMS) reference stations, generating a "nearly-live" comparison dashboard with publication-ready exportable charts.

## About
This project was developed for the graduate-level course **"Envirotech: DIY Sensors for Environmental Research"** taught by **Prof. Elad Levintal** at **Ben-Gurion University of the Negev**.

## Group Members
- Shelby Kaplan
- Rut Parnas
- Ramson Kabenla
- Mary Mitchell Adhiambo

## Repository Contents
The Arduino firmware is included here. The full project report is provided in this repository and covers:

- **Arduino firmware**, plus `secrets.h.example` (copy to `secrets.h` and add your own Notehub product UID before building — this file is git-ignored)
- **dashboard generator code** — pulls station + IMS reference data via API and generates the comparison dashboard (see [Dashboard & Validation](#dashboard--validation) below)
- **BILL_OF_MATERIALS.md** — full parts list with costs, links, and specs
- **Final project report** — covers Literature Review, Materials & Methods, Results & Discussion, Challenges & Considerations, and Conclusions
- **Final project presentation**

## At a Glance
| | |
|---|---|
| **Microcontroller** | Adafruit Feather M0 Adalogger |
| **Sensors** | SHT31 (temp/RH), ICP10111 (pressure), SEN0575 (rain), SEN0640 RS485 (solar radiation) |
| **Sensor bus** | DFRobot Gravity I²C multiplexer (TCA9548A), avoids bus contention with the Notecard |
| **Connectivity** | Blues Wireless Notecard (cellular, I²C mode) |
| **Power** | Solar panel + rechargeable Li-ion battery |
| **Storage** | microSD (local CSV backup) |
| **Power strategy** | 10-minute power-gated wake cycles (full hardware power cutoff via Notecard ATTN); 60-minute cloud sync |
| **Validation** | Live-compared against IMS Sde Boker & Ashalim reference stations |

## Dashboard & Validation
`dashboard generator code` pulls the station's readings from the Notehub API and overlays reference data from IMS's Sde Boker (~1 km away) and Ashalim (~15 km away) stations for the same period, producing an interactive HTML dashboard with per-chart PNG export.

**Setup:**
1. Create a Notehub Personal Access Token (Notehub → account menu → Settings → Personal Access Tokens).
2. (Optional, for IMS comparison) Request an IMS API token at ims@ims.gov.il — see the [IMS Observation Data API](https://ims.gov.il/en/ObservationDataAPI).
3. Create `notehub_secret.txt` next to the script (git-ignored) with:
NOTEHUB_TOKEN=your_token
NOTEHUB_PROJECT_UID=com.your-namespace:your_project
IMS_TOKEN=your_ims_token

4. Run `python3 station_dashboard.py` — writes `dashboard.html` and opens it in your browser. Re-run any time to refresh.

## Disclaimer
This project is shared for educational and reference purposes. It reflects the specific components, wiring, and environmental conditions used in our build. Any variations to the hardware, sensors, power setup, code, or deployment conditions may produce different results and performance. If you adapt this design, test thoroughly and proceed at your own risk.
