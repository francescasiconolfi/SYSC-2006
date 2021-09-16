# The C Programming Language Textbook Notes

## Table of Contents

<details>

<summary>Chapter 1: Introduction</summary>

[Section 1.1: Getting Started](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#section-11-getting-started)\
[Section 1.2: Variables and Artihmetic Expressions](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#section-12-variables-and-arithmetic-expressions)\
[Section 1.3: The For Statement](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#section-13-the-for-statement)\
[Section 1.4: Symbolic Constants](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#section-14-symbolic-constants)

</details>

<details>
    
<summary> Chapter 2: Types, Operators, and Expressions </summary>
    
[Section 2.1: Variable Names]()\
[Section 2.2]()\
[Section 2.3]()
    
</details>

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

#### Escape Sequences
The following is a list of escape sequences, which each consist of a blackslash and a single character, in order to represent particular actions within the program:

- `\n` represents a newline
- `\t` represents a tab
- `\b` represents a backspace
- `\"` represents a double quotation
- `\\` represents a backslash

#### Variable Declarations

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

##### Other Character Specifications:
The following is a list of character specifications recognized and read by printf(), as well as other applicable functions:

- `%d` represents a decimal value
- `%f` represents a float value
- `%o` represents an octal value
- `%x` represents a hexadecimal value
- `%c` represents a character value
- `%s` represents a string value
- `%%` represents the character '%'
- `%e` represents values in scientific notation

These character combinations also allows specification of character width, as well as decimal precision in the following format: `%#.#c`

where the first number (before the decimal) represents the width, and the number after the decimal represents the precision

To just specify one, omit the other.

Example:

`printf("I spent %.3f dollars today.\n", spent);` will result in the value assigned to variable 'spent' having 3 decimal places.

#### Making Comments
To make a single-line comment, use double slashes: `//`

To make a multiple-line comment, enclose text between `/*` (opening comment symbol) and `*/` (closing comment symbol).

#### While Loops
While loops repeatedly execute the body of the while loop, granted the condition results in True. Once the condition is evaluated to be False, the loop ends, and execution continues at the following statement.

While Loop Format:

For a single-statement while loop, braces are unnecessary:

``` C
main ()
{

    while (condition)
        body;

}
```

For a multiple-line while loop, use braces:

``` C
main()
{

    while (condition)
        {
        line 1;
        line 2;
        }

}
```
Notice: All statments controlled by the while loop are always indented once.

#### Arithmetic Notes

Integer division causes truncation, so any fraction < 1 will be read as 0.\
To avoid this, seperately multiply by the numerator, and divide by the denominator.\
Another option is to multiply by a fraction consisting of floating point numbers, since float division is not truncated.

If both operands in an operation are integers, integer operation is performed.
Operations with a floating point operand will cause the other operand to be converted to a float as well, given it was an int before.

### Section 1.3: The For Statement
For loops consist of three parts, seperated by semicolons, within parentheses, and act like that of the while loop.\
The first part within the parentheses is the initialization; the second part is the condition that controls the loop; the third is the increment step, which causese the body to be reevaluated.

Again, for a single-line body of the loop, braces are unnecessary:

``` C
main()
{

    for (initialization; condition; incremental step)
        body;
        
}
```

For a multiple-line for loop, use braces:
    
``` C
main()
{

    for (initialization; condition; incremental step)
        {
        line 1;
        line 2;
        }
        
}
```

Note: For loops are usually used when the initialization and increment statements are logically related and single statements.

Example:

``` C

# include <stdio.h>

main()
{
    int dog_age;
    
    for (dog_age = 0; dog_age <= 105; dog_age = dog_age + 7)
        printf("One year has passed, so my dog is now %d in human years.\n", dog_age);

}
```

Appearance:

> One year has passed, so my dog is now 0 in human years.\
> One year has passed, so my dog is now 7 in human years.\
> One year has passed, so my dog is now 14 in human years.\
> ...

### Section 1.4: Symbolic Constants
Constants are conventially replaced with symbolic names in order to allow better readability.

A #define line defines the symbolic name/constant like so: `#define name replacement text`

where any occurence of *name* will be replaced by *replacement text*; *name* is a sequence of letters + digits that begins w/ a letter (not within quotations); *replacement text* is any sequence of characters

Notes: (1) Symbolic constants are conventionally written in uppercase to be ditinguished from variables, (2) There is no semicolon at the end of #define line, (3) They are defined before any function is written.

Example:

``` C

# include <stdio.h>

#define BORN 0
#define DEAD 105
#define DIFF 7

main()
{
    int dog_age
    
    for (dog_age = BORN; dog_age <= DEAD; dog_age = dog_age + DIFF)
        printf("One year has passed, so my dog is now %d in human years.\n", dog_age);

}
```

## Chapter 2: Types, Operators, and Expressions

### Section 2.1: Variable Names
Convention and rules regarding variable names:
- The first character must be a letter
- The underscore counts as a letter (but do not start the name with one)
- Upper and lowercase are distinct; lowercase is convention for variables, while upper case is convention for symbolic constants

