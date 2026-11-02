# More While Loops

## Exercise 1: Sum five numbers
### Problem statement
Read five numbers and calculate their sum using a `while` loop.
### Concepts practiced
Counters, accumulators, input, and `while`.
### Explanation
We use a loop that runs exactly five times. Each time, we read one number and add it to a running total variable. The total is updated inside the loop using `sum += num;`. After the loop finishes, the final value of `sum` is printed.
### C solution
```c
#include <stdio.h>

int main() {
    int i = 1, num, sum = 0;

    while (i <= 5) {
        printf("Enter number %d: ", i);
        scanf("%d", &num);

        sum += num;
        i++;
    }

    printf("Sum = %d\n", sum);

    return 0;
}
```
### Sample run
```text
Input: 1 2 3 4 5
Output: 15
```

## Exercise 2: Print factors
### Problem statement
Print all factors of a number using a `while` loop.
### Concepts practiced
Divisibility, counters, and `while`.
### Explanation
A factor of a number divides that number exactly without leaving a remainder. We loop from 1 to the number itself. If `number % i == 0`, then `i` is a factor and we print it. This continues until the loop reaches the number.
### C solution
```c
#include <stdio.h>

int main() {
    int n, i = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    printf("Factors: ");

    while (i <= n) {
        if (n % i == 0) {
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
Input: 12
Output: 1 2 3 4 6 12
```

## Exercise 3: Reverse an integer
### Problem statement
Print the reverse of an integer using a `while` loop.
### Concepts practiced
Remainder, integer division, and digit extraction.
### Explanation
To reverse a number, we repeatedly take the last digit using `% 10` and then remove it from the original number using `n = n / 10`. Each digit is added to a reverse variable as: `reverse = reverse * 10 + lastDigit` This continues until the original number becomes zero.
### C solution
```c
#include <stdio.h>

int main() {
    int n, reverse = 0, digit;

    printf("Enter a number: ");
    scanf("%d", &n);

    while (n > 0) {
        digit = n % 10;
        reverse = reverse * 10 + digit;
        n = n / 10;
    }

    printf("Reverse = %d\n", reverse);

    return 0;
}
```
### Sample run
```text
Input: 1234
Output: 4321
```
