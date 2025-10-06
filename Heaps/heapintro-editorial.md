# Heaps: Complete Guide

A heap is a specialized tree-based data structure that satisfies the heap property. It is a complete binary tree where each node follows a specific ordering relationship with its children. Heaps are commonly used to implement priority queues and for efficient sorting algorithms.

## Structure of a Heap

A heap is a complete binary tree that can be efficiently represented using an array.

**Complete Binary Tree**: All levels are completely filled except possibly the last level, which has all nodes as far left as possible.

**Heap Property**: In a Max-Heap, each parent node is greater than or equal to its children. In a Min-Heap, each parent node is less than or equal to its children.

**Array Representation**: The root element is at index 0, and for any node at index i, its left child is at index (2*i + 1) and right child is at index (2*i + 2).

**Parent Node**: For any node at index i, its parent is at index (i-1)/2.

### Declaration

```cpp
// Min Heap in C++
class MinHeap {
    int *harr;        // pointer to array of elements
    int capacity;     // maximum possible size
    int heap_size;    // current number of elements
    
public:
    MinHeap(int capacity);
    void MinHeapify(int i);
    int parent(int i) { return (i-1)/2; }
    int left(int i) { return (2*i + 1); }
    int right(int i) { return (2*i + 2); }
    int extractMin();
    void decreaseKey(int i, int new_val);
    int getMin() { return harr[0]; }
    void deleteKey(int i);
    void insertKey(int k);
};
```

```java
// Min Heap in Java
class MinHeap {
    private int[] harr;
    private int capacity;
    private int heap_size;
    
    public MinHeap(int cap) {
        heap_size = 0;
        capacity = cap;
        harr = new int[cap];
    }
    
    int parent(int i) { return (i-1)/2; }
    int left(int i) { return (2*i + 1); }
    int right(int i) { return (2*i + 2); }
    int getMin() { return harr[0]; }
    void insertKey(int k);
    void decreaseKey(int i, int new_val);
    int extractMin();
    void deleteKey(int i);
    void MinHeapify(int i);
}
```

```python
# Min Heap in Python
class MinHeap:
    def __init__(self, capacity):
        self.heap_size = 0
        self.capacity = capacity
        self.harr = [0] * capacity
    
    def parent(self, i):
        return (i - 1) // 2
    
    def left(self, i):
        return 2 * i + 1
    
    def right(self, i):
        return 2 * i + 2
    
    def get_min(self):
        return self.harr[0]
    
    def insert_key(self, k):
        pass
    
    def decrease_key(self, i, new_val):
        pass
    
    def extract_min(self):
        pass
    
    def delete_key(self, i):
        pass
    
    def min_heapify(self, i):
        pass
```


## Advantages

**Efficient Priority Queue**: Provides O(log n) insertion and O(1) access to min/max element.

**Complete Binary Tree**: Efficient array representation without wasted space.

**Fast Extract Operations**: O(log n) time to extract minimum or maximum element.

**Heap Sort**: Enables O(n log n) in-place sorting algorithm.

**Memory Efficient**: Array representation uses less memory than pointer-based structures.

**Predictable Performance**: Guaranteed logarithmic time for insert, delete, and extract operations.

## Disadvantages

**No Fast Search**: Searching for arbitrary elements takes O(n) time.

**Not Sorted**: Elements are not fully sorted, only partially ordered.

**Fixed Array Size**: Array-based implementation requires predefined capacity.

**Complex Maintenance**: Heapify operations needed to maintain heap property.

**No Random Access**: Cannot efficiently access elements by rank or position.

## Types of Heaps

### Max-Heap

Each parent node has a value greater than or equal to its children. The maximum element is at the root.

### Min-Heap

Each parent node has a value less than or equal to its children. The minimum element is at the root.

## Building a Heap

### Build Heap from Array

```cpp
void heapify(int arr[], int n, int i) {
    int largest = i;
    int l = 2 * i + 1;
    int r = 2 * i + 2;
    
    if (l < n && arr[l] > arr[largest])
        largest = l;
    
    if (r < n && arr[r] > arr[largest])
        largest = r;
    
    if (largest != i) {
        swap(arr[i], arr[largest]);
        heapify(arr, n, largest);
    }
}

void buildHeap(int arr[], int n) {
    int startIdx = (n - 2) / 2;
    
    for (int i = startIdx; i >= 0; i--) {
        heapify(arr, n, i);
    }
}
```

```java
void heapify(int arr[], int n, int i) {
    int largest = i;
    int l = 2 * i + 1;
    int r = 2 * i + 2;
    
    if (l < n && arr[l] > arr[largest])
        largest = l;
    
    if (r < n && arr[r] > arr[largest])
        largest = r;
    
    if (largest != i) {
        int temp = arr[i];
        arr[i] = arr[largest];
        arr[largest] = temp;
        
        heapify(arr, n, largest);
    }
}

void buildHeap(int arr[], int n) {
    int startIdx = (n - 2) / 2;
    
    for (int i = startIdx; i >= 0; i--) {
        heapify(arr, n, i);
    }
}
```

```python
def heapify(arr, n, i):
    largest = i
    l = 2 * i + 1
    r = 2 * i + 2
    
    if l < n and arr[l] > arr[largest]:
        largest = l
    
    if r < n and arr[r] > arr[largest]:
        largest = r
    
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)

def build_heap(arr, n):
    start_idx = (n - 2) // 2
    
    for i in range(start_idx, -1, -1):
        heapify(arr, n, i)
```

**Output:**

```
Array representation of Heap is:
17 15 13 9 6 5 10 4 8 3 1
```


### Time Complexity

O(n) for building a heap from an array using the optimized approach.

### Space Complexity

O(log n) due to recursion stack for heapify operations.

## Insertion Operation

### Insert Key

```cpp
void MinHeap::insertKey(int k) {
    if (heap_size == capacity) {
        cout << "\nOverflow: Could not insertKey\n";
        return;
    }
    
    heap_size++;
    int i = heap_size - 1;
    harr[i] = k;
    
    while (i != 0 && harr[parent(i)] > harr[i]) {
        swap(harr[i], harr[parent(i)]);
        i = parent(i);
    }
}
```

```java
void insertKey(int k) {
    if (heap_size == capacity) {
        System.out.println("\nOverflow: Could not insertKey");
        return;
    }
    
    heap_size++;
    int i = heap_size - 1;
    harr[i] = k;
    
    while (i != 0 && harr[parent(i)] > harr[i]) {
        int temp = harr[i];
        harr[i] = harr[parent(i)];
        harr[parent(i)] = temp;
        i = parent(i);
    }
}
```

```python
def insert_key(self, k):
    if self.heap_size == self.capacity:
        print("\nOverflow: Could not insertKey")
        return
    
    self.heap_size += 1
    i = self.heap_size - 1
    self.harr[i] = k
    
    while i != 0 and self.harr[self.parent(i)] > self.harr[i]:
        self.harr[i], self.harr[self.parent(i)] = self.harr[self.parent(i)], self.harr[i]
        i = self.parent(i)
```

**Output:**

```
15 5 10 2 4 3
```


### Time Complexity

O(log n) where n is the number of elements in the heap, as we may need to traverse up to the root.

### Space Complexity

O(1) as insertion is done iteratively without recursion.

## Extraction Operation

### Extract Min (or Max)

```cpp
int MinHeap::extractMin() {
    if (heap_size <= 0)
        return INT_MAX;
    if (heap_size == 1) {
        heap_size--;
        return harr[0];
    }
    
    int root = harr[0];
    harr[0] = harr[heap_size - 1];
    heap_size--;
    MinHeapify(0);
    
    return root;
}

void MinHeap::MinHeapify(int i) {
    int l = left(i);
    int r = right(i);
    int smallest = i;
    
    if (l < heap_size && harr[l] < harr[i])
        smallest = l;
    if (r < heap_size && harr[r] < harr[smallest])
        smallest = r;
    
    if (smallest != i) {
        swap(harr[i], harr[smallest]);
        MinHeapify(smallest);
    }
}
```

```java
int extractMin() {
    if (heap_size <= 0)
        return Integer.MAX_VALUE;
    if (heap_size == 1) {
        heap_size--;
        return harr[0];
    }
    
    int root = harr[0];
    harr[0] = harr[heap_size - 1];
    heap_size--;
    MinHeapify(0);
    
    return root;
}

void MinHeapify(int i) {
    int l = left(i);
    int r = right(i);
    int smallest = i;
    
    if (l < heap_size && harr[l] < harr[i])
        smallest = l;
    if (r < heap_size && harr[r] < harr[smallest])
        smallest = r;
    
    if (smallest != i) {
        int temp = harr[i];
        harr[i] = harr[smallest];
        harr[smallest] = temp;
        MinHeapify(smallest);
    }
}
```

```python
def extract_min(self):
    if self.heap_size <= 0:
        return float('inf')
    if self.heap_size == 1:
        self.heap_size -= 1
        return self.harr[0]
    
    root = self.harr[0]
    self.harr[0] = self.harr[self.heap_size - 1]
    self.heap_size -= 1
    self.min_heapify(0)
    
    return root

def min_heapify(self, i):
    l = self.left(i)
    r = self.right(i)
    smallest = i
    
    if l < self.heap_size and self.harr[l] < self.harr[i]:
        smallest = l
    if r < self.heap_size and self.harr[r] < self.harr[smallest]:
        smallest = r
    
    if smallest != i:
        self.harr[i], self.harr[smallest] = self.harr[smallest], self.harr[i]
        self.min_heapify(smallest)
```

**Output:**

```
2 4 1
```


### Time Complexity

O(log n)

Reason: In the worst case, you need to bubble down the new root all the way to a leaf in a binary heap.

The height of a binary heap with n elements is log n.

### Space Complexity:

O(1) (Iterative implementation)
O(log n) (Recursive implementation due to call stack)
