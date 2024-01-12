# RP2040-zero-meshtastic
This repo contains the hardware and software development of a fixed node based on RP2040-Zero and SX127X (SX1276 and so) LoRa modules.

# Hardware
## Parts needed:
- RP2040-Zero
- SX1276 Module
- SSD1306 or similar I2C Oled screen compatible with Meshtastic.
 
# Wiring
![](https://github.com/vidalperezbohoyo/RP2040-zero-SX1276-meshtastic/blob/main/doc/diagram.png)

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

# Firmware
As the same module used in the firmware precompiled by Meshtastic (rpico) is not this (SX126X != SX127X), it is necessary to generate the binary ourselves. To do this, we must follow the steps outlined in this guide (it's not difficult but it takes some time). Additionally, we need to add the following folder to the **variants** directory and modify the **platform.ini** file as shown:


For compile, Ctrl + Shift + B or Ctrl + Shift + P. If all is SUCCESS, you have to upload it to the board .I get failure every time in middle of the upload with the Upload button. To solve this, Hold BOOT button of the RP2040-Zero and then connect to the PC, then copy in the folder that appears (like USB stick) the **firmware.uf2** located in the folder (inside the cloned repo): **.pio/build/rp2040-zero/**

When the copy ends, the board will reboot with the firmware installed. Then configure the region and check that there are no errors on the screen (or crash after 34 seconds).
