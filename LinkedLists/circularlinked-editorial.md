
### Circular Linked Lists: A Complete Guide

## Introduction

A circular linked list is a linked list where all nodes are connected to form a circle. There is no NULL at the end. The last node of the linked list points to the first node, creating a circular structure. This data structure can be implemented as a singly circular linked list or doubly circular linked list.

## Structure and Implementation

### Node Structure

Each node in a circular linked list contains two parts: data and a pointer to the next node. The implementation uses an external pointer that points to the last node of the list.

```cpp
struct Node {
    int data;
    struct Node *next;
};
```


### Why Point to the Last Node?

For insertion at the beginning or end, pointing to the last node is advantageous. If a pointer last points to the last node, then last->next will point to the first node. This approach eliminates the need to traverse the entire list for insertion operations at either end, making them constant time operations regardless of list length.

## Traversal Operations

### Basic Traversal

In a conventional linked list, traversal stops when NULL is reached. In a circular linked list, traversal stops when the first node is reached again.

```cpp
void traverse(struct Node *last) {
    struct Node *p;
    
    if (last == NULL) {
        cout << "List is empty." << endl;
        return;
    }
    
    p = last -> next;
    
    do {
        cout << p -> data << " ";
        p = p -> next;
    } while(p != last->next);
}
```


## Insertion Operations

### Insertion in Empty List

When the list is empty, the last pointer is NULL. After inserting the first node, it becomes both the first and last node, pointing to itself.

```cpp
struct Node *addToEmpty(struct Node *last, int data) {
    if (last != NULL)
        return last;
    
    struct Node *temp = new Node;
    temp -> data = data;
    last = temp;
    last -> next = last;
    
    return last;
}
```


### Insertion at Beginning

To insert a node at the beginning: create a new node, make its next pointer point to last->next, and update last->next to point to the new node.

```cpp
struct Node *addBegin(struct Node *last, int data) {
    if (last == NULL)
        return addToEmpty(last, data);
    
    struct Node *temp = new Node;
    temp -> data = data;
    temp -> next = last -> next;
    last -> next = temp;
    
    return last;
}
```

**Time Complexity**: O(1) - no need to traverse the list

**Space Complexity**: O(1)

### Insertion at End

To insert at the end: create a new node, set its next to last->next, update last->next to the new node, and make the new node the last node.

```cpp
struct Node *addEnd(struct Node *last, int data) {
    if (last == NULL)
        return addToEmpty(last, data);
    
    struct Node *temp = new Node;
    temp -> data = data;
    temp -> next = last -> next;
    last -> next = temp;
    last = temp;
    
    return last;
}
```

**Time Complexity**: O(N) when not maintaining a tail pointer

**Space Complexity**: O(1)

### Insertion After a Node

To insert after a specific node: search for the target node, create a new node, adjust pointers accordingly, and update the last pointer if inserting after the last node.

```cpp
struct Node *addAfter(struct Node *last, int data, int item) {
    if (last == NULL)
        return NULL;
    
    struct Node *temp, *p;
    p = last -> next;
    
    do {
        if (p ->data == item) {
            temp = new Node;
            temp -> data = data;
            temp -> next = p -> next;
            p -> next = temp;
            
            if (p == last)
                last = temp;
            
            return last;
        }
        p = p -> next;
    } while (p != last -> next);
    
    cout << item << " not present in the list." << endl;
    return last;
}
```

**Time Complexity**: O(N)

**Space Complexity**: O(1)

## Deletion Operations

### Delete First Node

To delete the first node: use two pointers (previous and current), traverse to find the last node, update the last node's next pointer to skip the first node, and update the head.

```cpp
void DeleteFirst(struct Node** head) {
    struct Node *previous = *head, *firstNode = *head;
    
    if (*head == NULL) {
        printf("\nList is empty\n");
        return;
    }
    
    if (previous->next == previous) {
        *head = NULL;
        return;
    }
    
    while (previous->next != *head) {
        previous = previous->next;
    }
    
    previous->next = firstNode->next;
    *head = previous->next;
    free(firstNode);
}
```


### Delete at Kth Position

To delete a node at a given index: find the list length, use two pointers (previous and next) to traverse, and when the index is reached, adjust the previous node's next pointer to skip the target node.

```cpp
void DeleteAtPosition(struct Node** head, int index) {
    int len = Length(*head);
    int count = 1;
    struct Node *previous = *head, *next = *head;
    
    if (*head == NULL) {
        printf("\nDelete Last List is empty\n");
        return;
    }
    
    if (index >= len || index < 0) {
        printf("\nIndex is not Found\n");
        return;
    }
    
    if (index == 0) {
        DeleteFirst(head);
        return;
    }
    
    while (len > 0) {
        if (index == count) {
            previous->next = next->next;
            free(next);
            return;
        }
        previous = previous->next;
        next = previous->next;
        len--;
        count++;
    }
}
```


## Advantages

**Flexible Starting Point**: Any node can be a starting point, and the whole list can be traversed by starting from any node. Traversal continues until the first visited node is visited again.

**Queue Implementation**: Circular linked lists are useful for queue implementation without maintaining separate front and rear pointers. The front can always be obtained as the next of the last inserted node.

**Cyclic Applications**: These lists are ideal for applications that repeatedly cycle through elements. Operating systems commonly use them for process scheduling, giving each application a time slice before cycling to the next.

**Advanced Data Structures**: Circular doubly linked lists are used in implementing advanced data structures like Fibonacci Heap.

**End Operations**: Circular linked lists are beneficial for end operations as start and finish coincide.

**Algorithm Efficiency**: Algorithms such as Round Robin can effectively manage queues without encountering NULL references.

## Disadvantages

**Infinite Loop Risk**: Improper handling can lead to infinite loops due to the circular nature.

**Increased Complexity**: Doubly linked circular lists are more complex compared to singly-linked lists.

**No Direct Access**: Elements cannot be accessed directly and must be traversed sequentially.

**Reversal Complexity**: Reversing a circular linked list is generally a complex task.

## Applications

**Resource Management**: Used to manage computing resources of computers.

**Data Structure Implementation**: Stacks and queues are implemented using circular linked lists.

**Advanced Algorithms**: Used in implementing Fibonacci Heap and other advanced data structures.

**Network Scheduling**: Applied in computer networking for token scheduling.

## Real-World Applications

**Gaming**: Round Robin scheduling technique in games.

**Media Streaming**: Audio and video streaming applications.

**Physical Systems**: Circular escalators and similar rotating systems.

## Complete Implementation Example

```cpp
#include<bits/stdc++.h>
using namespace std;


struct Node {
    int data;
    struct Node *next;
};


// Function implementations for all operations
// ... (include all functions shown above)


int main() {
    struct Node *last = NULL;
    
    last = addToEmpty(last, 6);
    last = addBegin(last, 4);
    last = addBegin(last, 2);
    last = addEnd(last, 8);
    last = addEnd(last, 12);
    last = addAfter(last, 10, 8);
    
    traverse(last);
    
    return 0;
}
```

**Output**: 2 4 6 8 10 12

## Complexity Analysis Summary

**Insertion at Beginning**: O(1) time, O(1) space

**Insertion at End**: O(N) time without tail pointer, O(1) space

**Insertion After Node**: O(N) time, O(1) space

**Deletion Operations**: O(N) time for most operations, O(1) space

**Traversal**: O(N) time, O(1) space for iterative, O(N) space for recursive

updaet the above to be in same as below code in all three langs and time and sc as well same format i want as per below

# Linked List: Complete Guide

A linked list is a linear data structure where elements are stored at non-contiguous memory locations and linked together using pointers. Unlike arrays, linked lists provide dynamic size and efficient insertion/deletion operations.

## Structure of a Node

Each node in a linked list contains two parts:

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
class LinkedList {
    Node head;
    
    class Node {
        int data;
        Node next;
        
        Node(int d) { 
            data = d; 
        }
    }
}
```

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class LinkedList:
    def __init__(self):
        self.head = None
```


## Advantages Over Arrays

**Dynamic Size**: The size can grow or shrink at runtime, unlike arrays with fixed size

**Efficient Insertion/Deletion**: No shifting of elements required. For example, inserting 1005 in a sorted array `[1000][1010][1050][2000][2040]` requires moving all elements after 1000, while in a linked list, you simply adjust pointers.

## Disadvantages

**No Random Access**: Elements must be accessed sequentially from the head, making binary search inefficient.

**Extra Memory**: Each node requires additional memory for the pointer.

**Poor Cache Locality**: Non-contiguous memory allocation results in worse performance compared to arrays.

**Slow Traversal**: Accessing elements and changing pointers takes more time.

## Creating a Simple Linked List

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
    third->next = NULL;
    
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
        third.next = null;
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
third.next = None
```


## Traversal Operations

### Iterative Traversal

```cpp
void printList(Node* node) {
    while (node != NULL) {
        cout << node->data << " ";
        node = node->next;
    }
}
```

```java
void printList(Node node) {
    while (node != null) {
        System.out.print(node.data + " ");
        node = node.next;
    }
}
```

```python
def print_list(node):
    while node is not None:
        print(node.data, end=" ")
        node = node.next
```


### Time Complexity

O(n) where n is the number of nodes in the linked list.

### Space Complexity

O(1) as we only use a constant amount of extra space.

### Recursive Traversal

```cpp
void traverse(Node* head) {
    if (head == NULL)
        return;
    
    cout << head->data << " ";
    traverse(head->next);
}
```

```java
void traverse(Node head) {
    if (head == null)
        return;
    
    System.out.print(head.data + " ");
    traverse(head.next);
}
```

```python
def traverse(head):
    if head is None:
        return
    
    print(head.data, end=" ")
    traverse(head.next)
```


### Time Complexity

O(n) where n is the number of nodes in the linked list.

### Space Complexity

O(n) due to recursive call stack.

## Insertion Operations

### Insert at Beginning

```cpp
void push(struct Node** head_ref, int new_data) {
    Node* new_node = new Node;
    new_node->data = new_data;
    new_node->next = (*head_ref);
    (*head_ref) = new_node;
}
```

```java
Node push(Node head, int new_data) {
    Node new_node = new Node(new_data);
    new_node.next = head;
    head = new_node;
    return head;
}
```

```python
def push(head, new_data):
    new_node = Node(new_data)
    new_node.next = head
    head = new_node
    return head
```


### Time Complexity

O(1) as we only need to adjust a few pointers.

### Space Complexity

O(1) as we only create one new node.

### Insert After a Given Node

```cpp
void insertAfter(struct Node* prev_node, int new_data) {
    if (prev_node == NULL) {
        cout << "Previous node cannot be NULL";
        return;
    }
    
    Node* new_node = new Node;
    new_node->data = new_data;
    new_node->next = prev_node->next;
    prev_node->next = new_node;
}
```

```java
void insertAfter(Node prev_node, int new_data) {
    if (prev_node == null) {
        System.out.println("Previous node cannot be null");
        return;
    }
    
    Node new_node = new Node(new_data);
    new_node.next = prev_node.next;
    prev_node.next = new_node;
}
```

```python
def insert_after(prev_node, new_data):
    if prev_node is None:
        print("Previous node cannot be None")
        return
    
    new_node = Node(new_data)
    new_node.next = prev_node.next
    prev_node.next = new_node
```


### Time Complexity

O(1) as we only need to adjust pointers at the given position.

### Space Complexity

O(1) as we only create one new node.

### Insert at End

```cpp
void append(struct Node** head_ref, int new_data) {
    Node* new_node = new Node;
    struct Node* last = *head_ref;
    
    new_node->data = new_data;
    new_node->next = NULL;
    
    if (*head_ref == NULL) {
        *head_ref = new_node;
        return;
    }
    
    while (last->next != NULL)
        last = last->next;
    
    last->next = new_node;
}
```

```java
Node append(Node head, int new_data) {
    Node new_node = new Node(new_data);
    
    if (head == null) {
        head = new_node;
        return head;
    }
    
    Node last = head;
    while (last.next != null)
        last = last.next;
    
    last.next = new_node;
    return head;
}
```

```python
def append(head, new_data):
    new_node = Node(new_data)
    
    if head is None:
        head = new_node
        return head
    
    last = head
    while last.next is not None:
        last = last.next
    
    last.next = new_node
    return head
```


### Time Complexity

O(n) where n is the number of nodes, as we need to traverse to the end.

### Space Complexity

O(1) as we only create one new node.

## Deletion Operations

### Delete at Given Position

```cpp
void deleteNode(struct Node** head_ref, int position) {
    if (*head_ref == NULL)
        return;
    
    struct Node* temp = *head_ref;
    
    if (position == 0) {
        *head_ref = temp->next;
        free(temp);
        return;
    }
    
    for (int i = 0; temp != NULL && i < position - 1; i++)
        temp = temp->next;
    
    if (temp == NULL || temp->next == NULL)
        return;
    
    struct Node* next = temp->next->next;
    free(temp->next);
    temp->next = next;
}
```

```java
Node deleteNode(Node head, int position) {
    if (head == null)
        return null;
    
    Node temp = head;
    
    if (position == 0) {
        head = temp.next;
        return head;
    }
    
    for (int i = 0; temp != null && i < position - 1; i++)
        temp = temp.next;
    
    if (temp == null || temp.next == null)
        return head;
    
    Node next = temp.next.next;
    temp.next = next;
    
    return head;
}
```

```python
def delete_node(head, position):
    if head is None:
        return None
    
    temp = head
    
    if position == 0:
        head = temp.next
        return head
    
    for i in range(position - 1):
        if temp is None:
            break
        temp = temp.next
    
    if temp is None or temp.next is None:
        return head
    
    next_node = temp.next.next
    temp.next = next_node
    
    return head
```


### Time Complexity

O(n) where n is the position of the node to be deleted.

### Space Complexity

O(1) as we only use a constant amount of extra space.

### Delete Given Node Pointer

```cpp
void deleteNode(struct Node* head, struct Node* node_ptr) {
    if (head == NULL)
        return;
    
    if (node_ptr->next == NULL) {
        struct Node* temp = head;
        while (temp->next != node_ptr)
            temp = temp->next;
        temp->next = NULL;
        free(node_ptr);
        return;
    }
    
    struct Node* temp = node_ptr->next;
    node_ptr->data = temp->data;
    node_ptr->next = temp->next;
    free(temp);
}
```

```java
void deleteNode(Node head, Node node_ptr) {
    if (head == null)
        return;
    
    if (node_ptr.next == null) {
        Node temp = head;
        while (temp.next != node_ptr)
            temp = temp.next;
        temp.next = null;
        return;
    }
    
    Node temp = node_ptr.next;
    node_ptr.data = temp.data;
    node_ptr.next = temp.next;
}
```

```python
def delete_node(head, node_ptr):
    if head is None:
        return
    
    if node_ptr.next is None:
        temp = head
        while temp.next != node_ptr:
            temp = temp.next
        temp.next = None
        return
    
    temp = node_ptr.next
    node_ptr.data = temp.data
    node_ptr.next = temp.next
```


### Time Complexity

O(1) if the node to be deleted is not the last node, O(n) if it is the last node.

### Space Complexity

O(1) as we only use a constant amount of extra space.

### Delete First Node

```cpp
Node* removeFirstNode(struct Node* head) {
    if (head == NULL)
        return NULL;
    
    Node* temp = head;
    head = head->next;
    delete temp;
    
    return head;
}
```

```java
Node removeFirstNode(Node head) {
    if (head == null)
        return null;
    
    head = head.next;
    return head;
}
```

```python
def remove_first_node(head):
    if head is None:
        return None
    
    head = head.next
    return head
```


### Time Complexity

O(1) as we only need to update the head pointer.

### Space Complexity

O(1) as we only use a constant amount of extra space.

### Delete Last Node

```cpp
Node* removeLastNode(struct Node* head) {
    if (head == NULL)
        return NULL;
    
    if (head->next == NULL) {
        delete head;
        return NULL;
    }
    
    Node* second_last = head;
    while (second_last->next->next != NULL)
        second_last = second_last->next;
    
    delete(second_last->next);
    second_last->next = NULL;
    
    return head;
}
```

```java
Node removeLastNode(Node head) {
    if (head == null)
        return null;
    
    if (head.next == null)
        return null;
    
    Node second_last = head;
    while (second_last.next.next != null)
        second_last = second_last.next;
    
    second_last.next = null;
    
    return head;
}
```

```python
def remove_last_node(head):
    if head is None:
        return None
    
    if head.next is None:
        return None
    
    second_last = head
    while second_last.next.next is not None:
        second_last = second_last.next
    
    second_last.next = None
    
    return head
```


### Time Complexity

O(n) where n is the number of nodes, as we need to traverse to find the second last node.

### Space Complexity

O(1) as we only use a constant amount of extra space.

## Search Operations

### Iterative Search

```cpp
bool search(Node* head, int x) {
    Node* current = head;
    while (current != NULL) {
        if (current->data == x)
            return true;
        current = current->next;
    }
    return false;
}
```

```java
boolean search(Node head, int x) {
    Node current = head;
    while (current != null) {
        if (current.data == x)
            return true;
        current = current.next;
    }
    return false;
}
```

```python
def search(head, x):
    current = head
    while current is not None:
        if current.data == x:
            return True
        current = current.next
    return False
```


### Time Complexity

O(n) where n is the number of nodes in the linked list.

### Space Complexity

O(1) as we only use a constant amount of extra space.

### Recursive Search

```cpp
bool search(struct Node* head, int x) {
    if (head == NULL)
        return false;
    
    if (head->data == x)
        return true;
    
    return search(head->next, x);
}
```

```java
boolean search(Node head, int x) {
    if (head == null)
        return false;
    
    if (head.data == x)
        return true;
    
    return search(head.next, x);
}
```

```python
def search(head, x):
    if head is None:
        return False
    
    if head.data == x:
        return True
    
    return search(head.next, x)
```


### Time Complexity

O(n) where n is the number of nodes in the linked list.

### Space Complexity

O(n) due to recursive call stack. and remove all references and also you dont add any references

I'll now compile the circular linked list guide following the exact format requested, with implementations in C++, Java, and Python, and consistent formatting for time and space complexity.

# Circular Linked List: Complete Guide

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
