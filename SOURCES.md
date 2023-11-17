# SOURCES
The SOURCES macro specifies the files to be compiled. The SOURCES macro is required by the cbuild.

cbuild examines these files and checks the file age. If any of those file change, cbuild rebuilds this source file.

Use this macro to list your source file names. Include the file name extension, and separate the entries in this list by using spaces or tabs


## Example:
``` Makefile
SOURCES=\
    common/mc.c common/predict.c common/pixel.c common/macroblock.c \
    common/frame.c common/dct.c common/cpu.c common/cabac.c \
    input/avs.c \
    input/thread.c \
    common/threadpool.c \
    common/win32thread.c \
    common/opencl.c \
    encoder/slicetype-cl.c \
    extras/getopt.c \
    common/x86/mc-c.c \

!ifdef _WIN64
    SOURCES+=common/x86/dct-64.asm common/x86/trellis-64.asm
!else
    SOURCES+=common/x86/dct-32.asm common/x86/pixel-32.asm
!endif
```