---
title: Wiring the MMU2 to your printer board
---

# Wiring the MMU2 to your printer board

The most important part here: a serial connection is used for communication between the printer board and the MMU2. Your options when using a RAMPS board are described [here](RAMPSserial).

The 4pin (2 red/2 black) power cable will go to your power supply. Prusa uses 24V on the Mk3, but 12V will also work.

The signal cable (5pin has the following connections

* +5V - blue wire
* RX - white wire
* TX - green wire
* RESET - brown wire

To wire the MMU2 to your printer board you have to connect

* the blue wire to a free 5V pin,
* RESET to a free digital pin (optional)
* RX (white) to TX on the printer board
* TX (green) to RX on the printer board

The RESET connection is optional but recommended. You can also enable MMU2 software reset in Marlin if there are no free digital pins on your board.
