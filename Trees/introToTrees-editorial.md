# Binary Trees: Complete Guide

A binary tree is a hierarchical non-linear data structure where each node has at most two children, referred to as the left child and right child. This structure efficiently represents hierarchical relationships and enables various tree traversal operations.

## Structure of a Binary Tree

A binary tree node contains three components that define its structure and connections.

**Data**: Stores the actual value or information in the node.

**Left Pointer**: Points to the left child node.

**Right Pointer**: Points to the right child node.

### Declaration

```cpp
// Binary Tree Node in C++
struct Node {
    int data;
    struct Node* left;
    struct Node* right;
    
    Node(int val) {
        data = val;
        left = right = NULL;
    }
};
```

```java
// Binary Tree Node in Java
class Node {
    int data;
    Node left, right;
    
    Node(int val) {
        data = val;
        left = right = null;
    }
}
```

```python
# Binary Tree Node in Python
class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None
```


## Advantages

**Hierarchical Structure**: Naturally represents hierarchical data like file systems and organizational charts.

**Efficient Search**: Binary Search Trees allow O(log n) search time in balanced trees.

**Flexible Size**: Dynamic size without upper limit using pointer implementation.

**Multiple Traversals**: Supports various traversal methods (inorder, preorder, postorder, level-order).

**Efficient Insertion/Deletion**: Moderate time complexity compared to arrays and linked lists.

**Expression Representation**: Efficiently represents arithmetic expressions and syntax trees.

## Disadvantages

**No Random Access**: Cannot directly access elements by index like arrays.

**Extra Memory**: Requires additional memory for storing pointers.

**Complex Implementation**: More complex than linear data structures like arrays and linked lists.

**Balancing Overhead**: Unbalanced trees can degrade to O(n) search time.

**Traversal Complexity**: Multiple traversal methods may confuse implementation.

## Types of Binary Trees

### Full Binary Tree

A binary tree where every node has either 0 or 2 children. No node has exactly one child.

### Complete Binary Tree

A binary tree where all levels are completely filled except possibly the last level, and the last level has all nodes as far left as possible.

### Perfect Binary Tree

A binary tree where all internal nodes have two children and all leaf nodes are at the same level.

## Creating a Binary Tree

### Implementation

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
    
    Node(int val) {
        data = val;
        left = right = NULL;
    }
};

struct Node* newNode(int data) {
    struct Node* temp = new Node(data);
    return temp;
}
```

```java
class Node {
    int data;
    Node left, right;
    
    Node(int val) {
        data = val;
        left = right = null;
    }
}

class BinaryTree {
    Node root;
    
    BinaryTree() {
        root = null;
    }
    
    Node newNode(int data) {
        return new Node(data);
    }
}
```

```python
class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None

class BinaryTree:
    def __init__(self):
        self.root = None
    
    def new_node(self, data):
        return Node(data)
```


## Tree Traversal Operations

### Inorder Traversal

Visits nodes in Left-Root-Right order.

```cpp
void printInorder(struct Node* node) {
    if (node == NULL)
        return;
    
    printInorder(node->left);
    cout << node->data << " ";
    printInorder(node->right);
}
```

```java
void printInorder(Node node) {
    if (node == null)
        return;
    
    printInorder(node.left);
    System.out.print(node.data + " ");
    printInorder(node.right);
}
```

```python
def print_inorder(node):
    if node is None:
        return
    
    print_inorder(node.left)
    print(node.data, end=" ")
    print_inorder(node.right)
```

**Output:**

```
Inorder traversal of binary tree is
4 2 5 1 3
```


### Time Complexity

O(n) where n is the number of nodes in the tree.

### Space Complexity

O(h) where h is the height of the tree due to recursion stack.

### Preorder Traversal

Visits nodes in Root-Left-Right order.

```cpp
void printPreorder(struct Node* node) {
    if (node == NULL)
        return;
    
    cout << node->data << " ";
    printPreorder(node->left);
    printPreorder(node->right);
}
```

```java
void printPreorder(Node node) {
    if (node == null)
        return;
    
    System.out.print(node.data + " ");
    printPreorder(node.left);
    printPreorder(node.right);
}
```

```python
def print_preorder(node):
    if node is None:
        return
    
    print(node.data, end=" ")
    print_preorder(node.left)
    print_preorder(node.right)
```

**Output:**

```
Preorder traversal of binary tree is
1 2 4 5 3
```


### Time Complexity

O(n) where n is the number of nodes in the tree.

### Space Complexity

O(h) where h is the height of the tree due to recursion stack.

### Postorder Traversal

Visits nodes in Left-Right-Root order.

```cpp
void printPostorder(struct Node* node) {
    if (node == NULL)
        return;
    
    printPostorder(node->left);
    printPostorder(node->right);
    cout << node->data << " ";
}
```

```java
void printPostorder(Node node) {
    if (node == null)
        return;
    
    printPostorder(node.left);
    printPostorder(node.right);
    System.out.print(node.data + " ");
}
```

```python
def print_postorder(node):
    if node is None:
        return
    
    print_postorder(node.left)
    print_postorder(node.right)
    print(node.data, end=" ")
```

**Output:**

```
Postorder traversal of binary tree is
4 5 2 3 1
```


### Time Complexity

O(n) where n is the number of nodes in the tree.

### Space Complexity

O(h) where h is the height of the tree due to recursion stack.

## Insertion Operation

### Insert at First Available Position

```cpp
#include <queue>

void insert(struct Node* temp, int key) {
    queue<struct Node*> q;
    q.push(temp);
    
    while (!q.empty()) {
        struct Node* temp = q.front();
        q.pop();
        
        if (!temp->left) {
            temp->left = newNode(key);
            break;
        } else
            q.push(temp->left);
        
        if (!temp->right) {
            temp->right = newNode(key);
            break;
        } else
            q.push(temp->right);
    }
}
```

```java
import java.util.LinkedList;
import java.util.Queue;

void insert(Node temp, int key) {
    Queue<Node> q = new LinkedList<>();
    q.add(temp);
    
    while (!q.isEmpty()) {
        Node temp_node = q.poll();
        
        if (temp_node.left == null) {
            temp_node.left = new Node(key);
            break;
        } else
            q.add(temp_node.left);
        
        if (temp_node.right == null) {
            temp_node.right = new Node(key);
            break;
        } else
            q.add(temp_node.right);
    }
}
```

```python
from collections import deque

def insert(temp, key):
    q = deque()
    q.append(temp)
    
    while q:
        temp_node = q.popleft()
        
        if temp_node.left is None:
            temp_node.left = Node(key)
            break
        else:
            q.append(temp_node.left)
        
        if temp_node.right is None:
            temp_node.right = Node(key)
            break
        else:
            q.append(temp_node.right)
```

**Output:**

```
Inorder traversal before insertion: 7 11 10 15 9 8
Inorder traversal after insertion: 7 11 12 10 15 9 8
```


### Time Complexity

O(n) where n is the number of nodes, as we may need to traverse all nodes.

### Space Complexity

O(w) where w is the maximum width of the tree due to queue storage.

## Deletion Operation

### Delete Given Node

```cpp
void deleteDeepest(struct Node* root, struct Node* d_node) {
    queue<struct Node*> q;
    q.push(root);
    
    struct Node* temp;
    while (!q.empty()) {
        temp = q.front();
        q.pop();
        
        if (temp->right) {
            if (temp->right == d_node) {
                temp->right = NULL;
                delete(d_node);
                return;
            } else
                q.push(temp->right);
        }
        
        if (temp->left) {
            if (temp->left == d_node) {
                temp->left = NULL;
                delete(d_node);
                return;
            } else
                q.push(temp->left);
        }
    }
}

void deletion(struct Node* root, int key) {
    queue<struct Node*> q;
    q.push(root);
    
    struct Node* temp;
    struct Node* key_node = NULL;
    
    while (!q.empty()) {
        temp = q.front();
        q.pop();
        
        if (temp->data == key)
            key_node = temp;
        
        if (temp->left)
            q.push(temp->left);
        
        if (temp->right)
            q.push(temp->right);
    }
    
    if (key_node != NULL) {
        int x = temp->data;
        deleteDeepest(root, temp);
        key_node->data = x;
    }
}
```

```java
void deleteDeepest(Node root, Node d_node) {
    Queue<Node> q = new LinkedList<>();
    q.add(root);
    
    Node temp = null;
    while (!q.isEmpty()) {
        temp = q.poll();
        
        if (temp.right != null) {
            if (temp.right == d_node) {
                temp.right = null;
                return;
            } else
                q.add(temp.right);
        }
        
        if (temp.left != null) {
            if (temp.left == d_node) {
                temp.left = null;
                return;
            } else
                q.add(temp.left);
        }
    }
}

void deletion(Node root, int key) {
    Queue<Node> q = new LinkedList<>();
    q.add(root);
    
    Node temp = null;
    Node key_node = null;
    
    while (!q.isEmpty()) {
        temp = q.poll();
        
        if (temp.data == key)
            key_node = temp;
        
        if (temp.left != null)
            q.add(temp.left);
        
        if (temp.right != null)
            q.add(temp.right);
    }
    
    if (key_node != null) {
        int x = temp.data;
        deleteDeepest(root, temp);
        key_node.data = x;
    }
}
```

```python
def delete_deepest(root, d_node):
    q = deque()
    q.append(root)
    
    while q:
        temp = q.popleft()
        
        if temp.right:
            if temp.right == d_node:
                temp.right = None
                return
            else:
                q.append(temp.right)
        
        if temp.left:
            if temp.left == d_node:
                temp.left = None
                return
            else:
                q.append(temp.left)

def deletion(root, key):
    q = deque()
    q.append(root)
    
    temp = None
    key_node = None
    
    while q:
        temp = q.popleft()
        
        if temp.data == key:
            key_node = temp
        
        if temp.left:
            q.append(temp.left)
        
        if temp.right:
            q.append(temp.right)
    
    if key_node:
        x = temp.data
        delete_deepest(root, temp)
        key_node.data = x
```

**Output:**

```
Inorder traversal before Deletion: 7 11 12 10 15 9 8
Inorder traversal after Deletion: 7 8 12 10 15 9
```


### Time Complexity

O(n) where n is the number of nodes, as we traverse all nodes.

### Space Complexity

O(w) where w is the maximum width of the tree due to queue storage.

## Properties of Binary Trees

### Maximum Nodes at Level

The maximum number of nodes at level 'l' is $2^{l-1}$ where level of root is 1.

### Maximum Nodes in Tree

Maximum number of nodes in a binary tree of height 'h' is $2^h - 1$.

### Minimum Height

In a binary tree with N nodes, the minimum possible height is $\log_2(N+1)$.

### Leaf Nodes Relationship

In a binary tree where every node has 0 or 2 children, the number of leaf nodes is always one more than nodes with two children: L = T + 1.

## Applications

**File System Representation**: Hierarchical folder structure in operating systems.

**Expression Trees**: Representing arithmetic and boolean expressions in compilers.

**Binary Search Trees**: Fast search, insert, and delete operations on sorted data.

**Heap Data Structure**: Implementing priority queues for scheduling algorithms.

**Database Indexing**: B-Tree and B+ Tree for efficient database indexing.

**Huffman Coding**: Data compression using optimal prefix codes.

**Decision Trees**: Machine learning classification and regression tasks.

**Syntax Trees**: Compiler design for parsing and code generation.

**Spanning Trees**: Network routing in routers and bridges.

**Trie Data Structure**: Implementing dictionaries with prefix lookup.

## Complete Implementation

```cpp
#include <iostream>
#include <queue>
using namespace std;

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
    
    Node(int val) {
        data = val;
        left = right = NULL;
    }
};

struct Node* newNode(int data) {
    return new Node(data);
}

void printInorder(struct Node* node) {
    if (node == NULL)
        return;
    printInorder(node->left);
    cout << node->data << " ";
    printInorder(node->right);
}

void printPreorder(struct Node* node) {
    if (node == NULL)
        return;
    cout << node->data << " ";
    printPreorder(node->left);
    printPreorder(node->right);
}

void printPostorder(struct Node* node) {
    if (node == NULL)
        return;
    printPostorder(node->left);
    printPostorder(node->right);
    cout << node->data << " ";
}

void insert(struct Node* temp, int key) {
    queue<struct Node*> q;
    q.push(temp);
    
    while (!q.empty()) {
        struct Node* temp = q.front();
        q.pop();
        
        if (!temp->left) {
            temp->left = newNode(key);
            break;
        } else
            q.push(temp->left);
        
        if (!temp->right) {
            temp->right = newNode(key);
            break;
        } else
            q.push(temp->right);
    }
}

int main() {
    // Create Binary Tree:
    //      1
    //     / \
    //    2   3
    //   / \
    //  4   5
    
    struct Node* root = newNode(1);
    root->left = newNode(2);
    root->right = newNode(3);
    root->left->left = newNode(4);
    root->left->right = newNode(5);
    
    cout << "Preorder traversal of binary tree is" << endl;
    printPreorder(root);
    
    cout << "\nInorder traversal of binary tree is" << endl;
    printInorder(root);
    
    cout << "\nPostorder traversal of binary tree is" << endl;
    printPostorder(root);
    
    cout << "\n\nInorder traversal before insertion: ";
    inorder(root);
    
    int key = 12;
    insert(root, key);
    
    cout << "\nInorder traversal after insertion: ";
    inorder(root);
    
    return 0;
}
```

```java
import java.util.LinkedList;
import java.util.Queue;

class Node {
    int data;
    Node left, right;
    
    Node(int val) {
        data = val;
        left = right = null;
    }
}

class BinaryTree {
    Node root;
    
    void printInorder(Node node) {
        if (node == null)
            return;
        printInorder(node.left);
        System.out.print(node.data + " ");
        printInorder(node.right);
    }
    
    void printPreorder(Node node) {
        if (node == null)
            return;
        System.out.print(node.data + " ");
        printPreorder(node.left);
        printPreorder(node.right);
    }
    
    void printPostorder(Node node) {
        if (node == null)
            return;
        printPostorder(node.left);
        printPostorder(node.right);
        System.out.print(node.data + " ");
    }
    
    void insert(Node temp, int key) {
        Queue<Node> q = new LinkedList<>();
        q.add(temp);
        
        while (!q.isEmpty()) {
            Node temp_node = q.poll();
            
            if (temp_node.left == null) {
                temp_node.left = new Node(key);
                break;
            } else
                q.add(temp_node.left);
            
            if (temp_node.right == null) {
                temp_node.right = new Node(key);
                break;
            } else
                q.add(temp_node.right);
        }
    }
    
    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();
        tree.root = new Node(1);
        tree.root.left = new Node(2);
        tree.root.right = new Node(3);
        tree.root.left.left = new Node(4);
        tree.root.left.right = new Node(5);
        
        System.out.println("Preorder traversal of binary tree is");
        tree.printPreorder(tree.root);
        
        System.out.println("\nInorder traversal of binary tree is");
        tree.printInorder(tree.root);
        
        System.out.println("\nPostorder traversal of binary tree is");
        tree.printPostorder(tree.root);
        
        System.out.print("\n\nInorder traversal before insertion: ");
        tree.printInorder(tree.root);
        
        int key = 12;
        tree.insert(tree.root, key);
        
        System.out.print("\nInorder traversal after insertion: ");
        tree.printInorder(tree.root);
    }
}
```

```python
from collections import deque

class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None

class BinaryTree:
    def __init__(self):
        self.root = None
    
    def print_inorder(self, node):
        if node is None:
            return
        self.print_inorder(node.left)
        print(node.data, end=" ")
        self.print_inorder(node.right)
    
    def print_preorder(self, node):
        if node is None:
            return
        print(node.data, end=" ")
        self.print_preorder(node.left)
        self.print_preorder(node.right)
    
    def print_postorder(self, node):
        if node is None:
            return
        self.print_postorder(node.left)
        self.print_postorder(node.right)
        print(node.data, end=" ")
    
    def insert(self, temp, key):
        q = deque()
        q.append(temp)
        
        while q:
            temp_node = q.popleft()
            
            if temp_node.left is None:
                temp_node.left = Node(key)
                break
            else:
                q.append(temp_node.left)
            
            if temp_node.right is None:
                temp_node.right = Node(key)
                break
            else:
                q.append(temp_node.right)

# Main program
tree = BinaryTree()
tree.root = Node(1)
tree.root.left = Node(2)
tree.root.right = Node(3)
tree.root.left.left = Node(4)
tree.root.left.right = Node(5)

print("Preorder traversal of binary tree is")
tree.print_preorder(tree.root)

print("\nInorder traversal of binary tree is")
tree.print_inorder(tree.root)

print("\nPostorder traversal of binary tree is")
tree.print_postorder(tree.root)

print("\n\nInorder traversal before insertion: ", end="")
tree.print_inorder(tree.root)

key = 12
tree.insert(tree.root, key)

print("\nInorder traversal after insertion: ", end="")
tree.print_inorder(tree.root)
```

**Output:**

```
Preorder traversal of binary tree is
1 2 4 5 3
Inorder traversal of binary tree is
4 2 5 1 3
Postorder traversal of binary tree is
4 5 2 3 1

Inorder traversal before insertion: 4 2 5 1 3
Inorder traversal after insertion: 4 2 5 1 12 3
```

This comprehensive editorial covers binary trees following the doubly linked list format with complete code implementations in C++, Java, and Python, including outputs for each section.

