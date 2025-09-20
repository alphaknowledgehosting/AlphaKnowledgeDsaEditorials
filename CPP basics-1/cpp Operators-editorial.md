C++ operators are symbols that perform specific operations on values called operands. They form the foundation of any programming language by enabling mathematical computations, logical evaluations, and data manipulations.

## Arithmetic Operators

### Unary Operators

These operators work with a single operand:

**Increment Operator (++)**

- Increases the integer value by one
- Two forms: pre-increment (`++a`) and post-increment (`a++`)

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    cout << "a++ = " << a++ << endl;  // prints 10, then increments
    cout << "++a = " << ++a << endl;  // increments first, then prints 12
    return 0;
}
```

**Decrement Operator (--)**

- Decreases the integer value by one
- Similar behavior to increment operator


### Binary Operators

These operators work with two operands:


| Operator | Symbol | Description | Example |
| :-- | :-- | :-- | :-- |
| Addition | + | Adds two operands | `int c = a + b;` |
| Subtraction | - | Subtracts second from first | `int c = a - b;` |
| Multiplication | * | Multiplies two operands | `int c = a * b;` |
| Division | / | Divides first by second | `int c = a / b;` |
| Modulo | % | Returns remainder of division | `int c = a % b;` |

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 8, b = 3;
    cout << "a + b = " << (a + b) << endl;  // 11
    cout << "a - b = " << (a - b) << endl;  // 5
    cout << "a * b = " << (a * b) << endl;  // 24
    cout << "a / b = " << (a / b) << endl;  // 2
    cout << "a % b = " << (a % b) << endl;  // 2
    return 0;
}
```


## Logical Operators

Logical operators combine conditions and return boolean values:


| Operator | Symbol | Description | Example |
| :-- | :-- | :-- | :-- |
| Logical AND | \&\& | True if both operands are true | `a && b` |
| Logical OR | \|\| | True if either operand is true | `a \|\| b` |
| Logical NOT | ! | Inverts the boolean value | `!a` |

### Short-Circuit Evaluation

Logical operators use short-circuit evaluation for efficiency:

- **AND (\&\&)**: If first operand is false, second is not evaluated
- **OR (||)**: If first operand is true, second is not evaluated


## Comparison Operators

These operators compare values and return boolean results:


| Operator | Symbol | Description |
| :-- | :-- | :-- |
| Greater than | > | Checks if left > right |
| Greater than or equal | >= | Checks if left >= right |
| Less than | < | Checks if left < right |
| Less than or equal | <= | Checks if left <= right |
| Equal to | == | Checks if left == right |
| Not equal to | != | Checks if left != right |

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 10, y = 20;
    cout << (x < y) << endl;   // 1 (true)
    cout << (x > y) << endl;   // 0 (false)
    cout << (x == y) << endl;  // 0 (false)
    cout << (x != y) << endl;  // 1 (true)
    return 0;
}
```


## Assignment Operators

Assignment operators assign values to variables:


| Operator | Description | Example | Equivalent |
| :-- | :-- | :-- | :-- |
| = | Simple assignment | `a = 10` | `a = 10` |
| += | Add and assign | `a += 5` | `a = a + 5` |
| -= | Subtract and assign | `a -= 5` | `a = a - 5` |
| *= | Multiply and assign | `a *= 5` | `a = a * 5` |
| /= | Divide and assign | `a /= 5` | `a = a / 5` |

## Bitwise Operators

Bitwise operators perform operations at the bit level:

### Binary Bitwise Operators

| Operator | Symbol | Description |
| :-- | :-- | :-- |
| AND | \& | Returns 1 if both bits are 1 |
| OR | \| | Returns 1 if at least one bit is 1 |
| XOR | ^ | Returns 1 if bits are different |
| Left Shift | << | Shifts bits left (multiply by 2^n) |
| Right Shift | >> | Shifts bits right (divide by 2^n) |

### Unary Bitwise Operator

**NOT (~)**: Inverts all bits (0 becomes 1, 1 becomes 0)

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 3;  // Binary: 0011
    int b = 6;  // Binary: 0110
    
    cout << (a & b) << endl;  // 2 (0010)
    cout << (a | b) << endl;  // 7 (0111)
    cout << (a ^ b) << endl;  // 5 (0101)
    cout << (a << 1) << endl; // 6 (left shift by 1)
    cout << (a >> 1) << endl; // 1 (right shift by 1)
    
    return 0;
}
```


### Shift Operators in Detail

**Left Shift (<<)**: Equivalent to multiplying by 2^n

- Example: `5 << 2` = 5 × 2² = 20

**Right Shift (>>)**: Equivalent to dividing by 2^n (integer division)

- Example: `20 >> 2` = 20 ÷ 2² = 5


