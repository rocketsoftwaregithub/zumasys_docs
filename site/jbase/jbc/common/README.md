# COMMON

<PageHeader />

## Description

The **COMMON** statement declares a list of variables and matrices that can be shared among various programs. There can be many common areas including a default, unnamed common area. The statement takes the general form:

```
COMMON {/CommonName/} variable{, variable ... }
```

Where:

The list of variables should not have been declared or referenced previously in the program file. The compiler will detect any bad declarations and display suitable warning or error messages. If the common area declared with the statement is to be named then the first entry in the list should be a string, delimited by the / character.

## Note

> The compiler will, by default, not check that variables declared in **COMMON** statements are initialized before they have been used as this may be beyond the scope of this single source code check.
>
> The "–Jci" option, when specified to the jBASE BASIC compiler, will force this check to be applied to common variables as well. The initialization of named common is controlled via options in the Config\_EMULATE file.
>
> Variables declared without naming the common area may only be shared between the program and its subroutines (unless [CHAIN](./../chain) is used). Variables declared in a named common area may be shared across program boundaries. When any common area is shared, all programs using it should have declared the same number of variables within it.
>
> [Dim](./../dimension-dim)ensioned arrays are declared and dimensioned within the **COMMON** statement.

An example of use is as:

```
COMMON var1, array1(2, 6, 10), var2
COMMON /Common1/ var1, var3, array2(10, 10)
```

Go back to [jBASE BASIC](./../README.md)

Go back to [Programmers' Reference Guide](./../../reference-guides/jbc/README.md)

<PageFooter />
