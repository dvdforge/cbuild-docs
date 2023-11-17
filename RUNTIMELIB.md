# RUNTIMELIB
Specify runtime libarary for linking.

## Valid Values
<div id=p>LIBCMT, MSVCRTXX, MFCSTATIC, MFCDLL, NONE</div>
<table>
<tr><th>Value</th><th>Meaning</th></tr>
<tr><td>LIBCMT</td><td>Link with LIBCMT.LIB</td></tr>
<tr><td>MSVCRTXX</td><td>Link with MSVCRTXX.LIB</td></tr>
<tr><td>MFCSTATIC</td><td>Use MFC in a Static Library</td></tr>
<tr><td>MFCDLL</td><td>Use MFC in a Shared DLL</td></tr>
<tr><td>NONE</td><td>Doesn't use runtime library, when build device driver</td></tr>
</table>

## Default Value
LIBCMT

## Example:
``` Makefile
# Static link c runtime library
TARGET_RUNTIME=LIBCMT
```