
# Hash Table Coding Exercises by Tom. Muc. 

### **Teoretical Learning Material**
[Video Tutorial](https://www.youtube.com/watch?v=yJjLqHZh9b0)


## Node Class Constructor for Hash Table

### Requirements

#### **Class Definition**
Within the `Node` class, define the following member variables:

- `string key`: Represents the key of the node.
- `int value`: Represents the value associated with the key.
- `Node* next`: Represents a pointer to the next node in the same bucket (or `nullptr` if there is no next node).

#### **Constructor Implementation**
The constructor must initialize the `Node` object with the given `key` and `value` and set the `next` pointer to `nullptr`. Specifically:

- The `key` parameter should be used to initialize the member variable `this->key`.
- The `value` parameter should be used to initialize the member variable `this->value`.
- The member variable `next` should be initialized to `nullptr`.

```cpp
#include <iostream>

using namespace std;


//   +=====================================================+
//   |                 WRITE YOUR CODE HERE                |
//   | Description:                                        |
//   | - This is the Node class for key-value pairs.       |
//   | - It includes a constructor to initialize the node. |
//   | - Sets the 'key' and 'value' and sets 'next' to     |
//   |   nullptr.                                          |
//   | - Return type: N/A (constructor)                    |
//   |                                                     |
//   | Tips:                                               |
//   | - Use 'this->key' and 'this->value' to set the      |
//   |   key and value.                                    |
//   | - Initialize 'next' pointer to nullptr.             |
//   | - Check output from Test.cpp in "User logs".        |
//   +=====================================================+


class HashTable {
    private:
        static const int SIZE = 7;
        Node* dataMap[SIZE];

    public:
        HashTable() {
            for(int i = 0; i < SIZE; i++) {
                dataMap[i] = nullptr;
            }
        }
        
        // ---------------------------------------------------
        //  Destructor code is similar to keys() function
        //  Watch that video to help understand how this works
        // ---------------------------------------------------
        ~HashTable() {
            for(int i = 0; i < SIZE; i++) {
                Node* head = dataMap[i];
                Node* temp = head;
                while (head) {
                    head = head->next;
                    delete temp;
                    temp = head;
                }
            }
        }
        
        void printTable() {
            for(int i = 0; i < SIZE; i++) {
                cout << "Index " << i << ": ";
                if(dataMap[i]) {
                    cout << "Contains => ";
                    Node* temp = dataMap[i];
                    while (temp) {
                        cout << "{" << temp->key << ", " << temp->value << "}";
                        temp = temp->next;
                        if (temp) cout << ", ";
                    }
                    cout << endl;
                } else {
                    cout << "Empty" << endl;
                }
            }
        }
        
};
```
---

## HashTable Class - Set Member Function

### **Functionality**
The `set` member function inserts a key-value pair into the hash table. If the key already exists, the function updates its value.

### **Input Parameters**
- `string key`: Represents the key of the new element to be added.
- `int value`: Represents the value associated with the key.

### **Implementation Steps**

1. **Calculate Hash Index**
   - Compute the hash index for the given key using a suitable hash function.

2. **Create a New Node**
   - Instantiate a new node (`newNode`) with the provided `key` and `value`.

3. **Check dataMap Entry at the Index**
   - If the `dataMap` entry at the computed index is `nullptr`:
     - Assign `newNode` to the `dataMap` entry at the index.
   
   - If the `dataMap` entry is **not** `nullptr`:
     - Traverse the linked list at the `dataMap` entry until either:
       - The key is found (update its value and return).
       - The end of the linked list is reached.
     - If the key is not found, insert `newNode` at the end of the linked list.

```cpp

#include <iostream>

using namespace std;


class Node {
    public:
        string key;
        int value;
        Node* next;

        Node(string key, int value) {
            this->key = key;
            this->value = value;
            next = nullptr;
        }
};

class HashTable {
    private:
        static const int SIZE = 7;
        Node* dataMap[SIZE];

        int hash(string key) {
            int hash = 0;
            for (int i = 0; i < key.length(); i++) {
                int asciiValue = int(key[i]);
                hash = (hash + asciiValue *  23) % SIZE;
            }
            return hash;
        }

    public:
        HashTable() {
            for(int i = 0; i < SIZE; i++) {
                dataMap[i] = nullptr;
            }
        }
        
        // ---------------------------------------------------
        //  Destructor code is similar to keys() function
        //  Watch that video to help understand how this works
        // ---------------------------------------------------
        ~HashTable() {
            for(int i = 0; i < SIZE; i++) {
                Node* head = dataMap[i];
                Node* temp = head;
                while (head) {
                    head = head->next;
                    delete temp;
                    temp = head;
                }
            }
        }
        
        void printTable() {
            for(int i = 0; i < SIZE; i++) {
                cout << "Index " << i << ": ";
                if(dataMap[i]) {
                    cout << "Contains => ";
                    Node* temp = dataMap[i];
                    while (temp) {
                        cout << "{" << temp->key << ", " << temp->value << "}";
                        temp = temp->next;
                        if (temp) cout << ", ";
                    }
                    cout << endl;
                } else {
                    cout << "Empty" << endl;
                }
            }
        }
        
        //   +=====================================================+
        //   |                 WRITE YOUR CODE HERE                |
        //   | Description:                                        |
        //   | - This method sets a key-value pair in the hash     |
        //   |   table.                                            |
        //   | - It first hashes the key to find the index.        |
        //   | - Creates a new node and inserts it at the index.   |
        //   | - Return type: void                                 |
        //   |                                                     |
        //   | Tips:                                               |
        //   | - Use the 'hash' function to get the index.         |
        //   | - If the index is empty, directly set the node.     |
        //   | - If not, traverse to the end and set the node.     |
        //   | - 'dataMap' is the array to hold the key-value      |
        //   |   pairs.                                            |
        //   | - Check output from Test.cpp in "User logs".        |
        //   +=====================================================+
        
        
        // We will write 'get' in the next coding exercise
        // but we need it here to run tests for 'set'
        // So please don't peek at this :-)
        int get(string key) {
            int index = hash(key);
            Node* temp = dataMap[index];
            while (temp != nullptr) {
                if (temp->key == key) return temp->value;
                temp = temp->next;
            }
            return 0;
        }
    
};

```
---

## HashTable Class - Get Member Function

### **Functionality**
The `get` member function retrieves the value associated with a given key from the hash table. If the key is not found, it returns `0`.

### **Input Parameter**
- `string key`: Represents the key of the element to be retrieved from the hash table.

### **Implementation Steps**

1. **Calculate Hash Index**
   - Compute the hash index for the given key using a suitable hash function.

2. **Create Temporary Pointer**
   - Initialize a temporary pointer `temp` pointing to the `dataMap` entry at the calculated index.

3. **Traverse the Linked List**
   - Iterate through the linked list using `temp`:
     - If the key of the current node matches the given key, return the value of that node.
     - If the key is not found in the linked list, return `0`.

```cpp
#include <iostream>

using namespace std;


class Node {
    public:
        string key;
        int value;
        Node* next;

        Node(string key, int value) {
            this->key = key;
            this->value = value;
            next = nullptr;
        }
};

class HashTable {
    private:
        static const int SIZE = 7;
        Node* dataMap[SIZE];

        int hash(string key) {
            int hash = 0;
            for (int i = 0; i < key.length(); i++) {
                int asciiValue = int(key[i]);
                hash = (hash + asciiValue *  23) % SIZE;
            }
            return hash;
        }

    public:
        HashTable() {
            for(int i = 0; i < SIZE; i++) {
                dataMap[i] = nullptr;
            }
        }
        
        // ---------------------------------------------------
        //  Destructor code is similar to keys() function
        //  Watch that video to help understand how this works
        // ---------------------------------------------------
        ~HashTable() {
            for(int i = 0; i < SIZE; i++) {
                Node* head = dataMap[i];
                Node* temp = head;
                while (head) {
                    head = head->next;
                    delete temp;
                    temp = head;
                }
            }
        }
        
        void printTable() {
            for(int i = 0; i < SIZE; i++) {
                cout << "Index " << i << ": ";
                if(dataMap[i]) {
                    cout << "Contains => ";
                    Node* temp = dataMap[i];
                    while (temp) {
                        cout << "{" << temp->key << ", " << temp->value << "}";
                        temp = temp->next;
                        if (temp) cout << ", ";
                    }
                    cout << endl;
                } else {
                    cout << "Empty" << endl;
                }
            }
        }
        
        void set(string key, int value) {
            int index = hash(key);
            Node* newNode = new Node(key, value);
            if (dataMap[index] == nullptr) {
                dataMap[index] = newNode;
            } else {
                Node* temp = dataMap[index];
                while (temp->next != nullptr) {
                    temp = temp->next;
                }
                temp->next = newNode;
            }
        }
    
        //   +=====================================================+
        //   |                 WRITE YOUR CODE HERE                |
        //   | Description:                                        |
        //   | - This method retrieves the value for a given key.  |
        //   | - It first hashes the key to find the index.        |
        //   | - Searches through the linked list at that index.   |
        //   | - Return type: int                                  |
        //   |                                                     |
        //   | Tips:                                               |
        //   | - Use the 'hash' function to get the index.         |
        //   | - Use a while loop to traverse the linked list.     |
        //   | - If the key matches, return the value.             |
        //   | - If the key is not found, return 0.                |
        //   | - Check output from Test.cpp in "User logs".        |
        //   +=====================================================+

};

```
---

## HashTable Class - Keys Member Function

### **Functionality**
The `keys` member function retrieves all the keys present in the hash table and returns them in a vector.

### **Implementation Steps**

1. **Create an Empty Vector**
   - Initialize an empty vector of strings called `allKeys` to store the keys.

2. **Iterate Over the DataMap Array**
   - Loop through each entry in the `dataMap` array.

3. **Traverse the Linked List**
   - For each non-empty entry in `dataMap`:
     - Create a temporary pointer `temp` pointing to the entry.
     - Iterate through the linked list using `temp`:
       - Add the key of the current node to the `allKeys` vector.

4. **Return All Keys**
   - Return the `allKeys` vector containing all the keys in the hash table.

```cpp

#include <iostream>
#include <vector>

using namespace std;


class Node {
    public:
        string key;
        int value;
        Node* next;

        Node(string key, int value) {
            this->key = key;
            this->value = value;
            next = nullptr;
        }
};

class HashTable {
    private:
        static const int SIZE = 7;
        Node* dataMap[SIZE];

        int hash(string key) {
            int hash = 0;
            for (int i = 0; i < key.length(); i++) {
                int asciiValue = int(key[i]);
                hash = (hash + asciiValue *  23) % SIZE;
            }
            return hash;
        }

    public:
        HashTable() {
            for(int i = 0; i < SIZE; i++) {
                dataMap[i] = nullptr;
            }
        }
        
        // ---------------------------------------------------
        //  Destructor code is similar to keys() function
        //  Watch that video to help understand how this works
        // ---------------------------------------------------
        ~HashTable() {
            for(int i = 0; i < SIZE; i++) {
                Node* head = dataMap[i];
                Node* temp = head;
                while (head) {
                    head = head->next;
                    delete temp;
                    temp = head;
                }
            }
        }

        void printTable() {
            for(int i = 0; i < SIZE; i++) {
                cout << "Index " << i << ": ";
                if(dataMap[i]) {
                    cout << "Contains => ";
                    Node* temp = dataMap[i];
                    while (temp) {
                        cout << "{" << temp->key << ", " << temp->value << "}";
                        temp = temp->next;
                        if (temp) cout << ", ";
                    }
                    cout << endl;
                } else {
                    cout << "Empty" << endl;
                }
            }
        }
        
        void set(string key, int value) {
            int index = hash(key);
            Node* newNode = new Node(key, value);
            if (dataMap[index] == nullptr) {
                dataMap[index] = newNode;
            } else {
                Node* temp = dataMap[index];
                while (temp->next != nullptr) {
                    temp = temp->next;
                }
                temp->next = newNode;
            }
        }
    
        int get(string key) {
            int index = hash(key);
            Node* temp = dataMap[index];
            while (temp != nullptr) {
                if (temp->key == key) return temp->value;
                temp = temp->next;
            }
            return 0;
        }

        //   +=====================================================+
        //   |                 WRITE YOUR CODE HERE                |
        //   | Description:                                        |
        //   | - This method retrieves all keys in the hash table. |
        //   | - It traverses each index of the 'dataMap' array.   |
        //   | - For each index, it traverses the linked list.     |
        //   | - All keys are stored in a vector.                  |
        //   | - Return type: vector<string>                       |
        //   |                                                     |
        //   | Tips:                                               |
        //   | - Loop through each index in 'dataMap'.             |
        //   | - Use a nested while loop for linked list traversal.|
        //   | - Use 'push_back' to add keys to the vector.        |
        //   | - 'allKeys' is the vector to store the keys.        |
        //   | - Check output from Test.cpp in "User logs".        |
        //   +=====================================================+

};

```
---

## Item In Common - Interview Question

### **Functionality**
The `itemInCommon()` function checks if two input vectors have at least one common item.

### **Input Parameters**
- `vect1`: A vector of integers.
- `vect2`: A vector of integers.

### **Output**
- The function should return a boolean value indicating whether the two input vectors have at least one item in common.

### **Constraints**
- The input vectors may have duplicate integers.

### **Examples**

#### Example 1
**Input:**
```cpp
vect1: {1, 2, 3, 4, 5}
vect2: {6, 7, 8, 9, 10}
```
**Output:**
```cpp
false
```

#### Example 2
**Input:**
```cpp
vect1: {1, 2, 3, 4, 5}
vect2: {4, 5, 6, 7, 8}
```
**Output:**
```cpp
true
```

#### Example 3
**Input:**
```cpp
vect1: {1, 2, 2, 4, 5}
vect2: {6, 7, 8, 2, 10}
```
**Output:**
```cpp
true
```

```cpp

#include "ItemInCommon.h"


bool itemInCommon(vector<int> vect1, vector<int> vect2) {
	//   +=====================================================+
	//   |                 WRITE YOUR CODE HERE                |
	//   | Description:                                        |
	//   | - This function checks if two vectors have a        |
	//   |   common element.                                   |
	//   | - It uses an unordered_map to store elements from   |
	//   |   the first vector.                                 |
	//   | - Then it checks each element from the second       |
	//   |   vector against the map.                           |
	//   |                                                     |
	//   | Return type: bool                                   |
	//   |                                                     |
	//   | Tips:                                               |
	//   | - 'myMap' stores elements from 'vect1' as keys.     |
	//   | - Loop through 'vect2' and check against 'myMap'.   |
	//   | - Check output from Test.cpp in "User logs".        |
	//   +=====================================================+
}

```

---


```cpp

#ifndef EXERCISE_H
#define EXERCISE_H

#include <unordered_map>
#include <vector>

using namespace std;

bool itemInCommon(vector<int> vect1, vector<int> vect2);

#endif // _EXERCISE_H
```

---

## TEST 


```

#include <iostream>
#include "Test.h"

using namespace std;

void test() {
    {
        cout << "\n----- Test: Has Items In Common -----\n";
        vector<int> vect1 = {1, 2, 3, 4, 5};
        vector<int> vect2 = {5, 6, 7, 8, 9};
        cout << "EXPECTED: True\n";
        cout << "RETURNED: " << (itemInCommon(vect1, vect2) ? "True\n" : "False\n");
        cout << (itemInCommon(vect1, vect2) ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: No Items In Common -----\n";
        vector<int> vect1 = {1, 2, 3, 4, 5};
        vector<int> vect2 = {6, 7, 8, 9, 10};
        cout << "EXPECTED: False\n";
        cout << "RETURNED: " << (itemInCommon(vect1, vect2) ? "True\n" : "False\n");
        cout << (!itemInCommon(vect1, vect2) ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Both Vectors Empty -----\n";
        vector<int> vect1 = {};
        vector<int> vect2 = {};
        cout << "EXPECTED: False\n";
        cout << "RETURNED: " << (itemInCommon(vect1, vect2) ? "True\n" : "False\n");
        cout << (!itemInCommon(vect1, vect2) ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: One Vector Empty -----\n";
        vector<int> vect1 = {1, 2, 3, 4, 5};
        vector<int> vect2 = {};
        cout << "EXPECTED: False\n";
        cout << "RETURNED: " << (itemInCommon(vect1, vect2) ? "True\n" : "False\n");
        cout << (!itemInCommon(vect1, vect2) ? "PASS\n" : "FAIL\n");
    }
    
}


/* 
    EXPECTED OUTPUT:
    ----- Test: Has Items In Common -----
    EXPECTED: True
    RETURNED: True
    PASS
    ----- Test: No Items In Common -----
    EXPECTED: False
    RETURNED: False
    PASS
    ----- Test: Both Vectors Empty -----
    EXPECTED: False
    RETURNED: False
    PASS
    ----- Test: One Vector Empty -----
    EXPECTED: False
    RETURNED: False
    PASS

*/


```

---

## TEST.h


```cpp

#ifndef TEST_H
#define TEST_H

#include "ItemInCommon.h"

void test();

#endif /* TEST_H */


```


---

## Find Duplicates - Interview Question

### **Functionality**
The `findDuplicates()` function finds and returns all the duplicate elements in a given vector of integers.

### **Input Parameters**
- The function takes a constant reference to a vector of integers `nums`.

### **Output**
- The function should return a vector of integers containing all the duplicate elements in the input vector `nums`.
- The order of the elements in the output vector does not matter.

### **Examples**

#### Example 1
**Input:**
```cpp
nums: {1, 2, 3, 4, 4, 5, 5, 6, 7, 8}
```
**Output:**
```cpp
{4, 5}
```

#### Example 2
**Input:**
```cpp
nums: {10, 20, 30, 20, 40, 50, 30}
```
**Output:**
```cpp
{20, 30}
```

#### Example 3
**Input:**
```cpp
nums: {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
```
**Output:**
```cpp
{}
```
```cpp
#include "FindDuplicates.h"


vector<int> findDuplicates(const vector<int>& nums) {
	//   +=====================================================+
	//   |                 WRITE YOUR CODE HERE                |
	//   | Description:                                        |
	//   | - This function finds duplicate integers in a given |
	//   |   vector.                                           |
	//   | - It uses an unordered_map to count each integer's  |
	//   |   occurrences.                                      |
	//   | - Loops through the map to find duplicates.         |
	//   |                                                     |
	//   | Return type: vector<int>                            |
	//   |                                                     |
	//   | Tips:                                               |
	//   | - 'numCounts' keeps track of each integer's count.  |
	//   | - 'duplicates' stores duplicate integers found.     |
	//   | - Check output from Test.cpp in "User logs".        |
	//   +=====================================================+
}
```
---

```cpp
#ifndef EXERCISE_H
#define EXERCISE_H

#include <unordered_map>
#include <vector>

using namespace std;

vector<int> findDuplicates(const vector<int>& nums);

#endif // _EXERCISE_H


```

## Test.cpp

```cpp

#include <iostream>
#include <algorithm>
#include "Test.h"

using namespace std;

void test() {
    auto printVector = [](const vector<int>& v) {
        cout << "(";
        for(int i = 0; i < v.size(); i++) {
            cout << v[i];
            if (i < v.size() - 1) cout << ", ";
        }
        cout << ")";
    };

    {
        cout << "\n----- Test: No Duplicates -----\n";
        vector<int> nums = {1, 2, 3, 4, 5};
        vector<int> expected = {};
        vector<int> result = findDuplicates(nums);
        cout << "EXPECTED: No Duplicates\n";
        cout << "RETURNED: ";
        printVector(result);
        cout << "\n";
        cout << (result == expected ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Some Duplicates -----\n";
        vector<int> nums = {1, 2, 3, 2, 1, 4, 5, 6, 5};
        vector<int> expected = {1, 2, 5};
        vector<int> result = findDuplicates(nums);
        sort(result.begin(), result.end());
        cout << "EXPECTED: Has Duplicates: ";
        printVector(expected);
        cout << "\n";
        cout << "RETURNED: ";
        printVector(result);
        cout << "\n";
        cout << (result == expected ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: All Duplicates -----\n";
        vector<int> nums = {1, 1, 2, 2, 3, 3};
        vector<int> expected = {1, 2, 3};
        vector<int> result = findDuplicates(nums);
        sort(result.begin(), result.end());
        cout << "EXPECTED: Has Duplicates: (1, 2, 3)\n";
        cout << "RETURNED: ";
        printVector(result);
        cout << "\n";
        cout << (result == expected ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Empty Vector -----\n";
        vector<int> nums = {};
        vector<int> expected = {};
        vector<int> result = findDuplicates(nums);
        cout << "EXPECTED: No Duplicates\n";
        cout << "RETURNED: ";
        printVector(result);
        cout << "\n";
        cout << (result == expected ? "PASS\n" : "FAIL\n");
    }
}



/* 
    EXPECTED OUTPUT:
    ----- Test: No Duplicates -----
    EXPECTED: No Duplicates
    RETURNED: ()
    PASS
    ----- Test: Some Duplicates -----
    EXPECTED: Has Duplicates: (1, 2, 5)
    RETURNED: (1, 2, 5)
    PASS
    ----- Test: All Duplicates -----
    EXPECTED: Has Duplicates: (1, 2, 3)
    RETURNED: (1, 2, 3)
    PASS
    ----- Test: Empty Vector -----
    EXPECTED: No Duplicates
    RETURNED: ()
    PASS

*/




```


## Test.h


```cpp

#ifndef TEST_H
#define TEST_H

#include "FindDuplicates.h"

void test();

#endif /* TEST_H */




```
