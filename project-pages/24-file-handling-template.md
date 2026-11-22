# File Handling

## Exercise 1: Display the content of a file
### Problem statement
Write a C program to display the content of a given file.
### Concepts practiced
`FILE` pointers, `fopen`, `fgetc`, `fclose`, and error checking.
### Explanation
`fopen(filename, "r")` opens a file for reading and returns `NULL` if the file does not exist, so we check it before use. `fgetc` reads one character at a time and returns `EOF` at the end of the file. The return value is stored in an `int` (not `char`) so that `EOF` can be detected correctly. Each character is printed with `putchar`, and the file is closed with `fclose`.
### C solution
```c
#include <stdio.h>

int main() {
    char filename[100];
    FILE *fp;
    int ch;

    printf("Enter file name: ");
    scanf("%99s", filename);

    fp = fopen(filename, "r");
    if (fp == NULL) {
        printf("Error: cannot open file '%s'.\n", filename);
        return 1;
    }

    while ((ch = fgetc(fp)) != EOF) {
        putchar(ch);
    }

    fclose(fp);
    return 0;
}
```
### Sample run
```text
Input: file name: t.txt
Output: (the contents of t.txt are printed)
```

## Exercise 2: Copy a file
### Problem statement
Write a C program to copy a given file.
### Concepts practiced
Reading and writing files, `fputc`, file modes `"r"` and `"w"`.
### Explanation
We open the source file in read mode and the target file in write mode (`"w"` creates the file or overwrites it). Characters are read from the source with `fgetc` and written to the target with `fputc` until `EOF`. If the target cannot be created, the source file is closed before exiting so no file handle is leaked.
### C solution
```c
#include <stdio.h>

int main() {
    char source[100], target[100];
    FILE *src, *dest;
    int ch;

    printf("Enter source file name: ");
    scanf("%99s", source);
    printf("Enter target file name: ");
    scanf("%99s", target);

    src = fopen(source, "r");
    if (src == NULL) {
        printf("Error: cannot open source file '%s'.\n", source);
        return 1;
    }

    dest = fopen(target, "w");
    if (dest == NULL) {
        printf("Error: cannot create target file '%s'.\n", target);
        fclose(src);
        return 1;
    }

    while ((ch = fgetc(src)) != EOF) {
        fputc(ch, dest);
    }

    printf("File copied successfully.\n");

    fclose(src);
    fclose(dest);
    return 0;
}
```
### Sample run
```text
Input: source: t.txt, target: copy.txt
Output: File copied successfully.
```

## Exercise 3: Count lines, words, tabs, and characters
### Problem statement
Write a C program to count the lines, words, tabs, and characters in a file.
### Concepts practiced
File reading, character classification with `isspace`, and counters.
### Explanation
We read the file one character at a time. Every character increments `chars`; a newline `\n` increments `lines`; a tab `\t` increments `tabs`. To count words we use a flag `inWord`: when we move from whitespace to a non-whitespace character, a new word begins, so we increment `words` and set the flag. Whitespace resets the flag.
### C solution
```c
#include <stdio.h>
#include <ctype.h>

int main() {
    char filename[100];
    FILE *fp;
    int ch;
    int lines = 0, words = 0, tabs = 0, chars = 0;
    int inWord = 0;

    printf("Enter file name: ");
    scanf("%99s", filename);

    fp = fopen(filename, "r");
    if (fp == NULL) {
        printf("Error: cannot open file '%s'.\n", filename);
        return 1;
    }

    while ((ch = fgetc(fp)) != EOF) {
        chars++;

        if (ch == '\n') {
            lines++;
        }
        if (ch == '\t') {
            tabs++;
        }

        if (isspace(ch)) {
            inWord = 0;
        } else if (!inWord) {
            inWord = 1;
            words++;
        }
    }

    fclose(fp);

    printf("Lines: %d\n", lines);
    printf("Words: %d\n", words);
    printf("Tabs: %d\n", tabs);
    printf("Characters: %d\n", chars);

    return 0;
}
```
### Sample run
```text
Input: file with 2 lines ("hello world<TAB>foo" / "second line here")
Output: Lines: 2
        Words: 6
        Tabs: 1
        Characters: 33
```

## Exercise 4: Store student names and marks in a file
### Problem statement
Write a C program to read the name and marks of `n` students and store them in a file.
### Concepts practiced
Structures, `fprintf`, `fscanf`, and text files.
### Explanation
A `Student` structure holds a name and marks. After opening `students.txt` in write mode, we read each student's details and write them as one line using `fprintf`, just like `printf` but sending output to a file. To confirm the data was saved, the file is reopened in read mode and its records are read back with `fscanf` and displayed.
### C solution
```c
#include <stdio.h>

struct Student {
    char name[30];
    int marks;
};

int main() {
    int n;
    FILE *fp;
    struct Student s;

    printf("Enter number of students: ");
    if (scanf("%d", &n) != 1 || n <= 0) {
        printf("Invalid number.\n");
        return 1;
    }

    fp = fopen("students.txt", "w");
    if (fp == NULL) {
        printf("Error: cannot create file.\n");
        return 1;
    }

    for (int i = 0; i < n; i++) {
        printf("Enter name and marks of student %d: ", i + 1);
        scanf("%29s %d", s.name, &s.marks);
        fprintf(fp, "%s %d\n", s.name, s.marks);
    }

    fclose(fp);
    printf("Data stored in students.txt\n");

    /* Read back to verify */
    fp = fopen("students.txt", "r");
    if (fp == NULL) {
        return 1;
    }
    printf("\nFile contents:\n");
    while (fscanf(fp, "%29s %d", s.name, &s.marks) == 2) {
        printf("%s - %d\n", s.name, s.marks);
    }
    fclose(fp);

    return 0;
}
```
### Sample run
```text
Input: 2 students: Alice 85, Bob 90
Output: Data stored in students.txt
        Alice - 85
        Bob - 90
```
