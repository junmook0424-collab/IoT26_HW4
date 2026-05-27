# IoT26-HW04 - Raspberry Pi Web Server using Flask to Control GPIOs

## Objective
Use RPI to create a standalone web server with a Raspberry Pi 
that can toggle two LEDs using Flask.

## Circuit
- LED1 (+) : GPIO 23 (pin16)
- LED1 (-) : GND
- LED2 (+) : GPIO 24 (pin18)
- LED2 (-) : GND
- Resistor : 220Ω

## How it works
- Access web server via browser
- Click LED ON/OFF buttons to control LEDs
- Web server runs on port 5000

## Installation
```bash
pip3 install flask
```

## How to Run
```bash
cd ~/hw4
python3 app.py
```

## Access
