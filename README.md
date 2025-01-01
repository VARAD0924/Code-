# Code-#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <conio.h>

void start_stopwatch() {
    clock_t start_time, end_time;
    double elapsed_time;
    char input;

    printf("Stopwatch started. Press 'q' to stop.\n");

    start_time = clock();

    while(1) {
        // If the user presses 'q', stop the stopwatch
        if (_kbhit()) {
            input = _getch();
            if(input == 'q' || input == 'Q') {
                break;
            }
        }

        // Get the elapsed time
        end_time = clock();
        elapsed_time = ((double)(end_time - start_time)) / CLOCKS_PER_SEC;

        // Display the elapsed time in seconds
        printf("\rElapsed Time: %.2f seconds", elapsed_time);
        fflush(stdout);
    }

    printf("\nStopwatch stopped.\n");
}

int main() {
    char start;

    printf("Welcome to the Stopwatch program!\n");
    printf("Press 's' to start the stopwatch: ");
    
    // Wait for the user to press 's'
    start = getchar();

    if (start == 's' || start == 'S') {
        start_stopwatch();
    } else {
        printf("Invalid input. Exiting.\n");
    }

    return 0;
}
