# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 

## OUTPUT
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

#define SIZE 3

int charToNum(char c) {
    return toupper(c) - 'A';
}

char numToChar(int n) {
    return (n % 26) + 'A';
}

void encryptBlock(int block[SIZE], int key[SIZE][SIZE], char result[SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        int sum = 0;
        for (int j = 0; j < SIZE; j++) {
            sum += key[i][j] * block[j];
        }
        result[i] = numToChar(sum % 26);
    }
}

int main() {
    char plaintext[100];
    char ciphertext[100] = "";
    int key[SIZE][SIZE] = {
        {6, 24, 1},
        {13, 16, 10},
        {20, 17, 15}
    };
    int block[SIZE];
    int len;

    printf("Enter Plaintext: ");
    scanf("%s", plaintext);

    len = strlen(plaintext);

    while (len % SIZE != 0) {
        plaintext[len++] = 'X'; // padding
        plaintext[len] = '\0';
    }

    for (int k = 0; k < len; k += SIZE) {
        for (int i = 0; i < SIZE; i++) {
            block[i] = charToNum(plaintext[k + i]);
        }
        char result[SIZE];
        encryptBlock(block, key, result);
        strncat(ciphertext, result, SIZE);
    }

    printf("Ciphertext: %s\n", ciphertext);
    return 0;
}
```
## RESULT
<img width="1688" height="902" alt="image" src="https://github.com/user-attachments/assets/535e7dc1-54bf-4cb2-9c43-d2461cf28e19" />

