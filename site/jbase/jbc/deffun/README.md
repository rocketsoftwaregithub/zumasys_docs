# DEFFUN

<PageHeader />

## Description

This statement is used to declare an external function to the jBASE BASIC compiler and optionally define its arguments. The statement is used in the program that calls the function. It takes the general form:

```
DEFFUN FuncName({ {MAT} Argument1, {MAT} Argument2...})
```

Where

- **FuncName** is the name used to define the function. It must be the same as the source file name.
- **Argument** specifies a value passed to the function by the calling program. To pass an array, you must use the MAT before the argument name. These parameters are optional (as indicated in the Command Syntax) but can be specified for clarity. Note that if the arguments are not initialized somewhere in the program you will receive a compiler warning.

## Note

> The **DEFFUN** statement identifies a user-written function to the jBASE BASIC compiler, which must be present in each program that calls the function, before the function is called. A hidden argument is passed to the function so that a value can be returned to the calling program. The return value is set in the function using the RETURN (value) statement. If the [RETURN](./../return) statement specifies no value then the function returns an empty string.

An example of use is as follows:

- Main program:

```
DEFFUN Add()

arg1 = 10
arg2 = 20

sum = Add(arg1, arg2)

CRT sum

arg3 = RND(42)
arg4 = RND(24)

CRT Add(arg3, arg4)
```

- Function:

```
FUNCTION Add(operand1, operand2)
    result = operand1 + operand2
RETURN(result)
```

Go back to [jBASE BASIC](./../README.md)

Go back to [Programmers' Reference Guide](./../../reference-guides/jbc/README.md)

<PageFooter />
