# Deque: Complete Guide

A deque (Double Ended Queue) is a generalized version of the queue data structure that allows insertion and deletion operations at both the front and rear ends. Unlike a standard queue that follows FIFO order, a deque provides flexibility to add or remove elements from either end. 

## Structure of a Deque

A deque maintains two pointers to manage insertions and deletions at both ends of the data structure.

**Data Elements**: Stores the actual values in the deque.

**Front Pointer**: Points to the first element in the deque where insertion and deletion can occur.

**Rear Pointer**: Points to the last element in the deque where insertion and deletion can occur.

**Capacity**: The maximum number of elements the deque can hold (in array implementation).

### Declaration

```cpp
// Deque using circular array in C++
class Deque {
    int arr[MAX];
    int front;
    int rear;
    int size;
public:
    Deque(int size) {
        front = -1;
        rear = 0;
        this->size = size;
    }
    void insertfront(int key);
    void insertrear(int key);
    void deletefront();
    void deleterear();
    bool isFull();
    bool isEmpty();
    int getFront();
    int getRear();
};
```

```java
// Deque using circular array in Java
class Deque {
    int[] arr;
    int front;
    int rear;
    int size;
    int capacity;
    
    Deque(int cap) {
        capacity = cap;
        arr = new int[capacity];
        front = -1;
        rear = 0;
        size = 0;
    }
    
    void insertFront(int key);
    void insertRear(int key);
    void deleteFront();
    void deleteRear();
    boolean isFull();
    boolean isEmpty();
    int getFront();
    int getRear();
}
```

```python
# Deque using list in Python
class Deque:
    def __init__(self, capacity):
        self.capacity = capacity
        self.arr = [0] * capacity
        self.front = -1
        self.rear = 0
        self.size = 0
    
    def insert_front(self, key):
        pass
    
    def insert_rear(self, key):
        pass
    
    def delete_front(self):
        pass
    
    def delete_rear(self):
        pass
    
    def is_full(self):
        pass
    
    def is_empty(self):
        pass
    
    def get_front(self):
        pass
    
    def get_rear(self):
        pass
```


## Advantages

**Dual-ended Operations**: Supports insertion and deletion at both ends in O(1) time. 

**Versatility**: Can function as both stack and queue data structures.[2]

**Efficient Rotations**: Supports clockwise and anticlockwise rotations in O(1) time.[2]

**Sliding Window Problems**: Ideal for problems requiring elements to be added or removed from both ends.[2]

**Undo Operations**: Efficiently stores undo operations in software applications.[2]

**Browser History**: Suitable for storing web browser history with forward and backward navigation.[2]

## Disadvantages

**Fixed Size**: Array-based deques have limited capacity leading to overflow.[2]

**Complexity**: More complex implementation compared to standard queues or stacks. 

**No Random Access**: Elements cannot be accessed from arbitrary positions in linked list implementation. 

**Memory Overhead**: Doubly linked list implementation requires extra memory for pointers. 

**Overflow and Underflow**: Occurs when inserting into a full deque or deleting from an empty deque.[2]

## Creating a Deque

### Implementation

```cpp
#include <iostream>
#define MAX 100
using namespace std;

class Deque {
    int arr[MAX];
    int front;
    int rear;
    int size;
    
public:
    Deque(int size) {
        front = -1;
        rear = 0;
        this->size = size;
    }
    
    bool isFull() {
        return ((front == 0 && rear == size - 1) || 
                front == rear + 1);
    }
    
    bool isEmpty() {
        return (front == -1);
    }
    
    void insertfront(int key) {
        if (isFull()) {
            cout << "Overflow" << endl;
            return;
        }
        
        if (front == -1) {
            front = 0;
            rear = 0;
        }
        else if (front == 0)
            front = size - 1;
        else
            front = front - 1;
        
        arr[front] = key;
    }
    
    void insertrear(int key) {
        if (isFull()) {
            cout << "Overflow" << endl;
            return;
        }
        
        if (front == -1) {
            front = 0;
            rear = 0;
        }
        else if (rear == size - 1)
            rear = 0;
        else
            rear = rear + 1;
        
        arr[rear] = key;
    }
    
    void deletefront() {
        if (isEmpty()) {
            cout << "Queue Underflow" << endl;
            return;
        }
        
        if (front == rear) {
            front = -1;
            rear = -1;
        }
        else if (front == size - 1)
            front = 0;
        else
            front = front + 1;
    }
    
    void deleterear() {
        if (isEmpty()) {
            cout << "Underflow" << endl;
            return;
        }
        
        if (front == rear) {
            front = -1;
            rear = -1;
        }
        else if (rear == 0)
            rear = size - 1;
        else
            rear = rear - 1;
    }
    
    int getFront() {
        if (isEmpty()) {
            cout << "Underflow" << endl;
            return -1;
        }
        return arr[front];
    }
    
    int getRear() {
        if (isEmpty() || rear < 0) {
            cout << "Underflow" << endl;
            return -1;
        }
        return arr[rear];
    }
};
```

```java
class Deque {
    int[] arr;
    int front;
    int rear;
    int size;
    int capacity;
    
    Deque(int cap) {
        capacity = cap;
        arr = new int[capacity];
        front = -1;
        rear = 0;
        size = 0;
    }
    
    boolean isFull() {
        return ((front == 0 && rear == capacity - 1) || 
                front == rear + 1);
    }
    
    boolean isEmpty() {
        return (front == -1);
    }
    
    void insertFront(int key) {
        if (isFull()) {
            System.out.println("Overflow");
            return;
        }
        
        if (front == -1) {
            front = 0;
            rear = 0;
        }
        else if (front == 0)
            front = capacity - 1;
        else
            front = front - 1;
        
        arr[front] = key;
    }
    
    void insertRear(int key) {
        if (isFull()) {
            System.out.println("Overflow");
            return;
        }
        
        if (front == -1) {
            front = 0;
            rear = 0;
        }
        else if (rear == capacity - 1)
            rear = 0;
        else
            rear = rear + 1;
        
        arr[rear] = key;
    }
    
    void deleteFront() {
        if (isEmpty()) {
            System.out.println("Queue Underflow");
            return;
        }
        
        if (front == rear) {
            front = -1;
            rear = -1;
        }
        else if (front == capacity - 1)
            front = 0;
        else
            front = front + 1;
    }
    
    void deleteRear() {
        if (isEmpty()) {
            System.out.println("Underflow");
            return;
        }
        
        if (front == rear) {
            front = -1;
            rear = -1;
        }
        else if (rear == 0)
            rear = capacity - 1;
        else
            rear = rear - 1;
    }
    
    int getFront() {
        if (isEmpty()) {
            System.out.println("Underflow");
            return -1;
        }
        return arr[front];
    }
    
    int getRear() {
        if (isEmpty() || rear < 0) {
            System.out.println("Underflow");
            return -1;
        }
        return arr[rear];
    }
}
```

```python
class Deque:
    def __init__(self, capacity):
        self.capacity = capacity
        self.arr = [0] * capacity
        self.front = -1
        self.rear = 0
    
    def is_full(self):
        return ((self.front == 0 and self.rear == self.capacity - 1) or 
                self.front == self.rear + 1)
    
    def is_empty(self):
        return self.front == -1
    
    def insert_front(self, key):
        if self.is_full():
            print("Overflow")
            return
        
        if self.front == -1:
            self.front = 0
            self.rear = 0
        elif self.front == 0:
            self.front = self.capacity - 1
        else:
            self.front = self.front - 1
        
        self.arr[self.front] = key
    
    def insert_rear(self, key):
        if self.is_full():
            print("Overflow")
            return
        
        if self.front == -1:
            self.front = 0
            self.rear = 0
        elif self.rear == self.capacity - 1:
            self.rear = 0
        else:
            self.rear = self.rear + 1
        
        self.arr[self.rear] = key
    
    def delete_front(self):
        if self.is_empty():
            print("Queue Underflow")
            return
        
        if self.front == self.rear:
            self.front = -1
            self.rear = -1
        elif self.front == self.capacity - 1:
            self.front = 0
        else:
            self.front = self.front + 1
    
    def delete_rear(self):
        if self.is_empty():
            print("Underflow")
            return
        
        if self.front == self.rear:
            self.front = -1
            self.rear = -1
        elif self.rear == 0:
            self.rear = self.capacity - 1
        else:
            self.rear = self.rear - 1
    
    def get_front(self):
        if self.is_empty():
            print("Underflow")
            return -1
        return self.arr[self.front]
    
    def get_rear(self):
        if self.is_empty() or self.rear < 0:
            print("Underflow")
            return -1
        return self.arr[self.rear]
```


## Deque Operations

### Insert at Front

```cpp
void Deque::insertfront(int key) {
    if (isFull()) {
        cout << "Overflow" << endl;
        return;
    }
    
    if (front == -1) {
        front = 0;
        rear = 0;
    }
    else if (front == 0)
        front = size - 1;
    else
        front = front - 1;
    
    arr[front] = key;
}
```

```java
void insertFront(int key) {
    if (isFull()) {
        System.out.println("Overflow");
        return;
    }
    
    if (front == -1) {
        front = 0;
        rear = 0;
    }
    else if (front == 0)
        front = capacity - 1;
    else
        front = front - 1;
    
    arr[front] = key;
}
```

```python
def insert_front(self, key):
    if self.is_full():
        print("Overflow")
        return
    
    if self.front == -1:
        self.front = 0
        self.rear = 0
    elif self.front == 0:
        self.front = self.capacity - 1
    else:
        self.front = self.front - 1
    
    self.arr[self.front] = key
```

**Output:**

```
inserting element at front end
```


### Time Complexity

O(1) as the element is directly inserted at the front using circular array indexing.[2]

### Space Complexity

O(1) as no extra space is needed.

### Insert at Rear

```cpp
void Deque::insertrear(int key) {
    if (isFull()) {
        cout << "Overflow" << endl;
        return;
    }
    
    if (front == -1) {
        front = 0;
        rear = 0;
    }
    else if (rear == size - 1)
        rear = 0;
    else
        rear = rear + 1;
    
    arr[rear] = key;
}
```

```java
void insertRear(int key) {
    if (isFull()) {
        System.out.println("Overflow");
        return;
    }
    
    if (front == -1) {
        front = 0;
        rear = 0;
    }
    else if (rear == capacity - 1)
        rear = 0;
    else
        rear = rear + 1;
    
    arr[rear] = key;
}
```

```python
def insert_rear(self, key):
    if self.is_full():
        print("Overflow")
        return
    
    if self.front == -1:
        self.front = 0
        self.rear = 0
    elif self.rear == self.capacity - 1:
        self.rear = 0
    else:
        self.rear = self.rear + 1
    
    self.arr[self.rear] = key
```

**Output:**

```
insert element at rear end  : 5
insert element at rear end : 10
```


### Time Complexity

O(1) as the element is directly inserted at the rear using circular array indexing.[2]

### Space Complexity

O(1) as no extra space is needed.

### Delete from Front

```cpp
void Deque::deletefront() {
    if (isEmpty()) {
        cout << "Queue Underflow" << endl;
        return;
    }
    
    if (front == rear) {
        front = -1;
        rear = -1;
    }
    else if (front == size - 1)
        front = 0;
    else
        front = front + 1;
}
```

```java
void deleteFront() {
    if (isEmpty()) {
        System.out.println("Queue Underflow");
        return;
    }
    
    if (front == rear) {
        front = -1;
        rear = -1;
    }
    else if (front == capacity - 1)
        front = 0;
    else
        front = front + 1;
}
```

```python
def delete_front(self):
    if self.is_empty():
        print("Queue Underflow")
        return
    
    if self.front == self.rear:
        self.front = -1
        self.rear = -1
    elif self.front == self.capacity - 1:
        self.front = 0
    else:
        self.front = self.front + 1
```

**Output:**

```
After delete front element new front become : 5
```


### Time Complexity

O(1) as the element is directly removed from the front using circular array indexing.[2]

### Space Complexity

O(1) as no extra space is needed.

### Delete from Rear

```cpp
void Deque::deleterear() {
    if (isEmpty()) {
        cout << "Underflow" << endl;
        return;
    }
    
    if (front == rear) {
        front = -1;
        rear = -1;
    }
    else if (rear == 0)
        rear = size - 1;
    else
        rear = rear - 1;
}
```

```java
void deleteRear() {
    if (isEmpty()) {
        System.out.println("Underflow");
        return;
    }
    
    if (front == rear) {
        front = -1;
        rear = -1;
    }
    else if (rear == 0)
        rear = capacity - 1;
    else
        rear = rear - 1;
}
```

```python
def delete_rear(self):
    if self.is_empty():
        print("Underflow")
        return
    
    if self.front == self.rear:
        self.front = -1
        self.rear = -1
    elif self.rear == 0:
        self.rear = self.capacity - 1
    else:
        self.rear = self.rear - 1
```

**Output:**

```
After delete rear element new rear become : 5
```


### Time Complexity

O(1) as the element is directly removed from the rear using circular array indexing.[2]

### Space Complexity

O(1) as no extra space is needed.

### Get Front

```cpp
int Deque::getFront() {
    if (isEmpty()) {
        cout << "Underflow" << endl;
        return -1;
    }
    return arr[front];
}
```

```java
int getFront() {
    if (isEmpty()) {
        System.out.println("Underflow");
        return -1;
    }
    return arr[front];
}
```

```python
def get_front(self):
    if self.is_empty():
        print("Underflow")
        return -1
    return self.arr[self.front]
```

**Output:**

```
get front element : 15
```


### Time Complexity

O(1) as we directly access the front element.[2]

### Space Complexity

O(1) as no extra space is needed.

### Get Rear

```cpp
int Deque::getRear() {
    if (isEmpty() || rear < 0) {
        cout << "Underflow" << endl;
        return -1;
    }
    return arr[rear];
}
```

```java
int getRear() {
    if (isEmpty() || rear < 0) {
        System.out.println("Underflow");
        return -1;
    }
    return arr[rear];
}
```

```python
def get_rear(self):
    if self.is_empty() or self.rear < 0:
        print("Underflow")
        return -1
    return self.arr[self.rear]
```

**Output:**

```
get rear element : 10
```


### Time Complexity

O(1) as we directly access the rear element.[2]

### Space Complexity

O(1) as no extra space is needed.

### isEmpty Operation

```cpp
bool Deque::isEmpty() {
    return (front == -1);
}
```

```java
boolean isEmpty() {
    return (front == -1);
}
```

```python
def is_empty(self):
    return self.front == -1
```


### Time Complexity

O(1) as it is a simple comparison.[2]

### Space Complexity

O(1) as no extra space is needed.

### isFull Operation

```cpp
bool Deque::isFull() {
    return ((front == 0 && rear == size - 1) || 
            front == rear + 1);
}
```

```java
boolean isFull() {
    return ((front == 0 && rear == capacity - 1) || 
            front == rear + 1);
}
```

```python
def is_full(self):
    return ((self.front == 0 and self.rear == self.capacity - 1) or 
            self.front == self.rear + 1)
```


### Time Complexity

O(1) as it is a simple comparison.[2]

### Space Complexity

O(1) as no extra space is needed.

## Applications

**Stack and Queue Operations**: Can function as both stack and queue data structures.[2]

**Sliding Window Maximum**: Efficiently solves the maximum of all subarrays of size k problem.[2]

**0-1 BFS**: Used in breadth-first search on graphs with edge weights 0 or 1.[2]

**Browser History**: Stores web browser history with forward and backward navigation.[2]

**Undo Operations**: Manages undo operations in software applications.[2]

**Job Scheduling**: Used in A-Steal job scheduling algorithm where deletions are required at both ends. [2]

**Palindrome Checking**: Efficiently checks if a string is a palindrome by comparing elements from both ends. 

**Task Management**: Manages tasks in operating systems where priority can change dynamically.[2]

## Complete Implementation

```cpp
#include <iostream>
#define MAX 100
using namespace std;

class Deque {
    int arr[MAX];
    int front;
    int rear;
    int size;
    
public:
    Deque(int size) {
        front = -1;
        rear = 0;
        this->size = size;
    }
    
    bool isFull() {
        return ((front == 0 && rear == size - 1) || 
                front == rear + 1);
    }
    
    bool isEmpty() {
        return (front == -1);
    }
    
    void insertfront(int key) {
        if (isFull()) {
            cout << "Overflow" << endl;
            return;
        }
        
        if (front == -1) {
            front = 0;
            rear = 0;
        }
        else if (front == 0)
            front = size - 1;
        else
            front = front - 1;
        
        arr[front] = key;
    }
    
    void insertrear(int key) {
        if (isFull()) {
            cout << "Overflow" << endl;
            return;
        }
        
        if (front == -1) {
            front = 0;
            rear = 0;
        }
        else if (rear == size - 1)
            rear = 0;
        else
            rear = rear + 1;
        
        arr[rear] = key;
    }
    
    void deletefront() {
        if (isEmpty()) {
            cout << "Queue Underflow" << endl;
            return;
        }
        
        if (front == rear) {
            front = -1;
            rear = -1;
        }
        else if (front == size - 1)
            front = 0;
        else
            front = front + 1;
    }
    
    void deleterear() {
        if (isEmpty()) {
            cout << "Underflow" << endl;
            return;
        }
        
        if (front == rear) {
            front = -1;
            rear = -1;
        }
        else if (rear == 0)
            rear = size - 1;
        else
            rear = rear - 1;
    }
    
    int getFront() {
        if (isEmpty()) {
            cout << "Underflow" << endl;
            return -1;
        }
        return arr[front];
    }
    
    int getRear() {
        if (isEmpty() || rear < 0) {
            cout << "Underflow" << endl;
            return -1;
        }
        return arr[rear];
    }
};

int main() {
    Deque dq(5);
    cout << "Insert element at rear end  : 5" << endl;
    dq.insertrear(5);
    
    cout << "insert element at rear end : 10" << endl;
    dq.insertrear(10);
    
    cout << "get rear element " << dq.getRear() << endl;
    
    dq.deleterear();
    cout << "After delete rear element new rear become " 
         << dq.getRear() << endl;
    
    cout << "inserting element at front end" << endl;
    dq.insertfront(15);
    
    cout << "get front element " << dq.getFront() << endl;
    
    dq.deletefront();
    
    cout << "After delete front element new front become " 
         << dq.getFront() << endl;
    
    return 0;
}
```

```java
class Deque {
    int[] arr;
    int front;
    int rear;
    int size;
    int capacity;
    
    Deque(int cap) {
        capacity = cap;
        arr = new int[capacity];
        front = -1;
        rear = 0;
        size = 0;
    }
    
    boolean isFull() {
        return ((front == 0 && rear == capacity - 1) || 
                front == rear + 1);
    }
    
    boolean isEmpty() {
        return (front == -1);
    }
    
    void insertFront(int key) {
        if (isFull()) {
            System.out.println("Overflow");
            return;
        }
        
        if (front == -1) {
            front = 0;
            rear = 0;
        }
        else if (front == 0)
            front = capacity - 1;
        else
            front = front - 1;
        
        arr[front] = key;
    }
    
    void insertRear(int key) {
        if (isFull()) {
            System.out.println("Overflow");
            return;
        }
        
        if (front == -1) {
            front = 0;
            rear = 0;
        }
        else if (rear == capacity - 1)
            rear = 0;
        else
            rear = rear + 1;
        
        arr[rear] = key;
    }
    
    void deleteFront() {
        if (isEmpty()) {
            System.out.println("Queue Underflow");
            return;
        }
        
        if (front == rear) {
            front = -1;
            rear = -1;
        }
        else if (front == capacity - 1)
            front = 0;
        else
            front = front + 1;
    }
    
    void deleteRear() {
        if (isEmpty()) {
            System.out.println("Underflow");
            return;
        }
        
        if (front == rear) {
            front = -1;
            rear = -1;
        }
        else if (rear == 0)
            rear = capacity - 1;
        else
            rear = rear - 1;
    }
    
    int getFront() {
        if (isEmpty()) {
            System.out.println("Underflow");
            return -1;
        }
        return arr[front];
    }
    
    int getRear() {
        if (isEmpty() || rear < 0) {
            System.out.println("Underflow");
            return -1;
        }
        return arr[rear];
    }
    
    public static void main(String[] args) {
        Deque dq = new Deque(5);
        System.out.println("Insert element at rear end  : 5");
        dq.insertRear(5);
        
        System.out.println("insert element at rear end : 10");
        dq.insertRear(10);
        
        System.out.println("get rear element " + dq.getRear());
        
        dq.deleteRear();
        System.out.println("After delete rear element new rear become " 
                         + dq.getRear());
        
        System.out.println("inserting element at front end");
        dq.insertFront(15);
        
        System.out.println("get front element " + dq.getFront());
        
        dq.deleteFront();
        
        System.out.println("After delete front element new front become " 
                         + dq.getFront());
    }
}
```

```python
class Deque:
    def __init__(self, capacity):
        self.capacity = capacity
        self.arr = [0] * capacity
        self.front = -1
        self.rear = 0
    
    def is_full(self):
        return ((self.front == 0 and self.rear == self.capacity - 1) or 
                self.front == self.rear + 1)
    
    def is_empty(self):
        return self.front == -1
    
    def insert_front(self, key):
        if self.is_full():
            print("Overflow")
            return
        
        if self.front == -1:
            self.front = 0
            self.rear = 0
        elif self.front == 0:
            self.front = self.capacity - 1
        else:
            self.front = self.front - 1
        
        self.arr[self.front] = key
    
    def insert_rear(self, key):
        if self.is_full():
            print("Overflow")
            return
        
        if self.front == -1:
            self.front = 0
            self.rear = 0
        elif self.rear == self.capacity - 1:
            self.rear = 0
        else:
            self.rear = self.rear + 1
        
        self.arr[self.rear] = key
    
    def delete_front(self):
        if self.is_empty():
            print("Queue Underflow")
            return
        
        if self.front == self.rear:
            self.front = -1
            self.rear = -1
        elif self.front == self.capacity - 1:
            self.front = 0
        else:
            self.front = self.front + 1
    
    def delete_rear(self):
        if self.is_empty():
            print("Underflow")
            return
        
        if self.front == self.rear:
            self.front = -1
            self.rear = -1
        elif self.rear == 0:
            self.rear = self.capacity - 1
        else:
            self.rear = self.rear - 1
    
    def get_front(self):
        if self.is_empty():
            print("Underflow")
            return -1
        return self.arr[self.front]
    
    def get_rear(self):
        if self.is_empty() or self.rear < 0:
            print("Underflow")
            return -1
        return self.arr[self.rear]

# Main program
dq = Deque(5)
print("Insert element at rear end  : 5")
dq.insert_rear(5)

print("insert element at rear end : 10")
dq.insert_rear(10)

print(f"get rear element {dq.get_rear()}")

dq.delete_rear()
print(f"After delete rear element new rear become {dq.get_rear()}")

print("inserting element at front end")
dq.insert_front(15)

print(f"get front element {dq.get_front()}")

dq.delete_front()

print(f"After delete front element new front become {dq.get_front()}")
```

**Output:**

```
Insert element at rear end  : 5
insert element at rear end : 10
get rear element : 10
After delete rear element new rear become : 5
inserting element at front end
get front element : 15
After delete front element new front become : 5
```

This comprehensive editorial covers deque following the doubly linked list format with complete code implementations in C++, Java, and Python, including a single output for each section after all three language codes.