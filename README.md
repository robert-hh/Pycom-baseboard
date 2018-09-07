Baseboard: Simple baseboard for PyCom development modules

This board does not use SMD components. Instead low price modules for the USB/UART
bridge and the SD card adapter are used. The USB/UART bridge is the red FTDI
module, which are sold at prices of $1.5 on. It has to be set to 3.3 V.
The SD card module is the one of Pololu, which is also widely available.
Pictures of the modules are included in the repository. Depending on the
soldered connectors, the board can also be used for WiPy1. Artwork on the board indicates, how the Pycom modules have to be inserted.

The board also carries the two transistor logic used by espressif to switch into
bootstrap mode. The Pycom command line updater pycom-fwtool-cli supports that
with the -r option. The graphical variant does not. If you are building The
firmware yourself, you have to change application.mk at the command for
flashing. Change it into:

  ESPTOOLPY_SERIAL = $(ESPTOOLPY) --port $(ESPPORT) --baud $(ESPBAUD)

especially, remove  "--before no_reset --after no_reset"

Also on the board:
- connections for a reset button, if the board is placed into a closed box.
- A JST2 connector for a battery. There is no charging circuit on the board,
but a diode is foreseen to decouple the battery from the USB/UART bridge. If
you do not need that, solder a wire. Depending on your preference, a Schottky
diode or a silicon diode can be used. Schottky diodes have a substantial
reverse current.  

The metal areas at the mounting holes are connected to GND. That is favorable
if you put the whole board into a metal box, used as ground plane for a Lora or
LTE antenna. If that gets a problem, use Nylon screws.
