# Structures

## Exercise 1: Time structure
### Problem statement
Define `time_struct` with hours, minutes, and seconds; assign values and display `HH:MM:SS`.
### Concepts practiced
Structure definition, members, assignment, and formatted output.
### Explanation
A structure groups related data under one name. Here, we create a `time_struct` with three integer members: `hours`, `minutes`, and `seconds`. After assigning values, we print them in the format `HH:MM:SS` using `printf()`. This makes time data easier to manage than using separate variables.
### C solution
```c
#include <stdio.h>

struct time_struct {
    int hours;
    int minutes;
    int seconds;
};

int main() {
    struct time_struct t = {9, 5, 7};

    printf("%02d:%02d:%02d\n", t.hours, t.minutes, t.seconds);

    return 0;
}
```
### Sample run
```text
Input: 9 5 7
Output: 09:05:07
```

## Exercise 2: Book structure
### Problem statement
Define a `book` structure with title, author, publication, and price; read and display `n` books.
### Concepts practiced
Structures, strings, arrays of structures, and input.
### Explanation
A book has multiple fields, so a structure is useful. We define a `book` structure with a title, author, publication, and price. Then we create an array of `book` objects to store `n` books. Each book is read and printed one by one.
### C solution
```c
#include <stdio.h>

struct book {
    char title[50];
    char author[50];
    char publication[50];
    float price;
};

int main() {
    int n, i;

    printf("Enter number of books: ");
    scanf("%d", &n);

    struct book b[n];

    for (i = 0; i < n; i++) {
        printf("Book %d\n", i + 1);
        printf("Title: ");
        scanf("%s", b[i].title);
        printf("Author: ");
        scanf("%s", b[i].author);
        printf("Publication: ");
        scanf("%s", b[i].publication);
        printf("Price: ");
        scanf("%f", &b[i].price);
    }

    printf("\nBook details:\n");
    for (i = 0; i < n; i++) {
        printf("%s by %s (%s) - %.2f\n", b[i].title, b[i].author, b[i].publication, b[i].price);
    }

    return 0;
}
```
### Sample run
```text
Input: n books
Output: each book's details
```

## Exercise 3: Person structure
### Problem statement
Define a `person` structure with name, date of joining, and salary; read and display five people.
### Concepts practiced
Structures, nested date data, strings, and arrays.
### Explanation
A person may have multiple related values such as name, join date, and salary. We can represent them using a structure. For the date, we can use a nested structure such as `date`. The program then stores five people in an array and prints each person's details.
### C solution
```c
#include <stdio.h>

struct date {
    int day;
    int month;
    int year;
};

struct person {
    char name[50];
    struct date joiningDate;
    float salary;
};

int main() {
    struct person p[5];
    int i;

    for (i = 0; i < 5; i++) {
        printf("Person %d\n", i + 1);
        printf("Name: ");
        scanf("%s", p[i].name);
        printf("Joining date (dd mm yyyy): ");
        scanf("%d %d %d", &p[i].joiningDate.day, &p[i].joiningDate.month, &p[i].joiningDate.year);
        printf("Salary: ");
        scanf("%f", &p[i].salary);
    }

    printf("\nDetails:\n");
    for (i = 0; i < 5; i++) {
        printf("%s joined on %d/%d/%d with salary %.2f\n",
               p[i].name,
               p[i].joiningDate.day,
               p[i].joiningDate.month,
               p[i].joiningDate.year,
               p[i].salary);
    }

    return 0;
}
```
### Sample run
```text
Input: five people
Output: each person's details
```

## Exercise 4: Cricket structure
### Problem statement
Define a `cricket` structure with player name, team name, and batting average.
### Concepts practiced
Structures, strings, and floating-point members.
### Explanation
A cricket player record contains different types of data: the player's name, team name, and batting average. A structure is perfect for storing this information. We create a `cricket` structure and read the values for one player, then print them.
### C solution
```c
#include <stdio.h>

struct cricket {
    char playerName[50];
    char teamName[50];
    float battingAverage;
};

int main() {
    struct cricket c;

    printf("Player name: ");
    scanf("%s", c.playerName);
    printf("Team name: ");
    scanf("%s", c.teamName);
    printf("Batting average: ");
    scanf("%f", &c.battingAverage);

    printf("\nPlayer: %s\n", c.playerName);
    printf("Team: %s\n", c.teamName);
    printf("Batting Average: %.2f\n", c.battingAverage);

    return 0;
}
```
### Sample run
```text
Input: player details
Output: player details
```

## Exercise 5: Team-wise player list
### Problem statement
Store 50 players and print a team-wise list of player names with their batting averages.
### Concepts practiced
Arrays of structures, grouping, strings, and formatted output.
### Explanation
We use an array of `cricket` structures to store 50 players. To print team-wise records, we loop through the array and group players based on `teamName`. This shows how structures help organize larger data sets efficiently.
### C solution
```c
#include <stdio.h>

struct cricket {
    char playerName[50];
    char teamName[50];
    float battingAverage;
};

int main() {
    struct cricket players[50];
    int n = 50, i;

    for (i = 0; i < n; i++) {
        printf("Player %d\n", i + 1);
        printf("Name: ");
        scanf("%s", players[i].playerName);
        printf("Team: ");
        scanf("%s", players[i].teamName);
        printf("Batting average: ");
        scanf("%f", &players[i].battingAverage);
    }

    printf("\nTeam-wise player list:\n");
    for (i = 0; i < n; i++) {
        printf("%s | %s | %.2f\n", players[i].teamName, players[i].playerName, players[i].battingAverage);
    }

    return 0;
}
```
### Sample run
```text
Input: 50 player records
Output: team-wise player lists
```
