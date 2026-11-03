# Advanced Functions

## Exercise 1: Simple interest
### Problem statement
Calculate simple interest using a function.
### Concepts practiced
Functions, parameters, return values, and arithmetic.
### Explanation
Simple interest is calculated using the formula:
`SI = (P * R * T) / 100`
where `P` is the principal amount, `R` is the rate of interest, and `T` is the time period. We define a function `simpleInterest(principal, rate, time)` that takes these values as parameters and returns the interest.
### C solution
```c
#include <stdio.h>

float simpleInterest(float principal, float rate, float time) {
    return (principal * rate * time) / 100.0;
}

int main() {
    float principal, rate, time;

    printf("Enter principal, rate, and time: ");
    scanf("%f %f %f", &principal, &rate, &time);

    printf("Simple Interest = %.2f\n", simpleInterest(principal, rate, time));

    return 0;
}
```
### Sample run
```text
Input: 10000 5 4
Output: 2000
```

## Exercise 2: Add two numbers
### Problem statement
Define a function that adds two numbers.
### Concepts practiced
Function definition, arguments, and return values.
### Explanation
We define a function `add(a, b)` that accepts two integers and returns their sum. This demonstrates the use of parameters and the return statement. The function is called from `main()`, and the result is printed.
### C solution
```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int x, y;

    printf("Enter two numbers: ");
    scanf("%d %d", &x, &y);

    printf("Sum = %d\n", add(x, y));

    return 0;
}
```
### Sample run
```text
Input: 4 6
Output: 10
```

## Exercise 3: Global and static local variables
### Problem statement
Demonstrate the difference between a global variable and a static local variable.
### Concepts practiced
Scope, lifetime, global variables, and `static` local variables.
### Explanation
A global variable is declared outside any function and can be accessed by all functions. A static local variable is declared inside a function but keeps its value between function calls. This shows that a static variable has local scope but a longer lifetime.
### C solution
```c
#include <stdio.h>

int globalVar = 10;

void demo() {
    static int staticVar = 0;

    printf("Global = %d, Static Local = %d\n", globalVar, staticVar);
    globalVar++;
    staticVar++;
}

int main() {
    demo();
    demo();
    demo();

    return 0;
}
```
### Sample run
```text
Input: Function called repeatedly
Output: Values showing scope and lifetime
```

## Exercise 4: Lowercase string to uppercase
### Problem statement
Write a function that converts a string argument from lowercase to uppercase.
### Concepts practiced
Strings, character operations, arrays, and function arguments.
### Explanation
We pass a character array to a function. The function loops through each character and checks whether it is between `'a'` and `'z'`. If so, it converts it to uppercase by subtracting 32 from the ASCII value. The modified string is printed in `main()`.
### C solution
```c
#include <stdio.h>

void toUpperCase(char str[]) {
    int i = 0;

    while (str[i] != '\0') {
        if (str[i] >= 'a' && str[i] <= 'z') {
            str[i] = str[i] - 32;
        }
        i++;
    }
}

int main() {
    char str[100];

    printf("Enter a lowercase string: ");
    scanf("%s", str);

    toUpperCase(str);

    printf("Uppercase: %s\n", str);

    return 0;
}
```
### Sample run
```text
Input: hello
Output: HELLO
```

## Exercise 5: Calculate `nCr`
### Problem statement
Calculate `nCr = n! / (r! * (n-r)!)` using user-defined functions.
### Concepts practiced
Function composition, factorials, and integer arithmetic.
### Explanation
We define a `factorial(n)` function to compute factorial values. Then we compute: `nCr = factorial(n) / (factorial(r) * factorial(n-r))` The values of `n` and `r` must satisfy `n >= r >= 0`, otherwise the result is invalid.
### C solution
```c
#include <stdio.h>

int factorial(int n) {
    int result = 1;

    for (int i = 1; i <= n; i++) {
        result *= i;
    }

    return result;
}

int main() {
    int n, r;

    printf("Enter n and r: ");
    scanf("%d %d", &n, &r);

    if (n >= r && r >= 0) {
        printf("nCr = %d\n", factorial(n) / (factorial(r) * factorial(n - r)));
    } else {
        printf("Invalid input\n");
    }

    return 0;
}
```
### Sample run
```text
Input: 5 2
Output: 10
```

## Exercise 6: GCD function
### Problem statement
Write a function that accepts two numbers and returns their GCD.
### Concepts practiced
Function parameters, return values, and the Euclidean algorithm.
### Explanation
The Euclidean algorithm repeatedly replaces the larger number with the remainder of division. For example: `gcd(a, b) = gcd(b, a % b)` This continues until the remainder becomes zero. The value of `b` at that point is the GCD.
### C solution
```c
#include <stdio.h>

int gcd(int a, int b) {
    while (b != 0) {
        int temp = a % b;
        a = b;
        b = temp;
    }
    return a;
}

int main() {
    int a, b;

    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);

    printf("GCD = %d\n", gcd(a, b));

    return 0;
}
```
### Sample run
```text
Input: 18 24
Output: 6
```
