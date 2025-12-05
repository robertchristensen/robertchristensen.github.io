# Parts List

## Processor

Adafruit QT Py - SAMD21 Dev Board with STEMMA QT

[product page](https://www.adafruit.com/product/4600)

[SAMD21 data sheet](https://onlinedocs.microchip.com/oxy/GUID-22527069-B4D6-49B9-BACC-3AF1C52EB48C-en-US-20/index.html)

[Dev Board pinout](https://learn.adafruit.com/adafruit-qt-py/pinouts)

This is a basic inexpensive board that uses a ATSAMD21E18. This is a ARM-Cortex M0+ with 256KB Flash and  32 KB RAM, which is more then enough for me.
The system does not need something more powerful, so I selected this
because it will meet the basic needs of the project. I wanted to try to
develop a project with an ARM processor.

## Rotation Sensor

Adafruit I2C Stemma QT Rotary Encoder Breakout with Encoder - STEMMA QT /
Qwiic

[product page](https://www.adafruit.com/product/5880)

I need a rotation sensor. This sensor is packaged with an onboard chip
that will count rotations. This will (hopefully) make it easier to work
with the rotary encoder while the motor is running.

## Motor Controller

Adafruit DRV8871 DC Motor Driver Breakout Board - 3.6 Max

[product page](https://www.adafruit.com/product/3190)

[DRV8871 datasheet](https://www.ti.com/document-viewer/drv8871/datasheet)

A motor controller that supports multiple directions, a variety of input
voltage, and a variety of speeds.

## Power Supply

Adafruit USB Type C Power Delivery Dummy - I2C or Switchable - HUSB238 -
STEMMA QT / Qwiic

[product page](https://www.adafruit.com/product/5991)

[HUSB238 datasheet](https://en.hynetek.com/uploadfiles/site/219/news/b038530d-67c0-4ba0-9269-de0e666cb35b.pdf)

USB-C is now widely available. Using a USB-C power supply makes power
delivery a lot easier. This supports selecting the power delivery at
different voltages, depending on the power required for the motor.

## Power Regulator

MPM3610 3.3V Buck Converter Breakout - 21 In 3.3V Out at 1.2A

[product page](https://www.adafruit.com/product/4683)

[MPM3610 datasheet](https://www.monolithicpower.com/en/documentview/productdocument/index/version/2/document_type/Datasheet/lang/en/sku/MPM3610GQV-Z/document_id/2090/)

The power pulled from USB-C can vary from 5V to 20V. That power will be
used by the motor. Power for logic systems and the processor requires
3.3V and this will be used to supply the voltage for the logic systems.
