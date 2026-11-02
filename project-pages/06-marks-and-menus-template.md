# Marks and Menus

## Exercise 1: Marks and class
### Problem statement
Read five subject marks, calculate the percentage, and assign a class: Fail below 35%, Pass from 35% to below 45%, Second Class from 45% to below 60%, First Class from 60% to 70%, and Distinction above 70%. Treat exactly 70% as First Class.
### Concepts practiced
Percentage calculation, range checks, and conditional statements.
### Explanation
We first read five subject marks and calculate the total. Then we compute the percentage using:
percentage = (total / 500) * 100
After that, we use `if` and `else if` statements to determine the class:
- Below 35% → Fail
- 35% to below 45% → Pass
- 45% to below 60% → Second Class
- 60% to 70% → First Class
- Above 70% → Distinction
The boundary conditions are checked carefully so values like exactly 35, 45, 60, and 70 fall in the correct class.
### C solution
```c
#include <stdio.h>

int main() {
    int m1, m2, m3, m4, m5;
    float total, percentage;

    printf("Enter five marks: ");
    scanf("%d %d %d %d %d", &m1, &m2, &m3, &m4, &m5);

    total = m1 + m2 + m3 + m4 + m5;
    percentage = (total / 500.0) * 100;

    printf("Percentage = %.2f%%\n", percentage);

    if (percentage < 35) {
        printf("Class: Fail\n");
    } else if (percentage >= 35 && percentage < 45) {
        printf("Class: Pass\n");
    } else if (percentage >= 45 && percentage < 60) {
        printf("Class: Second Class\n");
    } else if (percentage >= 60 && percentage <= 70) {
        printf("Class: First Class\n");
    } else {
        printf("Class: Distinction\n");
    }

    return 0;
}
```
### Sample run
```text
Input: five marks
Output: percentage and class
```

## Exercise 2: Largest with conditional operator
### Problem statement
Find the largest of three numbers using the conditional operator.
### Concepts practiced
Conditional operator and comparisons.
### Explanation
The conditional operator `?:` is a compact form of `if-else`. We compare the numbers and assign the largest one to a variable. For example: `largest = (a > b) ? ((a > c) ? a : c) : ((b > c) ? b : c);` This means:
- If `a` is greater than `b`, compare a with `c`.
- Otherwise, compare `b` with `c`. This reduces long nested `if` statements into a short expression.
### C solution
```c
#include <stdio.h>

int main() {
    int a, b, c, largest;

    printf("Enter three numbers: ");
    scanf("%d %d %d", &a, &b, &c);

    largest = (a > b) ? ((a > c) ? a : c) : ((b > c) ? b : c);

    printf("Largest number: %d\n", largest);

    return 0;
}
```
### Sample run
```text
Input: 4 12 7
Output: Largest number: 12
```

## Exercise 3: Days in a month
### Problem statement
Print the number of days in a month. Reject invalid month numbers; treat February as having 28 days.
### Concepts practiced
Range checks, grouped cases, and validation.
### Explanation
The program reads a month number. If the number is outside the range 1 to 12, it prints an error message. Otherwise, it checks the month:
- 1,3,5,7,8,10,12 → 31 days
- 4,6,9,11 → 30 days
- 2 → 28 days This uses `if` and `else if` conditions or a `switch` statement to handle month groups.
### C solution
```c
#include <stdio.h>

int main() {
    int month;

    printf("Enter month number: ");
    scanf("%d", &month);

    if (month < 1 || month > 12) {
        printf("Invalid month number.\n");
    } else if (month == 2) {
        printf("28 days\n");
    } else if (month == 4 || month == 6 || month == 9 || month == 11) {
        printf("30 days\n");
    } else {
        printf("31 days\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 2
Output: 28 days
```
