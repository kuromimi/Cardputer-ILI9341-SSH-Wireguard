# SSH Client for Cardputer-adv with ILI9341 LCD panel
SSH client on Cardputer-Adv with 2.8" ILI9341 LCD panel (320x240).

<img width="300" ALT="Normal font size" src="https://github.com/user-attachments/assets/d9a4a4ac-293e-44ef-bae2-18f9f969df09" /> 
<img width="300" ALT="Font size x2" src="https://github.com/user-attachments/assets/dd5ea331-df9a-46d0-938f-1ba8c4fb4dbb" />

This project is based on:
- Blaž Pivk [M5-SSH-Wireguard](https://github.com/bpivk/M5-SSH-Wireguard)
- AndyAi [ILI9341(320x240) LCD support](https://github.com/AndyAiCardputer/zx-spectrum-cardputer-ili9341)

![Version](https://img.shields.io/badge/version-1.0-blue)
![Platform](https://img.shields.io/badge/platform-ESP32--S3-green)
![Display](https://img.shields.io/badge/display-ILI9341%20320x240-orange)

## Hardware Requirements
- M5Stack Cardputer-Adv (ESP32-S3)
- 2.8" ILI9341 SPI Display Module (320x240)
- LCD cable via 14pin-EXT header on Cardputer-adv
- SD Card (FAT32) for storing SSH config

## Wiring: Cardputer-Adv EXT Connector → ILI9341

| EXT pin | FUNC  | ILI9341 | Description      |
|:-------:|-------|---------|------------------|
| 6       | 5VOUT | 1 VCC   | +5V Power        |
| 4       | GND   | 2 GND   | Ground           |
| 13      | G5    | 3 CS    | Chip Select      |
| 1       | G3    | 4 RESET | Reset            |
| 5       | G40   | 5 DC/RS | Data/Command     |
| 9       | G14   | 6 MOSI  | SPI Data In      |
| 7       | G40   | 7 SCK   | SPI Clock        |
| 3       | G4    | 8 LED   | Backlight-Enable |
| 11      | G39   | 9 MISO  | SPI Data Out     |

> [!IMPORTANT]
> The wiring on EXT changed in two places from AndyAi's original configuration.
> - pin2 -> pin6 (5IN isnot appropriate as power source)
> - pin6 -> pin3 (BL-EN shouldnot be 5V. Routed to GPIO4)

> [!NOTE]
> The display and SD card share the SPI bus (SPI3_HOST). SD card CS is on GPIO 12.

## Notes
- For connecting the LCD panel, please refer to [AndyAi's YouTube video](https://www.youtube.com/watch?v=ucNRMeOsK64)
- For build code and SSH/Wireguard configuration, please refer to the original [M5-SSH-Wireguard](https://github.com/bpivk/M5-SSH-Wireguard)
- LCD's backlignt is controlled by BL-EN signal (3.3V), which is routed to GPIO4 as configured for PWM.
- AndyAi's LCD cover is for panels without a touch panel. I redesigned the cover because I use a LCD unit having touch panel. I removed the pin header from LCD's PCB and wired them directly. Attaching the STL file for reference. The thickness of LCD panel including the SD card slot is designed to be 8.8mm.
- The first WG connection may result in "Host is unreachable" error. In that case, please retry connection. If it keeps failing, try power-OFF-ON cycle (This problem should be fixed in the future)
- I just merged two guys' deliverables. Can't enough to say thank to Blaž Pivk and AndyAi !!!

## License

MIT license
