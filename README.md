# RP2040-zero-meshtastic
This repo contains the hardware and software development of a fixed node based on RP2040-Zero and SX127X (SX1276 and so) LoRa modules.

# Hardware
## Parts needed:
- RP2040-Zero
- SX1276 Module
- SSD1306 or similar I2C Oled screen compatible with Meshtastic.
 
# Wiring
<img src="https://github.com/vidalperezbohoyo/RP2040-zero-SX1276-meshtastic/blob/main/doc/diagram.png" alt="Wiring" height="200">  

| SX127X                  | GPIO       |   | SSD1306 (or similar) | GPIO |
|-------------------------|------------|---|----------------------|------|
| SCK                     | 10         |   | VCC                  | 3.3v |
| MOSI                    | 11         |   | GND                  | GND  |
| MISO                    | 12         |   | SDA                  | 4    |
| NSS/CS                  | 3          |   | SCL                  | 5    |
| DIO0                    | 27         |   |                      |      |
| DIO1                    | 29         |   |                      |      |
| DIO2                    | 2          |   |                      |      |
| RST                     | 15         |   |                      |      |
| VDD                     | 3.3v       |   |                      |      |
| GND (any)               | GND        |   |                      |      |

> **Note:**
> Some boards as the TTGO Lora32 uses a 22 Ohm resistor between DIO0/DIO1 and their respective GPIOs. (Without this resistors works but if TTGO puts here, may be for a reason).
# Firmware
You can use one of the precompiled firmware located into the **firmware** folder of this repo. With the method *Drag and Drop* shown 
[here](https://meshtastic.org/docs/getting-started/flashing-firmware/nrf52/drag-n-drop).

## Build your own firmware
But if you want to build your own version, follow the steps below. ⬇️

As the same module used in the firmware precompiled by Meshtastic (rpico) is not this one (SX126X != SX127X), it is necessary to generate the binary ourselves. To do this, we must follow the steps outlined in this [guide](https://meshtastic.org/docs/development/firmware/build) (it's not difficult but it takes some time).  
Additionally, we need to add the following [folder](https://github.com/vidalperezbohoyo/RP2040-zero-SX1276-meshtastic/tree/main/variants/rp2040-zero) to the **variants** directory and modify the main **platform.ini** of the proyect as shown:  
```
; PlatformIO Project Configuration File
; https://docs.platformio.org/page/projectconf.html

[platformio]
;default_envs = tbeam ; Comment this
;default_envs = pico
default_envs = rp2040-zero ; Add this
;default_envs = tbeam-s3-core
;default_envs = tbeam0.7
;default_envs = heltec-v1
;default_envs = heltec-v2_0
  
```

For compile, **Ctrl + Shift + B** or **Ctrl + Shift + P**. If all is SUCCESS, you have to upload it to the board.  
I get failure every time in middle of the upload with the **Upload** button. To solve this, hold **BOOT** button of the RP2040-Zero and then connect to the PC, then copy in the folder that appears (like USB stick) the **firmware.uf2** located in the meshtastic firmware repo folder: **.pio/build/rp2040-zero/** (This appears when compilation was OK).

As soon as the copy ends, the board will reboot with the firmware installed. Then configure the region and check that there are no errors on the screen (or crash after 34 seconds if the radio is misconnected).


# Other usefull stuff
### The 3D printed case for this LoRa module  
Here is the Thingiverse [link](https://www.thingiverse.com/thing:6429173).  

<img src="https://github.com/vidalperezbohoyo/RP2040-zero-SX1276-meshtastic/blob/main/doc/case.jpg" alt="Case" height="300">  



