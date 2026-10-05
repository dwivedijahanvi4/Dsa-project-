# Dsa-project-
Stack circular queue 
question = 1
#include <iostream>
using namespace std;

#define SIZE 5

class Stack
{
    int arr[SIZE];
    int top;

public:
    Stack()
    {
        top = -1;
    }

    // PUSH operation
    void push(int x)
    {
        if (top == SIZE - 1)
        {
            cout << "Stack Overflow!" << endl;
            return;
        }

        top++;
        arr[top] = x;
        cout << x << " pushed into stack." << endl;
    }

    // POP operation
    void pop()
    {
        if (top == -1)
        {
            cout << "Stack Underflow!" << endl;
            return;
        }

        cout << arr[top] << " popped from stack." << endl;
        top--;
    }

    // PEEK operation
    void peek()
    {
        if (top == -1)
        {
            cout << "Stack is empty!" << endl;
            return;
        }

        cout << "Top element = " << arr[top] << endl;
    }

    // DISPLAY operation
    void display()
    {
        if (top == -1)
        {
            cout << "Stack is empty!" << endl;
            return;
        }

        cout << "Stack elements: ";

        for (int i = top; i >= 0; i--)
        {
            cout << arr[i] << " ";
        }

        cout << endl;
    }
};

int main()
{
    Stack s;

    s.push(10);
    s.push(20);
    s.push(30);
    s.push(40);
    s.push(50);

    s.display();

    s.peek();

    s.pop();
    s.pop();

    s.display();

    s.peek();

    return 0;
}

10 pushed into stack.
20 pushed into stack.
30 pushed into stack.
40 pushed into stack.
50 pushed into stack.
Stack elements: 50 40 30 20 10
Top element = 50
50 popped from stack.
40 popped from stack.
Stack elements: 30 20 10
Top element = 30


question 2 = 
#include <iostream>
using namespace std;

#define SIZE 5

class CircularQueue
{
    int arr[SIZE];
    int front, rear;

public:
    CircularQueue()
    {
        front = -1;
        rear = -1;
    }

    // ENQUEUE operation
    void enqueue(int x)
    {
        // Queue is full
        if ((rear + 1) % SIZE == front)
        {
            cout << "Queue Overflow! Queue is full." << endl;
            return;
        }

        // First element
        if (front == -1)
        {
            front = 0;
            rear = 0;
        }
        else
        {
            rear = (rear + 1) % SIZE;
        }

        arr[rear] = x;

        cout << x << " inserted into queue." << endl;
    }

    // DEQUEUE operation
    void dequeue()
    {
        if (front == -1)
        {
            cout << "Queue Underflow! Queue is empty." << endl;
            return;
        }

        cout << arr[front] << " deleted from queue." << endl;

        // Only one element was present
        if (front == rear)
        {
            front = -1;
            rear = -1;
        }
        else
        {
            front = (front + 1) % SIZE;
        }
    }

    // FRONT operation
    void getFront()
    {
        if (front == -1)
        {
            cout << "Queue is empty." << endl;
            return;
        }

        cout << "Front element = " << arr[front] << endl;
    }

    // DISPLAY operation
    void display()
    {
        if (front == -1)
        {
            cout << "Queue is empty." << endl;
            return;
        }

        cout << "Queue elements: ";

        int i = front;

        while (true)
        {
            cout << arr[i] << " ";

            if (i == rear)
                break;

            i = (i + 1) % SIZE;
        }

        cout << endl;
    }
};

int main()
{
    CircularQueue q;

    q.enqueue(10);
    q.enqueue(20);
    q.enqueue(30);
    q.enqueue(40);
    q.enqueue(50);

    q.display();

    q.getFront();

    q.dequeue();
    q.dequeue();

    q.display();

    q.enqueue(60);
    q.enqueue(70);

    q.display();

    q.getFront();

    return 0;
}

output 
10 inserted into queue.
20 inserted into queue.
30 inserted into queue.
40 inserted into queue.
50 inserted into queue.

Queue elements: 10 20 30 40 50
Front element = 10

10 deleted from queue.
20 deleted from queue.

Queue elements: 30 40 50

60 inserted into queue.
70 inserted into queue.

Queue elements: 30 40 50 60 70
Front element = 30
