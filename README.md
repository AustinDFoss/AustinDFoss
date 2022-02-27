// Austin Foss
// My Tic-Tac-Toe C Program



#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
#include <string.h>

// Create functions to be called whent he program is executed 
char square[10] = { 'o', '1', '2', '3', '4', '5', '6', '7', '8', '9' };
int checkwin();
void board();


/* This is the main program, which assigns each square to a number that
can then be used in the game for users to select number on keyboard to 
select that square. */
int main()
{
    int player = 1, i, choice; // i represents the players choice, then marks it in the game.
    char mark;
    do
    {
        board();
        player = (player % 2) ? 1 : 2;

        printf("Player %d, Choose a square: ", player); // Asks user to choose a square
        scanf_s("%d", &choice);

        mark = (player == 1) ? 'X' : 'O'; // Assigns player 1 as X and player 2 as O

        if (choice == 1 && square[1] == '1') // Number 1 represents square 1 on grid
            square[1] = mark;

        else if (choice == 2 && square[2] == '2') // Number 2 represents square 2 on grid
            square[2] = mark;

        else if (choice == 3 && square[3] == '3') // Number 3 represents square 3 on grid
            square[3] = mark;

        else if (choice == 4 && square[4] == '4') // Number 4 represents square 4 on grid
            square[4] = mark;

        else if (choice == 5 && square[5] == '5') // Number 5 represents square 5 on grid 
            square[5] = mark;

        else if (choice == 6 && square[6] == '6') // Number 6 represents square 6 on grid 
            square[6] = mark;

        else if (choice == 7 && square[7] == '7') // Number 7 represents square 7 on grid 
            square[7] = mark;

        else if (choice == 8 && square[8] == '8') // Number 8 represents square 8 on grid
            square[8] = mark;

        else if (choice == 9 && square[9] == '9') // Number 9 represents square 9 on grid
            square[9] = mark;

        else
        {
            printf("Invalid move "); // This error prompt displays when user selects a square already taken
            player--;
            _getch();
        }
        i = checkwin(); // All players choices will determine if they won the game. 
        player++;
    } while (i == -1);

    board();
    if (i == 1)
        printf("-->\aPlayer %d wins! Press enter! ", --player);
    else
        printf("-->\aDraw ");
    _getch();

    /* This FILE section opens a text file to display a game sheet that records the winner
    of each game. The text file is labeled as "Tic-Tac-Toe" and displays winner. */
    FILE* fopen(const char* filepath, const char* mode);
    FILE* fp;
    fp = fopen("Tic-Tac-Toe.txt", "w"); // Creates a file and allows players to read and write in it
    //processing files
    fprintf(fp, "%s", "\n\n\tUse this Game Sheet to keep track of who won the game!\n\n ");
    fprintf(fp, "%s", "\nPlayer Key: ");
    fprintf(fp, "%s", "\nPlayer 1 --> Player -1 ");
    fprintf(fp, "%s", "\nPlayer 2 --> Player 0 ");

    while (i == -1);
    if (i == 1)
        printf("\nPress enter again to record winner ", --player); // Displays at the end of game 
    else
        printf("\nDraw ");
    _getch();

    fprintf(fp, "\n\n\t****************    Player %d won!    ****************\n\n ", --player); // Displays the winner in the notepad
    // end of processing
    fclose(fp);

    return 0;
}

    /* This section determines the winner and sets the different winning outcomes.
    Whichever player reaches one of the outcomes below wins. This can be in
    outcomes for three marks horizontally, diagonally, or vertically. */
int checkwin()
{
    if (square[1] == square[2] && square[2] == square[3]) // A possible winning outcome
        return 1;

    else if (square[4] == square[5] && square[5] == square[6]) // A possible winning outcome
        return 1;

    else if (square[7] == square[8] && square[8] == square[9]) // A possible winning outcome
        return 1;

    else if (square[1] == square[4] && square[4] == square[7]) // A possible winning outcome
        return 1; 

    else if (square[2] == square[5] && square[5] == square[8]) // A possible winning outcome
        return 1;

    else if (square[3] == square[6] && square[6] == square[9]) // A possible winning outcome
        return 1;

    else if (square[1] == square[5] && square[5] == square[9]) // A possible winning outcome
        return 1;

    else if (square[3] == square[5] && square[5] == square[7]) // A possible winning outcome
        return 1;

// This is for the horizontal winning outcomes 
    else if (square[1] != '1' && square[2] != '2' && square[3] != '3' && 
        square[4] != '4' && square[5] != '5' && square[6] != '6' && square[7]
        != '7' && square[8] != '8' && square[9] != '9')

        return 0;
    else
        return  -1;
}

/* This function creates the 3x3 grid where users can play the game. Each square is marked with a number
which was defined in the main function. */
void board()
{
    system("cls"); // Clears the square space to replace with players mark
    printf("\n\n\tTic Tac Toe\n\n");
    printf("Player 1 (X)  -  Player 2 (O)\n\n\n");

    printf("     |     |     \n");
    printf("  %c  |  %c  |  %c \n", square[1], square[2], square[3]);
    printf("_____|_____|_____\n");
    printf("     |     |     \n");
    printf("  %c  |  %c  |  %c \n", square[4], square[5], square[6]);
    printf("_____|_____|_____\n");
    printf("     |     |     \n");
    printf("  %c  |  %c  |  %c \n", square[7], square[8], square[9]);
    printf("     |     |     \n\n");
}
