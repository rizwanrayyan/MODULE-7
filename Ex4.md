# Ex.No:4
# Ex.Name : Write a CPP program for Infix To Prefix Conversion using Linked List Stack STL
## Date: 18/09/2025
## Aim:
To write a C++ program to convert a given infix expression to prefix expression using a stack implemented through STL (linked list–based stack).

## Algorithm:
```
Step-1: Reverse the infix expression

Reverse the expression.

Replace every '(' with ')' and every ')' with '('.

Step-2: Scan each character of the reversed expression

For each symbol:

Operand → Add directly to result.

'(' → Push onto stack.

')' → Pop until '(' is encountered.

Operator →

While stack is not empty AND precedence(top) ≥ precedence(current),
pop the operator and add to result.

Push the current operator.

Step-3: Pop all remaining operators from stack
Step-4: Reverse the result
```

## Program:
```cpp
#include<bits/stdc++.h>
using namespace std;
#include<iostream>
#include<cstring>

struct Node{
    char data;
    struct Node *next;
}*top=NULL;

void push(char x){
    struct Node *p = new Node;
    if(p==NULL){
        p->data = x;
        p->next = top;
        top = p;
    }
    else{
        p->data = x;
        p->next = top;
        top = p;
    }
    
}

char pop(){
    int x=-1;
    struct Node *p;
    if(top==NULL){
        cout<<"\nStack is empty";
    }
    else{
        p=top;
        x = p->data;
        top = top->next;
        delete p;
    }
    return x;
}

int isEmpty(){
    return top?0:1;
}

int precedence(char ch){
    if(ch=='+'||ch=='-')
        return 1;
    else if(ch=='*'||ch=='/')
        return 2;
    else
        return 3;
}

string infixToPrefix(string infix){
    stack<char> s;
    int length=0,i,t;
    string prefix="";
    length = infix.length();
    reverse(infix.begin(),infix.end());
    for(i=0;i<length;i++){
        t = precedence(infix[i]);
        if(t==3){
            prefix += infix[i];
            continue;
        }
        else{
            if(s.empty()|| t>=precedence(s.top())){
                s.push(infix[i]);
                continue;
            }
            else{
                while(!s.empty() && t<precedence(s.top())){
                    prefix+=s.top();
                    s.pop();
                }
                s.push(infix[i]);
                continue;
            }
        }
    }
    
    while(!s.empty()){
        prefix += s.top();
        s.pop();
    }
    
    reverse(prefix.begin(),prefix.end());
    return prefix;
}

int main(){
    char *infix = new char;
    cin>>infix;
    cout<<infixToPrefix(infix);
}
```


## Output:
<img width="511" height="277" alt="image" src="https://github.com/user-attachments/assets/243915a0-04e3-4393-9355-5ec303b51321" />



## Result:
The program successfully converts an infix expression into its prefix form using the STL stack (linked list–based).
