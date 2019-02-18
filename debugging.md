---
title: Debugging the MMU2 connection
---

# Debugging the MMU2 connection

If you encounter issues with the communication between the printer board and the MMU2, please enable

```
#define MMU2_DEBUG
```
in Configuration_adv.h and connect a serial terminal to the USB port of your printer board using Pronterface, Repetier Host, 
Octoprint, or Arduino IDE.

The following describes a startup sequence without issues
> This is the debug output you should see in the serial terminal

## Startup sequence 

 * Power on or reset
 * Marlin bootscreen, MMU2 will do its init sequence: different LEDs lighting up, idler drum will move/home
 * > _Marlin bugfix-2.0.x_ (or whatever version you are using)
 * > _MMU <= reset_
 * MMU2 will do its init sequence again
 * > _MMU => 'start'_
 * > _MMU <= 'S1'_
 * > _MMU => 103_ (value depends on the MMU2 firmware version)
 * > _MMU <= 'S2'_
 * > _MMU => 212_ (value depends on the MMU2 firmware version)
 * > _MMU <= 'M1'_ (only if you enabled 12V mode in Configuration_adv.h)
 * > _MMU => ok_ (only if you enabled 12V mode in Configuration_adv.h)
 * > _MMU <= 'P0'
 * > _MMU => 0
 * > _MMU - ENABLED
 
  ## First tool change
 
 When a tool change command like T0 is sent the first time, the following should happen
 
  * > MMU <= 'T0'
  * MMU2 will home the selector and load filament from the first lane to the extruder
  * > MMU => 'ok'
 
