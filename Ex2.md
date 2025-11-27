# Ex.No:2
# Ex.Name : Write a CPP Program to implement Queue using Linked List, insert integer elements in to Q and delete two items from Q. 
## Date: 18/09/2025
## Aim: 
To write a C++ program to implement a Queue using Linked List, insert integer elements into the queue, and delete two items from the queue.

## Algorithm:
```
1. Insertion (Enqueue)

Create a new node.

If the queue is empty, set both front and rear to the new node.

Otherwise, link the new node to the end of the queue and update rear.

End.

2. Deletion (Dequeue)

If the queue is empty, display underflow.

Otherwise, delete the node pointed to by front.

Move front to the next node.

If front becomes NULL, set rear = NULL.

End.

3. Display

Traverse from front to rear and print all elements.
```
## Program:
```cpp
#include<iostream>
using namespace std;
struct Node
{
    float data;
    Node *next;
};
 
class Queue{
    public:
    Node *front,*rear;
    Queue(){front=rear=NULL;}
 
    void insert(float n);
    void deleteitem();
    void display();
    ~Queue();
};
 
void Queue::insert(float n)
{
    Node *temp=new Node;
    if(temp==NULL)
    {
        cout<<"Overflow"<<endl;
        return;
    }
    temp->data=n;
    temp->next=NULL;
    
    //for first node
    if(front==NULL){
        front=rear=temp;
    }
    else
    {
        rear->next=temp;
        rear=temp;
    }
    cout<<n<<" ";
}
 
void Queue::display()
{
    if(front==NULL)
    {
        cout<<"Underflow."<<endl;
        return;
    }
    Node *temp=front;
    //will check until NULL is not found
    while(temp)
    {
        cout<<temp->data<<" ";
        temp=temp->next;
    }
    cout<<endl;
}

void Queue :: deleteitem()
    {
    if (front==NULL)
    {
        cout<<"underflow"<<endl;
        return;
    }
    if(front==rear)//if only one node is there
        front=rear=NULL;
    else
        front=front->next;
}
 
Queue ::~Queue()
{
    while(front!=NULL)
    {
        Node *temp=front;
        front=front->next;
        delete temp;
    }
    rear=NULL;
}
 
int main()
{
    int n,i;
    float a[10];
    cin>>n;
    Queue Q;
    Q.display();
    cout<<"Queue :";
 	for(i=0;i<n;i++)
	{
	    cin>>a[i];
	    Q.insert(a[i]);
	}
    cout<<endl;
    Q.deleteitem();
    Q.deleteitem();
    cout<<"After DeQueue :";
    Q.display();
    cout << "Queue Front : " << (Q.front)->data << endl;
    cout << "Queue Rear : " << (Q.rear)->data;
    return 0;
}
```


## Output:
<img width="683" height="381" alt="image" src="https://github.com/user-attachments/assets/0e390d54-830f-4c09-8257-3de1457aafa2" />



## Result:
The Queue was successfully implemented using a linked list.
