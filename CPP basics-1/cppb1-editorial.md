# C++ Programming: 

**C++ is a powerful, general-purpose programming language that extends C with object-oriented programming capabilities**. Developed by Bjarne Stroustrup in the early 1980s, it has become one of the most widely used languages for system software, game development, embedded systems, and data structures \& algorithms (DSA). 

## Introduction to C++

C++ combines the efficiency of low-level programming with high-level features, making it ideal for performance-critical applications. Its versatility allows developers to work on diverse projects ranging from operating systems to video games. 

### Key Applications:

- **System Software**: Operating systems, device drivers
- **Game Development**: High-performance gaming engines
- **Embedded Systems**: IoT devices, microcontrollers
- **Competitive Programming**: Data structures and algorithms


## Basic Program Structure

Every C++ program follows a standard structure called the "boilerplate code" :

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, World!" << endl;
    return 0;
}
```


### How C++ Code Executes

The compilation process transforms human-readable code into executable programs :

```
Source Code (.cpp) → Compiler → Executable File (.exe) → Output
```

**Example of compilation process:**

```cpp
// hello.cpp (Source Code)
#include <iostream>
using namespace std;

int main() {
    cout << "Welcome to C++ Programming!" << endl;
    return 0;
}

// After compilation: hello.exe
// Output: Welcome to C++ Programming!
```


## Preprocessor Directives

Preprocessor directives begin with the `#` symbol and provide instructions to the compiler before actual compilation begins. 

### Header Files

```cpp
#include <iostream>  // Standard input/output stream
#include <vector>    // Dynamic arrays
#include <string>    // String operations
#include <algorithm> // Sorting and searching algorithms
```


### Using Namespace

```cpp
#include <iostream>
using namespace std;  // Avoids writing std:: repeatedly

int main() {
    cout << "No need for std::cout" << endl;
    // Instead of: std::cout << "Hello" << std::endl;
    return 0;
}
```

**Benefits of namespaces:**

- Prevents naming collisions between different libraries
- Organizes code into logical groups
- Standard C++ library uses `std` namespace


## Variables and Data Types

Variables are named memory locations that store data. C++ provides various data types to handle different kinds of information. 

### Variable Declaration Examples

```cpp
#include <iostream>
using namespace std;

int main() {
    // Integer variables
    int age = 25;
    int score = 100;
    
    // Floating-point variables
    float height = 5.8f;
    double pi = 3.14159265359;
    
    // Character and string
    char grade = 'A';
    string name = "John Doe";
    
    // Boolean
    bool isStudent = true;
    
    cout << "Name: " << name << endl;
    cout << "Age: " << age << endl;
    cout << "Grade: " << grade << endl;
    
    return 0;
}
```


### Data Type Categories

**Primitive Data Types:**

```cpp
int number = 42;        // Integer (4 bytes typically)
float decimal = 3.14f;  // Single precision float (4 bytes)
double precise = 2.718; // Double precision float (8 bytes)
char letter = 'X';      // Single character (1 byte)
bool flag = false;      // Boolean (1 byte)
void;                   // Represents "nothing"
```

**Derived Data Types:**

```cpp
int numbers = {1, 2, 3, 4, 5};  // Array
int* ptr = &number;                 // Pointer
int& ref = number;                  // Reference
```

**User-Defined Data Types:**

```cpp
struct Student {
    string name;
    int rollNumber;
    float marks;
};

enum Color { RED, GREEN, BLUE };

class Calculator {
    public:
        int add(int a, int b) {
            return a + b;
        }
};
```


### Naming Conventions

Valid variable names must follow these rules : 

```cpp
// Valid names
int age;
int _count;
int student1;
int firstName;
int MAX_SIZE;

// Invalid names
// int 1number;   // Cannot start with digit
// int class;     // Reserved keyword
// int first-name; // Hyphen not allowed
```


## Input and Output Operations

C++ uses streams for input and output operations : 

```cpp
#include <iostream>
using namespace std;

int main() {
    int number;
    string name;
    float salary;
    
    // Output
    cout << "Enter your name: ";
    
    // Input
    cin >> name;
    
    cout << "Enter your age: ";
    cin >> number;
    
    cout << "Enter your salary: ";
    cin >> salary;
    
    // Display results
    cout << "\n--- Your Information ---" << endl;
    cout << "Name: " << name << endl;
    cout << "Age: " << number << endl;
    cout << "Salary: $" << salary << endl;
    
    return 0;
}
```

**Multiple input example:**

```cpp
int a, b, c;
cout << "Enter three numbers: ";
cin >> a >> b >> c;
cout << "Sum: " << (a + b + c) << endl;
```


## Operators in C++

C++ provides various operators for different operations : 
<img src="https://github.com/alphaknowledgehosting/AlphaKnowledgeDsaEditorials/blob/main/CPP%20basics-1/LoopsTable.png?raw=true"/>

### Unary Operators

```cpp
int x = 10;
cout << "x = " << x << endl;        // 10
cout << "++x = " << ++x << endl;    // 11 (pre-increment)
cout << "x++ = " << x++ << endl;    // 11 (post-increment)
cout << "x = " << x << endl;        // 12

bool flag = true;
cout << "!flag = " << !flag << endl; // 0 (false)
```


### Binary Operators

**Arithmetic Operators:**

```cpp
int a = 15, b = 4;
cout << "a + b = " << (a + b) << endl;  // 19
cout << "a - b = " << (a - b) << endl;  // 11
cout << "a * b = " << (a * b) << endl;  // 60
cout << "a / b = " << (a / b) << endl;  // 3 (integer division)
cout << "a % b = " << (a % b) << endl;  // 3 (remainder)
```

**Relational Operators:**

```cpp
int x = 10, y = 20;
cout << "x < y: " << (x < y) << endl;   // 1 (true)
cout << "x > y: " << (x > y) << endl;   // 0 (false)
cout << "x == y: " << (x == y) << endl; // 0 (false)
cout << "x != y: " << (x != y) << endl; // 1 (true)
cout << "x <= y: " << (x <= y) << endl; // 1 (true)
cout << "x >= y: " << (x >= y) << endl; // 0 (false)
```

**Logical Operators:**

```cpp
bool p = true, q = false;
cout << "p && q: " << (p && q) << endl; // 0 (false)
cout << "p || q: " << (p || q) << endl; // 1 (true)
cout << "!p: " << (!p) << endl;         // 0 (false)
```

**Assignment Operators:**

```cpp
int num = 10;
cout << "Initial: " << num << endl;     // 10

num += 5;  // num = num + 5
cout << "After +=5: " << num << endl;   // 15

num -= 3;  // num = num - 3
cout << "After -=3: " << num << endl;   // 12

num *= 2;  // num = num * 2
cout << "After *=2: " << num << endl;   // 24

num /= 4;  // num = num / 4
cout << "After /=4: " << num << endl;   // 6

num %= 4;  // num = num % 4
cout << "After %=4: " << num << endl;   // 2
```


### Ternary Operator

```cpp
int a = 15, b = 10;
int max = (a > b) ? a : b;  // If a > b, assign a, else assign b
cout << "Maximum: " << max << endl;  // 15

// Another example
int age = 17;
string status = (age >= 18) ? "Adult" : "Minor";
cout << "Status: " << status << endl;  // Minor
```

**Complex ternary example:**

```cpp
int score = 85;
char grade = (score >= 90) ? 'A' : 
             (score >= 80) ? 'B' : 
             (score >= 70) ? 'C' : 
             (score >= 60) ? 'D' : 'F';
cout << "Grade: " << grade << endl;  // B
```


### Bitwise Operators

```cpp
int a = 5;   // Binary: 101
int b = 3;   // Binary: 011

cout << "a & b = " << (a & b) << endl;  // 1 (AND)
cout << "a | b = " << (a | b) << endl;  // 7 (OR)
cout << "a ^ b = " << (a ^ b) << endl;  // 6 (XOR)
cout << "~a = " << (~a) << endl;        // -6 (NOT)
cout << "a << 1 = " << (a << 1) << endl; // 10 (Left shift)
cout << "a >> 1 = " << (a >> 1) << endl; // 2 (Right shift)
```


## Comments in C++

Comments help document code and make it more readable : 

```cpp
#include <iostream>
using namespace std;

int main() {
    // Single line comment - explains the next line
    cout << "Hello World!" << endl;
    
    /*
       Multi-line comment
       Can span multiple lines
       Useful for detailed explanations
       or temporarily disabling code blocks
    */
    
    int age = 25;  // Variable to store age
    
    /*
    This section calculates area of rectangle
    length and width are user inputs
    area = length * width
    */
    int length = 10;
    int width = 5;
    int area = length * width;  // Calculate area
    
    cout << "Area: " << area << endl;
    
    return 0;
}
```


## Complete Example Program

Here's a comprehensive example that demonstrates multiple concepts : 

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    // Variable declarations with different data types
    string studentName;
    int age;
    float gpa;
    bool isEnrolled;
    
    // Input section
    cout << "=== Student Information System ===" << endl;
    cout << "Enter student name: ";
    getline(cin, studentName);  // Read full name with spaces
    
    cout << "Enter age: ";
    cin >> age;
    
    cout << "Enter GPA: ";
    cin >> gpa;
    
    cout << "Is student enrolled? (1 for Yes, 0 for No): ";
    cin >> isEnrolled;
    
    // Processing and calculations
    int yearsUntilGraduation = (age < 22) ? (22 - age) : 0;
    
    // Determine academic standing using ternary operator
    string academicStanding = (gpa >= 3.5) ? "Excellent" :
                             (gpa >= 3.0) ? "Good" :
                             (gpa >= 2.5) ? "Satisfactory" :
                             (gpa >= 2.0) ? "Needs Improvement" : "Critical";
    
    // Output section
    cout << "\n=== Student Report ===" << endl;
    cout << "Name: " << studentName << endl;
    cout << "Age: " << age << " years" << endl;
    cout << "GPA: " << gpa << endl;
    cout << "Enrollment Status: " << (isEnrolled ? "Enrolled" : "Not Enrolled") << endl;
    cout << "Academic Standing: " << academicStanding << endl;
    
    if (yearsUntilGraduation > 0) {
        cout << "Years until graduation: " << yearsUntilGraduation << endl;
    } else {
        cout << "Ready for graduation!" << endl;
    }
    
    // Demonstrate arithmetic operations
    cout << "\n=== Grade Statistics ===" << endl;
    float maxGPA = 4.0f;
    float percentage = (gpa / maxGPA) * 100;
    cout << "GPA Percentage: " << percentage << "%" << endl;
    
    return 0;
}
```


## Best Practices

When writing C++ programs, follow these conventions : 

1. **Use meaningful variable names**: `studentAge` instead of `a`
2. **Follow consistent naming**: camelCase or snake_case
3. **Add comments for complex logic**
4. **Initialize variables when declaring them**
5. **Use appropriate data types for different values**
6. **Avoid using `using namespace std;` in header files**

**Example of good practices:**

```cpp
#include <iostream>
using namespace std;

int main() {
    // Initialize variables with meaningful names
    const int MAX_STUDENTS = 100;
    int currentStudentCount = 0;
    float averageScore = 0.0f;
    bool hasPassedExam = false;
    
    // Use constants for fixed values
    const float PASSING_GRADE = 60.0f;
    
    // Clear variable usage
    cout << "Maximum students allowed: " << MAX_STUDENTS << endl;
    
    return 0;
}
```

