Operators are special symbols that perform operations on variables and values in C++. Understanding them is essential for writing concise and correct programs.

#### Arithmetic Operators

These operators perform mathematical operations.

- **Unary Operators:** Work with one operand.
    - Increment `++`
    - Decrement `--`

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    cout << "a++ is " << a++ << endl;
    cout << "++a is " << ++a << endl;
    cout << "Alphaknowledge: Demo of unary operators.\n";

    int b = 15;
    cout << "b-- is " << b-- << endl;
    cout << "--b is " << --b << endl;
    return 0;
}
```

**Output Tab:**
a++ is 10
++a is 12
Alphaknowledge: Demo of unary operators.
b-- is 15
--b is 13

- **Binary Operators:** Work with two operands.
    - Addition `+`, Subtraction `-`, Multiplication `*`, Division `/`, Modulo `%`

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 8, b = 3;
    cout << "Sum (a+b): " << (a + b) << endl;
    cout << "Difference (a-b): " << (a - b) << endl;
    cout << "Multiplication (a*b): " << (a * b) << endl;
    cout << "Division (a/b): " << (a / b) << endl;
    cout << "Remainder (a%b): " << (a % b) << endl;
    cout << "Alphaknowledge: Arithmetic binary demo\n";
    return 0;
}
```

**Output Tab:**
Sum (a+b): 11
Difference (a-b): 5
Multiplication (a*b): 24
Division (a/b): 2
Remainder (a%b): 2
Alphaknowledge: Arithmetic binary demo

***

### Logical Operators

Logical operators combine conditions and often control program flow.

- AND `&&`
- OR `||`
- NOT `!`

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 6, b = 4;
    cout << "a && b is " << (a && b) << endl;
    cout << "a || b is " << (a || b) << endl;
    cout << "!b is " << (!b) << endl;
    cout << "Alphaknowledge: Logical operation showcase\n";
    return 0;
}
```

**Output Tab:**
a \&\& b is 1
a || b is 1
!b is 0
Alphaknowledge: Logical operation showcase

***

### Assignment Operators

Assignment operators allow you to store values or update them easily.

- Simple Assignment `=`
- Add \& Assign `+=`
- Subtract \& Assign `-=`
- Multiply \& Assign `*=`
- Divide \& Assign `/=`

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    cout << "a = " << a << endl;
    a += 10; cout << "a += 10: " << a << endl;
    a -= 10; cout << "a -= 10: " << a << endl;
    a *= 10; cout << "a *= 10: " << a << endl;
    a /= 10; cout << "a /= 10: " << a << endl;
    cout << "Alphaknowledge: Assignment operator demo\n";
    return 0;
}
```

**Output Tab:**
a = 10
a += 10: 20
a -= 10: 10
a *= 10: 100
a /= 10: 10
Alphaknowledge: Assignment operator demo

***

### Comparison Operators

These compare values and return a boolean (true/false).

- Greater than `>`
- Less than `<`
- Greater-or-equal `>=`
- Less-or-equal `<=`
- Equal `==`
- Not equal `!=`

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 10, y = 20;
    cout << "x < y: " << (x < y) << endl;
    cout << "x > y: " << (x > y) << endl;
    cout << "x == y: " << (x == y) << endl;
    cout << "x >= y: " << (x >= y) << endl;
    cout << "x <= y: " << (x <= y) << endl;
    cout << "x != y: " << (x != y) << endl;
    cout << "Alphaknowledge: Comparison operator demo\n";
    return 0;
}
```

**Output Tab:**
x < y: 1
x > y: 0
x == y: 0
x >= y: 0
x <= y: 1
x != y: 1
Alphaknowledge: Comparison operator demo

***

### Bitwise Operators

These perform operations at the bit level.

- AND `&`
- OR `|`
- XOR `^`
- NOT `~`
- Left Shift `<<`
- Right Shift `>>`

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 3, y = 6;
    cout << "x & y: " << (x & y) << endl;
    cout << "x | y: " << (x | y) << endl;
    cout << "x ^ y: " << (x ^ y) << endl;
    cout << "x << 1: " << (x << 1) << endl;
    cout << "y >> 1: " << (y >> 1) << endl;
    cout << "~y: " << (~y) << endl;
    cout << "Alphaknowledge: Bitwise operator demo\n";
    return 0;
}
```

**Output Tab:**
x \& y: 2
x | y: 7
x ^ y: 5
x << 1: 6
y >> 1: 3
~y: -7
Alphaknowledge: Bitwise operator demo

***
