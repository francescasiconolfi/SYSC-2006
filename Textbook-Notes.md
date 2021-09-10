# The C Programming Language Textbook Notes

## Table of Contents
[Chapter 1: Introduction](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#chapter-1-introduction)\
[Section 1.1: Getting Started](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#section-11-getting-started)\
[Section 1.2:]()\


## Chapter 1: Introduction

### Section 1.1: Getting Started
First line of the program, `#include <stdio.h>` tells the compiler to include information about the stdin/stdout (standard input/standard output) library.

The second line of the program should define "main", which is a function vital to every program: `main()`.\
No arguments should be between its brackets.

In order to enclose statements in the function "main", *curly braces* ( {} ) are required following "main".

Finally, each line should end with a *semicolon* ( ; ).

Basic format of any C program:

``` C

#include <stdio.h>

main()
{

// statements;

}

```

where "// statements;" represents where the function's statements are supposed to be written

#### The printf Function
The `printf()` function is a library function that prints output.

All string literals should be the first argument between the brackets, while other values should follow, seperated by commas: `printf("str", variable1, value1, variable2)`.

Do not forget to include a newline each time it is used, to ensure there is a line advance after its output, using the following *escape sequence*: `\n`




