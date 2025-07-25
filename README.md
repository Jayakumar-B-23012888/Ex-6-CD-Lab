# Ex-6-IMPLEMENTATION-OF-THE-BACK-END-OF-THE-COMPILER-
# Date :13/05/2025

IMPLEMENTATION OF THE BACK END OF THE COMPILER 

# Aim :
To write a program to implement the back end of the compiler.
# ALGORITHM
1. Start the program.
2. Get the three variables from statements and stored in the text file k.txt.
3. Compile the program and give the path of the source file.
4. Execute the program.
5. Target code for the given statement is produced.
6. Stop the program.
# PROGRAM
```
Name : Jayakumar B
Reg.no: 212223040073
```
# expr6.txt
```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

int main() {
    char line[100], var[10], op1[10], op2[10], res[10], op;
    char filename[50];
    FILE *fp;
    int reg = 0;

    printf("Enter the filename of the intermediate code: ");
    scanf("%s", filename);

    fp = fopen(filename, "r");
    if (fp == NULL) {
        printf("Error: Could not open file.\n");
        return 1;
    }

    printf("\nIntermediate Code:\n\n");

    while (fgets(line, sizeof(line), fp)) {
        printf("\t\t%s", line);
    }

    rewind(fp);

    printf("\n\n\tStatement\t\tTarget Code\n\n");

    while (fgets(line, sizeof(line), fp)) {
        // Remove newline if exists
        line[strcspn(line, "\n")] = 0;

        // Example format: t1 = a + b
        if (sscanf(line, "%s = %s %c %s", res, op1, &op, op2) == 4) {
            printf("\t%s\t\tMOV %s, R%d\n", line, op2, reg);
            printf("\t\t\t\t");

            if (op == '+')
                printf("ADD ");
            else if (op == '-')
                printf("SUB ");
            else if (op == '*')
                printf("MUL ");
            else if (op == '/')
                printf("DIV ");
            else
                printf("OP? ");

            printf("%s, R%d\n\n", op1, reg);
            reg++;
        }
    }

    fclose(fp);
    return 0;
}

```
# OUTPUT
![image](https://github.com/user-attachments/assets/5b84c3fc-1709-44c0-b6ad-f57a9a4c04d8)


# Result
The back end of the compiler is implemented successfully, and the output is verified.
