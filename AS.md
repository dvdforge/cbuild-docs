# AS
Specify the assembler to build .asm file.

## Valid Values:
MASM, YASM, NASM

<table>
<tr><th>Value</th><th>Meaning</th></tr>
<tr><td>MASM</td><td>Microsoft MASM</td></tr>
<tr><td>YASM</td><td>Use <a href="http://yasm.tortall.net" target="_blank">YASM</a> (Yasm Modular Assembler)</td></tr>
<tr><td>NASM</td><td>Use <a href="http://sourceforge.net/projects/nasm" target="_blank">NASM</a> (Netwide Assembler)</td></tr>
</table>

## Example:
``` Makefile
# Use YASM to build .asm file
AS=YASM
```