# DEFCE

<PageHeader />

**Tags:**
<badge text='callc' vertical='middle' />

## Description

The **DEFCE** statement should be used, rather than the [DEFC](./../defc) statement, for calling External C programs, which are pure āCā code and do not use the jBASE library macros and functions.

For C functions that do not require jBASE functions, use the **DEFCE** statement, however the passing arguments can only be of type INT, FLOAT and STRING. An example of this can be as:

```
DEFCE INT CFUNC(INT, FLOAT, VAR)
Var1 = CFUNC(A, 45, B)
```

It is also possible to call standard UNIX functions directly by declaring them with the [DEFC](./../defc) statement according to their parameter requirements. They can be called directly provided they return type INT or FLOAT/DOUBLE, or that the return type may be ignored. An example is as:

```
DEFCE INT getpid()
CRT "Process id = " : getpid()
```

Go back to [jBASE BASIC](./../README.md)

Go back to [Programmers' Reference Guide](./../../reference-guides/jbc/README.md)

<PageFooter />
