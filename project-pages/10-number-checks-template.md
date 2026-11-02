# Number Checks

## Exercise 1: Perfect number
### Problem statement
Check whether a number is a perfect number.
### Concepts practiced
Divisors, accumulators, and loop limits.
### Explanation
A perfect number is a number whose sum of proper divisors equals the number itself. For example, 6 has divisors 1, 2, and 3, and 1 + 2 + 3 = 6. To check this, we loop from 1 to `n/2`, and whenever a number divides `n` evenly, we add it to a sum. After the loop, if the sum equals `n`, the number is perfect; otherwise, it is not.
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
Input: 6
Output: Perfect number
```

## Exercise 2: Prime number
### Problem statement
Check whether a number is prime.
### Concepts practiced
Divisors, counters, and efficient loop limits.
### Explanation
A prime number is greater than 1 and has no divisors other than 1 and itself. We check divisibility from 2 to `sqrt(n)`. If `n` is divisible by any value in that range, it is not prime. Otherwise, it is prime. This is efficient because we do not check beyond the square root.
### C solution
```c
#include <stdio.h>
#include <math.h>

int main() {
    int n, i;
    int isPrime = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    if (n <= 1) {
        isPrime = 0;
    } else {
        for (i = 2; i <= sqrt(n); i++) {
            if (n % i == 0) {
                isPrime = 0;
                break;
            }
        }
    }

    if (isPrime) {
        printf("Prime number\n");
    } else {
        printf("Not a prime number\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 13
Output: Prime number
```
