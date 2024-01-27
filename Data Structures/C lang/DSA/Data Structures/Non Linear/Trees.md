# Terminology
1. ### **Node:**
    
    - A fundamental building block of a tree that holds data and links to other nodes, typically representing an entity in the tree.

1. ### **Root:**
    
    - The topmost node in a tree hierarchy, serving as the entry point into the tree. A tree has only one root.
3. ### **Parent Node:**
    
    - A node that has one or more child nodes connected to it in a tree structure.
4. ### **Child Node:**
    
    - A node directly connected to another node (parent node) in the tree below it.
5. ### **Leaf Node (Terminal Node):**
    
    - A node in a tree that does not have any children, i.e., a node with zero out-degree.
6. ### **Internal Node (Non-leaf Node):**
    
    - A node in a tree that has at least one child, i.e., a node with a non-zero out-degree.
7. ### **Sibling Nodes:**
    
    - Nodes that share the same parent in a tree, forming a group of nodes at the same level.
8. ### **Depth of a Node:**
    
    - The distance from the root to a particular node, typically measured by the number of edges along the path.
9. ### **Height of a Node:**
    
    - The number of edges on the longest path from the node to a leaf node in the subtree rooted at the node.
10. ### **Depth of a Tree:**
    
    - The maximum depth among all nodes in the tree, indicating the longest path from the root to a leaf.
11. ### **Height of a Tree:**
    
    - The maximum height among all nodes in the tree, indicating the longest path from the root to a leaf.
12. ### **Subtree:**
    
    - A tree formed by a node and all its descendants, i.e., nodes reachable from that node.
13. ### **Degree of a Node:**
    
    - The number of children a node has. For binary trees, the degree is at most two.
# Traversal:
### **Traversal:**
    
- The process of visiting and processing each node in a tree, usually categorized into different types such as in-order, pre-order, post-order, and level-order traversal.
### **Traversal Order:**
    
- The order in which nodes are visited during a traversal, determining the sequence of node processing.
### **Pre-order Traversal:**
    
- Traversing a tree by visiting the root, then the left subtree, and finally the right subtree.
  ```c
  void preorder(TreeNode* root) {
    if (root == NULL)
        return;

    printf("%d ", root->data);
    preorder(root->left);
    preorder(root->right);
}
  
  ```
### **Post-order Traversal:**
    
- Traversing a tree by visiting the left subtree, then the right subtree, and finally the root.
```c
void postorder(TreeNode* root) {
    if (root == NULL)
        return;

    postorder(root->left);
    postorder(root->right);
    printf("%d ", root->data);
}

```
### **Level-order Traversal:**
    
- Traversing a tree level by level, starting from the root and moving to the next level from left to right.
```c
void levelorder(TreeNode* root) {
    if (root == NULL)
        return;

    Queue* queue = createQueue();
    enqueue(queue, root);

    while (queue->front != NULL) {
        TreeNode* current = dequeue(queue);
        printf("%d ", current->data);

        if (current->left != NULL)
            enqueue(queue, current->left);

        if (current->right != NULL)
            enqueue(queue, current->right);
    }

    free(queue);
}

```
### **In-order Traversal**
- Traversing a tree by visiting the left subtree, then the root, and finally the right subtree.
    
```c
void inorder(TreeNode* root) {
    if (root == NULL)
        return;

    inorder(root->left);
    printf("%d ", root->data);
    inorder(root->right);
}

```



# Types
1. [[Binary Tree]]
2. [[Binary Search Tree]]
3. [[Balanced Binary Tree]]
4. [[AVL Tree]]
5. [[Red-Black Tree]]
6. [[B-Tree]]
7. [[Trie]](Prefix Tree)
8. [[Heap]]
9. [[N-ary Tree]]
10. [[Quadtree]]
11. [[Octree]]
12. [[Ternary Search Tree]]