# EX 1 Display operator precedence in the infix expression.
## DATE:
## AIM:
To write a C program to find and display the priority of the operator in the given Postfix expression

## Algorithm
1. Start the program.
2.Define the priority() function to return the priority of operators.
3.Initialize the string containing operators and operands.
4.Loop through each character in the string.
5.For each operator, call the priority() function to determine its priority.
6.Print the operator and its corresponding priority level.   

## Program:
```
/*
Program to find and display the priority of the operator in the given Postfix expression
Developed by:  SANJAY S
RegisterNumber: 212222230132

#include <stdio.h> 
#include<string.h> 
int priority(char x) 
{ 
 
if(x == '&' || x == '|') 
return 1; 
if(x == '+' || x == '-') 
return 2; 
if(x == '*' || x == '/' || x == '%') 
return 3; 
if(x == '^') 
return 4; 
return 0; 
} 
 
int main() 
{ 
int i,j; 
  
  
char ch[100]="(A*B)^C+(D%H)/F&G"; 
for(i=0;i<strlen(ch);i++) 
{ 
if(ch[i]=='+'|| 
ch[i]=='-'|| 
ch[i]=='*'|| 
ch[i]=='/'|| 
ch[i]=='%'|| 
ch[i]=='^'|| 
ch[i]=='&'|| 
ch[i]=='|') 
{ 
j=priority(ch[i]); 
switch(j) 
{ 
case 1: 
printf("%c ---- > ",ch[i]); 
printf("Lowest Priority\n"); 
break; 
case 2: 
printf("%c ---- > ",ch[i]); 
printf("Second Lowest Priority\n"); 
break; 
case 3: 
printf("%c ---- > ",ch[i]); 
printf("Second Highest Priority\n"); 
break; 
case 4: 
printf("%c ---- > ",ch[i]); 
printf("Highest Priority\n"); 
break; 
} 
} 
} 
 
return 0; 
} 

*/
```

## Output:

![image](https://github.com/user-attachments/assets/78b826cf-7b74-4f7e-aceb-9d1300df3545)


## Result:
Thus the C program to find and display the priority of the operator in the given Postfix expression is implemented successfully
# Ex2 Conversion of the infix expression into postfix expression
## DATE:
## AIM:
To write a C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule.

## Algorithm
1. Start the program.
2.Initialize a stack and set the top index to -1.
3.Define the push() and pop() functions to add and remove elements from the stack.
4.Define the priority() function to assign priorities to operators.
5.Traverse the expression in the IntoPost() function, handling operands, parentheses, and operators.
6.After processing the expression, pop and print any remaining operators from the stack.
7.End.
  
## Program:
```
/*
Program to convert the infix expression into postfix expression
Developed by:  SANJAY S
RegisterNumber: 212222230132

*/
#include<stdio.h> 
#include<ctype.h> 
 
char stack[100]; 
int top = -1; 
void push(char x) 
{ 
stack[++top]=x; 
 
} 
 
char pop() 
{ 
if(top==-1) 
return 0; 
else 
return stack[top--]; 
} 
int priority(char x) 
{ 
if(x=='(') 
  
  
{ 
return 0; 
} 
if(x=='&'||x=='|') 
{ 
return 1; 
} 
if(x=='+'||x=='-') 
{ 
return 2; 
} 
if(x=='*'||x=='/'||x=='%') 
{ 
return 3; 
} 
if(x=='^') 
{ 
return 4; 
} 
return 0; 
} 
char IntoPost(char *exp) 
{ 
char *e,x; 
e=exp; 
while(*e!='\0') 
{ 
if(isalnum(*e)) 
{ 
printf("%c ",*e); 
} 
else if(*e=='(') 
{ 
push(*e); 
} 
else if(*e==')') 
{ 
while((x=pop())!='(') 
printf("%c ",x); 
} 
else 
{ 
while(priority(stack[top])>=priority(*e)) 
printf("%c ",pop()); 
push(*e); 
} 
e++; 
} 
  
  
 
while(top != -1) 
{ 
printf("%c ",pop()); 
}return 0; 
} 
int main() 
{ 
char exp[100]="3%2+4*(A&B)"; 
IntoPost(exp); 
return 1; 
}  
*/
```

## Output:

![image](https://github.com/user-attachments/assets/7baf42b1-800f-4019-9547-3b424f35b39a)


## Result:
Thus, the C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule is implemented successfully.
# EX3 Implementation of Tower of Hanoi
## DATE:
## AIM:
To write a C program to implement Tower of Hanoi

## Algorithm
1. Start the program.
2. Check if n is greater than 0.
3.Recursively move n-1 disks from source (x) to auxiliary (z) using destination (y).
4.Print the move of the n-th disk from source (x) to destination (y).
5.Recursively move n-1 disks from auxiliary (z) to destination (y) using source (x).
6.The function is called initially with TOH(n, 'A', 'B', 'C') where 'A', 'B', and 'C' are the rods.
7.End
 
## Program:
```
/*
Program to implement Tower of Hanoi
Developed by:  SANJAY S
RegisterNumber: 212222230132

#include<stdio.h> 
void TOH(int n,char x,char y,char z) 
{ 
if(n>0) 
{ 
TOH(n-1,x,z,y); 
printf("%c to %c",x,y); 
printf("\n"); 
TOH(n-1,z,y,x); 
} 
} 
int main() 
{ 
int n=2; 
TOH(n,'A','B','C'); 
}
*/
```

## Output:

![image](https://github.com/user-attachments/assets/fa455837-895f-4d39-b8a4-1bde186b585a)


## Result:
Thus, the C program to implement Tower of Hanoi using recursion is implemented successfully.

# Ex4 Evaluation of prefix expression
## DATE:
## AIM:
To write a C function to evaluate the given prefix expression using stack and print the output of the given prefix expression from the stack inside the function . 

## Algorithm
1. Start
2.Initialize an empty stack s with a variable top for tracking the stack index.
3.Define a push() function to add an element to the stack.
4.Define a pop() function to remove and return the top element from the stack.
5.In evalprefix(), loop through the given prefix expression from right to left.
6.For each character, if it’s an operator (+, *), pop two operands from the stack, perform the operation, and push the result.
7.If it's a digit, convert it to an integer and push it onto the stack; finally, print the result after the loop ends.
8.End  

## Program:
```
/*
Program to evaluate the given prefix expression
Developed by:  SANJAY S
RegisterNumber: 212222230132

#include<stdio.h> 
#include<string.h> 
#include<ctype.h> 
int s[50]; 
int top=0; 
void push(int ch) 
{ 
top++; 
s[top]=ch; 
} 
 
int pop() 
{ 
int ch; 
ch=s[top]; 
top=top-1; 
return(ch); 
} 
  
  
void evalprefix(char p[50]) 
{ 
int a,b,c,i; 
for(i=strlen(p)-1;i>=0;i--) 
{ 
if(p[i]=='+') 
{ 
a=pop(); 
b=pop(); 
c=a+b; 
push(c); 
} 
else if(p[i]=='*') 
{ 
a=pop(); 
b=pop(); 
c=a*b; 
push(c); 
} 
else 
{ 
push(p[i]-48); 
} 
} 
printf("%d",pop()); 
} 
*/
```

## Output:

![image](https://github.com/user-attachments/assets/c2863f62-6d17-4b34-a202-2dc259e837dd)


## Result:
Thus, the C program to evaluate the prefix expression using stack and print the output of the given prefix expression from the stack inside the function is implemented successfully.

# Ex5 Stack Operations
## DATE:
## AIM:
To write a C function to perform push and pop operation of the stack in the infix to postfix conversion.

## Algorithm
1. Initialize top as -1 and declare stack as a character array.
2. To push, increment top and assign the character to stack[top].
3. To pop, check if top is -1 and return -1 if true.
4. If not, return stack[top] and decrement top.

## Program:
```
/*
Program to find and display the priority of the operator in the given Postfix expression
Developed by:  SANJAY S
RegisterNumber: 212222230132
 
char stack[100]; 
int top = -1; 
void push(char x) 
{ 
    stack[++top] = x; 
} 
 
char pop() 
{ 
    if(top == -1) 
        return -1; 
    else 
        return stack[top--]; 
} 
*/
```

## Output:
![image](https://github.com/user-attachments/assets/eaa49ad7-dc4f-4985-8368-c884d11b93e2)



## Result:
Thus the C program to perform push and pop operation of the stack in the infix to postfix conversion is implemented successfully.
