# RadioHAT
Raspberry Pi PCIe HAT for radio modules

The HAT is a simple adapter board for mini-PCIe cards (half-size or full-size). The cards themselves house various RF modules.

## RadioHAT
![RadioHAT](https://github.com/radiolib-org/RadioHAT/releases/latest/download/RadioHAT-3D_top.png?raw=true)

## Card for modules from Dorji
![RadioHAT Dorji card](https://github.com/radiolib-org/RadioHAT/releases/latest/download/RadioHAT_Card_Dorji-3D_top.png)

## Card for modules from GNice-RF
![RadioHAT GNice-RF card](https://github.com/radiolib-org/RadioHAT/releases/latest/download/RadioHAT_Card_GNiceRF-3D_top.png)

## Card for modules from Ebyte
![RadioHAT Ebyte card](https://github.com/radiolib-org/RadioHAT/releases/latest/download/RadioHAT_Card_Ebyte-3D_top.png)

## Mini PCIe connector pinout
Different vendors (RAK Wireless, Waveshare, SeeedStudio and others) offer radio modules in the mini-PCIe card form factor. However, there seems to be no consensus on any specific pinout. Naturally, RadioLib defines its own version to add to the confusion. However, we try to adhere to the standard Mini PCIe 2.0 pinout in the following ways:

* Only 3.3V voltage pins are used
* Mini PCIe 2.0 SMB pins are used for I2C
* Mini PCIe 2.0 USB pins are used for USB
* IRQs, resets and various GPIOs are connected to Mini PCIe 2.0 digital signals

The complete pinout of the connector (and therefore the PCIe cards) is shown below.

| Pin | Signal   | Signal   | Pin |
| --- | -------- | -------- | --- |
|   1 | GPIO0    | 3V3      | 2   |
|   3 | IRQ0     | GND      | 4   |
|   5 | IRQ1     | NC       | 6   |
|   7 | GPIO1    | NC       | 8   |
|   9 | GND      | NC       | 10  |
|  11 | RST0     | NC       | 12  |
|  13 | RST1     | NC       | 14  |
|  15 | GND      | NC       | 16  |
|  17 | NC       | GND      | 18  |
|  19 | NC       | NC       | 20  |
|  21 | GND      | NC       | 22  |
|  23 | NC       | 3V3      | 24  |
|  25 | NC       | GND      | 26  |
|  27 | GND      | NC       | 28  |
|  29 | GND      | I2C_SCL  | 30  |
|  31 | PPS      | I2C_SDA  | 32  |
|  33 | NC       | GND      | 34  |
|  35 | GND      | USB_D-   | 36  |
|  37 | GND      | USB_D+   | 38  |
|  39 | 3V3      | GND      | 40  |
|  41 | 3V3      | LED0     | 42  |
|  43 | GND      | LED1     | 44  |
|  45 | SPI_SCK  | LED2     | 46  |
|  47 | SPI_MISO | NC       | 48  |
|  49 | SPI_MOSI | GND      | 50  |
|  51 | SPI_NSS  | 3V3      | 52  |


TODO:
 * split digital signals to allow multiple modules on a single card
 * add RPi pinout to readme
