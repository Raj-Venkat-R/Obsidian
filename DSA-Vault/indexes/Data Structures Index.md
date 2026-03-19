---
type: index
title: Data Structures Index
category: data-structures
status: active
tags: [index, data-structures]
---

# 🧱 Data Structures Index

> All data structures organized by category and learning order.  
> Each entry is a wiki link to its own note. Check off as you complete them.

*← Back to [[DSA Index]]*

---

## How to Read This Index

- ✅ Checked = studied and notes filled
- 🔁 Ordered = follow top-to-bottom within each section for the best learning path
- Complexity columns show **average-case** unless noted

---

## 1. Linear — Array-Based

> Data stored in contiguous memory. Index-based access. Foundation of most structures.

| # | Structure | Access | Insert | Delete | Space | Note |
|---|---|---|---|---|---|---|
| 1 | [[Array]] | O(1) | O(n) | O(n) | O(n) | Foundation |
| 2 | [[Dynamic Array]] | O(1) | O(1)* | O(n) | O(n) | Amortized insert |
| 3 | [[Prefix Sum Array]] | O(1) | O(n) | O(n) | O(n) | Range query trick |
| 4 | [[Difference Array]] | O(1) | O(1) | O(1) | O(n) | Range update trick |
| 5 | [[Sparse Array]] | O(1) | O(1) | O(1) | O(k) | For sparse data |
| 6 | [[Frequency Array]] | O(1) | O(1) | O(1) | O(k) | Count occurrences |
| 7 | [[Circular Array]] | O(1) | O(1) | O(1) | O(n) | Fixed-size ring |
| 8 | [[Bitset]] | O(1) | O(1) | O(1) | O(n/w) | Compact bool array |

### Checklist
- [ ] [[Array]]
- [ ] [[Dynamic Array]]
- [ ] [[Prefix Sum Array]]
- [ ] [[Difference Array]]
- [ ] [[Sparse Array]]
- [ ] [[Frequency Array]]
- [ ] [[Circular Array]]
- [ ] [[Bitset]]

---

## 2. Linear — Linked

> Data stored in nodes with pointers. Dynamic size, non-contiguous memory.

| # | Structure | Access | Insert (head) | Delete | Space |
|---|---|---|---|---|---|
| 1 | [[Singly Linked List]] | O(n) | O(1) | O(n) | O(n) |
| 2 | [[Doubly Linked List]] | O(n) | O(1) | O(1)* | O(n) |
| 3 | [[Circular Linked List]] | O(n) | O(1) | O(n) | O(n) |
| 4 | [[Skip List]] | O(log n) | O(log n) | O(log n) | O(n log n) |

### Checklist
- [ ] [[Singly Linked List]]
- [ ] [[Doubly Linked List]]
- [ ] [[Circular Linked List]]
- [ ] [[Skip List]]

---

## 3. Linear — Stack & Queue Family

> Restricted-access linear structures. LIFO or FIFO discipline.

| # | Structure | Push/Enqueue | Pop/Dequeue | Peek | Space |
|---|---|---|---|---|---|
| 1 | [[Stack]] | O(1) | O(1) | O(1) | O(n) |
| 2 | [[Queue]] | O(1) | O(1) | O(1) | O(n) |
| 3 | [[Deque]] | O(1) | O(1) | O(1) | O(n) |
| 4 | [[Priority Queue]] | O(log n) | O(log n) | O(1) | O(n) |
| 5 | [[Monotonic Stack]] | O(1) amort | O(1) | O(1) | O(n) |
| 6 | [[Monotonic Queue]] | O(1) amort | O(1) | O(1) | O(n) |
| 7 | [[Circular Queue]] | O(1) | O(1) | O(1) | O(n) |

### Checklist
- [ ] [[Stack]]
- [ ] [[Queue]]
- [ ] [[Deque]]
- [ ] [[Priority Queue]]
- [ ] [[Monotonic Stack]]
- [ ] [[Monotonic Queue]]
- [ ] [[Circular Queue]]

---

## 4. Non-Linear — Trees

> Hierarchical structures. One root, parent-child relationships, no cycles.

### 4.1 Basic Trees

| # | Structure | Search | Insert | Delete | Space |
|---|---|---|---|---|---|
| 1 | [[Tree (General)]] | O(n) | O(1) | O(n) | O(n) |
| 2 | [[Binary Tree]] | O(n) | O(n) | O(n) | O(n) |
| 3 | [[Binary Search Tree]] | O(h) | O(h) | O(h) | O(n) |
| 4 | [[Threaded Binary Tree]] | O(n) | O(h) | O(h) | O(n) |

### 4.2 Self-Balancing Trees

> h = O(log n) guaranteed. BST but balanced.

| # | Structure | Search | Insert | Delete | Notes |
|---|---|---|---|---|---|
| 1 | [[AVL Tree]] | O(log n) | O(log n) | O(log n) | Strict balance |
| 2 | [[Red-Black Tree]] | O(log n) | O(log n) | O(log n) | Java TreeMap internals |
| 3 | [[Splay Tree]] | O(log n) amort | O(log n) amort | O(log n) amort | Self-adjusting |
| 4 | [[Treap]] | O(log n) | O(log n) | O(log n) | BST + Heap hybrid |

### 4.3 Multi-way & Disk Trees

| # | Structure | Search | Insert | Delete | Notes |
|---|---|---|---|---|---|
| 1 | [[B-Tree]] | O(log n) | O(log n) | O(log n) | DB indexes |
| 2 | [[B+ Tree]] | O(log n) | O(log n) | O(log n) | DB leaf chaining |
| 3 | [[2-3 Tree]] | O(log n) | O(log n) | O(log n) | B-Tree special case |

### 4.4 Heap Trees

| # | Structure | Insert | Extract-Min/Max | Peek | Notes |
|---|---|---|---|---|---|
| 1 | [[Binary Heap]] | O(log n) | O(log n) | O(1) | PQ backbone |
| 2 | [[Min Heap]] | O(log n) | O(log n) | O(1) | Smallest at root |
| 3 | [[Max Heap]] | O(log n) | O(log n) | O(1) | Largest at root |
| 4 | [[Fibonacci Heap]] | O(1) amort | O(log n) amort | O(1) | Dijkstra optimization |
| 5 | [[Binomial Heap]] | O(log n) | O(log n) | O(log n) | Mergeable heap |
| 6 | [[Leftist Heap]] | O(log n) | O(log n) | O(1) | Mergeable |

### 4.5 Segment & Specialized Trees

| # | Structure | Query | Update | Space | Notes |
|---|---|---|---|---|---|
| 1 | [[Segment Tree]] | O(log n) | O(log n) | O(n) | Range queries |
| 2 | [[Fenwick Tree]] | O(log n) | O(log n) | O(n) | Prefix sums (BIT) |
| 3 | [[Sparse Table]] | O(1) | O(n log n) build | O(n log n) | Static RMQ |
| 4 | [[Interval Tree]] | O(log n + k) | O(log n) | O(n) | Overlapping intervals |
| 5 | [[K-D Tree]] | O(log n) avg | O(log n) avg | O(n) | Multi-dim spatial |

### 4.6 Trie Family

| # | Structure | Search | Insert | Space | Notes |
|---|---|---|---|---|---|
| 1 | [[Trie]] | O(m) | O(m) | O(ALPHABET × n) | Prefix search |
| 2 | [[Compressed Trie]] | O(m) | O(m) | O(n) | Patricia / Radix |
| 3 | [[Suffix Tree]] | O(m) | O(n) build | O(n) | Pattern matching |
| 4 | [[Suffix Array]] | O(m log n) | O(n log n) build | O(n) | Lighter suffix tree |
| 5 | [[Ternary Search Tree]] | O(log n) avg | O(log n) avg | O(n) | Near-miss search |

### Checklist — Trees
- [ ] [[Tree (General)]]
- [ ] [[Binary Tree]]
- [ ] [[Binary Search Tree]]
- [ ] [[Threaded Binary Tree]]
- [ ] [[AVL Tree]]
- [ ] [[Red-Black Tree]]
- [ ] [[Splay Tree]]
- [ ] [[Treap]]
- [ ] [[B-Tree]]
- [ ] [[B+ Tree]]
- [ ] [[2-3 Tree]]
- [ ] [[Binary Heap]]
- [ ] [[Min Heap]]
- [ ] [[Max Heap]]
- [ ] [[Fibonacci Heap]]
- [ ] [[Binomial Heap]]
- [ ] [[Leftist Heap]]
- [ ] [[Segment Tree]]
- [ ] [[Fenwick Tree]]
- [ ] [[Sparse Table]]
- [ ] [[Interval Tree]]
- [ ] [[K-D Tree]]
- [ ] [[Trie]]
- [ ] [[Compressed Trie]]
- [ ] [[Suffix Tree]]
- [ ] [[Suffix Array]]
- [ ] [[Ternary Search Tree]]

---

## 5. Non-Linear — Graphs

> Nodes (vertices) connected by edges. Most general non-linear structure.

| # | Structure | Notes |
|---|---|---|
| 1 | [[Graph (General)]] | Directed / Undirected / Weighted |
| 2 | [[Adjacency Matrix]] | O(1) edge check, O(V²) space |
| 3 | [[Adjacency List]] | O(V+E) space, standard representation |
| 4 | [[Edge List]] | Minimal, used in Kruskal's |
| 5 | [[DAG (Directed Acyclic Graph)]] | No cycles, enables topological sort |
| 6 | [[Bipartite Graph]] | Two-colorable |
| 7 | [[Union-Find (Disjoint Set)]] | O(α) nearly constant, connectivity |

### Checklist — Graphs
- [ ] [[Graph (General)]]
- [ ] [[Adjacency Matrix]]
- [ ] [[Adjacency List]]
- [ ] [[Edge List]]
- [ ] [[DAG (Directed Acyclic Graph)]]
- [ ] [[Bipartite Graph]]
- [ ] [[Union-Find (Disjoint Set)]]

---

## 6. Hash-Based

> Key-value mapping with average O(1) operations via hash function.

| # | Structure | Search | Insert | Delete | Space |
|---|---|---|---|---|---|
| 1 | [[Hash Table]] | O(1) avg | O(1) avg | O(1) avg | O(n) |
| 2 | [[Hash Map]] | O(1) avg | O(1) avg | O(1) avg | O(n) |
| 3 | [[Hash Set]] | O(1) avg | O(1) avg | O(1) avg | O(n) |
| 4 | [[Linked Hash Map]] | O(1) avg | O(1) avg | O(1) avg | O(n) |
| 5 | [[Bloom Filter]] | O(k) | O(k) | N/A | O(m) |
| 6 | [[Count-Min Sketch]] | O(k) | O(k) | N/A | O(k×w) |

### Checklist — Hash-Based
- [ ] [[Hash Table]]
- [ ] [[Hash Map]]
- [ ] [[Hash Set]]
- [ ] [[Linked Hash Map]]
- [ ] [[Bloom Filter]]
- [ ] [[Count-Min Sketch]]

---

## 7. Probabilistic & Specialized

| # | Structure | Notes |
|---|---|---|
| 1 | [[Skip List]] | Already listed — probabilistic linked structure |
| 2 | [[Bloom Filter]] | Already listed — probabilistic set membership |
| 3 | [[LRU Cache]] | Hash Map + Doubly Linked List combo |
| 4 | [[LFU Cache]] | Frequency-based eviction |
| 5 | [[Rope]] | String manipulation via binary tree |

### Checklist — Specialized
- [ ] [[LRU Cache]]
- [ ] [[LFU Cache]]
- [ ] [[Rope]]

---

*← [[DSA Index]] | → [[Algorithms Index]]*
