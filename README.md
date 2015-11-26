# The Cockroach
The "Cockroach" is the colloquial name for our first vehicle. It was built over the summer of 2015 by DriveAI. Below is a breakdown of the various aspects of its design.

#Hardware
- The Cockroach began as a [ScooterX Baja 49cc Go-Kart](http://www.scooterx.biz/en/gas-go-karts/20-49cc-scooterx-baja-off-road-go-kart.html). 
- The frame has been heavily modified. We removed the seat and bolted a sheet of particle board to the frame in its place to house all of the electronics. A custom metal body was bolted to the existing frame to give a more car-like appearance and protect the internals. 
- A custom [3D-printed gas gas cable actuator housing](https://github.com/DriveAI/cockroach-actuator/tree/master/parts) was designed, and uses a standard size servo motor to control acceleration.
- Steering and braking were actuated using [Firgelli Automations linear actuators](https://www.firgelliauto.com/products/feedback-rod-actuator) bolted directly to the steering column and brake cable, respectively.

#Electronics
- A 12v lead acid car battery was strapped to the front of the frame to power the systems.
- The battery was connected to a combination voltage and current meter to monitor power draw and battery life.
- The electrical harness was turned on and off by a 20 amp circuit breaker, which also served as a safety device.
- The main power cables supplying the terminal blocks were 8 gauge stranded copper lines.
- Power distribustion and grounding was handled using screw-type terminal blocks.
- The visual processor and decision-making computer was an [Nvidia Jetson Tk1](http://www.nvidia.com/object/jetson-tk1-embedded-dev-kit.html).
- All visual data was collected from a [StereoLabs Zed Camera](https://www.stereolabs.com/zed/specs/) and sent to the Jetson over USB 3.0 in real time.
- Actuation was controlled by an [Arduino Mega 2560](https://www.arduino.cc/en/Main/ArduinoBoardMega2560) which communicated with the Jetson via serial over USB 2.0.
- The actuators themselves were each powered by an [Arduino PWM Motor Shield] (http://www.robotshop.com/en/10a-dc-motor-driver-arduino-shield.html) attached to the terminal blocks.
- A wireless router is bolted to the underside of the system to allow easy networking access via ethernet and good range.
- 12v to 5v conversion for the arduino and sensors was done by a [DC to DC converter](http://www.ebay.com/itm/LM2596-Buck-Step-down-Power-Converter-Module-DC-4-0-40-to-1-3-37V-LED-Voltmeter-/400802470941?hash=item5d51b05c1d:g:XyoAAOSwLa9UXJBL).

#Software
- The Jetson is running the custom ARM build of Ubuntu 14.04 that Nvidia shipped it with.
- Our perception package uses the ZED SDK and is written in (C++?).
- The Arduino actuation controller is written in their proprietary language and is compiled down into AVR.
- The software uses the serial interface built into Linux to send commands to the Arduino.
