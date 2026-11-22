# Dynamic Memory Allocation

## Exercise 1: Sort numbers using malloc
### Problem statement
Write a C program to sort numbers using `malloc`.
### Concepts practiced
`malloc`, dynamic arrays, `free`, and sorting.
### Explanation
`malloc(n * sizeof(int))` reserves memory for `n` integers at run time, so the array size does not have to be known when the program is written. The function returns `NULL` if allocation fails, so we always check it. After sorting the data with bubble sort, `free(arr)` returns the memory to the system to avoid a memory leak.
### C solution
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n;
    int *arr;

    printf("Enter number of elements: ");
    if (scanf("%d", &n) != 1 || n <= 0) {
        printf("Invalid size.\n");
        return 1;
    }

    arr = (int *)malloc(n * sizeof(int));
    if (arr == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    printf("Enter %d numbers: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    printf("Sorted numbers: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    free(arr);
    return 0;
}
```
### Sample run
```text
Input: 5 elements: 9 3 7 1 5
Output: Sorted numbers: 1 3 5 7 9
```

## Exercise 2: Square of numbers using calloc
### Problem statement
Write a C program to find the square of numbers using `calloc`.
### Concepts practiced
`calloc`, zero-initialized memory, and `free`.
### Explanation
`calloc(n, sizeof(int))` works like `malloc` but takes the element count and element size separately, and it sets every byte of the allocated block to zero. This means the array starts with all elements equal to 0. We read the numbers, print the square of each one, and finally release the memory with `free`.
### C solution
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n;
    int *arr;

    printf("Enter number of elements: ");
    if (scanf("%d", &n) != 1 || n <= 0) {
        printf("Invalid size.\n");
        return 1;
    }

    arr = (int *)calloc(n, sizeof(int));
    if (arr == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    printf("Enter %d numbers: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Squares: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i] * arr[i]);
    }
    printf("\n");

    free(arr);
    return 0;
}
```
### Sample run
```text
Input: 4 elements: 1 2 3 4
Output: Squares: 1 4 9 16
```

## Exercise 3: Add and remove items using realloc
### Problem statement
Write a C program to add or remove an item from a list using `realloc`.
### Concepts practiced
`realloc`, growing and shrinking memory, menu-driven programs, and safe pointer handling.
### Explanation
`realloc(ptr, newSize)` resizes an existing block of memory while keeping its contents. When `ptr` is `NULL` it behaves like `malloc`, so an empty list can grow from nothing. We store the result of `realloc` in a temporary pointer first: if it fails and returns `NULL`, the original block is still valid and is not lost. Adding an item grows the list by one element; removing the last item shrinks it by one. A menu loop lets the user add, remove, and display items until they exit.
### C solution
```c
#include <stdio.h>
#include <stdlib.h>

void printList(int *list, int size) {
    if (size == 0) {
        printf("List is empty.\n");
        return;
    }
    printf("List: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", list[i]);
    }
    printf("\n");
}

int main() {
    int *list = NULL;
    int size = 0, choice, value;

    do {
        printf("\n1. Add item\n2. Remove last item\n3. Display list\n4. Exit\n");
        printf("Enter your choice: ");
        if (scanf("%d", &choice) != 1) {
            break;
        }

        switch (choice) {
            case 1: {
                printf("Enter value to add: ");
                scanf("%d", &value);
                int *temp = (int *)realloc(list, (size + 1) * sizeof(int));
                if (temp == NULL) {
                    printf("Memory allocation failed.\n");
                    break;
                }
                list = temp;
                list[size++] = value;
                break;
            }
            case 2:
                if (size == 0) {
                    printf("List is empty.\n");
                } else {
                    size--;
                    if (size == 0) {
                        free(list);
                        list = NULL;
                    } else {
                        int *temp = (int *)realloc(list, size * sizeof(int));
                        if (temp != NULL) {
                            list = temp;
                        }
                    }
                    printf("Last item removed.\n");
                }
                break;
            case 3:
                printList(list, size);
                break;
            case 4:
                printf("Goodbye!\n");
                break;
            default:
                printf("Invalid choice.\n");
        }
    } while (choice != 4);

    free(list);
    return 0;
}
```
### Sample run
```text
Input: add 10, add 20, add 30, display, remove, display
Output: List: 10 20 30
        Last item removed.
        List: 10 20
```
