# Array Operations

## Exercise 1: Largest array element
### Problem statement
Find the largest element in an array.
### Concepts practiced
Array traversal, comparison, and initialization.
### Explanation
We assume the first element is the largest and store it in a variable called `largest`. Then we traverse the array from the second element onward. If any element is greater than `largest`, we update `largest`. After the loop ends, `largest` contains the maximum value in the array.
### C solution
```c
#include <stdio.h>

int main() {
    int arr[10], n, i, largest;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    largest = arr[0];

    for (i = 1; i < n; i++) {
        if (arr[i] > largest) {
            largest = arr[i];
        }
    }

    printf("Largest element = %d\n", largest);

    return 0;
}
```
### Sample run
```text
Input: 4 9 2
Output: 9
```

## Exercise 2: Second and second-last elements
### Problem statement
Calculate the sum of the second and second-last elements of an array. Use one-based positions 2 and `n - 1`.
### Concepts practiced
Array indexing and position mapping.
### Explanation
In C, arrays are zero-based, so the second element in one-based position corresponds to index 1. The second-last element in one-based position corresponds to index `n - 2` because the last index is `n - 1`. We use these indexes to access the required elements and add them together.
### C solution
```c
#include <stdio.h>

int main() {
    int arr[10], n, i, sum;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    sum = arr[1] + arr[n - 2];
    printf("Sum = %d\n", sum);

    return 0;
}
```
### Sample run
```text
Input: 5 10 15 20
Output: 30
```

## Exercise 3: Copy an array
### Problem statement
Copy the elements of one array into another array.
### Concepts practiced
Arrays, indexing, and assignment.
### Explanation
We read values into the source array. Then we use a loop to assign each element of the source array to the corresponding position in the destination array. This duplicates the array contents without changing the original.
### C solution
```c
#include <stdio.h>

int main() {
    int arr1[10], arr2[10];
    int n, i;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr1[i]);
    }

    for (i = 0; i < n; i++) {
        arr2[i] = arr1[i];
    }

    printf("Copied array: ");
    for (i = 0; i < n; i++) {
        printf("%d ", arr2[i]);
    }
    printf("\n");

    return 0;
}
```
### Sample run
```text
Input: 1 2 3
Output: 1 2 3
```

## Exercise 4: Count odd and even elements
### Problem statement
Count the odd and even elements of an array.
### Concepts practiced
Arrays, `%`, and counters.
### Explanation
We traverse the array and check each element:
- If `element % 2 == 0`, it is even and we increment the even counter.
- Otherwise, it is odd and we increment the odd counter. At the end, we print both counts.
### C solution
```c
#include <stdio.h>

int main() {
    int arr[10], n, i, odd = 0, even = 0;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    for (i = 0; i < n; i++) {
        if (arr[i] % 2 == 0) {
            even++;
        } else {
            odd++;
        }
    }

    printf("Odd = %d, Even = %d\n", odd, even);

    return 0;
}
```
### Sample run
```text
Input: 1 2 3 4
Output: Odd = 2, Even = 2
```
