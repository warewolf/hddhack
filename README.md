General notes:

Dump an image:

bootstrap
> dump_image 0xFFFF0000.bin 0xFFFF0000 0x00002000

> stack
dump_image 0x4006000.bin 0x4006000 0x00010000


Display bytes:

> mdw 0xFFFF0000 0x50

3.3v + 4.7k ohm = 0x1C00A846


CON1 pins

(I apologize, the colors here are colors for wires I have soldered, heh)


### 88i6745 to CON1 to 0x1C00A846 io port value to bitflip to high/low ###

| Test Wire |  CON1 pin | 0x1C00A846 value  | bit flipped      |           LSR#13 | LSR#9   | status        | 88i6745 pin  | fw function
| --------- | --------- | ----------------- | ---------------- | ---------------- | ------  | ------------- | -------- | ------------
| normal    | XX        | 0xc802            | 1100100000000010 |              110 | 1100100 | normal H/L    | lots     |
| --------- | --------- | ----------------- | ---------------- | ---------------- | ------- | ------------- | -------- | ------------
| yellow    | 28        | 0xc800            | 0000000000000010 |              000 | 0000000 | HIGH          | 43 |
| green     | 26        | 0xc806            | 0000000000000100 |              000 | 0000000 | low           | 44 |
| blue      | 24        | 0xc80a            | 0000000000001000 |              000 | 0000000 | low           | 46 |
| violet    | 22        | 0xc812            | 0000000000010000 |              000 | 0000000 | low           | 48 |
| black     | 20        | 0xc822            | 0000000000100000 |              000 | 0000000 | low           | 49 |
| brown     | 18        | 0xc842            | 0000000001000000 |              000 | 0000000 | low           | 50 |
| red       | 16        | 0xc882            | 0000000010000000 |              000 | 0000000 | low           | 51 |
| yellow    | 06        | 0xc902            | 0000000100000000 |              000 | 0000000 | low           | 52 | 
| orange    | 32        | 0xca02            | 0000001000000000 |              000 | 0000001 | low           | 41 | LSR#9
| black     | 38        | 0xcc02            | 0000010000000000 |              000 | 0000010 | low           | 37 | LSR#9
| brown     | 36        | 0xc002            | 0000100000000000 |              000 | 0000100 | HIGH          | 38 | LSR#9
| red       | 34        | 0xd802            | 0001000000000000 |              000 | 0001000 | low           | 40 - to 3.3v |
| n/a       | n/a       | 0xe802            | 0010000000000000 |              001 | 0010000 | low           | 104 - P13 to 3.3v - R72 to 3.3v|
| n/a       | n/a       | 0x8802            | 0100000000000000 |              010 | 0100000 | HIGH          | 106 - P14 to ground | high = skip RAM test ?
| n/a       | n/a       | 0x4802            | 1000000000000000 |              100 | 1000000 | HIGH          | 107 - P15 to ground   | run RAM test

#### Notes from Doomer, hddguru forums
http://forum.hddguru.com/viewtopic.php?t=20324&f=13&start=20#p136913

"E62" from (2061-701499-e00) to GND makes 0x8000 -> inversed bit 0x16 (actually bit 16) of port 0x1C00A846 - so this is P15, 6745 pin 107
"E61" from (2061-701499-e00) to GND makes 0x4000 -> inversed bit 0x15 (actually bit 15) of port 0x1C00A846 - so this is P14, 6745 pin 106

Ram test = 0xFFFF01BC, triggered by (P15 HIGH = 88i6745 107 HIGH), so ram test is done by default.


normal value for 0x1C00A84E = 0x00f0 = 0000000011110000

### 88i6745 to CON1 to 0x1C00A84E io port value to bitflip to high/low ###

| Test Wire |  CON1 pin | factory jumpbers | 0x1C00A84E value  | bit flipped      | status        | 88i6745 pin  | fw function
| --------- | --------- | ---------------- | ----------------- | ---------------- | ------------- | ------------ | ------------
| normal    | XX        |                  | 0x00f0            | 0000000011110000 | normal        | lots         | 
| TP E6     | ??        | ??               | 0x02f0            | 0000001000000000 | ?             | 109          | enable external flash?
| white     | 30        |                  | 0x00b0            | 0000000001000000 | normally HIGH | 42           |
| PUIS      | XX        | 3+4              | 0x0050            | 0000000010100000 | normally HIGH |              |
|           | XX        | 5+6              | 0x00a0            | 0000000001010000 | normally HIGH |              | 1.5G PHY
|           | XX        | 3+1              | 0x00e0            | 0000000000010000 | normally HIGH |              |
| ?         | ??        | ??               | 0x2000            | 0010000000000000 | ?             | ?            | immediate jump to serial console

### Factory Jumpers
| Jumper Pin | 6745 pin | CON1 pin |
| ---------- | -------- | -------- |
| 1          | 42       | 30       |
| 2          |          |          |  3.3v?
| 3          | 117      | XX - serial
| 4          | GND      | GND
| 5          | 118      | XX - serial
| 6          | GND      | GND
| 7          | 43       | 28 via resistor

### Normal values for IO ports read from

| Port       | Value | Bits             | Name        |
| ---------- | ----- | ---------------- | ----------- |
| 0x1C00A84E | 00f0  | 0000000011110000 | CONFIG_IO_A | 
| 0x1C00A846 | c802  | 1100100000000010 | CONFIG_IO_B |


### JTAG to mini console via OpenOCD

E.g., to make sure you've got 3.3v ttl serial connected up correctly.

Speed: 115200 N,8,1

reset halt
reg sp_usr 0x4005000
reg pc 0xffff01b4
resume


### Test Points that are GND
e22
e12
unlabeled TP reverse C shape at E37

### Test Points that are 3v3
one side of R3 on E5

### Test Points that are 1.34v
E97

### Normal values for IO ports written to
|            |       |                  |
| 0x1C002806 | 007f  | 0000000001111111 |
| 0x1C004AA0 | 0000  | 0000000000000000 |
| 0x1C00A20A | 0200  | 0000001000000000 |
| 0x1C00A20C | 0000  | 0000000000000000 |
| 0x1C00A800 | ffc4  | 1111111111000100 |
| 0x1C00A820 | 666e  | 0110011001101110 |
| 0x1C00AA00 | 0004  | 0000000000000100 |


```

Tricks:

0xFFFF0088 - short P14 to ground (normally high)

0xFFFF00xx, A0 A8, B0, B8 - top 3 bits of 0x1C00A846 are 100, 101, 011, or 111 - jump to console. Normally 110.
 - 111 = infinite loop?

Problems:

P13 to 3.3v - does something that makes openocd `reset halt` not halt immediately in ROM, no idea why.


### 6745 pins
| pin | note |
| --- | ---- |
| 01 | TP P3 to DNP resistor to ground - black |
| 02 | TP P4 to DNP resistor to ground - green |
| 03 | 3.3v net on pcb top |
| 04 | via to unmarked TP on bottom, jumper resistor to blind VIA - to cap buffered (C13) GND - suspicious |
| 05 | DNP cap to via to ground |
| 06 | TP P5 - violet |
| 07 | TP P6 - blue |
| 08 | GND |
| 09 | 3.3v net on pcb top |
| 10 | 3.3v net on pcb top |
| 11 | GND |
| 12 | pickup |
| 13 | pickup |
| 14 | GND |
| 15 | resistor to ground to unmarked TP on bottom - suspicious |
| 16 | via to GND |
| 17 | pickup |
| 18 | pickup |
| 19 | 0ohm resistor to 3.3v via to unmakred TP on bottom - suspicious |
| 20 | 0ohm resistor to 3.3v via to unmakred TP on bottom - suspicious |
| 21 | pickup |
| 22 | pickup |
| 23 | cap to GND |
| 24 | pickup |
| 25 | pickup |
| 26 | pickup |
| 27 | pickup |
| 28 | 3.3v net on pcb top |
| 29 | via to unmarked TP on bottom - suspicious |
| 30 | JTAG |
| 31 | SMOOTH motor |

| 42 | Factory Jumper 1 |
| 109 | Test Point E6 - normally low, set high causes JTAG problems |


32 - SMOOTH motor 
33 - SMOOTH motor ?
34 - SMOOTH motor ?
35 - via to unlabeled test point
36 - cap to ground + via to unlabeled test point
```

