# .cb file
If you're used to build systems like Make you've already figured out that the .cb file is the cbuild equivalent of a Makefile. That is, the .cb file is the input file that cbuild reads to control the build.

<pre>
<a href="TARGETNAME.md">TARGETNAME</a>=MessageBox
<a href="TARGETTYPE.md">TARGETTYPE</a>=EXE
<a href="RUNTIMELIB.md">RUNTIMELIB</a>=LIBCMT  # {LIBCMT|MSVCRTXX|LIBC|MFCSTATIC|MFCDLL|NONE}, Default: LIBCMT
<a href="USE_UNICODE.md">USE_UNICODE</a>=1     # {MBCS|UNICODE}, Default: MBCS
<a href="PCH.md">PCH</a>=precomp.h

<a href="INCLUDES.md">INCLUDES</a>=.;..;include
<a href="MACROS.md">MACROS</a>=STATIC_LINK
<a href="LIBS.md">LIBS</a>=comctl32.lib;ws2_32.lib
<a href="LIBPATHS.md">LIBPATHS</a>=..\lib
<a href="CFLAGS.md">CFLAGS</a>=
<a href="LFLAGS.md">LFLAGS</a>=
<a href="RFLAGS.md">RFLAGS</a>=
<a href="AFLAGS.md">AFLAGS</a>=
<a href="AS.md">AS</a>=

# C/C++ source file
<a href="NAMEMANAGLING.md">NAMEMANAGLING</a>=1      #{0|1}, Default: 0
<a href="SOURCES.md">SOURCES</a>=\
    messagebox.c \
    main.c
    
# cbuild will recursive build subdirectory project
<a href="DIRS.md">DIRS</a>=\
    dir1 \
    dir2

<a href="PREBUILD.md">PREBUILD</a>:
    @echo after build action
    
<a href="POSTBUILD.md">POSTBUILD</a>:
    @echo before build action
</pre>

## Example
``` Makefile
# [SampleDir]\demo_console\makefile.cb
TARGETNAME=HelloWorld
TARGETTYPE=EXE
SOURCES=HelloWorld.c
```

``` Makefile
# x624 cbuild file
TARGETNAME=x264.exe
TARGETTYPE=x264.exe
RUNTIMELIB=LIBCMT
USE_UNICODE=1

INCLUDES=.;extras
LIBS=
MACROS=HAVE_STRING_H
CFLAGS=/sdl- /wd4996
LFLAGS=-map:map.txt
AFLAGS=-O2 -Worphan-labels -DSTACK_ALIGNMENT=32 -DHIGH_BIT_DEPTH=0 -DBIT_DEPTH=8
AS=YASM
NAMEMANGLING=1

SOURCES=\
    common/mc.c common/predict.c common/pixel.c common/macroblock.c \
    common/frame.c common/dct.c common/cpu.c common/cabac.c \
    common/common.c common/osdep.c common/rectangle.c \
    common/set.c common/quant.c common/deblock.c common/vlc.c \
    common/mvpred.c common/bitstream.c \
    encoder/analyse.c encoder/me.c encoder/ratecontrol.c \
    encoder/set.c encoder/macroblock.c encoder/cabac.c \
    encoder/cavlc.c encoder/encoder.c encoder/lookahead.c \
    x264.c input/input.c input/timecode.c input/raw.c input/y4m.c \
    output/raw.c output/matroska.c output/matroska_ebml.c \
    output/flv.c output/flv_bytestream.c filters/filters.c \
    filters/video/video.c filters/video/source.c filters/video/internal.c \
    filters/video/resize.c filters/video/cache.c filters/video/fix_vfr_pts.c \
    filters/video/select_every.c filters/video/crop.c filters/video/depth.c \
    input/avs.c \
    input/thread.c \
    common/threadpool.c \
    common/win32thread.c \
    common/opencl.c \
    encoder/slicetype-cl.c \
    extras/getopt.c \
    common/x86/mc-c.c \
    common/x86/predict-c.c \
    common/x86/const-a.asm \
    common/x86/cabac-a.asm \
    common/x86/dct-a.asm \
    common/x86/deblock-a.asm \
    common/x86/mc-a.asm \
    common/x86/mc-a2.asm \
    common/x86/pixel-a.asm \
    common/x86/predict-a.asm \
    common/x86/quant-a.asm \
    common/x86/cpu-a.asm \
    common/x86/bitstream-a.asm \
    common/x86/sad-a.asm

!ifdef _WIN64
MACROS+=;ARCH_X86_64=1
AFLAGS+=-DARCH_X86_64=1
SOURCES+=\
    common/x86/dct-64.asm \
    common/x86/trellis-64.asm
!else
MACROS+=;ARCH_X86=1
AFLAGS+=-DARCH_X86_64=0 -DPREFIX 
SOURCES+=\
    common/x86/dct-32.asm \
    common/x86/pixel-32.asm
!endif
```
