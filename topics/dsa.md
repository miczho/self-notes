## Data Structures & Algorithms

*TIPS, TRICKS, AND TECHNIQUES ON ALL THINGS DATA & ALGO*

#### Table of Contents:

- [Built-In Data Structures](#built-in_ds)
- [Binary Search](#binary_search)
    - [Longest Increasing Subsequence](#binary_search_lis)
    - [Ternary Search](#ternary_search)
- [Topological Sort](#topological_sort)
- [Dijkstra's Algorithm](#dijkstras)
    - [0-1 BFS](#0-1_bfs)
- Minimum Spanning Tree (WIP)
- Binary Lifting (WIP)
- [Dynamic Programming](#dynamic_programming)
    - [Knapsack](#dp_knapsack)
- [Union Find](#union_find)
- [Segment Tree](#segment_tree)
- [Trie](#trie)
- [Bit Manipulation](#bit_manipulation)


# <a id="built-in_ds"></a> Built-In Data Structures

A lot of simple/generic data structures are provided by coding languages as tooling

### Arrays, Lists

An *array* is a fixed-size sequence of elements of the same type, allowing direct access by index

A *list* is a dynamically-sized sequence of elements

| Operation | Array | Array List | Doubly Linked List |
| --------- | ----- | ---------- | ------------------ |
| Access by Index | O(1) | O(1) | O(n) |
| Update | O(1) | O(1) | O(n) |
| Insert Start | N/A | O(n) | O(1) |
| Insert Middle | N/A | O(n) | O(n) |
| Insert End | N/A | O(1) amortized | O(1) |
| Remove Start | N/A | O(n) | O(1) |
| Remove Middle | N/A | O(n) | O(n) |
| Remove End | N/A | O(1) | O(1) |

[Python's `list`](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists) is an array list  
[Java's `LinkedList`](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html) is a doubly linked list

### Sets, Maps

A *set* is a collection of unique elements

A *map* is a collection of key-value pairs, where each key is unique

| Operation | Hash Set (Unordered) | Tree/Sorted Set (Ordered) | Hash Map | Tree/Sorted Map  |
| --------- | -------------------- | ------------------------- |--------- | ---------------- |
| Access by Key | N/A | N/A | O(1) amortized | O(log n) |
| Access by Value | O(1) amortized | O(log n) | O(n) | O(n) |
| Update | N/A | N/A | O(1) amortized | O(log n) |
| Insert | O(1) amortized | O(log n) | O(1) amortized | O(log n) |
| Remove | O(1) amortized | O(log n) | O(1) amortized | O(log n) |

### Stacks, Queues, Deques

A *stack* is a sequence of elements following the Last-In-First-Out (LIFO) principle

A *queue* is a sequence of elements following the First-In-First-Out (FIFO) principle

A *deque* is a double-ended queue. Can be used as both a stack and a queue

| Operation | Stack | Queue | Deque |
| --------- | ----- | ----- | ----- |
| Insert Left | N/A | O(1) | O(1) |
| Insert Right | O(1) | N/A | O(1) |
| Remove Left | N/A | N/A | O(1) |
| Remove Right | O(1) | O(1) | O(1) |

### Heaps

A *heap* is a tree of elements where each node is always smaller (min-heap) or larger (max-heap) than its children

Most built-in implementations are of a binary tree

| Operation | Time Complexity |
| --------- | --------------- |
| Access Root | O(1) |
| Update | O(log n) |
| Insert | O(log n) |
| Remove Root | O(log n) |
| Build | O(n) |

[Python's `heapq`](https://docs.python.org/3/library/heapq.html) & [Java's `PriorityQueue`](https://docs.oracle.com/javase/8/docs/api/java/util/PriorityQueue.html) are min binary heaps

# <a id="binary_search"></a> Binary Search

[Reference Link](https://www.topcoder.com/community/competitive-programming/tutorials/binary-search) <br/>
[Practice Problem](https://codeforces.com/edu/course/2/lesson/6/1/practice/contest/283911/problem/A)

Binary search is used to find a target value in a ***monotonic*** dataset by repeatedly *HALVING* the search interval, while ternary search divides the interval into *THREE* parts to find the min or max in ***unimodal*** functions.

Only works if the ordered data is either constantly increasing or decreasing (non-changing is fine too). <br/>
If the condition is viewed as a boolean return and the data looks like this (FFFFFFFTTTTTTT), then binary will work.

```python
def binary_search():
    lo = min_possible_val - 1
    hi = max_possible_val + 1

    while lo != hi - 1:  # lo and hi will converge until they are next to each other
        mid = lo + (hi - lo) // 2  # same as (lo + hi) // 2, but prevents integer overflow

        if f(mid) == True:
            hi = mid  # can also set this to lo based off of needs
        else:
            lo = mid

    return lo  # return lo or hi based off of needs
```

Time complexity - O(log n)

### Calculating `mid`

Proving that `(lo + hi) // 2 == lo + (hi - lo) // 2`

![](../img/binsearch_int_overflow.png)

### Indexing

If `hi != lo`, then there will always be a point in the search where `lo == hi - 1`

For most cases, you never want `lo = 0` and `hi = n - 1` because if `n = 1` then `0 == n - 1`

### Built-In Libraries

Python's `bisect` are functions used to find insertion points in a sorted list
- If the element already exists in the list:
    - `bisect_left` returns index of the *FIRST* occurrence of the element
    - `bisect_right` returns index of the *LAST* occurrence of the element
    - Otherwise `bisect_left` and `bisect_right` return the same index

## Sample Problems

### <a id="binary_search_lis"></a> Longest Increasing Subsequence (LIS)

Given an array, return the length of the longest increasing subsequence.

```python
def lengthOfLis(nums):
    sequence = []

    for num in nums:
        lo, hi = -1, len(sequence)

        while lo + 1 != hi:
            mid = lo + (hi - lo) // 2
            if sequence[mid] < num:
                lo = mid
            else:
                hi = mid

        if hi == len(sequence):
            sequence.append(num)
        else:
            sequence[hi] = num

    return len(sequence)
```

This approach can also be modified to return the subsequence itself.

Time complexity - O(n * log n)  
Space complexity - O(n)

## <a id="ternary_search"></a> Ternary Search

Binary search, but with three pointers instead of two


# <a id="topological_sort"></a> Topological Sort

Practice:  
[LeetCode | Course Schedule II](https://leetcode.com/problems/course-schedule-ii)  
[NeetCode | Foreign Dictionary](https://neetcode.io/problems/foreign-dictionary)

Topological sort is a linear ordering of vertices in a directed acyclic graph (DAG) such that for every edge `u -> v`, `u` appears before `v` in the ordering.

Mainly used for detecting cycles in a DAG

### Sample Problem: Detect Cycle in a Directed Graph

Input:  
`n` -> number of nodes  
`edges` -> a list of edges that make up the graph

Output:  
A boolean indicating if a cycle exists  
A list representing a valid topological order

#### BFS Approach (Kahn's Algorithm)

This approach is ***more popular*** and arguably ***easier*** to implement.

```python
def topSortKahn(n, edges):
    # Step 1: Create the adjacency list and in-degree array
    children = [[] for _ in range(n)]
    inDegree = [0] * n

    for u, v in edges:
        children[u].append(v)
        inDegree[v] += 1

    # Step 2: Initialize the queue with nodes having in-degree of 0
    queue = [i for i in range(n) if inDegree[i] == 0]

    # Step 3: Traverse graph topologically
    for node in queue:        
        for child in children[node]:
            inDegree[child] -= 1
            if inDegree[child] == 0:
                queue.append(child)

    # Step 4: Check if the topological sort includes all nodes
    if len(queue) == n:
        return False, queue  # No cycle detected, return the topological order
    else:
        return True, []  # Cycle detected, return an empty list
```

#### DFS Approach

Note that the topological order does not need to be generated for DFS to detect a cycle.

```python
def topSortDfs(n, edges):
    # Step 1: Create an adjacency list
    children = [[] for _ in range(n)]

    for u, v in edges:
        children[u].append(v)
    
    # Step 2: Initialize visited and recursion stack
    visited = [False] * n
    recStack = [False] * n
    topOrder = []
    
    def dfs(node):
        if recStack[node]:
            return True  # Cycle detected
        if visited[node]:
            return False  # Node already processed
        
        visited[node] = True
        recStack[node] = True
        
        for child in children[node]:
            if dfs(child):
                return True
        
        recStack[node] = False
        topOrder.append(node)
        return False
    
    # Step 3: Check for cycles and build the topological order
    for node in range(n):
        if not visited[node]:
            if dfs(node):
                return True, []  # Cycle detected, return empty topological order
    
    return False, topOrder[::-1]  # No cycle detected, return reversed topological order
```

Time complexity - O(Vertices + Edges)  
Space complexity - O(Vertices + Edges)


# <a id="dijkstras"></a> Dijkstra's Algorithm

Dijkstra's algorithm finds the shortest path from starting node(s) to all other nodes in a NON-NEGATIVE weighted graph.

Similarities to BFS:
1. BFS finds shortest path in an *unweighted graph*, Dijkstra's finds shortest path in a *weighted graph*
2. BFS uses a *queue*, Dijkstra's uses a *min heap*

Nodes with shortest path get pushed to the front of the line.  
Nodes with longest path get pushed to the back of the line.

### Sample Problem: Find Shortest Path in Weighted Graph

Given a weighted graph, find the shortest path from the start node to the end node

Input:  
`n` -> number of nodes  
`edges` -> a list of edges and their weights that make up the graph  
`start` -> start node  
`end` -> end node

Output:  
Length of the shortest path

```python
def dijkstra(n, edges, start, end):
    neighbors = [[] for _ in range(n)]
    heap = [(0, start)]
    distances = [float("inf")] * n

    # Create adjacency list
    for node1, node2, weight in edges:
        neighbors[node1].append((node2, weight))
        neighbors[node2].append((node1, weight))

    distances[start] = 0

    while len(heap) != 0:
        dist, node = heapq.heappop(heap)

        if node == end:
            return dist

        # Shorter path found, terminate curr path
        if dist > distances[node]:
            continue

        for neighbor, weight in neighbors[node]:
            newDist = dist + weight

            if newDist < distances[neighbor]:
                distances[neighbor] = newDist
                heapq.heappush(heap, (newDist, neighbor))

    return -1  # No path found
```

With V = vertices and E = edges

Time Complexity - O((E + V) log V)  
Space Complexity - O(V + E)

For sparse graphs, where (E) is close to (V), time complexity is approx O(V log V)  
For dense graphs, where (E) approaches (V^2), complexity becomes O(V^2 log V)


## <a id="0-1_bfs"></a> 0-1 BFS

Practice:  
[LeetCode | Minimum Cost to Make at Least One Valid Path in a Grid](https://leetcode.com/problems/minimum-cost-to-make-at-least-one-valid-path-in-a-grid)

***NOTE: Any 0-1 BFS problem can also be solved with Dijkstra's, but 0-1 BFS is slightly faster***

0-1 BFS finds the shortest path from starting node(s) to all other nodes in a 0-1 weighted graph (edges have weights of either 0 or 1).

BFS uses a *queue*, 0-1 BFS uses a *deque*.

0-edge traversals get pushed to the front of the line.  
1-edge traversals get pushed to the back of the line.

### Sample Problem: Find Shortest Path in 0-1 Weighted Graph

Given a 0-1 weighted graph, find the shortest path from the start node to the end node

Input:  
`graph` -> list of neighbors and edge weight (either 0 or 1) for each node in the graph  
`start` -> start node  
`end` -> end node

```python
def bfs01(graph, start, end):
    n = len(graph)
    dq = deque([(0, start)])
    distances = [float("inf")] * n

    distances[start] = 0

    while len(dq) != 0:
        dist, node = dq.pop()

        if node == end:
            break
        elif dist > distances[node]:
            continue

        for neighbor, weight in graph[node]:
            newDist = dist + weight

            if newDist < distances[neighbor]:
                distances[neighbor] = newDist

                # 0-edge traversals get processed earlier
                if weight == 0:
                    dq.append((newDist, neighbor))
                else:
                    dq.appendleft((newDist, neighbor))

    return distances[end]  # INF if no path found
```

With V = vertices and E = edges

Time Complexity - O(V + E)  
Space Complexity - O(V + E)


# <a id="dynamic_programming"></a> Dynamic Programming (Memoization)

Saving values so you don't need to recalculate them  
DP is a form of **caching**

To solve a DP problem, all you need to know is the **state** and **transition**:
- state: the set of properties that *IDs* the value you are storing
- transition: how to calculate the value from previously saved values

## Popular Problems

### <a id="dp_knapsack"></a> Knapsack

Given a knapsack and an array of items with weights, determine if you can fill the knapsack completely (each item can only be chosen once).

```python
def knapsack(items, maxSize):
    n = len(items)
    dp = [0] * (maxSize + 1)
    
    dp[0] = 1
    for i in range(n):
        for j in range(maxSize, items[i]-1, -1):
            dp[j] |= dp[j - items[i]]  # bitwise OR

    return dp[maxSize]
```

Time complexity - O(n\*m) where n is item length, m is maxSize <br/>
Space complexity - O(m)

NOTE: If items can be chosen multiple times, then flip the direction of the second loop.


# <a id="union_find"></a> Union Find (Disjoint Set)

Groups elements together and finds which element belongs to what group.

```python
n = len(some_array)
parent = [i for i in range(n)]  # all elements initially in their own group

def union(x, y):
    parent[find(x)] = find(y)

def find(x):
    if parent[x] != x: parent[x] = find(parent[x])  # finds the root and compresses the branch
    return parent[x]
```


# <a id="segment_tree"></a> Segment Tree

[Practice Problem](https://codeforces.com/edu/course/2/lesson/4/1/practice/contest/273169/problem/A)

What is it? _It's a tree of segments dumbasssss_

Great for range queries

Say this is your array: `[3, 1, 2, 5, 6, 8, 3, 2]`

Then this would be your segment tree of sums:

![](../img/seg_tree.png)

The total number of nodes will always be to the power of 2 b/c it's a binary tree <br/>
If the original length of the array is not a power of 2, just pad the tree with zeros

There are different implementations. This is the most readable:

```python
segtree_n = 2 ** 17  # usually this amt of nodes is enough
segtree = [0] * 2 * segtree_n

def set(i, v, x=0, lo=0, hi=segtree_n):
    if hi - lo == 1:  # reached the bottom
        segtree[x] = v;
        return

    mid = (lo + hi) // 2
    if i < mid:
        set(i, v, 2*x+1, lo, mid)
    else:
        set(i, v, 2*x+2, mid, hi)

    segtree[x] = segtree[2*x+1] + segtree[2*x+2]  # operation changes based off needs


def get(target_lo, target_hi, x=0, lo=0, hi=segtree_n):
    if target_lo >= hi or target_hi <= lo: return 0  # range is out of bounds
    if target_lo <= lo and target_hi >= hi: return segtree[x]  # range is in bounds

    mid = (lo + hi) // 2  # range is partially in bounds
    a = get(target_lo, target_hi, 2*x+1, lo, mid)
    b = get(target_lo, target_hi, 2*x+2, mid, hi)

    return a + b  # again, operation changes
```

Setting/updating a value takes O(log n) time <br/>
Getting a segment takes O(log n) time

## Lazy Propagation

Sometimes you don't just want to update one value at a time. Sometimes you want to update a _range_ of values.

w/o lazy prop it'll take O(nlog n) time. _TOO SLOW!!!_ w/ lazy prop it'll take O(log n)


# <a id="trie"></a> Trie (Prefix Tree)

[Practice Problem](https://leetcode.com/problems/implement-trie-prefix-tree/)

It is called a trie b/c it's a re***TRIE***val data structure

What is it? _A tree where each node builds its value on top of its parent. Hence the alt name PREFIX tree._

Often used to store strings (words), but not limited to it.

<img src="../img/trie.png" width="400">

***NOTE: your chars are your EDGE VALUES, NOT your node values***

Can't a hash map do the same thing? _Hash maps can't search efficiently based off prefix. What if I wanted all words beginning in 'inter-'?_

### Sample Problem: Word Autocomplete

Given a list of words and a list of prefixes, return a list of words that complete each prefix.

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.isWord = False
        self.word = None  # Optional, for easy retrieval


class Trie:
    def __init__(self):
        self.root = TrieNode()


    def insert(self, word):
        node = self.root

        for ch in word:
            if ch not in node.children:
                node.children[ch] = TrieNode()
            node = node.children[ch]

        node.isWord = True
        node.word = word  # Optional        


    def startsWith(self, prefix):
        node = self.root

        for ch in prefix:
            if ch not in node.children:
                return []
            node = node.children[ch]

        return self.findAll(node)


    # BFS and DFS both work
    def findAll(self, start=None):
        if start == None:
            start = self.root

        queue = [start]
        result = []

        for node in queue:
            if node.isWord:
                # Easy retrieval
                # Can be substituted w/ DFS & backtracking
                result.append(node.word)

            for child in node.children.values():
                queue.append(child)

        return result
```

With N = number of words, L = average length of words, k = alphabet size

Space complexity is O(N * L * k)  
For the English alphabet that means O(N * L * 26)

Inserting a word takes O(L) time  
Searching if a word is in the trie takes O(L) time  
Traversing the entire tree takes O(N * L * 26) time


# <a id="bit_manipulation"></a> Bit Manipulation

Both AND (`&`) and OR (`|`) are destructive, but XOR (`^`) and NOT (`~`) are reversible.
