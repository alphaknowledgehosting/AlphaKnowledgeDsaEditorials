### Circular Linked List: Complete Guide

A circular linked list is a linked list where all nodes are connected to form a circle. The last node points back to the first node, creating a circular structure. This data structure can be implemented as a singly circular linked list or doubly circular linked list.  

## Structure of a Node

Each node in a circular linked list contains two parts:

**Data**: Stores the actual value or information. 

**Next Pointer**: Stores the address of the next node in memory. 

### Implementation

```cpp
struct Node {
    int data;
    struct Node* next;
};
```

```java
class Node {
    int data;
    Node next;
    
    Node(int d) {
        data = d;
    }
}
```

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
```


## Why Point to the Last Node?

Pointing to the last node is advantageous for insertion operations at the beginning or end. If a pointer last points to the last node, then last->next will point to the first node. This approach eliminates the need to traverse the entire list for insertion operations at either end, making them constant time operations regardless of list length.   

## Advantages

**Flexible Starting Point**: Any node can be a starting point, and the whole list can be traversed by starting from any node.  

**Efficient End Operations**: Insertion at the beginning or end takes O(1) time when maintaining a last pointer, unlike regular linked lists. 

**Queue Implementation**: Useful for queue implementation without maintaining separate front and rear pointers.  

**Cyclic Applications**: Ideal for applications that repeatedly cycle through elements, such as operating system process scheduling.  

## Disadvantages

**Infinite Loop Risk**: Improper handling can lead to infinite loops due to the circular nature.  

**Increased Complexity**: More complex implementation compared to singly-linked lists.  

**Difficult Debugging**: More complex pointer relationships make debugging harder. 

**Extra Memory**: Requires additional memory for maintaining the circular structure. 

## Creating a Circular Linked List

### Implementation

```cpp
#include <bits/stdc++.h>
using namespace std;

struct Node {
    int data;
    struct Node* next;
};

int main() {
    struct Node* head = NULL;
    struct Node* second = NULL;
    struct Node* third = NULL;
    
    head = new Node;
    second = new Node;
    third = new Node;
    
    head->data = 1;
    head->next = second;
    
    second->data = 2;
    second->next = third;
    
    third->data = 3;
    third->next = head;
    
    return 0;
}
```

```java
class Node {
    int data;
    Node next;
    
    Node(int d) {
        data = d;
        next = null;
    }
}

public class Main {
    public static void main(String[] args) {
        Node head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);
        
        head.next = second;
        second.next = third;
        third.next = head;
    }
}
```

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

# Create nodes
head = Node(1)
second = Node(2)
third = Node(3)

# Link nodes
head.next = second
second.next = third
third.next = head
```


## Traversal Operations

### Iterative Traversal

```cpp
void traverse(Node* last) {
    if (last == NULL) {
        cout << "List is empty." << endl;
        return;
    }
    
    Node* p = last->next;
    
    do {
        cout << p->data << " ";
        p = p->next;
    } while (p != last->next);
}
```

```java
void traverse(Node last) {
    if (last == null) {
        System.out.println("List is empty.");
        return;
    }
    
    Node p = last.next;
    
    do {
        System.out.print(p.data + " ");
        p = p.next;
    } while (p != last.next);
}
```

```python
def traverse(last):
    if last is None:
        print("List is empty.")
        return
    
    p = last.next
    
    while True:
        print(p.data, end=" ")
        p = p.next
        if p == last.next:
            break
```


### Time Complexity

O(n) where n is the number of nodes in the circular linked list. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

## Insertion Operations

### Insert in Empty List

```cpp
Node* addToEmpty(Node* last, int data) {
    if (last != NULL)
        return last;
    
    Node* newNode = new Node;
    newNode->data = data;
    last = newNode;
    last->next = last;
    
    return last;
}
```

```java
Node addToEmpty(Node last, int data) {
    if (last != null)
        return last;
    
    Node newNode = new Node(data);
    last = newNode;
    last.next = last;
    
    return last;
}
```

```python
def add_to_empty(last, data):
    if last is not None:
        return last
    
    new_node = Node(data)
    last = new_node
    last.next = last
    
    return last
```


### Time Complexity

O(1) as we only need to create a node and set pointers. 

### Space Complexity

O(1) as we only create one new node. 

### Insert at Beginning

```cpp
Node* addBegin(Node* last, int data) {
    if (last == NULL)
        return addToEmpty(last, data);
    
    Node* newNode = new Node;
    newNode->data = data;
    newNode->next = last->next;
    last->next = newNode;
    
    return last;
}
```

```java
Node addBegin(Node last, int data) {
    if (last == null)
        return addToEmpty(last, data);
    
    Node newNode = new Node(data);
    newNode.next = last.next;
    last.next = newNode;
    
    return last;
}
```

```python
def add_begin(last, data):
    if last is None:
        return add_to_empty(last, data)
    
    new_node = Node(data)
    new_node.next = last.next
    last.next = new_node
    
    return last
```


### Time Complexity

O(1) as no traversal is needed. 

### Space Complexity

O(1) as we only create one new node. 

### Insert at End

```cpp
Node* addEnd(Node* last, int data) {
    if (last == NULL)
        return addToEmpty(last, data);
    
    Node* newNode = new Node;
    newNode->data = data;
    newNode->next = last->next;
    last->next = newNode;
    last = newNode;
    
    return last;
}
```

```java
Node addEnd(Node last, int data) {
    if (last == null)
        return addToEmpty(last, data);
    
    Node newNode = new Node(data);
    newNode.next = last.next;
    last.next = newNode;
    last = newNode;
    
    return last;
}
```

```python
def add_end(last, data):
    if last is None:
        return add_to_empty(last, data)
    
    new_node = Node(data)
    new_node.next = last.next
    last.next = new_node
    last = new_node
    
    return last
```


### Time Complexity

O(1) when maintaining a last pointer. 

### Space Complexity

O(1) as we only create one new node. 

### Insert After a Node

```cpp
Node* addAfter(Node* last, int data, int item) {
    if (last == NULL)
        return NULL;
    
    Node* newNode;
    Node* p = last->next;
    
    do {
        if (p->data == item) {
            newNode = new Node;
            newNode->data = data;
            newNode->next = p->next;
            p->next = newNode;
            
            if (p == last)
                last = newNode;
            
            return last;
        }
        p = p->next;
    } while (p != last->next);
    
    cout << item << " not present in the list." << endl;
    return last;
}
```

```java
Node addAfter(Node last, int data, int item) {
    if (last == null)
        return null;
    
    Node newNode;
    Node p = last.next;
    
    do {
        if (p.data == item) {
            newNode = new Node(data);
            newNode.next = p.next;
            p.next = newNode;
            
            if (p == last)
                last = newNode;
            
            return last;
        }
        p = p.next;
    } while (p != last.next);
    
    System.out.println(item + " not present in the list.");
    return last;
}
```

```python
def add_after(last, data, item):
    if last is None:
        return None
    
    p = last.next
    
    while True:
        if p.data == item:
            new_node = Node(data)
            new_node.next = p.next
            p.next = new_node
            
            if p == last:
                last = new_node
            
            return last
        
        p = p.next
        if p == last.next:
            break
    
    print(item, "not present in the list.")
    return last
```


### Time Complexity

O(n) as we may need to traverse the entire list. 

### Space Complexity

O(1) as we only create one new node. 

## Deletion Operations

### Delete First Node

```cpp
void deleteFirst(Node** head) {
    if (*head == NULL) {
        cout << "List is empty" << endl;
        return;
    }
    
    Node* temp = *head;
    
    if (temp->next == temp) {
        *head = NULL;
        delete temp;
        return;
    }
    
    Node* last = *head;
    while (last->next != *head)
        last = last->next;
    
    last->next = temp->next;
    *head = temp->next;
    delete temp;
}
```

```java
Node deleteFirst(Node head) {
    if (head == null) {
        System.out.println("List is empty");
        return null;
    }
    
    Node temp = head;
    
    if (temp.next == temp) {
        head = null;
        return head;
    }
    
    Node last = head;
    while (last.next != head)
        last = last.next;
    
    last.next = temp.next;
    head = temp.next;
    
    return head;
}
```

```python
def delete_first(head):
    if head is None:
        print("List is empty")
        return None
    
    temp = head
    
    if temp.next == temp:
        head = None
        return head
    
    last = head
    while last.next != head:
        last = last.next
    
    last.next = temp.next
    head = temp.next
    
    return head
```


### Time Complexity

O(n) as we need to find the last node. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

### Delete at Kth Position

```cpp
void deleteAtPosition(Node** head, int index) {
    if (*head == NULL) {
        cout << "List is empty" << endl;
        return;
    }
    
    Node* current = *head;
    Node* prev = NULL;
    
    if (index == 0) {
        deleteFirst(head);
        return;
    }
    
    for (int i = 0; i < index; i++) {
        prev = current;
        current = current->next;
        
        if (current == *head) {
            cout << "Index out of bounds" << endl;
            return;
        }
    }
    
    prev->next = current->next;
    delete current;
}
```

```java
Node deleteAtPosition(Node head, int index) {
    if (head == null) {
        System.out.println("List is empty");
        return null;
    }
    
    Node current = head;
    Node prev = null;
    
    if (index == 0) {
        return deleteFirst(head);
    }
    
    for (int i = 0; i < index; i++) {
        prev = current;
        current = current.next;
        
        if (current == head) {
            System.out.println("Index out of bounds");
            return head;
        }
    }
    
    prev.next = current.next;
    
    return head;
}
```

```python
def delete_at_position(head, index):
    if head is None:
        print("List is empty")
        return None
    
    current = head
    prev = None
    
    if index == 0:
        return delete_first(head)
    
    for i in range(index):
        prev = current
        current = current.next
        
        if current == head:
            print("Index out of bounds")
            return head
    
    prev.next = current.next
    
    return head
```


### Time Complexity

O(n) where n is the position of the node to be deleted. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

### Delete Given Node

```cpp
void deleteNode(Node* last, int key) {
    if (last == NULL) {
        cout << "List is empty" << endl;
        return;
    }
    
    if (last->data == key && last->next == last) {
        delete last;
        last = NULL;
        return;
    }
    
    Node* temp = last;
    Node* d = NULL;
    
    if (last->data == key) {
        while (temp->next != last)
            temp = temp->next;
        
        temp->next = last->next;
        delete last;
        last = temp->next;
        return;
    }
    
    while (temp->next != last && temp->next->data != key)
        temp = temp->next;
    
    if (temp->next->data == key) {
        d = temp->next;
        temp->next = d->next;
        delete d;
    }
}
```

```java
Node deleteNode(Node last, int key) {
    if (last == null) {
        System.out.println("List is empty");
        return null;
    }
    
    if (last.data == key && last.next == last) {
        last = null;
        return last;
    }
    
    Node temp = last;
    Node d = null;
    
    if (last.data == key) {
        while (temp.next != last)
            temp = temp.next;
        
        temp.next = last.next;
        last = temp.next;
        return last;
    }
    
    while (temp.next != last && temp.next.data != key)
        temp = temp.next;
    
    if (temp.next.data == key) {
        d = temp.next;
        temp.next = d.next;
    }
    
    return last;
}
```

```python
def delete_node(last, key):
    if last is None:
        print("List is empty")
        return None
    
    if last.data == key and last.next == last:
        last = None
        return last
    
    temp = last
    
    if last.data == key:
        while temp.next != last:
            temp = temp.next
        
        temp.next = last.next
        last = temp.next
        return last
    
    while temp.next != last and temp.next.data != key:
        temp = temp.next
    
    if temp.next.data == key:
        d = temp.next
        temp.next = d.next
    
    return last
```


### Time Complexity

O(n) as we may need to traverse the entire list to find the node. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

## Search Operations

### Iterative Search

```cpp
bool search(Node* last, int key) {
    if (last == NULL)
        return false;
    
    Node* temp = last->next;
    
    do {
        if (temp->data == key)
            return true;
        temp = temp->next;
    } while (temp != last->next);
    
    return false;
}
```

```java
boolean search(Node last, int key) {
    if (last == null)
        return false;
    
    Node temp = last.next;
    
    do {
        if (temp.data == key)
            return true;
        temp = temp.next;
    } while (temp != last.next);
    
    return false;
}
```

```python
def search(last, key):
    if last is None:
        return False
    
    temp = last.next
    
    while True:
        if temp.data == key:
            return True
        temp = temp.next
        if temp == last.next:
            break
    
    return False
```


### Time Complexity

O(n) where n is the number of nodes in the circular linked list. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

### Recursive Search

```cpp
bool searchRecursive(Node* start, Node* last, int key) {
    if (start == NULL)
        return false;
    
    if (start->data == key)
        return true;
    
    if (start == last)
        return false;
    
    return searchRecursive(start->next, last, key);
}
```

```java
boolean searchRecursive(Node start, Node last, int key) {
    if (start == null)
        return false;
    
    if (start.data == key)
        return true;
    
    if (start == last)
        return false;
    
    return searchRecursive(start.next, last, key);
}
```

```python
def search_recursive(start, last, key):
    if start is None:
        return False
    
    if start.data == key:
        return True
    
    if start == last:
        return False
    
    return search_recursive(start.next, last, key)
```


### Time Complexity

O(n) where n is the number of nodes in the circular linked list. 

### Space Complexity

O(n) due to recursive call stack. 

## Applications

**Resource Management**: Used to manage computing resources in operating systems.  

**Process Scheduling**: Operating systems use circular linked lists for Round Robin scheduling.  

**Data Structure Implementation**: Used to implement queues and other data structures.  

**Fibonacci Heap**: Used in implementing advanced data structures like Fibonacci Heap. 

**Media Streaming**: Applied in audio and video streaming applications for continuous playback. 

**Gaming**: Used in Round Robin scheduling technique in multiplayer games.  

**Network Scheduling**: Applied in computer networking for token scheduling.  

## Complete Implementation Example

```cpp
#include<bits/stdc++.h>
using namespace std;

struct Node {
    int data;
    struct Node *next;
};

Node* addToEmpty(Node* last, int data) {
    if (last != NULL)
        return last;
    
    Node* newNode = new Node;
    newNode->data = data;
    last = newNode;
    last->next = last;
    
    return last;
}

Node* addBegin(Node* last, int data) {
    if (last == NULL)
        return addToEmpty(last, data);
    
    Node* newNode = new Node;
    newNode->data = data;
    newNode->next = last->next;
    last->next = newNode;
    
    return last;
}

Node* addEnd(Node* last, int data) {
    if (last == NULL)
        return addToEmpty(last, data);
    
    Node* newNode = new Node;
    newNode->data = data;
    newNode->next = last->next;
    last->next = newNode;
    last = newNode;
    
    return last;
}

void traverse(Node* last) {
    if (last == NULL) {
        cout << "List is empty." << endl;
        return;
    }
    
    Node* p = last->next;
    
    do {
        cout << p->data << " ";
        p = p->next;
    } while (p != last->next);
}

int main() {
    Node *last = NULL;
    
    last = addToEmpty(last, 6);
    last = addBegin(last, 4);
    last = addBegin(last, 2);
    last = addEnd(last, 8);
    last = addEnd(last, 12);
    
    traverse(last);
    
    return 0;
}
```

```java
class Node {
    int data;
    Node next;
    
    Node(int d) {
        data = d;
    }
}

class CircularLinkedList {
    static Node addToEmpty(Node last, int data) {
        if (last != null)
            return last;
        
        Node newNode = new Node(data);
        last = newNode;
        last.next = last;
        
        return last;
    }
    
    static Node addBegin(Node last, int data) {
        if (last == null)
            return addToEmpty(last, data);
        
        Node newNode = new Node(data);
        newNode.next = last.next;
        last.next = newNode;
        
        return last;
    }
    
    static Node addEnd(Node last, int data) {
        if (last == null)
            return addToEmpty(last, data);
        
        Node newNode = new Node(data);
        newNode.next = last.next;
        last.next = newNode;
        last = newNode;
        
        return last;
    }
    
    static void traverse(Node last) {
        if (last == null) {
            System.out.println("List is empty.");
            return;
        }
        
        Node p = last.next;
        
        do {
            System.out.print(p.data + " ");
            p = p.next;
        } while (p != last.next);
    }
    
    public static void main(String[] args) {
        Node last = null;
        
        last = addToEmpty(last, 6);
        last = addBegin(last, 4);
        last = addBegin(last, 2);
        last = addEnd(last, 8);
        last = addEnd(last, 12);
        
        traverse(last);
    }
}
```

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

def add_to_empty(last, data):
    if last is not None:
        return last
    
    new_node = Node(data)
    last = new_node
    last.next = last
    
    return last

def add_begin(last, data):
    if last is None:
        return add_to_empty(last, data)
    
    new_node = Node(data)
    new_node.next = last.next
    last.next = new_node
    
    return last

def add_end(last, data):
    if last is None:
        return add_to_empty(last, data)
    
    new_node = Node(data)
    new_node.next = last.next
    last.next = new_node
    last = new_node
    
    return last

def traverse(last):
    if last is None:
        print("List is empty.")
        return
    
    p = last.next
    
    while True:
        print(p.data, end=" ")
        p = p.next
        if p == last.next:
            break

# Main
last = None

last = add_to_empty(last, 6)
last = add_begin(last, 4)
last = add_begin(last, 2)
last = add_end(last, 8)
last = add_end(last, 12)

traverse(last)
```
