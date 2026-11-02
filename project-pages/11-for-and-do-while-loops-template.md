# For and Do-While Loops

## Exercise 1: Print 1 to `n` with `for`
### Problem statement
Print 1 to `n` using a `for` loop.
### Concepts practiced
`for`, counters, and output.
### Explanation
A `for` loop is ideal when the number of iterations is known beforehand. We initialize the counter to 1, set the condition `i <= n`, and increase the counter by 1 after each pass. This prints all numbers from 1 to `n` in order.
### C solution
```c
#include <stdio.h>

int main() {
    int n, i;

    printf("Enter a number: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        printf("%d ", i);
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

## Exercise 2: Factors with `for`
### Problem statement
Print all factors of a number using a `for` loop.
### Concepts practiced
`for`, divisibility, and counters.
### Explanation
To find factors, we test every number from 1 to the given input. If the input is divisible by the current number without a remainder, then it is a factor. The loop checks all possible divisors and prints those that satisfy the condition.
### C solution
```c
#include <stdio.h>

int main() {
    int n, i;

    printf("Enter a number: ");
    scanf("%d", &n);

    printf("Factors: ");

    for (i = 1; i <= n; i++) {
        if (n % i == 0) {
            printf("%d ", i);
        }
    }

    printf("\n");

    return 0;
}
```
### Sample run
```text
Input: 12
Output: 1 2 3 4 6 12
```

## Exercise 3: Perfect number with `for`
### Problem statement
Check whether a number is perfect using a `for` loop.
### Concepts practiced
Divisors, accumulators, and `for`.
### Explanation
A perfect number is one where the sum of all proper divisors equals the number itself. We start the loop from 1 to `n/2`, and whenever a divisor is found, we add it to a `sum`. After the loop, if `sum == n`, the number is perfect; otherwise it is not.
### C solution
```c
#include <stdio.h>

int main() {
    int n, i, sum = 0;

    printf("Enter a number: ");
    scanf("%d", &n);

    for (i = 1; i <= n / 2; i++) {
        if (n % i == 0) {
            sum += i;
        }
    }

    if (sum == n) {
        printf("Perfect number\n");
    } else {
        printf("Not a perfect number\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 28
Output: Perfect number
```

## Exercise 4: Odd numbers with `do...while`
### Problem statement
Print odd numbers from 1 to `n` using a `do...while` loop.
### Concepts practiced
`do...while`, counters, and odd-number checks.
### Explanation
A `do...while` loop executes the body at least once before checking the condition. We start with `i = 1`, print it if it is odd, and then increase it by 1. The loop continues until `i > n`.
### C solution
```c
#include <stdio.h>

int main() {
    int n, i = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    do {
        if (i % 2 != 0) {
            printf("%d ", i);
        }
        i++;
    } while (i <= n);

    printf("\n");

    return 0;
}
```
### Sample run
```text
Input: 7
Output: 1 3 5 7
```

## Exercise 5: Reverse with `do...while`
### Problem statement
Print the reverse of an integer using a `do...while` loop.
### Concepts practiced
Digit extraction, integer division, and `do...while`.
### Explanation
We repeatedly extract the last digit using `% 10`, append it to the reverse number, and remove the last digit using `/ 10`. The loop runs until the original number becomes 0. A `do...while` is useful here because the process must execute at least once for any non-zero number.
### C solution
```c
#include <stdio.h>

int main() {
    int n, reverse = 0, digit;

    printf("Enter a number: ");
    scanf("%d", &n);

    do {
        digit = n % 10;
        reverse = reverse * 10 + digit;
        n = n / 10;
    } while (n != 0);

    printf("Reverse = %d\n", reverse);

    return 0;
}
```
### Sample run
```text
Input: 1234
Output: 4321
```
