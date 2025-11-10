# User Manual

## Setup

TODO: Write about how to set up the system. This involves:

- How to set up the motor
- How to plug in the motor
- How to plug in the rotation sensor
- How to connect the main logic controller with the I/O board
- How to connect the buttons to the I/O board
- How to connect the pedal to the I/O board

## Interface

The user input consists of three buttons and one pedal. The buttons are:

- Button Up
- Button Down 1
- Button Down 2

**Button Up** will move the motor up. It will move in increments equal to that of
**Button Down 2**. When the button is pressed, it will move the planer *up* by
1/16 of an inch.

**Button Down 1** and **Button Down 2** will move the planer *down* by 1/32 of an
inch or 1/16 of an inch respectively.

If any of the buttons are pressed and held, they will move into **continuous mode**.
The motor will continue to move up or down continuously until any of the buttons
are pressed *or* any of the limit switches are triggered.

### Foot Pedal

When a button is pressed, the button will illuminate. Whichever button is
illuminated is the button that is controlled when pressing the foot pedal.
Pressing the foot pedal will behave exactly as if you pressed the illuminated
button, including press-and-hold features.

The foot pedal does not need to be connected for the system to function. The buttons
will continue to illuminate, indicating the last button pressed. A disconnected pedal
should not degrade the system.

### Limit Switch

Limit switches can be added to give bounds for the continuous mode of the
motor. When running in continuous mode, the motor will continue to move up or
down until a button is pressed or the limit switch is triggered. If a button is
tapped (not held), the limit switch will **not** stop the motor from
overextending.

