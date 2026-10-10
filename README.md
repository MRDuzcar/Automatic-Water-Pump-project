# Automatic Soil Watering System

A MATLAB-controlled watering system that checks soil moisture and switches a water pump through a Grove MOSFET module. Watering depends on both the scheduled check time and the measured moisture level, preventing the pump from running when the soil is already wet.

Built and tested as a university coursework project in April 2025.

## Features

- Reads the soil moisture sensor voltage and plots it over time.
- Classifies readings as wet soil, dry soil, or dry air using calibrated thresholds.
- Dispenses an estimated 250 mL for dry soil or 300 mL for a dry-air reading.
- Controls the pump through a MOSFET module and indicates pumping with an LED.
- Waits until the next scheduled check before evaluating watering again.
- Allows the user to terminate the program with a button.

## Hardware and software

- Grove interface board connected to a computer over USB
- Soil moisture sensor
- Grove MOSFET module
- Water pump, tubing, and water container
- External battery supply for the pump
- Button and LED
- MATLAB for control, sensor readings, and live plotting

## Control logic

The program initializes the hardware, sets the next check time, and reads the sensor approximately every 0.5 seconds while updating the moisture plot. When the scheduled check time is reached, it uses the sensor reading to decide whether watering is needed.

| Sensor voltage | Classification | Response at the scheduled check |
|---|---|---|
| Above 2.2 V | Dry air | Dispense an estimated 300 mL |
| 1.85–2.2 V | Dry soil | Dispense an estimated 250 mL |
| Below 1.85 V | Wet soil | Skip watering |

These thresholds were calibrated for the sensor and setup used in this project. They are voltage-based classifications, not measurements of moisture percentage.

The pump was calibrated at approximately 1 litre per 24 seconds. Water volume is estimated from pump runtime; the system does not measure flow directly. After each check, the program schedules the next check and continues monitoring.

## Testing and results

The report includes wiring photographs, a program flowchart, console output, and moisture plots from testing.

- In the dry-soil test, the program selected a 250 mL watering cycle. The plotted sensor voltage fell from roughly 1.9–2.0 V to 1.75–1.8 V after watering, consistent with wetter soil.
- In the wet-soil test, the program skipped watering and continued monitoring.
- The console output also records termination through the button.

## Project report

[View the project report](EECS%201011%20Water%20Pump%20-%20Google%20Docs.pdf)

[Watch the demonstration and coverage](https://youtu.be/Yv3L_J7syi4)

The report documents the implementation and test results. MATLAB source files are not currently included in this repository.

## AI assistance

AI tools assisted with preparing this README. The hardware prototyping and testing were my own work.
