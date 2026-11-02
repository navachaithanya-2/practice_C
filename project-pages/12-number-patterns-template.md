# Number Patterns

## Exercise: Print five patterns
### Problem statement
Print the five patterns shown below using nested loops:
```text
*****       12345       *****       12345       1
****        1234        ****        1234        12
***         123         ***         123         123
**          12          **          12          1234
*           1           *           1           12345
```
### Concepts practiced
Nested loops, row/column thinking, and formatted output.
### Explanation
A nested loop means one loop inside another. The outer loop controls the number of rows, and the inner loop controls the number of symbols or digits printed in each row. For each row:
- Pattern 1: print stars decreasing from 5 to 1
- Pattern 2: print numbers increasing from 1 to 5 in each row, but the row length decreases
- Pattern 3: print stars decreasing from 5 to 1
- Pattern 4: print numbers increasing in each row, but the row length decreases
- Pattern 5: print numbers increasing from 1 to row number, making a triangular pattern The inner loop prints the content of each row, while the outer loop moves to the next row.
### C solution
```c
#include <stdio.h>

int main() {
    int i, j;

    printf("Pattern 1:\n");
    for (i = 5; i >= 1; i--) {
        for (j = 1; j <= i; j++) {
            printf("*");
        }
        printf("\n");
    }

    printf("\nPattern 2:\n");
    for (i = 1; i <= 5; i++) {
        for (j = 1; j <= 6 - i; j++) {
            printf("%d", j);
        }
        printf("\n");
    }

    printf("\nPattern 3:\n");
    for (i = 5; i >= 1; i--) {
        for (j = 1; j <= i; j++) {
            printf("*");
        }
        printf("\n");
    }

    printf("\nPattern 4:\n");
    for (i = 1; i <= 5; i++) {
        for (j = 1; j <= 6 - i; j++) {
            printf("%d", j);
        }
        printf("\n");
    }

    printf("\nPattern 5:\n");
    for (i = 1; i <= 5; i++) {
        for (j = 1; j <= i; j++) {
            printf("%d", j);
        }
        printf("\n");
    }

    return 0;
}
```
### Sample run
```text
Input: No input
Output:
*****       12345       *****       12345       1
****        1234        ****        1234        12
***         123         ***         123         123
**          12          **          12          1234
*           1           *           1           12345
```
