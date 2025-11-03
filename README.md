#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Student {
    int id;
    char name[50];
    float grade;
};

int main() {
    struct Student students[100];
    int count = 0, choice;
    while (1) {
        printf("\n1. Add Student\n2. View All\n3. Search\n4. Exit\nChoose: ");
        scanf("%d", &choice);

        if (choice == 1) {
            printf("Enter ID, Name, Grade: ");
            scanf("%d %s %f", &students[count].id, students[count].name, &students[count].grade);
            count++;
            printf("Student added.\n");
        } else if (choice == 2) {
            printf("\n--- Student List ---\n");
            for (int i = 0; i < count; i++)
                printf("%d | %s | %.2f\n", students[i].id, students[i].name, students[i].grade);
        } else if (choice == 3) {
            int id, found = 0;
            printf("Enter ID: ");
            scanf("%d", &id);
            for (int i = 0; i < count; i++)
                if (students[i].id == id) {
                    printf("Found: %s with grade %.2f\n", students[i].name, students[i].grade);
                    found = 1;
                }
            if (!found) printf("Student not found.\n");
        } else if (choice == 4) break;
        else printf("Invalid choice.\n");
    }
    return 0;
}
