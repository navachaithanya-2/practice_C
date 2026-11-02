# Recursion and Number Systems

## Exercise 1: Factorial with recursion
### Problem statement
Find the factorial of a number using recursion.
### Concepts practiced
Base cases, recursive calls, and return values.
### Explanation
A recursive function calls itself to solve a smaller version of the same problem. For factorial:
- Base case: if `n == 0` or `n == 1`, return 1
- Recursive case: return `n * factorial(n - 1)`
This continues until the base case is reached.
### C solution
```c
#include <stdio.h>

int factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;
    }
    return n * factorial(n - 1);
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

## Exercise 2: Fibonacci sequence with recursion
### Problem statement
Print the Fibonacci sequence up to `n` terms using recursion.
### Concepts practiced
Recursive calls, base cases, and sequence generation.
### Explanation
The Fibonacci sequence is defined as:
- F(0) = 0
- F(1) = 1
- F(n) = F(n - 1) + F(n - 2) A recursive function computes the next number using the previous two values.
This continues until the base cases are reached.
### C solution
```c
#include <stdio.h>

int fib(int n) {
    if (n == 0) {
        return 0;
    } else if (n == 1) {
        return 1;
    }
    return fib(n - 1) + fib(n - 2);
}

int main() {
    int n, i;

    printf("Enter number of terms: ");
    scanf("%d", &n);

    printf("Fibonacci sequence: ");
    for (i = 0; i < n; i++) {
        printf("%d ", fib(i));
    }
    printf("\n");

    return 0;
}
```
### Sample run
```text
Input: 6
Output: 0 1 1 2 3 5
```

## Exercise 3: Decimal to binary
### Problem statement
Convert a decimal number to binary using recursion.
### Concepts practiced
Division, remainders, recursion, and number systems.
### Explanation
To convert decimal to binary, we repeatedly divide the number by 2 and store the remainder. The recursion prints the remainder after the recursive call, so the output is in the correct order.
### C solution
```c
#include <stdio.h>

void decimalToBinary(int n) {
    if (n == 0) {
        return;
    }
    decimalToBinary(n / 2);
    printf("%d", n % 2);
}

int main() {
    int n;

    printf("Enter a decimal number: ");
    scanf("%d", &n);

    printf("Binary: ");
    decimalToBinary(n);
    printf("\n");

    return 0;
}
```
### Sample run
```text
Input: 10
Output: 1010
```

## Exercise 4: Binary to decimal
### Problem statement
Convert a binary number to decimal using recursion.
### Concepts practiced
Recursion, positional values, and number systems.
### Explanation
Each binary digit has a positional value that doubles as we move left. The recursive function multiplies the current result by 2 and adds the next digit: `result = result * 2 + digit` This continues until all digits are processed.
### C solution
```c
#include <stdio.h>

int binaryToDecimal(char str[], int index) {
    if (str[index] == '\0') {
        return 0;
    }

    return binaryToDecimal(str, index + 1) * 2 + (str[index] - '0');
}

int main() {
    char binary[100];

    printf("Enter a binary number: ");
    scanf("%s", binary);

    printf("Decimal: %d\n", binaryToDecimal(binary, 0));

    return 0;
}
```
### Sample run
```text
Input: 1010
Output: 10
```

## Exercise 5: Hexadecimal to decimal
### Problem statement
Convert a hexadecimal number to decimal using recursion.
### Concepts practiced
Recursion, hexadecimal digits, positional values, and character conversion.
### Explanation
Hexadecimal digits have values from `0` to `15`. For letters `A` to `F`, we convert them to their numeric values:
- A = 10, B = 11, ..., F = 15 Each digit contributes its value multiplied by 16 raised to its position. The recursive function processes the digits from left to right.

### C solution
```c
#include <stdio.h>
#include <string.h>

int hexValue(char ch) {
    if (ch >= '0' && ch <= '9') {
        return ch - '0';
    }
    if (ch >= 'A' && ch <= 'F') {
        return ch - 'A' + 10;
    }
    if (ch >= 'a' && ch <= 'f') {
        return ch - 'a' + 10;
    }
    return 0;
}

int hexToDecimal(char str[], int index, int length) {
    if (index == length) {
        return 0;
    }

    return hexToDecimal(str, index + 1, length) * 16 + hexValue(str[index]);
}

int main() {
    char hex[100];

    printf("Enter a hexadecimal number: ");
    scanf("%s", hex);

    printf("Decimal: %d\n", hexToDecimal(hex, 0, strlen(hex)));

    return 0;
}
```
### Sample run
```text
Input: 1A
Output: 26
```
