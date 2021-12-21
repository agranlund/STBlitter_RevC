
[ET4000 Wiring]: Resources/ET4000%20Wiring.jpg
[Preview]: Resources/Preview.png

[STGA]: http://www.harbaum.org/till/atari/index.html
[STGA Archive]: https://web.archive.org/web/20210423201238/http://www.harbaum.org/till/atari/index.html

[Hints]: https://forum.atari-home.de/index.php?topic=12789.0
[Hints Archive]: https://web.archive.org/web/20211221063353/https://forum.atari-home.de/index.php?topic=12789.0

[Anders Granlund]: http://www.happydaze.se/


[CPLD-JED]: CPLD/STBLITTER_REVC_ATF1504.jed
[CPLD-PLD]: CPLD/STBLITTER_REVC_ATF1504.PLD

[Eagle-BRD]: Eagle/STBlitter_RevC2.brd
[Eagle-SCH]: Eagle/STBlitter_RevC2.sch

[Gerber-GBL]: Gerber/STBlitter_RevC2.GBL
[Gerber-GBO]: Gerber/STBlitter_RevC2.GBO
[Gerber-GBP]: Gerber/STBlitter_RevC2.GBP
[Gerber-GBS]: Gerber/STBlitter_RevC2.GBS
[Gerber-GL2]: Gerber/STBlitter_RevC2.GL2
[Gerber-GL3]: Gerber/STBlitter_RevC2.GL3
[Gerber-GML]: Gerber/STBlitter_RevC2.GML
[Gerber-GTL]: Gerber/STBlitter_RevC2.GTL
[Gerber-GTO]: Gerber/STBlitter_RevC2.GTO
[Gerber-GTP]: Gerber/STBlitter_RevC2.GTP
[Gerber-GTS]: Gerber/STBlitter_RevC2.GTS
[Gerber-TXT]: Gerber/STBlitter_RevC2.TXT


# ST Blitter
##### *Revision C2*

This repository provides **Blitter**, an **IDE**, a **TOS Decoder**<br>
as well as the **ET4000 Connector** for the **Atari ST(M)**.

Original designed by **[Anders Granlund]**

---

![Preview]

---

## Files

| CPLD | Eagle |
|:----:|:-----:|
| **[JED][CPLD-JED]** | **[BRD][Eagle-BRD]** |
| **[PLD][CPLD-PLD]** | **[SCH][Eagle-SCH]** |

<table>
    <tr>
      <th colspan = '6' >Gerber</th>
    </tr>
    <tr>
        <td><a href = 'Gerber/STBlitter_RevC2.GBL' ><b>GPL</b></a></td>
        <td><a href = 'Gerber/STBlitter_RevC2.GBP' ><b>GBP</b></a></td>
        <td><a href = 'Gerber/STBlitter_RevC2.GL2' ><b>GL2</b></a></td>
        <td><a href = 'Gerber/STBlitter_RevC2.GML' ><b>GML</b></a></td>
        <td><a href = 'Gerber/STBlitter_RevC2.GTO' ><b>GTO</b></a></td>
        <td><a href = 'Gerber/STBlitter_RevC2.GTS' ><b>GTS</b></a></td>
    </tr>
    <tr>
        <td><a href = 'Gerber/STBlitter_RevC2.GBO' ><b>GBO</b></a></td>
        <td><a href = 'Gerber/STBlitter_RevC2.GBS' ><b>GBS</b></a></td>
        <td><a href = 'Gerber/STBlitter_RevC2.GL3' ><b>GL3</b></a></td>
        <td><a href = 'Gerber/STBlitter_RevC2.GTL' ><b>GTL</b></a></td>
        <td><a href = 'Gerber/STBlitter_RevC2.GTP' ><b>GTP</b></a></td>
        <td><a href = 'Gerber/STBlitter_RevC2.TXT' ><b>TXT</b></a></td>
    </tr>
</table>



---

## BOM

| Component | Value | Size |
|:---------:|:-----:|:----:|
| **CPLD** | ATF1504 | |
| **R1 R2 R5 R6** | 2.2KΩ | 0805 |
| **R3 R4 R7 R8 R9** | 4.7KΩ | 0805 |
| *All Capacitors* | 0.1μF | 0805 |

**CPLD**: *Complex Programmable Logic Device*

---

## Blitter

1. Locate the jumpers in the CPU socket area.

2. `Enable / Disable` **Blitter** by setting the <br>
   `Blitter Enable` solder-jumper accordingly.

---

## IDE

By default `Interface 0` responds to the **IDE interface**.

<br>

If you wish to change this, you will have to use<br>
the soldering jumpers labeled `IDE address`.

The **IDE Interface** is determined by the following:

|  JumperA  |  JumperB  | Interface |
|:---------:|:---------:|:---------:|
|           |           |     0     |
|           | Connected |     1     |
| Connected |           |     2     |
| Connected | Connected |     3     |

<br>

If you however wish to **disable** the **IDE Interface**<br>
you will have to connect the `IDE Disable` jumper.

---

## TOS Decoding

The current firmware `no longer required the original ROM CE` from<br>
the motherboard, the **RCEI** on the leftmost header near the CPU socket.

It can fully decode `TOS1.xx`, `TOS2.xx` and `TOS3.xx`<br>
**ROMs** as well as send the `CE Signal` on the **RCEO** pin.

<br>

This feature can be disabled with the `ROM disable` jumper.

---

## Graphics Card

The **ET4000** feature can be disabled with the `ET Disable` jumper.

<br>

For wiring instructions, check out this **[Example][ET4000 Wiring]**.


#### Warning

This assumes a **ET4000** Card that only needs `+5V` and `GND`.

If your card requires `+12V` / `-12V`, you will have<br>
to wire this manually with the following pins.

| Voltage | Pin |
|:-------:|:---:|
|  +12V   |  B9 |
|  -12V   |  B7 |

<br>

#### Interface

The interface is based on **Till Harbaum's** `STGA`. ⸢ [:globe_with_meridians:][STGA] ⸥ ⸢ [:floppy_disk:][STGA Archive] ⸥

It has only been tested with the `NVDI 5.03` `ET4000` drivers.

Other drivers like **Idek's** `NOVA` for the `STGA`<br>
or **Till's** `STGA` driver will likely also work fine.

<br>

#### NVDI Driver

If you are using the `NVDI` driver you will need to<br>
configure your hardware with the `VMF-4000` tools:

1. Select `manual` for a graphics card

2. Set `Screenbaseaddress` to `$FEC00000`

3. Set `Registerbaseaddress` to `$FECF03B0`

4. Be sure to selected `16bit I/O`

5. For the **CLUT** use the following values:

    | Type | Value |
    |:----:|:-----:|
    | 8-bit|   00  |
    |15-bit|   A0  |
    |16-bit|   C0  |
    |24-bit|   F0  |

<br>

#### Useful

Hints for **STGA** under **NVDI**.  ⸢ [:globe_with_meridians:][Hints] ⸥ ⸢ [:floppy_disk:][Hints Archive] ⸥

Atari drivers are quite picky about which `ET4000` they support,<br>
especially when it comes to `RAMDAC` and / or clock generator.

*I don't know the details so I tried a few cards in a machine* <br>
*that had a known working `VOFA` setup, picked one that worked* <br>
*and wired it to the `STGA` interface on this board.*

*`Atari-Home.de` is a good source for finding* <br>
*threads about using graphics card on the Atari.*

***Frank Lukas*** *there is extremely knowledgeable on the subject.*
