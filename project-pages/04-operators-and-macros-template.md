# Operators and Macros

## Exercise 1: Circle area and circumference
### Problem statement
Use a macro to calculate the area and circumference of a circle.
### Concepts practiced
`#define`, arithmetic operators, and macros.
### Explanation
A macro is a symbol defined by `#define` that replaces text before compilation. Here, we define `PI` as `3.14159` and use it to calculate:
- Area = `PI * r * r`
- Circumference = `2 * PI * r`

This makes the code easier to read and avoids repeating the same constant many times.
### C solution
```c
#include <stdio.h>

#define PI 3.14159

int main() {
    float r, area, circumference;

    printf("Enter the radius: ");
    scanf("%f", &r);

    area = PI * r * r;
    circumference = 2 * PI * r;

    printf("Area = %.2f\n", area);
    printf("Circumference = %.2f\n", circumference);

    return 0;
}
```
### Sample run
```text
Input: radius = 5
Output: Area = 78.54
Circumference = 31.42
```

## Exercise 2: Square and Cube
### Problem statement
Use macros to calculate the square and cube of a number.
### Concepts practiced
Macros and arithmetic operators.
### Explanation
We define two macros:
- `SQUARE(x) = x * x`
- `CUBE(x) = x * x * x`

Then we call these macros with a value and print the results. This demonstrates how macros help simplify repeated computations.
### C solution
```c
#include <stdio.h>

#define SQUARE(x) ((x) * (x))
#define CUBE(x) ((x) * (x) * (x))

int main() {
    int n;

    printf("Enter a number: ");
    scanf("%d", &n);

    printf("Square = %d\n", SQUARE(n));
    printf("Cube = %d\n", CUBE(n));

    return 0;
}
```
### Sample run
```text
Input: 3
Output: Square = 9
Cube = 27
```

## Exercise 3: Even or odd with `%`
### Problem statement
Check whether a number is even or odd using the remainder operator.
### Concepts practiced
Remainder and comparison operators.
### Explanation
The `%` operator gives the remainder after division. When a number is divided by 2:
- If the remainder is 0, the number is even.
- Otherwise, it is odd.

This is a common way to test parity in C.
### C solution
```c
#include <stdio.h>

int main() {
    int num;

    printf("Enter a number: ");
    scanf("%d", &num);

    if (num % 2 == 0) {
        printf("Even\n");
    } else {
        printf("Odd\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 10
Output: Even
```

## Exercise 4: Swap without a temporary variable
### Problem statement
Swap two numbers without using a temporary variable.
### Concepts practiced
Assignment and arithmetic or bitwise operators.
### Explanation
To swap two numbers without a temporary variable, we can use arithmetic:
- `a = a + b`
- `b = a - b`
- `a = a - b`

After these steps, the values are exchanged. This works because the original values are used in the calculation.
### C solution
```c
#include <stdio.h>

int main() {
    int a, b;

    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);

    a = a + b;
    b = a - b;
    a = a - b;

    printf("After swapping: %d %d\n", a, b);

    return 0;
}
```
### Sample run
```text
Input: 2 9
Output: After swapping: 9 2
```
