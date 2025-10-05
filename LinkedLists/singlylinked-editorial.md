# Linked List: Complete Guide

A linked list is a linear data structure where elements are stored at non-contiguous memory locations and linked together using pointers. Unlike arrays, linked lists provide dynamic size and efficient insertion/deletion operations.

## Structure of a Node

Each node in a linked list contains two parts:

- **Data**: Stores the actual value or information
- **Next Pointer**: Stores the address of the next node in memory

In C/C++, a node is represented as:

```cpp
struct Node {
    int data;
    struct Node* next;
};
```

In Java:

```cpp
class LinkedList {
    Node head;
    
    class Node {
        int data;
        Node next;
        
        Node(int d) { data = d; }
    }
}
```


## Advantages Over Arrays

**Dynamic Size**: The size can grow or shrink at runtime, unlike arrays with fixed size.

**Efficient Insertion/Deletion**: No shifting of elements required. For example, inserting 1005 in a sorted array `[1000][1010][1050][2000][2040]` requires moving all elements after 1000, while in a linked list, you simply adjust pointers.

## Disadvantages

**No Random Access**: Elements must be accessed sequentially from the head, making binary search inefficient.

**Extra Memory**: Each node requires additional memory for the pointer.

**Poor Cache Locality**: Non-contiguous memory allocation results in worse performance compared to arrays.

**Slow Traversal**: Accessing elements and changing pointers takes more time.

## Creating a Simple Linked List

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

**Time Complexity**: $O(n)$
**Space Complexity**: $O(1)$

### Recursive Traversal

```cpp
void traverse(Node* head) {
    if (head == NULL)
        return;
    
    cout << head->data << " ";
    traverse(head->next);
}
```

**Time Complexity**: $O(n)$
**Space Complexity**: $O(n)$ due to recursive call stack

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

**Time Complexity**: $O(1)$

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

**Time Complexity**: $O(1)$

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
    return;
}
```

**Time Complexity**: $O(n)$

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

**Time Complexity**: $O(n)$

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

**Time Complexity**: $O(1)$ if not last node, $O(n)$ if last node

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

**Time Complexity**: $O(1)$

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

**Time Complexity**: $O(n)$

## Search Operations

### Iterative Search

```cpp
bool search(Node* head, int x) {
    Node* current = head;
    while (current != NULL) {
        if (current->key == x)
            return true;
        current = current->next;
    }
    return false;
}
```

**Time Complexity**: $O(n)$
**Space Complexity**: $O(1)$

### Recursive Search

```cpp
bool search(struct Node* head, int x) {
    if (head == NULL)
        return false;
    
    if (head->key == x)
        return true;
    
    return search(head->next, x);
}
```

**Time Complexity**: $O(n)$
**Space Complexity**: $O(n)$
