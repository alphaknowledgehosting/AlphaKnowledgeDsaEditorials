# Doubly Linked List: Complete Guide

A doubly linked list is a data structure where each node contains three parts: a data field and two pointer fields pointing to the previous and next nodes in the sequence. Unlike singly linked lists, doubly linked lists allow traversal in both forward and backward directions. 

## Structure of a Node

Each node in a doubly linked list contains three parts: 

**Data**: Stores the actual value or information. 

**Next Pointer**: Stores the address of the next node in the list. 

**Previous Pointer**: Stores the address of the previous node in the list. 

### Implementation

```cpp
class Node {
public:
    int data;
    Node* next;
    Node* prev;
};
```

```java
class Node {
    int data;
    Node next;
    Node prev;
    
    Node(int d) {
        data = d;
        next = null;
        prev = null;
    }
}
```

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None
```


## Advantages

**Bidirectional Traversal**: The list can be traversed in both forward and backward directions. 

**Efficient Deletion**: Deletion is more efficient when a pointer to the node is given, as the previous node can be accessed directly through the prev pointer. 

**Easy Insertion Before Node**: Inserting a new node before a given node is straightforward without traversing the list. 

**Better Implementation**: Provides better implementation for advanced data structures like heaps, binary trees, and Fibonacci heaps. 

## Disadvantages

**Extra Memory**: Each node requires additional memory for the previous pointer compared to singly linked lists. 

**Complex Operations**: All operations require maintaining an extra pointer, making implementation more complex. 

**Pointer Management**: More pointers need to be handled carefully during operations to avoid data loss. 

**Increased Overhead**: Extra steps are needed for insertion and deletion operations to maintain both next and previous pointers. 

## Creating a Doubly Linked List

### Implementation

```cpp
#include <bits/stdc++.h>
using namespace std;

class Node {
public:
    int data;
    Node* next;
    Node* prev;
};

int main() {
    Node* head = NULL;
    Node* second = NULL;
    Node* third = NULL;
    
    head = new Node;
    second = new Node;
    third = new Node;
    
    head->data = 1;
    head->prev = NULL;
    head->next = second;
    
    second->data = 2;
    second->prev = head;
    second->next = third;
    
    third->data = 3;
    third->prev = second;
    third->next = NULL;
    
    return 0;
}
```

```java
class Node {
    int data;
    Node next;
    Node prev;
    
    Node(int d) {
        data = d;
        next = null;
        prev = null;
    }
}

public class Main {
    public static void main(String[] args) {
        Node head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);
        
        head.prev = null;
        head.next = second;
        
        second.prev = head;
        second.next = third;
        
        third.prev = second;
        third.next = null;
    }
}
```

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

# Create nodes
head = Node(1)
second = Node(2)
third = Node(3)

# Link nodes
head.prev = None
head.next = second

second.prev = head
second.next = third

third.prev = second
third.next = None
```


## Traversal Operations

### Forward Traversal

```cpp
void traverseForward(Node* head) {
    if (head == NULL) {
        cout << "List is empty." << endl;
        return;
    }
    
    Node* temp = head;
    
    while (temp != NULL) {
        cout << temp->data << " ";
        temp = temp->next;
    }
    cout << endl;
}
```

```java
void traverseForward(Node head) {
    if (head == null) {
        System.out.println("List is empty.");
        return;
    }
    
    Node temp = head;
    
    while (temp != null) {
        System.out.print(temp.data + " ");
        temp = temp.next;
    }
    System.out.println();
}
```

```python
def traverse_forward(head):
    if head is None:
        print("List is empty.")
        return
    
    temp = head
    
    while temp is not None:
        print(temp.data, end=" ")
        temp = temp.next
    print()
```


### Backward Traversal

```cpp
void traverseBackward(Node* tail) {
    if (tail == NULL) {
        cout << "List is empty." << endl;
        return;
    }
    
    Node* temp = tail;
    
    while (temp != NULL) {
        cout << temp->data << " ";
        temp = temp->prev;
    }
    cout << endl;
}
```

```java
void traverseBackward(Node tail) {
    if (tail == null) {
        System.out.println("List is empty.");
        return;
    }
    
    Node temp = tail;
    
    while (temp != null) {
        System.out.print(temp.data + " ");
        temp = temp.prev;
    }
    System.out.println();
}
```

```python
def traverse_backward(tail):
    if tail is None:
        print("List is empty.")
        return
    
    temp = tail
    
    while temp is not None:
        print(temp.data, end=" ")
        temp = temp.prev
    print()
```


### Time Complexity

O(n) where n is the number of nodes in the doubly linked list. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

## Insertion Operations

### Insert at Beginning

```cpp
void push(Node** head_ref, int new_data) {
    Node* new_node = new Node();
    
    new_node->data = new_data;
    new_node->next = (*head_ref);
    new_node->prev = NULL;
    
    if ((*head_ref) != NULL)
        (*head_ref)->prev = new_node;
    
    (*head_ref) = new_node;
}
```

```java
Node push(Node head, int new_data) {
    Node new_node = new Node(new_data);
    
    new_node.next = head;
    new_node.prev = null;
    
    if (head != null)
        head.prev = new_node;
    
    head = new_node;
    return head;
}
```

```python
def push(head, new_data):
    new_node = Node(new_data)
    
    new_node.next = head
    new_node.prev = None
    
    if head is not None:
        head.prev = new_node
    
    head = new_node
    return head
```


### Time Complexity

O(1) as no traversal is needed. 

### Space Complexity

O(1) as we only create one new node. 

### Insert After a Node

```cpp
void insertAfter(Node* prev_node, int new_data) {
    if (prev_node == NULL) {
        cout << "The given previous node cannot be NULL";
        return;
    }
    
    Node* new_node = new Node();
    new_node->data = new_data;
    new_node->next = prev_node->next;
    prev_node->next = new_node;
    new_node->prev = prev_node;
    
    if (new_node->next != NULL)
        new_node->next->prev = new_node;
}
```

```java
void insertAfter(Node prev_node, int new_data) {
    if (prev_node == null) {
        System.out.println("The given previous node cannot be NULL");
        return;
    }
    
    Node new_node = new Node(new_data);
    new_node.next = prev_node.next;
    prev_node.next = new_node;
    new_node.prev = prev_node;
    
    if (new_node.next != null)
        new_node.next.prev = new_node;
}
```

```python
def insert_after(prev_node, new_data):
    if prev_node is None:
        print("The given previous node cannot be NULL")
        return
    
    new_node = Node(new_data)
    new_node.next = prev_node.next
    prev_node.next = new_node
    new_node.prev = prev_node
    
    if new_node.next is not None:
        new_node.next.prev = new_node
```


### Time Complexity

O(1) as we have direct access to the previous node. 

### Space Complexity

O(1) as we only create one new node. 

### Insert at End

```cpp
void append(Node** head_ref, int new_data) {
    Node* new_node = new Node();
    Node* last = *head_ref;
    
    new_node->data = new_data;
    new_node->next = NULL;
    
    if (*head_ref == NULL) {
        new_node->prev = NULL;
        *head_ref = new_node;
        return;
    }
    
    while (last->next != NULL)
        last = last->next;
    
    last->next = new_node;
    new_node->prev = last;
}
```

```java
Node append(Node head, int new_data) {
    Node new_node = new Node(new_data);
    Node last = head;
    
    new_node.next = null;
    
    if (head == null) {
        new_node.prev = null;
        head = new_node;
        return head;
    }
    
    while (last.next != null)
        last = last.next;
    
    last.next = new_node;
    new_node.prev = last;
    
    return head;
}
```

```python
def append(head, new_data):
    new_node = Node(new_data)
    last = head
    
    new_node.next = None
    
    if head is None:
        new_node.prev = None
        head = new_node
        return head
    
    while last.next is not None:
        last = last.next
    
    last.next = new_node
    new_node.prev = last
    
    return head
```


### Time Complexity

O(n) as we need to traverse to the end of the list. 

### Space Complexity

O(1) as we only create one new node. 

### Insert Before a Node

```cpp
void insertBefore(Node** head_ref, Node* next_node, int new_data) {
    if (next_node == NULL) {
        cout << "The given next node cannot be NULL";
        return;
    }
    
    Node* new_node = new Node();
    new_node->data = new_data;
    new_node->prev = next_node->prev;
    next_node->prev = new_node;
    new_node->next = next_node;
    
    if (new_node->prev != NULL)
        new_node->prev->next = new_node;
    else
        (*head_ref) = new_node;
}
```

```java
Node insertBefore(Node head, Node next_node, int new_data) {
    if (next_node == null) {
        System.out.println("The given next node cannot be NULL");
        return head;
    }
    
    Node new_node = new Node(new_data);
    new_node.prev = next_node.prev;
    next_node.prev = new_node;
    new_node.next = next_node;
    
    if (new_node.prev != null)
        new_node.prev.next = new_node;
    else
        head = new_node;
    
    return head;
}
```

```python
def insert_before(head, next_node, new_data):
    if next_node is None:
        print("The given next node cannot be NULL")
        return head
    
    new_node = Node(new_data)
    new_node.prev = next_node.prev
    next_node.prev = new_node
    new_node.next = next_node
    
    if new_node.prev is not None:
        new_node.prev.next = new_node
    else:
        head = new_node
    
    return head
```


### Time Complexity

O(1) as we have direct access to the next node. 

### Space Complexity

O(1) as we only create one new node. 

## Deletion Operations

### Delete First Node

```cpp
void deleteFirst(Node** head_ref) {
    if (*head_ref == NULL) {
        cout << "List is empty" << endl;
        return;
    }
    
    Node* temp = *head_ref;
    *head_ref = temp->next;
    
    if (*head_ref != NULL)
        (*head_ref)->prev = NULL;
    
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
    head = temp.next;
    
    if (head != null)
        head.prev = null;
    
    return head;
}
```

```python
def delete_first(head):
    if head is None:
        print("List is empty")
        return None
    
    temp = head
    head = temp.next
    
    if head is not None:
        head.prev = None
    
    return head
```


### Time Complexity

O(1) as we only need to update the head pointer. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

### Delete Last Node

```cpp
void deleteLast(Node** head_ref) {
    if (*head_ref == NULL) {
        cout << "List is empty" << endl;
        return;
    }
    
    Node* temp = *head_ref;
    
    if (temp->next == NULL) {
        *head_ref = NULL;
        delete temp;
        return;
    }
    
    while (temp->next != NULL)
        temp = temp->next;
    
    temp->prev->next = NULL;
    delete temp;
}
```

```java
Node deleteLast(Node head) {
    if (head == null) {
        System.out.println("List is empty");
        return null;
    }
    
    Node temp = head;
    
    if (temp.next == null) {
        head = null;
        return head;
    }
    
    while (temp.next != null)
        temp = temp.next;
    
    temp.prev.next = null;
    
    return head;
}
```

```python
def delete_last(head):
    if head is None:
        print("List is empty")
        return None
    
    temp = head
    
    if temp.next is None:
        head = None
        return head
    
    while temp.next is not None:
        temp = temp.next
    
    temp.prev.next = None
    
    return head
```


### Time Complexity

O(n) as we need to traverse to the last node. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

### Delete Given Node

```cpp
void deleteNode(Node** head_ref, Node* del) {
    if (*head_ref == NULL || del == NULL)
        return;
    
    if (*head_ref == del)
        *head_ref = del->next;
    
    if (del->next != NULL)
        del->next->prev = del->prev;
    
    if (del->prev != NULL)
        del->prev->next = del->next;
    
    delete del;
}
```

```java
Node deleteNode(Node head, Node del) {
    if (head == null || del == null)
        return head;
    
    if (head == del)
        head = del.next;
    
    if (del.next != null)
        del.next.prev = del.prev;
    
    if (del.prev != null)
        del.prev.next = del.next;
    
    return head;
}
```

```python
def delete_node(head, del_node):
    if head is None or del_node is None:
        return head
    
    if head == del_node:
        head = del_node.next
    
    if del_node.next is not None:
        del_node.next.prev = del_node.prev
    
    if del_node.prev is not None:
        del_node.prev.next = del_node.next
    
    return head
```


### Time Complexity

O(1) when pointer to the node is given. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

### Delete at Kth Position

```cpp
void deleteAtPosition(Node** head_ref, int position) {
    if (*head_ref == NULL || position < 1) {
        cout << "Invalid position" << endl;
        return;
    }
    
    Node* temp = *head_ref;
    
    if (position == 1) {
        deleteFirst(head_ref);
        return;
    }
    
    for (int i = 1; temp != NULL && i < position; i++)
        temp = temp->next;
    
    if (temp == NULL) {
        cout << "Position out of bounds" << endl;
        return;
    }
    
    deleteNode(head_ref, temp);
}
```

```java
Node deleteAtPosition(Node head, int position) {
    if (head == null || position < 1) {
        System.out.println("Invalid position");
        return head;
    }
    
    Node temp = head;
    
    if (position == 1) {
        return deleteFirst(head);
    }
    
    for (int i = 1; temp != null && i < position; i++)
        temp = temp.next;
    
    if (temp == null) {
        System.out.println("Position out of bounds");
        return head;
    }
    
    return deleteNode(head, temp);
}
```

```python
def delete_at_position(head, position):
    if head is None or position < 1:
        print("Invalid position")
        return head
    
    temp = head
    
    if position == 1:
        return delete_first(head)
    
    for i in range(1, position):
        if temp is None:
            break
        temp = temp.next
    
    if temp is None:
        print("Position out of bounds")
        return head
    
    return delete_node(head, temp)
```


### Time Complexity

O(n) where n is the position of the node to be deleted. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

## Search Operations

### Iterative Search

```cpp
bool search(Node* head, int key) {
    Node* temp = head;
    
    while (temp != NULL) {
        if (temp->data == key)
            return true;
        temp = temp->next;
    }
    
    return false;
}
```

```java
boolean search(Node head, int key) {
    Node temp = head;
    
    while (temp != null) {
        if (temp.data == key)
            return true;
        temp = temp.next;
    }
    
    return false;
}
```

```python
def search(head, key):
    temp = head
    
    while temp is not None:
        if temp.data == key:
            return True
        temp = temp.next
    
    return False
```


### Time Complexity

O(n) where n is the number of nodes in the doubly linked list. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

### Recursive Search

```cpp
bool searchRecursive(Node* head, int key) {
    if (head == NULL)
        return false;
    
    if (head->data == key)
        return true;
    
    return searchRecursive(head->next, key);
}
```

```java
boolean searchRecursive(Node head, int key) {
    if (head == null)
        return false;
    
    if (head.data == key)
        return true;
    
    return searchRecursive(head.next, key);
}
```

```python
def search_recursive(head, key):
    if head is None:
        return False
    
    if head.data == key:
        return True
    
    return search_recursive(head.next, key)
```


### Time Complexity

O(n) where n is the number of nodes in the doubly linked list. 

### Space Complexity

O(n) due to recursive call stack. 

## Reverse Operations

### Reverse a Doubly Linked List

```cpp
void reverse(Node** head_ref) {
    Node* temp = NULL;
    Node* current = *head_ref;
    
    while (current != NULL) {
        temp = current->prev;
        current->prev = current->next;
        current->next = temp;
        current = current->prev;
    }
    
    if (temp != NULL)
        *head_ref = temp->prev;
}
```

```java
Node reverse(Node head) {
    Node temp = null;
    Node current = head;
    
    while (current != null) {
        temp = current.prev;
        current.prev = current.next;
        current.next = temp;
        current = current.prev;
    }
    
    if (temp != null)
        head = temp.prev;
    
    return head;
}
```

```python
def reverse(head):
    temp = None
    current = head
    
    while current is not None:
        temp = current.prev
        current.prev = current.next
        current.next = temp
        current = current.prev
    
    if temp is not None:
        head = temp.prev
    
    return head
```


### Time Complexity

O(n) where n is the number of nodes in the doubly linked list. 

### Space Complexity

O(1) as we only use a constant amount of extra space. 

## Applications

**Browser History**: Used to implement back and forward navigation in web browsers. 

**Undo/Redo Operations**: Applied in text editors and applications requiring undo-redo functionality. 

**Navigation Systems**: Used in music players for previous and next song navigation. 

**LRU Cache**: Implemented in Least Recently Used cache for efficient insertion and deletion. 

**Advanced Data Structures**: Used as a building block for implementing Fibonacci heaps and other complex structures. 

**Operating Systems**: Applied in thread scheduling and memory management. 

## Complete Implementation Example

```cpp
#include <bits/stdc++.h>
using namespace std;

class Node {
public:
    int data;
    Node* next;
    Node* prev;
};

void push(Node** head_ref, int new_data) {
    Node* new_node = new Node();
    new_node->data = new_data;
    new_node->next = (*head_ref);
    new_node->prev = NULL;
    
    if ((*head_ref) != NULL)
        (*head_ref)->prev = new_node;
    
    (*head_ref) = new_node;
}

void insertAfter(Node* prev_node, int new_data) {
    if (prev_node == NULL) {
        cout << "The given previous node cannot be NULL";
        return;
    }
    
    Node* new_node = new Node();
    new_node->data = new_data;
    new_node->next = prev_node->next;
    prev_node->next = new_node;
    new_node->prev = prev_node;
    
    if (new_node->next != NULL)
        new_node->next->prev = new_node;
}

void append(Node** head_ref, int new_data) {
    Node* new_node = new Node();
    Node* last = *head_ref;
    
    new_node->data = new_data;
    new_node->next = NULL;
    
    if (*head_ref == NULL) {
        new_node->prev = NULL;
        *head_ref = new_node;
        return;
    }
    
    while (last->next != NULL)
        last = last->next;
    
    last->next = new_node;
    new_node->prev = last;
}

void printList(Node* node) {
    Node* last;
    cout << "Traversal in forward direction: ";
    while (node != NULL) {
        cout << node->data << " ";
        last = node;
        node = node->next;
    }
    
    cout << "\nTraversal in reverse direction: ";
    while (last != NULL) {
        cout << last->data << " ";
        last = last->prev;
    }
}

int main() {
    Node* head = NULL;
    
    append(&head, 6);
    push(&head, 7);
    push(&head, 1);
    append(&head, 4);
    insertAfter(head->next, 8);
    
    cout << "Created DLL is: " << endl;
    printList(head);
    
    return 0;
}
```

**Output:**

```
Created DLL is: 
Traversal in forward direction: 1 7 8 6 4 
Traversal in reverse direction: 4 6 8 7 1
```

```java
class Node {
    int data;
    Node next;
    Node prev;
    
    Node(int d) {
        data = d;
        next = null;
        prev = null;
    }
}

class DoublyLinkedList {
    static Node push(Node head, int new_data) {
        Node new_node = new Node(new_data);
        new_node.next = head;
        new_node.prev = null;
        
        if (head != null)
            head.prev = new_node;
        
        head = new_node;
        return head;
    }
    
    static void insertAfter(Node prev_node, int new_data) {
        if (prev_node == null) {
            System.out.println("The given previous node cannot be NULL");
            return;
        }
        
        Node new_node = new Node(new_data);
        new_node.next = prev_node.next;
        prev_node.next = new_node;
        new_node.prev = prev_node;
        
        if (new_node.next != null)
            new_node.next.prev = new_node;
    }
    
    static Node append(Node head, int new_data) {
        Node new_node = new Node(new_data);
        Node last = head;
        
        new_node.next = null;
        
        if (head == null) {
            new_node.prev = null;
            head = new_node;
            return head;
        }
        
        while (last.next != null)
            last = last.next;
        
        last.next = new_node;
        new_node.prev = last;
        
        return head;
    }
    
    static void printList(Node node) {
        Node last = null;
        System.out.print("Traversal in forward direction: ");
        while (node != null) {
            System.out.print(node.data + " ");
            last = node;
            node = node.next;
        }
        
        System.out.print("\nTraversal in reverse direction: ");
        while (last != null) {
            System.out.print(last.data + " ");
            last = last.prev;
        }
    }
    
    public static void main(String[] args) {
        Node head = null;
        
        head = append(head, 6);
        head = push(head, 7);
        head = push(head, 1);
        head = append(head, 4);
        insertAfter(head.next, 8);
        
        System.out.println("Created DLL is: ");
        printList(head);
    }
}
```

**Output:**

```
Created DLL is: 
Traversal in forward direction: 1 7 8 6 4 
Traversal in reverse direction: 4 6 8 7 1
```

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

def push(head, new_data):
    new_node = Node(new_data)
    new_node.next = head
    new_node.prev = None
    
    if head is not None:
        head.prev = new_node
    
    head = new_node
    return head

def insert_after(prev_node, new_data):
    if prev_node is None:
        print("The given previous node cannot be NULL")
        return
    
    new_node = Node(new_data)
    new_node.next = prev_node.next
    prev_node.next = new_node
    new_node.prev = prev_node
    
    if new_node.next is not None:
        new_node.next.prev = new_node

def append(head, new_data):
    new_node = Node(new_data)
    last = head
    
    new_node.next = None
    
    if head is None:
        new_node.prev = None
        head = new_node
        return head
    
    while last.next is not None:
        last = last.next
    
    last.next = new_node
    new_node.prev = last
    
    return head

def print_list(node):
    last = None
    print("Traversal in forward direction: ", end="")
    while node is not None:
        print(node.data, end=" ")
        last = node
        node = node.next
    
    print("\nTraversal in reverse direction: ", end="")
    while last is not None:
        print(last.data, end=" ")
        last = last.prev

# Main
head = None

head = append(head, 6)
head = push(head, 7)
head = push(head, 1)
head = append(head, 4)
insert_after(head.next, 8)

print("Created DLL is: ")
print_list(head)
```

**Output:**

```
Created DLL is: 
Traversal in forward direction: 1 7 8 6 4 
Traversal in reverse direction: 4 6 8 7 1
```

