# Tic-Tac-Toe-
A simple tic tac toe game using C language 
#include <stdio.h>

char c[3][3] = {

    {'1', '2', '3'},

    {'4', '5', '6'},

    {'7', '8', '9'}};

int i, j;

void print_board()

{

    printf("\n|---|---|---|\n");

    printf("| %c | %c | %c |\n", c[0][0], c[0][1], c[0][2]);

    printf("|---|---|---|\n");

    printf("| %c | %c | %c |\n", c[1][0], c[1][1], c[1][2]);

    printf("|---|---|---|\n");

    printf("| %c | %c | %c |\n", c[2][0], c[2][1], c[2][2]);

    printf("|---|---|---|\n");

}

void mark(char num, int o)

{

    for (i = 0; i < 3; i++)

    {

        for (j = 0; j < 3; j++)

        {

            if (c[i][j] == num && o == 1)

            {

                c[i][j] = 'X';

                o = 0;

            }

            if (c[i][j] == num && o == 2)

            {

                c[i][j] = 'O';

                o = 0;

            }

        }

    }

    if(o != 0)

    printf("\n*Not a valid choice 😁*\n*You missed your turn 😜*");

    print_board();

}

int winner(char p1[], char p2[], int *p)

{

    for (i = 0; i < 3; i++)

    {

        j = 0;

        if (c[i][0] == c[i][1] && c[i][1] == c[i][2])

        {

            if (c[i][0] == 'X')

            {

                printf("\n🏆%s is Winner🏆", p1);

                *p = 0;

                return *p;

            }

            else

            {

                printf("\n🏆%s is Winner🏆", p2);

                *p = 0;

                return *p;

            }

        }

    }

    for (i = 0; i < 3; i++)

    {

        j = 0;

        if (c[0][i] == c[1][i] && c[1][i] == c[2][i])

        {

            if (c[0][i] == 'X')

            {

                printf("\n🏆%s is Winner🏆", p1);

                *p = 0;

                return *p;

            }

            else

            {

                printf("\n🏆%s is Winner🏆", p2);

                *p = 0;

                return *p;

            }

        }

    }

    if (c[0][0] == c[1][1] && c[1][1] == c[2][2])

   {

            if (c[0][0] == 'X')

            {

                printf("\n🏆%s is Winner🏆", p1);

                *p = 0;

                return *p;

            }

            else

            {

                printf("\n🏆%s is Winner🏆", p2);

                *p = 0;

                return *p;

            }

    }

    if (c[0][2] == c[1][1] && c[1][1] == c[2][0])

   {

            if (c[2][0] == 'X')

            {

                printf("\n🏆%s is Winner🏆", p1);

                *p = 0;

                return *p;

            }

            else

            {

                printf("\n🏆%s is Winner🏆", p2);

                *p = 0;

                return *p;

            }

    }

    

}

void reset()

{

    c[0][0] = '1', c[0][1] = '2', c[0][2] = '3';

    c[1][0] = '4', c[1][1] = '5', c[1][2] = '6';

    c[2][0] = '7', c[2][1] = '8', c[2][2] = '9';

}

int main()

{

    printf("🙏*🌸*🙏🏵️WELCOME🏵️*🙏*🌸*🙏\n");

    printf("\n    🔥  tic tac toe  🔥   \n");

    char player1[15], player2[15];

    printf("\n->Enter player 1 name 🥷 : ");

    scanf("%s", player1);

    printf("\n->Enter player 2 name 🧛 : ");

    scanf("%s", player2);

    printf("\n");

    char choose, yn;

    int o;

    while (1)

    {

        printf(" \n");

        printf("\n.    💙NEW GAME💙    .");

        print_board();

        printf("\n❄️%s🥷=(X) / %s🧛=(O)❄️\n",player1,player2);

        printf("\n❄️Select the box number to put your mark(1-9)❄️\n");

        int draw = 0;

        while (1)

        {

            printf("\n%s's turn 🥷 : ", player1);

            scanf(" %c%*c", &choose);

            o = 1;

            mark(choose, o);

            winner(player1, player2, &o);

            if (o == 0)

                break;

            printf("\n%s's turn 🧛 : ", player2);

            scanf(" %c%*c", &choose);

            o = 2;

            mark(choose, o);

            draw++;

            winner(player1, player2, &o);

            if (o == 0)

            {

                break;

            }

                draw++;

            if(draw > 9)

            {

               printf("\n😅game is draw😁\n"); 

               break;

            }

        }

        if(draw == 9)

        

        printf("\n❄️Do you want to start new game?❄️");

        printf("\nyes(Y)😀/no(N)🥹:");

        scanf("%c", &yn);

        printf(".\n");

        if (yn == 'N')

        {

            printf("\n💙Thanks for playing😇\n");

            break;

        }

        else

            reset();

    }

    return 0;

}
