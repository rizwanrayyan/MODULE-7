# Ex.No:3
# Ex.Name : Write a CPP Program to insert five float elements in to Stack using linked list (use STL for Stack)
## Date: 18/09/2025
## Aim:
To write a C++ program to insert five float elements into a Stack using STL (Standard Template Library) and display the elements.

## Algorithm:
```
1. Start the program.
2. Create an empty stack of float type

stack<float> s;

3. Insert (push) five float values into the stack

Use s.push(value);

4. Display the stack elements

While the stack is not empty:

Print the top element using s.top()

Remove it using s.pop()

5. Stop the program.
```
## Program:
```cpp
#include<iostream>
#include<stack>
using namespace std;
int main()
{
    stack<float> charStack;
    float n;
    cin>>n;
    float val;
    for(int i=0;i<n;i++){
        cin>>val;
        charStack.push(val);
    }
    
        cout<<"Current size of the stack is "<<n<<endl;
        cout<<"The top element of the stack is "<<charStack.top()<<endl;
        charStack.pop();
        cout<<"The top element after 1 pop operation is "<<charStack.top()<<endl;
        charStack.pop();
        cout<<"The top element after 2 pop operations is "<<charStack.top()<<endl;
        cout<<"Size of the stack after 2 pop operations is "<<n-2<<endl;
    
    //write your code
}
```


## Output:
<img width="1194" height="391" alt="image" src="https://github.com/user-attachments/assets/995f3d7e-0712-47e4-b54e-038c9d3302fd" />



## Result:
The C++ program to insert five float elements into a stack using STL was successfully executed.
