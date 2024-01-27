
1. ### [[Arrays]]:
	- **Importance:** Arrays are fundamental, providing efficient indexing for accessing elements and enabling constant-time access based on an index.
	- **Time Complexities:**
	    - Insertion: O(n) for inserting an element at an arbitrary position.
	    - Searching: O(n) for linear search (unsorted), O(log n) for binary search (sorted).
	    - Deletion: O(n) for deleting an element at an arbitrary position.
	    - Sorting: O(n log n) for efficient sorting algorithms like [[Quick Sort|quicksort]] or [[Merge Sort|mergesort]].
1. ### [[Linked List]]
    
    - **Importance:** Linked lists allow for dynamic memory allocation and efficient insertion and deletion at the expense of sequential access.
    - **Time Complexities:**
        - Insertion: O(1) for inserting at the head or tail, O(n) for arbitrary position.
        - Searching: O(n) for linear search.
        - Deletion: O(1) for deletion at the head or tail, O(n) for arbitrary position.
        - Sorting: Typically not performed directly on linked lists.
2. ### [[Stack]]
    
    - **Importance:** Stacks follow the Last-In-First-Out (LIFO) principle, essential for algorithms and data management like function call stacks and expression evaluation.
    - **Time Complexities:**
        - Insertion (Push): O(1).
        - Searching: O(n) as it's typically not used for searching.
        - Deletion (Pop): O(1).
3. ### **[[Queue]]:**
    
    - **Importance:** Queues follow the First-In-First-Out (FIFO) principle and are vital for various applications like job scheduling and handling data in a sequential manner.
    - **Time Complexities:**
        - Enqueue: O(1).
        - Dequeue: O(1).
        - Searching: O(n) as it's typically not used for searching.
1. ### **[[Trees]]:**
    
    - **Importance:** Trees are versatile hierarchical structures used in various applications like file systems, databases, and efficient searching and sorting.
    - **Time Complexities:**
        - Insertion: O(log n) for balanced trees (e.g., [[AVL Tree|AVL]], [[Red-Black Tree|Red-Black]]).
        - Searching: O(log n) for balanced trees.
        - Deletion: O(log n) for balanced trees.
        - Sorting: O(n log n) for tree-based sorting algorithms (e.g., [[Heap Sort|heapsort]]).
2. ### **[[Graphs]]:**
    
    - **Importance:** Graphs model relationships and connections between data points, crucial for various real-world scenarios like network routing and social network analysis.
    - **Time Complexities:**
        - Vary greatly based on the graph representation and specific algorithms (e.g., depth-first search, breadth-first search).
3. ### **[[Hash Table]]:**
    
    - **Importance:** Hash tables provide fast data retrieval and are essential for implementing dictionaries, caches, and efficient searching.
    - **Time Complexities:**
        - Average case: O(1) for insertion, searching, and deletion (with a good hash function).
4. ### **[[Heap]]:**
    
    - **Importance:** Heaps are crucial for priority queues and efficient implementations of various algorithms like heap sort and Dijkstra's algorithm.
    - **Time Complexities:**
        - Insertion: O(log n).
        - Extraction (e.g., extract-min): O(log n).
1. ### **[[Tries]]:**
    
    - **Importance:** Tries are efficient for string-related operations and are used in applications like search engines and auto-complete features.
    - **Time Complexities:**
        - Insertion: O(m), where m is the length of the key.
        - Searching: O(m), where m is the length of the key.
2. ### **[[Hash Maps]]:**
    
    - **Importance:** Hash maps offer efficient key-value pair storage and retrieval using hash functions, essential for implementing associative arrays and dictionaries.
    - **Time Complexities:**
        - Average case: O(1) for insertion, searching, and deletion (with a good hash function).
3. ### [[Disjoint-Set|Disjoint-Set (Union-Find)]]
    
    - **Importance:** Disjoint-set data structures efficiently manage partitioning a set into disjoint subsets, crucial for various applications like image segmentation and Kruskal's algorithm.
    - **Time Complexities:**
        - Amortized O(α(n)), where α(n) is the inverse Ackermann function (very close to O(1) in practice).

