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
    
<summary>Chapter 2: Types, Operators, and Expressions </summary>
    
[Section 2.1: Variable Names](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#section-21-variable-names)\
[Section 2.2: Data Types and Sizes](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#section-22-data-types-and-sizes)\
[Section 2.3: Constants](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#23-constants)\
[Section 2.4: Declarations](https://github.com/francescasiconolfi/SYSC-2006/blob/main/Textbook-Notes.md#section-24-declarations)\
[Section 2.5: Arithmetic Operators]()
[Section 2.6: Relational and Logical Operators]()
[Section 2.7: Type Conversions]()
    
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
- `%u` represents an unsigned int

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

### Section 2.2: Data Types and Sizes
Recall:
- char (a single byte; one character)
- int (an integer)
- float (single-precision floating point)
- double (double-precision floating point)

which can all be modified by qualifiers, including but not limited to:
- short (applies to integers)
- long (applies to integers)
- long long (applies to integers)
- const (can be used instead of #define to declare a symbolic constant)
- signed (applies to char or any int)
- unsigned (declares numbers to be >= 0)

### 2.3: Constants
The value of an int can be specified to be in octal or hexidecimal with the following specifications:
- A leading **0** on an int constant puts it in *octal*
- A leading **0x** or **0X** on an int constant puts it in *hexidecimal*
- Octal/hexidecimal constants can be followed directly by L to declare them long and/or U to declare them unsigned

Examples:

1. (25)<sub>10</sub> is simply `25` in C, while (31)<sub>8</sub> would be `031`
2. (31)<sub>8</sub> is equivalent to 19<sub>16</sub>, which is represented as `0X19` in C
3. `0X1BUL` means the number is an unsigned long hexadecimal 1B, or (27)<sub>10</sub>

#### Character Constants
A character constant is an integer written as a single character within **single quotations**. Its actual value is the numeric value of the written character in the machine's character set (i.e. 'A' has the ASCII value 065, and would be interpreted as such due to the **single quotations**).

Note: String literals are surrounded by double quotes, and are not equivalent to character constants. They are actually arrays of characters with an internal representation of a null character at each of their ends, so physical storage is always one more than the number of characters in the string.

**REMEMBER**: 'x' != "x"

#### A Complete List of Escape Sequences
The following is a list of escape sequences:
- `\a` (alert/bell)
- `\b` (backspace)
- `\f` (formfeed)
- `\n` (newline)
- `\r` (carriage return)
- `\t` (horizontal tab)
- `\v` (vertical tab)
- `\\` (backslash)
- `\?` (question mark)
- `\'` (single quote)
- `\"` (double quote)
- `\ooo` (octal number)
- `\xhh` (hexadecimal number, where x is actually written)

Note: The character constant '/0' represents the character with value zero - *the null character*. The numeric value is actually 0.

#### The Function strlen()
`strlen(char)` returns the length of its character str argument, *char*, excluding the null character '\0'.

#### The Enumeration Constant
An enumeration is a list of constant integer values, where the first name in an enum has value 0, the second has value 1, the third has value 2... and so on. This is true unless the values are specified. If not all are specified, the unspecified values will continue progression from last value (i.e. if first value is 1, second is 2, and so on).

General format:

``` C

main()
{

    enum name { variable1 = int1, variable2 = int2, variable3 = int3 };
    
}
```

### Section 2.4: Declarations
All variables must be declared before use.

General formatting:\
Of a single declaration: `type variable;`
Of a multi-declaration: `type variable1, variable2;`
Of a single initialization: `type variable = value;`

Example:
`char cheese[4] = "good";`

The qualifier *const* can be applied to the declaration of any variable to specify its value will not be changed.\
In an array, the *const* qualifier says the elements will not be altered; it can also be used with array arguments.

### Section 2.5: Arithmetic Operators
The following is a list of binary arithmetic operators:
- + (addition)
- - (subtraction)
- * (multiplication)
- / (integer division)
- % (modulus)

Notes: (1) The modulus operator cannot be applied to floats/doubles, (2) If one operand is a float/double when dividing, the other becomes automatically converted to a float/double, and division is performed with decimals.

Precedence:
**\*, /, %** > **+, -**

### Section 2.6: Relational and Logical Operators
The following is a list of relational operators:
- > (greater than)
- < (less than)
- >= (greater than or equal to)
- <= (less than or equal to)
- == (equal)
- != (not equal)

Precedence:
**>, <, >=, <=** > **==, !=**

The following is a list of logical operators:
- && (AND)
- || (OR)

Precedence:
Relational and equality operators > **&&** > **||**

Notes: (1) Expressions with relational operators are evaluated left to right, and evaluation stops as soon as the truth or falsehood is known, (2) Assignment has lower precedence than all operators except ',' which simply enforces sequential evaluation, (3) The numeric value of a relational/logical expression is 1 if True and 0 if False, (4) The unary negation operator (!) converts a non-zero operand into 0 and a zero operand into 1.

Example: 
`if (!valid)` is equivalent to `if (valid == 0)`

### Section 2.7: Type Conversions
