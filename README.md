# ideate-
#include <stdio.h>
#include <string.h>

#define MAX_ENTRIES 100
#define STADIUM_NAME_LENGTH 50

typedef struct {
    char stadiumName[STADIUM_NAME_LENGTH];
    int capacity;
} StadiumEntry;

void displayStadiums(StadiumEntry stadiums[], int count) {
    printf("Football Stadium Capacities:\n");
    for (int i = 0; i < count; i++) {
        printf("Stadium Name: %s, Capacity: %d\n", stadiums[i].stadiumName, stadiums[i].capacity);
    }
}

int main() {
    StadiumEntry stadiums[MAX_ENTRIES] = {
        {"Camp Nou", 99354},
        {"Wembley Stadium", 90000},
        {"Old Trafford", 74879},
        {"Santiago Bernabeu", 81044},
        {"San Siro", 80018},
    };
    int count = 5;  
    char inputStadiumName[STADIUM_NAME_LENGTH];
    int choice;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Search for stadium capacity\n");
        printf("2. Display all stadiums\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        
        if (scanf("%d", &choice) != 1) {  
            printf("Invalid input. Please enter a number.\n");
            while (getchar() != '\n');  
            continue;
        }

        switch (choice) {
            case 1:
                printf("Enter the stadium name to search: ");
                scanf(" %[^\n]%*c", inputStadiumName); 

                int found = 0;
                for (int i = 0; i < count; i++) {
                    if (strcasecmp(stadiums[i].stadiumName, inputStadiumName) == 0) { 
                        printf("Stadium Name: %s, Capacity: %d\n", stadiums[i].stadiumName, stadiums[i].capacity);
                        found = 1;
                        break;
                    }
                }
                if (!found) {
                    printf("The stadium %s is not in the directory.\n", inputStadiumName);
                }
                break;

            case 2:
                displayStadiums(stadiums, count);
                break;

            case 3:
                printf("Exiting the program.\n");
                return 0;

            default:
                printf("Invalid choice. Please try again.\n");
                break;
        }
    }

    return 0;
}
