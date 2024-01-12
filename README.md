# RP2040-zero-meshtastic
This repo contains the hardware and software development of a fixed node based on RP2040-Zero and SX127X (SX1276 and so) LoRa modules.

# Hardware
## Parts needed:
- RP2040-Zero
- SX1276 Module
- Ipex connector
- This beautifull pcb (or some protoboard for ultra-DIY)
 
# Wiring
![](https://github.com/vidalperezbohoyo/RP2040-zero-SX1276-meshtastic/blob/main/doc/diagram.png)

| SX1276 Pin | GPIO      |
|-----------|-----------|
| SCK         | 10         |
| MOSI         | 11         |
| MISO         | 12         |
| NSS/CS        | 3        |
| DIO0        | 27        |
| DIO1        | 29        |
| DIO2         | 2         |
| RST         | 15        |
| VDD         | 3.3v     |
| GND (any)   | GND     |

| SSD1306 (or similar) | GPIO      |
|-----------|-----------|
| VCC         | 3.3v         |
| GND         | GND         |
| SDA         | 4         |
| SCL        | 5        |

# Firmware
The firmware is not the prebuilt for the pico because the LoRa module is different. Only is needed to change the **variant** file to this.  
Then compile meshtastic with: this.  
