# One-Dimensional Arrays

## Exercise 1: Count positive and negative values
### Problem statement
Count positive and negative values in an array of 10 integers.
### Concepts practiced
Arrays, traversal, counters, and comparisons.
### Explanation
An array stores multiple values in a single variable name. We read 10 integers into an array and then loop through it. For each element:
- If the value is greater than 0, increase the positive counter.
- If it is less than 0, increase the negative counter.
At the end, print both counts.
### C solution
```c
#include <stdio.h>

int main() {
    int arr[10];
    int i, positive = 0, negative = 0;

    printf("Enter 10 integers:\n");
    for (i = 0; i < 10; i++) {
        scanf("%d", &arr[i]);
    }

    for (i = 0; i < 10; i++) {
        if (arr[i] > 0) {
            positive++;
        } else if (arr[i] < 0) {
            negative++;
        }
    }

    printf("Positive count = %d\n", positive);
    printf("Negative count = %d\n", negative);

    return 0;
}
```
### Sample run
```text
Input: 10 integers
Output: positive count and negative count
```

## Exercise 2: Reverse an array
### Problem statement
Read an array and print its elements in reverse order.
### Concepts practiced
Array indexing and reverse traversal.
### Explanation
We store the numbers in an array, then loop from the last index to the first index. Each element is printed in the reverse order. This is done using the index `i` from `n - 1` down to 0.
### C solution
```c
#include <stdio.h>

int main() {
    int arr[10], n, i;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Reversed array: ");
    for (i = n - 1; i >= 0; i--) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
```
### Sample run
```text
Input: 1 2 3 4
Output: 4 3 2 1
```

## Exercise 3: Sum array elements
### Problem statement
Calculate the sum of all array elements.
### Concepts practiced
Arrays, traversal, and accumulators.
### Explanation
We store numbers in an array and use a loop to visit each element. A variable called `sum` starts at 0 and adds each array value to it. After the loop, we print the total.
### C solution
```c
#include <stdio.h>

int main() {
    int arr[10], n, i, sum = 0;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    for (i = 0; i < n; i++) {
        sum += arr[i];
    }

    printf("Sum = %d\n", sum);

    return 0;
}
```
### Sample run
```text
Input: 1 2 3
Output: 6
```

## Exercise 4: Average array elements
### Problem statement
Calculate the average of the array elements.
### Concepts practiced
Array traversal, sums, and floating-point division.
### Explanation
First, we compute the total sum of all array elements. Then we divide the sum by the number of elements. Since division of integers can lose decimals, we use a floating-point variable and cast or use `float` for the average.
### C solution
```c
#include <stdio.h>

int main() {
    int arr[10], n, i;
    float sum = 0, average;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    for (i = 0; i < n; i++) {
        sum += arr[i];
    }

    average = sum / n;

    printf("Average = %.2f\n", average);

    return 0;
}
```
### Sample run
```text
Input: 2 4 6
Output: 4.00
```
