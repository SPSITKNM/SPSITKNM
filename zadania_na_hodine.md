
# Developed by Tom (Starký) Muc. - Exercises for the Doubly Linked List Section


# 1. DoublyLinkedList: Swap First and Last

### Task
Implement a member function called `swapFirstLast()` for the `DoublyLinkedList` class:

- **Functionality**:
  - Swap the values of the first and last nodes in the list.
  - If the length of the list is less than 2, the function should not perform any operation.

- **Input**:
  - The function is a member of the `DoublyLinkedList` class, which has:
    - A `head` pointer to the first node.
    - A `tail` pointer to the last node.
    - A `length` attribute indicating the number of elements in the list.

- **Output**:
  - No explicit output is returned.
  - The function should modify the doubly linked list so that the values of the first and last nodes are swapped.

---

### Example
#### Before `swapFirstLast()`:
- Head value: `1`
- Tail value: `5`

#### After `swapFirstLast()`:
- Head value: `5`
- Tail value: `1`


```cpp
#include <iostream>
#include <iostream>

using namespace std;

class Node { 
    public: 
        int value;
        Node* next;
        Node* prev;
    
        Node(int value) {
            this->value = value;
            next = nullptr;
            prev = nullptr;
        }
};

class DoublyLinkedList {
    private:
        Node* head;
        Node* tail;
        int length;
    
    public:
        DoublyLinkedList(int value) {
            Node* newNode = new Node(value);
            head = newNode;
            tail = newNode;
            length = 1;
        }
    
        ~DoublyLinkedList() {
            Node* temp = head;
            while (head) {
                head = head->next;
                delete temp;
                temp = head;
            }
        }
    
        void printList() {
            Node* temp = head;
            if (temp == nullptr) {
                cout << "empty" << endl;
                return;
            }
            while (temp->next != nullptr) {
                cout << temp->value << " <-> ";
                temp = temp->next;
            }
            cout << temp->value << endl;
        }
    
        Node* getHead() {
            return head;
        }
    
        Node* getTail() {
            return tail;
        }
    
        int getLength() {
            return length;
        }

        void append(int value) {
            Node* newNode = new Node(value);
            if (length == 0) {
                head = newNode;
                tail = newNode;
            } else {
                tail->next = newNode;
                newNode->prev = tail;
                tail = newNode;
            }
            length++;
        }
        
        //   +=====================================================+
        //   |                 WRITE YOUR CODE HERE                |
        //   | Description:                                        |
        //   | - This is the swapFirstLast function.               |
        //   | - It swaps the values of the first and last nodes   |
        //   |   in the doubly linked list.                        |
        //   | - Return type: void                                 |
        //   |                                                     |
        //   | Tips:                                               |
        //   | - Check if the list has less than 2 nodes. If so,   |
        //   |   just return; nothing to swap.                     |
        //   | - Use a temporary variable to store the value of    |
        //   |   the head node.                                    |
        //   | - Assign the value of the tail node to the head     |
        //   |   node.                                             |
        //   | - Assign the stored head node value to the tail.    |
        //   | - Check output from Test.cpp in "User logs".        |
        //   +=====================================================+
        
};


```

# CODE FOR TESTING 


```cpp
#include <iostream>
#include "DoublyLinkedList.cpp"

using namespace std;


//  +=====================================================+
//  |                                                     |
//  |          THE TEST CODE BELOW WILL PRINT             |
//  |              OUTPUT TO "USER LOGS"                  |
//  |                                                     |
//  |  Use the output to test and troubleshoot your code  |
//  |                                                     |
//  +=====================================================+


static void test() {

    // Test: Swap First and Last with Single Node
    {
        cout << "\n----- Test: Swap First and Last with Single Node -----\n";
        DoublyLinkedList list(1);
        cout << "DLL before swapping first and last:\n";
        list.printList();
        list.swapFirstLast();
        cout << "DLL after swapping first and last:\n";
        list.printList();
        int headValue = list.getHead()->value;
        int tailValue = list.getTail()->value;
        cout << "Head value after swapping: " << headValue << " - EXPECTED: 1\n";
        cout << "Tail value after swapping: " << tailValue << " - EXPECTED: 1\n";
        cout << ((headValue == 1 && tailValue == 1) ? "PASS\n" : "FAIL\n");
    }

    // Test: Swap First and Last with Two Nodes
    {
        cout << "\n----- Test: Swap First and Last with Two Nodes -----\n";
        DoublyLinkedList list(1);
        list.append(2);
        cout << "DLL before swapping first and last:\n";
        list.printList();
        list.swapFirstLast();
        cout << "DLL after swapping first and last:\n";
        list.printList();
        int headValue = list.getHead()->value;
        int tailValue = list.getTail()->value;
        cout << "Head value after swapping: " << headValue << " - EXPECTED: 2\n";
        cout << "Tail value after swapping: " << tailValue << " - EXPECTED: 1\n";
        cout << ((headValue == 2 && tailValue == 1) ? "PASS\n" : "FAIL\n");
    }

    // Test: Swap First and Last with Multiple Nodes
    {
        cout << "\n----- Test: Swap First and Last with Multiple Nodes -----\n";
        DoublyLinkedList list(1);
        list.append(2);
        list.append(3);
        list.append(4);
        cout << "DLL before swapping first and last:\n";
        list.printList();
        list.swapFirstLast();
        cout << "DLL after swapping first and last:\n";
        list.printList();
        int headValue = list.getHead()->value;
        int tailValue = list.getTail()->value;
        int headNextValue = list.getHead()->next->value;
        int tailPrevValue = list.getTail()->prev->value;
        cout << "Head value after swapping: " << headValue << " - EXPECTED: 4\n";
        cout << "Tail value after swapping: " << tailValue << " - EXPECTED: 1\n";
        cout << "Value after head after swapping: " << headNextValue << " - EXPECTED: 2\n";
        cout << "Value before tail after swapping: " << tailPrevValue << " - EXPECTED: 3\n";
        bool pass = headValue == 4 && tailValue == 1 && headNextValue == 2 && tailPrevValue == 3;
        cout << (pass ? "PASS\n" : "FAIL\n");
    }
    
}
```

# 2. DoublyLinkedList: Reverse

### Task
Implement a member function called `reverse()` for the `DoublyLinkedList` class:

- **Functionality**:
  - Reverse the order of the nodes in the doubly linked list.
  - Update the `prev` and `next` pointers of each node to achieve the reversal.

- **Input**:
  - The function is a member of the `DoublyLinkedList` class, which has:
    - A `head` pointer to the first node.
    - A `tail` pointer to the last node.
    - A `length` attribute indicating the number of elements in the list.

- **Output**:
  - No explicit output is returned.
  - The function modifies the doubly linked list to reverse the order of its nodes.

---

### Constraints
- The doubly linked list may:
  - Be empty (no operation needed).
  - Have only one node (no operation needed).
  - Have two or more nodes.

---

### Example

#### Before `reverse()`:
- **Head**: `1`
- **Tail**: `5`
- **Length**: `5`

**Doubly Linked List**:
`1 <-> 2 <-> 3 <-> 4 <-> 5`

#### After `reverse()`:
- **Head**: `5`
- **Tail**: `1`
- **Length**: `5`

**Doubly Linked List**:
`5 <-> 4 <-> 3 <-> 2 <-> 1`

---

### Steps to Implement
1. **Edge Cases**:
   - If the list is empty or has only one node, return immediately as no changes are needed.
   
2. **Traverse and Swap**:
   - Use a temporary pointer to traverse the list.
   - For each node:
     - Swap its `prev` and `next` pointers.
   - Continue until all nodes are processed.

3. **Update Head and Tail**:
   - After traversal, swap the `head` and `tail` pointers to reflect the new order.

---

### Key Notes
- Ensure the integrity of the list is maintained during pointer swapping.
- Properly handle edge cases to avoid null pointer dereferences.
- Verify the updated `head` and `tail` pointers after the reversal.

Good luck implementing the `reverse()` function!



```cpp

#include <iostream>

using namespace std;

class Node { 
    public: 
        int value;
        Node* next;
        Node* prev;
    
        Node(int value) {
            this->value = value;
            next = nullptr;
            prev = nullptr;
        }
};

class DoublyLinkedList {
    private:
        Node* head;
        Node* tail;
        int length;
    
    public:
        DoublyLinkedList(int value) {
            Node* newNode = new Node(value);
            head = newNode;
            tail = newNode;
            length = 1;
        }
    
        ~DoublyLinkedList() {
            Node* temp = head;
            while (head) {
                head = head->next;
                delete temp;
                temp = head;
            }
        }
    
        void printList() {
            Node* temp = head;
            if (temp == nullptr) {
                cout << "empty" << endl;
                return;
            }
            while (temp->next != nullptr) {
                cout << temp->value << " <-> ";
                temp = temp->next;
            }
            cout << temp->value << endl;
        }
    
        Node* getHead() {
            return head;
        }
    
        Node* getTail() {
            return tail;
        }
    
        int getLength() {
            return length;
        }

        void append(int value) {
            Node* newNode = new Node(value);
            if (length == 0) {
                head = newNode;
                tail = newNode;
            } else {
                tail->next = newNode;
                newNode->prev = tail;
                tail = newNode;
            }
            length++;
        }
        
        //   +=====================================================+
        //   |                 WRITE YOUR CODE HERE                |
        //   | Description:                                        |
        //   | - This is the reverse method.                       |
        //   | - It reverses the entire doubly linked list.        |
        //   | - Return type: void                                 |
        //   |                                                     |
        //   | Tips:                                               |
        //   | - Create two pointers: current and temp.            |
        //   | - Loop through the list swapping next and prev      |
        //   |   for each node.                                    |
        //   | - After loop, swap head and tail pointers.          |
        //   | - Check output from Test.cpp in "User logs".        |
        //   +=====================================================+
        
};

```


# CODE FOR TESTING
```cpp

#include <iostream>
#include "DoublyLinkedList.cpp"

using namespace std;


//  +=====================================================+
//  |                                                     |
//  |          THE TEST CODE BELOW WILL PRINT             |
//  |              OUTPUT TO "USER LOGS"                  |
//  |                                                     |
//  |  Use the output to test and troubleshoot your code  |
//  |                                                     |
//  +=====================================================+


static void test() {

    // Test: Reverse Single Node
    {
        cout << "\n----- Test: Reverse Single Node -----\n";
        DoublyLinkedList list(1);
        cout << "DLL before reversing:\n";
        list.printList();
        list.reverse();
        cout << "DLL after reversing:\n";
        list.printList();
        int headValue = list.getHead()->value;
        int tailValue = list.getTail()->value;
        cout << "Head value after reversing: " << headValue << " - EXPECTED: 1\n";
        cout << "Tail value after reversing: " << tailValue << " - EXPECTED: 1\n";
        cout << ((headValue == 1 && tailValue == 1) ? "PASS\n" : "FAIL\n");
    }

    // Test: Reverse Two Nodes
    {
        cout << "\n----- Test: Reverse Two Nodes -----\n";
        DoublyLinkedList list(1);
        list.append(2);
        cout << "DLL before reversing:\n";
        list.printList();
        list.reverse();
        cout << "DLL after reversing:\n";
        list.printList();
        int headValue = list.getHead()->value;
        int tailValue = list.getTail()->value;
        cout << "Head value after reversing: " << headValue << " - EXPECTED: 2\n";
        cout << "Tail value after reversing: " << tailValue << " - EXPECTED: 1\n";
        cout << ((headValue == 2 && tailValue == 1) ? "PASS\n" : "FAIL\n");
    }

    // Test: Reverse Multiple Nodes
    {
        cout << "\n----- Test: Reverse Multiple Nodes -----\n";
        DoublyLinkedList list(1);
        list.append(2);
        list.append(3);
        list.append(4);
        cout << "DLL before reversing:\n";
        list.printList();
        list.reverse();
        cout << "DLL after reversing:\n";
        list.printList();
        int headValue = list.getHead()->value;
        int tailValue = list.getTail()->value;
        int headNextValue = list.getHead()->next->value;
        int tailPrevValue = list.getTail()->prev->value;
        cout << "Head value after reversing: " << headValue << " - EXPECTED: 4\n";
        cout << "Tail value after reversing: " << tailValue << " - EXPECTED: 1\n";
        cout << "Value after head after reversing: " << headNextValue << " - EXPECTED: 3\n";
        cout << "Value before tail after reversing: " << tailPrevValue << " - EXPECTED: 2\n";
        bool pass = headValue == 4 && tailValue == 1 && headNextValue == 3 && tailPrevValue == 2;
        cout << (pass ? "PASS\n" : "FAIL\n");
    }
    
}




```

# 3. DoublyLinkedList: Palindrome Checker

### Task
Implement a member function called `isPalindrome()` for the `DoublyLinkedList` class:

- **Functionality**:
  - Check if the list is a palindrome, meaning its elements read the same forward and backward.
  - Return `true` if the list is a palindrome, and `false` otherwise.

- **Input**:
  - The function is a member of the `DoublyLinkedList` class, which has:
    - A `head` pointer to the first node.
    - A `tail` pointer to the last node.
    - A `length` attribute indicating the number of elements in the list.

- **Output**:
  - A boolean value:
    - `true` if the doubly linked list is a palindrome.
    - `false` otherwise.

---

### Constraints
- The doubly linked list may:
  - Be empty.
  - Have only one node.
  - Have two or more nodes.

---

### Examples

#### Example 1
**Before `isPalindrome()`**:
- **Head**: `1`
- **Tail**: `1`
- **Length**: `5`

**Doubly Linked List**:
`1 <-> 2 <-> 3 <-> 2 <-> 1`

**Result**:
- The function returns `true`, as the list is a palindrome.

---

#### Example 2
**Before `isPalindrome()`**:
- **Head**: `1`
- **Tail**: `5`
- **Length**: `5`

**Doubly Linked List**:
`1 <-> 2 <-> 3 <-> 4 <-> 5`

**Result**:
- The function returns `false`, as the list is not a palindrome.

```cpp

#include <iostream>

using namespace std;

class Node { 
    public: 
        int value;
        Node* next;
        Node* prev;
    
        Node(int value) {
            this->value = value;
            next = nullptr;
            prev = nullptr;
        }
};

class DoublyLinkedList {
    private:
        Node* head;
        Node* tail;
        int length;
    
    public:
        DoublyLinkedList(int value) {
            Node* newNode = new Node(value);
            head = newNode;
            tail = newNode;
            length = 1;
        }
    
        ~DoublyLinkedList() {
            Node* temp = head;
            while (head) {
                head = head->next;
                delete temp;
                temp = head;
            }
        }
    
        void printList() {
            Node* temp = head;
            if (temp == nullptr) {
                cout << "empty" << endl;
                return;
            }
            while (temp->next != nullptr) {
                cout << temp->value << " <-> ";
                temp = temp->next;
            }
            cout << temp->value << endl;
        }
    
        Node* getHead() {
            return head;
        }
    
        Node* getTail() {
            return tail;
        }
    
        int getLength() {
            return length;
        }

        void append(int value) {
            Node* newNode = new Node(value);
            if (length == 0) {
                head = newNode;
                tail = newNode;
            } else {
                tail->next = newNode;
                newNode->prev = tail;
                tail = newNode;
            }
            length++;
        }

        //   +=====================================================+
        //   |                 WRITE YOUR CODE HERE                |
        //   | Description:                                        |
        //   | - This is the isPalindrome method.                  |
        //   | - It checks if the list is a palindrome or not.     |
        //   | - Return type: bool                                 |
        //   |                                                     |
        //   | Tips:                                               |
        //   | - A list with 0 or 1 node is a palindrome.          |
        //   | - Create two pointers: forwardNode and backwardNode.|
        //   | - Loop from the start to the middle of the list.    |
        //   | - Compare forwardNode and backwardNode values.      |
        //   | - If any pair is not equal, return false.           |
        //   | - Otherwise, return true.                           |
        //   | - Check output from Test.cpp in "User logs".        |
        //   +=====================================================+

};


```

# CODE FOR TESTING

```cpp

#include <iostream>
#include "DoublyLinkedList.cpp"

using namespace std;


//  +=====================================================+
//  |                                                     |
//  |          THE TEST CODE BELOW WILL PRINT             |
//  |              OUTPUT TO "USER LOGS"                  |
//  |                                                     |
//  |  Use the output to test and troubleshoot your code  |
//  |                                                     |
//  +=====================================================+


static void test() {

    // Test: Is Palindrome with Single Node
    {
        cout << "\n----- Test: Is Palindrome with Single Node -----\n";
        DoublyLinkedList list(1);
        cout << "DLL:\n";
        list.printList();
        bool result = list.isPalindrome();
        cout << "Is Palindrome: " << (result ? "true" : "false") << " - EXPECTED: true\n";
        cout << (result ? "PASS\n" : "FAIL\n");
    }

    // Test: Is Palindrome with Two Nodes
    {
        cout << "\n----- Test: Is Palindrome with Two Nodes -----\n";

        DoublyLinkedList list(1);
        list.append(1);
        cout << "DLL (equal values):\n";
        list.printList();
        bool result1 = list.isPalindrome();
        cout << "Is Palindrome: " << (result1 ? "true" : "false") << " - EXPECTED: true\n";
        cout << (result1 ? "PASS\n" : "FAIL\n");

        DoublyLinkedList list2(1);
        list2.append(2);
        cout << "\nDLL (different values):\n";
        list2.printList();
        bool result2 = list2.isPalindrome();
        cout << "Is Palindrome: " << (result2 ? "true" : "false") << " - EXPECTED: false\n";
        cout << (result2 ? "FAIL\n" : "PASS\n");
    }

    // Test: Is Palindrome with Multiple Nodes
    {
        cout << "\n----- Test: Is Palindrome with Multiple Nodes -----\n";

        DoublyLinkedList list(1);
        list.append(2);
        list.append(3);
        list.append(2);
        list.append(1);
        cout << "DLL (palindrome):\n";
        list.printList();
        bool result1 = list.isPalindrome();
        cout << "Is Palindrome: " << (result1 ? "true" : "false") << " - EXPECTED: true\n";
        cout << (result1 ? "PASS\n" : "FAIL\n");

        DoublyLinkedList list2(1);
        list2.append(2);
        list2.append(3);
        list2.append(3);
        list2.append(2);
        cout << "\nDLL (not palindrome):\n";
        list2.printList();
        bool result2 = list2.isPalindrome();
        cout << "Is Palindrome: " << (result2 ? "true" : "false") << " - EXPECTED: false\n";
        cout << (result2 ? "FAIL\n" : "PASS\n");
    }
    
}

```


# 4. DoublyLinkedList: Swap Nodes in Pairs

### Task
Implement a member function called `swapPairs()` for the `DoublyLinkedList` class:

- **Functionality**:
  - Swap every two adjacent nodes in the list.
  - The pointers to the nodes themselves must be updated to achieve the swapping, not just their values.

- **Input**:
  - The function is a member of the `DoublyLinkedList` class, which has:
    - A `head` pointer to the first node.
    - A `length` attribute indicating the number of elements in the list.

- **Output**:
  - No explicit output is returned.
  - The function should modify the doubly linked list such that every two adjacent nodes are swapped.

---

### Constraints
- The doubly linked list may:
  - Be empty.
  - Have only one node.
  - Have two or more nodes.
- **Note**: This implementation does not require a tail pointer, simplifying the logic.

---

### Examples

#### Example 1
**Before `swapPairs()`**:
- **Head**: `1`
- **Length**: `6`

**Doubly Linked List**:
`1 <-> 2 <-> 3 <-> 4 <-> 5 <-> 6`

**After `swapPairs()`**:
- **Head**: `2`
- **Length**: `6`

**Doubly Linked List**:
`2 <-> 1 <-> 4 <-> 3 <-> 6 <-> 5`

---

#### Example 2
**Before `swapPairs()`**:
- **Head**: `1`
- **Length**: `5`

**Doubly Linked List**:
`1 <-> 2 <-> 3 <-> 4 <-> 5`

**After `swapPairs()`**:
- **Head**: `2`
- **Length**: `5`

**Doubly Linked List**:
`2 <-> 1 <-> 4 <-> 3 <-> 5`

---

### Tips for Solving
1. **Visualize**:
   - Draw out the list structure and simulate the pointer changes.
2. **Plan Steps**:
   - Traverse the list in pairs.
   - For each pair:
     - Update the `next` and `prev` pointers to swap the nodes.
     - Ensure that the head pointer is updated for the new first node.
3. **Edge Cases**:
   - Handle cases where the list is empty or has only one node (no operation needed).
   - Carefully check and maintain the integrity of pointers during the swap.

---

### Reminder
This challenge is advanced and requires a solid understanding of doubly linked lists and pointer manipulation. Take your time, and revisit the problem if needed. Progress comes with perseverance!





```cpp
#include <iostream>

using namespace std;

class Node { 
    public: 
        int value;
        Node* next;
        Node* prev;
    
        Node(int value) {
            this->value = value;
            next = nullptr;
            prev = nullptr;
        }
};

class DoublyLinkedList {
    private:
        Node* head;
        Node* tail;
        int length;
    
    public:
        DoublyLinkedList(int value) {
            Node* newNode = new Node(value);
            head = newNode;
            tail = newNode;
            length = 1;
        }
    
        ~DoublyLinkedList() {
            Node* temp = head;
            while (head) {
                head = head->next;
                delete temp;
                temp = head;
            }
        }
    
        void printList() {
            Node* temp = head;
            if (temp == nullptr) {
                cout << "empty" << endl;
                return;
            }
            while (temp->next != nullptr) {
                cout << temp->value << " <-> ";
                temp = temp->next;
            }
            cout << temp->value << endl;
        }
    
        Node* getHead() {
            return head;
        }
    
        Node* getTail() {
            return tail;
        }
    
        int getLength() {
            return length;
        }

        void append(int value) {
            Node* newNode = new Node(value);
            if (length == 0) {
                head = newNode;
                tail = newNode;
            } else {
                tail->next = newNode;
                newNode->prev = tail;
                tail = newNode;
            }
            length++;
        }

        //   +=====================================================+
        //   |                 WRITE YOUR CODE HERE                |
        //   | Description:                                        |
        //   | - The swapPairs function swaps adjacent pairs       |
        //   |   of nodes in a doubly linked list.                 |
        //   | - Return type: void                                 |
        //   |                                                     |
        //   | Tips:                                               |
        //   | - Utilizes a dummyNode to simplify edge cases.      |
        //   | - Uses pointers to navigate and swap nodes.         |
        //   | - Pay close attention to the 'next' and 'prev'      |
        //   |   pointers of the nodes.                            |
        //   | - Works in-place; doesn't create new nodes.         |
        //   | - Always checks if the list is empty or has only    |
        //   |   one node.                                         |
        //   | - Check output from Test.cpp in "User logs".        |
        //   +=====================================================+

};



```

# CODE FOR TESTING


```cpp

#include <iostream>
#include "DoublyLinkedList.cpp"

using namespace std;


//  +=====================================================+
//  |                                                     |
//  |          THE TEST CODE BELOW WILL PRINT             |
//  |              OUTPUT TO "USER LOGS"                  |
//  |                                                     |
//  |  Use the output to test and troubleshoot your code  |
//  |                                                     |
//  +=====================================================+


static void test() {

    // Test: Swap Pairs with Single Node
    {
        cout << "\n----- Test: Swap Pairs with Single Node -----\n";
        DoublyLinkedList list(1);
        cout << "DLL before swapping pairs:\n";
        list.printList();
        list.swapPairs();
        cout << "\nDLL after swapping pairs:\n";
        list.printList();
        int value = list.getHead()->value;
        cout << "Head value after swapping pairs: " << value << " - EXPECTED: 1\n";
        cout << (value == 1 ? "PASS\n" : "FAIL\n");
    }

    // Test: Swap Pairs with Two Nodes
    {
        cout << "\n----- Test: Swap Pairs with Two Nodes -----\n";
        DoublyLinkedList list(1);
        list.append(2);
        cout << "DLL before swapping pairs:\n";
        list.printList();
        list.swapPairs();
        cout << "\nDLL after swapping pairs:\n";
        list.printList();
        int headValue = list.getHead()->value;
        int nextValue = list.getHead()->next->value;
        cout << "Head value after swapping pairs: " << headValue << " - EXPECTED: 2\n";
        cout << "Next value after swapping pairs: " << nextValue << " - EXPECTED: 1\n";
        cout << (headValue == 2 && nextValue == 1 ? "PASS\n" : "FAIL\n");
    }

    // Test: Swap Pairs with Multiple Nodes
    {
        cout << "\n----- Test: Swap Pairs with Multiple Nodes -----\n";
        DoublyLinkedList list(1);
        list.append(2);
        list.append(3);
        list.append(4);
        cout << "DLL before swapping pairs:\n";
        list.printList();
        list.swapPairs();
        cout << "\nDLL after swapping pairs:\n";
        list.printList();
        //cout << "PASS/FAIL test: ";
        cout << (list.getHead()->value == 2 && 
                 list.getHead()->next->value == 1 && 
                 list.getHead()->next->next->value == 4 &&
                 list.getHead()->next->next->next->value == 3 ? "PASS\n" : "FAIL\n");
    }

}


```


