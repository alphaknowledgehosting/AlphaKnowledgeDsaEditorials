# Queues: Complete Guide

A queue is a linear data structure that follows the First In First Out (FIFO) order, where the element inserted first will be the first one to be removed. This is similar to a real-world queue where the person who arrives first is served first. 

## Structure of a Queue

A queue maintains two pointers to manage insertions and deletions at opposite ends of the data structure.

**Data Elements**: Stores the actual values in the queue.

**Front Pointer**: Points to the first element in the queue where deletion occurs.

**Rear Pointer**: Points to the last element in the queue where insertion occurs.

**Capacity**: The maximum number of elements the queue can hold (in array implementation).

### Declaration

```cpp
// Queue using array in C++
class Queue {
    int front, rear, size;
    unsigned capacity;
    int* array;
public:
    Queue(unsigned cap) {
        capacity = cap;
        front = size = 0;
        rear = capacity - 1;
        array = new int[capacity];
    }
    bool enqueue(int x);
    int dequeue();
    int getFront();
    int getRear();
    bool isEmpty();
    bool isFull();
};
```

```java
// Queue using array in Java
class Queue {
    int front, rear, size;
    int capacity;
    int[] array;
    
    Queue(int cap) {
        capacity = cap;
        front = size = 0;
        rear = capacity - 1;
        array = new int[capacity];
    }
    
    boolean enqueue(int x);
    int dequeue();
    int getFront();
    int getRear();
    boolean isEmpty();
    boolean isFull();
}
```

```python
# Queue using list in Python
class Queue:
    def __init__(self, capacity):
        self.capacity = capacity
        self.front = 0
        self.size = 0
        self.rear = capacity - 1
        self.array =  [0] * capacity
    
    def enqueue(self, x):
        pass
    
    def dequeue(self):
        pass
    
    def get_front(self):
        pass
    
    def get_rear(self):
        pass
    
    def is_empty(self):
        pass
    
    def is_full(self):
        pass
```


## Advantages

**FIFO Order Processing**: Ensures fair processing where first arrived element is processed first. 

**Efficient Operations**: Enqueue and dequeue operations execute in constant time O(1). 

**Resource Sharing**: Effectively manages shared resources among multiple consumers. 

**Asynchronous Data Transfer**: Handles data transfer between processes at different rates. 

**Breadth First Search**: Essential for BFS traversal in graphs and trees. 

**Real-time Systems**: Useful in operating systems for CPU scheduling and disk scheduling. 

## Disadvantages

**Fixed Size**: Array-based queues have limited capacity leading to overflow. 

**Memory Waste**: Empty spaces at the front cannot be reused in simple array implementation. 

**No Random Access**: Elements can only be accessed from front or rear, not from arbitrary positions. 

**Queue Overflow**: Occurs when inserting elements into a full queue. 

**Queue Underflow**: Occurs when removing from an empty queue. 

## Creating a Queue

### Implementation

```cpp
#include <iostream>
using namespace std;

class Queue {
    int front, rear, size;
    unsigned capacity;
    int* array;
    
public:
    Queue(unsigned cap) {
        capacity = cap;
        front = size = 0;
        rear = capacity - 1;
        array = new int[capacity];
    }
    
    ~Queue() {
        delete[] array;
    }
    
    bool isFull() {
        return (size == capacity);
    }
    
    bool isEmpty() {
        return (size == 0);
    }
    
    void enqueue(int item) {
        if (isFull()) {
            cout << "Queue is full" << endl;
            return;
        }
        rear = (rear + 1) % capacity;
        array[rear] = item;
        size = size + 1;
        cout << item << " enqueued to queue" << endl;
    }
    
    int dequeue() {
        if (isEmpty()) {
            cout << "Queue is empty" << endl;
            return -1;
        }
        int item = array[front];
        front = (front + 1) % capacity;
        size = size - 1;
        return item;
    }
    
    int getFront() {
        if (isEmpty())
            return -1;
        return array[front];
    }
    
    int getRear() {
        if (isEmpty())
            return -1;
        return array[rear];
    }
};
```

```java
class Queue {
    int front, rear, size;
    int capacity;
    int[] array;
    
    Queue(int cap) {
        capacity = cap;
        front = size = 0;
        rear = capacity - 1;
        array = new int[capacity];
    }
    
    boolean isFull() {
        return (size == capacity);
    }
    
    boolean isEmpty() {
        return (size == 0);
    }
    
    void enqueue(int item) {
        if (isFull()) {
            System.out.println("Queue is full");
            return;
        }
        rear = (rear + 1) % capacity;
        array[rear] = item;
        size = size + 1;
        System.out.println(item + " enqueued to queue");
    }
    
    int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue is empty");
            return -1;
        }
        int item = array[front];
        front = (front + 1) % capacity;
        size = size - 1;
        return item;
    }
    
    int getFront() {
        if (isEmpty())
            return -1;
        return array[front];
    }
    
    int getRear() {
        if (isEmpty())
            return -1;
        return array[rear];
    }
}
```

```python
class Queue:
    def __init__(self, capacity):
        self.capacity = capacity
        self.front = 0
        self.size = 0
        self.rear = capacity - 1
        self.array =  [0] * capacity
    
    def is_full(self):
        return self.size == self.capacity
    
    def is_empty(self):
        return self.size == 0
    
    def enqueue(self, item):
        if self.is_full():
            print("Queue is full")
            return
        self.rear = (self.rear + 1) % self.capacity
        self.array[self.rear] = item
        self.size += 1
        print(f"{item} enqueued to queue")
    
    def dequeue(self):
        if self.is_empty():
            print("Queue is empty")
            return -1
        item = self.array[self.front]
        self.front = (self.front + 1) % self.capacity
        self.size -= 1
        return item
    
    def get_front(self):
        if self.is_empty():
            return -1
        return self.array[self.front]
    
    def get_rear(self):
        if self.is_empty():
            return -1
        return self.array[self.rear]
```


## Queue Operations

### Enqueue Operation

```cpp
void Queue::enqueue(int item) {
    if (isFull()) {
        cout << "Queue is full" << endl;
        return;
    }
    rear = (rear + 1) % capacity;
    array[rear] = item;
    size = size + 1;
    cout << item << " enqueued to queue" << endl;
}
```

```java
void enqueue(int item) {
    if (isFull()) {
        System.out.println("Queue is full");
        return;
    }
    rear = (rear + 1) % capacity;
    array[rear] = item;
    size = size + 1;
    System.out.println(item + " enqueued to queue");
}
```

```python
def enqueue(self, item):
    if self.is_full():
        print("Queue is full")
        return
    self.rear = (self.rear + 1) % self.capacity
    self.array[self.rear] = item
    self.size += 1
    print(f"{item} enqueued to queue")
```

**Output:**

```
10 enqueued to queue
```


### Time Complexity

O(1) as the element is directly inserted at the rear using circular increment. 

### Space Complexity

O(1) as no extra space is needed.

### Dequeue Operation

```cpp
int Queue::dequeue() {
    if (isEmpty()) {
        cout << "Queue is empty" << endl;
        return -1;
    }
    int item = array[front];
    front = (front + 1) % capacity;
    size = size - 1;
    return item;
}
```

```java
int dequeue() {
    if (isEmpty()) {
        System.out.println("Queue is empty");
        return -1;
    }
    int item = array[front];
    front = (front + 1) % capacity;
    size = size - 1;
    return item;
}
```

```python
def dequeue(self):
    if self.is_empty():
        print("Queue is empty")
        return -1
    item = self.array[self.front]
    self.front = (self.front + 1) % self.capacity
    self.size -= 1
    return item
```

**Output:**

```
10 dequeued from queue
```


### Time Complexity

O(1) as the element is directly removed from the front using circular increment. 

### Space Complexity

O(1) as no extra space is needed.

### Front Operation

```cpp
int Queue::getFront() {
    if (isEmpty())
        return -1;
    return array[front];
}
```

```java
int getFront() {
    if (isEmpty())
        return -1;
    return array[front];
}
```

```python
def get_front(self):
    if self.is_empty():
        return -1
    return self.array[self.front]
```

**Output:**

```
Front item is 20
```


### Time Complexity

O(1) as we directly access the front element. 

### Space Complexity

O(1) as no extra space is needed.

### Rear Operation

```cpp
int Queue::getRear() {
    if (isEmpty())
        return -1;
    return array[rear];
}
```

```java
int getRear() {
    if (isEmpty())
        return -1;
    return array[rear];
}
```

```python
def get_rear(self):
    if self.is_empty():
        return -1
    return self.array[self.rear]
```

**Output:**

```
Rear item is 40
```


### Time Complexity

O(1) as we directly access the rear element. 

### Space Complexity

O(1) as no extra space is needed.

### isEmpty Operation

```cpp
bool Queue::isEmpty() {
    return (size == 0);
}
```

```java
boolean isEmpty() {
    return (size == 0);
}
```

```python
def is_empty(self):
    return self.size == 0
```


### Time Complexity

O(1) as it is a simple comparison. 

### Space Complexity

O(1) as no extra space is needed.

### isFull Operation

```cpp
bool Queue::isFull() {
    return (size == capacity);
}
```

```java
boolean isFull() {
    return (size == capacity);
}
```

```python
def is_full(self):
    return self.size == self.capacity
```


### Time Complexity

O(1) as it is a simple comparison. 

### Space Complexity

O(1) as no extra space is needed.

## Queue Using Linked List

### Implementation

```cpp
#include <bits/stdc++.h>
using namespace std;

struct QNode {
    int data;
    QNode* next;
    QNode(int d) {
        data = d;
        next = NULL;
    }
};

struct Queue {
    QNode *front, *rear;
    
    Queue() {
        front = rear = NULL;
    }
    
    void enQueue(int x) {
        QNode* temp = new QNode(x);
        
        if (rear == NULL) {
            front = rear = temp;
            cout << x << " enqueued to queue" << endl;
            return;
        }
        
        rear->next = temp;
        rear = temp;
        cout << x << " enqueued to queue" << endl;
    }
    
    void deQueue() {
        if (front == NULL) {
            cout << "Queue is empty" << endl;
            return;
        }
        
        QNode* temp = front;
        front = front->next;
        
        if (front == NULL)
            rear = NULL;
        
        cout << temp->data << " dequeued from queue" << endl;
        delete(temp);
    }
    
    int getFront() {
        if (front == NULL) {
            cout << "Queue is empty" << endl;
            return -1;
        }
        return front->data;
    }
    
    int getRear() {
        if (rear == NULL) {
            cout << "Queue is empty" << endl;
            return -1;
        }
        return rear->data;
    }
};
```

```java
class QNode {
    int data;
    QNode next;
    
    QNode(int d) {
        data = d;
        next = null;
    }
}

class Queue {
    QNode front, rear;
    
    Queue() {
        front = rear = null;
    }
    
    void enQueue(int x) {
        QNode temp = new QNode(x);
        
        if (rear == null) {
            front = rear = temp;
            System.out.println(x + " enqueued to queue");
            return;
        }
        
        rear.next = temp;
        rear = temp;
        System.out.println(x + " enqueued to queue");
    }
    
    void deQueue() {
        if (front == null) {
            System.out.println("Queue is empty");
            return;
        }
        
        QNode temp = front;
        front = front.next;
        
        if (front == null)
            rear = null;
        
        System.out.println(temp.data + " dequeued from queue");
    }
    
    int getFront() {
        if (front == null) {
            System.out.println("Queue is empty");
            return -1;
        }
        return front.data;
    }
    
    int getRear() {
        if (rear == null) {
            System.out.println("Queue is empty");
            return -1;
        }
        return rear.data;
    }
}
```

```python
class QNode:
    def __init__(self, d):
        self.data = d
        self.next = None

class Queue:
    def __init__(self):
        self.front = None
        self.rear = None
    
    def enqueue(self, x):
        temp = QNode(x)
        
        if self.rear is None:
            self.front = self.rear = temp
            print(f"{x} enqueued to queue")
            return
        
        self.rear.next = temp
        self.rear = temp
        print(f"{x} enqueued to queue")
    
    def dequeue(self):
        if self.front is None:
            print("Queue is empty")
            return
        
        temp = self.front
        self.front = self.front.next
        
        if self.front is None:
            self.rear = None
        
        print(f"{temp.data} dequeued from queue")
    
    def get_front(self):
        if self.front is None:
            print("Queue is empty")
            return -1
        return self.front.data
    
    def get_rear(self):
        if self.rear is None:
            print("Queue is empty")
            return -1
        return self.rear.data
```

**Output:**

```
10 enqueued to queue
20 enqueued to queue
10 dequeued from queue
20 dequeued from queue
30 enqueued to queue
40 enqueued to queue
50 enqueued to queue
30 dequeued from queue
Queue Front : 40
Queue Rear : 50
```


### Time Complexity

O(1) for both enqueue and dequeue operations as we only change pointers. 

### Space Complexity

O(n) where n is the number of elements in the queue.

## Applications

**CPU Scheduling**: Managing processes in operating systems for fair resource allocation. 

**Disk Scheduling**: Handling disk I/O requests in the order they arrive. 

**Breadth First Search**: Essential for BFS traversal in graphs and trees. 

**IO Buffers**: Managing asynchronous data transfer between processes. 

**Printer Spooling**: Managing print jobs in the order they are received. 

**Network Routers**: Managing packets in routers and switches. 

**Mail Queues**: Handling email processing in mail servers. 

**Semaphores**: Managing access to shared resources in operating systems. 

**Keyboard Buffer**: Storing keystrokes until they are processed. 

**Call Center Systems**: Managing customer calls in the order they are received. 

## Complete Implementation

```cpp
#include <iostream>
using namespace std;

class Queue {
    int front, rear, size;
    unsigned capacity;
    int* array;
    
public:
    Queue(unsigned cap) {
        capacity = cap;
        front = size = 0;
        rear = capacity - 1;
        array = new int[capacity];
    }
    
    ~Queue() {
        delete[] array;
    }
    
    bool isFull() {
        return (size == capacity);
    }
    
    bool isEmpty() {
        return (size == 0);
    }
    
    void enqueue(int item) {
        if (isFull()) {
            cout << "Queue is full" << endl;
            return;
        }
        rear = (rear + 1) % capacity;
        array[rear] = item;
        size = size + 1;
        cout << item << " enqueued to queue" << endl;
    }
    
    int dequeue() {
        if (isEmpty()) {
            cout << "Queue is empty" << endl;
            return -1;
        }
        int item = array[front];
        front = (front + 1) % capacity;
        size = size - 1;
        return item;
    }
    
    int getFront() {
        if (isEmpty())
            return -1;
        return array[front];
    }
    
    int getRear() {
        if (isEmpty())
            return -1;
        return array[rear];
    }
};

int main() {
    Queue q(1000);
    
    q.enqueue(10);
    q.enqueue(20);
    q.enqueue(30);
    q.enqueue(40);
    
    cout << q.dequeue() << " dequeued from queue" << endl;
    
    cout << "Front item is " << q.getFront() << endl;
    cout << "Rear item is " << q.getRear() << endl;
    
    return 0;
}
```

```java
class Queue {
    int front, rear, size;
    int capacity;
    int[] array;
    
    Queue(int cap) {
        capacity = cap;
        front = size = 0;
        rear = capacity - 1;
        array = new int[capacity];
    }
    
    boolean isFull() {
        return (size == capacity);
    }
    
    boolean isEmpty() {
        return (size == 0);
    }
    
    void enqueue(int item) {
        if (isFull()) {
            System.out.println("Queue is full");
            return;
        }
        rear = (rear + 1) % capacity;
        array[rear] = item;
        size = size + 1;
        System.out.println(item + " enqueued to queue");
    }
    
    int dequeue() {
        if (isEmpty()) {
            System.out.println("Queue is empty");
            return -1;
        }
        int item = array[front];
        front = (front + 1) % capacity;
        size = size - 1;
        return item;
    }
    
    int getFront() {
        if (isEmpty())
            return -1;
        return array[front];
    }
    
    int getRear() {
        if (isEmpty())
            return -1;
        return array[rear];
    }
    
    public static void main(String[] args) {
        Queue q = new Queue(1000);
        
        q.enqueue(10);
        q.enqueue(20);
        q.enqueue(30);
        q.enqueue(40);
        
        System.out.println(q.dequeue() + " dequeued from queue");
        
        System.out.println("Front item is " + q.getFront());
        System.out.println("Rear item is " + q.getRear());
    }
}
```

```python
class Queue:
    def __init__(self, capacity):
        self.capacity = capacity
        self.front = 0
        self.size = 0
        self.rear = capacity - 1
        self.array =  [0] * capacity
    
    def is_full(self):
        return self.size == self.capacity
    
    def is_empty(self):
        return self.size == 0
    
    def enqueue(self, item):
        if self.is_full():
            print("Queue is full")
            return
        self.rear = (self.rear + 1) % self.capacity
        self.array[self.rear] = item
        self.size += 1
        print(f"{item} enqueued to queue")
    
    def dequeue(self):
        if self.is_empty():
            print("Queue is empty")
            return -1
        item = self.array[self.front]
        self.front = (self.front + 1) % self.capacity
        self.size -= 1
        return item
    
    def get_front(self):
        if self.is_empty():
            return -1
        return self.array[self.front]
    
    def get_rear(self):
        if self.is_empty():
            return -1
        return self.array[self.rear]

# Main program
q = Queue(1000)

q.enqueue(10)
q.enqueue(20)
q.enqueue(30)
q.enqueue(40)

print(f"{q.dequeue()} dequeued from queue")

print(f"Front item is {q.get_front()}")
print(f"Rear item is {q.get_rear()}")
```

**Output:**

```
10 enqueued to queue
20 enqueued to queue
30 enqueued to queue
40 enqueued to queue
10 dequeued from queue
Front item is 20
Rear item is 40
```


## Queue Using Linked List - Complete Example

```cpp
#include <bits/stdc++.h>
using namespace std;

struct QNode {
    int data;
    QNode* next;
    QNode(int d) {
        data = d;
        next = NULL;
    }
};

struct Queue {
    QNode *front, *rear;
    
    Queue() {
        front = rear = NULL;
    }
    
    void enQueue(int x) {
        QNode* temp = new QNode(x);
        
        if (rear == NULL) {
            front = rear = temp;
            cout << x << " enqueued to queue" << endl;
            return;
        }
        
        rear->next = temp;
        rear = temp;
        cout << x << " enqueued to queue" << endl;
    }
    
    void deQueue() {
        if (front == NULL) {
            cout << "Queue is empty" << endl;
            return;
        }
        
        QNode* temp = front;
        cout << temp->data << " dequeued from queue" << endl;
        front = front->next;
        
        if (front == NULL)
            rear = NULL;
        
        delete(temp);
    }
};

int main() {
    Queue q;
    q.enQueue(10);
    q.enQueue(20);
    q.deQueue();
    q.deQueue();
    q.enQueue(30);
    q.enQueue(40);
    q.enQueue(50);
    q.deQueue();
    cout << "Queue Front : " << (q.front)->data << endl;
    cout << "Queue Rear : " << (q.rear)->data << endl;
    
    return 0;
}
```

```java
class QNode {
    int data;
    QNode next;
    
    QNode(int d) {
        data = d;
        next = null;
    }
}

class Queue {
    QNode front, rear;
    
    Queue() {
        front = rear = null;
    }
    
    void enQueue(int x) {
        QNode temp = new QNode(x);
        
        if (rear == null) {
            front = rear = temp;
            System.out.println(x + " enqueued to queue");
            return;
        }
        
        rear.next = temp;
        rear = temp;
        System.out.println(x + " enqueued to queue");
    }
    
    void deQueue() {
        if (front == null) {
            System.out.println("Queue is empty");
            return;
        }
        
        QNode temp = front;
        System.out.println(temp.data + " dequeued from queue");
        front = front.next;
        
        if (front == null)
            rear = null;
    }
    
    public static void main(String[] args) {
        Queue q = new Queue();
        q.enQueue(10);
        q.enQueue(20);
        q.deQueue();
        q.deQueue();
        q.enQueue(30);
        q.enQueue(40);
        q.enQueue(50);
        q.deQueue();
        System.out.println("Queue Front : " + q.front.data);
        System.out.println("Queue Rear : " + q.rear.data);
    }
}
```

```python
class QNode:
    def __init__(self, d):
        self.data = d
        self.next = None

class Queue:
    def __init__(self):
        self.front = None
        self.rear = None
    
    def enqueue(self, x):
        temp = QNode(x)
        
        if self.rear is None:
            self.front = self.rear = temp
            print(f"{x} enqueued to queue")
            return
        
        self.rear.next = temp
        self.rear = temp
        print(f"{x} enqueued to queue")
    
    def dequeue(self):
        if self.front is None:
            print("Queue is empty")
            return
        
        temp = self.front
        print(f"{temp.data} dequeued from queue")
        self.front = self.front.next
        
        if self.front is None:
            self.rear = None

# Main program
q = Queue()
q.enqueue(10)
q.enqueue(20)
q.dequeue()
q.dequeue()
q.enqueue(30)
q.enqueue(40)
q.enqueue(50)
q.dequeue()
print(f"Queue Front : {q.front.data}")
print(f"Queue Rear : {q.rear.data}")
```

**Output:**

```
10 enqueued to queue
20 enqueued to queue
10 dequeued from queue
20 dequeued from queue
30 enqueued to queue
40 enqueued to queue
50 enqueued to queue
30 dequeued from queue
Queue Front : 40
Queue Rear : 50
```

This comprehensive editorial covers queues following the doubly linked list format with complete code implementations in C++, Java, and Python, including a single output for each section after all three language codes.