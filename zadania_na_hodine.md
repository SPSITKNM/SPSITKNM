
# Graph Practice Problems Based on Classroom Topics 

## Graph: Add Vertex

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

