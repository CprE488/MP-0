MP-0 Report
===========

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

