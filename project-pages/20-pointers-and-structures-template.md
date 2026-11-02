# Pointers and Structures

## Exercise 1: Modify a student through a structure pointer
### Problem statement
Create a student structure and display and modify its name and marks through a structure pointer using `->` and `(*ptr).member`.
### Concepts practiced
Structures, pointers, `->`, and dereferenced member access.
### Explanation
A pointer stores the address of a structure variable. We can access the members of the structure either with `ptr->name` or with `(*ptr).name`. Both forms mean the same thing: "access the member of the structure pointed to by `ptr`." This lets us modify the original data without copying the whole structure.
### C solution
```c
#include <stdio.h>
#include <string.h>

struct Student {
    char name[30];
    int marks;
};

int main() {
    struct Student s = {"Alice", 85};
    struct Student *ptr = &s;

    printf("Before modification:\n");
    printf("Name: %s\n", ptr->name);
    printf("Marks: %d\n", ptr->marks);

    strcpy(ptr->name, "Bob");
    (*ptr).marks = 90;

    printf("\nAfter modification:\n");
    printf("Name: %s\n", (*ptr).name);
    printf("Marks: %d\n", (*ptr).marks);

    return 0;
}
```
### Sample run
```text
Input: student record
Output: original and modified record
```

## Exercise 2: Rectangle through a pointer to constant structure
### Problem statement
Read rectangle length and width through a structure pointer, then calculate its area in another function that accepts a pointer to a constant structure.
### Concepts practiced
Structure pointers, `const`, functions, and `->`.
### Explanation
When a function accepts `const struct Rectangle *ptr`, it means the function can read the values but cannot modify them. This is useful for calculation functions such as `area()`, where we only need to read the dimensions and compute the result. The `->` operator helps access members through the pointer.
### C solution
```c
#include <stdio.h>

struct Rectangle {
    float length;
    float width;
};

float area(const struct Rectangle *r) {
    return r->length * r->width;
}

int main() {
    struct Rectangle rect;
    printf("Enter length and width: ");
    scanf("%f %f", &rect.length, &rect.width);

    printf("Area = %.2f\n", area(&rect));

    return 0;
}
```
### Sample run
```text
Input: length = 5, width = 3
Output: area = 15
```
