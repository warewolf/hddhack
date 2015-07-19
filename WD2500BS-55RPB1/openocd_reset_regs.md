### openocd
####  reset halt
```
JTAG tap: feroceon.cpu0 tap/device found: 0x259663d3 (mfg: 0x1e9, part: 0x5966, ver: 0x2)
unexpected Feroceon EICE version signature
unexpected Feroceon EICE version signature
target state: halted
target halted in ARM state due to debug-request, current mode: Supervisor
cpsr: 0x000000d3 pc: 0xffff0000
MMU: disabled, D-Cache: disabled, I-Cache: disabled
```

#### > reg
```
===== ARM registers
(0) r0 (/32): 0x00000013 (dirty)
(1) r1 (/32): 0x000000D3
(2) r2 (/32): 0x0400095C
(3) r3 (/32): 0x04000164
(4) r4 (/32): 0x00000013
(5) r5 (/32): 0x04000958
(6) r6 (/32): 0x11111111
(7) r7 (/32): 0x11111111
(8) r8 (/32): 0x11111111
(9) r9 (/32): 0x11111111
(10) r10 (/32): 0x11111111
(11) r11 (/32): 0x11111111
(12) r12 (/32): 0x00000013
(13) sp_usr (/32)
(14) lr_usr (/32)
(15) pc (/32): 0xFFFF0000 (dirty)
(16) r8_fiq (/32)
(17) r9_fiq (/32)
(18) r10_fiq (/32)
(19) r11_fiq (/32)
(20) r12_fiq (/32)
(21) sp_fiq (/32)
(22) lr_fiq (/32)
(23) sp_irq (/32)
(24) lr_irq (/32)
(25) sp_svc (/32): 0x04004B6C
(26) lr_svc (/32): 0x00001865
(27) sp_abt (/32)
(28) lr_abt (/32)
(29) sp_und (/32)
(30) lr_und (/32)
(31) cpsr (/32): 0x000000D3
(32) spsr_fiq (/32)
(33) spsr_irq (/32)
(34) spsr_svc (/32): 0x00000010
(35) spsr_abt (/32)
(36) spsr_und (/32)
===== EmbeddedICE registers
(37) debug_ctrl (/6): 0x05
(38) debug_status (/5)
(39) comms_ctrl (/6)
(40) comms_data (/32)
(41) watch_0_addr_value (/32)
(42) watch_0_addr_mask (/32)
(43) watch_0_data_value (/32)
(44) watch_0_data_mask (/32)
(45) watch_0_control_value (/9)
(46) watch_0_control_mask (/8)
(47) watch_1_addr_value (/32)
(48) watch_1_addr_mask (/32)
(49) watch_1_data_value (/32)
(50) watch_1_data_mask (/32)
(51) watch_1_control_value (/9)
(52) watch_1_control_mask (/8)
(53) vector_catch (/8): 0x00
```
