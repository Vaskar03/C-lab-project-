# C-lab-project-
#include <stdio.h>

#include <stdlib.h>

#include <string.h>

#define MAX_STUDENTS 100

struct student {

    char name[50];

    int roll_number;

    int marks;

    char grade;

};

int num_students = 0;

struct student students[MAX_STUDENTS];

void add_student() {

    if (num_students == MAX_STUDENTS) {

        printf("Cannot add more students, maximum number of students reached.\n");

        return;

    }

    struct student new_student;

    printf("Enter student name: ");

    scanf("%s", new_student.name);

    printf("Enter student roll number: ");

    scanf("%d", &new_student.roll_number);

    printf("Enter student marks: ");

    scanf("%d", &new_student.marks);

    if (new_student.marks >= 90) {

        new_student.grade = 'A';

    } else if (new_student.marks >= 80) {

        new_student.grade = 'B';

    } else if (new_student.marks >= 70) {

        new_student.grade = 'C';

    } else if (new_student.marks >= 60) {

        new_student.grade = 'D';

    } else {

        new_student.grade = 'F';

    }

    students[num_students++] = new_student;

    printf("Student added successfully.\n");

}

void search_student() {

    int roll_number;

    printf("Enter student roll number to search: ");

    scanf("%d", &roll_number);

    for (int i = 0; i < num_students; i++) {

        if (students[i].roll_number == roll_number) {

            printf("Student name: %s\n", students[i].name);

            printf("Student roll number: %d\n", students[i].roll_number);

            printf("Student marks: %d\n", students[i].marks);

            printf("Student grade: %c\n", students[i].grade);

            return;

        }

    }

    printf("Student with roll number %d not found.\n", roll_number);

}

void display_students() {

    if (num_students == 0) {

        printf("No students to display.\n");

        return;

    }

    printf("Student details:\n");

    for (int i = 0; i < num_students; i++) {

        printf("Name: %s, Roll Number: %d, Marks: %d, Grade: %c\n",

            students[i].name, students[i].roll_number, students[i].marks, students[i].grade);

    }

}

int main() {

    int choice;

    do {

        printf("\n");

        printf("1. Add Student\n");

        printf("2. Search Student\n");

        printf("3. Display All Students\n");

        printf("4. Quit\n");

        printf("\n");

        printf("Enter choice: ");

        scanf("%d", &choice);

        switch (choice) {

            case 1:

                add_student();

                break;

            case 2:

                search_student();

                break;

            case 3:

                display_students();

                break;

            case 4:

                printf("Exiting...\n");

                exit(0);

            default:

                printf("Invalid choice.\n");

        }

    } while (1);

    return 0;

}
