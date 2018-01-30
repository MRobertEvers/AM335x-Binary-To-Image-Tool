# AM335x-Binary-To-Image-Tool
Takes a binary compiled for ARM processors and adds the necessary overhead to boot into it. Adds the 'Magic' TOC and GP Header to the start of the binary. (See AM335x Technical Reference Manual)

Usage: `btoi.exe <input_file> <output_file>'

Output: Outputs a binary file that is a combinations of the 'Magic' TOC ([See AM335x Technical Reference Manual Section 26.1.10](http://www.ti.com/lit/ug/spruh73p/spruh73p.pdf)), an appropriate GP Header, and the input binary file. The output binary is ready for "RAW Mode" boot from an SD Card on an AM335x Processor.

I.e.
1. Places TOC in addresses 0x0-0x1FF
2. Places GP Header in addresses 0x200-0x207. Calculates the size of the input binary, stores that value (little endian) at address 0x200-0x203; and stores the RAM Start location (little endian) at 0x204-0x207.
3. Places Input binary resides in addresses 0x208-
