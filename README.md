# EX.-NO-5-Rail-Fence-Cipher
Implementation of the Rail Fence Cipher encryption technique in C, demonstrating text encryption using different key values (number of rails).

## Name: Joshna.M
## Reference Number: 212225230118

# AIM:
To write a C program to implement the rail fence transposition technique.

# ALGORITHM
1. Start the program.
2. Read the plaintext and the number of rails (key) from the user.
3. Create a matrix to store the plaintext in a zigzag pattern.
4. Fill the matrix by moving downwards and upwards between the rails.
5. Read the characters row by row to generate the ciphertext.
6. Display the encrypted message.
7. Stop the program.

# PROGRAM
```

#include <stdio.h>
#include <string.h>

int main()
{
    char text[1000], rail[100][1000];
    int i, j, row = 0, direction = 1;
    int len, key;

    printf("Enter the plain text: ");
    scanf("%999s", text);

    printf("Enter number of rails: ");
    scanf("%d", &key);

    len = strlen(text);

    if (key < 2 || key > len || key > 100)
    {
        printf("Enter a key between 2 and %d\n",
               len < 100 ? len : 100);
        return 0;
    }

    for (i = 0; i < key; i++)
        for (j = 0; j < len; j++)
            rail[i][j] = '\0';

    for (i = 0; i < len; i++)
    {
        rail[row][i] = text[i];

        if (row == 0)
            direction = 1;
        else if (row == key - 1)
            direction = -1;

        row += direction;
    }

    printf("Cipher text: ");

    for (i = 0; i < key; i++)
        for (j = 0; j < len; j++)
            if (rail[i][j] != '\0')
                printf("%c", rail[i][j]);

    printf("\n");

    return 0;
}
```
# OUTPUT

<img width="1462" height="237" alt="image" src="https://github.com/user-attachments/assets/57ddd7a2-97d0-448b-91a4-57b315703afc" />

# RESULT
Thus, the C program to implement the Rail Fence Cipher encryption technique was successfully executed using the specified number of rails.
