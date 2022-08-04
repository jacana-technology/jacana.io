+++
title = "Part 1: Introduction and Background"
date = 2022-08-03T17:03:34-07:00
draft = true
tags = []
categories = []
series = "ulx3s-doom"
+++

![7o301kk6v5f91.jpg](:/41d78c8f6746444bbf2a906e822e4d2e)
*A cactus can technically run DOOM, but the frame rate is awful (from [Reddit](https://www.reddit.com/r/hmmm/comments/wdrf44/hmmm/))*

## Introduction
It's a right of passage to get an embedded system (or any system, really) [to run DOOM](https://www.reddit.com/r/itrunsdoom/). I was rummaging around my box of development boards recently and I rediscovered my awesome [ULX3S](https://radiona.org/ulx3s/). It's based around the Lattice ECP5 FPGA, which, thanks to the amazing work of a huge community of people, has a [fully open-source toolchain](https://github.com/YosysHQ/oss-cad-suite-build) that supports many other boards and FPGA vendors. In addition to the ECP5, the ULX3S also sports:
* 32MB SDRAM
* HDMI port (called GPDI or General-Purpose Differential Interface for licensing reasons)
* Audio jack
* Buttons, switches, & LEDs
* A bunch of GPIO
* FLASH memory
* A whole ESP32 module for Bluetooth and WiFi
* Lots more

There are several other [DOOM-on-FPGA](https://www.youtube.com/watch?v=3ZBAZ5QoCAk) projects out in the wild, even one [that implements the game in gateware (no CPU)](https://twitter.com/sylefeb/status/1258808333265514497?s=20), and another that uses a [custom processor instruction set architecture](https://github.com/mbitsnbites/mc1-doom). My goal with this was to learn how to get all the way from the logic gates all the way to running applications in Linux only using open source tools. That's `FPGA -> SoC -> Bootloader -> OS -> DOOM` all with FOSS tooling. Maybe one day I'll even run it on [open-source silicon](https://skywater-pdk.readthedocs.io/en/main/).

I'm breaking the project up into a few milestones to make sure that I have the tools set up correctly and that I can tweak things at the various layers without everything breaking. This is important because each piece relies on the pieces below it to function. The plan is thus:

1. FPGA
  1. Accumulate resources like datasheets, manuals, tutorials, and similar projects to serve as reference materials
  2. Download and install the FPGA toolchain
  3. Flash a pre-built bitstream of the "Hello World" Blinky project to verify that my computer can communicate with the ULX3S
  4. Clone the Blinky project and run the synthesis, placing, and routing tools verify that HDL-to-bitstream generation works
  5. Modify the speed or pattern of the blinking LED in the source code and re-upload to verify basic modifications work
2. System-on-a-Chip
	1. Research SoC options for running Linux on an FPGA
	2. Download and flash pre-built SoC bitstream
	3. Clone design files, build bitstream, and flash to FPGA
	4. Explore source code and make a small modification to the design before building and uploading again
3. Binary interface, bootloader, root FS, & OS
	1. Download and transfer via serial port pre-built SBI, root filesystem, and Linux system with included bootloader. Verify Linux is running.
	2. Clone source projects for each of the above. Build the items, and transfer them to the FPGA
	3. Explore source code and make a small modification to the design before building and uploading again. Also speed up the transfer process since the default method is very slow.
4. Graphics on Linux
	1. Investigate the ways to support graphics in embedded Linux and the ULX3S
	2. Choose a solution and try to find pre-built binaries to test with
	3. Clone necessary projects and build the graphics stack necessary to run Doom
6. DOOM
	1. Get a WAD file
	2. Clone Chocolate DOOM
	3. Build it natively and/or cross-compile it
	4. Play DOOM