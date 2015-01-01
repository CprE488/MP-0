MP-0 Report
===========

Team member contributions
-------------------------
Jeramie Vens: 50%
Adam Sunderman: 50%

describe how nes_bootloader.c currently works
---------------------------------------------
1. Initialize the board
  1. Get frame buffer address
  2. Initialize the Vtc Module
  3. Set frame buffers to all INIT_COLOR
  4. Initialize the Video DMA
2. Initialize NES core
3. Enable Cache
4. Load and play game
  1. Load zelda into ROM
  2. Reset the core
  3. Set state to playing
  4. Play game forever

Click three different green boxes
---------------------------------
1. General Settings: Set UART BAUD rate--useful for comunication and debugging.
2. DMA Controller: Set which interfaces are enabled and disabbled, useful for designating which peripherals we are using.
3. ACP Slave AXI: enable or disable ACP interface, ACP doesn't exist because there is not a wikipedia article about it.

Are these buttons, LEDs, and switches connected via the PS subsystem or the PL subsystem?
-----------------------------------------------------------------------------------------
PL because it comes into the PS system through the AXI bus.  All three are general purpose input/ouput devices.

How would you (in software) read the current state of the switches?
-------------------------------------------------------------------
Reading the value in the GPIO_DATA register at C_BASEADDR 0x41200000

Describe what print() does, and how.
------------------------------------
Print() calls outbyte() for each character in the string. It takes less memory.

VDMA Register Values
--------------------
We want to operate in circular mode and start the VDMA so we set the config register to 0b11.  The rest were setting to match the hardware settings and set the size of the buffer values.  Last was to point to the start of the memory map which held the frame buffer.

Color Values
------------
We rounded each byte to the MSN.  Therefore, 0xYZ rounds to Y when Z is less than 8 and rounds to Y+1 otherwise.

