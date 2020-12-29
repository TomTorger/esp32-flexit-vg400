# Flexit SP 30

This project is still in progress. I blew a relay on the main board in this process. I believe that the resistor for the relay controlling "high" fan speed might be too small.

### Implementation for esp32 and Home Assistant
 - esp32
 - [SP425 controller board](https://www.flexit.no/produkter/ventilasjonsaggregat/utgatte_modeller/tilbehor_aggregater_utgatte_modeller/sp425_styringskort_for_sentralstyring_sd/styringskort_datastyring_sp425/)
 - 3x3V relays
 - Network cable (RJ45)
 - Prototyping board
 - 3x 1kOhm resistors
 - 2x 2kOhm resistors
 - 1x 4kOhm resistor
 - Wires

<img src="https://github.com/TomTorger/no.almli.flexit.zuno/blob/master/docs_esp32/esp32_protoboard_phase1.jpg" width="1173" height="787">

### Other hardware
 - Rpi4

### Software
 - Home Assistant running in docker container
 - Esphome running in docker container


Flexit SP 30 panel to Z-UNO.

### Hardware

- [Z-UNO](https://products.z-wavealliance.org/products/1825)
- [SP425 controller board](https://www.flexit.no/produkter/ventilasjonsaggregat/utgatte_modeller/tilbehor_aggregater_utgatte_modeller/sp425_styringskort_for_sentralstyring_sd/styringskort_datastyring_sp425/)
- 3 x 3 V relays
- 3 x 817 optocouplers
- 4 x DS18B20 temperature sensors 
- RJ45 wire
- breadboard
- resistors
- wires

### Build instructions:

<img src="https://balmli.github.io/no.almli.flexit.zuno/circuit.png" width="1173" height="787">

Connect the three 3 V relays to the Z-UNO:
- Z-UNO, pin  9: to relay 1 in
- Z-UNO, pin 10: to relay 2 in
- Z-UNO, pin 11: to relay 3 in
- 3V to relay Vin
- GND to relay GND-in

Connect the fan RJ45 wire to the breadboard:
- wire pin 3: to a diode, and then to relay 3 out
- wire pin 3: with a 1 kΩ resistor to optocoupler 3 input 
- wire pin 4: to relay 1,2,3 GND-out
- wire pin 5: to a 2.2 kΩ resistor, and then to relay 1 out
- wire pin 5: with a 1 kΩ resistor to optocoupler 1 input 
- wire pin 6: to a 2.2 kΩ resistor, and then to relay 2 out
- wire pin 6: with a 1 kΩ resistor to optocoupler 2 input 
- wire pin 7: to optocoupler 1,2,3 GND-in 

Connect the three optocouplers to the Z-UNO:
- optocoupler 1 out: to Z-UNO, pin A1
- optocoupler 2 out: to Z-UNO, pin A2
- optocoupler 3 out: to Z-UNO, pin A3
- optocoupler 1,2,3 GND-out: with 1 kΩ resistors to GND

Connect the four DS18B20 temperature sensors to the Z-UNO:
- Z-UNO, pin 12: to DS18B20 data pin
- 4.7 kΩ pullup resistor for DS18B20 data pin
- 5V to DS18B20 5V pins
- GND to DS18B20 GND pins

Connect power to the Z-UNO:
- Z-UNO, USB: power source
- Z-UNO, GND


### Firmware

Upload to Z-UNO by:

- install the Z-UNO software version 2.1.5 for Arduino.  See '[here](https://z-uno.z-wave.me/install)' for instructions.
- upload '[firmware](https://github.com/balmli/no.almli.flexit.zuno/blob/master/Flexit_SP30_ZUNO/Flexit_SP30_ZUNO.ino)'.

