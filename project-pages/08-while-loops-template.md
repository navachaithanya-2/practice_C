# While Loops

## Exercise 1: Print 1 to `n`
### Problem statement
Print the numbers from 1 to `n` using a `while` loop.
### Concepts practiced
`while`, counters, and formatted output.
### Explanation
A `while` loop repeats as long as a condition is true. Here, we start with `i = 1` and keep printing while `i <= n`. After each print, we increase `i` by 1. This ensures the loop stops after reaching `n`.
### C solution
```c
#include <stdio.h>

int main() {
    int n, i = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    while (i <= n) {
        printf("%d ", i);
        i++;
    }

    printf("\n");

    return 0;
}
```
### Sample run
```text
Input: 5
Output: 1 2 3 4 5
```

## Exercise 2: Print odd numbers
### Problem statement
Print the odd numbers from 1 to `n` using a `while` loop.
### Concepts practiced
`while`, incrementing, and odd-number checks.
### Explanation
We start from `i = 1` and continue until `i <= n`. In each iteration, we check whether `i` is odd using `i % 2 != 0`. If it is odd, we print it. Then we increase `i` by 1. This prints only the odd numbers.
### C solution
```c
#include <stdio.h>

int main() {
    int n, i = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    while (i <= n) {
        if (i % 2 != 0) {
            printf("%d ", i);
        }
        i++;
    }

    printf("\n");

    return 0;
}
```
### Sample run
```text
Input: 7
Output: 1 3 5 7
```

## Exercise 3: Multiplication table
### Problem statement
Print the multiplication table of a number using a `while` loop.
### Concepts practiced
`while`, counters, and multiplication.
### Explanation
The loop starts with `i = 1` and continues until `i <= 10`. In each iteration, we multiply the chosen number by `i` and print the result. This generates the multiplication table for that number.
### C solution
```c
#include <stdio.h>

int main() {
    int num, i = 1;

    printf("Enter a number: ");
    scanf("%d", &num);

    while (i <= 10) {
        printf("%d x %d = %d\n", num, i, num * i);
        i++;
    }

    return 0;
}
```
### Sample run
```text
Input: 3
Output:
3 x 1 = 3
3 x 2 = 6
3 x 3 = 9
...
```
