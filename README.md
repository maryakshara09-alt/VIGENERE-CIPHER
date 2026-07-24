# VIGENERE-CIPHER
## EX. NO: 4
 

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM
```
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

void encipher();
void decipher();

int main()
{
    int choice;

    while (1)
    {
        printf("\n1. Encrypt Text");
        printf("\n2. Decrypt Text");
        printf("\n3. Exit");

        printf("\n\nEnter Your Choice: ");
        scanf("%d", &choice);

        if (choice == 1)
            encipher();
        else if (choice == 2)
            decipher();
        else if (choice == 3)
            return 0;
        else
            printf("Please Enter a Valid Option.\n");
    }
}

void encipher()
{
    int i, j;
    char input[50], key[20];

    printf("\nEnter Plain Text: ");
    scanf("%s", input);

    printf("Enter Key Value: ");
    scanf("%s", key);

    printf("Resultant Cipher Text: ");

    for (i = 0, j = 0; i < strlen(input); i++, j++)
    {
        if (j >= strlen(key))
            j = 0;

        printf("%c", 65 + (((toupper(input[i]) - 65) +
                            (toupper(key[j]) - 65)) % 26));
    }

    printf("\n");
}

void decipher()
{
    int i, j, value;
    char input[50], key[20];

    printf("\nEnter Cipher Text: ");
    scanf("%s", input);

    printf("Enter Key Value: ");
    scanf("%s", key);

    printf("Decrypted Plain Text: ");

    for (i = 0, j = 0; i < strlen(input); i++, j++)
    {
        if (j >= strlen(key))
            j = 0;

        value = (toupper(input[i]) - 65) - (toupper(key[j]) - 65);

        if (value < 0)
            value += 26;

        printf("%c", 65 + (value % 26));
    }

    printf("\n");
}
```

## OUTPUT
<img width="1686" height="648" alt="Screenshot 2026-07-24 113452" src="https://github.com/user-attachments/assets/7101fdd2-cc79-48dd-973b-c91e43649b26" />

## RESULT
The output is executed and verified successfully
