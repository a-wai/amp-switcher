# Amp Switcher

The Amp Switcher is a device for easily switching between (guitar) amplifiers
when a single speaker cabinet is used and/or available.

It is designed so that, at any given moment:
* the guitar input is routed to the selected amp (and only this one!)
* the selected amp's output (and only this one!) is routed to the cab
* all unused amps have their input muted ("shorted" in electrical terms)
* all unused amps have a dummy (resistive) load connected to their speaker
  output

![](img/block-diagram.png)

Note: this repository only includes the electronics schematics and PCB designs.
Mechanical design and building is left to the reader's skills and imagination.

## Relays Array

This is the part responsible for the actual switching. In order to minimize the
number of different parts needed, this PCB is meant to be "universal", in the
sense that it can be used both for the "Guitar -> Amp Inputs" section (with an
optional built-in buffer) and for the "Amp Outputs -> Speaker Cab" one.

![](img/relays-array-8.png)

The board should be populated differently depending on the intended function:
* for a speaker out board, the 2W resistors (R1-R8) should be populated,
  especially when used with tube amplifiers
* guitar in boards shouldn't include those resistors, but instead the
  corresponding solder jumpers should be bridged by applying solder across them

![](img/relays-jumper-closeup.png)

The input/output section (part of the PCB on the left of J1 & K1) can also be
used in 4 different ways:
* external connector, direct routing: do not populate any component except J10
  (+12V) and **J15** (to/from external connector)
* on-board jack connector, direct routing (recommended for speaker out board):
  populate only J14 and J10, and (generously) apply solder across JPX1
* external connector, input buffer (only suitable for "guitar input" board): do
  not populate any component except J10 (+12V) and **J16** (to/from external
  connector)
* on-board jack connector, input buffer (only suitable for "guitar input"
  board): populate all components except J15 and J16

![](img/relays-io-section.png)

Finally, the PCB is split in blocks of 2 relays, with oblong holes in the board
so it can easily be broken to only keep the needed number of I/Os. This allows
the same design to be used in projects of different sizes. Of course, you can
avoid wasting material by using the properly-sized PCB: we provide design and
Gerber files for variants with 2, 4, 6 or 8 relays.

![](img/relays-bare-pcb.png)

**WARNING: although using relatively wide (2mm) PCB tracks, we recommend the
boards to be manufactured with 2oz copper weight if they are to be used with
amplifiers above 20W RMS of nominal output power.**

## Control Matrix

The control board is kept as simple as possible: it is made of a single rotary
switch, with as many LEDs as needed to indicate the currently selected amp. The
first switch position (fully counter-clockwise) is the OFF position where no
amplifier is selected; turning the switch clockwise will select amplifiers one
after another, lighting the corresponding LED on (the first being D1 -- the
leftmost one -- then D2, D3 and so on...).

![](img/control-matrix-8.png)

This PCB is meant to be mounted directly on the front panel, with screw
terminals on the opposite side of the board for connecting to the corresponding
terminals of the "Relays Array" boards. Like the latter, it also includes
oblong holes for easily resizing the PCB to your needs, and we still provide
design and Gerber files for 2/4/6/8-way variants.

Finally, a simpler (and more compact) version is also provided for 2-way
devices, using a smaller ON-OFF-ON toggle switch instead of the rotary one.

![](img/control-matrix-2-alt.png)

*Note: those familiar with matrices will likely notice the "Control Matrix"
naming isn't really accurate, as a 1xN matrix is basically an array, just like
the "Relays Array" board is; however I didn't want to use "array" in both
boards' names, and I think it sounds better that way anyway* 😉

## Licensing

Copyright 2025 Arnaud Ferraris.

3D models for the Neutrik jacks are © Inventor eFX Technology and have been
downloaded from https://www.inventfx.com/_ifxkicad/_ifxkicadxtra.htm

3D models for the rotary and toggle switches aren't included due to licensing
restrictions, but they can be downloaded from https://componentsearchengine.com
* [CK1049](https://componentsearchengine.com/part-view/CK1049/Lorlin) rotary
  switch
* [A105SYZQ04](https://componentsearchengine.com/part-view/A105SYZQ04/TE%20Connectivity)
  toggle switch

This source describes Open Hardware and is licensed under the CERN-OHL-S v2.

You may redistribute and modify this source and make products using it
under the terms of the CERN-OHL-S v2 (https://ohwr.org/cern_ohl_s_v2.txt).

This source is distributed WITHOUT ANY EXPRESS OR IMPLIED WARRANTY, INCLUDING
OF MERCHANTABILITY, SATISFACTORY QUALITY AND FITNESS FOR A PARTICULAR PURPOSE.
Please see the CERN-OHL-S v2 for applicable conditions.

Source location: https://github.com/a-wai/amp-switcher

As per CERN-OHL-S v2 section 4, should You produce hardware based on this
source, You must where practicable maintain the Source Location visible on the
PCBs and user documentation of the Amp Switcher or other products you make
using this source.
