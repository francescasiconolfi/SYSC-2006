# SYSC 2006 LECTURES

## Table of Contents
[Lecture 2](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-2)
[Lecture 3]()

## Lecture 2

### Imperative Programming
Computation specified using statements that change the program's *state*.

The state is maintained using variables.\
Assignment statements change the program's state.\
Statements are executed sequentially.

Some Terms:
- *Loop*: Executes a sequence of statements multiple times
- *Conditional Branch*: A sequence of statements are executed only if the condition is True
- *Unconditional Branching*: jumps and subprograms/functions/procedures

Python vs. C:

In Python:

``` Python

print("Hello, world!")

```

In C:

``` C

int main()
{
  printf("Hello, world!\n");
  
  return 0;

}

```

Example: Farenheit vs. Celsius

In Python:

``` Python

lower = 0
upper = 300
step = 20

fahr = lower
while fahr <= upper:
  celsius = 5 / 9 * (fahr - 32)
  print(fahr, round(celsius, 1))
  fahr = fahr + step
  
```

In C:

``` C

#include <stdio.h>

int main(void):
{
  int lower, upper, step;
  float fahr, celsius;
  
  // Set lower and upper limits of table and step size
  lower = 0;
  upper = 300;
  step = 20;
  fahr = lower;
  
  while (fahr <= upper)
  {
    celsius = 5.0/9.0 * (fahr - 32.0);
    printf("%4.0f %6.1f\n", fahr, celsius);
    fahr = fahr + step;
  }
 
 return 0
 
 }
 
 ```

Analyzing Step-By-Step:

1. `#include <stdio.h>` is a *header file* read by the C compiler which contains information about the std I/O library (i.e. printf() fxn).

2. Each program contains at least one fxn, and execution always begins with main().
- The function header is int main(void), where int declares the fxn is returning an integer, and void declares the fxn has no argument list
- Statements in the function body are always enclosed in braces ({}) and indented (though indentation is not required by the compiler)
- Statements are terminated by semicolons (;)

3. A one line comment begins with //; a multi-line comment beings with /* and ends with */.

4. Variables must be declared before use by specifying the type of the variable before the name(s).

5. Assignment statements have the form: `variable = value`.

6. Iteration *while* loop has general format:

``` C

int main()
{
  while (condition)
  {
    body;
  }

}
```

where braces are only required for bodies spanning multiple lines.

Note: The body is only iterated over again if condition is True.

7. `printf("%4.0f %6.1f\n", fahr, celsius);` specifies format of each variable interpretation like so:
- % specifies formatting is following
- 4 in '%4.0f' specifies the value will be at least 4 characters wide
- 0 in '%4.0f' specifies the value will have no decimal point and no fractional digits
- 1 in '%6.1f' specifies the value (celsius) will have 1 digit after its decimal point
- The first value declared by % corresponds to the first variable listed after the str, and so on

### Elements of C

Fundamental Types:
- *char* (character - usually a byte)
- *int* (signed integer)
- *float* (single-precision floating-point)
- *double* (double-precision floating-point)
- *_Bool* (Boolean - added in C99)
- *_Complex* (Complex numbers - added in C99)

Note: There is no str type.

Type Qualifiers:
- unsigned
- short
- long

Examples:
1. 1234 is an int
2. 1.2, -7.2, 2e-3. 7.3e+4 are doubles
3. 'x' is a char
4. "x" and "hello" are str literals

Rules for Naming Variables:
- First character must be a letter (underscore included) (convention: lowercase)
- Remaining characters can be letters and digits 

Rules for Using Variables:
- Must declare a variable before use (ex. `int lower; upper;`)
- Can initialize variables whilst declaring them (ex. `int k = 0`)

Arithmetic Operators:
- Binary Operators (*, /, % have precedence over +, -)
- Integer Operators (when operands are all *int* - always rounds towards 0, as of C99) (% is only used with integers)

Relational Operators:
- \>, >=, <, <= have precedence over ==, !=

Note: Arithmetic operators > Relational operators

Operands are converted to a common type before evaluation ("narrower" operands are usually converted to "wider" operands).
- Any statements with *double*s will cause all operands to convert to *double*
- Any statements with *float*s will cause all operands to convert to *float*
- Otherwise, *char* will be converted to *int*

### If Statements
General format:

``` C

int main()
{

  if (expression)
  {
    statement 1;
    statment 2;
  }
  
return 0

}

```

Note: Statments are executed if *expression* is True.

### If-Else Statements
General format:

``` C

int main()
{

  if (expression)
  {
    statement 1;
    statment 2;
  }
  else 
  {
    statement 3;
    statement 4;
  }
  
return 0

}

```

Notes: (1) `else` is executed if *expression* is False, (2) There is no elif keyword, so only have nested if statements (else if statements), (3) There is only ever maximum one 'if' and 'else', but can have any number of 'else if' statements.

### For Loops
General format:

``` C

int main()
{

  for (expr1; expr2; expr3)
  {
    statements;
  }
  
  // Furthermore:
  
  for (initial statement; condition; incrementation)
  {
    statements;
  }
  
  // Is equivalent to:
  
  expr1;
  while (expr2)
  {
    statements;
    expr3;
  }

}

```

Example:

``` C

int main()
{
  int i;

  for (i = 0; i < n; i = i + 1)
  {
    
    printf("i is %d.\n", i)
    
}
  
```

### Do-While Loop
General format:

``` C

int main()
{
  do
  {
  
  statement 1;
  statement 2;
  
  }
  while (expression);

}
  
```

Note: The loop body is executed at least once, until *expression* in *while* loop is evaluated. If *expression* is True, the loop body is executed once more, and then *expression* is re-evaluted, and so on.

### Functions
Functions must be declared before use:
- Define the function ahead of all functions and then call it
- Put a function prototype ahead of all functions that call the function

Function Prototypes:\
General format: `type fxn(type parameter1, type parameter2...);`

Example:

``` C

#include <stdio.h>

int power(int m, int n); // Function prototype appears before calling, so no error

int main(void):
{
  
  int i = 0;
  while (i < 10)
  {
    printf("%d %d %d\n", i, power(2, i), power(-3, i));
    i = i + 1;
  }

  return 0;
 
}

int power(int base, int n)
{

  int p = 1;
  while (n > 0)
  {
  
    p *= base;
    n--;
  
  }
  
  return p;

}
 
```
 
**Arguments**:\
All function arguments are passed by value.\
Altering a parameter does not modify the corresponding argument.

### Example
zyBooks Challenge 4.7.1:

METHOD 1:

``` C

#include <stdio.h>

int main()
{
  int userNum;
  int i;
  int j;
  
  userNum = 10;
  
  // print values from 0 - userNum, one per line with spaces, equal to the number being printed
  
  for (i = 0; i <= userNUm; i++)
  {
    for (j = 0; j < i; j++)
    {
      printf(" ");
    }
    printf("%d\n", i);
  }

}
 
```

METHOD 2:

``` C

#include <stdio.h>

void printNspaces(int n)
{
  int i;
  for  (i = 0; i < n; i ++)
    {
      printf(" ");
    }
}

int main()
{
  int userNum;
  int i;
  int j;
  
  userNum = 10;
  
  // print values from 0 - userNum, one per line with spaces, equal to the number being printed
  
  for (i = 0; i <= userNUm; i++)
  {
    printNspaces(i);
    printf("%d\n", i);
  }

}

```

METHOD 3:

``` C

#include <stdio.h>

void printNspaces(int n)
{
  int i;
  for  (i = 0; i < n; i ++)
    {
      printf(" ");
    }
}

int numDigits(int n)
{
  int count;
  for (count = 0; n! = 0; count ++)
  {
    n = n / 10;
  }
  return count;
}

int main()
{
  int userNum;
  int i;
  int j;
  
  userNum = 10;
  
  // print values from 0 - userNum, one per line with spaces, equal to the number being printed
  
  for (i = 0; i <= userNum; i++)
  {
    
    printf("%*d\n", i + numDigits(i), i); // '*' is replaced by first value argument (i + numDigits(i)) and d is replaced by second (i)
  }

}

```

Note: Incrementing by 1 can be represented by double addition signs (i.e. `i++` is equivalent to `i = i + 1`, and decrementing by 1 can be represented by double subtraction signs (i.e. `i--` is equivalent to `i = i - 1`).

---

## Lecture 3

### 

##### Table 1: Format specifiers for printf() and scanf() statements.
| Format specifier | Data type | Notes |
| --- | --- | --- |
| %c | char | Prints/reads a single ASCII character |
| %d | int | Prints/reads a decimal integer value |
| %f | float | Prints/reads a float floating-point value |
| %lf | double | Prints/reads a double floating-point value (lf = "long float") |
| %s | string | Prints the contents of a string (literal or array) up to null character; reads a string of characters from input up to a whitespace character |
| %% | percent | Prints the % character |

