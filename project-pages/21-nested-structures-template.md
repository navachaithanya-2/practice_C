# Nested Structures

## Exercise 1: Person with nested date
### Problem statement
Define a person structure containing a nested date structure. Read and display a birth date in `dd/mm/yyyy` format.
### Concepts practiced
Nested structures, member access, input, and formatted output.
### Explanation
A nested structure means one structure is declared inside another. Here, we create a `date` structure with `day`, `month`, and `year`, and then a `person` structure that contains a `date` member called `dob`. To access the inner structure, we use `person.dob.day`, `person.dob.month`, and `person.dob.year`. This keeps related information organized.
### C solution
```c
#include <stdio.h>

struct Date {
    int day;
    int month;
    int year;
};

struct Person {
    char name[30];
    struct Date dob;
};

int main() {
    struct Person p;

    printf("Enter name: ");
    scanf("%s", p.name);

    printf("Enter birth date (dd mm yyyy): ");
    scanf("%d %d %d", &p.dob.day, &p.dob.month, &p.dob.year);

    printf("Name: %s\n", p.name);
    printf("Date of birth: %02d/%02d/%04d\n", p.dob.day, p.dob.month, p.dob.year);

    return 0;
}
```
### Sample run
```text
Input: 02 11 2000
Output: 02/11/2000
```

## Exercise 2: Employee with nested address
### Problem statement
Define an employee structure containing a nested address structure, initialize it at declaration time, and display all details.
### Concepts practiced
Nested structures, initialization, strings, and member access.
### Explanation
We define an `Address` structure with fields like city and state, and an `Employee` structure containing `name`, `id`, and an `Address` member. We initialize the nested structure at declaration time like: `employee e = {"John", 101, {"Bangalore", "Karnataka"}};` This is a convenient way to create structured data without assigning values one by one.
### C solution
```c
#include <stdio.h>

struct Address {
    char city[30];
    char state[30];
};

struct Employee {
    char name[30];
    int id;
    struct Address addr;
};

int main() {
    struct Employee e = {"John", 101, {"Bangalore", "Karnataka"}};

    printf("Employee Name: %s\n", e.name);
    printf("Employee ID: %d\n", e.id);
    printf("City: %s\n", e.addr.city);
    printf("State: %s\n", e.addr.state);

    return 0;
}
```
### Sample run
```text
Input: Initialized employee
Output: employee and address details
```

## Exercise 3: Pointer to a nested date structure
### Problem statement
Access a nested date structure inside a student structure using pointers, and change the admission year through a separate pointer to the inner structure.
### Concepts practiced
Nested structures, structure pointers, inner-structure pointers, and `->`.
### Explanation
We create a `Date` structure and a `Student` structure that contains it. We then use a pointer to the `Student` and another pointer to the inner `Date` structure. This shows how nested structures can be accessed through multiple pointer levels:
- `studentPtr->dob.year`
- `datePtr->year` The Admission year is updated through the inner pointer to demonstrate pointer-based modification.

### C solution
```c
#include <stdio.h>

struct Date {
    int day;
    int month;
    int year;
};

struct Student {
    char name[30];
    struct Date dob;
};

int main() {
    struct Student s = {"Alice", {10, 6, 2002}};
    struct Student *studentPtr = &s;
    struct Date *datePtr = &s.dob;

    printf("Before change:\n");
    printf("Name: %s\n", studentPtr->name);
    printf("Date of birth: %02d/%02d/%04d\n", studentPtr->dob.day, studentPtr->dob.month, studentPtr->dob.year);

    datePtr->year = 2003;

    printf("\nAfter change:\n");
    printf("Name: %s\n", studentPtr->name);
    printf("Date of birth: %02d/%02d/%04d\n", studentPtr->dob.day, studentPtr->dob.month, studentPtr->dob.year);

    return 0;
}
```
### Sample run
```text
Input: student record with admission date
Output: record with updated admission year
```
