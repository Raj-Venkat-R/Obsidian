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

*(What makes another structure better here?)*

---

## 7. Types / Variants

*(Subtypes, special cases, related variants)*

---

## 8. Java Implementation

```java
// Fill when studying
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
