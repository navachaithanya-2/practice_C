# Decision Making

## Exercise 1: Vowel or consonant
### Problem statement
Check whether an entered character is a vowel or a consonant.
### Concepts practiced
`if`, `else if`, character comparisons, and input validation.
### Explanation
The program reads a character from the user. Then it checks whether the character is one of the vowels: `a`, `e`, `i`, `o`, or `u`. This check is done using `if` and `else if` conditions. If the character is a vowel, we print `Vowel`; otherwise, we print `Consonant`. We can also convert the input to lowercase before checking, so both uppercase and lowercase letters work.
### C solution
```c
#include <stdio.h>

int main() {
    char ch;

    printf("Enter a character: ");
    scanf("%c", &ch);

    if (ch >= 'A' && ch <= 'Z') {
        ch = ch + 32;
    }

    if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
        printf("Vowel\n");
    } else {
        printf("Consonant\n");
    }

    return 0;
}
```
### Sample run
```text
Input: e
Output: Vowel
```

## Exercise 2: Calculator
### Problem statement
Build a calculator for addition, subtraction, multiplication, and division based on the user's choice. Implement it with an `if...else` ladder and with nested `if` statements.
### Concepts practiced
Conditional ladders, nested conditions, operators, and division validation.
### Explanation
We take two numbers and an operator from the user. Then we use `if...else if` statements to decide which operation to perform:
- `+` for addition
- `-` for subtraction
- `*` for multiplication
- `/` for division
We also check whether the divisor is zero before division, because dividing by zero is invalid. This can also be written using nested `if` statements instead of a ladder.
### C solution
```c
#include <stdio.h>

int main() {
    float a, b, result;
    char op;

    printf("Enter first number: ");
    scanf("%f", &a);

    printf("Enter operator (+, -, *, /): ");
    scanf(" %c", &op);

    printf("Enter second number: ");
    scanf("%f", &b);

    if (op == '+') {
        result = a + b;
        printf("Result: %.2f\n", result);
    } else if (op == '-') {
        result = a - b;
        printf("Result: %.2f\n", result);
    } else if (op == '*') {
        result = a * b;
        printf("Result: %.2f\n", result);
    } else if (op == '/') {
        if (b == 0) {
            printf("Error: Division by zero is not allowed.\n");
        } else {
            result = a / b;
            printf("Result: %.2f\n", result);
        }
    } else {
        printf("Invalid operator.\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 8 / 2
Output: 4
```
