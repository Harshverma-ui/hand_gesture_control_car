 Pico Hand Gesture RC Car
This project outlines the construction of a remote-controlled car that is operated by hand gestures. The system uses two Raspberry Pi Picos
 for the transmitter and receiver, 
communicating wirelessly via nRF24L01 modules.

The transmitter unit uses an MPU-6050 accelerometer/gyroscope to detect the tilt of the user's hand, which is then translated into 
driving commands for the car.

Features 
Intuitive Control: Drive a car by simply tilting your hand forward, backward, left, or right.
Wireless Communication: Employs reliable 2.4GHz communication using nRF24L01 modules.
Modular Code: Professional, object-oriented code structure for clarity, maintenance, and scalability.
Real-time Response: Low-latency control suitable for maneuvering the car.
Safety Failsafe: The car automatically stops if it loses the signal from the transmitter.


Hardware Required 
Transmitter Unit:
1 x Raspberry Pi Pico
1 x nRF24L01 Wireless Transceiver Module
1 x MPU-6050 Accelerometer/Gyroscope Module
Jumper Wires
A power source (e.g., USB power bank)

Receiver Unit (Car):
1 x Raspberry Pi Pico
1 x nRF24L01 Wireless Transceiver Module
1 x L298N or similar H-Bridge Motor Driver
1 x 2WD or 4WD Car Chassis with DC Motor
A 7.4V - 12V battery pack to power the motors and Pico.

Jumper Wires

Connections (in Detail) 🔌
1. Transmitter Unit Wiring
This unit reads hand gestures and sends commands.

Component	Pin	Raspberry Pi Pico (Transmitter)
MPU-6050	VCC	3.3V OUT (Pin 36)
GND	GND (Pin 38)
SCL	GP5 (Pin 7) - I2C0
SDA	GP4 (Pin 6) - I2C0
nRF24L01	VCC	3.3V OUT (Pin 36)
GND	GND (Pin 38)
CSN	GP13 (Pin 17) - SPI1
CE	GP12 (Pin 16)
SCK	GP10 (Pin 14) - SPI1
MOSI	GP11 (Pin 15) - SPI1
MISO	GP8 (Pin 11) - SPI1


2. Receiver Unit Wiring
This unit receives commands and drives the car.

Component	Pin	Raspberry Pi Pico (Receiver)
nRF24L01	VCC	3.3V OUT (Pin 36)
GND	GND (Pin 38)
CSN	GP13 (Pin 17) - SPI1
CE	GP12 (Pin 16)
SCK	GP10 (Pin 14) - SPI1
MOSI	GP11 (Pin 15) - SPI1
MISO	GP8 (Pin 11) - SPI1
L298N Driver	ENA	GP18 (Pin 24)
IN1	GP16 (Pin 21)
IN2	GP17 (Pin 22)
ENB	GP21 (Pin 27)
IN3	GP20 (Pin 26)
IN4	GP19 (Pin 25)
+12V/VIN	Battery Positive (+)
GND	Battery Negative (-) and Pico GND


Software & Libraries 
This project requires a specific library for the nRF24L01 module.
MicroPython Firmware: Ensure both Picos are flashed with the latest MicroPython firmware.
Thonny IDE: Use Thonny for an easy interface to upload files to your Picos.

nRF24L01 Library:
Download the official MicroPython nRF24L01 library from here.

Save this file as nrf24l01.py.
Using Thonny, upload this nrf24l01.py file to both of your Raspberry Pi Picos.


Project Files & Usage 
You will need to save and upload the following code files to your Picos.

On the Transmitter Pico:
Save the code below as transmitter.py.
Upload transmitter.py and nrf24l01.py to this Pico.
Rename transmitter.py to main.py on the Pico if you want it to run automatically on boot.

On the Receiver (Car) Pico:
Save the MotorDriver class code below as motordriver.py.
Save the main receiver code as receiver.py.
Upload receiver.py, motordriver.py, and nrf24l01.py to this Pico.
Rename receiver.py to main.py on the Pico for auto-run.

To operate:
Power on both the transmitter and the receiver.
Hold the transmitter flat in your palm to stop the car.
Tilt your hand forward to move forward, backward to reverse, and left/right to turn.
