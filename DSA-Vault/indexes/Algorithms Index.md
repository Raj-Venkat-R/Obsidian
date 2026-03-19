---
type: index
title: Algorithms Index
category: algorithms
status: active
tags: [index, algorithms]
---

# ⚙️ Algorithms Index

> All algorithms organized by category and learning order.  
> Complexity classes, NP theory, and paradigms included.

*← Back to [[DSA Index]]*

---

## Complexity Class Reference

> Before diving into algorithms, understand how they're measured and classified.

| Class | Meaning | Example |
|---|---|---|
| O(1) | Constant | Hash lookup |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Array scan |
| O(n log n) | Linearithmic | Merge sort |
| O(n²) | Quadratic | Bubble sort |
| O(n³) | Cubic | Naive matrix multiply |
| O(2ⁿ) | Exponential | Recursive subsets |
| O(n!) | Factorial | All permutations |

---

## Complexity Theory & NP

> Understanding the limits of computation.

| # | Topic | Notes |
|---|---|---|
| 1 | [[P vs NP]] | The central open question in CS |
| 2 | [[P Class]] | Problems solvable in polynomial time |
| 3 | [[NP Class]] | Solutions verifiable in polynomial time |
| 4 | [[NP-Hard]] | At least as hard as any NP problem |
| 5 | [[NP-Complete]] | NP ∩ NP-Hard — hardest problems in NP |
| 6 | [[Reduction]] | Transforming one problem into another |
| 7 | [[Approximation Algorithms]] | Near-optimal solutions for NP-Hard |
| 8 | [[Heuristics]] | No guarantee, practical solutions |
| 9 | [[Randomized Algorithms]] | Use randomness to improve expected perf |

### Checklist — Complexity Theory
- [ ] [[P vs NP]]
- [ ] [[P Class]]
- [ ] [[NP Class]]
- [ ] [[NP-Hard]]
- [ ] [[NP-Complete]]
- [ ] [[Reduction]]
- [ ] [[Approximation Algorithms]]
- [ ] [[Heuristics]]
- [ ] [[Randomized Algorithms]]

---

## 1. Sorting Algorithms

| # | Algorithm | Best | Average | Worst | Space | Stable | Notes |
|---|---|---|---|---|---|---|---|
| 1 | [[Bubble Sort]] | O(n) | O(n²) | O(n²) | O(1) | ✅ | Teaching only |
| 2 | [[Selection Sort]] | O(n²) | O(n²) | O(n²) | O(1) | ❌ | Simple, never use |
| 3 | [[Insertion Sort]] | O(n) | O(n²) | O(n²) | O(1) | ✅ | Good for small/nearly sorted |
| 4 | [[Shell Sort]] | O(n log n) | O(n^1.3) | O(n²) | O(1) | ❌ | Gap-based insertion sort |
| 5 | [[Merge Sort]] | O(n log n) | O(n log n) | O(n log n) | O(n) | ✅ | Divide & conquer, stable |
| 6 | [[Quick Sort]] | O(n log n) | O(n log n) | O(n²) | O(log n) | ❌ | Fastest in practice |
| 7 | [[Heap Sort]] | O(n log n) | O(n log n) | O(n log n) | O(1) | ❌ | In-place, not cache-friendly |
| 8 | [[Counting Sort]] | O(n+k) | O(n+k) | O(n+k) | O(k) | ✅ | Integer keys only |
| 9 | [[Radix Sort]] | O(nk) | O(nk) | O(nk) | O(n+k) | ✅ | Digit-by-digit |
| 10 | [[Bucket Sort]] | O(n+k) | O(n+k) | O(n²) | O(n) | ✅ | Uniform distribution |
| 11 | [[Tim Sort]] | O(n) | O(n log n) | O(n log n) | O(n) | ✅ | Java/Python default sort |
| 12 | [[Intro Sort]] | O(n log n) | O(n log n) | O(n log n) | O(log n) | ❌ | C++ STL default |

### Checklist — Sorting
- [ ] [[Bubble Sort]]
- [ ] [[Selection Sort]]
- [ ] [[Insertion Sort]]
- [ ] [[Shell Sort]]
- [ ] [[Merge Sort]]
- [ ] [[Quick Sort]]
- [ ] [[Heap Sort]]
- [ ] [[Counting Sort]]
- [ ] [[Radix Sort]]
- [ ] [[Bucket Sort]]
- [ ] [[Tim Sort]]
- [ ] [[Intro Sort]]

---

## 2. Searching Algorithms

| # | Algorithm | Time | Space | Notes |
|---|---|---|---|---|
| 1 | [[Linear Search]] | O(n) | O(1) | Unsorted |
| 2 | [[Binary Search]] | O(log n) | O(1) | Sorted array |
| 3 | [[Jump Search]] | O(√n) | O(1) | Sorted, block-jump |
| 4 | [[Interpolation Search]] | O(log log n) avg | O(1) | Uniform distribution |
| 5 | [[Exponential Search]] | O(log n) | O(1) | Unbounded sorted |
| 6 | [[Ternary Search]] | O(log₃ n) | O(1) | Unimodal function |

### Checklist — Searching
- [ ] [[Linear Search]]
- [ ] [[Binary Search]]
- [ ] [[Jump Search]]
- [ ] [[Interpolation Search]]
- [ ] [[Exponential Search]]
- [ ] [[Ternary Search]]

---

## 3. Graph Algorithms

### 3.1 Traversal

| # | Algorithm | Time | Space | Notes |
|---|---|---|---|---|
| 1 | [[BFS (Breadth-First Search)]] | O(V+E) | O(V) | Level-by-level, shortest path unweighted |
| 2 | [[DFS (Depth-First Search)]] | O(V+E) | O(V) | Explore deep first, recursion/stack |

### 3.2 Shortest Path

| # | Algorithm | Time | Notes |
|---|---|---|---|
| 1 | [[Dijkstra's Algorithm]] | O((V+E) log V) | Non-negative weights |
| 2 | [[Bellman-Ford Algorithm]] | O(VE) | Handles negative weights |
| 3 | [[Floyd-Warshall Algorithm]] | O(V³) | All-pairs shortest path |
| 4 | [[A* Algorithm]] | O(E) best | Heuristic-guided, pathfinding |
| 5 | [[Johnson's Algorithm]] | O(V² log V + VE) | All-pairs, sparse graphs |

### 3.3 Minimum Spanning Tree

| # | Algorithm | Time | Notes |
|---|---|---|---|
| 1 | [[Kruskal's Algorithm]] | O(E log E) | Edge-based, Union-Find |
| 2 | [[Prim's Algorithm]] | O(E log V) | Vertex-based, greedy |
| 3 | [[Borůvka's Algorithm]] | O(E log V) | Parallel MST |

### 3.4 Connectivity & Components

| # | Algorithm | Time | Notes |
|---|---|---|---|
| 1 | [[Union-Find Algorithm]] | O(α(n)) | Nearly constant, disjoint sets |
| 2 | [[Tarjan's Algorithm]] | O(V+E) | SCCs, bridges, articulation points |
| 3 | [[Kosaraju's Algorithm]] | O(V+E) | Strongly connected components |
| 4 | [[Bridges and Articulation Points]] | O(V+E) | Graph vulnerability |

### 3.5 Topological Sort

| # | Algorithm | Time | Notes |
|---|---|---|---|
| 1 | [[Kahn's Algorithm]] | O(V+E) | BFS-based topological sort |
| 2 | [[DFS-Based Topological Sort]] | O(V+E) | Post-order DFS |

### 3.6 Flow & Matching

| # | Algorithm | Time | Notes |
|---|---|---|---|
| 1 | [[Ford-Fulkerson Algorithm]] | O(E × max_flow) | Max flow |
| 2 | [[Edmonds-Karp Algorithm]] | O(VE²) | BFS-based Ford-Fulkerson |
| 3 | [[Dinic's Algorithm]] | O(V² E) | Layered graph max flow |
| 4 | [[Hungarian Algorithm]] | O(n³) | Bipartite matching, assignment |

### 3.7 Eulerian & Hamiltonian

| # | Algorithm | Notes |
|---|---|---|
| 1 | [[Eulerian Path and Circuit]] | Visit every edge once |
| 2 | [[Hamiltonian Path and Circuit]] | Visit every vertex once — NP-Complete |

### Checklist — Graph
- [ ] [[BFS (Breadth-First Search)]]
- [ ] [[DFS (Depth-First Search)]]
- [ ] [[Dijkstra's Algorithm]]
- [ ] [[Bellman-Ford Algorithm]]
- [ ] [[Floyd-Warshall Algorithm]]
- [ ] [[A* Algorithm]]
- [ ] [[Johnson's Algorithm]]
- [ ] [[Kruskal's Algorithm]]
- [ ] [[Prim's Algorithm]]
- [ ] [[Borůvka's Algorithm]]
- [ ] [[Union-Find Algorithm]]
- [ ] [[Tarjan's Algorithm]]
- [ ] [[Kosaraju's Algorithm]]
- [ ] [[Bridges and Articulation Points]]
- [ ] [[Kahn's Algorithm]]
- [ ] [[DFS-Based Topological Sort]]
- [ ] [[Ford-Fulkerson Algorithm]]
- [ ] [[Edmonds-Karp Algorithm]]
- [ ] [[Dinic's Algorithm]]
- [ ] [[Hungarian Algorithm]]
- [ ] [[Eulerian Path and Circuit]]
- [ ] [[Hamiltonian Path and Circuit]]

---

## 4. Dynamic Programming

> Break problem into subproblems. Memoize or tabulate. Optimal substructure + overlapping subproblems.

| # | Algorithm / Pattern | Notes |
|---|---|---|
| 1 | [[DP Introduction]] | Top-down vs Bottom-up, memoization vs tabulation |
| 2 | [[0-1 Knapsack]] | Classic DP, O(nW) |
| 3 | [[Unbounded Knapsack]] | Unlimited item usage |
| 4 | [[Longest Common Subsequence]] | LCS, O(mn) |
| 5 | [[Longest Increasing Subsequence]] | LIS, O(n log n) optimal |
| 6 | [[Edit Distance (Levenshtein)]] | String transformation |
| 7 | [[Matrix Chain Multiplication]] | Optimal parenthesization |
| 8 | [[Coin Change]] | Minimum coins / number of ways |
| 9 | [[Rod Cutting]] | Maximize revenue |
| 10 | [[Palindrome Subsequence and Substring]] | LPS / LPS |
| 11 | [[Egg Drop Problem]] | Classic DP puzzle |
| 12 | [[Wildcard and Regex Matching]] | Pattern matching DP |
| 13 | [[DP on Trees]] | Tree DP, rerooting technique |
| 14 | [[DP on Grids]] | Path counting, grid traversal |
| 15 | [[Bitmask DP]] | Subset states, TSP |
| 16 | [[Interval DP]] | Partition problems |
| 17 | [[Digit DP]] | Count numbers with property |

### Checklist — DP
- [ ] [[DP Introduction]]
- [ ] [[0-1 Knapsack]]
- [ ] [[Unbounded Knapsack]]
- [ ] [[Longest Common Subsequence]]
- [ ] [[Longest Increasing Subsequence]]
- [ ] [[Edit Distance (Levenshtein)]]
- [ ] [[Matrix Chain Multiplication]]
- [ ] [[Coin Change]]
- [ ] [[Rod Cutting]]
- [ ] [[Palindrome Subsequence and Substring]]
- [ ] [[Egg Drop Problem]]
- [ ] [[Wildcard and Regex Matching]]
- [ ] [[DP on Trees]]
- [ ] [[DP on Grids]]
- [ ] [[Bitmask DP]]
- [ ] [[Interval DP]]
- [ ] [[Digit DP]]

---

## 5. Greedy Algorithms

> Make locally optimal choice at each step hoping for global optimum. No backtracking.

| # | Algorithm | Notes |
|---|---|---|
| 1 | [[Greedy Introduction]] | When greedy works vs DP |
| 2 | [[Activity Selection]] | Interval scheduling |
| 3 | [[Fractional Knapsack]] | Greedy vs 0-1 |
| 4 | [[Huffman Coding]] | Optimal prefix-free codes |
| 5 | [[Job Sequencing with Deadlines]] | Profit maximization |
| 6 | [[Gas Station Problem]] | Circular route feasibility |

### Checklist — Greedy
- [ ] [[Greedy Introduction]]
- [ ] [[Activity Selection]]
- [ ] [[Fractional Knapsack]]
- [ ] [[Huffman Coding]]
- [ ] [[Job Sequencing with Deadlines]]
- [ ] [[Gas Station Problem]]

---

## 6. Divide and Conquer

| # | Algorithm | Time | Notes |
|---|---|---|---|
| 1 | [[Divide and Conquer Introduction]] | — | Master theorem, recurrence |
| 2 | [[Merge Sort]] | O(n log n) | Already in sorting |
| 3 | [[Quick Sort]] | O(n log n) avg | Already in sorting |
| 4 | [[Binary Search]] | O(log n) | Already in searching |
| 5 | [[Karatsuba Multiplication]] | O(n^1.585) | Fast multiplication |
| 6 | [[Strassen's Matrix Multiplication]] | O(n^2.807) | Faster than O(n³) |
| 7 | [[Closest Pair of Points]] | O(n log n) | Geometric D&C |

### Checklist — D&C
- [ ] [[Divide and Conquer Introduction]]
- [ ] [[Karatsuba Multiplication]]
- [ ] [[Strassen's Matrix Multiplication]]
- [ ] [[Closest Pair of Points]]

---

## 7. Backtracking

> Explore all possibilities, prune invalid paths early.

| # | Algorithm | Notes |
|---|---|---|
| 1 | [[Backtracking Introduction]] | State space tree, pruning |
| 2 | [[N-Queens Problem]] | Classic constraint satisfaction |
| 3 | [[Sudoku Solver]] | Constraint propagation |
| 4 | [[Subset Sum]] | NP-Complete in general |
| 5 | [[Permutations and Combinations]] | Generate all |
| 6 | [[Word Search]] | Grid DFS |
| 7 | [[Graph Coloring]] | NP-Complete |
| 8 | [[Rat in a Maze]] | Classic pathfinding |

### Checklist — Backtracking
- [ ] [[Backtracking Introduction]]
- [ ] [[N-Queens Problem]]
- [ ] [[Sudoku Solver]]
- [ ] [[Subset Sum]]
- [ ] [[Permutations and Combinations]]
- [ ] [[Word Search]]
- [ ] [[Graph Coloring]]
- [ ] [[Rat in a Maze]]

---

## 8. String Algorithms

| # | Algorithm | Time | Notes |
|---|---|---|---|
| 1 | [[Naive String Matching]] | O(nm) | Brute force |
| 2 | [[KMP Algorithm]] | O(n+m) | Failure function |
| 3 | [[Rabin-Karp Algorithm]] | O(n+m) avg | Rolling hash |
| 4 | [[Boyer-Moore Algorithm]] | O(n/m) best | Skip-based matching |
| 5 | [[Z Algorithm]] | O(n+m) | Z-array prefix matching |
| 6 | [[Aho-Corasick Algorithm]] | O(n+m+z) | Multi-pattern matching |
| 7 | [[Manacher's Algorithm]] | O(n) | Longest palindromic substring |
| 8 | [[Suffix Array Construction]] | O(n log n) | See also Suffix Array DS |

### Checklist — Strings
- [ ] [[Naive String Matching]]
- [ ] [[KMP Algorithm]]
- [ ] [[Rabin-Karp Algorithm]]
- [ ] [[Boyer-Moore Algorithm]]
- [ ] [[Z Algorithm]]
- [ ] [[Aho-Corasick Algorithm]]
- [ ] [[Manacher's Algorithm]]
- [ ] [[Suffix Array Construction]]

---

## 9. Mathematical Algorithms

| # | Algorithm | Time | Notes |
|---|---|---|---|
| 1 | [[Sieve of Eratosthenes]] | O(n log log n) | Primes up to n |
| 2 | [[Sieve of Sundaram]] | O(n log n) | Alternate prime sieve |
| 3 | [[Euclidean GCD]] | O(log min(a,b)) | GCD / LCM |
| 4 | [[Extended Euclidean Algorithm]] | O(log min(a,b)) | Modular inverse |
| 5 | [[Fast Exponentiation]] | O(log n) | Binary exponentiation |
| 6 | [[Modular Arithmetic]] | — | Core for competitive |
| 7 | [[Chinese Remainder Theorem]] | — | System of congruences |
| 8 | [[Matrix Exponentiation]] | O(k³ log n) | Linear recurrences |
| 9 | [[Catalan Numbers]] | O(n) | Counting problems |
| 10 | [[Inclusion-Exclusion Principle]] | — | Counting overlaps |

### Checklist — Math
- [ ] [[Sieve of Eratosthenes]]
- [ ] [[Sieve of Sundaram]]
- [ ] [[Euclidean GCD]]
- [ ] [[Extended Euclidean Algorithm]]
- [ ] [[Fast Exponentiation]]
- [ ] [[Modular Arithmetic]]
- [ ] [[Chinese Remainder Theorem]]
- [ ] [[Matrix Exponentiation]]
- [ ] [[Catalan Numbers]]
- [ ] [[Inclusion-Exclusion Principle]]

---

## 10. Bit Manipulation

| # | Algorithm / Technique | Notes |
|---|---|---|
| 1 | [[Bit Manipulation Basics]] | AND, OR, XOR, shifts |
| 2 | [[Bit Tricks]] | Check/set/clear bit, LSB, MSB |
| 3 | [[Counting Set Bits]] | Brian Kernighan's |
| 4 | [[Power of Two Check]] | n & (n-1) == 0 |
| 5 | [[XOR Tricks]] | Find missing, single number |
| 6 | [[Subset Enumeration via Bits]] | 2ⁿ subsets with bitmask |

### Checklist — Bit Manipulation
- [ ] [[Bit Manipulation Basics]]
- [ ] [[Bit Tricks]]
- [ ] [[Counting Set Bits]]
- [ ] [[Power of Two Check]]
- [ ] [[XOR Tricks]]
- [ ] [[Subset Enumeration via Bits]]

---

## 11. Two Pointers & Sliding Window

| # | Technique | Notes |
|---|---|---|
| 1 | [[Two Pointers]] | Opposite ends or same-dir |
| 2 | [[Sliding Window (Fixed)]] | Fixed-size window |
| 3 | [[Sliding Window (Variable)]] | Shrink/expand window |
| 4 | [[Fast and Slow Pointers]] | Cycle detection (Floyd's) |

### Checklist — Pointers
- [ ] [[Two Pointers]]
- [ ] [[Sliding Window (Fixed)]]
- [ ] [[Sliding Window (Variable)]]
- [ ] [[Fast and Slow Pointers]]

---

## 12. Geometric Algorithms

| # | Algorithm | Notes |
|---|---|---|
| 1 | [[Convex Hull]] | Graham scan / Jarvis march |
| 2 | [[Line Intersection]] | Segment overlap detection |
| 3 | [[Point in Polygon]] | Ray casting |
| 4 | [[Closest Pair of Points]] | D&C O(n log n) |

### Checklist — Geometry
- [ ] [[Convex Hull]]
- [ ] [[Line Intersection]]
- [ ] [[Point in Polygon]]
- [ ] [[Closest Pair of Points]]

---

## Known NP-Complete Problems

> These have no known polynomial-time algorithm. Appear across fields.

| Problem | Notes |
|---|---|
| [[Boolean Satisfiability (SAT)]] | First proven NP-Complete (Cook's theorem) |
| [[Hamiltonian Path and Circuit]] | Visit all vertices once |
| [[Travelling Salesman Problem]] | Shortest tour through all cities |
| [[Vertex Cover]] | Minimum vertices covering all edges |
| [[Clique Problem]] | Find complete subgraph of size k |
| [[Graph Coloring]] | k-coloring of a graph |
| [[Subset Sum]] | Does any subset sum to target? |
| [[Partition Problem]] | Equal-sum partition |
| [[3-SAT]] | SAT restricted to 3-literal clauses |
| [[Independent Set]] | Max set of non-adjacent vertices |

### Checklist — NP-Complete
- [ ] [[Boolean Satisfiability (SAT)]]
- [ ] [[Hamiltonian Path and Circuit]]
- [ ] [[Travelling Salesman Problem]]
- [ ] [[Vertex Cover]]
- [ ] [[Clique Problem]]
- [ ] [[Graph Coloring]]
- [ ] [[Subset Sum]]
- [ ] [[Partition Problem]]
- [ ] [[3-SAT]]
- [ ] [[Independent Set]]

---

*← [[Data Structures Index]] | → Start with [[Bubble Sort]] or [[BFS (Breadth-First Search)]]*
