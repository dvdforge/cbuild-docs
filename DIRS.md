# DIRS
The DIRS macro is used to specify a list of subdirectories or .cb files that the cbuild will build every time that it runs.

If DIRS specifies a directory, then it will ues the default build.cb.

## Example:
The following example instructs the cbuild to build the subdirectories in the order in the order in which they are specified by the DIRS macro.

``` Makefile
# => cbuild will build the following file one by one:
# demo_console\build.cb
# demo_exe\build.cb
# demo_mfc\tst.cb
# demo_lib\build.cb
# demo_dll\build.cb

DIRS=\
    demo_console \
    demo_exe \
    demo_mfc\tst.cb \
    demo_lib \
    demo_dll
```