# RadioHAT
Raspberry Pi PCIe HAT for radio modules

This HAT is an all-in-one radio modules development platform with the following features. 

* **Built-in logic analyzer** - All pins routed to the transceivers (SPI and various GPIO signals) are also routed to additional Raspberry Pi GPIO pins, to allow the RPi to monitor and record the state of communication pins. See the [pinalyzer repository](https://github.com/radiolib-org/pinalyzer) for details.
* **Adjustable linear voltage regulator** - To supply power-intensive transceivers, there is a dedicated LDO regulator with adjustable output. The output voltage is adjustable between 2.9 and 3.6 V.
* **Power consumption measurement** - There is a built-in INA219 current monitor which allows to measure the power consumption of the transceiver. See the [dc-powermon repository](https://github.com/radiolib-org/dc-powermon) for details.

While these features are useful, they are entirely optional. Without them, the HAT is a simple adapter board for mini-PCIe cards (half-size or full-size) and can be left with most of the components unpopulated, except for the RPi pin header, PCIe connector and the card latch.

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

* Mini PCIe 2.0 SMB pins are used for I2C
* Mini PCIe 2.0 USB pins are used for USB
* IRQs, resets and various GPIOs are connected to Mini PCIe 2.0 digital signals
* 3.3V voltage pins are used for most modules, though sometimes 5V is optionally used 

The complete pinout of the connector (and therefore the PCIe cards) is shown below.

| Pin | Signal   | Signal   | Pin |
| --- | -------- | -------- | --- |
|   1 | GPIO0    | 3V3      | 2   |
|   3 | IRQ0     | GND      | 4   |
|   5 | IRQ1     | 5V       | 6   |
|   7 | GPIO1    | NC       | 8   |
|   9 | GND      | NC       | 10  |
|  11 | RST0     | NC       | 12  |
|  13 | RST1     | NC       | 14  |
|  15 | GND      | NC       | 16  |
|  17 | NC       | GND      | 18  |
|  19 | NC       | NSS1     | 20  |
|  21 | GND      | NC       | 22  |
|  23 | NC       | 3V3      | 24  |
|  25 | NC       | GND      | 26  |
|  27 | GND      | 5V       | 28  |
|  29 | GND      | I2C_SCL  | 30  |
|  31 | PPS      | I2C_SDA  | 32  |
|  33 | NC       | GND      | 34  |
|  35 | GND      | USB_D-   | 36  |
|  37 | GND      | USB_D+   | 38  |
|  39 | 3V3      | GND      | 40  |
|  41 | 3V3      | LED0     | 42  |
|  43 | GND      | LED1     | 44  |
|  45 | SPI_SCK  | LED2     | 46  |
|  47 | SPI_MISO | 5V       | 48  |
|  49 | SPI_MOSI | GND      | 50  |
|  51 | NSS0     | 3V3      | 52  |

## Raspberry Pi pinout

The shield routes the Mini PCIe connector signals to the following Raspberry Pi GPIO header pins. The pins with prefix `SNS_` are connected to the digital signals through a series resistor and GPIO, allowing to use the RPi as a makeshift logic analyzer.

| Pin | Signal    | Signal    | Pin |
| --- | --------- | --------- | --- |
|   1 | 3V3       | 5V        | 2   |
|   3 | I2C_SCL   | 5V        | 4   |
|   5 | I2C_SDA   | GND       | 6   |
|   7 | SNS_NSS0  | SNS_SDA   | 8   |
|   9 | GND       | SNS_SCL   | 10  |
|  11 | SNS_SCK   | RST0      | 12  |
|  13 | SNS_MISO  | GND       | 14  |
|  15 | SNS_MOSI  | GPIO1     | 16  |
|  17 | 3V3       | IRQ1      | 18  |
|  19 | SPI_MOSI  | GND       | 20  |
|  21 | SPI_MISO  | RST1      | 22  |
|  23 | SPI_SCK   | NSS0      | 24  |
|  25 | GND       | NSS1      | 26  |
|  27 | NC        | NC        | 28  |
|  29 | SNS_IRQ0  | GND       | 30  |
|  31 | SNS_RST0  | SNS_GPIO0 | 32  |
|  33 | SNS_NSS1  | GND       | 34  |
|  35 | SNS_IRQ1  | IRQ0      | 36  |
|  37 | SNS_GPIO1 | GPIO0     | 38  |
|  39 | GND       | SNS_RST1  | 40  |
