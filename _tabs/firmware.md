---
title: Firmware
icon: fas fa-microchip
order: 2
published: true
---

| Model | Version | Download |
|-------|---|:----------------|
| Arylic S10 | 35 | UP2STREAM_PRO_V4, [UP2STREAM_PRO_V3](https://ota.rakoit.com/release/UP2STREAM_PRO_V3/UP2STREAM_PRO_V3-0035-99e42697-20220509.mcu.bin) |
| Arylic S50 Pro+ | 35 | [ARYLIC_S50A](https://ota.rakoit.com/release/ARYLIC_S50A/ARYLIC_S50A-0035-99e42697-20220506.mcu.bin), [ARYLIC_S50](https://ota.rakoit.com/release/ARYLIC_S50/ARYLIC_S50-0035-99e42697-20220506.mcu.bin) |
| Arylic A30+ | 35 | [ARYLIC_A30](https://ota.rakoit.com/release/ARYLIC_A30/ARYLIC_A30-0035-99e42697-20220506.mcu.bin) |
| Arylic A50+ | 35 | [ARYLIC_A50N](https://ota.rakoit.com/release/ARYLIC_A50N/ARYLIC_A50N-0035-2b814e71-20220622.mcu.bin), [ARYLIC_A50S](https://ota.rakoit.com/release/ARYLIC_A50S/ARYLIC_A50S-0034-85e6877a-20220428.mcu.bin), [ARYLIC_A50TE](https://ota.rakoit.com/release/ARYLIC_A50TE/ARYLIC_A50TE-0034-85e6877a-20220428.mcu.bin) |
| Arylic SA100 | 35 | [Rakoso_SA100_V3](https://ota.rakoit.com/release/Rakoso_SA100_V3/Rakoso_SA100_V3-0035-99e42697-20220509.mcu.bin) |
| Arylic WBC65 | 35 | [RAKOSO_C650](https://ota.rakoit.com/release/RAKOSO_C650/RAKOSO_C650-0035-f3af5f53-20220511.mcu.bin) |
| Up2Stream Mini V3 | 36 | UP2STREAM_MINI_V4, [UP2STREAM_MINI_V3](https://ota.rakoit.com/release/UP2STREAM_MINI_V3/UP2STREAM_MINI_V3-0036-30cb0ae0-20220704.mcu.bin) |
| Up2Stream Pro V3 | 35 | UP2STREAM_PRO_V4, [UP2STREAM_PRO_V3](https://ota.rakoit.com/release/UP2STREAM_PRO_V3/UP2STREAM_PRO_V3-0035-99e42697-20220509.mcu.bin) |
| Up2Stream Amp 2.0 V3 | 35 | [UP2STREAM_AMP_V3](https://ota.rakoit.com/release/UP2STREAM_AMP_V3/UP2STREAM_AMP_V3-0035-99e42697-20220509.mcu.bin) |
| Up2Stream Amp 2.0 V4/Mono | 36 | [UP2STREAM_AMP_V4](https://ota.rakoit.com/release/UP2STREAM_AMP_V4/UP2STREAM_AMP_V4-0036-30cb0ae0-20220702.mcu.bin) |
| Up2Stream Amp 2.1 | 35 | [UP2STREAM_AMP_2P1](https://ota.rakoit.com/release/UP2STREAM_AMP_2P1/UP2STREAM_AMP_2P1-0035-99e42697-20220509.mcu.bin) |
| Up2Stream Amp Sub | 31 | [ARYLIC_SUBWOOFER](https://ota.rakoit.com/release/ARYLIC_SUBWOOFER/ARYLIC_SUBWOOFER-0031-a3e827a1-20211113.mcu.bin) |
| Up2Stream Plate Amp | 35 | [ARYLIC_V20](https://ota.rakoit.com/release/ARYLIC_V20/ARYLIC_V20-0035-99e42697-20220506.mcu.bin) |
| Up2Stream Plate Amp 2.1 | 35 | [UP2STREAM_PLATE_2P1](https://ota.rakoit.com/release/UP2STREAM_PLATE_2P1/UP2STREAM_PLATE_2P1-0035-99e42697-20220509.mcu.bin) |
| Up2Stream HD DAC | 35 | UP2STREAM_HDDAC |

## Firmware version

The version read from App contains 4 numbers, eg: `4.6.337862.29`. The first 3 numbers `4.6.337862` is the version for A31/A97 module, which is the WiFi module plugged onto the base board and handle all network related tasks. And the last number `29` is the verison of the MCU on base board, which handles the audio DSP and peripherals including IR/Key/LED/Screen, etc.
So the device has 2 firmwares, and can be upgraded seperately. And firmwares listed here are for MCU only. 

## Project name

Each board has a unique project name, which is used to identify the base board. And the packed MCU firmware which ends with `.mcu.bin` will also contain this project name, to make sure the right firmware is upgraded to the base board. There’re 3 ways to get the device project name:

* Use HTTP API, http://device_ip/httpapi.asp?command=getStatusEx (remember to replace the device_ip with real IP of device), and it will return a JSON text, you could get the value with field name project.

* Use the [UpdateTool](https://drive.google.com/file/d/16b-o3TUj3oYi0pnYFdJDE8OI3pbU40TI/view?usp=sharing), after connected, it will show on the bottom left with label Project.

* For A31 based model, you also could open the built-in web management page, and it will show the project name in the settings.

## Upgrade manually

Normally you could upgrade firmware on web management page, just open web page with the device IP address, and click the Settings icon on top. It will show the page to upgrade firmware, select the file and click upgrade and waiting the progress finish. Please note that the web page does not have the progress, and normally the white LED will keep fast blinking, please make sure the power is not lost in this process and just wait the device finish the job and reboot itself.

You could use the [UpdateTool](https://drive.google.com/file/d/16b-o3TUj3oYi0pnYFdJDE8OI3pbU40TI/view?usp=sharing) to upgrade device firmware manually. And please make sure the Project Name is same, or else the upgrading will fail. Just connect to the IP of device with tool, and then select upgrade file, and click Upgrade. 

## Upgrade online

We normally will transfer firmwares to online server, and user will use API to redirect the OTA server to upgrade online.

1. Find out the IP address of your device, eg: 192.168.0.100

2. Open the redirect link on browser on PC or phone: http://device_ip/httpapi.asp?command=SetUpdateServer:http://ota.rakoit.com/alpha. Normally, it will return plain text OK.

3. Open the App, and the target device would show a new version, and you can click to upgrade.

## Note

The device will upgrade the MCU firmware to the same version with OTA server, no matter it’s higher or lower, and it will upgrade automatically when idling. And you could redirect the OTA server with the API `setUpdateServer` to an unexisting place each time when device reboot.

Have fun :-)
