# Binary Search Trees: Complete Guide

A Binary Search Tree (BST) is a node-based binary tree data structure that maintains an ordering property where the left subtree contains nodes with keys less than or equal to the node's key, and the right subtree contains nodes with keys greater than the node's key. This ordering enables efficient search, insertion, and deletion operations.

## Structure of a BST

A Binary Search Tree node contains three components and maintains specific ordering properties.

**Data/Key**: Stores the value used for ordering and comparison.

**Left Pointer**: Points to the left child containing smaller values.

**Right Pointer**: Points to the right child containing larger values.

**BST Property**: For any node, all values in the left subtree are smaller, and all values in the right subtree are larger.

### Declaration

```cpp
// BST Node in C++
struct Node {
    int key;
    struct Node* left;
    struct Node* right;
    
    Node(int val) {
        key = val;
        left = right = NULL;
    }
};
```

```java
// BST Node in Java
class Node {
    int key;
    Node left, right;
    
    Node(int val) {
        key = val;
        left = right = null;
    }
}
```

```python
# BST Node in Python
class Node:
    def __init__(self, val):
        self.key = val
        self.left = None
        self.right = None
```


## Advantages

**Efficient Search**: O(log n) average case search time in balanced BSTs.

**Ordered Structure**: Inorder traversal produces sorted output automatically.

**Fast Insertion/Deletion**: O(log n) average time for insert and delete operations.

**Dynamic Size**: No predefined size limit, grows as needed.

**Range Queries**: Efficiently finds all elements within a range.

**Predecessor/Successor**: Quick access to next smaller or larger elements.

## Disadvantages

**Unbalanced Trees**: Can degrade to O(n) operations in worst case (skewed tree).

**Extra Memory**: Requires additional memory for storing pointers.

**Complex Operations**: More complex than simple arrays or linked lists.

**No Random Access**: Cannot directly access elements by index.

**Balancing Overhead**: Self-balancing BSTs require additional maintenance operations.

## Creating a BST

### Implementation

```cpp
#include <iostream>
using namespace std;

struct Node {
    int key;
    struct Node* left;
    struct Node* right;
};

struct Node* newNode(int item) {
    Node* temp = new Node;
    temp->key = item;
    temp->left = temp->right = NULL;
    return temp;
}

void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left);
        cout << root->key << " ";
        inorder(root->right);
    }
}
```

```java
class Node {
    int key;
    Node left, right;
    
    Node(int val) {
        key = val;
        left = right = null;
    }
}

class BST {
    Node root;
    
    BST() {
        root = null;
    }
    
    void inorder(Node root) {
        if (root != null) {
            inorder(root.left);
            System.out.print(root.key + " ");
            inorder(root.right);
        }
    }
}
```

```python
class Node:
    def __init__(self, val):
        self.key = val
        self.left = None
        self.right = None

class BST:
    def __init__(self):
        self.root = None
    
    def inorder(self, root):
        if root:
            self.inorder(root.left)
            print(root.key, end=" ")
            self.inorder(root.right)
```


## Search Operation

### Search for a Key

```cpp
struct Node* search(struct Node* root, int key) {
    // Base Cases: root is null or key is present at root
    if (root == NULL || root->key == key)
        return root;
    
    // Key is greater than root's key
    if (root->key < key)
        return search(root->right, key);
    
    // Key is smaller than root's key
    return search(root->left, key);
}
```

```java
Node search(Node root, int key) {
    // Base Cases: root is null or key is present at root
    if (root == null || root.key == key)
        return root;
    
    // Key is greater than root's key
    if (root.key < key)
        return search(root.right, key);
    
    // Key is smaller than root's key
    return search(root.left, key);
}
```

```python
def search(root, key):
    # Base Cases: root is null or key is present at root
    if root is None or root.key == key:
        return root
    
    # Key is greater than root's key
    if root.key < key:
        return search(root.right, key)
    
    # Key is smaller than root's key
    return search(root.left, key)
```

**Output:**

```
Node Found: YES
```


### Time Complexity

O(h) where h is the height of the BST. In balanced BSTs, h = log n, giving O(log n) time complexity.

### Space Complexity

O(h) due to recursion stack, where h is the height of the tree.

## Insertion Operation

### Insert a Key

```cpp
struct Node* insert(struct Node* node, int key) {
    // If the tree is empty, return a new node
    if (node == NULL)
        return newNode(key);
    
    // Otherwise, recur down the tree
    if (key < node->key)
        node->left = insert(node->left, key);
    else if (key > node->key)
        node->right = insert(node->right, key);
    
    // Return the (unchanged) node pointer
    return node;
}
```

```java
Node insert(Node node, int key) {
    // If the tree is empty, return a new node
    if (node == null)
        return new Node(key);
    
    // Otherwise, recur down the tree
    if (key < node.key)
        node.left = insert(node.left, key);
    else if (key > node.key)
        node.right = insert(node.right, key);
    
    // Return the (unchanged) node pointer
    return node;
}
```

```python
def insert(node, key):
    # If the tree is empty, return a new node
    if node is None:
        return Node(key)
    
    # Otherwise, recur down the tree
    if key < node.key:
        node.left = insert(node.left, key)
    elif key > node.key:
        node.right = insert(node.right, key)
    
    # Return the (unchanged) node pointer
    return node
```

**Output:**

```
20 30 40 50 60 70 80
```


### Time Complexity

O(h) where h is the height of the BST. In balanced BSTs, h = log n, giving O(log n) time complexity.

### Space Complexity

O(h) due to recursion stack, where h is the height of the tree.

## Deletion Operation

### Delete a Key

```cpp
struct Node* minValueNode(struct Node* node) {
    struct Node* current = node;
    
    // Loop down to find the leftmost leaf
    while (current->left != NULL)
        current = current->left;
    
    return current;
}

struct Node* deleteNode(struct Node* root, int key) {
    // Base case
    if (root == NULL)
        return root;
    
    // If the key to be deleted is smaller than root's key
    if (key < root->key)
        root->left = deleteNode(root->left, key);
    
    // If the key to be deleted is greater than root's key
    else if (key > root->key)
        root->right = deleteNode(root->right, key);
    
    // If key is same as root's key, this is the node to be deleted
    else {
        // Node with only one child or no child
        if (root->left == NULL) {
            struct Node* temp = root->right;
            free(root);
            return temp;
        }
        else if (root->right == NULL) {
            struct Node* temp = root->left;
            free(root);
            return temp;
        }
        
        // Node with two children: Get the inorder successor
        struct Node* temp = minValueNode(root->right);
        
        // Copy the inorder successor's content to this node
        root->key = temp->key;
        
        // Delete the inorder successor
        root->right = deleteNode(root->right, temp->key);
    }
    
    return root;
}
```

```java
Node minValueNode(Node node) {
    Node current = node;
    
    // Loop down to find the leftmost leaf
    while (current.left != null)
        current = current.left;
    
    return current;
}

Node deleteNode(Node root, int key) {
    // Base case
    if (root == null)
        return root;
    
    // If the key to be deleted is smaller than root's key
    if (key < root.key)
        root.left = deleteNode(root.left, key);
    
    // If the key to be deleted is greater than root's key
    else if (key > root.key)
        root.right = deleteNode(root.right, key);
    
    // If key is same as root's key, this is the node to be deleted
    else {
        // Node with only one child or no child
        if (root.left == null)
            return root.right;
        else if (root.right == null)
            return root.left;
        
        // Node with two children: Get the inorder successor
        Node temp = minValueNode(root.right);
        
        // Copy the inorder successor's content to this node
        root.key = temp.key;
        
        // Delete the inorder successor
        root.right = deleteNode(root.right, temp.key);
    }
    
    return root;
}
```

```python
def min_value_node(node):
    current = node
    
    # Loop down to find the leftmost leaf
    while current.left is not None:
        current = current.left
    
    return current

def delete_node(root, key):
    # Base case
    if root is None:
        return root
    
    # If the key to be deleted is smaller than root's key
    if key < root.key:
        root.left = delete_node(root.left, key)
    
    # If the key to be deleted is greater than root's key
    elif key > root.key:
        root.right = delete_node(root.right, key)
    
    # If key is same as root's key, this is the node to be deleted
    else:
        # Node with only one child or no child
        if root.left is None:
            return root.right
        elif root.right is None:
            return root.left
        
        # Node with two children: Get the inorder successor
        temp = min_value_node(root.right)
        
        # Copy the inorder successor's content to this node
        root.key = temp.key
        
        # Delete the inorder successor
        root.right = delete_node(root.right, temp.key)
    
    return root
```

**Output:**

```
Inorder traversal of the given tree
20 30 40 50 60 70 80
Delete 20
Inorder traversal of the modified tree
30 40 50 60 70 80
Delete 30
Inorder traversal of the modified tree
40 50 60 70 80
Delete 50
Inorder traversal of the modified tree
40 60 70 80
```


### Time Complexity

O(h) where h is the height of the BST. In balanced BSTs, h = log n, giving O(log n) time complexity.

### Space Complexity

O(h) due to recursion stack, where h is the height of the tree.

## Properties of BST

### Inorder Traversal

Inorder traversal of BST always produces sorted output in ascending order.

### Unique BST Count

Number of unique BSTs with n distinct keys is the nth Catalan Number.

### Construction

A BST can be constructed with only Preorder or Postorder or Level Order traversal.

### Minimum/Maximum

Minimum value is always at the leftmost node, maximum at the rightmost node.

## Applications

**Database Indexing**: BSTs and variants like B-trees used for database indexing.

**File System**: Hierarchical file system organization in operating systems.

**Priority Queues**: Implementing priority queues with efficient operations.

**Autocomplete Systems**: Storing dictionary words for prefix-based search.

**Range Queries**: Finding all elements within a specific range efficiently.

**Expression Evaluation**: Parsing and evaluating mathematical expressions.

**Network Routing**: Router tables for efficient packet routing.

**Memory Management**: Managing free memory blocks in operating systems.

**Compiler Design**: Symbol tables for storing variable and function information.

**Game Development**: Decision trees for AI behavior and game logic.

## Complete Implementation

```cpp
#include <iostream>
using namespace std;

struct Node {
    int key;
    struct Node* left;
    struct Node* right;
};

struct Node* newNode(int item) {
    Node* temp = new Node;
    temp->key = item;
    temp->left = temp->right = NULL;
    return temp;
}

void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left);
        cout << root->key << " ";
        inorder(root->right);
    }
}

struct Node* insert(struct Node* node, int key) {
    if (node == NULL)
        return newNode(key);
    
    if (key < node->key)
        node->left = insert(node->left, key);
    else if (key > node->key)
        node->right = insert(node->right, key);
    
    return node;
}

struct Node* search(struct Node* root, int key) {
    if (root == NULL || root->key == key)
        return root;
    
    if (root->key < key)
        return search(root->right, key);
    
    return search(root->left, key);
}

struct Node* minValueNode(struct Node* node) {
    struct Node* current = node;
    while (current->left != NULL)
        current = current->left;
    return current;
}

struct Node* deleteNode(struct Node* root, int key) {
    if (root == NULL)
        return root;
    
    if (key < root->key)
        root->left = deleteNode(root->left, key);
    else if (key > root->key)
        root->right = deleteNode(root->right, key);
    else {
        if (root->left == NULL) {
            struct Node* temp = root->right;
            free(root);
            return temp;
        }
        else if (root->right == NULL) {
            struct Node* temp = root->left;
            free(root);
            return temp;
        }
        
        struct Node* temp = minValueNode(root->right);
        root->key = temp->key;
        root->right = deleteNode(root->right, temp->key);
    }
    
    return root;
}

int main() {
    /* Create BST:
          50
        /    \
       30     70
      /  \   /  \
     20  40 60  80 */
    
    struct Node* root = NULL;
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 20);
    insert(root, 40);
    insert(root, 70);
    insert(root, 60);
    insert(root, 80);
    
    cout << "Inorder traversal of the given tree" << endl;
    inorder(root);
    
    cout << "\n\nDelete 20" << endl;
    root = deleteNode(root, 20);
    cout << "Inorder traversal of the modified tree" << endl;
    inorder(root);
    
    cout << "\n\nDelete 30" << endl;
    root = deleteNode(root, 30);
    cout << "Inorder traversal of the modified tree" << endl;
    inorder(root);
    
    cout << "\n\nDelete 50" << endl;
    root = deleteNode(root, 50);
    cout << "Inorder traversal of the modified tree" << endl;
    inorder(root);
    
    return 0;
}
```

```java
class Node {
    int key;
    Node left, right;
    
    Node(int val) {
        key = val;
        left = right = null;
    }
}

class BST {
    Node root;
    
    BST() {
        root = null;
    }
    
    void inorder(Node root) {
        if (root != null) {
            inorder(root.left);
            System.out.print(root.key + " ");
            inorder(root.right);
        }
    }
    
    Node insert(Node node, int key) {
        if (node == null)
            return new Node(key);
        
        if (key < node.key)
            node.left = insert(node.left, key);
        else if (key > node.key)
            node.right = insert(node.right, key);
        
        return node;
    }
    
    Node search(Node root, int key) {
        if (root == null || root.key == key)
            return root;
        
        if (root.key < key)
            return search(root.right, key);
        
        return search(root.left, key);
    }
    
    Node minValueNode(Node node) {
        Node current = node;
        while (current.left != null)
            current = current.left;
        return current;
    }
    
    Node deleteNode(Node root, int key) {
        if (root == null)
            return root;
        
        if (key < root.key)
            root.left = deleteNode(root.left, key);
        else if (key > root.key)
            root.right = deleteNode(root.right, key);
        else {
            if (root.left == null)
                return root.right;
            else if (root.right == null)
                return root.left;
            
            Node temp = minValueNode(root.right);
            root.key = temp.key;
            root.right = deleteNode(root.right, temp.key);
        }
        
        return root;
    }
    
    public static void main(String[] args) {
        BST tree = new BST();
        tree.root = tree.insert(tree.root, 50);
        tree.insert(tree.root, 30);
        tree.insert(tree.root, 20);
        tree.insert(tree.root, 40);
        tree.insert(tree.root, 70);
        tree.insert(tree.root, 60);
        tree.insert(tree.root, 80);
        
        System.out.println("Inorder traversal of the given tree");
        tree.inorder(tree.root);
        
        System.out.println("\n\nDelete 20");
        tree.root = tree.deleteNode(tree.root, 20);
        System.out.println("Inorder traversal of the modified tree");
        tree.inorder(tree.root);
        
        System.out.println("\n\nDelete 30");
        tree.root = tree.deleteNode(tree.root, 30);
        System.out.println("Inorder traversal of the modified tree");
        tree.inorder(tree.root);
        
        System.out.println("\n\nDelete 50");
        tree.root = tree.deleteNode(tree.root, 50);
        System.out.println("Inorder traversal of the modified tree");
        tree.inorder(tree.root);
    }
}
```

```python
class Node:
    def __init__(self, val):
        self.key = val
        self.left = None
        self.right = None

class BST:
    def __init__(self):
        self.root = None
    
    def inorder(self, root):
        if root:
            self.inorder(root.left)
            print(root.key, end=" ")
            self.inorder(root.right)
    
    def insert(self, node, key):
        if node is None:
            return Node(key)
        
        if key < node.key:
            node.left = self.insert(node.left, key)
        elif key > node.key:
            node.right = self.insert(node.right, key)
        
        return node
    
    def search(self, root, key):
        if root is None or root.key == key:
            return root
        
        if root.key < key:
            return self.search(root.right, key)
        
        return self.search(root.left, key)
    
    def min_value_node(self, node):
        current = node
        while current.left is not None:
            current = current.left
        return current
    
    def delete_node(self, root, key):
        if root is None:
            return root
        
        if key < root.key:
            root.left = self.delete_node(root.left, key)
        elif key > root.key:
            root.right = self.delete_node(root.right, key)
        else:
            if root.left is None:
                return root.right
            elif root.right is None:
                return root.left
            
            temp = self.min_value_node(root.right)
            root.key = temp.key
            root.right = self.delete_node(root.right, temp.key)
        
        return root

# Main program
tree = BST()
tree.root = tree.insert(tree.root, 50)
tree.insert(tree.root, 30)
tree.insert(tree.root, 20)
tree.insert(tree.root, 40)
tree.insert(tree.root, 70)
tree.insert(tree.root, 60)
tree.insert(tree.root, 80)

print("Inorder traversal of the given tree")
tree.inorder(tree.root)

print("\n\nDelete 20")
tree.root = tree.delete_node(tree.root, 20)
print("Inorder traversal of the modified tree")
tree.inorder(tree.root)

print("\n\nDelete 30")
tree.root = tree.delete_node(tree.root, 30)
print("Inorder traversal of the modified tree")
tree.inorder(tree.root)

print("\n\nDelete 50")
tree.root = tree.delete_node(tree.root, 50)
print("Inorder traversal of the modified tree")
tree.inorder(tree.root)
```

**Output:**

```
Inorder traversal of the given tree
20 30 40 50 60 70 80

Delete 20
Inorder traversal of the modified tree
30 40 50 60 70 80

Delete 30
Inorder traversal of the modified tree
40 50 60 70 80

Delete 50
Inorder traversal of the modified tree
40 60 70 80
```

This comprehensive editorial covers Binary Search Trees following the doubly linked list format with complete code implementations in C++, Java, and Python, including outputs for each section.