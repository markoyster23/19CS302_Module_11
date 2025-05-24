 PROGRAM TO CONVERT UPPERCASE TO LOWERCASE WITHOUT 
USING THE INBUILT FUNCTION. 
 
AIM: 
To write a program to convert uppercase to lowercase without using the inbuilt function. 
 
ALGORITHM: 
1. Start. 
2. Define a variables. 
3. Write a program to convert uppercase to lowercase without using the inbuilt function. 
4. Read the value using scanf. 
5. Ask the user to make an input. 
6. Print out the answer. 
7. End

Program:
```
#include <stdio.h> 
#include <ctype.h> 
#include <string.h> 
 
int main() { 
char str[10]; 
scanf("%s",str); 
int len = strlen(str); 
for (int i = 0; i < len; i++) { 
str[i] = tolower(str[i]); 
} 
printf("%s", str); 
}
```
OUTPUT:
TODAY\
today
