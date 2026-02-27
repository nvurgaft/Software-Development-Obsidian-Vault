
When an Interrupt is invoked

1. the processor is interrupted
2. Old state saved on the stack
3. Interrupt executed

The Interrupt Vector Table (IVT) describes 256 Interrupt handles

Every Interrupt is mapped by 2 Offset bytes and Segment bytes

| Offset  | Segment | Offset  | Segment | Offset  | Segment | Offset  | Segment |     |
| ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | --- |
| 0x00    | 0x7c0   | 0x8d00  | 0x00    | 0x00    | 0x8d0   | 0x7c00  | 0x587   |     |
| 2 bytes | 2 bytes | 2 bytes | 2 bytes | 2 bytes | 2 bytes | 2 bytes | 2 bytes |     |

Interrupts 0 = address 0x00
Interrupts 1 = address 0x04
Interrupts 2 = address 0x08