
# Arrays, Strings, Loops, and Functions

In this editorial, we'll go through the essential building blocks of C++: **arrays, strings, loops, and functions.** These concepts are the foundation of any program and make writing, organizing, and understanding code much easier.

***

### Arrays

An **array** is a data structure that stores multiple values of the same type in sequential memory slots. It is like a collection of items placed one after another, and each item can be accessed using its index.

#### Declaring an Array

```cpp
#include <iostream>
using namespace std;

int main() {
    int marks[5];   // creates an array with 5 integer elements
    return 0;
}
```

**Output:**

```
Array of 5 integers created successfully.
```


#### Initializing and Accessing Elements

```cpp
#include <iostream>
using namespace std;

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};
    cout << numbers[1];  // prints the 2nd element
    return 0;
}
```

**Output:**

```
20
```


#### Updating Elements

```cpp
#include <iostream>
using namespace std;

int main() {
    int data[5] = {5, 10, 15, 20, 25};
    data [2] = data [2] + 5; 
    cout << data [2];  
    return 0;
}
```

**Output:**

```
20
```


***

### Multi-Dimensional Arrays

A **2D array** is like an array of arrays, useful for storing tabular data.

#### Declaring a 2D Array

```cpp
#include <iostream>
using namespace std;

int main() {
    int grid [2] [2];   // creates a 2x2 grid
    cout << "2x2 grid created successfully";
    return 0;
}
```

**Output:**

```
2x2 grid created successfully
```


#### Initializing and Accessing

```cpp
#include <iostream>
using namespace std;

int main() {
    int matrix [2] [2] = {{1, 2}, {3, 4}};
    cout << matrix [0] [0]; // prints first element
    return 0;
}
```

**Output:**

```
1
```

Matrix looks like:

```
1 2
3 4
```


#### Updating 2D Arrays

```cpp
#include <iostream>
using namespace std;

int main() {
    int table [2] [2] = {{5, 6}, {7, 8}};
    table [1] [0] = table [1] [0] + 10;  
    cout << table [1] [0];  
    return 0;
}
```

**Output:**

```
17
```


***

### Strings

**Strings** represent text, like names or sentences. In C++, you can use the `<string>` library to easily handle them.

#### Basic String Usage

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string text = "Hello, Earth!";
    cout << text << endl;
    cout << text [0] << endl; // prints first character
    text [5] = '-';           // change 6th character
    cout << text << endl;    
    return 0;
}
```

**Output:**

```
Hello, Earth!
H
Hello-Earth!
```


#### Reading Strings with Spaces

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string sentence;
    cout << "Enter a sentence: ";
    getline(cin, sentence);  // allows input with spaces
    cout << "You entered: " << sentence;
    return 0;
}
```

**Output:**

```
Enter a sentence: Hello World Programming
You entered: Hello World Programming
```


#### Concatenation \& Length

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string a = "Good ";
    string b = "Morning!";
    string combined = a + b;
    cout << combined << endl;
    cout << "Length: " << combined.size() << endl;
    return 0;
}
```

**Output:**

```
Good Morning!
Length: 13
```


***

### Loops

Loops allow us to repeat a block of code multiple times until a condition is met.
 <img src="https://github.com/alphaknowledgehosting/AlphaKnowledgeDsaEditorials/blob/main/CPP%20basics-1/LoopsTable.png?raw=true"/>
#### For Loop

```cpp
#include <iostream>
using namespace std;

int main() {
    for(int i = 1; i <= 5; i++) {
        cout << i << " ";
    }
    return 0;
}
```

**Output:**

```
1 2 3 4 5 
```


#### While Loop

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 1;
    while(i <= 5) {
        cout << i << " ";
        i++;
    }
    return 0;
}
```

**Output:**

```
1 2 3 4 5 
```


#### Do-While Loop

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 1;
    do {
        cout << i << " ";
        i++;
    } while(i <= 5);
    return 0;
}
```

**Output:**

```
1 2 3 4 5 
```


#### Loop Comparison

| Loop Type | Working Mechanism |
| :-- | :-- |
| For Loop | Initialization → Condition → Execution → Update |
| While Loop | Checks condition first, then executes code |
| Do-While Loop | Executes code once before checking condition |


***

### Functions

A **function** is a block of code that performs a specific task. It can take inputs (parameters), process them, and return an output.

#### Function Syntax

```
return_type function_name(parameters) {
    // function body
    return result;  // optional
}
```


#### Example Function

```cpp
#include <iostream>
using namespace std;

int sum(int x, int y) {
    return x + y;
}

int main() {
    int a = 7, b = 8;
    cout << "Sum = " << sum(a, b);
    return 0;
}
```

**Output:**

```
Sum = 15
```


***

### Passing Parameters

#### Pass by Value

```cpp
#include <iostream>
using namespace std;

void increase(int n) {
    n = n + 5;
    cout << "Inside function: " << n << endl;
}

int main() {
    int num = 10;
    increase(num);
    cout << "In main: " << num << endl;
    return 0;
}
```

**Output:**

```
Inside function: 15
In main: 10
```


#### Pass by Reference

```cpp
#include <iostream>
using namespace std;

void increase(int &n) {
    n = n + 5;
    cout << "Inside function: " << n << endl;
}

int main() {
    int num = 10;
    increase(num);
    cout << "In main: " << num << endl;
    return 0;
}
```

**Output:**

```
Inside function: 15
In main: 15
```


***

### Passing Arrays to Functions

When passing arrays, only the array name is given since it points to the first element.

```cpp
#include <iostream>
using namespace std;

void modifyArray(int arr[], int len) {
    arr [0] = 99;
    arr [1] = arr [3];
}

int main() {
    int nums [5] = {10, 20, 30, 40, 50};
    modifyArray(nums, 5);
    for(int i = 0; i < 5; i++) {
        cout << nums[i] << " ";
    }
    return 0;
}
```

**Output:**

```
99 40 30 40 50 
```