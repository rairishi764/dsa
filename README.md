# 8-Week DSA Interview Prep Plan — Progress Tracker

> **How to use:** Tick `[ ]` → `[x]` as you complete each item. Update the **Progress Dashboard** at the top after each session. Keep notes in the "Reflection" line at the end of each week.

---

## Progress Dashboard

| Metric | Target | Current |
|---|---|---|
| Weeks completed | 8 | 0 |
| LeetCode problems solved | 150 | 0 |
| Udemy lectures watched | ~400 | 0 |
| Mock interviews done | 4 | 0 |
| Re-review queue size | <10 by end | — |

**Status legend for problems:** `[ ]` not started · `[~]` attempted, needs review · `[x]` solved cleanly

**Start date:** _______ &nbsp;&nbsp;&nbsp;&nbsp; **Target end date:** _______

---

## Ground rules

**Weekly time budget (~16–18 hrs/week):**
- **Mon–Fri:** ~1.5 hrs/day after work (7.5 hrs/week)
- **Sat:** ~4 hrs (theory + problems)
- **Sun:** ~4 hrs (problems + weekly review)
- **Total over 8 weeks:** ~130–140 hrs

**Daily structure (weekdays):** 30–45 min Udemy at 1.5× + 45–60 min for 1–2 LC problems.
**Weekend structure:** 1 hr Udemy catch-up + 2 hr problems + 1 hr review (re-solve from scratch on paper).

**The 30-minute rule:** If a problem stumps you for 30 min, read the editorial, understand it deeply, then **re-solve it from scratch the next day without looking**. Don't grind for 2 hours hoping inspiration strikes.

**Spaced repetition:** Every Sunday, re-solve 3 problems from earlier weeks that you found hard. Add any you flag as `[~]` to the re-review queue at the bottom.

---

## Week 1 — Foundations: Big O, Arrays, Strings, Hashmap

**Goal:** Comfort with Python data structures and Big O. Knock out the easy/medium volume of Array/String/Hashmap.

### Theory (Udemy)
- [ ] Big O fundamentals (O(1), O(N), O(N²), O(logN), drop constants/non-dominant)
- [ ] Space complexity
- [ ] Arrays: 1D operations (insert, traverse, search, delete) + memory layout
- [ ] 2D Arrays: creation, traversal, complexity
- [ ] Lists: create, slice, update, delete, search, list comprehension
- [ ] Dictionaries: operations, hashing intro, dict comprehension
- [ ] Tuples: operations, vs list
- [ ] Big O practice questions (Print Pairs, Reverse, O(N) equivalents)

### LeetCode problems (24)
**Mon (Two Sum + Anagram)**
- [ ] Two Sum (E)
- [ ] Valid Anagram (E)

**Tue (basic array)**
- [ ] Merge Sorted Array (E)
- [ ] Remove Element (E)

**Wed**
- [ ] Remove Duplicates from Sorted Array (E)
- [ ] Majority Element (E)

**Thu**
- [ ] Best Time to Buy and Sell Stock (E)
- [ ] Contains Duplicate II (E)

**Fri (hashmap intro)**
- [ ] Ransom Note (E)
- [ ] Isomorphic Strings (E)

**Sat (longer session)**
- [ ] Group Anagrams (M)
- [ ] Happy Number (E)
- [ ] Word Pattern (E)
- [ ] Length of Last Word (E)
- [ ] Roman to Integer (E)

**Sun (review + harder set)**
- [ ] Longest Common Prefix (E)
- [ ] Reverse Words in a String (M)
- [ ] Longest Consecutive Sequence (M)
- [ ] Plus One (E)
- [ ] Palindrome Number (E)
- [ ] Remove Duplicates from Sorted Array II (M)
- [ ] Rotate Array (M)
- [ ] Best Time to Buy and Sell Stock II (M)
- [ ] Find the Index of the First Occurrence in a String (E)

**Checkpoint:** Can you state the Big O of every solution above without thinking? **Reflection:** _______

---

## Week 2 — Two Pointers, Sliding Window, Matrix, Math

### Theory
- [ ] Two pointers pattern (same direction + opposite ends)
- [ ] Sliding window pattern (fixed + variable size templates)
- [ ] Matrix traversal patterns (in-place rotation, spiral)
- [ ] Math review (overflow, modular arithmetic, GCD)

### LeetCode problems (18)
**Mon — Two pointers**
- [ ] Valid Palindrome (E)
- [ ] Is Subsequence (E)

**Tue**
- [ ] Two Sum II - Input Array Is Sorted (M)
- [ ] Container With Most Water (M)

**Wed — Sliding window**
- [ ] Minimum Size Subarray Sum (M)
- [ ] Longest Substring Without Repeating Characters (M)

**Thu — Matrix**
- [ ] Valid Sudoku (M)
- [ ] Rotate Image (M)

**Fri — Math**
- [ ] Sqrt(x) (E)
- [ ] Pow(x, n) (M)

**Sat**
- [ ] 3Sum (M)
- [ ] Spiral Matrix (M)
- [ ] Set Matrix Zeroes (M)
- [ ] Game of Life (M)

**Sun**
- [ ] Factorial Trailing Zeroes (M)
- [ ] Insert Delete GetRandom O(1) (M)
- [ ] Product of Array Except Self (M)
- [ ] Jump Game (M)

**Checkpoint:** Can you implement a sliding window template in <2 minutes? **Reflection:** _______

---

## Week 3 — Linked Lists, Stack, Queue

### Theory
- [ ] Singly linked list: node class, append, prepend, insert, traverse
- [ ] SLL: search, get, set, pop, remove
- [ ] Doubly linked list: append, prepend, traverse, get/set/pop
- [ ] Stack: list-based + linked-list based implementations
- [ ] Queue: list-based, circular queue, linked-list based
- [ ] `collections.deque` and `queue` module

### LeetCode problems (16)
**Mon**
- [ ] Linked List Cycle (E)
- [ ] Merge Two Sorted Lists (E)

**Tue**
- [ ] Remove Nth Node From End of List (M)
- [ ] Add Two Numbers (M)

**Wed**
- [ ] Reverse Linked List II (M)
- [ ] Partition List (M)

**Thu — Stack**
- [ ] Valid Parentheses (E)
- [ ] Min Stack (M)

**Fri**
- [ ] Evaluate Reverse Polish Notation (M)
- [ ] Simplify Path (M)

**Sat**
- [ ] LRU Cache (M)
- [ ] Copy List with Random Pointer (M)
- [ ] Rotate List (M)
- [ ] Remove Duplicates from Sorted List II (M)

**Sun**
- [ ] Reverse Nodes in k-Group (H)
- [ ] Basic Calculator (H)

**Checkpoint:** Can you draw the pointer dance for reversing a linked list with your eyes closed? **Reflection:** _______

---

## Week 4 — Recursion + Trees (Binary Tree, BST, BFS)

### Theory
- [ ] Recursion: 3-step framework, base case, recursive case
- [ ] Recursion time complexity (recurrence relations, T(n) = 2T(n/2) + n etc.)
- [ ] Binary Tree: representation, creation
- [ ] Tree traversals: PreOrder, InOrder, PostOrder, LevelOrder
- [ ] BST: insert, search, delete
- [ ] Merge Sort + Quick Sort (recursion practice)
- [ ] Sum of Digits / GCD / Decimal-to-Binary recursion exercises

### LeetCode problems (21)
**Mon**
- [ ] Maximum Depth of Binary Tree (E)
- [ ] Same Tree (E)

**Tue**
- [ ] Invert Binary Tree (E)
- [ ] Symmetric Tree (E)

**Wed**
- [ ] Validate Binary Search Tree (M)
- [ ] Kth Smallest Element in a BST (M)

**Thu**
- [ ] Construct Binary Tree from Preorder and Inorder Traversal (M)
- [ ] Path Sum (E)

**Fri — BFS**
- [ ] Binary Tree Level Order Traversal (M)
- [ ] Binary Tree Right Side View (M)

**Sat (longer session)**
- [ ] Lowest Common Ancestor of a Binary Tree (M)
- [ ] Flatten Binary Tree to Linked List (M)
- [ ] Sum Root to Leaf Numbers (M)
- [ ] Count Complete Tree Nodes (E)
- [ ] Average of Levels in Binary Tree (E)
- [ ] Convert Sorted Array to Binary Search Tree (E)

**Sun**
- [ ] Sort List (M)
- [ ] Construct Binary Tree from Inorder and Postorder Traversal (M)
- [ ] Binary Tree Zigzag Level Order Traversal (M)
- [ ] Minimum Absolute Difference in BST (E)
- [ ] Binary Search Tree Iterator (M)
- [ ] Populating Next Right Pointers in Each Node II (M)

**Checkpoint:** Can you instantly recognize "DFS this tree, return X"? This is the most-tested category. **Reflection:** _______

---

## Week 5 — Heap, Trie, Backtracking

### Theory
- [ ] Binary heap: insert, extract, heapify, sizeofheap
- [ ] Python `heapq` module (min-heap, simulating max-heap)
- [ ] Trie: insert, search, delete, prefix matching
- [ ] Backtracking template: choose / explore / un-choose
- [ ] N-Queens walkthrough

### LeetCode problems (17)
**Mon**
- [ ] Kth Largest Element in an Array (M)

**Tue**
- [ ] Find K Pairs with Smallest Sums (M)
- [ ] Find Median from Data Stream (H)

**Wed — Trie**
- [ ] Implement Trie (Prefix Tree) (M)
- [ ] Design Add and Search Words Data Structure (M)

**Thu — Backtracking**
- [ ] Letter Combinations of a Phone Number (M)
- [ ] Generate Parentheses (M)

**Fri**
- [ ] Combinations (M)
- [ ] Permutations (M)

**Sat**
- [ ] Combination Sum (M)
- [ ] Word Search (M)
- [ ] N-Queens II (H)
- [ ] Word Search II (H)

**Sun**
- [ ] IPO (H)
- [ ] Binary Tree Maximum Path Sum (H)
- [ ] Merge k Sorted Lists (H)

**Checkpoint:** Do you have *one* backtracking template you trust and can adapt in 5 minutes? **Reflection:** _______

---

## Week 6 — Graphs + Intervals + Greedy

### Theory
- [ ] Graph representations (adjacency list vs matrix)
- [ ] BFS in graphs
- [ ] DFS in graphs
- [ ] Topological sort (Kahn's + DFS-based)
- [ ] Dijkstra (concepts only — visualization is enough)
- [ ] Greedy: Activity Selection, Coin Change

### LeetCode problems (13)
**Mon**
- [ ] Number of Islands (M)

**Tue**
- [ ] Surrounded Regions (M)
- [ ] Clone Graph (M)

**Wed — Topological**
- [ ] Course Schedule (M)
- [ ] Course Schedule II (M)

**Thu — BFS state-space**
- [ ] Snakes and Ladders (M)
- [ ] Minimum Genetic Mutation (M)

**Fri — Intervals**
- [ ] Merge Intervals (M)
- [ ] Insert Interval (M)

**Sat**
- [ ] Word Ladder (H)
- [ ] Evaluate Division (M)
- [ ] Summary Ranges (E)

**Sun**
- [ ] Minimum Number of Arrows to Burst Balloons (M)
- [ ] Gas Station (M)
- [ ] Candy (H)

**Checkpoint:** Can you write BFS and DFS templates from memory in under 3 minutes each? **Reflection:** _______

---

## Week 7 — Binary Search, Bit Manipulation, Kadane, Divide & Conquer

### Theory
- [ ] Binary search template (lo/hi/mid, invariants, off-by-one)
- [ ] Binary search variants (rotated, peak, first/last position)
- [ ] Linear search & when to use it
- [ ] Bit manipulation basics (AND, OR, XOR, shifts)
- [ ] XOR tricks (single number, swap)
- [ ] Kadane's algorithm

### LeetCode problems (18)
**Mon**
- [ ] Search Insert Position (E)
- [ ] Search a 2D Matrix (M)

**Tue**
- [ ] Find Peak Element (M)
- [ ] Find First and Last Position of Element in Sorted Array (M)

**Wed**
- [ ] Search in Rotated Sorted Array (M)
- [ ] Find Minimum in Rotated Sorted Array (M)

**Thu — Bit**
- [ ] Single Number (E)
- [ ] Number of 1 Bits (E)
- [ ] Add Binary (E)

**Fri**
- [ ] Reverse Bits (E)
- [ ] Single Number II (M)
- [ ] Maximum Subarray (M)

**Sat**
- [ ] Median of Two Sorted Arrays (H)
- [ ] Maximum Sum Circular Subarray (M)
- [ ] Bitwise AND of Numbers Range (M)
- [ ] Trapping Rain Water (H)
- [ ] H-Index (M)

**Sun**
- [ ] Construct Quad Tree (M)
- [ ] Max Points on a Line (H)
- [ ] Jump Game II (M)

**Checkpoint:** Binary search is the highest-leverage pattern this week — drill it until *invariants* feel natural. **Reflection:** _______

---

## Week 8 — Dynamic Programming + Mock Interviews

### Theory
- [ ] DP framework: state, transition, base case
- [ ] Top-down memoization vs bottom-up tabulation
- [ ] House Robber walkthrough
- [ ] Knapsack (0/1) walkthrough
- [ ] LCS / LPS walkthroughs
- [ ] Edit distance walkthrough

### LeetCode problems (15)
**Mon**
- [ ] Climbing Stairs (E)
- [ ] House Robber (M)

**Tue**
- [ ] Coin Change (M)
- [ ] Word Break (M)

**Wed**
- [ ] Longest Increasing Subsequence (M)
- [ ] Maximal Square (M)

**Thu — 2D Grid DP**
- [ ] Triangle (M)
- [ ] Minimum Path Sum (M)
- [ ] Unique Paths II (M)

**Fri — String DP**
- [ ] Longest Palindromic Substring (M)
- [ ] Edit Distance (M)

**Sat**
- [ ] Best Time to Buy and Sell Stock III (H)
- [ ] Best Time to Buy and Sell Stock IV (H)
- [ ] Interleaving String (M)
- [ ] Text Justification (H)

**Sun — MOCK DAY**
- [ ] Mock interview #3 (45 min) + retro
- [ ] Mock interview #4 (45 min) + retro

### Mock interviews schedule
- [ ] Mock #1 — Tue evening, week 8 (Pramp / interviewing.io / friend)
- [ ] Mock #2 — Thu evening, week 8
- [ ] Mock #3 — Sun, week 8
- [ ] Mock #4 — Sun, week 8

**Checkpoint:** All 150 attempted; ≥130 solved cleanly; 4 mocks done. **Reflection:** _______

---

## Re-review queue (the "must re-solve" set)

> Add any problem you marked `[~]` here. Re-solve weekly. Move to "Mastered" once you can solve from scratch in target time.

**Active queue:**
- [ ] _______
- [ ] _______
- [ ] _______
- [ ] _______
- [ ] _______

**Mastered:**
- [ ] _______
- [ ] _______

---

## High-frequency interview problems (always re-review these)

These appear in real interviews most often. Re-review them in the final 2 weeks regardless of how comfortable you feel.

- [ ] Two Sum
- [ ] Group Anagrams
- [ ] Longest Substring Without Repeating Characters
- [ ] Merge Intervals
- [ ] Insert Interval
- [ ] Reverse Linked List II
- [ ] LRU Cache
- [ ] Validate Binary Search Tree
- [ ] Lowest Common Ancestor of a Binary Tree
- [ ] Binary Tree Level Order Traversal
- [ ] Number of Islands
- [ ] Course Schedule
- [ ] Kth Largest Element in an Array
- [ ] Find Median from Data Stream
- [ ] Word Search
- [ ] Generate Parentheses
- [ ] Search in Rotated Sorted Array
- [ ] Coin Change
- [ ] House Robber
- [ ] Longest Increasing Subsequence
- [ ] Edit Distance

---

## What to skip if you fall behind

**Skip in this order (least → most damaging to skip):**
1. Hard problems flagged in the table
2. Udemy AVL Trees, Floyd-Warshall, Bellman-Ford (rare in LC150)
3. Udemy Circular Doubly Linked List variants
4. LC Math hards (Max Points on a Line)

**Never skip:** Trees, Graphs, Binary Search, DP fundamentals, LRU Cache.

---

## Daily habit hygiene

- [ ] Code by hand at least 3 problems/week (no autocomplete)
- [ ] Time yourself — Mediums >40 min go into the re-review queue
- [ ] Verbalize your approach out loud before coding (even alone)
- [ ] End each session with one line: "Today I learned ___"

---

## Definition of done (end of Week 8)

- [ ] All 150 LC problems attempted
- [ ] ≥130 solved cleanly (Green)
- [ ] Can implement from memory in <5 min: BFS, DFS, binary search, sliding window, backtracking
- [ ] 4 mock interviews completed with written retrospectives
- [ ] Re-review queue mostly empty
