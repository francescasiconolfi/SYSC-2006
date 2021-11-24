# SYSC 2006 LECTURES

## Table of Contents
[Lecture 2](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-2)\
[Lecture 3](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-3)\
[Lecture 4](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-4)\
[Lecture 5](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-5)\
[Lecture 6](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-6)\
[Lecture 7](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-7)\
[Lecture 8](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-8)\
[Lecture 9](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-9)\
[Lecture 10](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-10)\
[Lecture 11](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-11)\
[Lecture 13](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-13)\
[Lecture 15](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-15)\
[Lecture 16](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-16)\
[Lecture 17](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-17)\
[Lecture 18](https://github.com/francescasiconolfi/SYSC-2006/blob/main/2006-Lectures.md#lecture-18)\
[Lecture 19]()

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

### Specifiers

##### Table 1: Format specifiers for printf() and scanf() statements.
| Format specifier | Data type | Notes |
| --- | --- | --- |
| %c | char | Prints/reads a single ASCII character |
| %d | int | Prints/reads a decimal integer value |
| %hd | short | Prints/reads a short integer value |
| %ld | long | Prints/reads a long integer value |
| %lld | long long | Prints/reads a long long integer value |
| %u | unsigned int | Prints/reads an unsigned integer |
| %hu | unsigned short | Prints/reads an unsigned short integer | 
| %lu | unsigned long | Prints/reads an unsigned long integer |
| %llu | unsigned long long | Prints/reads an unsigned long long integer |
| %f | float | Prints/reads a float floating-point value |
| %lf | double | Prints/reads a double floating-point value (lf = "long float") |
| %s | string | Prints the contents of a string (literal or array) up to null character; reads a string of characters from input up to a whitespace character |
| %% | percent | Prints the % character |

---

## Lecture 4

### Do-While Statement
General format:

``` C

int main()
{
  do {
    Y;
 } while (condition);
 
\\ is equivalent to:

  Y;
  while (condition) {
    Y;
  }
  
```

### For Loop
General format:

``` C

int main()
{
  for (initialization; condition; incrementation) {
    body;
  }
  
}

```

### Arrays
Declaration format: `type name[capacity]`
where # elements in array == *capacity* and each element is of the same specified *type*

**Indicies:**
- To access inidividual elements, use indexing (specify index in brackets), where indicies ranges from 0 to (*capacity* - 1) (i.e. array[1] points to the array's second element).
- An index that is negative or (>= *capacity*) will access memory outside of the array (do not want this).
- Indicies can also be expressions or function calls

Array processing loops:
``` C

int main()
{
  for (int i = 0; i < n; i++) {
    \\ do something with array
  }

}
```

If using array in a function:
- First parameter: `type name[]` where *capacity* is not specified
- Second parameter: `int n` where n is the # of elements the function should process

Notes: (1) When using an array as an argument (i.e. actually calling the function), only the array's name is necessary, (2) Arrays are passed by reference (i.e. functions can actually modify arrays.

Other note: sizeof() is a function that evaluates the amount of memory allocated to an array (or just one element if indexed) (int takes up 4 bytes; a pointer takes up 8).

---

## Lecture 5

### Array Example
``` C
int main()
  
  // const int LENGTH = 10;
  #define LENGTH 10
  int array[LENGTH];
  int i, j, temp, index;
  
  // initialize array
  for (i = 0; i < LENGTH; i++) {
    array[i] = i + 1;
  }
  
  // print array
  printf("Initial Array: ");
  for (i = 0; i < LENGTH; i++) {
    printf("%d ", array[i]);
  }
  
  printf("\n");
  
  // reverse array
  for (i = 0; i < LENGTH/2; i++) {
    index = LENGTH - i - 1;
    temp = array[i];
    array[i] = array[index];
    array[index] = temp;
    
    // print array
    printf("Intermediate Array: step %d: ", i + 1);
    for (j = 0; j < LENGTH; j++) {
      printf("%d ", array[j]); // shows array after each step
    }
    printf("\n");
  }
  
  // print array
  printf("Final Array: ");
  for (i = 0; i < LENGTH; i++) {
    printf("%d ", array[i]);
  }
  printf("\n");
  
  return 0;
  
```

### Finding Mean and Median of An Array Example

``` C

int main(void) {

  const int LEN = 6;
  int arr[] = [1, 5, 3, 4, 5, 2}; // creates array with exact necessary size according to amount of elements listed
  int sum = 0;
  double mean, median;
  
  for (int i = 0; i < LEN; i+= 1) { // i only exists inside for loop, since it is initialized inside
    sum += arr[i];
  }
  
  mean = sum / (LEN*1.0); // do not want int division
  
  sort(LEN, arr); // function that sorts data (not shown here)
  
  if (LEN % 2 == 0) {
    median = (arr[LEN/2] + arr[LEN/2 - 1] / 2.0;
  }
  else { // array is odd
    median = arr[LEN/2];
  }
  
  return 0;
  
}
```

### Finding Mode of An Array

``` C

int numTimes(int ar[], int n, int value) {
  int count = 0;
  for(int i= 0; i < n; i++) {
    if (ar[i] == value) {
      count += 1;
    }
  }
  
  return count;
}

int main(void)
{

  const int LEN = 6;
  int arr[] = {1, 5, 3, 4, 5, 2};
  int x = numTimes(arr, LEN, 3);
  int mode;
  int num;
  int temp;
  
  num = numTimes(arr, LEN, arr[0]);
  mode = arr[0];
  
  for (int i = 1; i < LEN; i++) {
     temp = numTimes(arr, LEN, arr[i]);
     if (temp < num) {
      num = temp;
      mode = arr[i];
     }
  }
  
  return 0;
} 
```

### Computer Memory Notes
When a function is called by, i.e. main(), or any function, the other function is used and accessed until the computer is finished with it, and then it is removed from the stack.

**Remember** if a function calls another that is below it, must include a function prototype above: `type function(type p1, type p2);`.

---

## Lecture 6

### Recall: Declaring Arrays
Method 1. Specifying Capacity

``` C

int main()
{
  
  type array[capacity];
}

```

Method 2. Initializing List

``` C

int main()
{
  
  type array[] = {1, 2, 3, 4, 5, 6};
}

```

where capacity is calculated based on how many values are in initializer list

### Structures
One of more variables grouped together under a single name (types can differ). This allows a group of related variables to be treated as a unit.

General format:
``` C

struct tag {
  type var1;
  type var2;
}
```
where var1 and var2 are members of the structure, and *tag* is name of tag.

Note: A structure declaration doesn't allocate memory.

Given the declaration of *point*, `struct point point1 point2` declares variables point1 and point2 as instances of type "struct point".

Visualizing the structures:

| | struct point | | struct point|
| --- | --- | --- |  --- |
| point1 | x int ? | point 2 | x int ? |
| | y int ? | | y int ? |

#### Initializing members of the structure:
`struct point point3 = {val1, val2}` assigns val1 to x and val2 to y.
OR
`point4 = (struct point) {val1, val2}` where point4 was previously declared as a struct point.

#### To declare a synonym for struct point:
`typedef struct point point_t` uses typedef ("type definition") to create synonym for struct point, in order to make it more concise.

Combining structure and typedef declarations:
``` C

typedef struct tag {
  type var1;
  type var2
} synonym;

```

#### Accessing Members:
General format: `variable.member = expression`

Example:
`point3.x += 20;`

Note: This becomes a regular int.

#### Structure Assignment
Can assign one variable to another, which will copy x, y, etc. values over (i.e. point1 = point2;)

#### Structures and Functions
``` C

point_t makepoint(int x, int y) {
  point_t temp;
  
  temp.x = x;
  temp.y = y;
  return temp;
}
```

Typical call:

``` C

int main() {

  int a, b;
  point_t point1;
  
  a = 320;
  b = 200;
  
  point1 = makepoint(a, b);
  
}
```

---

## Lecture 7

### Structures Example

``` C

typedef struct {
  int number;
  double credits;
  double GPA;
} student_t;

void printStudent(student_t student) {
  printf("Student Name: %d; Credits: %.1lf; GPA: %.2lf\n", student.number, student.credits, student.GPA);
}

student_t addCredit(student_t student, double credits, double numGrade) {
  
  double newCredits = student.credits + credits;
  student.GPA = ((student.credits * student.GPA) + (newCredits * newGrade)) / newCredits;
  student.credits = newCredits;
  
  return student;
  
  // or: return (student_t) {student.number, newCredits, ((student.credits * student.GPA) + (newCredits * newGrade)) / newCredits};
}

int main() {
  student_t bob = {123456789, 0, 0};
  student_t mary, fred;
  mary = (student_t) {123444444, 1, 10};
  fred.number = 123123123;
  
  printStudent(bob);
  
  bob = addCredit(bob, 1, 10);
  printStudent(bob);
  
  bob = addCredit(bob, 0.5, 12);
  printStudent(bob);
  
  bob = addCredit(bob, 0.5, 6);
  printStudent(bob);
  
  return 0;
}
```

### Pointers

#### Memory Organization
Memory can be viewed as a collection of consecutively-numbered cells, where:
- each cell holds an 8-bit byte
- a char is stored in one cell
- a 32-bit int is stored in 4 adjacent cells
- cell numbers are known as *addresses*
- a variable is a symbolic name for a group of cells
- a **pointer** is a variable that contains the address of a variable

#### Declaration of Pointers
General format: `type *var;`

where *type* is "pointer to int"

Can also write `type* var;` if declaring only one variable.

#### Address-of Operator
`&` is a unary operator that yields the address of its operand.

Example:
``` C

int main() {

  int *p;
  int x = 1, y = 2;
  p = &x;
}
```

assigns the address of x to variable p

Therefore, p now **points to** x, which contains int 1: p -> | 1 | x

To make another var equal to the value p points to: `y = *p;`
Note: Types have to match.

To change the variable p is pointing to: `*p = val`

\*p and x are SYNONYMS, so anywhere you would put x, you can put \*p.

Can also assign a pointer to another pointer:
``` C
  int *p2;
  p2 = p;
```
p2 and p now point to the same memory location

#### Precedence
'&' and '\*' have higher precedence than arithmetic, comparison, and logical operators.

#### Pointers and Functions
Integers are not called by reference in functions, so the actual value of the argument variables are not affected. Must use pointers to actually modify the values.

Swapping function:
``` C
  void swap(int *px, int *py) {
    int temp;
    
    temp = *px; // sets val of temp to val px points to (5)
    *px = *py; // make var px points to equal to the val py points to (a now contains 10)
    *py = temp; // make val py points to equal to same value as temp (b now contains 5)
}
 
int main() {
    int a = 5, b = 10;
    swap(&a, &b);
    return 0;
}
```
Note: Making temp a pointer will not work, since it does not have an initial value. Would have to make it point to something first, before you can assign it to the same val as another pointer.

---

## Lecture 8

Example: Pointers to pointers

``` C

int main() {
  int x;
  int *p;
  int **q;
  int ***r;
  
  x = 5;
  p = &x;
  q = &p;
  r = &q;
  
  printf("*p=%d; **q=%d; ***r=%d\n". *p, **q, ***r);
  
  return 0
  
}

Note: More asterisks indicates more levels of pointers (i.e. int **q is a pointer to a pointer to an int).

### sizeof(struct)

Function sizeof() will determine size needed for a struct based on its variable needs, which are stored in blocks of 8 bits (therefore a struct with an int and a double variable will need 16 bits, not 12, since the double is not stored in the leftover 4 of the int, since it cannot fully fit; a struct with an int and a float would only need 8, since the float can fit inside the leftover 4 bits).

### Pointers and Structures
Pointing to struct types:
``` C

  point_t* ptr; // creates pointer, ptr, which points to a value with type struct
  point_t point1 = {320, 200}; // initializes point1 as a variable with type point_t, thereby making it a struct
  
  ...
  
  ptr = &point1; 
  
  /* pointer ptr now points to struct point1 (contains address of first byte in memory alloacted to point1 since it takes up more than one mem address */
  
```

Notes:

- \*ptr is the entire structure
- (\*ptr).x and (\*ptr).y are the members
- (\*ptr).x is read as "the x member of the structure pointed to by ptr"
- parentheses are required since the dot operator has higher precedence than the asterisk: \*ptr.x means \*(ptr.x) which is an error since it would be trying to access the x member of ptr, not the value ptr points to

#### -> Operator
`ptr->member` is shorthand for `(*ptr).member` (if ptr points to a structure).

Example:
``` C
 
  point_t* ptr;
  point_t point1;
  ...
  ptr = &point1;
  ptr->x = 320; // equivalent to (*ptr).x = 320;
  ptr->y = 200; // equivalent to (*ptr).y = 200;
```

#### Function Arguments
Do not want to pass structures as function arguments since the function has to copy the entire structure to use it, which uses a lot of memory and time (pass-by-value semantics).

Instead, pass pointers to structures as function arguments.

Version 1:
``` C

typedef struct {
  int x;
  int y;
} point_t;

void addpoints(point_t* ptr1, const point_t* ptr2) { 
    // putting "const" is good documentation, does not allow changes to the struct, and makes code more efficient
    
    ptr1->x = ptr1->x + ptr2->x;
    ptr1->y = ptr1->y + ptr2->y;
    
}

int main() {

  // typical call:
  point_t point1, point2;
  point1 = makepoint(320, 200); // or point_t point1 = {320, 200};
  point2 = makepoint(30, 40);
  
  addpoints(&point1, &point2);
  
}
```

Version 2:
``` C
// What if we don't want the function to modify point1?

void addpoints(const point_t* ptr1, const point_t* ptr2, point_t* sum) {
  sum->x = ptr1->x + ptr2->x;
  sum->y = ptr1->y + ptr2->y;
}

#### Returning a Pointer

The following is a function that returns a POINTER pointing to a value of TYPE "point_t".
``` C

point_t* addpoints(const point_t* ptr1, const point_t* ptr2) { // can also put a space between point_t and the asterisk
  point_t sum;
  sum.x = ptr1->x + ptr2->x;
  sum.y = ptr1->y 
  
  return &sum; // this is a BUG since it is a local variable and will disappear from the stack
}

To actually make this work, allocate the structure on the HEAP (coming soon).

#### Pointers and Arrays
``` C

  int a[10] // declares an array with 10 int elements
  
  int *pa;
  pa = &a[0]; // pa points to element 0 in array a
  
  int x = 3;
  *pa = x; // copies contents of x into a[0]
```

**Pointer Artihmetic**:
pa+1 is the address of the next element
pa+i is the address of the i-th element after the one pa points to

So:
- if `pa = &a[0];`
- `pa+1` is the address of a[1]
- \*(pa+1) is the contents of a[1]
- pa+i is the address of a[i]
- \*(pa+i) is the contents of a[i]

The name of an array is a synonym for the address of its 0th element.\
This means: `pa = &a[0];` can be written as `pa = a;`.\
Therefore the value of a+i is the address of the i-th element after a\[0], and \*(a+i) is the contents of the i-th element after a[0].\
This means `*(a+i)` is equivalent to `a[i]`.\
Can also do so with a pointer: `pa[i]` is equivalent to `*(pa+i)` a.k.a. **you can index pointers like you do arrays**.

An important difference between points and array names: an array can not be assigned to a pointer: `a = pa;` is not permitted

#### Arrays as Arguments
Example: Avg of an array of ints

``` C

double average(int data[], int n) {
  double sum = 0;
  int i;
  
  for (i = 0; i < n; i++) {
    sum = sum + data[i];
  }
  
  return sum / n;
}
```

An array name used as a fxn argument causes C to pass the address of the 0th element:

``` C
double average(int data[], int n); // where data is a pointer that points to the array in its argument place when the fxn is called
int samples[100];

average(samples, 50);
// is converted to
average(&samples[0], 50);
```

---

## Lecture 9

### Arrays as Arguments Continued

``` C

double average(int data[], int n) {
  ...
}

// is equivalent to

double average(int *data, int n) { // first parameter is a "pointer to int"
  double sum = 0;
  int i;
  
  for (i = 0; i < n; i++) {
    sum += *data + i);
  }
  
  return sum / n;
  
}
```

#### Pointer Arithmetic
Pointers are variables, so can add and subtract values from them: 
Example: `pa = pa + 1;` updates *pa* to point to next array element.

Common idioms:
- `pa += `;`
- `++pa;`
- `pa++;`

Example: "Walking Pointer"

``` C

double average(int *data, int n) { 
  double sum = 0;
  int i;
  
  for (i = 0; i < n; i++) {
    sum += *data;
    data += 1; // "Walks the pointer through the array
  }
  
  return sum / n;
  
}
```

Example: Loop variable (i) as a pointer to int

``` C

double average(int *data, int n) { 
  double sum = 0.0;
  int *i;
  
  for (i = data; i < n + data; i++) {
    sum += *i; // i will walk through array
  }
  
  ...
  
}
```

Summary:
- fxn parameter `int data[]` is equivalent to int \*data
- fxn can treat data as either an array of integers (data[i]), or a pointer to the first int in an array of ints, where each int can be accessed (\*data or \*(data+i))

### Character Strings
C does not have a string type.

**String constant/literal**: A sequence of characters in double quotes, stored as an array of characters All strings are terminated with NUL ('\0'.

Ex: "SYSC" would be stored as 'S' 'Y' 'S' 'C' '\0'

Notes: (1) '\0' is not equivalent to '0' (the character zero) or NULL (the null pointer), (2) The number of elements in the array is always one more than the # of characters specified between quotes (because of NUL).

Adjacent string constants are concatenated at compile time (i.e. "Hello, " "world!" would become "Hello, world!".

#### String Variables
The declaration: `char dept[] = "SYSC";` allocates an array named *dept*, initialized with 5 chars: 'S' 'Y' 'S' 'C' '\0'

``` C
  
  char dept[] = "SYSC";
  
  // is equivalent to:

  char dept[5];
  dept[] = 'S';
  dept[] = 'Y';
  dept[] = 'S';
  dept[] = 'C';
  dept[] = '\0';
  
  // dept = "SYSC" would give an error; you cannot do this! Specify one character at a time.
  
```

Notes: (1) If you specify a size too small for an array (# of char without including NUL for example), there will be a compile error, (2) If you specify a size too big for an array, the extra spaces are ignored.

Putting *const* in front of char would make the string array immutable, and therefore none of its char elements could later be replaced.

#### String Operations
'+' CANNOT be used for string concatenation.

#### Using <string.h>

##### strlen
Format: `size_t strlen(const char *s);`
Function: Returns the length of the string pointed to by s, EXCLUDING '\0'
Note: "size_t" specifies an int that is >= 0 (int would still work).

##### strcmp
Format: `int strcmp(const char *s, const char *t);`
Function: Compares the string pointed to by s to the string pointed to by t.
Note: Returns negative value if s > t; Returns 0 if s == t (same length, characters, in same order, i.e. arr1\[i] == arr2\[i]); Returns positive value if s > t.

Example:
``` C
int main() {

  char name1[30];
  char name2[30];
  
  if (strcmp(name1, name2) != 0) {
    printf("Strings are different.");
  } else {
    printf("Strings are same.");
  }
}
```

##### strstr
Format: `char *strstr(const char *s, const char *t);`
Function: Searches for the first occurence of the string pointed to by t in the string pointed to by s.
Note: If string is found, returns a pointer to the located string; If string isn't found, returns **NULL pointer**.

##### strcpy
Format: `char *strcpy(char *dst, const char *src);`
Function: Copies all chars in string pointed to by src (including NUL) to the string pointed to by dst, then returns dst.
Note: Programmer is responisble for ensuring dst is big enough to hold all chars from src.

##### strcat
Format: `char *strcat(char *dst, const char *src);`
Function: Appends a copy of the string pointed to by src (including NUL) to end of the string pointed to by dst, then returns dst
Notes: (1) NUL at the end of dst is overwritten by first char of src, (2) Programmer is responisble for ensuring dst is big enough to hold all chars from src.

---

## Lecture 10

##### Walking Pointer Implementation for strcpy

Example:
``` C

char *CU_strcpy(char *dst, const char *src) {
  char *dest = dst;
  while ((*dst = *src) != '/0') { // dst points to same thing as src, which cannot be equal to NUL while the loop runs
    dst += 1;
    src += 1;
  }
  return dest;
}

// MORE CONCISE:

char *CU_strcpy(char *dst, const char *src) {
  char *dest = dst;
  while (*dst++ = *src++) { // this will stop when the statement in parentheses returns 0 (false)
  }
  return dest;
}
```

### Allocating Memory on the Heap

``` C
#include <stdlib.h>
.
.
.
int *p;
p = malloc(sizeof(int)); // malloc(para) is a function "memory allocation" with para as a # of memory allocations required on heap
if (p != NULL( {
  *p = 3;
} else {
  // error - malloc failed, NULL returned
}
```

**sizeof(type-name)** is an operator that calculates the amount of memory (in bytes) required to hold one value of the specified type.

**malloc(size)** allocates a block of memory of the specified size (bytes), from the heap.
- returns a pointer to allocated memory block
- is memory cannot be allocated, NULL is returned
- <stdlib.h> required

**assert(exp)** is a function that will terminate the program (w/ a error) if the expression (exp) is false, or will allow the program to continue if it is true.
- <assert.h> required

Typical format:
``` C

#include <stdlib.h> 
#include <assert.h>

int *p;
p = malloc(sizeof(int));
assert(p != NULL); // typically comes after a malloc declaration
*p = 3;
```

#### Allocating a Struct

``` C

// allocate a struct that represents point (0, 0)

point_t *ptr;
ptr = malloc(sizeof(point_t));
assert(ptr != NULL);
ptr->x = 0;
ptr->y = 0;
```

#### Allocating an Array

``` C

#include <stdlib.h> 
#include <assert.h>

int *pa;
pa = malloc(10 * sizeof(int)); // allows for array of size 10
assert(pa != NULL);
```

#### Example
``` C

int main(void) {

  // one int from heap
  int *ptr_to_int;
  ptr_to_int = malloc(sizeof(int));
  assert(ptr_to_int != NULL);
  
  *ptr_to_int = 3;
  
  // one point_t struct from heap
  point_t *ptr_to_struct;
  ptr_to_struct = malloc(sizeof(point_t));
  assert(ptr_to_struct != NULL);
  
  ptr_to_struct->x = 0;
  ptr_to_struct->y = 0;
  
  // an array of 10 ints from heap
  int *ptr_to_array;
  ptr_to_array = malloc(10 * sizeof(int));
  assert(ptr_to_array != NULL);
  
  // now giving it values:
  for (int i = 0; i < 10; i += 1) {
    ptr_to_array[i] = i; // or *(ptr_to_array + i) = i;
  }
  
  free(ptr_to_int); // must free pointers from memory on heap at end of code
  free(ptr_to_struct);
  free(ptr_to_array); 
  // include one free() for every malloc()
  
```

#### Fixing addpoints function

``` C

typedef struct {
  int x;
  int y;
} point_t;

point_t *addpoints(point_t *ptr1, point_t *ptr2) {

  point_t *sum;
  
  sump = malloc(sizeof(point_t));
  assert(sump != NULL);
  sump->x = ptr1->x + ptr2->x;
  sump->y = ptr1->y + ptr2->y;
  return sump;
}
```

---

## Lecture 11

### Allocating Arrays

``` C

#include <stdlib.h>
#include <assert.h>

int *alloc_array_of_ints(int capacity) {
  int *pa;
  
  assert(capacity > 0); // stops program if statement is false
  pa = malloc(capacity*sizeof(int))
  assert(pa != NULL); // pa would be assigned NULL if malloc() failed
  return pa;
  
  free pa; // release the array
  pa = NULL;
}
```

Note: For every malloc(), include a free()!

### Freeing Memory
The pointer passed to free must be one that was returned by a previous call to malloc() (passing any other pointer will likely corrupt the heap).

``` C

  int *pa;
  int x;
  int capacity = 10;
  pa = malloc(capacity * sizeof(int));
  
  free(&x); // NO! x is not in the heap!
  free(pa+1); // NO! pa+1 isn't the address of a (pa+1 is the second element of array a)!
  free(pa); // YES! Releases the array!
  pa = NULL;
```

Note: Do not free the memory more than once (can corrupt the heap).

Free does not actually change the pointer's argument, it lets the program know the memory will not be used anymore.

---

## Lecture 13

### Looping Through Characters (Number-Letter Conversion)
ex.
``` C

int main() {
  for (int i = 0; i < 5; i++) {
    printf("%d ", i + 'A'); // prints 65 66 67 68 69
  }
  
  for (int i = 0; i < 5; i++) {
    printf("%c ", i + 'A'); // prints A B C D E
  }
  
  return 0
  
}
```

### A Structure That Knows Its Capacity

``` C 

#include <assert.h>
#include <stdlib.h>

typedef struct {
  int cap;
  int inc;
  int count;
  int *elems;
} arr_t;

arr_t *create_arr_t(int capacity, int increment) {
  assert(capacity > 0);
  assert(increment > 0);
  
  arr_t *p = malloc(sizeof(arr_t));
  assert(p != NULL);
  
  p->cap = capacity;
  p->inc = increment;
  p->count = 0;
  p->elems = malloc(capacity * sideof(int));
  
  return p
  
}

void check_arr_t(arr_t *p) {
  assert(p != NULL && p->cap > 0 && p->inc > 0 && p->count >= 0 && p->elems != NULL && count <= cap);
  
}

void add_arr_t(arr_t* p, int value) {
   check_arr_t(p);
   
   if (p->count == p->cap) {
     p->cap += p->inc;
     int *new = malloc(p->cap*sizeof(int));
     assert(new != NULL);
     for (int i = 0; i < p->count; i++) {
        new[i] = p->elems[i];
     }
     free(p->elems); // getting rid of old array
     p->elems = new;
   }
   
   }
   
   p->elems[p->count] = value;
   p->count++;
   // p->elems[p->count++] = value; stores value in LHS and adds 1 to p->count
   
}

int main(void) {

  arr_t *ptr = create_arr_t(3, 2);
  add_arr_t(ptr, 5);
  add_arr_t(ptr, 3);
  add_arr_t(ptr, 99);
  add_arr_t(ptr, 7);
  add_arr_t(ptr, -5);
  add_arr_t(ptr, 0);
  
  for (int i = 0; i < ptr->count; i++) {
    printf("%d ", ptr->elems[i]);
  }
  printf("\n");
  
  free(ptr->elems);
  ptr->elems = NULL;
  free(ptr);
  ptr = NULL;
  
  return 0;
  
}
```

### Linked Lists
Linked lists are made up of *nodes* and a pointer to the same structure type (to another node).\
The *head pointer* points to the first node, and the end pointer is a special pointer to NULL marking the end of the linked list.\
Can add a *tail pointer* to decrease the running time of certain operations.

The simplest linked list: The head pointer is NULL.\
Next simplest linked list: The head pointer points to a node, and the next pointer points to NULL.

A singlely-linked list: Start at head, and walk towards tail.\
A doublely-linked list: Start at head; can start at end; can walk back to beginning after any node.

Each node is an intnode_t and the head is a pointer to a type intnode_t:
``` C

typedef struct intnode {
  int value;
  struct intnode *next; // because this is above synonym declaration, must use long form of struct intnode
} intnode_t;

intnode_t* head;
```
Notes: (1) *value* stores one int, (2) *next* stores the pointer to the next node in a linked list.

---

## Lecture 15 

### Head and Tail Pointers
Head pointer points to the first node, and tail pointer points to the last node.

### Creating a Node
Allocating a node on the heap:

``` C

intnode_t *p = malloc(sizeof(intnode_t));
assert(p != NULL);
p->value = 10;
p->next = NULL;
```

NULL pointer: a constant pointer that does not point to any object.

An **empty list** contains NULL in the head.

### Designing Operations
Ensure algorithm works for following cases:
- empty lists
- operation ahead of or at first node
- operation after or at last node
- operation in middle of list

Example 1: Inserting at Beginning
Consider cases 1 & 2:\
Case 1: Create new node after head1.\
Case2: Insert node between head1 and first node (pass value in new node, and pointer to what head pointer pointed to; head pointer points to new node)

``` C

if (head == NULL) {
  head = intnode_construct(value, NULL);
}
else {
  head = intnode_construct(value, head);
}

// Simplifying:

head = intnode_construct(value, head);

```

## Lecture 16

### Traversing a Linked List
Make another ptr point to head's node, then update it so it continues to move throughout the nodes. If the ptr is NULL, know that have walked all the way through list.

In other words, if the ptr is named "curr", writing a loop like so:
- curr = head
- done? (curr == NULL)?
- if NO, then do something with curr->value
- curr = curr->next // curr now points to what the ptr in the current node points to (i.e. the next node)

For Loop version:
``` C

intnode_t *curr;
for (curr = head; curr != NULL; curr = curr->next) {
  // visit curr->value and do something
}

```

### Functions that Traverse
Writing a function that returns the length of the list (# of nodes): Walk through list and add to "count" (# of nodes) and "sum" (of node values)

Two cases:
- empty list (return 0)
- non-empty list (return #)

Writing a function that appends a node to the end: Stop when curr->next = NULL, then set curr->next to point to new node.

Note: Ensure curr != NULL (since curr->next would cause an issue). If curr == NULL, this is a different case, since there are no nodes in the list (if statement).

---

## Lecture 17

### Adding and Deleting Nodes at the End of a Linked List

``` C

intnode_t *append(intnode_t* head, int vale) {

intnode_t *newnode = intnode_construct(value, NULL);

  if (head == NULL) {
    return newnode; // only node in list
  }
  
  // for lists with nodes, traverse list until curr->next is NULL
  intnode_t *curr;
  for (curr = head; curr->next != NULL; curr = curr->next) {
    printf("currentvalue is: %d\n", curr->value); // shows us what's happening
  }
  curr->next = newnode;
  
  return head;
}

// method 1: using two ptrs
intnode_t *delnode(intnode_t* head) {
  
  if (head == NULL) {
    return NULL;
  }
  
  //traverse using prev and curr; prev points to last node and curr points to NULL by end
  intnode_t *prev, *curr;
  for (prev = NULL, curr = head; curr->next != NULL; prev = curr, curr = curr->next) {
    printf("The current node contains: %d\n", curr->value);
  }
  free(curr); // finished using last node
  
  // case with only one node
  if (prev == NULL) { // i.e. if there was only one node in the list, set head to NULL
    head = NULL;
  } else {
     prev->next = NULL; // i.e. make the pointer after prev point to NULL (thereby ending the list)
   }
   
   // method 2: using one ptr
   intnode_t *remove_last(intnode_t *head) {
    
    intnode_t *current;
    
    // case 1: empty list (i.e. there's nothing to delete)
    assert(head != NULL);
    
    // case 2: there is exactly one node
    if (head->next == NULL) {
      free(head);
      head = NULL;
    } // case 3: there is > 1 node
    else {
      for (current = head; current->next->next != NULL; // as long as the ptr of the next node != NULL
      current = current->next;
    }
    // current now poiuts to the node before the node to delete
    free(current->next);
    .. current now points to last node
    current->next = NULL;
    
    return head;
  }
   
 ```

### Big O Notation
Format: O(n), where n is the performance (largest value from formula).

**Order 1: O(1)**
- Fixed algorithms that don't depend on *n*

Example:
- Inserting a node at the beginning of a linked list takes 4 steps, no matter *n* (i.e. the amount of nodes), so this is Order 1.
- Changing *n* doesn't change the # of steps

**Order *n*: O(n)**
- Algorithms that depend on *n*
- Grows directly in relation to *n* (linear relationship)

Example:
- Inserting a node at the end of a linked list depends on *n* (i.e. the amount of nodes that need to be walked through), so this is Order n.
- Nested loops (i = 1-n, j = 1-n, gives a formula with n^2) have notation O(n^2))

Order 2^N: O(2^N)
- Alogrithms whose growth doubles with each addition to the input data set (exponential growth curve)

Example:
- Fibonacci numbers

Order log(n): O(log N)
- Algorithms that peak in the beginning and slowly flatten out as the size of the data set increases 

Example:
- Binary search (middle of data set is selected, and compared to target value to see if it is less or greater than the median (to see which data set to next compare to i.e. the first half or latter half)

**Looking at different scenarios:**

Adding a node at the beginning of a linked list is O(1) (head points to new node and new node's ptr points to original first node).

Adding a node at the end of a linked list is O(n) (ptr has to walk through entire list).

Adding a node at the end of a linked list with a tail ptr is O(1) (to delete would still be O(n)).

Adding a node at the beginning of an array is O(n) (have to shuffle all the values over).

Adding a value at the end of an array is O(1) (simply inserts at end if there is space).

Deleting an element anywhere except the last element in an array is O(n) (requires shuffling).

### Ring Arrays
An array in the form of a ring.

Start: Beginning of the array\
End: First empty space (first element without value)\
Count: Number of values\
All begin with value 0. Highest possible value is (size - 1).

Note: As new values are inserted, End and Count have 1 added to them. To remove beginning element, simply add 1 to Start.

---

## Lecture 18

Freeing the first node without freeing the other nodes in a linked list causes a memory leak. This can cause the memory to become filled without any way to access it.

One way to properly delete the first node:
``` C
// inside a free all nodes function:

intnode_t *current, *node_to_delete;

for (intnode_t *current = head; current != NULL; ) {{
  node_to_delete = current;
  current = current->next; // moves current to next node
  free(node_to_delete); // frees first node
}
```

Example: Inserting a node according to value order
``` C

intnode_t* insert_in_order(intnode_t* head, int value) {
  
   intnode_t *prev, *curr;
   for (prev = NULL; curr = head; curr != NULL && value > curr->value; pre = curr, curr = curr->next) {
    printf("The current node contains: %d\n", curr->value);
   }
   
   if (prev == NULL) {
    head = intnode_construct(value, curr);
   } else {
    prev->next = intnode_construct(value, curr);
   }
   
   return head;
}
```

### Queues and Stacks

#### Queues
Imagery: a queue/line in a store

*Queue*: A collection in which the elements are maintained in the order in which they are added (First-in, First-out: FIFO)
- Enqueue: Insert at end
- Dequeue: Remove from beginning
- Look/Peek: Check the beginning

Example: 
- Enqueue 5, now have: (front) 5 (rear)
- Enqueue 3, now have: (front) 53 (rear)
- Enqueue 7, now have: (front) 537 (rear)
- Dequeue (returns 5), now have: (front) 37 (rear)
- Dequeue (returns 3), now have: (front) 7 (rear)

Note: Since elements are always added at rear but retrieved from front, should pick a data structure that permits efficient manipulation of both ends of the queue (access to middle is not important)

**With Singly Linked Lists**

*Ways of Implementing*
With one pointer: If head is 'front', enqueue is O(n), and dequeue is O(1)\
With one pointer: If head is 'rear', enqueue is O(1), and dequeue is O(n)\
With two pointers: If head is 'rear' and tail ptr is 'front', enqueue is O(1) and dequeue is O(n) (need access to node before to change it to NULL)\
**With two pointers: If head is 'front' and tail ptr is 'rear', enqueue is O(1) and dequeue is O(1)** (BEST WAY)

Circular Linked List: Instead of last node pointing to NULL (know it's last node because rear (tail ptr) points to it, it points to head (saves memory)

**With Arrays**
If want both dequeue and enqueue operations to be O(1), use a *ring array* 

#### Stacks
Imagery: A stack of plates

*Stack*: A collection in which the elements are mainted in the order in which they were added (Last-in, First out: LIFO)
- Push: Insert at top
- Pop: Remove from top
- Peek: Check top

Example:
- Push 10, now have: (top) 10
- Push 20: (top) 20 | 10
- Peek: 20 returned
- Pop: (top) 10 (20 removed & returned)

Other Operations:
- Determine if stack is empty
- Empty a stack
- Determine length
- Compare two stacks for equality
- Print contents
- Iterate over contents

Unsupported Operations:
- Searching a stack for a specific element
- Removing a specific element
- Retrieving/Replacing/Inserting/Deleting an element at a specific position

Note: These all contradict LIFO

**With Singly Linked Lists**

*Ways of Implementing*
- With one pointer: Head is 'top' and the last node is the 'bottom' (push, pop, and peek operating on the front of the linked list with be O(1)

Note: Both a tail pointer or a doubly linked list are unnecessary since already achieved O(1)

``` C

typedef struct {
  intnode_t *top;
  int size; // not necessary but useful
} intstack_t;

```

---

## Lecture 19

### Working with Queues

``` C

typedef struct {
  intnode_t *front;
  intnode_t *rear;
  int size;
} intqueue_t;
  
intnode_t *intnode_construct(int value, intnode_t *next)
{
    intnode_t *p = malloc(sizeof(intnode_t));
    //assert (p != NULL);
    p->value = value;
    p->next = next;
    return p;
}

/* Return a pointer to a new, empty queue.
 * Terminate (via assert) if memory for the queue cannot be allocated.
 */
intqueue_t *intqueue_construct(void)
{
    intqueue_t *queue = malloc(sizeof(intqueue_t));
    // assert(queue != NULL);

    queue->front = NULL;
    queue->rear = NULL;
    queue->size = 0;
    return queue;
}

void intqueue_enqueue(intqueue_t *queue, int value)
{
    //assert(queue != NULL);

    // Store value in a new node, and append the node at the rear of
    // the queue (the tail of the linked list).

    intnode_t *p = intnode_construct(value, NULL);

    if (queue->front == NULL) {
        // Case 1: the queue is empty.
        // front will be NULL if we are enqueue'ing a value in an 
        // empty queue. Because we're inserting a node in an empty 
        // linked list, we have to update the pointer to the head node.
        queue->front = p;
    } else {
        // Case 2: the queue is not empty.
        // Append the node to the tail of the queue's linked list.
        queue->rear->next = p;
    }
    queue->rear = p;  // Always update the pointer to the node
                      // at the tail of node's linked list.
    queue->size += 1;
}

/* Copy the value at the front of a queue to the variable pointed to
 * by parameter element, remove that value from the queue, and return 
 * true. Return false if the queue is empty.
 * Parameter queue points to the queue.
 * Terminate (via assert) if queue is NULL.
 */
 
 _Bool intqueue_dequeue(intqueue_t *queue, int *element)
{
    // assert(queue != NULL);

    // Case 1: the queue is empty.
    if (queue->size == 0) {
        return false;  // Can't dequeue a value from an empty queue.
    }

    // Case 2: the queue has exactly one element.
    // Case 3: the queue has more than element.  
    // Retrieve the value from the node at the front of the queue
    // (the head of the linked list) and deallocate that node.
    // The next node (if any) becomes the node at the queue front.

    *element = queue->front->value;

    intnode_t *node_to_delete = queue->front;
    queue->front = queue->front->next;  // Update the pointer to the 
                                        // node at the head of the
                                        // queue's linked list.
    free(node_to_delete);

    // Extra processing for Case 2.
    // front will be NULL if the queue is now empty; i.e., if we just
    // performed a dequeue operation on a queue with one element.
    // Because the queue is now empty, we also have to NULL the pointer
    // to the rear of the queue.

    if (queue->front == NULL) {
        queue->rear = NULL;  // front and rear are both NULL in 
                             // an empty queue
    }
    
    queue->size -= 1;
    return true;
}
```

### Ring Array Implementation

``` C

typedef struct {
  int* array;
  int capacity;
  int size; // number of elements currently stored
  int start; // index of the first one
  int end; // index one after the last one
} ringarray_t;

```
 
