The BIOS is executed directly from ROM

The CPU executed instructions directly from the BIOS

The BIOS loads itself into the RAM and continues executing from the RAM.

The BIOS initializes essential hardware.

The BIOS looks for a bootloaders boot by searching all storage mediums for the boot signature 0x55AA

The BIOS loads the bootloader into RAM at absolute address 0x7c00.

The BIOS instructs the process to perform a jump to absolute address 0x7c00 and begin executing the operating system bootloader.

The BIOS is a 16 bit code which means only 16 bit code can execute it properly (REAL mode).

The BIOS routines are generic and standard.