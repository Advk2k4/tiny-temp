
# TinyTemp: ATtiny85-Based OLED Temperature Monitor

TinyTemp is a lightweight, low-power temperature monitoring project built using the ATtiny85 microcontroller and a 0.96" SSD1306 I2C OLED display. It continuously samples analog temperature data, converts it to both Celsius and Fahrenheit, and displays it on the OLED. If the temperature exceeds a defined threshold, a "TOO HOT!" warning appears. The system uses sleep mode and watchdog timers to conserve power between measurements.

---

## 🔧 Features

- 🧠 Built using ATtiny85, AVR-GCC, and bare-metal C.
- 📺 Displays temperature in both °C and °F on an OLED screen.
- 🌡️ Alerts when temperature exceeds user-defined threshold.
- 💡 Uses Watchdog Timer for periodic wake-up and power efficiency.
- 📉 Takes multiple ADC samples to average out noise and improve accuracy.

---

## 📁 Project Structure

```
TinyTemp/
├── tinyOLED.h         # OLED + I2C library header for ATtiny
├── tinyOLED.c         # OLED + I2C library source
├── megaTempSleep.h    # Contains watchdog and sleep mode helper functions
├── makefile           # Makefile to compile the project with AVR-GCC
```

---

## 🔍 How It Works

- **Sensor Input:** Analog temperature sensor feeds data to ADC pin PB3 (ADC3) on ATtiny85.
- **ADC Averaging:** Samples are averaged to smooth readings.
- **Temperature Conversion:** Raw ADC values are converted to millivolts and then to Celsius and Fahrenheit.
- **Display:** OLED shows temperatures with a warning if the Fahrenheit value exceeds a preset max.
- **Power Saving:** After each display update, the microcontroller enters a deep sleep (power-down mode) and wakes periodically using the watchdog timer.

---

## ⚙️ Hardware Requirements

- ATtiny85 microcontroller (or ATtiny25/45)
- SSD1306 I2C OLED Display (128x64)
- LM35 or similar analog temperature sensor
- 10kΩ pull-up resistors for SDA and SCL
- USBTinyISP or equivalent AVR programmer

---

## 🚀 Getting Started

### 🔨 Build

Ensure `avr-gcc`, `avrdude`, and `make` are installed.

```bas
make
```

### ⏏️ Flash to ATtiny85

Update your `makefile` with the correct `PORT` and run:

```bash
make flash
```

---

## 🧪 Authors

Developed by Aadvik Mishra & Gautam Jayakishan  
ECE-304 Spring 2025 – University of Massachusetts Amherst

---

## 📜 License

Based on original code by Stefan Wagner  
Modified and extended under [Creative Commons BY-SA 3.0 License](http://creativecommons.org/licenses/by-sa/3.0/)
