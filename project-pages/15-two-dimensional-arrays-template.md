# Two-Dimensional Arrays

## Exercise 1: Integer palindrome
### Problem statement
Check whether an integer is a palindrome.
### Concepts practiced
Digit extraction, reverse construction, and comparisons.
### Explanation
A palindrome reads the same forward and backward. To check this, we take the number digit by digit and build its reverse. For example, if the input is 1221, the reverse is also 1221. We compare the original number with the reversed number. If they are equal, the number is a palindrome; otherwise, it is not.
### C solution
```c
#include <stdio.h>

int main() {
    int n, original, reverse = 0, digit;

    printf("Enter a number: ");
    scanf("%d", &n);

    original = n;

    while (n > 0) {
        digit = n % 10;
        reverse = reverse * 10 + digit;
        n = n / 10;
    }

    if (original == reverse) {
        printf("Palindrome\n");
    } else {
        printf("Not a palindrome\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 1221
Output: Palindrome
```

## Exercise 2: Count values in a 2D array
### Problem statement
Count positive, negative, and zero elements in a two-dimensional array.
### Concepts practiced
2D arrays, nested loops, and counters.
### Explanation
A two-dimensional array is stored in rows and columns. We use two nested loops: one for rows and one for columns. For each element, we check whether it is:
- greater than 0 → positive
- less than 0 → negative
- equal to 0 → zero

We increase the matching counter for each case.
### C solution
```c
#include <stdio.h>

int main() {
    int a[3][3];
    int i, j, positive = 0, negative = 0, zero = 0;

    printf("Enter 9 elements:\n");
    for (i = 0; i < 3; i++) {
        for (j = 0; j < 3; j++) {
            scanf("%d", &a[i][j]);
        }
    }

    for (i = 0; i < 3; i++) {
        for (j = 0; j < 3; j++) {
            if (a[i][j] > 0) {
                positive++;
            } else if (a[i][j] < 0) {
                negative++;
            } else {
                zero++;
            }
        }
    }

    printf("Positive = %d\n", positive);
    printf("Negative = %d\n", negative);
    printf("Zero = %d\n", zero);

    return 0;
}
```
### Sample run
```text
Input: 8 -5 2 2 0 -4 -2 1 -3
Output: Positive = 4
Negative = 4
Zero = 1
```

## Exercise 3: Add two matrices
### Problem statement
Add two matrices when their dimensions are compatible.
### Concepts practiced
2D arrays, nested loops, and dimension checks.
### Explanation
Two matrices can be added only if they have the same number of rows and columns. We use nested loops to access every corresponding element and add them: `result[i][j] = a[i][j] + b[i][j]` The result is stored in a third matrix.
### C solution
```c
#include <stdio.h>

int main() {
    int a[2][2], b[2][2], sum[2][2];
    int i, j;

    printf("Enter first matrix (2x2):\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            scanf("%d", &a[i][j]);
        }
    }

    printf("Enter second matrix (2x2):\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            scanf("%d", &b[i][j]);
        }
    }

    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            sum[i][j] = a[i][j] + b[i][j];
        }
    }

    printf("Sum of matrices:\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            printf("%d ", sum[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 9 3 0 4
8 -1 0 -4
Output: 17 2 0 0
```

## Exercise 4: Multiply two matrices
### Problem statement
Multiply two matrices when their dimensions are compatible.
### Concepts practiced
2D arrays, nested loops, and matrix dimension checks.
### Explanation
Matrix multiplication requires the number of columns of the first matrix to equal the number of rows of the second matrix. We use three nested loops:
- outer loop for rows of the result matrix
- middle loop for columns of the second matrix
- inner loop to multiply and sum the matching elements

For each result position: `result[i][j] += a[i][k] * b[k][j]`
### C solution
```c
#include <stdio.h>

int main() {
    int a[2][2], b[2][2], product[2][2];
    int i, j, k;

    printf("Enter first matrix (2x2):\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            scanf("%d", &a[i][j]);
        }
    }

    printf("Enter second matrix (2x2):\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            scanf("%d", &b[i][j]);
        }
    }

    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            product[i][j] = 0;
            for (k = 0; k < 2; k++) {
                product[i][j] += a[i][k] * b[k][j];
            }
        }
    }

    printf("Product of matrices:\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            printf("%d ", product[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 1 -2 3 4
1 0 2 1
Output: -3 -2 11 4
```
