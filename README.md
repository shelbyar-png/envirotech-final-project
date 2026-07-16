# Mini Met Station 🌦️

A low-power remote weather station built on an **Adafruit Feather M0 Adalogger** with cellular (Blues Notecard) uplink. The station wakes every 10 minutes, records a suite of environmental sensors, logs the data locally to microSD, transmits it to the cloud, and then cuts its own power until the next cycle to conserve battery in the field.

The system is **solar powered**, running on a solar panel and rechargeable battery pack, allowing it to operate autonomously off-grid.

**Measured parameters:** air temperature & humidity, barometric pressure, rainfall, and solar radiation.

## About
This project was developed for the graduate-level course **"Envirotech: DIY Sensors for Environmental Research"** taught by **Prof. Elad Levintal** at **Ben-Gurion University of the Negev**.

## Group Members
- Shelby Kaplan
- Rut Parnas
- Ramson Kabenla
- Mary Mitchell Adhiambo

## Repository Contents
The Arduino firmware is included here. The full project report is provided in this repository and covers:

- **Bill of Materials**
- **Wiring Diagram**
- **Literature Review**
- **Results and Discussion**
- **Conclusion**

## At a Glance
| | |
|---|---|
| **Microcontroller** | Adafruit Feather M0 Adalogger |
| **Sensors** | SHT31 (temp/RH), ICP10111 (pressure), SEN0575 (rain), RS485 (solar sensor) |
| **Connectivity** | Blues Wireless Notecard (cellular) |
| **Power** | Solar panel + rechargeable battery |
| **Storage** | microSD (local CSV backup) |
| **Power strategy** | 10-minute power-gated wake cycles; 60-minute cloud sync |

## Disclaimer
This project is shared for educational and reference purposes. It reflects the specific components, wiring, and environmental conditions used in our build. Any variations to the hardware, sensors, power setup, code, or deployment conditions may produce different results and performance. If you adapt this design, test thoroughly and proceed at your own risk.
