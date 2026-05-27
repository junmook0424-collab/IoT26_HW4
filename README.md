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

## Source Code
```python
from flask import Flask, render_template
import RPi.GPIO as GPIO

app = Flask(__name__)

GPIO.setmode(GPIO.BCM)
GPIO.setwarnings(False)
GPIO.cleanup()
GPIO.setup(23, GPIO.OUT)
GPIO.setup(24, GPIO.OUT)

led1_state = "OFF"
led2_state = "OFF"

@app.route("/")
def index():
    return render_template("index.html", led1=led1_state, led2=led2_state)

@app.route("/led1on")
def led1on():
    global led1_state
    GPIO.output(23, GPIO.HIGH)
    led1_state = "ON"
    return render_template("index.html", led1=led1_state, led2=led2_state)

@app.route("/led1off")
def led1off():
    global led1_state
    GPIO.output(23, GPIO.LOW)
    led1_state = "OFF"
    return render_template("index.html", led1=led1_state, led2=led2_state)

@app.route("/led2on")
def led2on():
    global led2_state
    GPIO.output(24, GPIO.HIGH)
    led2_state = "ON"
    return render_template("index.html", led1=led1_state, led2=led2_state)

@app.route("/led2off")
def led2off():
    global led2_state
    GPIO.output(24, GPIO.LOW)
    led2_state = "OFF"
    return render_template("index.html", led1=led1_state, led2=led2_state)

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000, debug=False)
```

## Result
![실행화면](./screenshot.png)
![데모영상](./demo.mp4)

## Note
- SSH terminal was used to run the code remotely on Raspberry Pi 5
- Photos and videos were taken separately due to SSH connection limitations
- Used RPi.GPIO instead of gpiozero due to GPIO busy issue on Raspberry Pi 5
