# CROSSWORD-PUZZLE

#include <stdio.h>
#include <string.h>

#define ROWS 10
#define COLS 10

void printCrossword(char crossword[ROWS][COLS]) {
    for (int i = 0; i < ROWS; i++) {
        for (int j = 0; j < COLS; j++) {
            printf("%c ", crossword[i][j]);
        }
        printf("\n");
    }
}

void insertWord(char crossword[ROWS][COLS], char word[], int row, int col, char direction) {
    int len = strlen(word);
    if (direction == 'h') {
        for (int i = 0; i < len; i++) {
            crossword[row][col + i] = word[i];
        }
    } else if (direction == 'v') {
        for (int i = 0; i < len; i++) {
            crossword[row + i][col] = word[i];
        }
    }
}

int main() {
    char crossword[ROWS][COLS];
    memset(crossword, '-', sizeof(crossword)); // Initialize crossword with '-'

    // Prompt user to input words and positions
    char word[20];
    int row, col;
    char direction;

    printf("Enter word to insert: ");
    scanf("%s", word);
    printf("Enter starting row (0-9): ");
    scanf("%d", &row);
    printf("Enter starting column (0-9): ");
    scanf("%d", &col);
    printf("Enter direction (h for horizontal, v for vertical): ");
    scanf(" %c", &direction);

    // Insert the word into the crossword
    insertWord(crossword, word, row, col, direction);

    // Print the crossword
    printf("\nCrossword puzzle:\n");
    printCrossword(crossword);

    return 0;
}

