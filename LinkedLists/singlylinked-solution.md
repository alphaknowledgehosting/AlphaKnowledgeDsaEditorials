# Linked List: Complete Guide

A linked list is a linear data structure where elements are stored at non-contiguous memory locations and linked together using pointers. Unlike arrays, linked lists provide dynamic size and efficient insertion/deletion operations.

***

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


***

## Advantages Over Arrays

**Dynamic Size**: The size can grow or shrink at runtime, unlike arrays with fixed size.

**Efficient Insertion/Deletion**: No shifting of elements required. For example, inserting 1005 in a sorted array `[1000][1010][1050][2000][2040]` requires moving all elements after 1000, while in a linked list, you simply adjust pointers.

***

## Disadvantages

**No Random Access**: Elements must be accessed sequentially from the head, making binary search inefficient.

**Extra Memory**: Each node requires additional memory for the pointer.

**Poor Cache Locality**: Non-contiguous memory allocation results in worse performance compared to arrays.

**Slow Traversal**: Accessing elements and changing pointers takes more time.

***

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


***

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

***

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

***

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

***

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

***

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

***

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

***

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

***

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

***

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

***

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

***

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

O(n) due to recursive call stack.
