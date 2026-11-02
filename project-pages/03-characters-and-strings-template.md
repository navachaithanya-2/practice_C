# Characters and Strings

## Exercise 1: Read and print a character
### Problem statement
Read and print one character using `getchar()` and `putchar()`.
### Concepts practiced
Characters, `getchar()`, and `putchar()`.
### Explanation
This program reads one character from the keyboard using `getchar()`. The character is stored in a variable of type `char`. Then `putchar()` prints the same character to the screen. This is useful when working with single characters instead of full strings.### C solution
```c
#include <stdio.h>

int main() {
    char ch;

    printf("Enter a character: ");
    ch = getchar();

    printf("You entered: ");
    putchar(ch);
    printf("\n");

    return 0;
}
```

### Sample run
```text
Input: A
Output: A
```

## Exercise 2: Read and print a string
### Problem statement
Read and print a string using `fgets()` and `puts()`.
### Concepts practiced
Character arrays, `fgets()`, `puts()`, and safe line input.
### Explanation
A string in C is stored as an array of characters. We declare a character array like `char str[100];`. The `fgets()` function reads a line of text safely from input and stores it in the array. `puts()` prints the string to the output screen. This is a safe way to read text with spaces.
```c
#include <stdio.h>

int main() {
    char str[100];

    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);

    printf("You entered: ");
    puts(str);

    return 0;
}
```
### Sample run
```text
Input: Hello C
Output: Hello C
```

## Exercise 3: Convert lowercase to uppercase
### Problem statement
Convert a lowercase character to uppercase using character operations.
### Concepts practiced
Character codes and character arithmetic.
### Explanation
In C, each character has an ASCII value. Lowercase letters and uppercase letters differ by a fixed value: `'a' - 'A' = 32`. So to convert a lowercase letter to uppercase, we subtract 32 from its ASCII value. This works for lowercase letters `a` to `z`.
```c
#include <stdio.h>

int main() {
    char ch;

    printf("Enter a lowercase letter: ");
    scanf("%c", &ch);

    if (ch >= 'a' && ch <= 'z') {
        ch = ch - 32;
    }

    printf("Uppercase: %c\n", ch);

    return 0;
}```
### Sample run
```text
Input: m
Output: M
```
