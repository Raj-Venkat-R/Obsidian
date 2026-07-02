---
topic: Tree (General)
category: data-structure
structure: Tree (General)
data: general
mutability: mutable
access: varies
priority: medium
difficulty: medium
status: 🔲 not started
used_in: []
tags: [data-structure, non-linear--trees]
---

# Tree (General)

*← [[Circular Queue]] | [[Binary Tree]] →*

---

## 1. Overview

> A **Tree** is a **non-linear hierarchical data structure** consisting of **nodes** connected by **edges**. It starts from a single **root node**, and every node (except the root) has exactly one **parent** and zero or more **children**. A tree contains **no cycles**, is always **connected**, and there is **exactly one unique path** between any two nodes.

**Category:** Non-Linear Data Structure

---

## 2. Core Concept

A tree organizes data in a **hierarchical structure**, where information flows from a single **root** to multiple **child nodes**. Unlike linear data structures (arrays or linked lists), a tree allows a node to branch into multiple paths, making it suitable for representing hierarchical relationships.

Each node is connected through **parent-child relationships**, and every node (except the root) has **exactly one parent**. A tree contains **no cycles**, ensuring there is **exactly one unique path** between any two nodes.

The fundamental idea behind a tree is to represent data in a way that supports **hierarchical organization**, **efficient searching**, **recursive processing**, and **divide-and-conquer algorithms**.

### Core Mental Model

Think of a tree as an upside-down family tree.

- The **root** is the starting point.

- Every node can have one or more **children**.

- Information flows from **parent → child**.

- Each branch represents a different path.

- Traversing the tree means visiting nodes in a specific order.

Unlike arrays, where elements are arranged sequentially, a tree allows data to branch into multiple directions, making it ideal for representing structures such as file systems, company hierarchies, HTML DOM, decision trees, and Binary Search Trees.

---

## 3. Structure & Internals

A tree is **not stored as a continuous block of memory** like an array.

Instead, it is made up of **nodes**, where each node is an individual object stored anywhere in memory. Nodes are connected using **references (pointers)**, forming the tree structure.

---

### Structure of a Node

A tree node generally consists of:

- **Data** → stores the value of the node.
- **References (Pointers)** → stores the address of its child nodes.

For a general tree:

```text
+----------------------+
| Data | Child Links   |
+----------------------+
```

For a binary tree:

```text
+---------------------------+
| Data | Left | Right       |
+---------------------------+
```

---

### Binary Tree Node in Java

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
    }
}
```

Memory representation:

```text
           +----------------------+
root ----> | val = 10             |
           | left  ----------+    |
           | right -----+    |    |
           +------------|----|----+
                        |    |
                        |    |
                        v    v

          +----------------+     +----------------+
          | val = 5        |     | val = 15       |
          | left = null    |     | left = null    |
          | right = null   |     | right = null   |
          +----------------+     +----------------+
```

The variables `left` and `right` do **not store the child node itself**.

They store the **reference (memory address)** of another `TreeNode` object.

---

### How Nodes Are Connected

Example:

```java
TreeNode root = new TreeNode(1);
root.left = new TreeNode(2);
root.right = new TreeNode(3);
```

Logical structure:

```text
        1
       / \
      2   3
```

Memory view:

```text
root
 │
 ▼
+----------------------+
| val = 1              |
| left  -----------+   |
| right ------+    |   |
+-------------|----|---+
              |    |
              |    |
              ▼    ▼
        +---------+   +---------+
        | val = 2 |   | val = 3 |
        | left    |   | left    |
        | right   |   | right   |
        +---------+   +---------+
```

---

### Why References Are Used

Using references allows a tree to:

- Grow dynamically.
- Allocate memory only when a new node is created.
- Connect nodes without requiring contiguous memory.
- Easily add or remove nodes.

---

### Tree vs Array Memory

**Array**

```text
Index:  0   1   2   3   4

Memory:
+---+---+---+---+---+
|10 |20 |30 |40 |50 |
+---+---+---+---+---+

Stored in contiguous memory.
```

---

**Tree**

```text
Memory

0x100  -> Node(10)
0x450  -> Node(5)
0x890  -> Node(15)

Nodes may be stored anywhere.

Connections are maintained using references.
```

Unlike arrays, tree nodes **do not need to be adjacent in memory**.

---

### Key Takeaways

- A tree is made up of **nodes** connected by **references**.
- Every node is an independent object in memory.
- Trees use **dynamic memory allocation**.
- Tree nodes are **not stored contiguously**.
- The `left` and `right` variables store **references (addresses)**, not the child nodes themselves.

---

## 4. Operations & Complexity

| Operation | Time Complexity | Space Complexity | Notes |
|------------|-----------------|------------------|-------|
| Create Root | O(1) | O(1) | Create the first node of the tree. |
| Insert Node | O(h) | O(1) | Depends on tree height. Different tree types have different insertion rules. |
| Delete Node | O(h) | O(1) | Searching for the node takes O(h). Deletion logic depends on the tree type. |
| Search Node | O(h) | O(1) | Search follows the tree from root to the target node. |
| Access Root | O(1) | O(1) | Root node is directly accessible. |
| DFS Traversal (Preorder, Inorder, Postorder) | O(n) | O(h) | Every node is visited exactly once. Recursive stack uses O(h) space. |
| BFS Traversal (Level Order) | O(n) | O(w) | Uses a queue. `w` is the maximum width of the tree. |
| Find Height | O(n) | O(h) | Every node may need to be visited. |
| Count Nodes | O(n) | O(h) | Visits every node once. |
| Count Leaf Nodes | O(n) | O(h) | Visits every node once. |

---

### Complexity Terms

- **n** = Number of nodes in the tree
- **h** = Height of the tree
- **w** = Maximum width (maximum number of nodes present at any level)

---

### Best vs Worst Case

For a **balanced tree**:

- Height = **O(log n)**
- Search = **O(log n)**
- Insert = **O(log n)**
- Delete = **O(log n)**

Example:

```text
        8
      /   \
     4     12
    / \   /  \
   2  6 10  14
```

---

For a **skewed tree**:

- Height = **O(n)**
- Search = **O(n)**
- Insert = **O(n)**
- Delete = **O(n)**

Example:

```text
1
 \
  2
   \
    3
     \
      4
```

---

### Key Observations

- Tree operations depend on the **height** of the tree, not directly on the number of nodes.
- Traversals always visit every node, so their time complexity is **O(n)**.
- A balanced tree is much more efficient than a skewed tree.
- The recursion stack during DFS uses **O(h)** auxiliary space.


---

## 5. When to Use

Use a tree when the data naturally forms a **hierarchical relationship** or when efficient searching, organization, and traversal are required.

Common situations include:

- Representing hierarchical data
  - File systems (folders and files)
  - Company organizational charts
  - Family trees

- Fast searching and retrieval
  - Binary Search Tree (BST)
  - AVL Tree
  - B-Tree

- Expression evaluation
  - Expression Trees
  - Syntax Trees used by compilers

- Database indexing
  - B-Tree
  - B+ Tree

- Auto-complete and dictionaries
  - Trie (Prefix Tree)

- Priority-based scheduling
  - Heap

- Network routing and shortest path algorithms
  - Spanning Trees
  - Routing Trees

- Decision making and Artificial Intelligence
  - Decision Trees
  - Game Trees

- HTML and XML parsing
  - DOM (Document Object Model)

- Graph algorithms
  - DFS
  - BFS

---

### Problem Signals

A tree is usually the right choice when the problem involves:

- Parent-child relationships
- Hierarchical data
- Recursive structures
- Searching from a root node
- Traversing nodes in different orders (DFS/BFS)
- Breaking a large problem into smaller subproblems

---

### Advantages

- Efficient hierarchical organization
- Supports recursive algorithms naturally
- Faster searching in balanced trees
- Dynamic size (nodes can be added or removed easily)
- Multiple traversal techniques (Preorder, Inorder, Postorder, Level Order)

---

### Trade-offs

- More memory is required because each node stores references.
- Implementation is more complex than arrays or linked lists.
- Performance depends on the height of the tree.
- A skewed tree can degrade search performance to **O(n)**.
---

## 6. When NOT to Use

A tree is not always the best choice. Consider other data structures when the problem does not involve hierarchical relationships or when a simpler structure provides better performance.

### Do NOT use a tree when:

- Data is sequential and accessed by index.
  - Use an **Array** instead.

- Frequent random access is required.
  - Arrays provide **O(1)** indexing, whereas trees require traversal.

- Only linear traversal is needed.
  - Use a **Linked List**.

- The problem requires only LIFO operations.
  - Use a **Stack**.

- The problem requires only FIFO operations.
  - Use a **Queue**.

- Data is frequently searched using exact keys.
  - Use a **HashMap** or **HashSet**, which provide average **O(1)** lookup.

- Data has no hierarchical relationship.
  - A tree adds unnecessary complexity.

- Memory usage is a major concern.
  - Every tree node stores additional references (child pointers), increasing memory overhead.

- The tree is likely to become highly skewed.
  - Operations may degrade to **O(n)**.
  - Consider balanced trees such as **AVL Tree** or **Red-Black Tree** instead.

---

### Better Alternatives

| Requirement | Better Data Structure |
|-------------|----------------------|
| Fast random access | Array |
| Sequential processing | Linked List |
| LIFO operations | Stack |
| FIFO operations | Queue |
| Fast key lookup | HashMap / HashSet |
| Ordered collection with indexing | ArrayList |
| Priority-based processing | Heap (Priority Queue) |

---

### Key Takeaways

- Do not use a tree if there is **no hierarchical relationship**.
- Arrays are better for **index-based access**.
- HashMaps are better for **fast key-value lookups**.
- Trees are powerful, but they introduce additional memory usage and implementation complexity.
- Choose a tree only when its hierarchical structure or traversal capabilities provide a clear advantage.

---

## 7. Types / Variants

Trees are classified based on their structure, balancing technique, or purpose.

---

### 1. General Tree

A tree where a node can have **any number of children**.

Example:

```text
        A
      / | \
     B  C  D
       / \
      E   F
```

Use Cases:
- File systems
- Organization charts
- XML/HTML DOM

---

### 2. Binary Tree

A tree where every node has **at most two children**.

Children are called:
- Left Child
- Right Child

Example:

```text
        1
       / \
      2   3
     /
    4
```

This is the foundation for many advanced tree structures.

---

### 3. Binary Search Tree (BST)

A special type of Binary Tree where:

- Left subtree contains smaller values
- Right subtree contains larger values

Example:

```text
        8
       / \
      4   12
     / \   \
    2   6   15
```

Provides efficient searching when balanced.

---

### 4. Balanced Binary Tree

A Binary Tree where the height difference between left and right subtrees remains small.

Examples:
- AVL Tree
- Red-Black Tree

Purpose:
- Prevents the tree from becoming skewed.
- Keeps operations close to **O(log n)**.

---

### 5. AVL Tree

A self-balancing Binary Search Tree.

Property:

```
|Height(Left) - Height(Right)| ≤ 1
```

Whenever the tree becomes unbalanced, rotations are performed.

---

### 6. Red-Black Tree

A self-balancing Binary Search Tree that uses node colors (Red and Black) to maintain balance.

Used in:
- Java TreeMap
- Java TreeSet

---

### 7. Heap

A complete Binary Tree used for priority-based processing.

Types:

- Min Heap
- Max Heap

Applications:
- Priority Queue
- Heap Sort
- Scheduling

---

### 8. Trie (Prefix Tree)

Stores strings character by character.

Applications:
- Auto-complete
- Spell checker
- Dictionary search
- Prefix matching

---

### 9. Segment Tree

A Binary Tree used for efficient range queries.

Applications:
- Range Sum
- Range Minimum
- Range Maximum

Supports updates efficiently.

---

### 10. Fenwick Tree (Binary Indexed Tree)

A space-efficient alternative to Segment Tree.

Applications:
- Prefix Sum
- Range Sum Queries
- Frequency Counting

---

### 11. B-Tree

A multi-way search tree designed for storage systems.

Applications:
- Databases
- File Systems

Allows multiple keys per node.

---

### 12. B+ Tree

An extension of B-Tree.

Applications:
- Database indexing
- File systems

Leaf nodes are linked together for faster range queries.

---

### 13. N-ary Tree

A tree where each node can have at most **N children**.

Example (3-ary Tree):

```text
         A
      /  |  \
     B   C   D
```

General Tree is a special case of an N-ary Tree.

---

## Summary

| Tree Type | Maximum Children | Main Purpose |
|-----------|------------------|--------------|
| General Tree | Unlimited | Hierarchical data |
| Binary Tree | 2 | Foundation for tree algorithms |
| Binary Search Tree | 2 | Efficient searching |
| AVL Tree | 2 | Self-balancing BST |
| Red-Black Tree | 2 | Self-balancing BST |
| Heap | 2 | Priority processing |
| Trie | Variable | String and prefix searching |
| Segment Tree | 2 | Range queries |
| Fenwick Tree | 2 | Prefix and range sums |
| B-Tree | Multiple | Database indexing |
| B+ Tree | Multiple | Efficient database storage |
| N-ary Tree | N | General hierarchical structures |

---

### Learning Order

Study these trees in the following order:

1. General Tree
2. Binary Tree
3. Binary Search Tree (BST)
4. Heap
5. AVL Tree
6. Red-Black Tree
7. Trie
8. Segment Tree
9. Fenwick Tree
10. B-Tree
11. B+ Tree

---

## 8. Java Implementation

```java
public class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    Tree(int val){
        this.val = val;
    }

    public static void main(String[] args) {
        Tree root = new Tree(5);
        Tree node1 = new Tree(4);
        Tree node2 = new Tree(6);
        root.left = node1;
        root.right = node2;
    }
}


```

---

## 9. Built-in Java Equivalent

*(Does Java standard library have this? What class? Key methods?)*

---

## 10. Common Patterns & Tricks

*(Clever uses, interview patterns, edge cases)*

---

## 11. Related

*(Wiki links to related structures, algorithms that use this)*

---

*← [[Circular Queue]] | [[Binary Tree]] →*
*← [[Data Structures Index]] | [[DSA Index]]*
