# Switch Statements

## Exercise 1: Divisible by 3 and 5
### Problem statement
Check whether a number is divisible by both 3 and 5.
### Concepts practiced
`switch`, `case`, divisibility, and validation.
### Explanation
A number is divisible by both 3 and 5 if it is divisible by 15. The simplest way is to check the remainder using `%`:
- If `n % 3 == 0` and `n % 5 == 0`, then it is divisible by both.
This exercise can also be extended using `switch` to select cases based on input ranges or conditions, but the core logic is based on divisibility checks.
### C solution
```c
#include <stdio.h>

int main() {
    int n;

    printf("Enter a number: ");
    scanf("%d", &n);

    if (n % 3 == 0 && n % 5 == 0) {
        printf("Divisible by both 3 and 5\n");
    } else {
        printf("Not divisible by both 3 and 5\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 30
Output: Divisible by both 3 and 5
```

## Exercise 2: Perfect square
### Problem statement
Check whether an entered number is a perfect square.
### Concepts practiced
Integer checks, loops, and `switch`-based decisions where appropriate.
### Explanation
A perfect square is a number that can be written as the square of an integer. We can test this by checking all numbers from 1 up to `sqrt(n)`. If any value squared equals `n`, then it is a perfect square. This uses loop-based checking and comparison.### C solution
```c
#include <stdio.h>
#include <math.h>

int main() {
    int n, i;

    printf("Enter a number: ");
    scanf("%d", &n);

    if (n < 0) {
        printf("Not a perfect square\n");
        return 0;
    }

    for (i = 0; i <= sqrt(n); i++) {
        if (i * i == n) {
            printf("Perfect square\n");
            return 0;
        }
    }

    printf("Not a perfect square\n");
    return 0;
}
```
### Sample run
```text
Input: 49
Output: Perfect square
```

## Exercise 3: Season for a month
### Problem statement
Display the season for a month: winter (December-February), summer (March-May), monsoon (June-September), or autumn (October-November).
### Concepts practiced
Grouped `case` labels, `switch`, and validation.
### Explanation
The month number is read from the user. Then we use a `switch` statement with grouped cases:
- 12, 1, 2 → Winter
- 3, 4, 5 → Summer
- 6, 7, 8, 9 → Monsoon
- 10, 11 → Autumn If the month is invalid, we print an error message.
### C solution
```c
#include <stdio.h>

int main() {
    int month;

    printf("Enter month number: ");
    scanf("%d", &month);

    switch (month) {
        case 12:
        case 1:
        case 2:
            printf("Winter\n");
            break;

        case 3:
        case 4:
        case 5:
            printf("Summer\n");
            break;

        case 6:
        case 7:
        case 8:
        case 9:
            printf("Monsoon\n");
            break;

        case 10:
        case 11:
            printf("Autumn\n");
            break;

        default:
            printf("Invalid month number\n");
            break;
    }

    return 0;
}
```
### Sample run
```text
Input: 7
Output: Monsoon
```

## Exercise 4: Menu-driven area calculator
### Problem statement
Create a menu-driven area calculator for a circle, square, rectangle, and triangle using `switch`.
### Concepts practiced
Menus, `switch`, arithmetic, and input validation.
### Explanation
The user chooses a shape from a menu. Based on the selected option, the program reads the required dimensions and calculates the area. The `switch` statement is used to decide which formula to apply:
- Circle: `πr²`
- Square: `side²`
- Rectangle: `length * breadth`
- Triangle: `(base * height) / 2`
If the choice is invalid, we print a message.
### C solution
```c
#include <stdio.h>
#define PI 3.14159

int main() {
    int choice;
    float r, side, length, breadth, base, height, area;

    printf("Menu:\n");
    printf("1. Circle\n");
    printf("2. Square\n");
    printf("3. Rectangle\n");
    printf("4. Triangle\n");
    printf("Enter your choice: ");
    scanf("%d", &choice);

    switch (choice) {
        case 1:
            printf("Enter radius: ");
            scanf("%f", &r);
            area = PI * r * r;
            printf("Area of circle = %.2f\n", area);
            break;

        case 2:
            printf("Enter side: ");
            scanf("%f", &side);
            area = side * side;
            printf("Area of square = %.2f\n", area);
            break;

        case 3:
            printf("Enter length and breadth: ");
            scanf("%f %f", &length, &breadth);
            area = length * breadth;
            printf("Area of rectangle = %.2f\n", area);
            break;

        case 4:
            printf("Enter base and height: ");
            scanf("%f %f", &base, &height);
            area = 0.5 * base * height;
            printf("Area of triangle = %.2f\n", area);
            break;

        default:
            printf("Invalid choice\n");
            break;
    }

    return 0;
}
```
### Sample run
```text
Input: choice and dimensions
Output: selected shape's area
```
