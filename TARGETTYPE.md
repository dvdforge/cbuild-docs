# TARGETTYPE
Use the TargetType macro to specify the type of product being built.

TargetType gives the cbuild utility clues about some of the input files that it should expect.

## Valid Values
EXE, DLL, LIB, DRV
<table>
<tr><th>Value</th><th>Meaning</th></tr>
<tr><td>EXE</td><td>Build .exe program</td></tr>
<tr><td>DLL</td><td>Build .dll library</td></tr>
<tr><td>LIB</td><td>Build .lib static link library</td></tr>
<tr><td>DRV</td><td>Build .sys system device driver</td></tr>
</table>

## Example:
``` Makefile
# to build an application
TargetType=EXE

# to build a dynamic link library
TargetType=DLL

# to build a static link library
TargetType=LIB

# to build a device driver
TargetType=DRV
```