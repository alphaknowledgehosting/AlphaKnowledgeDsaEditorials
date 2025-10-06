
# Arrays: Complete Guide

An array is a data structure that stores a collection of elements of the same data type at contiguous memory locations. This allows efficient access to elements using their index position, making arrays one of the fundamental data structures in computer science.

## Structure of an Array

An array consists of elements stored sequentially in memory where each element occupies a fixed amount of space determined by its data type.

**Data Elements**: Stores the actual values of the same data type.

**Index**: The position identifier for each element, ranging from 0 to size-1.

**Contiguous Memory**: All elements are stored in adjacent memory locations.

### Declaration and Initialization

```cpp
// C++ Array Declaration
int arr;  // declares array of size 5

// Array Initialization
int arr = {10, 20, 30, 40, 50};

// Size can be omitted during initialization
int arr[] = {10, 20, 30, 40, 50};
```

```java
// Java Array Declaration
int[] arr = new int[];

// Array Initialization
int[] arr = {10, 20, 30, 40, 50};

// Two-step declaration
int[] arr;
arr = new int[] ;
```

```python
# Python Array (List) Declaration
arr = [None] * 5  # creates array of size 5

# Array Initialization
arr = [10, 20, 30, 40, 50]

# Empty array
arr = []
```


## Advantages

**Random Access**: Elements can be accessed directly using their index in O(1) time.  

**Cache Locality**: Contiguous memory allocation provides better cache performance. 

**Memory Efficiency**: No extra memory required for pointers or references.

**Simple Implementation**: Easy to understand and implement compared to complex data structures.

**Fixed Memory Allocation**: Memory is allocated once during declaration.

## Disadvantages

**Fixed Size**: Array size cannot be changed after declaration in static arrays.

**Costly Insertion/Deletion**: Requires shifting elements, resulting in O(n) time complexity.[^10]

**Memory Waste**: Unused allocated space cannot be utilized by other variables.

**Contiguous Memory Requirement**: Large arrays may fail to allocate if contiguous memory is unavailable.

**Same Data Type**: Can only store elements of the same data type.

## Creating an Array

### Implementation

```cpp
#include <iostream>
using namespace std;

int main() {
    // Creating and initializing array
    int arr[]  = {10, 20, 30, 40, 50};
    
    // Displaying array elements
    cout << "Array elements: ";
    for (int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```

```java
public class ArrayExample {
    public static void main(String[] args) {
        // Creating and initializing array
        int[] arr = {10, 20, 30, 40, 50};
        
        // Displaying array elements
        System.out.print("Array elements: ");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
    }
}
```

```python
# Creating and initializing array
arr = [10, 20, 30, 40, 50]

# Displaying array elements
print("Array elements:", end=" ")
for element in arr:
    print(element, end=" ")
print()
```


## Traversal Operations

### Forward Traversal

```cpp
void traverseArray(int arr[], int n) {
    if (n == 0) {
        cout << "Array is empty" << endl;
        return;
    }
    
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}
```

```java
void traverseArray(int[] arr) {
    if (arr.length == 0) {
        System.out.println("Array is empty");
        return;
    }
    
    for (int i = 0; i < arr.length; i++) {
        System.out.print(arr[i] + " ");
    }
    System.out.println();
}
```

```python
def traverse_array(arr):
    if len(arr) == 0:
        print("Array is empty")
        return
    
    for element in arr:
        print(element, end=" ")
    print()
```


### Time Complexity

O(n) where n is the number of elements in the array.

### Space Complexity

O(1) as only a constant amount of extra space is used.

## Insertion Operations

### Insert at End

```cpp
bool insertAtEnd(int arr[], int &n, int capacity, int element) {
    if (n >= capacity) {
        cout << "Array is full" << endl;
        return false;
    }
    
    arr[n] = element;
    n++;
    return true;
}
```

```java
boolean insertAtEnd(int[] arr, int n, int element) {
    if (n >= arr.length) {
        System.out.println("Array is full");
        return false;
    }
    
    arr[n] = element;
    return true;
}
```

```python
def insert_at_end(arr, element):
    arr.append(element)
    return True
```


### Time Complexity

O(1) as the element is directly inserted at the end.[^10]

### Space Complexity

O(1) as no extra space is needed.

### Insert at Position

```cpp
bool insertAtPosition(int arr[], int &n, int capacity, int pos, int element) {
    if (n >= capacity) {
        cout << "Array is full" << endl;
        return false;
    }
    
    if (pos < 0 || pos > n) {
        cout << "Invalid position" << endl;
        return false;
    }
    
    // Shift elements to the right
    for (int i = n - 1; i >= pos; i--) {
        arr[i + 1] = arr[i];
    }
    
    arr[pos] = element;
    n++;
    return true;
}
```

```java
boolean insertAtPosition(int[] arr, int n, int pos, int element) {
    if (n >= arr.length) {
        System.out.println("Array is full");
        return false;
    }
    
    if (pos < 0 || pos > n) {
        System.out.println("Invalid position");
        return false;
    }
    
    // Shift elements to the right
    for (int i = n - 1; i >= pos; i--) {
        arr[i + 1] = arr[i];
    }
    
    arr[pos] = element;
    return true;
}
```

```python
def insert_at_position(arr, pos, element):
    if pos < 0 or pos > len(arr):
        print("Invalid position")
        return False
    
    arr.insert(pos, element)
    return True
```


### Time Complexity

O(n) in worst case when inserting at the beginning, as all elements need to be shifted.[^10]

### Space Complexity

O(1) as no extra space is needed.

## Deletion Operations

### Delete at End

```cpp
bool deleteAtEnd(int arr[], int &n) {
    if (n == 0) {
        cout << "Array is empty" << endl;
        return false;
    }
    
    n--;
    return true;
}
```

```java
boolean deleteAtEnd(int n) {
    if (n == 0) {
        System.out.println("Array is empty");
        return false;
    }
    
    return true;
}
```

```python
def delete_at_end(arr):
    if len(arr) == 0:
        print("Array is empty")
        return False
    
    arr.pop()
    return True
```


### Time Complexity

O(1) as only the size pointer is decremented.

### Space Complexity

O(1) as no extra space is needed.

### Delete at Position

```cpp
bool deleteAtPosition(int arr[], int &n, int pos) {
    if (n == 0) {
        cout << "Array is empty" << endl;
        return false;
    }
    
    if (pos < 0 || pos >= n) {
        cout << "Invalid position" << endl;
        return false;
    }
    
    // Shift elements to the left
    for (int i = pos; i < n - 1; i++) {
        arr[i] = arr[i + 1];
    }
    
    n--;
    return true;
}
```

```java
boolean deleteAtPosition(int[] arr, int n, int pos) {
    if (n == 0) {
        System.out.println("Array is empty");
        return false;
    }
    
    if (pos < 0 || pos >= n) {
        System.out.println("Invalid position");
        return false;
    }
    
    // Shift elements to the left
    for (int i = pos; i < n - 1; i++) {
        arr[i] = arr[i + 1];
    }
    
    return true;
}
```

```python
def delete_at_position(arr, pos):
    if len(arr) == 0:
        print("Array is empty")
        return False
    
    if pos < 0 or pos >= len(arr):
        print("Invalid position")
        return False
    
    arr.pop(pos)
    return True
```


### Time Complexity

O(n) in worst case when deleting from the beginning, as all elements need to be shifted.[^10]

### Space Complexity

O(1) as no extra space is needed.

### Delete by Value

```cpp
bool deleteByValue(int arr[], int &n, int value) {
    int pos = -1;
    
    // Search for the element
    for (int i = 0; i < n; i++) {
        if (arr[i] == value) {
            pos = i;
            break;
        }
    }
    
    if (pos == -1) {
        cout << "Element not found" << endl;
        return false;
    }
    
    return deleteAtPosition(arr, n, pos);
}
```

```java
boolean deleteByValue(int[] arr, int n, int value) {
    int pos = -1;
    
    // Search for the element
    for (int i = 0; i < n; i++) {
        if (arr[i] == value) {
            pos = i;
            break;
        }
    }
    
    if (pos == -1) {
        System.out.println("Element not found");
        return false;
    }
    
    return deleteAtPosition(arr, n, pos);
}
```

```python
def delete_by_value(arr, value):
    try:
        arr.remove(value)
        return True
    except ValueError:
        print("Element not found")
        return False
```


### Time Complexity

O(n) as the element needs to be searched and then elements shifted.[^10]

### Space Complexity

O(1) as no extra space is needed.

## Search Operations

### Linear Search

```cpp
int linearSearch(int arr[], int n, int key) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == key) {
            return i;
        }
    }
    return -1;
}
```

```java
int linearSearch(int[] arr, int key) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == key) {
            return i;
        }
    }
    return -1;
}
```

```python
def linear_search(arr, key):
    for i in range(len(arr)):
        if arr[i] == key:
            return i
    return -1
```


### Time Complexity

O(n) where n is the number of elements in the array.[^10]

### Space Complexity

O(1) as no extra space is needed.

### Binary Search

```cpp
int binarySearch(int arr[], int n, int key) {
    int left = 0, right = n - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (arr[mid] == key)
            return mid;
        
        if (arr[mid] < key)
            left = mid + 1;
        else
            right = mid - 1;
    }
    
    return -1;
}
```

```java
int binarySearch(int[] arr, int key) {
    int left = 0, right = arr.length - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (arr[mid] == key)
            return mid;
        
        if (arr[mid] < key)
            left = mid + 1;
        else
            right = mid - 1;
    }
    
    return -1;
}
```

```python
def binary_search(arr, key):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = left + (right - left) // 2
        
        if arr[mid] == key:
            return mid
        
        if arr[mid] < key:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1
```


### Time Complexity

O(log n) for binary search in a sorted array.

### Space Complexity

O(1) as no extra space is needed.

## Reverse Operations

### Reverse Array

```cpp
void reverseArray(int arr[], int n) {
    int start = 0, end = n - 1;
    
    while (start < end) {
        // Swap elements
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        
        start++;
        end--;
    }
}
```

```java
void reverseArray(int[] arr) {
    int start = 0, end = arr.length - 1;
    
    while (start < end) {
        // Swap elements
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        
        start++;
        end--;
    }
}
```

```python
def reverse_array(arr):
    start, end = 0, len(arr) - 1
    
    while start < end:
        # Swap elements
        arr[start], arr[end] = arr[end], arr[start]
        start += 1
        end -= 1
```


### Time Complexity

O(n) where n is the number of elements.

### Space Complexity

O(1) as the reversal is done in-place.

## Applications

**Storing Data**: Arrays store multiple values of the same type efficiently.

**Sorting Algorithms**: Most sorting algorithms like QuickSort, MergeSort work on arrays.

**Matrix Operations**: 2D arrays represent matrices for mathematical computations.

**Lookup Tables**: Arrays store precomputed values for quick retrieval.

**Buffer Implementation**: Arrays serve as buffers in I/O operations and data streaming.

**Stack and Queue**: Arrays implement these fundamental data structures.

**Dynamic Programming**: Arrays store intermediate results in DP problems.

## Complete Implementation

```cpp
#include <iostream>
using namespace std;

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

bool insertAtPosition(int arr[], int &n, int capacity, int pos, int element) {
    if (n >= capacity) {
        cout << "Array is full" << endl;
        return false;
    }
    
    if (pos < 0 || pos > n) {
        cout << "Invalid position" << endl;
        return false;
    }
    
    for (int i = n - 1; i >= pos; i--) {
        arr[i + 1] = arr[i];
    }
    
    arr[pos] = element;
    n++;
    return true;
}

bool deleteAtPosition(int arr[], int &n, int pos) {
    if (n == 0) {
        cout << "Array is empty" << endl;
        return false;
    }
    
    if (pos < 0 || pos >= n) {
        cout << "Invalid position" << endl;
        return false;
    }
    
    for (int i = pos; i < n - 1; i++) {
        arr[i] = arr[i + 1];
    }
    
    n--;
    return true;
}

int linearSearch(int arr[], int n, int key) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == key) {
            return i;
        }
    }
    return -1;
}

int main() {
    int arr[^10] = {10, 20, 30, 40, 50};
    int n = 5;
    int capacity = 10;
    
    cout << "Original array: ";
    printArray(arr, n);
    
    insertAtPosition(arr, n, capacity, 2, 25);
    cout << "After inserting 25 at position 2: ";
    printArray(arr, n);
    
    deleteAtPosition(arr, n, 4);
    cout << "After deleting at position 4: ";
    printArray(arr, n);
    
    int key = 25;
    int index = linearSearch(arr, n, key);
    if (index != -1)
        cout << "Element " << key << " found at index: " << index << endl;
    else
        cout << "Element not found" << endl;
    
    return 0;
}
```

**Output:**

```
Original array: 10 20 30 40 50 
After inserting 25 at position 2: 10 20 25 30 40 50 
After deleting at position 4: 10 20 25 30 50 
Element 25 found at index: 2
```

```java
public class ArrayOperations {
    
    static void printArray(int[] arr, int n) {
        for (int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
    }
    
    static int insertAtPosition(int[] arr, int n, int pos, int element) {
        if (n >= arr.length) {
            System.out.println("Array is full");
            return n;
        }
        
        if (pos < 0 || pos > n) {
            System.out.println("Invalid position");
            return n;
        }
        
        for (int i = n - 1; i >= pos; i--) {
            arr[i + 1] = arr[i];
        }
        
        arr[pos] = element;
        return n + 1;
    }
    
    static int deleteAtPosition(int[] arr, int n, int pos) {
        if (n == 0) {
            System.out.println("Array is empty");
            return n;
        }
        
        if (pos < 0 || pos >= n) {
            System.out.println("Invalid position");
            return n;
        }
        
        for (int i = pos; i < n - 1; i++) {
            arr[i] = arr[i + 1];
        }
        
        return n - 1;
    }
    
    static int linearSearch(int[] arr, int n, int key) {
        for (int i = 0; i < n; i++) {
            if (arr[i] == key) {
                return i;
            }
        }
        return -1;
    }
    
    public static void main(String[] args) {
        int[] arr = new int[10];
        arr[^0] = 10; arr  = 20; arr  = 30; arr  = 40; arr  = 50;
        int n = 5;
        
        System.out.print("Original array: ");
        printArray(arr, n);
        
        n = insertAtPosition(arr, n, 2, 25);
        System.out.print("After inserting 25 at position 2: ");
        printArray(arr, n);
        
        n = deleteAtPosition(arr, n, 4);
        System.out.print("After deleting at position 4: ");
        printArray(arr, n);
        
        int key = 25;
        int index = linearSearch(arr, n, key);
        if (index != -1)
            System.out.println("Element " + key + " found at index: " + index);
        else
            System.out.println("Element not found");
    }
}
```

**Output:**

```
Original array: 10 20 30 40 50 
After inserting 25 at position 2: 10 20 25 30 40 50 
After deleting at position 4: 10 20 25 30 50 
Element 25 found at index: 2
```

```python
def print_array(arr):
    for element in arr:
        print(element, end=" ")
    print()

def insert_at_position(arr, pos, element):
    if pos < 0 or pos > len(arr):
        print("Invalid position")
        return False
    
    arr.insert(pos, element)
    return True

def delete_at_position(arr, pos):
    if len(arr) == 0:
        print("Array is empty")
        return False
    
    if pos < 0 or pos >= len(arr):
        print("Invalid position")
        return False
    
    arr.pop(pos)
    return True

def linear_search(arr, key):
    for i in range(len(arr)):
        if arr[i] == key:
            return i
    return -1

# Main program
arr = [10, 20, 30, 40, 50]

print("Original array: ", end="")
print_array(arr)

insert_at_position(arr, 2, 25)
print("After inserting 25 at position 2: ", end="")
print_array(arr)

delete_at_position(arr, 4)
print("After deleting at position 4: ", end="")
print_array(arr)

key = 25
index = linear_search(arr, key)
if index != -1:
    print(f"Element {key} found at index: {index}")
else:
    print("Element not found")
```

**Output:**

```
Original array: 10 20 30 40 50 
After inserting 25 at position 2: 10 20 25 30 40 50 
After deleting at position 4: 10 20 25 30 50 
Element 25 found at index: 2
```

This editorial provides a comprehensive guide to arrays following the circular linked list format, with no external references and complete code implementations in C++, Java, and Python.