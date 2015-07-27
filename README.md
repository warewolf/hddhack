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


88i6745 to CON1 to 0x1C00A846 io port value to bitflip to high/low

normal = c802 = 1100100000000010

| Test Wire | CON1 pin | 0x1C00A846 value | bit              | status        | 88i6745 pin 
| --------- | -------- | ---------------- | ---------------- | ------------- | --------
| white     | 30       | ????		  | 0000000001000000 | normally ???  | 6745 pin 42 (io port 0x1C00A84E, not 0x1C00A846)
| yellow    | 28       | 0xc800		  | 0000000000000010 | normally HIGH | 6745 pin 43
| green     | 26       | 0xc806		  | 0000000000000100 | normally low  | 6745 pin 44
| blue      | 24       | 0xc80a		  | 0000000000001000 | normally low  | 6745 pin 46
| violet    | 22       | 0xc812		  | 0000000000010000 | normally low  | 6745 pin 48
| black     | 20       | 0xc822		  | 0000000000100000 | normally low  | 6745 pin 49
| brown	    | 18       | 0xc842		  | 0000000001000000 | normally low  | 6745 pin 50
| red	    | 16       | 0xc882		  | 0000000010000000 | normally low  | 6745 pin 51
| yellow    | 06       | 0xc902		  | 0000000100000000 | normally low  | 6745 pin 52
| orange    | 32       | 0xca02		  | 0000001000000000 | normally low  | 6745 pin 41
| black	    | 38       | 0xcc02		  | 0000010000000000 | normally low  | 6745 pin 37
| brown	    | 36       | 0xc002		  | 0000100000000000 | normally HIGH | 6745 pin 38
| red	    | 34       | 0xd802		  | 0001000000000000 | normally low  | 6745 pin 40 - to 3.3v
| n/a	    | n/a      | 0xe802		  | 0010000000000000 | normally low -| 6745 pin 104 - P13 to 3.3v
| n/a	    | n/a      | 0x8802		  | 0100000000000000 | normally HIGH | 6745 pin 106 - P14 to ground
| n/a	    | n/a      | 0x4802		  | 1000000000000000 | normally HIGH | 6745 pin 107 - P15 to ground  


```
6745 pins
01 - TP P3 to DNP resistor to ground - black
02 - TP P4 to DNP resistor to ground - green
03 - 3.3v net on pcb top
04 - via to unmarked TP on bottom, jumper resistor to blind VIA - to cap buffered ground
05 - DNP cap to via to ground
06 - TP P5 - violet
07 - TP P6 - blue
08 ?
09 - 3.3v net on pcb top
10 - 3.3v net on pcb top
15 - resistor to ground to unmarked TP on bottom
20 - 3.3v net on pcb top
28 - 3.3v net on pcb top
33 - SMOOTH motor ?
34 - SMOOTH motor ?
35 - via to unlabeled test point
36 - cap to ground + via to unlabeled test point
```
