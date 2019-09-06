# Begonia
A GreatFET Neighbor for writing firmware to the IM-Me or YARD Stick One.

Required KiCad dependency:

https://github.com/greatscottgadgets/gsg-kicad-lib

If you are using git, the preferred way to install gsg-kicad-lib is to use the
submodule:

```
git submodule init && git submodule update
```

## Usage Instructions

Choose whether or not you want Begonia to provide power to the target device.  You can have the target device self-powered at 3.3 V or you can have the Begonia provide power by setting the power switch to ON.  I recommend that you supply power from the Begonia, but, if you do this, you must be sure that the target's own power source is disconnected first.  The indicator LED on Begonia shows you when target power is detected, either from the Begonia supply or from the target's supply.

Being careful to use the correct orientation, press the spring pins firmly against the target's programming test points.  Make sure that the power indicator LED is activated.  While holding Begonia against the target, use the greatfet swra124 program.  (FIXME: This doesn't actually work yet as you need [firmware](https://github.com/Maescool/greatfet/tree/swra124) that has not yet been pushed to master, and you need to bodge a [pin assignment error](https://github.com/greatfet-hardware/begonia/issues/1).)

## Pin Usage

signal  | pin   | alt1  | alt2
--------|-------|-------|-----
DC      | J1.38 |       |
DD      | J1.39 |       |
RESET_N | J1.37 | J1.29 | J1.36

J1.38 and J1.39 are the SCK and MOSI pins of the primary SPI interface.  J1.37 is the SSEL pin for that SPI interface.  It is used here because Begonia is not expected to be useful in a stacked configuration with other neighbors.  If required, solder jumpers can be used to enable one of the alternative RESET_N pins instead.
