# C++ Basics - Loops and Functions 

C++ provides powerful control structures including loops and functions that enable efficient program flow control and code organization. This comprehensive guide covers for loops, while loops, do-while loops, and function implementation with parameter passing techniques.

## Algorithm Explanation

Learning C++ loops and functions involves understanding flow control mechanisms:

1. Master different loop types (for, while, do-while) for repetitive tasks
2. Understand loop components: initialization, condition, and iteration
3. Learn function syntax for code modularity and reusability
4. Implement parameter passing methods (by value and by reference)
5. Practice combining loops and functions in practical applications

## Implementation

### Loops

In programming, loops repeat a set of instructions either for a predetermined number of times or until a specific condition is met, aiding in efficient execution of repetitive tasks.

**Initialization Statement**
The initialization in a loop is like setting things up before you start, such as creating and assigning values to special variables that only work within the loop.

**Condition**
The condition in a loop acts like a checkmark before each iteration; if it's true, the loop continues, and if it's false, the loop stops.

**Iteration Execution**
The update step in a loop serves as the final action before reevaluating the condition, whether the loop continues or stops, even if a "break" or an error occurred within the loop.

### For Loop

A for loop in programming is used to repeatedly execute a block of code a specific number of times, controlled by an initial condition, a condition for continuation, and an update statement.[^1]

**Syntax:**

```cpp
for (initialization; condition; update) {
    // code to be executed
}
```

**Example:**

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Numbers from 1 to 5:" << endl;
    
    for (int i = 1; i <= 5; i++) {
        cout << i << " ";
    }
    cout << endl;
    
    // Example: Sum of first n natural numbers
    int n = 10, sum = 0;
    for (int i = 1; i <= n; i++) {
        sum += i;
    }
    cout << "Sum of first " << n << " natural numbers: " << sum << endl;
    
    return 0;
}
```


### While Loop

A while loop in programming repeatedly executes a block of code as long as a specified condition remains true.[^1]

**Syntax:**

```cpp
while (condition) {
    // code to be executed
}
```

**Example:**

```cpp
#include <iostream>
using namespace std;

int main() {
    int count = 1;
    
    cout << "Counting from 1 to 5 using while loop:" << endl;
    while (count <= 5) {
        cout << count << " ";
        count++;
    }
    cout << endl;
    
    // Example: Finding factorial
    int num = 5, factorial = 1, i = 1;
    cout << "Factorial of " << num << ": ";
    
    while (i <= num) {
        factorial *= i;
        i++;
    }
    cout << factorial << endl;
    
    return 0;
}
```


### Do-while Loop

A do-while loop in programming executes a block of code at least once and then repeatedly as long as a specified condition remains true.[^1]

**Syntax:**

```cpp
do {
    // code to be executed
} while (condition);
```

**Example:**

```cpp
#include <iostream>
using namespace std;

int main() {
    int number;
    
    cout << "Guess the number (1-10). Enter 0 to quit:" << endl;
    
    do {
        cout << "Enter your guess: ";
        cin >> number;
        
        if (number == 7) {
            cout << "Congratulations! You guessed correctly!" << endl;
            break;
        } else if (number != 0) {
            cout << "Try again!" << endl;
        }
    } while (number != 0);
    
    cout << "Game ended!" << endl;
    return 0;
}
```


### Loop Comparison Table



## Functions

A function is a pre-defined set of instructions that processes input, performs a specific task, and provides an output, offering a convenient way to reuse code for repetitive tasks.[^6]

**Syntax:**

```cpp
return_type function_name(parameter_list) {
    // function body
    return value; // if return_type is not void
}
```

**Example:**

```cpp
#include <iostream>
using namespace std;

// Function to add two numbers
int add(int a, int b) {
    return a + b;
}

// Function to check if a number is prime
bool isPrime(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0 || n % 3 == 0) return false;
    
    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0) {
            return false;
        }
    }
    return true;
}

// Function to print a pattern
void printPattern(int rows) {
    for (int i = 1; i <= rows; i++) {
        for (int j = 1; j <= i; j++) {
            cout << "* ";
        }
        cout << endl;
    }
}

int main() {
    int num1 = 10, num2 = 20;
    cout << "Sum of " << num1 << " and " << num2 << " is: " << add(num1, num2) << endl;
    
    int number = 17;
    if (isPrime(number)) {
        cout << number << " is a prime number." << endl;
    } else {
        cout << number << " is not a prime number." << endl;
    }
    
    cout << "\nPattern:" << endl;
    printPattern(5);
    
    return 0;
}
```


### Why do we use functions?

We use functions to break down a program into smaller, reusable parts, making it easier to understand, maintain, and avoid repeating code.[^6]

### Passing Parameters to Functions

**Pass by Value:** When parameters are passed this way, the original values provided by the caller are duplicated into the function's parameters, allowing changes inside the function without affecting the caller's values.[^6]

**Example:**

```cpp
#include <iostream>
using namespace std;

void modifyValue(int x) {
    x = x * 2;
    cout << "Inside function: " << x << endl;
}

int main() {
    int original = 10;
    cout << "Before function call: " << original << endl;
    
    modifyValue(original);
    
    cout << "After function call: " << original << endl;
    return 0;
}
```

**Pass by Reference:** In this approach, the main function's and function's parameters share the same memory, so changes in the function affect the main function's parameters directly.[^6]

**Example:**

```cpp
#include <iostream>
using namespace std;

void modifyReference(int &x) {
    x = x * 2;
    cout << "Inside function: " << x << endl;
}

void swap(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int original = 10;
    cout << "Before function call: " << original << endl;
    
    modifyReference(original);
    
    cout << "After function call: " << original << endl;
    
    // Swap example
    int x = 5, y = 15;
    cout << "\nBefore swap: x = " << x << ", y = " << y << endl;
    swap(x, y);
    cout << "After swap: x = " << x << ", y = " << y << endl;
    
    return 0;
}
```

### Time Complexity

- **For Loop**: O(n) where n is the number of iterations
- **While Loop**: O(n) where n depends on the condition
- **Do-While Loop**: O(n) with at least one execution guaranteed
- **Function Calls**: O(1) for the call itself, plus complexity of function body


### Space Complexity

- **Loops**: O(1) constant space for loop variables
- **Functions**: O(1) for parameters and local variables (excluding recursive calls)
- **Pass by Value**: O(k) where k is the size of copied parameters
- **Pass by Reference**: O(1) as no copying occurs
