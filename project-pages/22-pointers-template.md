# Pointers

## Exercise 1: Swap two numbers using pointers
### Problem statement
Write a C program to swap two numbers using pointers.
### Concepts practiced
Pointers, call by reference, and the dereference operator `*`.
### Explanation
A function normally receives copies of its arguments, so swapping inside it does not affect the caller. If we pass the addresses of the variables (`&x`, `&y`) and receive them as pointers (`int *a`, `int *b`), the function can read and change the original values using `*a` and `*b`. A temporary variable holds one value while the two are exchanged.
### C solution
```c
#include <stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x, y;

    printf("Enter two numbers: ");
    if (scanf("%d %d", &x, &y) != 2) {
        printf("Invalid input.\n");
        return 1;
    }

    printf("Before swap: x = %d, y = %d\n", x, y);
    swap(&x, &y);
    printf("After swap: x = %d, y = %d\n", x, y);

    return 0;
}
```
### Sample run
```text
Input: 10 20
Output: Before swap: x = 10, y = 20
        After swap: x = 20, y = 10
```

## Exercise 2: Print value and address using a pointer
### Problem statement
Write a C program to print the value and address of a variable using a pointer.
### Concepts practiced
Pointer declaration, address-of operator `&`, and the `%p` format specifier.
### Explanation
A pointer is a variable that stores a memory address. `int *ptr = &num;` makes `ptr` hold the address of `num`. Using `*ptr` gives the value stored at that address, and `&ptr` gives the address of the pointer itself. Addresses are printed with `%p` after casting to `(void *)`. The actual address values change from run to run.
### C solution
```c
#include <stdio.h>

int main() {
    int num = 25;
    int *ptr = &num;

    printf("Value of num: %d\n", num);
    printf("Address of num: %p\n", (void *)&num);
    printf("Value stored in ptr (address of num): %p\n", (void *)ptr);
    printf("Value pointed to by ptr: %d\n", *ptr);
    printf("Address of ptr itself: %p\n", (void *)&ptr);

    return 0;
}
```
### Sample run
```text
Input: none
Output: Value of num: 25
        Value pointed to by ptr: 25
        (addresses differ on every run)
```

## Exercise 3: Sum of two numbers using pointers
### Problem statement
Write a C program to calculate the sum of two numbers using pointers.
### Concepts practiced
Pointers, `scanf` with pointers, and dereferencing.
### Explanation
We store the addresses of `a` and `b` in `p1` and `p2`. Because pointers already hold addresses, `scanf` can use them directly without `&`. The sum is computed with `*p1 + *p2`, which reads the values the pointers point to.
### C solution
```c
#include <stdio.h>

int main() {
    int a, b, sum;
    int *p1 = &a, *p2 = &b;

    printf("Enter two numbers: ");
    if (scanf("%d %d", p1, p2) != 2) {
        printf("Invalid input.\n");
        return 1;
    }

    sum = *p1 + *p2;
    printf("Sum = %d\n", sum);

    return 0;
}
```
### Sample run
```text
Input: 15 27
Output: Sum = 42
```

## Exercise 4: Sum of array elements using a pointer
### Problem statement
Write a C program to calculate the sum of elements of an array using a pointer.
### Concepts practiced
Arrays and pointers, pointer arithmetic, and loops.
### Explanation
The name of an array points to its first element, so `ptr = arr;` makes the pointer start at `arr[0]`. The expression `*(ptr + i)` is the same as `arr[i]`: adding `i` to a pointer moves it forward by `i` elements, not `i` bytes. A loop adds each element to `sum`.
### C solution
```c
#include <stdio.h>

int main() {
    int arr[100], n, sum = 0;
    int *ptr;

    printf("Enter number of elements (max 100): ");
    if (scanf("%d", &n) != 1 || n <= 0 || n > 100) {
        printf("Invalid size.\n");
        return 1;
    }

    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    ptr = arr;
    for (int i = 0; i < n; i++) {
        sum += *(ptr + i);
    }

    printf("Sum of array elements = %d\n", sum);

    return 0;
}
```
### Sample run
```text
Input: 5 elements: 1 2 3 4 5
Output: Sum of array elements = 15
```

## Exercise 5: Sort an array using a pointer
### Problem statement
Write a C program for sorting using a pointer.
### Concepts practiced
Passing arrays to functions, pointer arithmetic, and bubble sort.
### Explanation
An array passed to a function decays to a pointer to its first element, so the function parameter `int *arr` works on the original array. Inside the function we use bubble sort: compare neighbouring elements `*(arr + j)` and `*(arr + j + 1)` and swap them if they are out of order. After each pass the largest remaining element settles at the end.
### C solution
```c
#include <stdio.h>

void sortArray(int *arr, int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (*(arr + j) > *(arr + j + 1)) {
                int temp = *(arr + j);
                *(arr + j) = *(arr + j + 1);
                *(arr + j + 1) = temp;
            }
        }
    }
}

int main() {
    int arr[100], n;

    printf("Enter number of elements (max 100): ");
    if (scanf("%d", &n) != 1 || n <= 0 || n > 100) {
        printf("Invalid size.\n");
        return 1;
    }

    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", arr + i);
    }

    sortArray(arr, n);

    printf("Sorted array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", *(arr + i));
    }
    printf("\n");

    return 0;
}
```
### Sample run
```text
Input: 5 elements: 9 3 7 1 5
Output: Sorted array: 1 3 5 7 9
```

## Exercise 6: Sum of two numbers using a pointer to function
### Problem statement
Write a C program to find the sum of two numbers using a pointer to function.
### Concepts practiced
Function pointers, function declarations, and indirect calls.
### Explanation
A function pointer stores the address of a function. The declaration `int (*fptr)(int, int) = add;` creates a pointer that can point to any function taking two `int` values and returning an `int`. We call the function through the pointer with `fptr(x, y)`. Function pointers are the basis for callbacks and menu-style dispatch tables.
### C solution
```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int x, y;
    int (*fptr)(int, int) = add;

    printf("Enter two numbers: ");
    if (scanf("%d %d", &x, &y) != 2) {
        printf("Invalid input.\n");
        return 1;
    }

    printf("Sum = %d\n", fptr(x, y));

    return 0;
}
```
### Sample run
```text
Input: 8 12
Output: Sum = 20
```
