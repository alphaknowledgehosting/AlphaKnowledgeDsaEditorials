# Recursion: Complete Guide

Recursion is a programming technique where a function calls itself directly or indirectly to solve a problem by breaking it down into smaller, similar subproblems. This approach is particularly useful for problems that can be naturally divided into similar subproblems, such as tree traversals, graph algorithms, and mathematical computations.  

## Structure of Recursion

A recursive function contains two essential components that define its behavior and termination.

**Base Case**: The condition that stops the recursion and prevents infinite function calls. It provides the solution for the simplest instance of the problem.  

**Recursive Case**: The part where the function calls itself with modified parameters, moving toward the base case.  

**Stack Frame**: Each recursive call creates a new stack frame in memory, storing local variables and return addresses. 

**Return Path**: After reaching the base case, the function returns values back through the call stack to the original caller.

### Declaration

```cpp
// Factorial function in C++
int factorial(int n) {
    // Base case
    if (n == 0 || n == 1)
        return 1;
    
    // Recursive case
    return n * factorial(n - 1);
}
```

```java
// Factorial function in Java
public static int factorial(int n) {
    // Base case
    if (n == 0 || n == 1)
        return 1;
    
    // Recursive case
    return n * factorial(n - 1);
}
```

```python
# Factorial function in Python
def factorial(n):
    # Base case
    if n == 0 or n == 1:
        return 1
    
    # Recursive case
    return n * factorial(n - 1)
```


## Advantages

**Clean and Simple Code**: Recursion provides elegant solutions for naturally recursive problems. 

**Problem Decomposition**: Breaks complex problems into simpler, manageable subproblems.  

**Natural for Tree Structures**: Ideal for tree and graph traversals where structure is inherently recursive.

**Mathematical Elegance**: Directly translates mathematical recursive definitions into code. 

**Reduces Code Complexity**: Eliminates need for explicit loops and state management in certain problems.

## Disadvantages

**Higher Space Complexity**: Each recursive call consumes stack space, leading to O(n) space complexity. 

**Stack Overflow Risk**: Deep recursion can exhaust stack memory causing program crashes.

**Performance Overhead**: Function call overhead makes recursion slower than iterative solutions. 

**Debugging Difficulty**: Harder to trace and debug compared to iterative approaches.

**Memory Limitations**: Limited by system stack size, unsuitable for large input sizes.

## How Recursion Works

### Memory Allocation

```cpp
void printFun(int test) {
    if (test < 1)
        return;
    else {
        cout << test << " ";
        printFun(test - 1);
        cout << test << " ";
        return;
    }
}

int main() {
    int test = 3;
    printFun(test);
    return 0;
}
```

```java
public static void printFun(int test) {
    if (test < 1)
        return;
    else {
        System.out.print(test + " ");
        printFun(test - 1);
        System.out.print(test + " ");
        return;
    }
}

public static void main(String[] args) {
    int test = 3;
    printFun(test);
}
```

```python
def print_fun(test):
    if test < 1:
        return
    else:
        print(test, end=" ")
        print_fun(test - 1)
        print(test, end=" ")
        return

test = 3
print_fun(test)
```

**Output:**

```
3 2 1 1 2 3
```


### Time Complexity

O(n) where n is the depth of recursion.

### Space Complexity

O(n) due to recursive call stack storing function frames.

## Basic Recursion Problems

### Problem 1: Search Element in Array

```cpp
bool recursiveSearch(int arr[], int l, int r, int x) {
    if (r < l)
        return false;
    if (arr[l] == x)
        return true;
    if (arr[r] == x)
        return true;
    
    return recursiveSearch(arr, l + 1, r - 1, x);
}
```

```java
boolean recursiveSearch(int arr[], int l, int r, int x) {
    if (r < l)
        return false;
    if (arr[l] == x)
        return true;
    if (arr[r] == x)
        return true;
    
    return recursiveSearch(arr, l + 1, r - 1, x);
}
```

```python
def recursive_search(arr, l, r, x):
    if r < l:
        return False
    if arr[l] == x:
        return True
    if arr[r] == x:
        return True
    
    return recursive_search(arr, l + 1, r - 1, x)
```

**Output:**

```
Element found: True
```


### Time Complexity

O(n) where n is the size of the array.

### Space Complexity

O(n) due to recursive call stack.

### Problem 2: Palindrome Check

```cpp
bool isPalindrome(char str[], int s, int e) {
    if (s == e)
        return true;
    
    if (str[s] != str[e])
        return false;
    
    if (s < e)
        return isPalindrome(str, s + 1, e - 1);
    
    return true;
}
```

```java
boolean isPalindrome(String str, int s, int e) {
    if (s == e)
        return true;
    
    if (str.charAt(s) != str.charAt(e))
        return false;
    
    if (s < e)
        return isPalindrome(str, s + 1, e - 1);
    
    return true;
}
```

```python
def is_palindrome(s, start, end):
    if start == end:
        return True
    
    if s[start] != s[end]:
        return False
    
    if start < end:
        return is_palindrome(s, start + 1, end - 1)
    
    return True
```

**Output:**

```
Is palindrome: Yes
```


### Time Complexity

O(n) where n is the length of the string.

### Space Complexity

O(n) due to recursive call stack.

## Tail Recursion

### What is Tail Recursion

A recursive function is tail-recursive if the recursive call is the last operation in the function, with no further computation after the recursive call returns. 

### Non-Tail Recursive Example

```cpp
int fact(int N) {
    if (N == 0)
        return 1;
    
    return N * fact(N - 1);  // Not tail recursive
}
```

```java
int fact(int N) {
    if (N == 0)
        return 1;
    
    return N * fact(N - 1);  // Not tail recursive
}
```

```python
def fact(N):
    if N == 0:
        return 1
    
    return N * fact(N - 1)  # Not tail recursive
```


### Tail Recursive Example

```cpp
int factTR(int N, int a) {
    if (N == 0)
        return a;
    
    return factTR(N - 1, N * a);  // Tail recursive
}
```

```java
int factTR(int N, int a) {
    if (N == 0)
        return a;
    
    return factTR(N - 1, N * a);  // Tail recursive
}
```

```python
def fact_tr(N, a):
    if N == 0:
        return a
    
    return fact_tr(N - 1, N * a)  # Tail recursive
```

**Output:**

```
Factorial: 120
```


### Time Complexity

O(n) for both tail and non-tail recursive versions.

### Space Complexity

O(1) for tail-recursive (with compiler optimization), O(n) for non-tail recursive.

## Common Recursion Patterns

### Linear Recursion

```cpp
int sum(int n) {
    if (n <= 0)
        return 0;
    return n + sum(n - 1);
}
```

```java
int sum(int n) {
    if (n <= 0)
        return 0;
    return n + sum(n - 1);
}
```

```python
def sum_n(n):
    if n <= 0:
        return 0
    return n + sum_n(n - 1)
```

**Output:**

```
Sum of 10: 55
```


### Time Complexity

O(n) where n is the input value.

### Space Complexity

O(n) due to recursive call stack.

## Applications

**Tree Traversals**: Inorder, preorder, and postorder traversals of binary trees.

**Graph Algorithms**: Depth-First Search (DFS) and backtracking algorithms.

**Divide and Conquer**: Merge Sort, Quick Sort, and Binary Search algorithms.

**Tower of Hanoi**: Classic recursive problem for moving disks between rods.

**Fibonacci Sequence**: Computing Fibonacci numbers using recursive relations.

**Backtracking**: N-Queens problem, Sudoku solver, and maze solving.

**Dynamic Programming**: Recursive solutions with memoization for optimization.

**Combinatorial Problems**: Generating permutations, combinations, and subsets.

## Complete Implementation

```cpp
#include <iostream>
using namespace std;

// Factorial calculation
int factorial(int n) {
    if (n == 0 || n == 1)
        return 1;
    return n * factorial(n - 1);
}

// Print function
void printFun(int test) {
    if (test < 1)
        return;
    cout << test << " ";
    printFun(test - 1);
    cout << test << " ";
}

// Sum of n numbers
int sum(int n) {
    if (n <= 0)
        return 0;
    return n + sum(n - 1);
}

// Palindrome check
bool isPalindrome(char str[], int s, int e) {
    if (s == e)
        return true;
    if (str[s] != str[e])
        return false;
    if (s < e)
        return isPalindrome(str, s + 1, e - 1);
    return true;
}

int main() {
    cout << "Factorial of 5: " << factorial(5) << endl;
    
    cout << "Print function output: ";
    printFun(3);
    cout << endl;
    
    cout << "Sum of 10 numbers: " << sum(10) << endl;
    
    char str[] = "malayalam";
    int n = strlen(str);
    if (isPalindrome(str, 0, n - 1))
        cout << "String is palindrome" << endl;
    else
        cout << "String is not palindrome" << endl;
    
    return 0;
}
```

```java
public class Recursion {
    
    public static int factorial(int n) {
        if (n == 0 || n == 1)
            return 1;
        return n * factorial(n - 1);
    }
    
    public static void printFun(int test) {
        if (test < 1)
            return;
        System.out.print(test + " ");
        printFun(test - 1);
        System.out.print(test + " ");
    }
    
    public static int sum(int n) {
        if (n <= 0)
            return 0;
        return n + sum(n - 1);
    }
    
    public static boolean isPalindrome(String str, int s, int e) {
        if (s == e)
            return true;
        if (str.charAt(s) != str.charAt(e))
            return false;
        if (s < e)
            return isPalindrome(str, s + 1, e - 1);
        return true;
    }
    
    public static void main(String[] args) {
        System.out.println("Factorial of 5: " + factorial(5));
        
        System.out.print("Print function output: ");
        printFun(3);
        System.out.println();
        
        System.out.println("Sum of 10 numbers: " + sum(10));
        
        String str = "malayalam";
        if (isPalindrome(str, 0, str.length() - 1))
            System.out.println("String is palindrome");
        else
            System.out.println("String is not palindrome");
    }
}
```

```python
# Factorial calculation
def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)

# Print function
def print_fun(test):
    if test < 1:
        return
    print(test, end=" ")
    print_fun(test - 1)
    print(test, end=" ")

# Sum of n numbers
def sum_n(n):
    if n <= 0:
        return 0
    return n + sum_n(n - 1)

# Palindrome check
def is_palindrome(s, start, end):
    if start == end:
        return True
    if s[start] != s[end]:
        return False
    if start < end:
        return is_palindrome(s, start + 1, end - 1)
    return True

# Main program
print(f"Factorial of 5: {factorial(5)}")

print("Print function output: ", end="")
print_fun(3)
print()

print(f"Sum of 10 numbers: {sum_n(10)}")

s = "malayalam"
if is_palindrome(s, 0, len(s) - 1):
    print("String is palindrome")
else:
    print("String is not palindrome")
```

**Output:**

```
Factorial of 5: 120
Print function output: 3 2 1 1 2 3
Sum of 10 numbers: 55
String is palindrome
```

This comprehensive editorial covers recursion following the doubly linked list format with complete code implementations in C++, Java, and Python, including outputs for each section.