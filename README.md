#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    int random, guess;
    int no_of_guess = 0;
    srand(time(NULL));
  
    printf("Welcome to the world of Guessing Numbers\n");
    random = rand() % 100 + 1; // Generating between 1 to 100

    do {
        char buf[64];
        printf("\nPlease enter your Guess between (1 to 100): ");
        if (!fgets(buf, sizeof(buf), stdin)) {
            printf("Input error. Exiting.\n");
            break;
        }

        char *endptr;
        long val = strtol(buf, &endptr, 10);
        if (endptr == buf || (*endptr != '\n' && *endptr != '\0')) {
            printf("Invalid input — please enter an integer.\n");
            continue;
        }

        guess = (int)val;
        if (guess < 1 || guess > 100) {
            printf("Invalid input! Please enter a number between 1 and 100.\n");
            continue;
        }

        no_of_guess++;

        if (guess < random) {
            printf("Guess a larger number.\n");
        } else if (guess > random) {
            printf("Guess a smaller number.\n");
        } else {
            printf("\nCongratulations!!! You have guessed the number in %d attempts.\n", no_of_guess);
        }

    } while (guess != random);

    printf("\nBye Bye, Thanks for Playing.\n");
    printf("Developed by: jafshii\n");

    return 0;
}

