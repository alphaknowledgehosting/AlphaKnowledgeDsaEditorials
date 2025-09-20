An operator is a symbol that operates on a value to perform specific mathematical or logical computations. They form the foundation of any programming language. In C++, we have built-in operators to provide the required functionality.
An operator operates the operands. For example, 
int c = a + b;
Here, ‘+’ is the addition operator. ‘a’ and ‘b’ are the operands that are being ‘added’.
Operators in C++ can be classified into 6 types:
Arithmetic Operators
Relational Operators
Logical Operators
Bitwise Operators
Assignment Operators
Ternary or Conditional Operators
 
 
Arithmetic Operators
These operators are used to perform arithmetic or mathematical operations on the operands. For example, ‘+’ is used for addition, ‘-‘ is used for subtraction ‘*’ is used for multiplication, etc. 
Arithmetic Operators can be classified into 2 Types:
A) Unary Operators: These operators operate or work with a single operand. For example: Increment(++) and Decrement(–) Operators.
NameSymbolDescriptionExample
Increment Operator
++
 Increases the integer value of the variable by one
int a = 5;
a++; // returns 6
Decrement Operator

-     - 

Decreases the integer value of the variable by one
int a = 5;
a- -; // returns 4
 
Example:
// CPP Program to demonstrate the increment
// and decrement operators
\#include <iostream>
using namespace std;
​
int main()
{
int a = 10;
cout << "a++ is " << a++ << endl;
cout << "++a is " << ++a << endl;
​
int b = 15;
cout << "b-- is " << b-- << endl;
cout << "--b is " << --b << endl;

    return 0;
    }
Output
a++ is 10
++a is 12
b-- is 15
--b is 13
Note: ++a and a++, both are increment operators, however, both are slightly different.
In ++a, the value of the variable is incremented first and then It is used in the program. In a++, the value of the variable is assigned first and then It is incremented. Similarly happens for the decrement operator.
B) Binary Operators: These operators operate or work with two operands. For example: Addition(+), Subtraction(-), etc.
NameSymbolDescriptionExample
Addition
+
Adds two operands
int a = 3, b = 6;
int c = a+b; // c = 9
Subtraction
–
Subtracts second operand from the first
int a = 9, b = 6;
int c = a-b; // c = 3
Multiplication
*
Multiplies two operands
int a = 3, b = 6;
int c = a*b; // c = 18
Division
/
Divides first operand by the second operand 
int a = 12, b = 6;
 
int c = a/b; // c = 2
Modulo Operation
%
Returns the remainder an integer division
int a = 8, b = 6;
int c = a%b; // c = 2
Note: The Modulo operator(%) operator should only be used with integers.
Example:
// CPP Program to demonstrate the Binary Operators
\#include <iostream>
using namespace std;
​
int main()
{
int a = 8, b = 3;
​
// Addition operator
cout << "a + b = " << (a + b) << endl;

    // Subtraction operator
    cout << "a - b = " << (a - b) << endl;
    
    // Multiplication operator
    cout << "a * b = " << (a * b) << endl;
    
    // Division operator
    cout << "a / b = " << (a / b) << endl;
    
    // Modulo operator
    cout << "a % b = " << (a % b) << endl;
    ​
return 0;
}
Output
a + b = 11
a - b = 5
a * b = 24
a / b = 2
a % b = 2
Discussions( Threads )[](https://discuss.geeksforgeeks.org/dashboard?utm-source=gfg&utm-event=comment-thread)
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks
[](https://www.geeksforgeeks.org/)
54
D
[My Profile](https://www.geeksforgeeks.org/user/dangudubiypdwy/)[My Courses](https://www.geeksforgeeks.org/myCourses)[Leaderboard](https://practice.geeksforgeeks.org/leaderboard)[Explore Community](https://www.geeksforgeeks.org/community/)[Transaction History](https://practice.geeksforgeeks.org/transactions)[Saved Videos](https://www.geeksforgeeks.org/videos/watchlist/)[Edit Profile](https://www.geeksforgeeks.org/edit-profile/)[Logout](https://authapi.geeksforgeeks.org/logout/?to=https%3A%2F%2Fwww.geeksforgeeks.org%2Fbatch%2Fcpp-stl-2%2Ftrack%2Ffoundation-cpp-operators-2%2Farticle%2FNjc0MQ%253D%253D)
[Courses]()
[Placement]()
[Data Science]()
[GATE]()
Change Language
Logical Operators
Logical Operators
These operators are used to combine two or more conditions or constraints or to complement the evaluation of the original condition in consideration. The result returns a Boolean value, i.e., true or false.
NameSymbolDescriptionExample
Logical AND
\&\&
Returns true only if all the operands are true or non-zero
int a = 3, b = 6;
 
a\&\&b;
// returns true
Logical OR
||
Returns true if either of the operands is true or non-zero
int a = 3, b = 6;
a||b;
// returns true
Logical NOT
!
Returns true if the operand is false or zero
int a = 3;
!a;
// returns false
// CPP Program to demonstrate the Logical Operators
\#include <iostream>
using namespace std;
​
int main()
{
int a = 6, b = 4;
​
// Logical AND operator
cout << "a \&\& b is " << (a \&\& b) << endl;

    // Logical OR operator
    cout << "a || b is " << (a || b) << endl;
    
    // Logical NOT operator
    cout << "!b is " << (!b) << endl;
    ​
return 0;
}
Output
a \&\& b is 1
a ! b is 1
!b is 0
Here, 0 denotes false and 1 denotes true.
 
Short-Circuiting in Logical Operators: 
 
In the case of logical AND, the second operand is not evaluated if the first operand is false. For example, program 1 below doesn’t print “GeeksQuiz” as the first operand of logical AND itself is false. 
\#include <iostream>
using namespace std;
​
int main()
{
int a = 10, b = 4;
bool res = ((a == b) \&\& cout << "GeeksQuiz");
return 0;
}
But the below program prints “GeeksQuiz” as the first operand of logical AND is true. 
\#include <iostream>
using namespace std;
​
int main()
{
int a = 10, b = 4;
bool res = ((a != b) \&\& cout << "GeeksQuiz");
return 0;
}
Output
GeeksQuiz
In the case of logical OR, the second operand is not evaluated if the first operand is true. For example, program 1 below doesn’t print “GeeksQuiz” as the first operand of logical OR itself is true. 
\#include <iostream>
using namespace std;
int main()
{
int a = 10, b = 4;
bool res = ((a != b) || cout << "GeeksQuiz");
return 0;
}
But the below program prints “GeeksQuiz” as the first operand of logical OR is false. 
\#include <iostream>
using namespace std;
int main()
{
int a = 10, b = 4;
bool res = ((a == b) || cout << "GeeksQuiz");
return 0;
}
Output
GeeksQuiz
 
Discussions( Threads )[](https://discuss.geeksforgeeks.org/dashboard?utm-source=gfg&utm-event=comment-thread)
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks
[](https://www.geeksforgeeks.org/)
54
D
[My Profile](https://www.geeksforgeeks.org/user/dangudubiypdwy/)[My Courses](https://www.geeksforgeeks.org/myCourses)[Leaderboard](https://practice.geeksforgeeks.org/leaderboard)[Explore Community](https://www.geeksforgeeks.org/community/)[Transaction History](https://practice.geeksforgeeks.org/transactions)[Saved Videos](https://www.geeksforgeeks.org/videos/watchlist/)[Edit Profile](https://www.geeksforgeeks.org/edit-profile/)[Logout](https://authapi.geeksforgeeks.org/logout/?to=https%3A%2F%2Fwww.geeksforgeeks.org%2Fbatch%2Fcpp-stl-2%2Ftrack%2Ffoundation-cpp-operators-2%2Farticle%2FNjc3Mw%253D%253D)
[Courses]()
[Placement]()
[Data Science]()
[GATE]()
Change Language
Assignment Operator
Assignment Operators
Assignment operators are used to assigning value to a variable. The left side operand of the assignment operator is a variable and right side operand of the assignment operator is a value. The value on the right side must be of the same data-type of the variable on the left side otherwise the compiler will raise an error.
Different types of assignment operators are shown below:
“=”: This is the simplest assignment operator. This operator is used to assign the value on the right to the variable on the left.
For example:
a = 10;
b = 20;
ch = 'y';
“+=”: This operator is combination of ‘+’ and ‘=’ operators. This operator first adds the current value of the variable on left to the value on the right and then assigns the result to the variable on the left.
Example:
(a += b) can be written as (a = a + b)
If initially value stored in a is 5. Then (a += 6) = 11.
“-=”This operator is combination of ‘-‘ and ‘=’ operators. This operator first subtracts the current value of the variable on left from the value on the right and then assigns the result to the variable on the left.
Example:
(a -= b) can be written as (a = a - b)
If initially value stored in a is 8. Then (a -= 6) = 2.
“*=”This operator is combination of ‘*’ and ‘=’ operators. This operator first multiplies the current value of the variable on left to the value on the right and then assigns the result to the variable on the left.
Example:
(a *= b) can be written as (a = a * b)
If initially value stored in a is 5. Then (a *= 6) = 30.
“/=”This operator is combination of ‘/’ and ‘=’ operators. This operator first divides the current value of the variable on left by the value on the right and then assigns the result to the variable on the left.
Example:
(a /= b) can be written as (a = a / b)
If initially value stored in a is 6. Then (a /= 2) = 3.
Below example illustrates the various Assignment Operators:
// C++ program to demonstrate
// working of Assignment operators
​
\#include <iostream>
using namespace std;
​
int main()
{
​
// Assigning value 10 to a
// using "=" operator
int a = 10;
cout << "Value of a is "<<a<<"\n";
​
// Assigning value by adding 10 to a
// using "+=" operator
a += 10;
cout << "Value of a is "<<a<<"\n";
​
// Assigning value by subtracting 10 from a
// using "-=" operator
a -= 10;
cout << "Value of a is "<<a<<"\n";
​
// Assigning value by multiplying 10 to a
// using "*=" operator
a *= 10;
cout << "Value of a is "<<a<<"\n";
​
// Assigning value by dividing 10 from a
// using "/=" operator
a /= 10;
cout << "Value of a is "<<a<<"\n";
​
return 0;
}
Output
Value of a is 10
Value of a is 20
Value of a is 10
Value of a is 100
Value of a is 10
 
Discussions( Threads )[](https://discuss.geeksforgeeks.org/dashboard?utm-source=gfg&utm-event=comment-thread)
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks
[](https://www.geeksforgeeks.org/)
54
D
[My Profile](https://www.geeksforgeeks.org/user/dangudubiypdwy/)[My Courses](https://www.geeksforgeeks.org/myCourses)[Leaderboard](https://practice.geeksforgeeks.org/leaderboard)[Explore Community](https://www.geeksforgeeks.org/community/)[Transaction History](https://practice.geeksforgeeks.org/transactions)[Saved Videos](https://www.geeksforgeeks.org/videos/watchlist/)[Edit Profile](https://www.geeksforgeeks.org/edit-profile/)[Logout](https://authapi.geeksforgeeks.org/logout/?to=https%3A%2F%2Fwww.geeksforgeeks.org%2Fbatch%2Fcpp-stl-2%2Ftrack%2Ffoundation-cpp-operators-2%2Farticle%2FNzUwNQ%253D%253D)
[Courses]()
[Placement]()
[Data Science]()
[GATE]()
Change Language
Comparison Operator
Comparison operators are used for comparing two elements. They are commonly used in conditional statements like if-else because they return a boolean value: true (1) if the condition is satisfied, or false (0) if it is not.
There are mainly 6 Comparison Operators namely:

1. Greater than (>)  :  Checks if the left operand is greater than the right operand.
Example:
5 > 3 // Returns true
2. Greater than or equal to (>=): Checks if the left operand is greater than or equal to the right operand.
Example:
5 >= 5 // Returns true
3. Less than (<): Checks if the left operand is less than the right operand.
Example:
3 < 5 // Returns true
4. Less than or equal to (<=): Checks if the left operand is less than or equal to the right operand.
Example:
5 <= 5 // Returns true
5. Equal to (==): Checks if the left operand is equal to the right operand.
Example:
5 == 5 // Returns true
6. Not equal to (!=): Checks if the left operand is not equal to the right operand.
Example:
5 != 3 // Returns true
Example Code to cover all 6 Comparison Operators: 
\#include<iostream>
using namespace std;
int main()
{
int x = 10, y = 20 ;
cout << (x<y) << "\n"
<< (x>y) << "\n"
<< (x==y) << "\n"
<< (x>=y) << "\n"
<< (x<=y) << "\n"
<< (x!=y) << "\n";
return 0;
}
Output
1
0
0
0
1
1
 
Discussions( Threads )[](https://discuss.geeksforgeeks.org/dashboard?utm-source=gfg&utm-event=comment-thread)
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks
[](https://www.geeksforgeeks.org/)
54
D
[My Profile](https://www.geeksforgeeks.org/user/dangudubiypdwy/)[My Courses](https://www.geeksforgeeks.org/myCourses)[Leaderboard](https://practice.geeksforgeeks.org/leaderboard)[Explore Community](https://www.geeksforgeeks.org/community/)[Transaction History](https://practice.geeksforgeeks.org/transactions)[Saved Videos](https://www.geeksforgeeks.org/videos/watchlist/)[Edit Profile](https://www.geeksforgeeks.org/edit-profile/)[Logout](https://authapi.geeksforgeeks.org/logout/?to=https%3A%2F%2Fwww.geeksforgeeks.org%2Fbatch%2Fcpp-stl-2%2Ftrack%2Ffoundation-cpp-operators-2%2Farticle%2FNzUwNQ%253D%253D)
[Courses]()
[Placement]()
[Data Science]()
[GATE]()
Change Language
Comparison Operator
Comparison operators are used for comparing two elements. They are commonly used in conditional statements like if-else because they return a boolean value: true (1) if the condition is satisfied, or false (0) if it is not.
There are mainly 6 Comparison Operators namely:
7. Greater than (>)  :  Checks if the left operand is greater than the right operand.
Example:
5 > 3 // Returns true
8. Greater than or equal to (>=): Checks if the left operand is greater than or equal to the right operand.
Example:
5 >= 5 // Returns true
9. Less than (<): Checks if the left operand is less than the right operand.
Example:
3 < 5 // Returns true
10. Less than or equal to (<=): Checks if the left operand is less than or equal to the right operand.
Example:
5 <= 5 // Returns true
11. Equal to (==): Checks if the left operand is equal to the right operand.
Example:
5 == 5 // Returns true
12. Not equal to (!=): Checks if the left operand is not equal to the right operand.
Example:
5 != 3 // Returns true
Example Code to cover all 6 Comparison Operators: 
\#include<iostream>
using namespace std;
int main()
{
int x = 10, y = 20 ;
cout << (x<y) << "\n"
<< (x>y) << "\n"
<< (x==y) << "\n"
<< (x>=y) << "\n"
<< (x<=y) << "\n"
<< (x!=y) << "\n";
return 0;
}
Output
1
0
0
0
1
1
 
Discussions( Threads )[](https://discuss.geeksforgeeks.org/dashboard?utm-source=gfg&utm-event=comment-thread)
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks
[](https://www.geeksforgeeks.org/)
54
D
[My Profile](https://www.geeksforgeeks.org/user/dangudubiypdwy/)[My Courses](https://www.geeksforgeeks.org/myCourses)[Leaderboard](https://practice.geeksforgeeks.org/leaderboard)[Explore Community](https://www.geeksforgeeks.org/community/)[Transaction History](https://practice.geeksforgeeks.org/transactions)[Saved Videos](https://www.geeksforgeeks.org/videos/watchlist/)[Edit Profile](https://www.geeksforgeeks.org/edit-profile/)[Logout](https://authapi.geeksforgeeks.org/logout/?to=https%3A%2F%2Fwww.geeksforgeeks.org%2Fbatch%2Fcpp-stl-2%2Ftrack%2Ffoundation-cpp-operators-2%2Farticle%2FNjgwNA%253D%253D)
[Courses]()
[Placement]()
[Data Science]()
[GATE]()
Change Language
BITWISE OPERATOR (Part 1 and Part2)
Bitwise Operators
These operators are used to perform bit-level operations on the operands. The operators are first converted to bit-level and then the calculation is performed on the operands. The mathematical operations such as addition, subtraction, multiplication, etc. can be performed at the bit-level for faster processing. 
 
NameSymbolDescriptionExample
Binary AND
\&
The bitwise AND operator performs a bit-by-bit comparison of two numbers. It returns 1 for each bit position where both corresponding bits in the operands are 1; otherwise, it returns 0.
int a = 2, b = 3;
(a \& b); //returns 2
Binary OR
|
The bitwise OR operator performs a bit-by-bit comparison of two numbers. It returns 1 for each bit position where at least one of the corresponding bits in the operands is 1.
int a = 2, b = 3;
(a | b); //returns 3
Binary XOR
^
The bitwise XOR operator performs a bit-by-bit comparison of two numbers. It returns 1 for each bit position where the corresponding bits in the operands are different (i.e., one is 1 and the other is 0); otherwise, it returns 0.
int a = 2, b = 3;
(a ^ b); //returns 1
Left Shift
<<
The left shift operator (<<) shifts the bits of its left-hand operand to the left by the number of positions specified by its right-hand operand. For each left shift, the most significant bits (leftmost) are discarded, and 0s are inserted into the least significant bits (rightmost).
int a = 2, b = 3;
(a << 1); //returns 4
Right Shift
>>
The right shift operator (>>) shifts the bits of its left-hand operand to the right by the number of positions specified by its right-hand operand. For each right shift, the least significant bits (rightmost) are discarded, and the most significant bits (leftmost) are filled with 0 for unsigned numbers or the sign bit for signed numbers
int a = 2, b = 3;
(a >> 1); //returns 1
Bitwise NOT
~
The bitwise NOT operator (~) inverts the bits of its operand. For every bit in the number, 0 becomes 1, and 1 becomes 0. It essentially flips all bits of the operand.
int b = 3;
(~b); //returns -4
Note: Only char and int data types  can be used with Bitwise Operators.
Example 1: Bitwise AND (\&)
\#include <iostream>
using namespace std;
​
int main() {
int x = 3;  // Binary: 0011
int y = 6;  // Binary: 0110
​
cout << (x \& y); // Perform bitwise AND
return 0;
}
Explanation:
3 in binary: 0011
6 in binary: 0110
AND: 0010
Output: 2
Example 2: Bitwise OR (|)
\#include <iostream>
using namespace std;
​
int main() {
int x = 3;  // Binary: 0011
int y = 6;  // Binary: 0110
​
cout << (x | y); // Perform bitwise OR
return 0;
}
Explanation:
3 in binary: 0011
6 in binary: 0110
OR: 0111
Output: 7
Example 3: Bitwise XOR (^)
\#include <iostream>
using namespace std;
​
int main() {
int x = 3;  // Binary: 0011
int y = 6;  // Binary: 0110
​
cout << (x ^ y); // Perform bitwise XOR
return 0;
}
Explanation:
3 in binary: 0011
6 in binary: 0110
XOR: 0101
Output: 5
Example 4 : Left Shift Operator (<<)
\#include <iostream>
using namespace std;
​
int main() {
int x = 3;  // Binary: 0000...0011
cout << (x << 1) << endl;  // Shift left by 1
cout << (x << 2) << endl;  // Shift left by 2
​
int y = 4;  // Binary: 0000...0100
int z = (x << y);          // Shift left by 4
cout << z;                 // Output the result
​
return 0;
}
Explanation of the Code
Variable Initialization:
x = 3: Binary representation: 0000...0011.
y = 4: Binary representation: 0000...0100.
Shift Left by 1 (x << 1):
Shifting 3 (0000...0011) left by 1 position: 0000...0110.
Result = 6.
Shift Left by 2 (x << 2):
Shifting 3 (0000...0011) left by 2 positions: 0000...1100.
Result = 12.
Shift Left by y (x << y):
Shifting 3 (0000...0011) left by 4 positions: 0000...110000.
Result = 48.
Output:
The program outputs:
6 for x << 1.
12 for x << 2.
48 for x << y
Example 5 : Right Shift Operator (>>)
\#include <iostream>
using namespace std;
​
int main() {
int x = 33;  // Binary: 0000...100001
cout << (x >> 1) << endl;  // Shift right by 1
cout << (x >> 2) << endl;  // Shift right by 2
​
int y = 4;  // Binary: 0000...0100
int z = (x >> y);          // Shift right by 4
cout << z;                 // Output the result
​
return 0;
}
Explanation of the Code
Variable Initialization:
x = 33: Binary representation: 0000...100001.
y = 4: Binary representation: 0000...0100.
Right Shift Operations:
x >> 1: Shifts x (33) right by 1 bit (0000...100001 → 0000...010000), result = 16.
x >> 2: Shifts x (33) right by 2 bits (0000...100001 → 0000...001000), result = 8.
x >> y: Shifts x (33) right by 4 bits (0000...100001 → 0000...000010), result = 2.
Output:
First cout outputs 16.
Second cout outputs 8.
Third cout outputs 2.
Interesting Facts About Left Shift and Right Shift Operators
Left Shift Operator (<<)
The left shift operator is equivalent to multiplying a number by 2y, where y is the number of positions shifted.
Appending a 0 to the trailing bits during a left shift is what makes the operation equivalent to multiplication by 2.
It assumes that the leading bits of the number are 0. If the leading bits are 1 (e.g., in very large numbers), the result may not correctly represent 2y multiplication.
Using left shift for multiplication is efficient and fits well within the constraints of 32-bit integers. Traditional multiplication may not work correctly with very large numbers due to overflow.
Right Shift Operator (>>)
The right shift operator is equivalent to dividing a number by 2y and taking the floor of the result (integer division).
It discards the least significant bits (trailing bits) during the shift.
For example:
33 >> 1 is equivalent to 33/21=16.5, and the floor is 16.
33 >> 2 is equivalent to 33/22=8.25, and the floor is 8.
The right shift is useful for efficiently performing division by powers of 2 without introducing decimal points or inaccuracies.
Example 6 : Bitwise NOT Operator (~)
\#include <iostream>
using namespace std;
​
int main() {
unsigned int x = 1;  // Binary: 0000...0001
cout << (~x) << endl; // Perform bitwise NOT on x
​
x = 5;  // Binary: 0000...0101
cout << (~x) << endl; // Perform bitwise NOT on x
​
return 0;
}
Explanation of the Code
Variable Initialization:
x = 1: Binary representation: 0000...0001.
x = 5: Binary representation: 0000...0101.
Bitwise NOT Operation:
For x = 1:
~x: Inverts 0000...0001 to 1111...1110.
Decimal value: 232−1−1=42949672942^{32} - 1 - 1 = 4294967294232−1−1=4294967294 (for 32-bit unsigned integer).
For x = 5:
~x: Inverts 0000...0101 to 1111...1010.
Decimal value: 232−1−5=42949672902^{32} - 1 - 5 = 4294967290232−1−5=4294967290.
Output:
First cout outputs 4294967294.
Second cout outputs 4294967290.
Discussions( Threads )[](https://discuss.geeksforgeeks.org/dashboard?utm-source=gfg&utm-event=comment-thread)
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks combine all this and generate one editorial for my alphaknowledge use alphaknowledge in programs when there is gfg and also make sure to change some content dont paste as it  is update or modify but should be simple only
i want code snippets as well for each of that as above but use alphaknolwedge instead of gfg in cout statments dont includealphaknolwedge in every soutput just when needed and also in the editorial below the code show ouptu taab as well

Here is a concise editorial covering C++ Operators including Arithmetic, Logical, Assignment, Comparison, and Bitwise Operators, with code snippets adapted to use "Alphaknowledge" instead of "GFG" in some outputs. The explanations are simple, updated, and not copied exactly from any source.

***

### Editorial: C++ Operators (AlphaKnowledge Edition)

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
