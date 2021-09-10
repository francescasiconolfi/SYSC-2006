# The C Programming Language Textbook Notes

## Table of Contents
[Chapter 1: Introduction](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#chapter-1-introduction)\
[Section 1.1: Getting Started](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#section-11-getting-started)\
[Section 1.2: Variables and Artihmetic Expressions](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#section-12-variables-and-arithmetic-expressions)\


## Chapter 1: Introduction

### Section 1.1: Getting Started
First line of the program, `#include <stdio.h>` tells the compiler to include information about the stdin/stdout (standard input/standard output) library.

The second line of the program should define "main", which is a function vital to every program: `main()`.\
No arguments should be between its brackets.

In order to enclose statements in the function "main", *curly braces* ( {} ) are required following "main".

Finally, each line terminates with a *semicolon* ( ; ).

Basic format of any C program:

``` C

#include <stdio.h>

main()
{

// statements;

}

```

where "// statements;" represents where the function's statements are supposed to be written

### Section 1.2: Variables and Arithmetic Expressions

### Escape Sequences
The following is a list of escape sequences, which each consist of a blackslash and a single character, in order to represent particular actions within the program:

- `\n` represents a newline
- `\t` represents a tab
- `\b` represents a backspace
- `\"` represents a double quotation
- `\\` represents a backslash

### Variable Declarations

All created variables must be declared before they are used; that is, their type and name must be declared before use in the following order: `type name`

The following is a list of types that can be used to create different types of variables:

- `int` creates an integer variable
- `float` creates a float variable
- `double` creates a double-precision floating point variable
- `char` creates a string (actually a character array) variable
- `short` creates an integer variable (ranging from −32,767 to 32,767)
- `long` creates an integer variable (ranging from −2,147,483,647 to 2,147,483,647)

To assign values to these variables, use an *assignment statement*: `variable = value`

Example: 

``` C

#include <stdio.h>

main()
{

int age

age = 3

}

```

where *age* is a variable, type int, assigned to the value 3

#### The printf Function
The `printf()` function is a library function that prints output.

All string literals should be the first argument between the brackets, while other values should follow, seperated by commas: `printf("str", variable1, value1, variable2)`.

Each variable/value corresponds to a '%c' within the string argument, with the first value substituting the first occurence of '%c', the second value substituting the second occurence of '%c', and so on.

Do not forget to include a newline each time it is used, to ensure there is a line advance after its output, using the following *escape sequence* within quotations: `\n`

Example:

``` C

#include <stdio.h>

main()
{

int income
int expenses

income = 50000
expenses = 60000

printf("If your income is $%d, and your expenses are $%d, you are probably in debt.\n", income, expenses);

}

```

Appearance:

> If your income is $50000, and your expenses are $60000, you are probably in debt.
>

#### Other Character Specifications:
The following is a list of character specifications recognized and read by printf(), as well as other applicable functions:

- `%d` represents a decimal value
- `%f` represents a float value
- `%o` represents an octal value
- `%x` represents a hexadecimal value
- `%c` represents a character value
- `%s` represents a string value
- `%%` represents the character '%'

#### Making Comments
To make a single-line comment, use double slashes: `//`

To make a multiple-line comment, enclose text between `/*` (opening comment symbol) and `*/` (closing comment symbol).

#### While Loops






