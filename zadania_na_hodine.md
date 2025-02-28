
# Graph Practice Problems Based on Classroom Topics By Muc. Tom. 

## Graph: Add Vertex

---

### **Teoretical Learning Material**
[Video Tutorial](https://www.youtube.com/watch?v=yJjLqHZh9b0)

---

## Task
Implement the `addVertex` member function in the `Graph` class to add a new vertex to the graph's adjacency list.

## Requirements
The function should return a `bool` value, indicating whether the vertex was successfully added.

### Step 1: Check if the vertex already exists
- If the vertex is already present in the adjacency list (i.e., `adjList.count(vertex) != 0`), return `false`.

### Step 2: Add the new vertex
- If the vertex is not already present in the adjacency list, insert it as a new key with an empty `unordered_set` as its value.
- Then, return `true`.

## Notes
- Use an **unordered_map** to represent the adjacency list (`adjList`).
- Use an **unordered_set** to store the neighboring vertices.

```cpp 
#include <iostream>
#include <unordered_map>
#include <unordered_set>

using namespace std;


class Graph {
    private:
        unordered_map<string, unordered_set<string> > adjList;
    
    public:
        void printGraph() {
            unordered_map<string, unordered_set<string>>::iterator kvPair = adjList.begin();
            while (kvPair != adjList.end()) {
                cout << kvPair->first << ": [";
                unordered_set<string>::iterator edge = kvPair->second.begin();
                bool first = true;
                while (edge != kvPair->second.end()) {
                    if (!first) {
                        cout << ", ";
                    }
                    cout << *edge;
                    edge++;
                    first = false;
                }
                cout << "]" << endl;
                kvPair++;
            }
        }

		//   +=====================================================+
		//   |               WRITE YOUR CODE HERE                  |
		//   | Description:                                        |
		//   | - This method adds a vertex to the graph.           |
		//   | - It checks if the vertex already exists.           |
		//   |                                                     |
		//   | Return type: bool                                   |
		//   | - Returns true if vertex added, false otherwise.    |
		//   |                                                     |
		//   | Tips:                                               |
		//   | - Utilizes unordered_map for adjacency list.        |
		//   | - 'adjList' holds the graph data.                   |
		//   | - Check output from Test.cpp in "User logs".        |
		//   +=====================================================+

};



```

---


```cpp


#include <iostream>
#include "Graph.cpp"

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
    
    {
        cout << "\n----- Test: Add New Vertex -----\n";
        Graph g;
        cout << "Before:\n";
        g.printGraph();
        cout << "Adding vertex 'A'.\n";
        bool result = g.addVertex("A");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: true\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == true ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Add Duplicate Vertex -----\n";
        Graph g;
        g.addVertex("A");
        cout << "Before:\n";
        g.printGraph();
        cout << "Adding duplicate vertex 'A'.\n";
        bool result = g.addVertex("A");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: false\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == false ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Add Multiple Vertices -----\n";
        Graph g;
        cout << "Before:\n";
        g.printGraph();
        cout << "Adding vertices 'A', 'B', duplicate 'A', and duplicate 'B'.\n";
        bool result1 = g.addVertex("A");
        bool result2 = g.addVertex("B");
        bool result3 = g.addVertex("A");
        bool result4 = g.addVertex("B");
        cout << "After:\n";
        g.printGraph();
        cout << "Adding 'A': EXPECTED: true, RETURNED: " << (result1 ? "true" : "false") << "\n";
        cout << "Adding 'B': EXPECTED: true, RETURNED: " << (result2 ? "true" : "false") << "\n";
        cout << "Adding duplicate 'A': EXPECTED: false, RETURNED: " << (result3 ? "true" : "false") << "\n";
        cout << "Adding duplicate 'B': EXPECTED: false, RETURNED: " << (result4 ? "true" : "false") << "\n";
        cout << (result1 && result2 && !result3 && !result4 ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Add Empty String Vertex -----\n";
        Graph g;
        cout << "Before:\n";
        g.printGraph();
        cout << "Adding empty string vertex.\n";
        bool result = g.addVertex("");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: true\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == true ? "PASS\n" : "FAIL\n");
    }
    
}





```

---

# Graph: Add Edge

## Task
Implement the `addEdge` member function in the `Graph` class to add a new edge between two vertices in the graph's adjacency list.

## Requirements
The function should return a `bool` value, indicating whether the edge was successfully added.

### Step 1: Check if both vertices exist
- If both vertices (`vertex1` and `vertex2`) are present in the adjacency list (i.e., `adjList.count(vertex1) != 0` and `adjList.count(vertex2) != 0`), proceed to the next step.
- Otherwise, return `false`.

### Step 2: Add the new edge
- If both vertices are present in the adjacency list, insert `vertex2` into the `unordered_set` associated with `vertex1`, and insert `vertex1` into the `unordered_set` associated with `vertex2`.
- Return `true` to indicate that the edge was successfully added.

## Notes
- Use an **unordered_map** to represent the adjacency list (`adjList`).
- Use an **unordered_set** to store the neighboring vertices.



```cpp 

#include <iostream>
#include <unordered_map>
#include <unordered_set>

using namespace std;


class Graph {
    private:
        unordered_map<string, unordered_set<string> > adjList;
    
    public:
        void printGraph() {
            unordered_map<string, unordered_set<string>>::iterator kvPair = adjList.begin();
            while (kvPair != adjList.end()) {
                cout << kvPair->first << ": [";
                unordered_set<string>::iterator edge = kvPair->second.begin();
                bool first = true;
                while (edge != kvPair->second.end()) {
                    if (!first) {
                        cout << ", ";
                    }
                    cout << *edge;
                    edge++;
                    first = false;
                }
                cout << "]" << endl;
                kvPair++;
            }
        }

        bool addVertex(string vertex) {
            if (adjList.count(vertex) == 0) {
                adjList[vertex];
                return true;
            }
            return false;
        }

		//   +=====================================================+
		//   |                WRITE YOUR CODE HERE                 |
		//   | Description:                                        |
		//   | - This method adds an edge between vertex1 and      |
		//   |   vertex2 in the graph.                             |
		//   | - Checks if both vertices exist in the graph.       |
		//   |                                                     |
		//   | Return type: bool                                   |
		//   | - Returns true if edge is successfully added.       |
		//   | - Returns false if either vertex does not exist.    |
		//   |                                                     |
		//   | Tips:                                               |
		//   | - Uses 'adjList' to hold the graph's adjacency list.|
		//   | - Check output from Test.cpp in "User logs".        |
		//   +=====================================================+
        
};




```

---

```cpp

#include <iostream>
#include "Graph.cpp"

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
    
    {
        cout << "\n----- Test: Add Edge To Empty Graph -----\n";
        Graph g;
        cout << "Before:\n";
        g.printGraph();
        cout << "Adding edge between 'A' and 'B'.\n";
        bool result = g.addEdge("A", "B");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: false\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == false ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n---- Test: Add Edge Between Nonexistent Vertices (C & D) ----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        cout << "Before:\n";
        g.printGraph();
        cout << "Adding edge between 'C' and 'D'.\n";
        bool result = g.addEdge("C", "D");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: false\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == false ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Add Edge Between One Nonexistent Vertex (B) -----\n";
        Graph g;
        g.addVertex("A");
        cout << "Before:\n";
        g.printGraph();
        cout << "Adding edge between 'A' and 'B'.\n";
        bool result = g.addEdge("A", "B");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: false\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == false ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Add Edge Between Existing Vertices (A & B) -----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        cout << "Before:\n";
        g.printGraph();
        cout << "Adding edge between 'A' and 'B'.\n";
        bool result = g.addEdge("A", "B");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: true\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == true ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Add Duplicate Edge (A & B) -----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        g.addEdge("A", "B");
        cout << "Before:\n";
        g.printGraph();
        cout << "Adding edge again between 'A' and 'B'.\n";
        bool result = g.addEdge("A", "B");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: true\n";  // Adjusted based on your tests. If duplicates are not allowed, this should be "false"
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == true ? "PASS\n" : "FAIL\n");
    }
    
}


```


---



# Graph: Remove Edge

## Task
Implement the `removeEdge` member function in the `Graph` class to remove an existing edge between two vertices in the graph's adjacency list.

## Requirements
The function should return a `bool` value, indicating whether the edge was successfully removed.

### Step 1: Check if both vertices exist
- If both vertices (`vertex1` and `vertex2`) are present in the adjacency list (i.e., `adjList.count(vertex1) != 0` and `adjList.count(vertex2) != 0`), proceed to the next step.
- Otherwise, return `false`.

### Step 2: Remove the edge
- If both vertices are present in the adjacency list, erase `vertex2` from the `unordered_set` associated with `vertex1`, and erase `vertex1` from the `unordered_set` associated with `vertex2`.
- Return `true` to indicate that the edge was successfully removed.

## Notes
- Use an **unordered_map** to represent the adjacency list (`adjList`).
- Use an **unordered_set** to store the neighboring vertices.




```cpp

#include <iostream>
#include <unordered_map>
#include <unordered_set>

using namespace std;


class Graph {
    private:
        unordered_map<string, unordered_set<string> > adjList;
    
    public:
        void printGraph() {
            unordered_map<string, unordered_set<string>>::iterator kvPair = adjList.begin();
            while (kvPair != adjList.end()) {
                cout << kvPair->first << ": [";
                unordered_set<string>::iterator edge = kvPair->second.begin();
                bool first = true;
                while (edge != kvPair->second.end()) {
                    if (!first) {
                        cout << ", ";
                    }
                    cout << *edge;
                    edge++;
                    first = false;
                }
                cout << "]" << endl;
                kvPair++;
            }
        }

        bool addVertex(string vertex) {
            if (adjList.count(vertex) == 0) {
                adjList[vertex];
                return true;
            }
            return false;
        }

        bool addEdge(string vertex1, string vertex2) {
            if (adjList.count(vertex1) != 0 && adjList.count(vertex2) != 0) {
                adjList.at(vertex1).insert(vertex2);
                adjList.at(vertex2).insert(vertex1);
                return true;
            }         
            return false;            
        }

		//   +=====================================================+
		//   |                WRITE YOUR CODE HERE                 |
		//   | Description:                                        |
		//   | - This method removes an edge between vertex1 and   |
		//   |   vertex2 in the graph.                             |
		//   | - Checks if both vertices exist in the graph.       |
		//   |                                                     |
		//   | Return type: bool                                   |
		//   | - Returns true if edge is successfully removed.     |
		//   | - Returns false if either vertex does not exist.    |
		//   |                                                     |
		//   | Tips:                                               |
		//   | - Uses 'adjList' to update the graph's adjacency    |
		//   |   list.                                             |
		//   | - Check output from Test.cpp in "User logs".        |
		//   +=====================================================+
        
};




```

---

```cpp


#include <iostream>
#include "Graph.cpp"

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
    
    {
        cout << "\n----- Test: Remove Edge From Empty Graph -----\n";
        Graph g;
        cout << "Before:\n";
        g.printGraph();
        cout << "Removing edge between 'A' and 'B'.\n";
        bool result = g.removeEdge("A", "B");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: false\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == false ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Remove Edge Between Nonexistent Vertices -----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        cout << "Before:\n";
        g.printGraph();
        cout << "Removing edge between 'C' and 'D'.\n";
        bool result = g.removeEdge("C", "D");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: false\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == false ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Remove NonExistent Edge Between Existing Vertices -----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        cout << "Before:\n";
        g.printGraph();
        cout << "Removing edge between 'A' and 'B'.\n";
        bool result = g.removeEdge("A", "B");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: true\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == true ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Remove Existing Edge -----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        g.addEdge("A", "B");
        cout << "Before first removal:\n";
        g.printGraph();
        cout << "Removing edge between 'A' and 'B'.\n";
        bool result1 = g.removeEdge("A", "B");
        cout << "After first removal:\n";
        g.printGraph();
        cout << "Removing edge again between 'A' and 'B'.\n";
        bool result2 = g.removeEdge("A", "B");
        cout << "After second removal:\n";
        g.printGraph();
        cout << "First removal: EXPECTED: true, RETURNED: " << (result1 ? "true" : "false") << "\n";
        cout << "Second removal: EXPECTED: true, RETURNED: " << (result2 ? "true" : "false") << "\n";
        cout << ((result1 && result2) == true ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Remove Edge After Vertex Removal -----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        g.addEdge("A", "B");
        g.removeEdge("A", "B");
        cout << "Before second removal:\n";
        g.printGraph();
        cout << "Removing edge again between 'A' and 'B'.\n";
        bool result = g.removeEdge("A", "B");
        cout << "After second removal:\n";
        g.printGraph();
        cout << "EXPECTED: true\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == true ? "PASS\n" : "FAIL\n");
    }
    
}


```




---


# Graph: Remove Vertex

## Task
Implement the `removeVertex` member function in the `Graph` class to remove an existing vertex and its associated edges from the graph's adjacency list.

## Requirements
The function should return a `bool` value, indicating whether the vertex was successfully removed.

### Step 1: Check if the vertex exists
- If the vertex is present in the adjacency list (i.e., `adjList.count(vertex) != 0`), proceed to the next step.
- Otherwise, return `false`.

### Step 2: Remove the edges associated with the vertex
- For each vertex (`otherVertex`) connected to the vertex to be removed, erase the vertex from the `unordered_set` associated with `otherVertex`.

### Step 3: Remove the vertex
- After removing all associated edges, erase the vertex from the adjacency list.
- Return `true` to indicate that the vertex was successfully removed.

## Notes
- Use an **unordered_map** to represent the adjacency list (`adjList`).
- Use an **unordered_set** to store the neighboring vertices.


```cpp

#include <iostream>
#include <unordered_map>
#include <unordered_set>

using namespace std;


class Graph {
    private:
        unordered_map<string, unordered_set<string> > adjList;
    
    public:
        void printGraph() {
            unordered_map<string, unordered_set<string>>::iterator kvPair = adjList.begin();
            while (kvPair != adjList.end()) {
                cout << kvPair->first << ": [";
                unordered_set<string>::iterator edge = kvPair->second.begin();
                bool first = true;
                while (edge != kvPair->second.end()) {
                    if (!first) {
                        cout << ", ";
                    }
                    cout << *edge;
                    edge++;
                    first = false;
                }
                cout << "]" << endl;
                kvPair++;
            }
        }

        bool addVertex(string vertex) {
            if (adjList.count(vertex) == 0) {
                adjList[vertex];
                return true;
            }
            return false;
        }

        bool addEdge(string vertex1, string vertex2) {
            if (adjList.count(vertex1) != 0 && adjList.count(vertex2) != 0) {
                adjList.at(vertex1).insert(vertex2);
                adjList.at(vertex2).insert(vertex1);
                return true;
            }         
            return false;            
        }

        bool removeEdge(string vertex1, string vertex2) {
            if (adjList.count(vertex1) != 0 && adjList.count(vertex2) != 0) {
                adjList.at(vertex1).erase(vertex2);
                adjList.at(vertex2).erase(vertex1);
                return true;
            }
            return false;
        }

		//   +=====================================================+
		//   |                WRITE YOUR CODE HERE                 |
		//   | Description:                                        |
		//   | - This method removes a vertex from the graph.      |
		//   | - Removes all edges connected to this vertex.       |
		//   |                                                     |
		//   | Return type: bool                                   |
		//   | - Returns true if vertex is successfully removed.   |
		//   | - Returns false if the vertex does not exist.       |
		//   |                                                     |
		//   | Tips:                                               |
		//   | - Uses 'adjList' to update the graph's adjacency    |
		//   |   list.                                             |
		//   | - Check output from Test.cpp in "User logs".        |
		//   +=====================================================+
        
};


```

---

```cpp

#include <iostream>
#include "Graph.cpp"

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
    
    {
        cout << "\n----- Test: Remove NonExistent Vertex -----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        cout << "Before:\n";
        g.printGraph();
        cout << "Removing vertex 'C'.\n";
        bool result = g.removeVertex("C");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: false\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == false ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Remove Vertex With No Edges -----\n";
        Graph g;
        g.addVertex("A");
        cout << "Before:\n";
        g.printGraph();
        cout << "Removing vertex 'A'.\n";
        bool result = g.removeVertex("A");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED: true\n";
        cout << "RETURNED: " << (result ? "true" : "false") << "\n";
        cout << (result == true ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Remove Vertex With Multiple Edges -----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        g.addVertex("C");
        g.addEdge("A", "B");
        g.addEdge("A", "C");
        cout << "Before:\n";
        g.printGraph();
        cout << "Removing vertex 'A'.\n";
        bool result1 = g.removeVertex("A");
        bool result2 = g.removeVertex("A");  // Trying again
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED 1st Removal: true\n";
        cout << "RETURNED 1st Removal: " << (result1 ? "true" : "false") << "\n";
        cout << "EXPECTED 2nd Removal: false\n";
        cout << "RETURNED 2nd Removal: " << (result2 ? "true" : "false") << "\n";
        cout << (result1 && !result2 ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Remove Vertex And Check Edges -----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        g.addVertex("C");
        g.addEdge("A", "B");
        g.addEdge("A", "C");
        cout << "Before:\n";
        g.printGraph();
        cout << "Removing vertex 'A'.\n";
        g.removeVertex("A");
        bool result1 = g.removeEdge("A", "B");
        bool result2 = g.removeEdge("A", "C");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED Edges Removal: false, false\n";
        cout << "RETURNED Edges Removal: " << (result1 ? "true" : "false") << ", " << (result2 ? "true" : "false") << "\n";
        cout << (!result1 && !result2 ? "PASS\n" : "FAIL\n");
    }

    {
        cout << "\n----- Test: Remove Vertex And Update Graph -----\n";
        Graph g;
        g.addVertex("A");
        g.addVertex("B");
        g.addEdge("A", "B");
        cout << "Before:\n";
        g.printGraph();
        cout << "Removing vertex 'A' and re-adding it, then re-adding edge A-B.\n";
        g.removeVertex("A");
        g.addVertex("A");
        bool result = g.addEdge("A", "B");
        cout << "After:\n";
        g.printGraph();
        cout << "EXPECTED Edge Addition: true\n";
        cout << "RETURNED Edge Addition: " << (result ? "true" : "false") << "\n";
        cout << (result ? "PASS\n" : "FAIL\n");
    }
    
}


```

--- 


# Heap: Insert

## Task
You are given a `Heap` class that encapsulates the functionality of a **max heap**, except for one crucial operation: inserting a new element while maintaining the heap's integrity. Your task is to implement the `insert` method for this class.

## Requirements

### Method Prototype
```cpp
void insert(int value);
```

### Functionality
Your implementation must:
1. **Add a new integer value to the heap.**  
   - After insertion, the heap must still comply with the **max heap property**, where each parent node's value is greater than or equal to the values of its children.

2. **Initial Insertion:**
   - Begin by adding the new value to the **end** of the heap's internal storage (`heap` vector).
   - This action maintains the **completeness** of the binary tree but may temporarily disrupt the **max heap property**.

3. **Heap Restoration:**
   - Adjust the position of the newly inserted element by comparing it with its parent's value.
   - If the new element's value is **greater** than its parent’s, swap them.
   - Repeat this process until:
     - The new element is **no longer greater than its parent**, or  
     - It becomes the **root** of the heap.

4. **Utility Functions:**
   - Use the provided helper functions:
     - `parent(int index)`: Calculates the index of a node's parent.
     - `swap(int index1, int index2)`: Exchanges the values of two nodes in the heap.

## Additional Information
- The `heap` vector is used to represent the heap structure and is a **private member** of the `Heap` class.
- The heap is **zero-indexed**, with the **root element at index 0**.

## Example Usage

**Given initial heap:**  
```cpp
[20, 15, 10]
```
**After calling `insert(22)`:**  
```cpp
[22, 15, 10, 20]
```
The heap property is maintained after the insertion.

```cpp
#include <iostream>
#include <vector>
#include <climits> 

using namespace std;

class Heap {
    private:
        vector<int> heap;

        int leftChild(int index) {
            return 2 * index + 1;
        }

        int rightChild(int index) {
            return 2 * index + 2;
        }

        int parent(int index) {
            return (index - 1) / 2;
        }

        void swap(int index1, int index2) {
            int temp = heap[index1];
            heap[index1] = heap[index2];
            heap[index2] = temp;
        }

    public:
        void printHeap() {
            cout << "\n[";
            for (size_t i = 0; i < heap.size(); i++) {
                cout << heap[i];
                if (i < heap.size() - 1) { 
                    cout << ", ";
                }
            }
            cout << "]" << endl;
        }
        
        const vector<int>& getHeap() const {
            return heap;
        }

        //   +===================================================+
        //   |              WRITE YOUR CODE HERE                 |
        //   | Description:                                      |
        //   | - Inserts a new value into the heap.              |
        //   | - Maintains the heap's property by ensuring the   |
        //   |   newly inserted element is moved to its          |
        //   |   correct position in the heap.                   |
        //   |                                                   |
        //   | Parameters:                                       |
        //   | - value: The value to be inserted into the heap.  |
        //   |                                                   |
        //   | Behavior:                                         |
        //   | - The value is added to the end of the heap.      |
        //   | - The method then compares the added value with   |
        //   |   its parent node, swapping them if necessary to  |
        //   |   maintain the heap property.                     |
        //   | - This comparison and potential swap continue     |
        //   |   until the heap property is restored or the      |
        //   |   added node becomes the root of the heap.        |
        //   +===================================================+

};

```

---


# Heap: Remove

## Task
Your task is to complete the `remove` method for the `Heap` class, which encapsulates a **max heap** structure. This method should remove and return the **maximum value** from the heap while ensuring the heap's integrity and maintaining the **max heap property** after removal.

## Functionality Details

### Method Prototype
```cpp
int remove();
```

### Return Value
- The method returns the **maximum value** in the heap.
- If the heap is **empty**, it returns `INT_MIN` to indicate that no value can be removed.

### Max Heap Property
- After removing the **maximum value** (the root of the heap), the heap must still satisfy the **max heap property**, where each **parent node's value** is greater than or equal to the values of its children.

## Implementation Steps

### 1. Handle Empty Heap
- Check if the heap is **empty**.
- If so, return `INT_MIN`.

### 2. Remove the Maximum Value
- Save the **value at the root** of the heap (the first element in the heap vector), as this is the **maximum value** to be removed and returned.
- If the heap contains **more than one element**:
  - Replace the **root** with the **last element** in the heap.
  - Remove the **last element**.  
  - This action ensures the **completeness** of the binary tree but may violate the **max heap property**.
- If the heap contains **only one element**:
  - Simply **remove it**.

### 3. Restore the Max Heap Property
- If you've **replaced the root with the last element**, call the `sinkDown` method **starting from the new root** to adjust the heap.
- The `sinkDown` method ensures the **new root moves down** to its correct position while maintaining the **heap's integrity**.

## Requirements
- Utilize the provided **`sinkDown` method** to adjust the heap after removing the root.
- The **heap vector** is the internal storage for the heap's elements and should be manipulated accordingly.
- The heap is **zero-indexed**, with the **root element at index 0**.

## Example Usage

**Given initial heap:**  
```cpp
[30, 20, 15, 5, 10, 12, 6]
```
**After calling `remove()`:**  
- The method should return `30`.
- The heap should be adjusted to:
```cpp
[20, 10, 15, 5, 6, 12]
```

```cpp

#include <iostream>
#include <vector>
#include <climits> 

using namespace std;

class Heap {
    private:
        vector<int> heap;

        int leftChild(int index) {
            return 2 * index + 1;
        }

        int rightChild(int index) {
            return 2 * index + 2;
        }

        int parent(int index) {
            return (index - 1) / 2;
        }

        void swap(int index1, int index2) {
            int temp = heap[index1];
            heap[index1] = heap[index2];
            heap[index2] = temp;
        }



    public:
        void printHeap() {
            cout << "\n[";
            for (size_t i = 0; i < heap.size(); i++) {
                cout << heap[i];
                if (i < heap.size() - 1) { 
                    cout << ", ";
                }
            }
            cout << "]" << endl;
        }
        
        const vector<int>& getHeap() const {
            return heap;
        }

        void insert(int value) {
            heap.push_back(value);
            int current = heap.size() - 1;

            while (current > 0 && heap[current] > heap[parent(current)]) {
                swap(current, parent(current));
                current = parent(current);
            }
        }

        void sinkDown(int index) {
            int maxIndex = index;
            while (true) {
                int leftIndex = leftChild(index);
                int rightIndex = rightChild(index);

                if (leftIndex < heap.size() && heap[leftIndex] > heap[maxIndex]) {
                    maxIndex = leftIndex;
                }

                if (rightIndex < heap.size() && heap[rightIndex] > heap[maxIndex]) {
                    maxIndex = rightIndex;
                }

                if (maxIndex != index) {
                    swap(index, maxIndex);
                    index = maxIndex;
                } else {
                    return;
                }
            }
        }

        //   +===================================================+
        //   |              WRITE YOUR CODE HERE                 |
        //   | Description:                                      |
        //   | - Removes and returns the maximum value from      |
        //   |   the heap.                                       |
        //   | - Maintains the heap's property by reorganizing   |
        //   |   the heap after the removal.                     |
        //   |                                                   |
        //   | Return:                                           |
        //   | - The maximum value in the heap. If the heap is   |
        //   |   empty, returns INT_MIN as an error indication.  |
        //   |                                                   |
        //   | Behavior:                                         |
        //   | - If the heap is empty, returns INT_MIN.          |
        //   | - Saves the maximum value (the root of the heap). |
        //   | - Replaces the root with the last element in the  |
        //   |   heap and then restores the heap property using  |
        //   |   a sink down operation.                          |
        //   | - If there's only one element, it is simply       |
        //   |   removed from the heap.                          |
        //   +===================================================+

};

```

---

# Heap: Sink Down

## Task
Your task is to implement the `sinkDown` method within the `Heap` class. This method is crucial for maintaining the **max heap's integrity** after operations that might disturb its order, such as **removing the maximum element**. The `sinkDown` method ensures that the **heap property** is preserved by adjusting the position of an element within the heap.

## Method Overview

### Prototype
```cpp
void sinkDown(int index);
```

### Purpose
- Adjusts the heap starting from the node at the given `index`, moving **downwards** to ensure the **max heap property** is maintained.
- The **max heap property** requires that a **parent node's value** must be **greater than or equal** to the values of its children.

## Implementation Details

### 1. Starting Point
- The method begins at the node specified by `index`.  
- This is **typically** the new root after a removal or any node that might **violate the max heap property**.

### 2. Child Nodes Evaluation
- Determine the **indices** of the **left** and **right children** of the current node using the `leftChild` and `rightChild` methods.
- Compare the **values** of these children against the **current node** to identify if a swap is needed to maintain the **max heap property**.

### 3. Selecting the Larger Child
- If **either child** is larger than the **current node** (`heap[maxIndex]`), update `maxIndex` to the **index of the larger child**.
- The goal is to ensure that the **parent node always holds a value greater than or equal to its children**.

### 4. Swapping and Continuing
- If a **larger child** is found (`maxIndex` changes), swap the **current node** with this child using the `swap` method.
- Update the `index` to the `maxIndex` of the **larger child** and **continue** the process.
- This **iterative or recursive** continuation is necessary because the swap might introduce new violations **further down** the tree.

### 5. Termination
- The process repeats until **no child is larger** than the **current node**.
- This ensures that the node has been **"sunk"** to its correct position and that the **max heap property** is restored.

## Constraints
- Assume the heap is implemented as a **`std::vector<int>`** named `heap`, storing the elements.
- The heap is **zero-indexed**, with the **root of the heap at index 0**, and the tree is filled **from left to right**.

## Example Scenario

### Given Initial Heap (Before Removal)
```cpp
[50, 30, 40, 10, 20]
```

### After Removing the Maximum Element:
- If the root (`50`) is removed and replaced with the last element, the heap becomes:
```cpp
[20, 30, 40, 10]
```

### Applying `sinkDown`:
- The `sinkDown` method should adjust the heap back to:
```cpp
[40, 30, 20, 10]
```
- This restores the **max heap order**.



```cpp


#include <iostream>
#include <vector>
#include <climits> 

using namespace std;

class Heap {
    private:
        vector<int> heap;

        int leftChild(int index) {
            return 2 * index + 1;
        }

        int rightChild(int index) {
            return 2 * index + 2;
        }

        int parent(int index) {
            return (index - 1) / 2;
        }

        void swap(int index1, int index2) {
            int temp = heap[index1];
            heap[index1] = heap[index2];
            heap[index2] = temp;
        }



    public:
        void printHeap() {
            cout << "\n[";
            for (size_t i = 0; i < heap.size(); i++) {
                cout << heap[i];
                if (i < heap.size() - 1) { 
                    cout << ", ";
                }
            }
            cout << "]" << endl;
        }
        
        const vector<int>& getHeap() const {
            return heap;
        }

        void insert(int value) {
            heap.push_back(value);
            int current = heap.size() - 1;

            while (current > 0 && heap[current] > heap[parent(current)]) {
                swap(current, parent(current));
                current = parent(current);
            }
        }

        
        //   +===================================================+
        //   |              WRITE YOUR CODE HERE                 |
        //   | Description:                                      |
        //   | - Performs the sink down operation in the heap.   |
        //   | - It's used to restore the heap's properties      |
        //   |   by moving a node down the tree until it is      |
        //   |   either smaller than its children or in its      |
        //   |   correct position.                               |
        //   |                                                   |
        //   | Parameters:                                       |
        //   | - index: The starting index for the sink down     |
        //   |   operation.                                      |
        //   |                                                   |
        //   | Behavior:                                         |
        //   | - Compares the node with its left and right       |
        //   |   children.                                       |
        //   | - If the node is smaller than either of its       |
        //   |   children, it is swapped with the larger child.  |
        //   | - This process repeats until the node is larger   |
        //   |   than both its children or it reaches the bottom |
        //   |   of the heap.                                    |
        //   +===================================================+


        int remove() {
            if (heap.empty()) {
                return INT_MIN;
            }

            int maxValue = heap.front();

            if (heap.size() == 1) {
                heap.pop_back();
            } else {
                heap[0] = heap.back();
                heap.pop_back();
                sinkDown(0);
            }

            return maxValue;
        }

};


```

---


# Heap: MinHeap Insert

## Task
You are tasked with implementing the `insert` function within the `MinHeap` class.  
This class models a **min heap**, a specialized tree-based data structure that satisfies the **heap property**:  
- In a **min heap**, every **parent node** is **less than or equal** to its children.  
- Your implementation should ensure that **after inserting a new element**, the **min heap property** remains intact.

## Method Prototype
```cpp
void insert(int value);
```

## Key Requirements

### 1. Adding the New Element
- The method starts by **adding the new element** to the **end** of the heap vector.
- This action **maintains the complete binary tree structure** but **might temporarily violate** the min heap property.

### 2. Restoring the Min Heap Property
- After the initial addition, the **min heap property may be disrupted**.
- You must restore this property by ensuring that, for any given node, its **value is less than or equal to its parent's value**.
- This involves:
  1. Comparing the newly added element with its **parent** (using the `parent` method to find the parent’s index).
  2. Swapping their values if the **child’s value is smaller** (using the provided `swap` method).
  3. Continuing this **"bubble-up"** process until:
     - The **new element reaches its correct position**, or
     - The new element becomes the **root of the heap**.

## Functionality to Utilize
- **`parent(int index)`**: Returns the index of the **parent node**.
- **`swap(int index1, int index2)`**: Swaps the values of two nodes in the heap.

## Constraints
- Assume the heap is represented **internally** as a `std::vector<int>`, starting with:
  - An **empty vector**, or  
  - A vector that **already satisfies the min heap property** before insertion.
- The heap vector is **zero-indexed**, meaning the **first element (root of the heap) is at index 0**.

## Expected Behavior

### Example
#### **Given initial min heap:**  
```cpp
[2, 4, 3]
```
#### **After calling `insert(1)`:**  
```cpp
[1, 4, 3, 2]
```
- The `insert` function **adjusts the heap** to **maintain the min heap property**.


```cpp

#include <iostream>
#include <vector>
#include <climits>

using namespace std;

class MinHeap {
    private:
        vector<int> heap;
    
        int leftChild(int index) {
            return 2 * index + 1;
        }
    
        int rightChild(int index) {
            return 2 * index + 2;
        }
    
        int parent(int index) {
            return (index - 1) / 2;
        }
    
        void swap(int index1, int index2) {
            int temp = heap[index1];
            heap[index1] = heap[index2];
            heap[index2] = temp;
        }
    
    public:
        void printHeap() {
            cout << "\n[";
            for (size_t i = 0; i < heap.size(); i++) {
                cout << heap[i];
                if (i < heap.size() - 1) { 
                    cout << ", ";
                }
            }
            cout << "]" << endl;
        }
        
        const vector<int>& getHeap() const {
            return heap;
        }
    
        //   +===================================================+
        //   |              WRITE YOUR CODE HERE                 |
        //   | Description:                                      |
        //   | - Inserts a new value into the min heap.          |
        //   | - Adjusts the heap to maintain the min heap       |
        //   |   property after the insertion.                   |
        //   |                                                   |
        //   | Parameters:                                       |
        //   | - value: The value to be inserted into the heap.  |
        //   |                                                   |
        //   | Behavior:                                         |
        //   | - The value is added to the end of the heap.      |
        //   | - The method then compares the added value with   |
        //   |   its parent, swapping them if the child is       |
        //   |   smaller, to maintain the min heap property.     |
        //   | - This comparison and potential swap continue     |
        //   |   until the new node is in its correct position   |
        //   |   or it becomes the root node.                    |
        //   +===================================================+
        
};
    

```

---


# Heap: MinHeap Remove

## Task
Your task is to implement the `remove` function within the `MinHeap` class.  
This class encapsulates a **min heap**, a binary tree-based data structure where **every parent node has a value less than or equal to any of its children**.  
The `remove` function should efficiently **remove and return the minimum element** from the heap while ensuring that:
- The **structure's integrity** is maintained.
- The **min heap property** is preserved after removal.

## Method Prototype
```cpp
int remove();
```

## Key Requirements

### 1. Return Value
- The method should **return the minimum value** in the heap.
- If the heap is **empty**, return `INT_MIN` as an indicator of the **underflow condition**.

### 2. Maintaining Heap Structure and Property

#### **1. Empty Check**
- Check if the heap is **empty**.
- If so, return `INT_MIN`.

#### **2. Removing the Root**
- The root of the heap (**the minimum value**) is to be **removed**.
- To maintain the heap's structure, follow these steps:
  1. **Replace the root** with the **last element** in the heap.
  2. **Remove the last element** from the heap.
  3. This may disrupt the **min heap order**, so further adjustments are necessary.

#### **3. Heap Property Restoration**
- Use the **`sinkDown`** method starting from the **new root** to **re-establish** the **min heap property**.
- The `sinkDown` method should adjust the **new root’s position**, ensuring that **parent nodes are smaller than their children** throughout the heap.

## Functionality to Utilize
- **`sinkDown(int index)`**: Use this method to restore the **min heap property** after **removing and replacing the root**.
- **Helper Functions**:
  - **`leftChild(int index)`**: Returns the index of the **left child**.
  - **`rightChild(int index)`**: Returns the index of the **right child**.
  - **`swap(int index1, int index2)`**: Swaps the values of two heap elements.

## Constraints
- The heap is internally represented as a **`std::vector<int>`** named **`heap`**.
- The heap is **zero-indexed**, meaning:
  - The **root element is at index 0**.
  - The tree is filled **from left to right**.

## Expected Behavior

### Example
#### **Given initial min heap:**
```cpp
[3, 4, 8, 10, 9, 7]
```
#### **After calling `remove()`:**
- The method should return `3`.
- The heap should adjust to:
```cpp
[4, 9, 7, 10, 8]
```
- This maintains the **min heap property**.


```cpp

#include <iostream>
#include <vector>
#include <climits>

using namespace std;

class MinHeap {
    private:
        vector<int> heap;
    
        int leftChild(int index) {
            return 2 * index + 1;
        }
    
        int rightChild(int index) {
            return 2 * index + 2;
        }
    
        int parent(int index) {
            return (index - 1) / 2;
        }
    
        void swap(int index1, int index2) {
            int temp = heap[index1];
            heap[index1] = heap[index2];
            heap[index2] = temp;
        }
    
    public:
        void printHeap() {
            cout << "\n[";
            for (size_t i = 0; i < heap.size(); i++) {
                cout << heap[i];
                if (i < heap.size() - 1) { 
                    cout << ", ";
                }
            }
            cout << "]" << endl;
        }
        
        const vector<int>& getHeap() const {
            return heap;
        }
    
        void insert(int value) {
            heap.push_back(value);
            int current = heap.size() - 1;
    
            while (current > 0 && heap[current] < heap[parent(current)]) {
                swap(current, parent(current));
                current = parent(current);
            }
        }
    
        void sinkDown(int index) {
            int minIndex = index;
            while (true) {
                int leftIndex = leftChild(index);
                int rightIndex = rightChild(index);
    
                if (leftIndex < heap.size() && heap[leftIndex] < heap[minIndex]) {
                    minIndex = leftIndex;
                }
    
                if (rightIndex < heap.size() && heap[rightIndex] < heap[minIndex]) {
                    minIndex = rightIndex;
                }
    
                if (minIndex != index) {
                    swap(index, minIndex);
                    index = minIndex;
                } else {
                    return;
                }
            }
        }
    
        //   +===================================================+
        //   |              WRITE YOUR CODE HERE                 |
        //   | Description:                                      |
        //   | - Removes and returns the minimum value from the  |
        //   |   min heap.                                       |
        //   | - Ensures the heap maintains its properties after |
        //   |   the removal of the root element.                |
        //   |                                                   |
        //   | Return:                                           |
        //   | - The minimum value in the heap. If the heap is   |
        //   |   empty, returns INT_MIN as a signal of underflow.|
        //   |                                                   |
        //   | Behavior:                                         |
        //   | - If the heap is empty, returns INT_MIN.          |
        //   | - Saves the minimum value (the root of the heap). |
        //   | - Replaces the root with the last element in the  |
        //   |   heap and restores the heap property using a     |
        //   |   sink down operation.                            |
        //   | - If there's only one element, it is simply       |
        //   |   removed from the heap.                          |
        //   +===================================================+
    
};




```

---


# Heap: MinHeap Sink Down

## Task
Your task is to complete the implementation of the `sinkDown` method within the `MinHeap` class.  
This method plays a **critical role** in maintaining the **min heap's structure and properties**,  
especially after the **removal of the minimum element** or any operation that might **disrupt the heap order**.

## Method Prototype
```cpp
void sinkDown(int index);
```

## Key Requirements

### 1. Purpose
- The `sinkDown` method adjusts the heap to ensure that **every parent node** is **less than or equal** to its children.
- This adjustment is crucial after:
  - The **root element (minimum value) is removed**.
  - The **last element in the heap replaces the root**.

### 2. Functionality

1. **Start from the node at the given index**.
2. **Compare this node** to its **left and right children** to find the **smallest** of the three.
3. **If the node is not the smallest**, swap it with its **smallest child**.
4. **Continue this process** (potentially moving down multiple levels in the heap) until:
   - The node is **smaller than both of its children**.
   - The node **has no children**.
5. This ensures that the **min heap property is preserved**.

### 3. Iterative Approach
- Utilize a **while loop** that runs indefinitely **until explicitly exited**.
- This loop facilitates the **comparison and potential swapping down the heap**.
- Steps:
  1. Determine the **indices** of the **left and right children** using the `leftChild` and `rightChild` methods.
  2. Update `minIndex` if either **child is smaller** than the **current node**.
  3. If necessary, **swap** the current node with the **smallest child**.
  4. Update the **current index** to **continue down the heap**.

### 4. Termination Condition
- Exit the loop and **end the method** if the **current node is in its correct position**, meaning:
  - It is **smaller than its children**.
  - It **has no children**.

## Functionality to Utilize
- **Helper Functions**:
  - `leftChild(int index)`: Returns the **index** of the **left child**.
  - `rightChild(int index)`: Returns the **index** of the **right child**.
  - `swap(int index1, int index2)`: **Swaps** the values of two heap elements.

## Constraints
- The heap is represented as a **`std::vector<int>`** named **`heap`**, which is **private** to the `MinHeap` class.
- The heap is **zero-indexed**, meaning:
  - The **root of the heap** is at **index 0**.

## Expected Behavior

### Example
#### **Given initial min heap:**
```cpp
[5, 4, 8, 17, 10]
```
#### **After removing the root (5) and replacing it with 10:**
```cpp
[10, 4, 8, 17]
```
#### **After calling `sinkDown(0)`:**
```cpp
[4, 10, 8, 17]
```
- This restores the **min heap property**.


```cpp

#include <iostream>
#include <vector>
#include <climits>

using namespace std;

class MinHeap {
    private:
        vector<int> heap;
    
        int leftChild(int index) {
            return 2 * index + 1;
        }
    
        int rightChild(int index) {
            return 2 * index + 2;
        }
    
        int parent(int index) {
            return (index - 1) / 2;
        }
    
        void swap(int index1, int index2) {
            int temp = heap[index1];
            heap[index1] = heap[index2];
            heap[index2] = temp;
        }
    
    public:
        void printHeap() {
            cout << "\n[";
            for (size_t i = 0; i < heap.size(); i++) {
                cout << heap[i];
                if (i < heap.size() - 1) { 
                    cout << ", ";
                }
            }
            cout << "]" << endl;
        }
        
        const vector<int>& getHeap() const {
            return heap;
        }
    
        void insert(int value) {
            heap.push_back(value);
            int current = heap.size() - 1;
    
            while (current > 0 && heap[current] < heap[parent(current)]) {
                swap(current, parent(current));
                current = parent(current);
            }
        }
 
    
        //   +===================================================+
        //   |              WRITE YOUR CODE HERE                 |
        //   | Description:                                      |
        //   | - Performs the sink down operation on the min     |
        //   |   heap to maintain the heap property after        |
        //   |   removal or insertion.                           |
        //   | - This method is used to adjust the position of   |
        //   |   a node to ensure the smallest element remains   |
        //   |   at the root of the heap.                        |
        //   |                                                   |
        //   | Parameters:                                       |
        //   | - index: The starting index from where the sink   |
        //   |   down operation begins.                          |
        //   |                                                   |
        //   | Behavior:                                         |
        //   | - Compares the node at the given index with its   |
        //   |   left and right children to find the smallest    |
        //   |   of the three.                                   |
        //   | - If the current node is not the smallest, it is  |
        //   |   swapped with the smallest child, and the        |
        //   |   operation repeats for the new position.         |
        //   | - Continues until the node is in its correct      |
        //   |   position (smaller than its children or it has   |
        //   |   no children).                                   |
        //   +===================================================+


        int remove() {
            if (heap.empty()) {
                return INT_MIN;
            }
    
            int minValue = heap.front();
    
            if (heap.size() == 1) {
                heap.pop_back();
            } else {
                heap[0] = heap.back();
                heap.pop_back();
                sinkDown(0);
            }
    
            return minValue;
        }
    
};




```

