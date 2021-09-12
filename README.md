include <stdio.h>
#include <string.h>
void main()
{
    char teams[5][100] = {"Man Utd", "Arsenal", "Liverpool","Chelsea","Leicester City"}, t[100];
    int goals[5], points[5] = {0, 0, 0, 0, 0}, temp;
    printf("Enter the scores of:\n");
    for (int i = 0; i < 5; i++)
    {
        for (int j = 0; j < 5; j++)
        {
            if (i == j)
            {
                if (j == 4)
                {
                    break;
                }
                j++;
            }
            printf("%s vs %s:", teams[i], teams[j]);
            scanf("%d%d", &goals[i], &goals[j]);
            if (goals[i] > goals[j])
            {
                points[i] += 3;
            }
            else if (goals[j] > goals[i])
            {
                points[j] += 3;
            }
            else
            {
                points[i] += 1;
                points[j] += 1;
            }
        }
    }
    for (int i = 0; i < 5 - 1; i++)
    {
        for (int j = i; j < 5 - 1; j++)
        {
            if (points[j] < points[j + 1])
            {
                temp = points[j];
                points[j] = points[j + 1];
                points[j + 1] = temp;
                strcpy(t, teams[j]);
                strcpy(teams[j], teams[j + 1]);
                strcpy(teams[j + 1], t);
            }
        }
    }
    printf("---------------------------------\n");
    printf("|Team\t\t\t|Points\t|\n");
    for (int i = 0; i < 5; i++)
    {
        printf("|%s\t\t|%d\t|\n", teams[i], points[i]);
    }
    printf("---------------------------------\n");
    printf("%s is the winner of the league\n",teams[0]);
    printf("%s is relagated from the league\n",teams[4]);
}
