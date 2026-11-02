# Comparing Numbers

## Exercise 1: Find the larger of two numbers
### Problem statement
Read two numbers and display the larger number, handling equal values clearly.
### Concepts practiced
Input, comparison operators, and conditional statements.
### Explanation
To compare two numbers, we first read both values using `scanf()`. Then we check whether the first number is greater than the second. If it is, we print the first number. Otherwise, if the second number is larger, we print the second number. If both numbers are equal, we print a message saying they are equal. This uses comparison operators such as `>` and `==`.
### C solution
```c
#include <stdio.h>

int main() {
    int a, b;

    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);

    if (a > b) {
        printf("Larger number: %d\n", a);
    } else if (b > a) {
        printf("Larger number: %d\n", b);
    } else {
        printf("Both numbers are equal.\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 8 5
Output: 8
```

## Exercise 2: Find the largest of three numbers
### Problem statement
Read three numbers and display the largest number, handling ties clearly.
### Concepts practiced
Multiple comparisons and conditional statements.
### Explanation
We read three integer values and compare them step by step. First, we assume the first value is the largest. Then we compare it with the second and third values. If the second value is greater than the current largest, we update the largest. We do the same with the third value. At the end, we print the largest number. If two or more numbers are equal, we can handle that separately by printing a message such as "Tie".
### C solution
```c
#include <stdio.h>

int main() {
    int a, b, c;
    int largest;

    printf("Enter three numbers: ");
    scanf("%d %d %d", &a, &b, &c);

    largest = a;

    if (b > largest) {
        largest = b;
    }

    if (c > largest) {
        largest = c;
    }

    printf("Largest number: %d\n", largest);

    return 0;
}
```
### Sample run
```text
Input: 4 12 7
Output: 12
```
