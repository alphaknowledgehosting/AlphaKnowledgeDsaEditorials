# Searching Algorithms: Complete Guide

Searching algorithms are fundamental techniques used to locate specific elements within a data structure. These algorithms vary in efficiency and applicability depending on whether the data is sorted or unsorted. The two primary searching methods are Linear Search and Binary Search.

## Linear Search

Linear Search is a sequential search algorithm that examines each element in a list from the beginning until the target element is found or the end of the list is reached.

**Sequential Access**: Checks each element one by one from start to end.

**No Prerequisite**: Works on both sorted and unsorted arrays.

**Simple Implementation**: Easy to understand and implement with minimal code.

**Time Complexity**: O(n) in worst case where n is the number of elements.

### Declaration

```cpp
// Linear Search in C++
int search(int arr[], int N, int x) {
    for (int i = 0; i < N; i++)
        if (arr[i] == x)
            return i;
    return -1;
}
```

```java
// Linear Search in Java
public static int search(int arr[], int x) {
    int N = arr.length;
    for (int i = 0; i < N; i++) {
        if (arr[i] == x)
            return i;
    }
    return -1;
}
```

```python
# Linear Search in Python
def search(arr, x):
    N = len(arr)
    for i in range(N):
        if arr[i] == x:
            return i
    return -1
```


## Advantages of Linear Search

**Works on Unsorted Data**: Can be applied to arrays regardless of sorting.

**No Extra Memory**: Requires no additional memory allocation.

**Simple Implementation**: Easy to code and understand for beginners.

**Small Dataset Efficiency**: Well-suited for small collections of data.

**Flexible Data Types**: Works with any comparable data type.

## Disadvantages of Linear Search

**Slow for Large Data**: O(n) time complexity makes it inefficient for large datasets.

**No Optimization**: Cannot take advantage of sorted data properties.

**Performance Issues**: Linear growth in time as dataset size increases.

**Not Scalable**: Poor performance with increasing data volume.

## Linear Search Implementation

### Complete Implementation

```cpp
#include <bits/stdc++.h>
using namespace std;

int search(int arr[], int N, int x) {
    for (int i = 0; i < N; i++)
        if (arr[i] == x)
            return i;
    return -1;
}

int main(void) {
    int arr[] = { 2, 3, 4, 10, 40 };
    int x = 10;
    int N = sizeof(arr) / sizeof(arr[0]);
    
    int result = search(arr, N, x);
    (result == -1)
        ? cout << "Element is not present in array"
        : cout << "Element is present at index " << result;
    return 0;
}
```

```java
public class LinearSearch {
    public static int search(int arr[], int x) {
        int N = arr.length;
        for (int i = 0; i < N; i++) {
            if (arr[i] == x)
                return i;
        }
        return -1;
    }
    
    public static void main(String args[]) {
        int arr[] = { 2, 3, 4, 10, 40 };
        int x = 10;
        
        int result = search(arr, x);
        if (result == -1)
            System.out.println("Element is not present in array");
        else
            System.out.println("Element is present at index " + result);
    }
}
```

```python
def search(arr, x):
    N = len(arr)
    for i in range(N):
        if arr[i] == x:
            return i
    return -1

arr = [2, 3, 4, 10, 40]
x = 10

result = search(arr, x)
if result == -1:
    print("Element is not present in array")
else:
    print(f"Element is present at index {result}")
```

**Output:**

```
Element is present at index 3
```


### Time Complexity

O(n) where n is the number of elements in the array.

### Space Complexity

O(1) as no extra space is used.

## Binary Search

Binary Search is an efficient searching algorithm that works on sorted arrays by repeatedly dividing the search interval in half. It compares the target value with the middle element and eliminates half of the remaining elements in each iteration.

**Sorted Data Required**: Only works on sorted arrays or lists.

**Divide and Conquer**: Divides search space in half at each step.

**Logarithmic Time**: O(log n) time complexity for efficient searching.

**Two Approaches**: Can be implemented iteratively or recursively.

### How Binary Search Works

**Step 1**: Set low index to first element and high index to last element.

**Step 2**: Calculate middle index as (low + high) / 2.

**Step 3**: Compare target with middle element.

**Step 4**: If target equals middle element, return middle index.

**Step 5**: If target is less than middle, search left half.

**Step 6**: If target is greater than middle, search right half.

**Step 7**: Repeat until target is found or search space is exhausted.

## Advantages of Binary Search

**Fast Search**: O(log n) time complexity for large datasets.

**Efficient**: Much faster than linear search for sorted data.

**Predictable Performance**: Logarithmic growth with increasing data size.

**Building Block**: Used in complex algorithms and data structures.

**Scalable**: Handles large datasets efficiently.

## Disadvantages of Binary Search

**Requires Sorted Data**: Array must be sorted before searching.

**Sorting Overhead**: O(n log n) time needed to sort unsorted data.

**Memory Constraints**: Requires contiguous memory for array storage.

**Comparable Elements**: Elements must be orderable.

**Not Always Optimal**: Hash tables may be faster for very large datasets.

## Iterative Binary Search

### Implementation

```cpp
#include <bits/stdc++.h>
using namespace std;

int binarySearch(int arr[], int l, int r, int x) {
    while (l <= r) {
        int m = l + (r - l) / 2;
        
        if (arr[m] == x)
            return m;
        
        if (arr[m] < x)
            l = m + 1;
        else
            r = m - 1;
    }
    
    return -1;
}

int main(void) {
    int arr[] = { 2, 3, 4, 10, 40 };
    int x = 10;
    int n = sizeof(arr) / sizeof(arr[0]);
    int result = binarySearch(arr, 0, n - 1, x);
    (result == -1)
        ? cout << "Element is not present in array"
        : cout << "Element is present at index " << result;
    return 0;
}
```

```java
public class BinarySearch {
    public static int binarySearch(int arr[], int l, int r, int x) {
        while (l <= r) {
            int m = l + (r - l) / 2;
            
            if (arr[m] == x)
                return m;
            
            if (arr[m] < x)
                l = m + 1;
            else
                r = m - 1;
        }
        
        return -1;
    }
    
    public static void main(String args[]) {
        int arr[] = { 2, 3, 4, 10, 40 };
        int x = 10;
        int result = binarySearch(arr, 0, arr.length - 1, x);
        if (result == -1)
            System.out.println("Element is not present in array");
        else
            System.out.println("Element is present at index " + result);
    }
}
```

```python
def binary_search(arr, l, r, x):
    while l <= r:
        m = l + (r - l) // 2
        
        if arr[m] == x:
            return m
        
        if arr[m] < x:
            l = m + 1
        else:
            r = m - 1
    
    return -1

arr = [2, 3, 4, 10, 40]
x = 10
result = binary_search(arr, 0, len(arr) - 1, x)

if result == -1:
    print("Element is not present in array")
else:
    print(f"Element is present at index {result}")
```

**Output:**

```
Element is present at index 3
```


### Time Complexity

O(log n) where n is the number of elements in the array.

### Space Complexity

O(1) as no extra space is used in iterative approach.

## Recursive Binary Search

### Implementation

```cpp
#include <bits/stdc++.h>
using namespace std;

int binarySearch(int arr[], int l, int r, int x) {
    if (r >= l) {
        int mid = l + (r - l) / 2;
        
        if (arr[mid] == x)
            return mid;
        
        if (arr[mid] > x)
            return binarySearch(arr, l, mid - 1, x);
        
        return binarySearch(arr, mid + 1, r, x);
    }
    
    return -1;
}

int main() {
    int arr[] = { 2, 3, 4, 10, 40 };
    int x = 10;
    int n = sizeof(arr) / sizeof(arr[0]);
    int result = binarySearch(arr, 0, n - 1, x);
    (result == -1)
        ? cout << "Element is not present in array"
        : cout << "Element is present at index " << result;
    return 0;
}
```

```java
public class RecursiveBinarySearch {
    public static int binarySearch(int arr[], int l, int r, int x) {
        if (r >= l) {
            int mid = l + (r - l) / 2;
            
            if (arr[mid] == x)
                return mid;
            
            if (arr[mid] > x)
                return binarySearch(arr, l, mid - 1, x);
            
            return binarySearch(arr, mid + 1, r, x);
        }
        
        return -1;
    }
    
    public static void main(String args[]) {
        int arr[] = { 2, 3, 4, 10, 40 };
        int x = 10;
        int result = binarySearch(arr, 0, arr.length - 1, x);
        if (result == -1)
            System.out.println("Element is not present in array");
        else
            System.out.println("Element is present at index " + result);
    }
}
```

```python
def binary_search(arr, l, r, x):
    if r >= l:
        mid = l + (r - l) // 2
        
        if arr[mid] == x:
            return mid
        
        if arr[mid] > x:
            return binary_search(arr, l, mid - 1, x)
        
        return binary_search(arr, mid + 1, r, x)
    
    return -1

arr = [2, 3, 4, 10, 40]
x = 10
result = binary_search(arr, 0, len(arr) - 1, x)

if result == -1:
    print("Element is not present in array")
else:
    print(f"Element is present at index {result}")
```

**Output:**

```
Element is present at index 3
```


### Time Complexity

O(log n) where n is the number of elements in the array.

### Space Complexity

O(log n) due to recursive call stack.

## Built-in Binary Search Methods

### C++ STL Functions

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> vec = {10, 15, 20, 25, 30, 35};
    
    // binary_search()
    if (binary_search(vec.begin(), vec.end(), 15))
        cout << "15 exists in vector" << endl;
    else
        cout << "15 does not exist" << endl;
    
    // lower_bound()
    vector<int>::iterator low = lower_bound(vec.begin(), vec.end(), 20);
    cout << "lower_bound for element 20 at position: " 
         << (low - vec.begin()) << endl;
    
    // upper_bound()
    vector<int>::iterator up = upper_bound(vec.begin(), vec.end(), 35);
    cout << "upper_bound for element 35 at position: " 
         << (up - vec.begin()) << endl;
    
    return 0;
}
```

**Output:**

```
15 exists in vector
lower_bound for element 20 at position: 2
upper_bound for element 35 at position: 6
```


### Java Built-in Methods

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.ArrayList;
import java.util.List;

public class BuiltInBinarySearch {
    public static void main(String[] args) {
        // Arrays.binarySearch()
        int[] intArr = {10, 20, 15, 22, 35};
        Arrays.sort(intArr);
        int intKey = 22;
        System.out.println(intKey + " found at index = " 
                         + Arrays.binarySearch(intArr, intKey));
        
        // Collections.binarySearch()
        List<Integer> al = new ArrayList<>();
        al.add(1);
        al.add(2);
        al.add(3);
        al.add(10);
        al.add(20);
        
        int index = Collections.binarySearch(al, 10);
        System.out.println("10 found at index " + index);
    }
}
```

**Output:**

```
22 found at index = 3
10 found at index 3
```


### Time Complexity

O(log n) for all built-in binary search methods.

### Space Complexity

O(1) as no extra space is used.

## Complexity Analysis

### Why Binary Search is O(log n)

At each iteration, the array is divided by half. After k iterations, the length becomes n/2^k. When the length becomes 1:

n/2^k = 1
=> n = 2^k
=> log₂(n) = log₂(2^k)
=> log₂(n) = k * log₂(2)
=> k = log₂(n)

Therefore, the time complexity is O(log n).

## Applications

**Database Indexing**: Searching records in sorted databases efficiently.

**Dictionary Lookups**: Finding words in sorted dictionaries and glossaries.

**Version Control**: Identifying specific versions in sorted version histories.

**Machine Learning**: Finding optimal hyperparameters in sorted ranges.

**Competitive Programming**: Solving optimization problems with binary search.

**Game Development**: Implementing AI decision trees and pathfinding.

**File Systems**: Locating files in sorted directory structures.

**Network Routing**: Finding optimal paths in routing tables.

## When to Use Each Algorithm

**Use Linear Search**: Small datasets, unsorted data, simple implementation needed.

**Use Binary Search**: Large sorted datasets, performance critical applications, repeated searches.

This comprehensive editorial covers searching algorithms following the established format with complete code implementations in C++, Java, and Python, including outputs for each section.