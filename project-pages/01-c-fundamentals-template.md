# C Fundamentals

## Exercise 1: Print `Hello, World!`
### Problem statement
Write a C program that prints `Hello, World!`.
### Concepts practiced
`main`, `printf`, and standard output.
### Explanation
The program starts with `#include <stdio.h>`, which allows us to use the `printf()` function. The `main()` function is the entry point of the program. Inside it, `printf("Hello, World!\n");` prints the message to the screen. The `\n` moves the cursor to the next line. The `return 0;` statement ends the program successfully.
### C solution
```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```
### Sample run
```text
Input: No input
Output: Hello, World!
```

## Exercise 2: Check the sign of an integer
### Problem statement
Read an integer and determine whether it is positive, negative, or zero.
### Concepts practiced
`scanf`, variables, comparisons, and conditional statements.
### Explanation
First, we declare an integer variable named num. Then we use scanf("%d", &num); to read the value entered by the user. After that, we check the value:

    If num > 0, it is positive.
    Else if num < 0, it is negative.
    Otherwise, it is zero. We use if, else if, and else statements to make these decisions.

### C solution
```c
#include <stdio.h>

int main() {
    int num;

    printf("Enter an integer: ");
    scanf("%d", &num);

    if (num > 0) {
        printf("Positive\n");
    } else if (num < 0) {
        printf("Negative\n");
    } else {
        printf("Zero\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 12
Output: Positive
```

## Exercise 3: Check even or odd
### Problem statement
Read an integer and determine whether it is even or odd.
### Concepts practiced
`scanf`, `%`, and conditional statements.
### Explanation
We read an integer using scanf("%d", &num);. Then we use the modulo operator % to find the remainder when the number is divided by 2. If the remainder is 0, the number is even; otherwise, it is odd. This is checked with an if condition.
### C solution
```c
#include <stdio.h>

int main() {
    int num;

    printf("Enter an integer: ");
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
Input: 7
Output: Odd
```
