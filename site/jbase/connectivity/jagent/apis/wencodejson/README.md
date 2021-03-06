# WENCODEJSON

<PageHeader />

The **WENCODEJSON** subroutine will encode a string to properly be in a JSON value.

## Command SYntax

```
CALL WENCODEJSON(OPTION,INSTR,OUTSTR)
```

### Syntax Elements

| Parameter | Description |
| --- | --- |
| OPTION | Leave blank. ¬†Placeholder for future features |
| INSTR | The string you wish to encode |
| OUTSTR | The encoded string. |

#### Example

```
CALL WENCODEJSON("",'"',OUTSTR)
* OUTSTR = \u0022   (Encoding for ")
```

#### Notes

>The WENCODEJSON function is primarily used internally by the other subroutines (such as WBUILDJSON and WOBJ), although it can be called independently if you are performing your own string building.

[Back to jAgent APIs](./../README.md)

  
<PageFooter />
