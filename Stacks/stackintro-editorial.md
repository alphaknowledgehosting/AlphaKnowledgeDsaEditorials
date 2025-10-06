# Stacks: Complete Guide

A stack is a linear data structure that follows a specific order in which operations are performed. The order is LIFO (Last In First Out) or FILO (First In Last Out), where the element inserted last is the first to be removed. 

## Structure of a Stack

A stack contains elements where insertion and deletion operations occur at one end called the **top** of the stack.

**Data Elements**: Stores the actual values in the stack.

**Top Pointer**: Points to the topmost element in the stack.

**Capacity**: The maximum number of elements the stack can hold (in array implementation).

### Declaration

```cpp
// Stack using array in C++
class Stack {
    int top;
    int arr[MAX];
public:
    Stack() { top = -1; }
    bool push(int x);
    int pop();
    int peek();
    bool isEmpty();
};
```

```java
// Stack using array in Java
class Stack {
    int top;
    int[] arr;
    int capacity;
    
    Stack(int size) {
        arr = new int[size];
        capacity = size;
        top = -1;
    }
    
    boolean push(int x);
    int pop();
    int peek();
    boolean isEmpty();
}
```

```python
# Stack using list in Python
class Stack:
    def __init__(self):
        self.stack = []
    
    def push(self, x):
        self.stack.append(x)
    
    def pop(self):
        if not self.is_empty():
            return self.stack.pop()
    
    def peek(self):
        if not self.is_empty():
            return self.stack[-1]
    
    def is_empty(self):
        return len(self.stack) == 0
```


## Advantages

**Simple Implementation**: Easy to understand and implement using arrays or linked lists. 

**LIFO Management**: Efficiently manages data following Last In First Out principle. 

**Function Call Management**: Enables systematic storage of function parameters and local variables. 

**Memory Efficiency**: Automatic cleanup of objects when they are popped. 

**Fast Operations**: Push, pop, and peek operations execute in constant time. 

**Secure and Reliable**: Data integrity is maintained as access is restricted to the top element. 

## Disadvantages

**Limited Size**: Array-based stacks have fixed capacity leading to stack overflow. 

**No Random Access**: Elements can only be accessed from the top, not from arbitrary positions. 

**Memory Constraints**: Stack size must be defined beforehand in array implementation. 

**Stack Overflow**: Occurs when pushing elements into a full stack. 

**Stack Underflow**: Occurs when popping from an empty stack. 

## Creating a Stack

### Implementation

```cpp
#include <iostream>
#define MAX 1000
using namespace std;

class Stack {
    int top;
public:
    int a[MAX];
    
    Stack() { top = -1; }
    
    bool push(int x) {
        if (top >= (MAX - 1)) {
            cout << "Stack Overflow" << endl;
            return false;
        }
        a[++top] = x;
        cout << x << " pushed into stack" << endl;
        return true;
    }
    
    int pop() {
        if (top < 0) {
            cout << "Stack Underflow" << endl;
            return 0;
        }
        int x = a[top--];
        return x;
    }
    
    int peek() {
        if (top < 0) {
            cout << "Stack is Empty" << endl;
            return 0;
        }
        return a[top];
    }
    
    bool isEmpty() {
        return (top < 0);
    }
};
```

```java
class Stack {
    static final int MAX = 1000;
    int top;
    int a[] = new int[MAX];
    
    Stack() {
        top = -1;
    }
    
    boolean push(int x) {
        if (top >= (MAX - 1)) {
            System.out.println("Stack Overflow");
            return false;
        }
        a[++top] = x;
        System.out.println(x + " pushed into stack");
        return true;
    }
    
    int pop() {
        if (top < 0) {
            System.out.println("Stack Underflow");
            return 0;
        }
        int x = a[top--];
        return x;
    }
    
    int peek() {
        if (top < 0) {
            System.out.println("Stack is Empty");
            return 0;
        }
        return a[top];
    }
    
    boolean isEmpty() {
        return (top < 0);
    }
}
```

```python
class Stack:
    def __init__(self, max_size=1000):
        self.max_size = max_size
        self.stack = []
        self.top = -1
    
    def push(self, x):
        if self.top >= self.max_size - 1:
            print("Stack Overflow")
            return False
        self.stack.append(x)
        self.top += 1
        print(f"{x} pushed into stack")
        return True
    
    def pop(self):
        if self.top < 0:
            print("Stack Underflow")
            return 0
        x = self.stack.pop()
        self.top -= 1
        return x
    
    def peek(self):
        if self.top < 0:
            print("Stack is Empty")
            return 0
        return self.stack[self.top]
    
    def is_empty(self):
        return self.top < 0
```


## Stack Operations

### Push Operation

```cpp
bool Stack::push(int x) {
    if (top >= (MAX - 1)) {
        cout << "Stack Overflow" << endl;
        return false;
    }
    a[++top] = x;
    cout << x << " pushed into stack" << endl;
    return true;
}
```

```java
boolean push(int x) {
    if (top >= (MAX - 1)) {
        System.out.println("Stack Overflow");
        return false;
    }
    a[++top] = x;
    System.out.println(x + " pushed into stack");
    return true;
}
```

```python
def push(self, x):
    if self.top >= self.max_size - 1:
        print("Stack Overflow")
        return False
    self.stack.append(x)
    self.top += 1
    print(f"{x} pushed into stack")
    return True
```

**Output:**

```
10 pushed into stack
```


### Time Complexity

O(1) as the element is directly inserted at the top. 

### Space Complexity

O(1) as no extra space is needed.

### Pop Operation

```cpp
int Stack::pop() {
    if (top < 0) {
        cout << "Stack Underflow" << endl;
        return 0;
    }
    int x = a[top--];
    return x;
}
```

```java
int pop() {
    if (top < 0) {
        System.out.println("Stack Underflow");
        return 0;
    }
    int x = a[top--];
    return x;
}
```

```python
def pop(self):
    if self.top < 0:
        print("Stack Underflow")
        return 0
    x = self.stack.pop()
    self.top -= 1
    return x
```

**Output:**

```
30 Popped from stack
```


### Time Complexity

O(1) as the element is directly removed from the top. 

### Space Complexity

O(1) as no extra space is needed.

### Peek Operation

```cpp
int Stack::peek() {
    if (top < 0) {
        cout << "Stack is Empty" << endl;
        return 0;
    }
    return a[top];
}
```

```java
int peek() {
    if (top < 0) {
        System.out.println("Stack is Empty");
        return 0;
    }
    return a[top];
}
```

```python
def peek(self):
    if self.top < 0:
        print("Stack is Empty")
        return 0
    return self.stack[self.top]
```

**Output:**

```
Top element is: 20
```


### Time Complexity

O(1) as we directly access the top element. 

### Space Complexity

O(1) as no extra space is needed.

### isEmpty Operation

```cpp
bool Stack::isEmpty() {
    return (top < 0);
}
```

```java
boolean isEmpty() {
    return (top < 0);
}
```

```python
def is_empty(self):
    return self.top < 0
```


### Time Complexity

O(1) as it is a simple comparison. 

### Space Complexity

O(1) as no extra space is needed.

## Stack Using Linked List

### Implementation

```cpp
#include <bits/stdc++.h>
using namespace std;

struct StackNode {
    int data;
    struct StackNode* next;
};

StackNode* newNode(int data) {
    StackNode* stackNode = new StackNode();
    stackNode->data = data;
    stackNode->next = NULL;
    return stackNode;
}

int isEmpty(StackNode* root) {
    return !root;
}

void push(StackNode** root, int data) {
    StackNode* stackNode = newNode(data);
    stackNode->next = *root;
    *root = stackNode;
    cout << data << " pushed to stack" << endl;
}

int pop(StackNode** root) {
    if (isEmpty(*root))
        return INT_MIN;
    StackNode* temp = *root;
    *root = (*root)->next;
    int popped = temp->data;
    free(temp);
    return popped;
}

int peek(StackNode* root) {
    if (isEmpty(root))
        return INT_MIN;
    return root->data;
}
```


```java
class StackNode {
    int data;
    StackNode next;
    
    StackNode(int d) {
        data = d;
        next = null;
    }
}

class LinkedStack {
    StackNode root;
    
    boolean isEmpty() {
        return root == null;
    }
    
    void push(int data) {
        StackNode stackNode = new StackNode(data);
        stackNode.next = root;
        root = stackNode;
        System.out.println(data + " pushed to stack");
    }
    
    int pop() {
        if (isEmpty()) {
            System.out.println("Stack Underflow");
            return Integer.MIN_VALUE;
        }
        StackNode temp = root;
        root = root.next;
        int popped = temp.data;
        return popped;
    }
    
    int peek() {
        if (isEmpty()) {
            System.out.println("Stack is Empty");
            return Integer.MIN_VALUE;
        }
        return root.data;
    }
}
```


```python
class StackNode:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedStack:
    def __init__(self):
        self.root = None
    
    def is_empty(self):
        return self.root is None
    
    def push(self, data):
        stack_node = StackNode(data)
        stack_node.next = self.root
        self.root = stack_node
        print(f"{data} pushed to stack")
    
    def pop(self):
        if self.is_empty():
            print("Stack Underflow")
            return float('-inf')
        temp = self.root
        self.root = self.root.next
        popped = temp.data
        return popped
    
    def peek(self):
        if self.is_empty():
            print("Stack is Empty")
            return float('-inf')
        return self.root.data
```

**Output:**

```
10 pushed to stack
20 pushed to stack
30 pushed to stack
30 popped from stack
Top element is 20
```


### Time Complexity

O(1) for all push, pop, and peek operations. 

### Space Complexity

O(n) where n is the number of elements in the stack.

## Applications

**Expression Evaluation**: Evaluating postfix and prefix expressions using stacks. 

**Balancing Parentheses**: Checking for balanced parentheses in expressions. 

**Function Call Management**: Managing function calls, storing activation records, and returning values. 

**Undo/Redo Operations**: Implementing undo and redo features in text editors and applications. 

**Browser Navigation**: Implementing back and forward buttons in web browsers. 

**Backtracking Algorithms**: Used in backtracking problems like N-Queen, maze solving, and Knight's tour. 

**Memory Management**: Managing memory allocation in modern computer systems. 

**String Reversal**: Reversing strings by pushing characters onto the stack. 

**Graph Algorithms**: Used in Depth First Search and topological sorting. 

**Infix to Postfix Conversion**: Converting infix expressions to postfix notation. 

## Complete Implementation

```cpp
#include <iostream>
#define MAX 1000
using namespace std;

class Stack {
    int top;
public:
    int a[MAX];
    
    Stack() { top = -1; }
    
    bool push(int x) {
        if (top >= (MAX - 1)) {
            cout << "Stack Overflow" << endl;
            return false;
        }
        a[++top] = x;
        cout << x << " pushed into stack" << endl;
        return true;
    }
    
    int pop() {
        if (top < 0) {
            cout << "Stack Underflow" << endl;
            return 0;
        }
        int x = a[top--];
        return x;
    }
    
    int peek() {
        if (top < 0) {
            cout << "Stack is Empty" << endl;
            return 0;
        }
        return a[top];
    }
    
    bool isEmpty() {
        return (top < 0);
    }
};

int main() {
    Stack s;
    s.push(10);
    s.push(20);
    s.push(30);
    
    cout << s.pop() << " Popped from stack" << endl;
    
    cout << "Top element is: " << s.peek() << endl;
    
    cout << "Elements present in stack: ";
    while (!s.isEmpty()) {
        cout << s.peek() << " ";
        s.pop();
    }
    
    return 0;
}
```


```java
class Stack {
    static final int MAX = 1000;
    int top;
    int a[] = new int[MAX];
    
    Stack() {
        top = -1;
    }
    
    boolean push(int x) {
        if (top >= (MAX - 1)) {
            System.out.println("Stack Overflow");
            return false;
        }
        a[++top] = x;
        System.out.println(x + " pushed into stack");
        return true;
    }
    
    int pop() {
        if (top < 0) {
            System.out.println("Stack Underflow");
            return 0;
        }
        int x = a[top--];
        return x;
    }
    
    int peek() {
        if (top < 0) {
            System.out.println("Stack is Empty");
            return 0;
        }
        return a[top];
    }
    
    boolean isEmpty() {
        return (top < 0);
    }
    
    public static void main(String[] args) {
        Stack s = new Stack();
        s.push(10);
        s.push(20);
        s.push(30);
        
        System.out.println(s.pop() + " Popped from stack");
        
        System.out.println("Top element is: " + s.peek());
        
        System.out.print("Elements present in stack: ");
        while (!s.isEmpty()) {
            System.out.print(s.peek() + " ");
            s.pop();
        }
    }
}
```


```python
class Stack:
    def __init__(self, max_size=1000):
        self.max_size = max_size
        self.stack = []
        self.top = -1
    
    def push(self, x):
        if self.top >= self.max_size - 1:
            print("Stack Overflow")
            return False
        self.stack.append(x)
        self.top += 1
        print(f"{x} pushed into stack")
        return True
    
    def pop(self):
        if self.top < 0:
            print("Stack Underflow")
            return 0
        x = self.stack.pop()
        self.top -= 1
        return x
    
    def peek(self):
        if self.top < 0:
            print("Stack is Empty")
            return 0
        return self.stack[self.top]
    
    def is_empty(self):
        return self.top < 0

# Main program
s = Stack()
s.push(10)
s.push(20)
s.push(30)

print(f"{s.pop()} Popped from stack")

print(f"Top element is: {s.peek()}")

print("Elements present in stack: ", end="")
while not s.is_empty():
    print(s.peek(), end=" ")
    s.pop()
```

**Output:**

```
10 pushed into stack
20 pushed into stack
30 pushed into stack
30 Popped from stack
Top element is: 20
Elements present in stack: 20 10
```

