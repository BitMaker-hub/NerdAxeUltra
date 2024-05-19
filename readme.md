```
Closed Source is Antithetical to Bitcoin
```
# The NerdAxe
NerdAxe is a fork from bitaxe Ultra with fullcolor display graphics. NerdAxe is indented to be an upgrade board for these who have a NerdMiner and would like to have more powerful mining features without losing the NerdMiner essence. That's why NerdAxe is currently controlled by the common board used on Nerdminer project called TTGO-TDisplayS3.

The following fork could not be possible without the previous work of @skot & bitaxe devs.

Upgrade your NerdMiner experience throught this addon board and start playing with ASICs

![NerdAxeUltra design](doc/NerdAxeGuithub.png)

## Goals
- **Plug&Play**: your NerdMiner board and convert it into a NerdAxe.
- **Standalone**: can mine directly to your pool over WiFi. No External computer needed.
- **Embedded**: low cost, low maintenance, high availability, high reliability, low power.
- **ASIC**: based on the very, very efficient BM1366 from Bitmain.
- **Versatile**: solo/pool mining, autotune power/heat/efficiency.
- **Open Source**: All design files are provided.

## Features
- **TTGO-TDisplay** ESP32s3 wifi microcontroller display board
- **TI TPS40305** buck regulator steps down the 5V input to power the BM1366
- **Maxim DS4432U+** current DAC digitally adjusts the BM1366 core voltage from 0.04V to 2.4V
- **TI INA260** power meter measures the input voltage and current of the miner
- **Microchip EMC2101** PWM controls the fan and monitors tach output. Measuring internal die temp isn't working.
- 0.91" **SSD1306 OLED** I2C Display Module 

## Software & Firmware
- Check the software over the [ESP-Miner Nerdaxe version](https://github.com/BitMaker-hub/ESP-Miner-NerdAxe). This firmware has been adapted to use TTGO board and uses LVGL as graphic interface lib.
- You can flash NerdAxe firmware using the folowing firwmare flash tool:
1. Get a TTGO T-display S3 
1. Get a NerdAxe board
1. Go to flasher online tool: https://flasher.bitronics.store/ (recommend via Google Chrome incognito mode)

## The DIY area

### Asic BM1366
- The BM1366 is a undocumented SHA256 mining ASIC from Bitmain. It's mostly used in the Antminer S19XP
- Bitmain claims the BM1366 has 0.021J/GH efficiency
- The BM1366 is available (new) for around $15 each in small quantities.
- The BM1366 has a different footprint and pinout from the BM1397 and BM1387 in previous bitaxe.
- The BM1366 appears to roll more than just the nonce on the chip. This is great news, because it allows much longer serial chains of ASICs and new work doesn't need to be sent as often.


### Other components & build troubleshooting
- [BM1366 from NBTC on AliExpress](https://www.aliexpress.us/item/3256804709142138.html). You can use BM1366AL or AG. 
- [40x40mm heatsink and 5V fan](https://www.aliexpress.com/item/2251832861666365.html) from a random AliExpress seller. At least half of these arrived broken in some way. But they are cheap and the working ones do keep the BM1387's nice and cool when used with some thermal compound.
    - Swap this fan with the [Noctua NF-A4x10](https://noctua.at/en/products/fan/nf-a4x10-pwm) 5V 4-Pin fan for a much more pleasant experience.
- The BM1366 serial port is 1.8V. These pins are broken out, but the main idea is to communicate with the BM1366 from the ESP32
- Board is designed with [KiCad 7](https://www.kicad.org) design files
- All of the parts on the board are listed in the KiCad BOM
- Check out [building.md](building.md) for PCB ordering tips
- Check out [assembly.md](assembly.md) for assembly tips

### Power Supply Requirements
- [5VDC Power supply](https://www.amazon.com/BTF-LIGHTING-Plastic-Adapter-Transformer-WS2812B/dp/B01D8FM4N4). Should be capable of over 20W

### ESP32 Programming Requirements
To program the onboard ESP32 the old way, you need the following tools;

- [ESP-Prog](https://www.digikey.com/en/products/detail/espressif-systems/ESP-PROG/10259352) ESP32 Programmer
- [TC2030-IDC-NL](https://www.tag-connect.com/product/tc2030-idc-nl) Tag Connect Cable
- [TC2030-CLIP](https://www.tag-connect.com/product/tc2030-retaining-clip-board-3-pack)
- This is best done with VSCode and the Espressif plugin


