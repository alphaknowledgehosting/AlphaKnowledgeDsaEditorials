

# Circular Linked Lists: A Complete Guide

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

