# EX 51 C program to reverse a string.
## DATE:
## AIM:
To write a C program to reverse a string.

## Algorithm
1. Start. 
2. Define a variables. 
3. Write a c program to press any character and find its REVERSE value. 
4. Read the value using scanf. 
5. Ask the user to make an input. 
6. Print out the answer. 
7. End.

## Program:
```
#include <stdio.h>
#include <string.h>

void reverseString(char str[]) {
    int i, len = strlen(str);
    char temp;

    for (i = 0; i < len / 2; i++) {
        // Swap characters
        temp = str[i];
        str[i] = str[len - i - 1];
        str[len - i - 1] = temp;
    }
}

int main() {
    char str[100];

    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);

    // Remove newline character if present
    size_t ln = strlen(str) - 1;
    if (str[ln] == '\n') str[ln] = '\0';

    reverseString(str);

    printf("Reversed string: %s\n", str);

    return 0;
}

```

## Output:



## Result:
Thus the program was executed and the output was verified successfully.
