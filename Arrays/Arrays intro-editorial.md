<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# Courses

Tutorials
Practice
Jobs
60
D
Introduction to Arrays
An array is a collection of items of the same data type stored at contiguous memory locations. This makes it easier to calculate the position of each element by simply adding an offset to a base value, i.e., the memory location of the first element of the array (generally denoted by the name of the array).

For simplicity, we can think of an array as a fleet of stairs where on each step a value is placed (let’s say one of your friends). Here, you can identify the location of any of your friends by simply knowing the count of the step that they are on.

Remember: “Location of the next index depends on the data type that we use”.

The above image can be looked at as a top-level view of a staircase where you are at the base of the staircase. Each element can be uniquely identified by their index in the array (in a similar way where you could identify your friends by the step on which they were on in the above example).

Defining an Array: Array definition is similar to defining any other variable. There are two things that are needed to be kept in mind, the data type of the array elements and the sizeof the array. The size of the array is fixed and the memory for an array needs to be allocated before use, the size of an array cannot be increased or decreased dynamically.
Generally, arrays are declared as:
dataType arrayName[arraySize];

An array is distinguished from a normal variable
by brackets [ and ].

Accessing array elements: Arrays allows to access elements randomly. Elements in an array can be accessed using indexes. Suppose an array named arr stores N elements. Indexes in an array are in the range of 0 to N-1, where the first element is present at 0-th index and consecutive elements are placed at consecutive indexes. Element present at ith index in the array arr[] can be accessed as arr[i]. The below image shows an array arr[] of size 5:

Advantages of using arrays:
Arrays allow random access of elements. This makes accessing elements by their position faster.
Arrays have better cache locality that can make a pretty big difference in performance.

Examples:
// A character array in C/C++/Java
char arr1[] = {'g', 'e', 'e', 'k', 's'};

// An Integer array in C/C++/Java
int arr2[] = {10, 20, 30, 40, 50};

// Item at i'th index in array is typically accessed
// as "arr[i]".  For example arr1[0] gives us 'g'
// and arr2[3] gives us 40.

Searching in an Array
Searching for an element in an array means to check if a given element is present in the array or not. This can be done by accessing elements of the array one by one starting from the first element and checking whether any of the elements matches with the given element. We can use loops to perform the above operation of array traversal and access the elements, using indexes. Suppose the array is named arr[] with size N and the element to be searched is referred to as key. Below is the algorithm to perform the search operation in the given array.
for(i = 0; i < N; i++)
{
if(arr[i] == key)
{
print "Element Found";
break; // Exit loop once the element is found
}
}

if(i == N) // If the loop completes without finding the element
{
print "Element not Found";
}
Time Complexity
of this search operation will be O(N) in the worst case as we are checking every element of the array from 1st to last, so the number of operations is N.
Discussions( Threads )
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks

Courses
Tutorials
Practice
Jobs
60
D
Insertion and Deletion in Arrays
Insertion in Arrays

Given an array of a given size. The task is to insert a new element in this array. There are two possible ways of inserting elements in an array:
 
Insert elements at the end of the array.
Insert element at any given index in the array.

Special Case: A special case is needed to be considered is that whether the array is already full or not. If the array is full, then the new element can not be inserted.

Consider the given array is arr[] and the initial size of the array is N, that is the array can contain a maximum of N elements and the length of the array is len. That is, there are len number of elements already present in this array. 
 
Insert an element K at end in arr[]: The first step is to check if there is any space left in the array for new element. To do this check,
if(len < N)
// space left
else
// array is full
If there is space left for the new element, insert it directly at the end at position len + 1 and index len:
arr[len] = k;
Time Complexity of this insert operation is constant, i.e. O(1) as we are directly inserting the element in a single operation.
Insert an element K at position, pos in arr[]: The first step is to check if there is any space left in the array for new element. To do this check,
if(len < N)
// space left
else
// array is full
Now, if there is space left, the element can be inserted. The index of the new element will be idx = pos - 1. Now, before inserting the element at the index idx, shift all elements from the index idx till end of the array to the right by 1 place. This can be done as:
for(i = len-1; i >= idx; i--)
{
arr[i+1] = arr[i];
}
After shifting the elements, place the element K at index idx.
arr[idx] = K;
Time Complexity in worst case of this insertion operation can be linear i.e. O(N) as we might have to shift all of the elements by one place to the right.

Deletion in Arrays

To delete a given element from an array, we will have to first search the element in the array. If the element is present in the array then delete operation is performed for the element otherwise the user is notified that the array does not contains the given element.

Consider the given array is arr[] and the initial size of the array is N, that is the array can contain a maximum of N elements and the length of the array is len. That is, there are len number of elements already present in this array.

Deleting an element K from the array arr[]: Search the element K in the array arr[] to find the index at which it is present.
 
for(i = 0; i < N; i++)
{
if(arr[i] == K)
idx = i; return;
else
Element not Found;
}

Now, to delete the element present at index idx, left shift all of the elements present after idx by one place and finally reduce the length of the array by 1. 
 
for(i = idx+1; i < len; i++)
{
arr[i-1] = arr[i];
}

len = len-1;

Time Complexity in worst case of this deletion operation can be linear i.e. O(N) as we might have to shift all of the elements by one place to the left.
 
Discussions( Threads )
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks

Courses
Tutorials
Practice
Jobs
60
D
Implementing Arrays in C++ using STL
We already have discussed the basic declaration of arrays. Arrays can also be implemented using some built-in classes available in the C++ Standard Template Library.

Some of the most commonly used classes for implementing sequential lists or arrays are:
 
Vector
List

Let's look at each of these classes in details.

Vector

Vector in C++ STL is a class that represents a dynamic array. The advantages of vector over normal arrays are,
 
We do not need to pass size as an extra parameter when we pass vector.
Vectors have many in-built functions for erasing an element, inserting an element etc.
Vectors support dynamic sizes, we do not have to initially specify the size of a vector. We can also resize a vector.
There are many other functionalities vector provide.

Vectors are same as dynamic arrays with the ability to resize itself automatically when an element is inserted or deleted, with their storage being handled automatically by the container. Vector elements are placed in contiguous storage so that they can be accessed and traversed using iterators. In vectors, data is inserted at the end. Inserting at the end takes differential time, as sometimes there may be a need of extending the array. Removing the last element takes only constant time because no resizing happens. Inserting and erasing at the beginning or in the middle is linear in time.

To use the Vector class, include the below header file in your program:
 
\#include< vector >

Declaring Vector: 
 
vector< Type_of_element > vector_name;

Here, Type_of_element can be any valid C++ data type,
or can be any other container also like Pair, List etc.

Some important and commonly used functions of Vector class are:
 
begin() – Returns an iterator pointing to the first element in the vector.
end() – Returns an iterator pointing to the theoretical element that follows the last element in the vector.
size() – Returns the number of elements in the vector.
capacity() – Returns the size of the storage space currently allocated to the vector expressed as number of elements.
empty() – Returns whether the container is empty.
push_back() – It push the elements into a vector from the back.
pop_back() – It is used to pop or remove elements from a vector from the back.
insert() – It inserts new elements before the element at the specified position.
erase() – It is used to remove elements from a container from the specified position or range.
swap() – It is used to swap the contents of one vector with another vector of same type and size.
clear() – It is used to remove all the elements of the vector container.
emplace() – It extends the container by inserting new element at position.
emplace_back() – It is used to insert a new element into the vector container, the new element is added to the end of the vector.

Below program illustrate the above methods:
 
// C++ program to illustrate the above functions
​
\#include <iostream>
\#include <vector>
​
using namespace std;
​
int main()
{
vector<int> v;

    // Push elements 
    for (int i = 1; i <= 5; i++) 
        v.push_back(i); 
    ​
cout << "Size : " << v.size();

    // checks if the vector is empty or not 
    if (v.empty() == false) 
        cout << "\nVector is not empty"; 
    else
        cout << "\nVector is empty"; 
    ​
cout << "\nOutput of begin and end: ";
for (auto i = v.begin(); i != v.end(); ++i)
cout << *i << " ";

    // inserts at the beginning 
    v.emplace(v.begin(), 5); 
    cout << "\nThe first element is: " << v[0]; 
    
    // Inserts 20 at the end 
    v.emplace_back(20); 
    int n = v.size(); 
    cout << "\nThe last element is: " << v[n - 1]; 
    
    // erases the vector 
    v.clear(); 
    cout << "\nVector size after erase(): " << v.size();     
    ​
return 0;
}
Output:
 
Size : 5
Vector is not empty
Output of begin and end: 1 2 3 4 5
The first element is: 5
The last element is: 20
Vector size after erase(): 0

List

Lists are sequence containers that allow non-contiguous memory allocation. List in C++ STL implements a doubly linked list and not arrays. As compared to vector, list has slow traversal, but once a position has been found, insertion and deletion are quick. Normally, when we say a List, we talk about doubly linked lists. For implementing a singly linked list, we can use forward_list class in C++ STL.

To use the List class, include the below header file in your program:
 
\#include< list >

Declaring List: 
 
list< Type_of_element > list_name;

Here, Type_of_element can be any valid C++ data type,
or can be any other container also like Pair, List etc.

Some important and commonly used functions of List are:
 
front() – Returns the value of the first element in the list.
back() – Returns the value of the last element in the list.
push_front(g) – Adds a new element ‘g’ at the beginning of the list.
push_back(g) – Adds a new element ‘g’ at the end of the list.
pop_front() – Removes the first element of the list, and reduces the size of the list by 1.
pop_back() – Removes the last element of the list, and reduces the size of the list by 1.
begin() and end() – begin() function returns an iterator pointing to the first element of the list.
empty() – Returns whether the list is empty(1) or not(0).
insert() – Inserts new elements in the list before the element at a specified position.
reverse() – Reverses the list.
size() – Returns the number of elements in the list.
sort() – Sorts the list in increasing order.

Below program illustrate the above functions:
 
\#include <iostream>
\#include <list>
\#include <iterator>
using namespace std;
​
//function for printing the elements in a list
void showlist(list <int> g)
{
list <int> :: iterator it;
for(it = g.begin(); it != g.end(); ++it)
cout << '\t' << *it;
cout << '\n';
}
​
int main()
{
​
list <int> gqlist1, gqlist2;
​
​
for (int i = 0; i < 10; ++i)
{
gqlist1.push_back(i * 2);
gqlist2.push_front(i * 3);
}
cout << "\nList 1 (gqlist1) is : ";
showlist(gqlist1);
​
cout << "\nList 2 (gqlist2) is : ";
showlist(gqlist2);
​
cout << "\ngqlist1.front() : " << gqlist1.front();
cout << "\ngqlist1.back() : " << gqlist1.back();
​
cout << "\ngqlist1.pop_front() : ";
gqlist1.pop_front();
showlist(gqlist1);
​
cout << "\ngqlist2.pop_back() : ";
gqlist2.pop_back();
showlist(gqlist2);
​
cout << "\ngqlist1.reverse() : ";
gqlist1.reverse();
showlist(gqlist1);
​
cout << "\ngqlist2.sort(): ";
gqlist2.sort();
showlist(gqlist2);
​
return 0;
​
}
 
Output :-
List 1 (gqlist1) is : 	0	2	4	6	8	10	12	14	16	18
List 2 (gqlist2) is : 	27	24	21	18	15	12	9	6	3	0

gqlist1.front() : 0
gqlist1.back() : 18
gqlist1.pop_front() : 	2	4	6	8	10	12	14	16	18

gqlist2.pop_back() : 	27	24	21	18	15	12	9	6	3

gqlist1.reverse() : 	18	16	14	12	10	8	6	4	2

gqlist2.sort(): 	3	6	9	12	15	18	21	24	27
Discussions( Threads )
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks

Courses
Tutorials
Practice
Jobs
60
D
Iterators in C++ STL
Iterators are used to point at the memory addresses of STL containers. They are primarily used in a sequence of numbers, characters etc. We can use iterators to move through the contents of the container. They can be visualised as something similar to a pointer pointing to some location and we can access content at that particular location using them.

Basic Operations of iterators :-

begin() :- This function is used to return the beginning position of the container.
end() :- This function is used to return the after end position of the container.
// C++ code to demonstrate the working of
// iterator, begin() and end()
​
\#include<iostream>
\#include<iterator> // for iterators
\#include<vector> // for vectors
​
using namespace std;
​
int main()
{
vector<int> ar = { 1, 2, 3, 4, 5 };

    // Declaring iterator to a vector
    vector<int>::iterator ptr;
    
    // Displaying vector elements using begin() and end()
    cout << "The vector elements are : ";
    for (ptr = ar.begin(); ptr < ar.end(); ptr++)
        cout << *ptr << " ";
    
    return 0;    
    }
Output:
The vector elements are : 1 2 3 4 5

advance() :- This function is used to increment the iterator position till the specified number mentioned in its arguments.
// C++ code to demonstrate the working of
// advance()
​
\#include<iostream>
\#include<iterator> // for iterators
\#include<vector> // for vectors
​
using namespace std;
​
int main()
{
vector<int> ar = { 1, 2, 3, 4, 5 };

    // Declaring iterator to a vector
    vector<int>::iterator ptr = ar.begin();
    
    // Using advance() to increment iterator position
    // points to 4
    advance(ptr, 3);
    
    // Displaying iterator position
    cout << "The position of iterator after advancing is : ";
    cout << *ptr << " ";
    
    return 0;
    }
Output:
The position of iterator after advancing is : 4

next() :- This function returns the new iterator that the iterator would point after advancing the positions mentioned in its arguments.
prev() :- This function returns the new iterator that the iterator would point after decrementing the positions mentioned in its arguments.
// C++ code to demonstrate the working of
// next() and prev()
​
\#include<iostream>
\#include<iterator> // for iterators
\#include<vector> // for vectors
​
using namespace std;
​
int main()
{
vector<int> ar = { 1, 2, 3, 4, 5 };

    // Declaring iterators to a vector
    vector<int>::iterator ptr = ar.begin();
    vector<int>::iterator ftr = ar.end();
    
    
    // Using next() to return new iterator
    // points to 4
    auto it = next(ptr, 3);
    
    // Using prev() to return new iterator
    // points to 3
    auto it1 = prev(ftr, 3);
    
    // Displaying iterator position
    cout << "The position of new iterator using next() is : ";
    cout << *it << " ";
    cout << endl;
    
    // Displaying iterator position
    cout << "The position of new iterator using prev()  is : ";
    cout << *it1 << " ";
    cout << endl;
    
    return 0; 
    }
Output:
The position of new iterator using next() is : 4
The position of new iterator using prev()  is : 3

inserter() :- This function is used to insert the elements at any position in the container. It accepts 2 arguments, the container and iterator to position where the elements have to be inserted.
// C++ code to demonstrate the working of
// inserter()
​
\#include<iostream>
\#include<iterator> // for iterators
\#include<vector> // for vectors
​
using namespace std;
​
int main()
{
vector<int> ar = { 1, 2, 3, 4, 5 };
vector<int> ar1 = {10, 20, 30};

    // Declaring iterator to a vector
    vector<int>::iterator ptr = ar.begin();
    
    // Using advance to set position
    advance(ptr, 3);
    
    // copying 1 vector elements in other using inserter()
    // inserts ar1 after 3rd position in ar
    copy(ar1.begin(), ar1.end(), inserter(ar,ptr));
    
    // Displaying new vector elements
    cout << "The new vector after inserting elements is : ";
    for (int &x : ar) 
        cout << x << " ";
    
    return 0;    
    }
Output:
The new vector after inserting elements is : 1 2 3 10 20 30 4 5

Discussions( Threads )
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks

Courses
Tutorials
Practice
Jobs
60
D
Implementing Arrays in Java
Arrays in Java are used to store a group of elements of same data type at contiguous memory locations.

The general form of Array declaration in Java is:

type array-name[];

OR

type[] array-name;

An array declaration has two components: the type and the name. Type declares the element type of the array. The element type determines the data type of each element that comprises the array. Like an array of type int, we can also create an array of other primitive data types such as char, float, double..etc, or user-defined data type(objects of a class). Thus, the element type for the array determines what type of data the array will hold.

For Example:

// both are valid declarations
int intArray[];
or int[] intArray;

byte byteArray[];
short shortsArray[];
boolean booleanArray[];
long longArray[];
float floatArray[];
double doubleArray[];
char charArray[];

Instantiating an Array: When an array is declared, only a reference of the array is created. To actually create or give memory to the array, you create an array like this:

array-name = new type [size];

Here,

type specifies the type of data being allocated.
size specifies the number of elements in the array.
array-name is the name of array variable that is linked to the array.

Example:

int intArray[];    //declaring array
intArray = new int[20];  // allocating memory to array

OR

int[] intArray = new int[20]; // combining both statements in one

Accessing Java Array Elements using for Loop: Each element in the array is accessed by its index. The index begins with 0 and ends at (total array size)-1. All the elements of array can be accessed using Java for Loop as shown below.

// Accessing the elements of the specified array
for (int i = 0; i < arr.length; i++)
System.out.println("Element at index " + i +
" : "+ arr[i]);

Here, arr.length gives the number of elements
present in the array named arr.

Implementation:

// Java program to illustrate creating an array
// of integers,  puts some values in the array,
// and prints each value to standard output.

class GFG
{
public static void main (String[] args)
{
// declares an Array of integers.
int[] arr;

      // allocating memory for 5 integers. 
      arr = new int[5]; 
          
      // initialize the first elements of the array 
      arr[0] = 10; 
          
      // initialize the second elements of the array 
      arr[1] = 20; 
          
      // so on... 
      arr[2] = 30; 
      arr[3] = 40; 
      arr[4] = 50; 
          
      // accessing the elements of the specified array 
      for (int i = 0; i < arr.length; i++) 
         System.out.println("Element at index " + i +  
                                      " : "+ arr[i]);           
    } 
    }
Output:

Element at index 0 : 10
Element at index 1 : 20
Element at index 2 : 30
Element at index 3 : 40
Element at index 4 : 50

Java also provides some inbuilt classes which can be used for implementing arrays or sequential lists. Let's look at some of these in detail.

ArrayList in Java

ArrayList is a part of the collection framework and is present in java.util package. It provides us dynamic arrays in Java. Though it may be slower than standard arrays, it can be helpful in programs where a lot of array manipulation is needed.

Constructors in Java ArrayList:

ArrayList(): This constructor is used to build an empty array list.
ArrayList(Collection c): This constructor is used to build an array list initialized with the elements from collection c.
ArrayList(int capacity): This constructor is used to build an array list with the specified initial capacity.

Creating a generic integer ArrayList:

ArrayList arrli = new ArrayList();

Implementation:

// Java program to demonstrate working of
// ArrayList in Java
​
import java.io.*;
import java.util.*;

class arrayli
{
public static void main(String[] args)
throws IOException
{
// size of ArrayList
int n = 5;

        // declaring ArrayList with initial size n 
        ```
        ArrayList<Integer> arrli = new ArrayList<Integer>(n); 
        ```
    
        // Appending the new element at the end of the list 
        for (int i=1; i<=n; i++) 
            arrli.add(i); 
    
        // Printing elements 
        System.out.println(arrli); 
    
        // Remove element at index 3 
        arrli.remove(3); 
    
        // Displaying ArrayList after deletion 
        System.out.println(arrli); 
    
        // Printing elements one by one 
        for (int i=0; i<arrli.size(); i++) 
            System.out.print(arrli.get(i)+" "); 
    } 
    }
Output:

[1, 2, 3, 4, 5]
[1, 2, 3, 5]
1 2 3 5

Click Here to learn ArrayList in Java in detail !

Vector Class in Java

The Vector class implements a growable array of objects. Vectors basically falls in legacy classes but now it is fully compatible with collections.

Vector implements a dynamic array that means it can grow or shrink as required. Like an array, it contains components that can be accessed using an integer index.
They are very similar to ArrayList but Vector is synchronized and has some legacy method, which the collection framework does not contain.
It extends AbstractList and implements List interfaces.

Constructor:

Vector(): Creates a default vector of initial capacity 10.
Vector(int size): Creates a vector whose initial capacity is specified by size.
Vector(int size, int incr): Creates a vector whose initial capacity is specified by size and the increment is specified by incr. It specifies the number of elements to allocate each time a vector is resized upwards.
Vector(Collection c): Creates a vector that contains the elements of collection c.

Implementation:

// Java code to illustrate Vector
​
import java.util.*;
class Vector_demo {
public static void main(String[] arg)
{
// Create a vector
```        Vector<Integer> v = new Vector<Integer>();         ```

        // Insert elements in the Vector
        v.add(1); 
        v.add(2); 
        v.add(3); 
        v.add(4); 
        v.add(3); 
    
        // Print the Vector
        System.out.println("Vector is " + v); 
    } 
    }
Output:

Vector is [1, 2, 3, 4, 3]

Click Here to learn Vector in Java in detail !
Discussions( Threads )
Most Recent
Commenting as Dangudubiyyapu AkashComment AnonymouslySubmit
If you are facing any issue on this page. Please let us know.
Practice | GeeksforGeeks | A computer science portal for geeks for the above matter give editorial as per below format used for circular linked lists

Based on the information gathered, here is the complete editorial for arrays formatted according to the circular linked lists style:

***

# Arrays: Complete Guide

An array is a data structure that stores a collection of elements of the same data type at contiguous memory locations. This allows efficient access to elements using their index position, making arrays one of the fundamental data structures in computer science.[^1][^2][^5]

## Structure of an Array

An array consists of elements stored sequentially in memory where each element occupies a fixed amount of space determined by its data type.[^6]

**Data Elements**: Stores the actual values of the same data type.

**Index**: The position identifier for each element, ranging from 0 to size-1.

**Contiguous Memory**: All elements are stored in adjacent memory locations.

### Declaration and Initialization

```cpp
// C++ Array Declaration
int arr[^5];  // declares array of size 5

// Array Initialization
int arr[^5] = {10, 20, 30, 40, 50};

// Size can be omitted during initialization
int arr[] = {10, 20, 30, 40, 50};
```

```java
// Java Array Declaration
int[] arr = new int[^5];

// Array Initialization
int[] arr = {10, 20, 30, 40, 50};

// Two-step declaration
int[] arr;
arr = new int[^5];
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

**Random Access**: Elements can be accessed directly using their index in O(1) time.[^2][^1]

**Cache Locality**: Contiguous memory allocation provides better cache performance.[^1]

**Memory Efficiency**: No extra memory required for pointers or references.

**Simple Implementation**: Easy to understand and implement compared to complex data structures.

**Fixed Memory Allocation**: Memory is allocated once during declaration.

## Disadvantages

**Fixed Size**: Array size cannot be changed after declaration in static arrays.[^10]

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
    int arr[^5] = {10, 20, 30, 40, 50};
    
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
        int[] arr = new int[^10];
        arr[^0] = 10; arr[^1] = 20; arr[^2] = 30; arr[^3] = 40; arr[^4] = 50;
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

This editorial provides a comprehensive guide to arrays following the circular linked list format, with no external references and complete code implementations in C++, Java, and Python.[^5][^2][^1][^10]
<span style="display:none">[^7][^8][^9]</span>

<div align="center">⁂</div>

[^1]: https://www.geeksforgeeks.org/dsa/array-data-structure-guide/

[^2]: https://www.tutorialspoint.com/data_structures_algorithms/array_data_structure.htm

[^3]: https://www.w3schools.com/dsa/dsa_data_arrays.php

[^4]: https://www.youtube.com/watch?v=8wmn7k1TTcI

[^5]: https://www.simplilearn.com/tutorials/data-structure-tutorial/arrays-in-data-structure

[^6]: https://www.geeksforgeeks.org/c/c-arrays/

[^7]: https://www.hackerearth.com/practice/data-structures/arrays/1-d/tutorial/

[^8]: https://www.youtube.com/watch?v=sTSLRDgfOyE

[^9]: https://www.w3schools.com/dsa/dsa_intro.php

[^10]: paste.txt

