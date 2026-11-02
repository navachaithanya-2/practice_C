# Functions

## Exercise 1: Power function
### Problem statement
Calculate the power of a number using a function.
### Concepts practiced
Function declaration, parameters, return values, and loops.
### Explanation
A function helps us reuse code. Here, we create a function `power(base, exponent)` that multiplies the base by itself `exponent` times. The function takes two parameters and returns the result. This makes the program cleaner and easier to understand.
### C solution
```c
#include <stdio.h>

int power(int base, int exponent) {
    int result = 1;
    for (int i = 1; i <= exponent; i++) {
        result *= base;
    }
    return result;
}

int main() {
    int base, exponent;

    printf("Enter base and exponent: ");
    scanf("%d %d", &base, &exponent);

    printf("Result: %d\n", power(base, exponent));

    return 0;
}
```
### Sample run
```text
Input: 2 5
Output: 32
```

## Exercise 2: Factorial function
### Problem statement
Calculate the factorial of a number using a function.
### Concepts practiced
Functions, loops, and return values.
### Explanation
The factorial of a number `n` is the product of all positive integers from `1` to `n`. We create a function `factorial(n)` that multiplies the values in a loop and returns the result. For example, `5! = 5 * 4 * 3 * 2 * 1 = 120`.
### C solution
```c
#include <stdio.h>

int factorial(int n) {
    int result = 1;

    for (int i = 1; i <= n; i++) {
        result *= i;
    }

    return result;
}

int main() {
    int n;

    printf("Enter a number: ");
    scanf("%d", &n);

    printf("Factorial = %d\n", factorial(n));

    return 0;
}
```
### Sample run
```text
Input: 5
Output: 120
```

## Exercise 3: Prime-check function
### Problem statement
Check whether a number is prime using a function.
### Concepts practiced
Functions, divisors, and Boolean-style return values.
### Explanation
A prime number is greater than 1 and has no divisors other than 1 and itself. We write a function `isPrime(n)` that checks divisibility from 2 to `sqrt(n)`. It returns `1` if the number is prime and `0` otherwise.
### C solution
```c
#include <stdio.h>
#include <math.h>

int isPrime(int n) {
    if (n <= 1) {
        return 0;
    }

    for (int i = 2; i <= sqrt(n); i++) {
        if (n % i == 0) {
            return 0;
        }
    }

    return 1;
}

int main() {
    int n;

    printf("Enter a number: ");
    scanf("%d", &n);

    if (isPrime(n)) {
        printf("Prime\n");
    } else {
        printf("Not Prime\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 13
Output: Prime
```

## Exercise 4: Swap function
### Problem statement
Swap two values using a function.
### Concepts practiced
Function parameters, addresses, and pointers.
### Explanation
When a function receives normal variables, it gets copies of the values, not the original variables. To change the original values in the caller, we pass their addresses using pointers. The function `swap(a, b)` receives pointers and swaps the values stored at those memory locations.
### C solution
```c
#include <stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x = 2, y = 9;

    printf("Before swap: %d %d\n", x, y);

    swap(&x, &y);

    printf("After swap: %d %d\n", x, y);

    return 0;
}
```
### Sample run
```text
Input: 2 9
Output:
Before swap: 2 9
After swap: 9 2
```
