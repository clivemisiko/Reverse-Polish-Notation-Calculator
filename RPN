#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

#define MAX 100

char stack[MAX];
int top = -1;

void push(char item) {
    if (top >= MAX - 1) {
        printf("Stack Overflow.\n");
    } else {
        stack[++top] = item;
    }
}

char pop() {
    if (top < 0) {
        printf("Stack Underflow.\n");
        return -1;
    } else {
        return stack[top--];
    }
}

int isOperator(char symbol) {
    return symbol == '+' || symbol == '-' || symbol == '*' || symbol == '/' || symbol == '%';
}

int precedence(char symbol) {
    switch (symbol) {
        case '+':
        case '-':
            return 1;
        case '*':
        case '/':
        case '%':
            return 2;
        default:
            return 0;
    }
}

void InfixToPrefix(char infix[], char prefix[]) {
    int i, j = 0;
    char item, x;

    strrev(infix);
    for (i = 0; i < strlen(infix); i++) {
        item = infix[i];
        if (item == ')') {
            push(item);
        } else if (item == '(') {
            while ((x = pop()) != ')') {
                prefix[j++] = x;
            }
        } else if (isOperator(item)) {
            while (precedence(stack[top]) >= precedence(item)) {
                prefix[j++] = pop();
            }
            push(item);
        } else {
            prefix[j++] = item;
        }
    }

    while (top != -1) {
        prefix[j++] = pop();
    }
    strrev(prefix);
    prefix[j] = '\0';
}

int main() {
    char infix[MAX], prefix[MAX];

    printf("Enter an infix expression: ");
    gets(infix);

    InfixToPrefix(infix, prefix);

    printf("Prefix expression: %s\n", prefix);

    return 0;
}
