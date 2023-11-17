# PREBUILD
Specifies a list of commands to be executed for the pre-build.

```
PREBUILD:
    [command 1]
    [command 2]
    ...
    [command n]
```

## Command Modifiers
<table>
<tr><th>Modifier</th><th>Purpose</th></tr>
<tr><td>@command</td><td>Prevents display of the command. Display by commands is not suppressed. By default, cbuild echoes all executed commands.</td></tr>
<tr><td>¨Ccommand</td><td>Turns off error checking for command. By default, cbuild halts when a command returns a nonzero exit code. If ¨Cnumber is used, cbuild ignores the exit code.</td></tr>
</table>

## Example:
``` Makefile
# copy header file to public header folder
PREBUILD:
    @-mkdir $(INCDIR)\portable
    @copy /Y os.h $(INCDIR)\portable
    @copy /Y common.h $(INCDIR)\portable
    @copy /Y bufferpool.h $(INCDIR)\portable
```