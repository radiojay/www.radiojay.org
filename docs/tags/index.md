# RadioJay tags

## Altimeter tags

### RadioJay A2 (aka Mostag V2)

The first tag, [RadioJay A2](radiojay-a2.md) ("Altimeter"),
was developed in the context of tracking birds using Motus
around offshore wind farms where flight altitude is of prime interest.
The tag is compatible with the CTT 434Mhz radio technology deployed in Motus and extends
the packets to include live air pressure information, from which flight altitude can be calculated.

This specific version is the second prototype with the primary goal to produce a tag that
weighs 1 gram all-included (entire tag and leg loop harness).
In order to produce a dozen tags at low cost a flexible PCB substrate was used,
which is very thin and thus light-weight.
The flexibility was expected to be an issue but seemed like a worthwhile experiment to see
whether it's unworkable or not.
The tags can be stiffened using a little epoxy and fiberglass.

The tags include a 32 bit microcontroller, FSK radio, pressure sensor, accelerometer, rechargeable battery, and solar cell.

### RadioJay A1 (aka Mostag V1)

The [RadioJay A1](radiojay-a1.md) tag is the very first prototype to test the various components.
It uses a standard 1.6mm thick PCB which is way too heavy and all components are on one side
for easy testing with the intent that the components on one half would get "folded under" to the
other side on the next version, which is what happened for RadioJay A2.

## Test tags

### RadioJay T1

Test tag emitting CTT signals

### RadioJay T2

Test tag emitting both CTT and Lotek signals

## GPS tags

- [RadioJay G1](radiojay-g1.md)
