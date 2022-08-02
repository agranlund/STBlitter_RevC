
# Graphics Card

The **ET4000** feature can be disabled with the `ET Disable` jumper.

<br>

For wiring instructions, check out this **[Example][ET4000 Wiring]**.


## Warning

This assumes a **ET4000** Card that only needs `+5V` and `GND`.

If your card requires `+12V` / `-12V`, you will have<br>
to wire this manually with the following pins.

| Voltage | Pin |
|:-------:|:---:|
| `+12V` | **B9** |
| `-12V` | **B7** |

<br>
<br>

## Interface

The interface is based on **Till Harbaum's** `STGA`. ⸢ [:globe_with_meridians:][STGA] ⸥ ⸢ [:floppy_disk:][STGA Archive] ⸥

It has only been tested with the `NVDI 5.03` `ET4000` drivers.

Other drivers like **Idek's** `NOVA` for the `STGA`<br>
or **Till's** `STGA` driver will likely also work fine.

<br>
<br>

## NVDI Driver

If you are using the `NVDI` driver you will need to<br>
configure your hardware with the `VMF-4000` tools:

1.  Select `manual` for a graphics card

2.  Set `Screenbaseaddress` to `$FEC00000`

3.  Set `Registerbaseaddress` to `$FECF03B0`

4.  Be sure to selected `16bit I/O`

5.  For the **CLUT** use the following values:

    | Type | Value |
    |:----:|:-----:|
    |  8-bit |  `00`  |
    | 15-bit |  `A0`  |
    | 16-bit |  `C0`  |
    | 24-bit |  `F0`  |

<br>
<br>

## Useful

Hints for **STGA** under **NVDI**.  ⸢ [:globe_with_meridians:][Hints] ⸥ ⸢ [:floppy_disk:][Hints Archive] ⸥

Atari drivers are quite picky about which `ET4000` they support,<br>
especially when it comes to `RAMDAC` and / or clock generator.

*I don't know the details so I tried a few cards in a machine* <br>
*that had a known working `VOFA` setup, picked one that worked* <br>
*and wired it to the `STGA` interface on this board.*

*`Atari-Home.de` is a good source for finding* <br>
*threads about using graphics card on the Atari.*

***Frank Lukas*** *there is extremely knowledgeable on the subject.*

<br>


<!----------------------------------------------------------------------------->

[Hints Archive]: https://web.archive.org/web/20211221063353/https://forum.atari-home.de/index.php?topic=12789.0
[STGA Archive]: https://web.archive.org/web/20210423201238/http://www.harbaum.org/till/atari/index.html
[Hints]: https://forum.atari-home.de/index.php?topic=12789.0
[STGA]: http://www.harbaum.org/till/atari/index.html

[ET4000 Wiring]: Resources/ET4000%20Wiring.jpg
