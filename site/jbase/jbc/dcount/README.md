# DCOUNT

<PageHeader />

## Description

This function counts the number of field elements in a string that are separated by a specified delimiter. It takes the general form:

```
DCOUNT(expression1, expression2)
```

Where:

- **expression1**¬†evaluates to a string in which fields are to be counted.
- **expression2**¬†evaluates to the delimiter string used to count the fields.

## Note

> - The delimiter string may consist of more than one character.
> - If **expression1** is a NULL string, the function returns a value of zero.
> - The delimiter string may consist of any character, including system delimiters such as field marks or value marks.

An example of use is as follows:

```
    alphaString = "A : B : C : D"
    CRT "The result of DCOUNT(alphaString, ':') is " : DCOUNT(alphaString, ':')
    CRT "The result of COUNT(alphaString, ':')  is " : COUNT(alphaString, ':')
```

The above code will result in the following output:

```
The result of DCOUNT(alphaString, ':') is 4
The result of COUNT(alphaString, ':')  is 3
```

> Note the difference in result returned by the COUNT function

See also: [COUNT](./../count).

Go back to [jBASE BASIC](./../README.md)

Go back to [Programmers' Reference Guide](./../../reference-guides/jbc/README.md)

<PageFooter />
