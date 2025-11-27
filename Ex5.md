# Ex.No:5
# Ex.Name : Write a CPP program for Prefix To Postfix Conversion using Stack STL
## Date: 18/09/2025
## Aim: 
To write a C++ program to convert a Prefix expression to Postfix using a Stack implemented with STL.

## Algorithm:
```
1. Start the program.
2. Read the Prefix expression.
3. Scan the expression from right to left:

For each character:

If operand

Push it onto the stack as a string.

If operator

Pop the top two elements from the stack (operand1 and operand2).

Form a new string:
postfix = operand1 + operand2 + operator

Push this new postfix string back onto the stack.

4. After scanning all characters

The stack's top element contains the Postfix expression.

5. Display the postfix expression.
6. End the program.
```



## Program:
```cpp
#include<bits/stdc++.h>
using namespace std;
bool isOperator(char c){
    switch(c){
        case '+':
        case '-':
        case '*':
        case '/':
            return true;
    }
    return false;
}

string preToPost(string prefix){
    int n = prefix.size();
    stack<string> s;
    int i;
    for(i=n-1;i>=0;i--){
        if(isOperator(prefix[i])){
            string op1 = s.top();
            s.pop();
            string op2 = s.top();
            s.pop();
            string temp = op1+op2+prefix[i];
            s.push(temp);
        }
        else{
            s.push(string(1,prefix[i]));
        }
    }
    string postfix="";
    while(!s.empty()){
        postfix += s.top();
        s.pop();
    }
    return postfix;
}

int main(){
    string prefix;
    cin>>prefix;
    cout<<"Prefix to Postfix expression:"<<endl<<preToPost(prefix);
}
```


## Output:
<img width="635" height="293" alt="image" src="https://github.com/user-attachments/assets/73cbb8e5-04bb-4520-9282-d05b2244f1c8" />



## Result:
The Prefix expression was successfully converted into its corresponding Postfix form using STL Stack.
