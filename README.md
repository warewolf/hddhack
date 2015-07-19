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
```

bit                   1111111000000000
bit                   6543210987654321

      normal = c802 = 1100100000000010
black   = 38 = cc02 = 0000010000000000 normally low  - 6745 pin 37
brown   = 36 = c002 = 0000100000000000 normally HIGH - 6745 pin 38
                   cap to ground, via tied to pin 47 - 6745 pin 39
red     = 34 = d802 = 0001000000000000 normally low  - 6745 pin 40
orange  = 32 = ca02 = 0000001000000000 normally low  - 6745 pin 41
white   = 30 = ???? = 0000000001000000 normally ???  - 6745 pin 42 (io port 0x1C00A84E, not 0x1C00A846)
yellow  = 28 = c800 = 0000000000000010 normally HIGH - 6745 pin 43
green   = 26 = c806 = 0000000000000100 normally low  - 6745 pin 44
         cap to ground + via to unlabeled test point - 6745 pin 45
blue    = 24 = c80a = 0000000000001000 normally low  - 6745 pin 46
                   cap to ground, via tied to pin 39 - 6745 pin 47

violet  = 22 = c812 = 0000000000010000 normally low  - 6745 pin 48
black   = 20 = c822 = 0000000000100000 normally low  - 6745 pin 49
brown   = 18 = c842 = 0000000001000000 normally low  - 6745 pin 50
red     = 16 = c882 = 0000000010000000 normally low  - 6745 pin 51
yellow  = 06 = c902 = 0000000100000000 normally low
<<>>    = 14 = 3.3v = 3.3v normally high
<<>>    = 12 = 3.3v = 3.3v normally high
orange  = 10 = nothing, floating pin w/ optional resistor to ground
<<>>    = 08 = NC
```

```
6745 pins
01 - TP P3 to DNP resistor to ground
02 - TP P4 to DNP resistor to ground
03 - 3.3v net on pcb top
04 - via to unmarked TP on bottom, jumper resistor to blind VIA - to cap buffered ground
05 - DNP cap to via to ground
06 - TP P5
07 - TP P6
08 ?
09 - 3.3v net on pcb top
10 - 3.3v net on pcb top
20 - 3.3v net on pcb top
28 - 3.3v net on pcb top
33 - SMOOTH motor ?
34 - SMOOTH motor ?
35 - via to unlabeled test point
36 - cap to ground + via to unlabeled test point
```
