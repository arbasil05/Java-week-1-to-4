# 🧠 Complete DSA Conceptual Guide — 4-Week Test Preparation

> **Purpose:** Deep conceptual understanding of every topic, pattern, and thinking model across all 4 weeks.
> **Rule:** No code. No solutions. Pure concepts only.

---

# 📅 WEEK 1 — Mathematical Thinking, Recursion & Backtracking

## Problems Covered

| # | Problem | Category |
|---|---------|----------|
| 1 | Factorial Trailing Zeroes | Math |
| 2 | Power of Two | Bit Manipulation / Math |
| 3 | Add Digits | Math / Number Theory |
| 4 | Fibonacci Number | Recursion / DP |
| 5 | Pow(x, n) | Recursion / Math |
| 6 | Valid Palindrome | Two Pointers / Strings |
| 7 | Combination Sum | Backtracking |
| 8 | Generate Parentheses | Backtracking |
| 9 | Letter Combinations of a Phone Number | Backtracking |

---

## 📌 Core Topics Covered

### 1. Mathematical Foundations
- **Prime Factorization Thinking:** Many math problems on LeetCode reduce to understanding how prime factors compose a number. Trailing zeroes in a factorial is entirely about counting pairs of 2s and 5s in the prime factorization of n!. Since 2s are always more abundant, the problem reduces to counting factors of 5.
- **Modular Arithmetic & Digital Roots:** Add Digits is grounded in the concept of a *digital root*, which has a direct closed-form formula based on modulo 9 arithmetic. Understanding congruence (n ≡ r mod 9) is key.
- **Powers and Logarithmic Thinking:** Determining if a number is a power of two requires understanding binary representation. A power of two has exactly one set bit. This connects math to bit manipulation.
- **Exponentiation by Squaring:** Pow(x, n) introduces the concept of *fast exponentiation* — reducing O(n) multiplications to O(log n) by exploiting the property that x^n = (x^(n/2))^2.

### 2. Recursion
- **Base Case + Recursive Case:** Every recursive solution must define when to stop (base case) and how to reduce the problem (recursive case).
- **Overlapping Subproblems:** Fibonacci is the canonical example. Naive recursion recomputes the same values exponentially. This motivates memoization and dynamic programming.
- **Divide and Conquer via Recursion:** Pow(x, n) divides the exponent in half each time — a textbook divide-and-conquer recursion.
- **Recursion Tree Visualization:** For backtracking problems, visualizing the recursion tree is the single most important mental model. Each node is a decision point; each branch is a choice.

### 3. Backtracking
- **The Backtracking Template:** Choose → Explore → Un-choose. Every backtracking problem follows this pattern. You make a choice, recurse deeper, then undo the choice to try the next option.
- **Constraint Satisfaction:** Generate Parentheses adds constraints — you can only add a closing parenthesis if you have more open ones than closed ones so far. Backtracking with pruning.
- **Combination Generation:** Combination Sum explores all possible combinations that sum to a target. The key insight is whether you allow reuse of elements (unbounded) or not (bounded).
- **Mapping & Branching:** Letter Combinations of a Phone Number maps each digit to a set of characters, then generates all combinations. The branching factor at each level depends on the digit's mapping.

### 4. Two-Pointer / String Manipulation
- **Palindrome Checking:** Valid Palindrome introduces the two-pointer technique on strings — one pointer from the start, one from the end, moving inward while comparing characters.
- **Character Filtering:** Real interview palindrome problems require ignoring non-alphanumeric characters and being case-insensitive. Preprocessing vs. skipping in-place is a design choice.

---

## 🧠 Patterns & Thinking Models

### Pattern 1: Reduce to a Simpler Mathematical Property
- Trailing Zeroes → count factors of 5 in n!
- Power of Two → check if exactly one bit is set (n & (n-1) == 0)
- Add Digits → digital root formula (1 + (n-1) % 9)
- **Thinking Model:** Before writing any algorithm, ask: "Is there a mathematical shortcut or closed-form solution?"

### Pattern 2: Recursion with Memoization
- Fibonacci → naive recursion has O(2^n) time; with memoization it becomes O(n)
- Pow(x, n) → recursion that halves the problem each time → O(log n)
- **Thinking Model:** "Can I break this into smaller identical subproblems? Are subproblems recomputed?"

### Pattern 3: Backtracking Decision Tree
- Combination Sum → at each step, decide to include a number or skip it
- Generate Parentheses → at each step, decide to add '(' or ')'
- Letter Combinations → at each digit, branch into all possible characters
- **Thinking Model:** "What are my choices at each step? What constraints prune invalid branches?"

### Pattern 4: Two-Pointer Convergence
- Valid Palindrome → left pointer moves right, right pointer moves left
- **Thinking Model:** "Can I solve this by examining both ends and working inward?"

### Pattern 5: Exponentiation by Squaring (Divide & Conquer)
- Instead of multiplying x, n times, compute x^(n/2) once and square it
- Handle odd n by multiplying one extra x
- Handle negative n by inverting x and negating n
- **Thinking Model:** "Can I halve the problem size at each step?"

---

## 📊 Data Structures Used

| Data Structure | Where Used | Why |
|---------------|-----------|-----|
| **Integer / Long** | Trailing Zeroes, Power of Two, Add Digits | Core math operations; watch for overflow |
| **Recursion Stack (Call Stack)** | Fibonacci, Pow, Backtracking problems | Implicit stack for recursive calls |
| **Array / List** | Combination Sum, Letter Combinations | Accumulate partial results during backtracking |
| **String / StringBuilder** | Generate Parentheses, Valid Palindrome | Build candidates character by character |
| **HashMap (Memoization)** | Fibonacci (optimized) | Cache previously computed results |
| **Character Array** | Valid Palindrome | In-place character comparison |

---

## ⚙️ Algorithms Involved

### 1. Fast Exponentiation (Binary Exponentiation)
- Repeatedly square the base while halving the exponent
- Time: O(log n), Space: O(log n) recursive / O(1) iterative

### 2. Backtracking
- Systematic exploration of all possible configurations
- Pruning eliminates invalid branches early
- Time: varies by problem (often exponential in the worst case)

### 3. Recursion with Memoization (Top-Down DP)
- Store results of subproblems in a table
- Convert exponential recursion to polynomial time

### 4. Two-Pointer Technique
- Two indices moving towards each other
- O(n) time, O(1) space for palindrome checking

### 5. Prime Factor Counting
- Iteratively divide and count specific prime factors
- For trailing zeroes: repeatedly divide n by 5 and accumulate

---

## ⏱ Time & Space Complexity Patterns

| Problem | Time | Space | Key Insight |
|---------|------|-------|-------------|
| Factorial Trailing Zeroes | O(log₅ n) | O(1) | Divide n by 5 repeatedly |
| Power of Two | O(1) | O(1) | Single bit operation |
| Add Digits | O(1) | O(1) | Closed-form digital root |
| Fibonacci Number | O(n) memoized / O(2^n) naive | O(n) / O(1) iterative | Classic DP example |
| Pow(x, n) | O(log n) | O(log n) recursive | Halving the exponent |
| Valid Palindrome | O(n) | O(1) | Single pass, two pointers |
| Combination Sum | O(2^(T/min)) | O(T/min) | T = target, min = smallest candidate |
| Generate Parentheses | O(4^n / √n) — Catalan | O(n) | nth Catalan number |
| Letter Combinations | O(4^n) | O(n) | Max 4 letters per digit, n digits |

**Themes:**
- Math problems often achieve O(1) or O(log n) — recognize when a formula exists
- Backtracking is inherently exponential — pruning is what makes it practical
- Recursion depth = space complexity when no tail-call optimization is available

---

## ⚠️ Common Mistakes

### Math Problems
- **Overflow:** When computing factorials or powers, intermediate values can exceed int/long range. Pow(x, n) with n = Integer.MIN_VALUE — negating it overflows.
- **Off-by-one in factor counting:** Forgetting that n=25 contributes TWO factors of 5 (5 and 25), n=125 contributes THREE.
- **Zero and negative inputs:** Power of Two with n ≤ 0 should return false. Add Digits with n = 0 is a special case.

### Recursion
- **Missing base case:** Infinite recursion and stack overflow.
- **Not memoizing:** Fibonacci without memoization is O(2^n) — unacceptable.
- **Mutating shared state without backtracking:** In backtracking, if you modify a list and don't undo the modification, subsequent branches see corrupted state.

### Backtracking
- **Not sorting candidates:** In Combination Sum, sorting helps skip duplicates and prune branches where remaining candidates exceed the target.
- **Generating duplicates:** Not handling repeated elements properly leads to duplicate combinations in the result.
- **Incorrect pruning:** Being too aggressive with pruning misses valid solutions; being too lenient wastes time.

### String / Palindrome
- **Not filtering characters:** Forgetting to skip non-alphanumeric characters.
- **Case sensitivity:** Comparing 'A' and 'a' as different characters.
- **Empty string:** An empty string is a valid palindrome.

---

## 🔁 How Problems Connect to Each Other

```
                    ┌─────────────────┐
                    │  RECURSION       │
                    │  (Foundation)    │
                    └───────┬─────────┘
                            │
               ┌────────────┼────────────┐
               ▼            ▼            ▼
        ┌──────────┐  ┌──────────┐  ┌──────────────┐
        │Fibonacci │  │ Pow(x,n) │  │ Backtracking │
        │(Overlap) │  │(Divide & │  │  Problems    │
        └────┬─────┘  │ Conquer) │  └──────┬───────┘
             │        └──────────┘         │
             ▼                    ┌────────┼────────┐
        ┌──────────┐              ▼        ▼        ▼
        │Memoize / │        Combination  Generate  Letter
        │   DP     │           Sum     Parentheses Combos
        └──────────┘
        
        ┌───────────────────────────────────────────┐
        │           MATH CLUSTER                     │
        │  Trailing Zeroes ←→ Power of Two           │
        │         (Prime factors)  (Bit manipulation)│
        │              Add Digits                    │
        │         (Number theory / modular arith)    │
        └───────────────────────────────────────────┘
        
        ┌───────────────────────────────────────────┐
        │      Valid Palindrome                      │
        │  (Two-pointer on strings — foundation     │
        │   for Week 4's Palindrome Linked List)    │
        └───────────────────────────────────────────┘
```

- **Fibonacci → Pow(x, n):** Both use recursion, but Fibonacci has overlapping subproblems (needs memoization) while Pow has non-overlapping subproblems (pure divide & conquer).
- **Combination Sum → Generate Parentheses → Letter Combinations:** All three are backtracking. They differ in the *branching choices* and *constraints* but share the same Choose → Explore → Un-choose skeleton.
- **Trailing Zeroes → Power of Two:** Both require understanding how numbers decompose into prime factors. One counts factors of 5; the other checks for a single factor of 2.
- **Valid Palindrome → Palindrome Linked List (Week 4):** The two-pointer palindrome concept carries directly into checking palindromes on linked lists, where you reverse half the list and compare.

---

## 🚀 Advanced Insights

1. **Catalan Numbers in Generate Parentheses:** The number of valid parentheses combinations for n pairs is the nth Catalan number: C(n) = (2n)! / ((n+1)! * n!). Understanding Catalan numbers appears in many combinatorial problems (BST counting, ballot problems, Dyck paths).

2. **Iterative Fibonacci with O(1) Space:** You only need two variables to compute Fibonacci bottom-up. This is the simplest example of "rolling array" optimization in DP — a technique that scales to harder DP problems.

3. **Binet's Formula for Fibonacci:** There's a closed-form O(1) solution using the golden ratio: F(n) = (φ^n - ψ^n) / √5. In practice, floating-point precision limits its usefulness, but knowing it exists demonstrates the power of mathematical analysis.

4. **Backtracking as Constrained DFS:** Every backtracking problem is essentially a depth-first search on a decision tree with constraint-based pruning. This mental model unifies backtracking with graph traversal (Week 4).

5. **Negative Exponent Trap in Pow(x, n):** When n = Integer.MIN_VALUE (-2^31), you cannot simply negate it because Integer.MAX_VALUE is 2^31 - 1. You must handle this edge case by converting to long or handling one multiplication separately.

---
---

# 📅 WEEK 2 — Arrays, Binary Search, Sorting & Matrix Operations

## Problems Covered

| # | Problem | Category |
|---|---------|----------|
| 1 | Running Sum of 1D Array | Prefix Sum |
| 2 | Average Salary | Array / Math |
| 3 | Find Numbers with Even Number of Digits | Array / Math |
| 4 | Remove Duplicates from Sorted Array | Two Pointers |
| 5 | Container With Most Water | Two Pointers |
| 6 | Trapping Rain Water | Two Pointers / Stack / DP |
| 7 | Richest Customer Wealth | Matrix / Array |
| 8 | Matrix Diagonal Sum | Matrix |
| 9 | Transpose Matrix | Matrix |
| 10 | Find Minimum in Rotated Sorted Array | Binary Search |
| 11 | Find Index of First Occurrence in String | String Matching |
| 12 | Binary Search | Binary Search |
| 13 | First Bad Version | Binary Search |
| 14 | Search Insert Position | Binary Search |
| 15 | Find First and Last Position | Binary Search |
| 16 | Sort an Array | Sorting |
| 17 | Height Checker | Sorting |
| 18 | Third Maximum Number | Array / Sorting |
| 19 | Kth Largest Element | Sorting / Heap |
| 20 | Merge Intervals | Sorting / Intervals |

---

## 📌 Core Topics Covered

### 1. Prefix Sum
- **Concept:** A prefix sum array stores cumulative sums: prefix[i] = arr[0] + arr[1] + ... + arr[i]. This allows computing any subarray sum in O(1) after O(n) preprocessing.
- **Running Sum** is literally constructing the prefix sum array.
- **Foundation for Week 4:** Prefix sums appear again in "Shortest Subarray with Sum at Least K."

### 2. Array Manipulation & In-Place Operations
- **Remove Duplicates from Sorted Array** requires modifying the array *in-place* with O(1) extra space. This is a classic two-pointer technique where a "write pointer" trails behind a "read pointer."
- **In-place means no extra array.** You overwrite elements in the original array.

### 3. Two-Pointer Technique (Advanced)
- **Container With Most Water:** Two pointers start at the extremes and move inward. The key insight is that moving the pointer at the *shorter* line is the only way to potentially increase the area. Moving the taller pointer can never increase area because the width decreases and the height is limited by the shorter line.
- **Trapping Rain Water:** The most conceptually rich problem in this week. Multiple approaches exist:
  - *Two-pointer approach:* Track left_max and right_max, process from the side with the smaller max.
  - *DP approach:* Precompute left_max[] and right_max[] arrays, then water at each index = min(left_max[i], right_max[i]) - height[i].
  - *Stack approach:* Use a monotonic decreasing stack to identify "valleys" that trap water.

### 4. Matrix Operations
- **Row-major traversal:** Richest Customer Wealth sums each row.
- **Diagonal traversal:** Matrix Diagonal Sum accesses elements where row == col (primary diagonal) and row + col == n-1 (secondary diagonal). Watch for the center element overlap in odd-sized matrices.
- **Transpose:** Transpose interchanges rows and columns. For an m×n matrix, the transpose is n×m. Key property: transpose[j][i] = matrix[i][j].

### 5. Binary Search
- **The Core Invariant:** Binary search maintains a search range [lo, hi] and eliminates half the range at each step based on a condition.
- **Standard Binary Search:** Find a target in a sorted array. O(log n).
- **Search Insert Position:** Find where a target *would* be inserted. This is binary search for the *leftmost position* where the element ≥ target.
- **First Bad Version:** Binary search on a boolean predicate — find the first index where isBadVersion returns true. This is the "binary search on answer" pattern.
- **Find First and Last Position:** Two binary searches — one for the leftmost occurrence, one for the rightmost. Understanding how to bias binary search left or right is critical.
- **Find Minimum in Rotated Sorted Array:** Binary search where the midpoint comparison is against the rightmost element to determine which half is sorted.

### 6. Sorting Algorithms
- **Sort an Array** asks you to implement a sorting algorithm. The expected approaches:
  - **Merge Sort:** Divide array in half, sort each half, merge. O(n log n) guaranteed. Stable. O(n) space.
  - **Quick Sort:** Choose a pivot, partition around it, recurse on each side. O(n log n) average, O(n²) worst case. Not stable. O(log n) space.
  - **Heap Sort:** Build a max-heap, repeatedly extract the maximum. O(n log n) guaranteed. Not stable. O(1) space.
- **Height Checker** compares the array with its sorted version — understanding what "sorted order" means.
- **Counting Sort** is applicable when the range of values is small — O(n + k) time.

### 7. Finding the Kth Element
- **Third Maximum Number:** Find the 3rd largest distinct value. Can be done with three tracking variables or a min-heap of size 3.
- **Kth Largest Element:** The crucial algorithmic insight:
  - **Sorting approach:** Sort and index — O(n log n)
  - **Min-Heap of size K:** Maintain a heap of the K largest elements — O(n log k)
  - **Quickselect:** Partition-based selection — O(n) average, O(n²) worst case. This is the expected optimal approach.
  
### 8. Interval Problems
- **Merge Intervals:** Sort intervals by start time, then iterate and merge overlapping intervals. The key condition: if current.start ≤ previous.end, they overlap.

### 9. String Matching
- **Find Index of First Occurrence:** Naive approach is O(n × m). KMP (Knuth-Morris-Pratt) achieves O(n + m) by precomputing a failure function. Understanding the concept of the *longest proper prefix which is also a suffix* is the foundation of KMP.

---

## 🧠 Patterns & Thinking Models

### Pattern 1: Prefix Sum / Running Computation
- Compute cumulative values in a single pass
- Enables O(1) range queries after O(n) preprocessing
- **Thinking Model:** "Do I need repeated subarray sum queries? Build a prefix sum."

### Pattern 2: Two-Pointer (Converging)
- Two pointers start at opposite ends and move toward each other
- Used when the array is sorted or when you're optimizing over a pair
- Container With Most Water, Remove Duplicates, Trapping Rain Water
- **Thinking Model:** "Can I eliminate one end based on a comparison?"

### Pattern 3: Two-Pointer (Read-Write / Slow-Fast)
- One pointer reads, another writes; used for in-place modifications
- Remove Duplicates: fast pointer scans, slow pointer writes unique values
- **Thinking Model:** "Do I need to modify an array in-place while scanning?"

### Pattern 4: Binary Search on Sorted Data
- Prerequisite: the search space must be monotonic (sorted or satisfying a monotonic predicate)
- Standard: find exact value
- Bisect-left: find first occurrence / insertion point
- Bisect-right: find last occurrence
- **Thinking Model:** "Is the search space sorted or can I define a monotonic predicate? Can I halve the search space at each step?"

### Pattern 5: Sort First, Then Process
- Merge Intervals: sort by start → greedy merge
- Height Checker: sort → compare
- Kth Largest: sort → index, or use partial sort
- **Thinking Model:** "Would sorting simplify comparisons or grouping?"

### Pattern 6: Matrix Traversal Patterns
- Row-by-row, column-by-column, diagonal, anti-diagonal, spiral
- Transpose is a specific index-swap pattern
- **Thinking Model:** "What traversal order does this problem need? What's the index relationship?"

### Pattern 7: Partitioning / Quickselect
- Don't fully sort when you only need the Kth element
- Quickselect gives expected O(n) by only recursing into the relevant half
- **Thinking Model:** "Do I need full sorting or just the Kth element?"

---

## 📊 Data Structures Used

| Data Structure | Where Used | Why |
|---------------|-----------|-----|
| **Array** | Nearly all problems | Primary data container |
| **Prefix Sum Array** | Running Sum | O(1) range sum queries |
| **2D Array / Matrix** | Richest Customer, Diagonal Sum, Transpose | Row-column indexed data |
| **Min-Heap / Max-Heap** | Kth Largest, Third Maximum | Efficiently track top-K elements |
| **Stack (Monotonic)** | Trapping Rain Water (one approach) | Track decreasing heights to find valleys |
| **List of Intervals** | Merge Intervals | Represent start-end pairs |
| **StringBuilder / String** | First Occurrence in String | String matching operations |

---

## ⚙️ Algorithms Involved

| Algorithm | Problem(s) | Time | Space |
|-----------|-----------|------|-------|
| Prefix Sum Construction | Running Sum | O(n) | O(1) in-place |
| Two-Pointer Convergence | Container With Most Water, Trapping Rain Water | O(n) | O(1) |
| Two-Pointer Read-Write | Remove Duplicates | O(n) | O(1) |
| Binary Search (Standard) | Binary Search | O(log n) | O(1) |
| Binary Search (Bisect Left/Right) | First and Last Position, Search Insert, First Bad Version | O(log n) | O(1) |
| Binary Search (Rotated Array) | Find Minimum in Rotated Sorted Array | O(log n) | O(1) |
| Merge Sort | Sort an Array | O(n log n) | O(n) |
| Quickselect | Kth Largest Element | O(n) avg | O(1) |
| Heap-based Selection | Kth Largest, Third Maximum | O(n log k) | O(k) |
| Counting Sort | Height Checker | O(n + k) | O(k) |
| Interval Merging (Greedy) | Merge Intervals | O(n log n) | O(n) |
| KMP String Matching | First Occurrence | O(n + m) | O(m) |

---

## ⏱ Time & Space Complexity Patterns

| Problem | Time | Space | Key Insight |
|---------|------|-------|-------------|
| Running Sum | O(n) | O(1) in-place | Modify array in-place |
| Average Salary | O(n) | O(1) | Single pass, track min/max/sum |
| Even Digit Numbers | O(n × d) | O(1) | d = digits per number |
| Remove Duplicates | O(n) | O(1) | In-place two-pointer |
| Container With Most Water | O(n) | O(1) | Greedy two-pointer |
| Trapping Rain Water | O(n) | O(1) two-pointer / O(n) DP | Multiple approaches |
| Richest Customer | O(m × n) | O(1) | Sum each row |
| Matrix Diagonal Sum | O(n) | O(1) | Single pass over diagonals |
| Transpose Matrix | O(m × n) | O(m × n) | New matrix required |
| Find Min in Rotated Array | O(log n) | O(1) | Modified binary search |
| Binary Search | O(log n) | O(1) | Standard |
| First Bad Version | O(log n) | O(1) | Binary search on predicate |
| Search Insert Position | O(log n) | O(1) | Bisect-left |
| First and Last Position | O(log n) | O(1) | Two binary searches |
| Sort an Array | O(n log n) | O(n) for merge sort | Comparison-based lower bound |
| Kth Largest | O(n) avg | O(1) | Quickselect |
| Merge Intervals | O(n log n) | O(n) | Sort dominates |

**Themes:**
- **O(log n) means binary search.** Whenever you see O(log n) in the expected complexity, think binary search.
- **O(n) with O(1) space means two-pointer or single-pass.** These problems test your ability to avoid extra data structures.
- **O(n log n) is the lower bound for comparison-based sorting.** You can't do better with comparisons alone.
- **Heap gives O(n log k) for top-K problems.** Better than full sorting when k << n.

---

## ⚠️ Common Mistakes

### Binary Search Pitfalls
- **Infinite loops:** Using `lo <= hi` vs `lo < hi` — the loop condition must match how you update lo and hi. If you use `lo <= hi`, you must narrow the range by setting `lo = mid + 1` or `hi = mid - 1` (never `hi = mid`). If you use `lo < hi`, you can set `hi = mid`.
- **Integer overflow in midpoint:** `(lo + hi) / 2` can overflow. Use `lo + (hi - lo) / 2` instead.
- **Off-by-one when searching for boundaries:** First/Last position requires careful handling of when `arr[mid] == target` — do you continue searching left or right?
- **Rotated array confusion:** Forgetting to compare mid with the *right* endpoint (not the left) to determine which half is sorted.

### Two-Pointer Mistakes
- **Moving the wrong pointer:** In Container With Most Water, always move the pointer at the shorter line.
- **Not handling duplicates in Remove Duplicates:** The write pointer should only advance when a new distinct value is found.

### Sorting Mistakes
- **Using O(n²) sort when O(n log n) is required:** Bubble sort or insertion sort will TLE on large inputs.
- **Quicksort worst case:** Already sorted input + always picking first/last as pivot → O(n²). Solution: randomized pivot.
- **Forgetting stability requirements:** Merge sort is stable; quicksort and heapsort are not.

### Trapping Rain Water
- **Confusing the formula:** Water at position i = min(maxLeft, maxRight) - height[i], NOT max.
- **Negative water:** If height[i] is taller than the minimum of the two maxes, water = 0 (not negative). Clamp to 0.

### Merge Intervals
- **Not sorting first:** Without sorting by start time, you can't merge in a single pass.
- **Incorrect merge condition:** Overlap occurs when current.start ≤ previous.end (not strictly less than).

### Kth Largest
- **Confusing "Kth largest" with "Kth smallest."** Kth largest in a sorted-ascending array is at index n - k.
- **Not handling duplicates:** "Third maximum" asks for the third *distinct* maximum.

---

## 🔁 How Problems Connect to Each Other

```
┌─────────────────────────────────────────────────────┐
│               BINARY SEARCH CLUSTER                  │
│                                                      │
│  Binary Search (foundation)                          │
│       │                                              │
│       ├── Search Insert Position (bisect-left)       │
│       ├── First Bad Version (predicate search)       │
│       ├── First & Last Position (bisect-left/right)  │
│       └── Min in Rotated Array (modified invariant)  │
│                                                      │
│  ALL share the core "halve the search space" logic.  │
│  They differ in what comparison to make at mid.      │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│              TWO-POINTER CLUSTER                     │
│                                                      │
│  Remove Duplicates (read-write pointer)              │
│  Container With Most Water (converging pointers)     │
│  Trapping Rain Water (converging pointers + state)   │
│                                                      │
│  Progression: Simple → Medium → Hard                 │
│  Same technique, increasing constraints              │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│              SORTING + SELECTION CLUSTER              │
│                                                      │
│  Sort an Array → Height Checker (uses sorted copy)   │
│  Sort an Array → Merge Intervals (sort first)        │
│  Sort an Array → Kth Largest (partial sort idea)     │
│  Third Maximum ←→ Kth Largest (same concept, K=3)    │
│                                                      │
│  Sorting is the prerequisite; selection refines it.  │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│              MATRIX CLUSTER                          │
│                                                      │
│  Richest Customer (row sums)                         │
│  Matrix Diagonal Sum (diagonal traversal)            │
│  Transpose Matrix (index swap: [i][j] → [j][i])     │
│                                                      │
│  All test 2D array indexing fluency.                 │
└─────────────────────────────────────────────────────┘

Running Sum of 1D Array → Foundation for prefix sums
    → Connects to Week 4: Shortest Subarray with Sum at Least K
    
Trapping Rain Water → Appears again in Week 4 (stack-based approach)
    → Deepens understanding across multiple paradigms
```

---

## 🚀 Advanced Insights

1. **Binary Search Template Unification:** All binary search variants can be unified into a single template: "Find the smallest index i such that condition(i) is true." The condition changes per problem:
   - Standard search: arr[i] >= target (for leftmost)
   - First Bad Version: isBadVersion(i) == true
   - Search Insert: arr[i] >= target
   - Rotated Min: compare arr[mid] with arr[hi]

2. **Trapping Rain Water as a Bridge Problem:** This single problem connects four different paradigms: brute force (O(n²)), DP with precomputation (O(n) time, O(n) space), two-pointer (O(n) time, O(1) space), and monotonic stack (O(n) time, O(n) space). Understanding all four approaches for one problem is a masterclass in optimization.

3. **Quickselect and the Median of Medians:** While Quickselect is O(n) on average, worst case is O(n²). The Median of Medians algorithm guarantees O(n) worst case but is rarely implemented in interviews due to complexity. Know it exists conceptually.

4. **From Merge Sort to Merge Intervals:** Merge Sort's merge step and Merge Intervals share the same "two-finger" merge logic. The sorted order + linear scan pattern is foundational.

5. **Counting Sort unlocks O(n) for constrained inputs:** When values are bounded (e.g., heights 1-100 in Height Checker), counting sort beats the O(n log n) comparison lower bound.

---
---

# 📅 WEEK 3 — Object-Oriented Design, HashMap Patterns & System Design

## Problems Covered

| # | Problem | Category |
|---|---------|----------|
| 1 | Simple Bank System | OOP Design |
| 2 | Design Twitter | OOP + Data Structure Design |
| 3 | Encode and Decode TinyURL | Design / Hashing |

---

## 📌 Core Topics Covered

### 1. Object-Oriented Programming Principles

#### Encapsulation
- **What:** Bundling data (fields) and behavior (methods) together within a class, while restricting direct access to internal details.
- **How:** Use `private` fields with `public` getters/setters. Expose behavior, not data.
- **Bank System example:** Account balances should be private. External code interacts through `deposit()`, `withdraw()`, `transfer()` — never by directly modifying the balance variable.
- **Why it matters:** Prevents invalid states. A `withdraw()` method can enforce that balance never goes negative; direct field access cannot.

#### Abstraction
- **What:** Hiding complex implementation details behind simple interfaces.
- **TinyURL example:** The caller only sees `encode(url)` → shortUrl and `decode(shortUrl)` → url. They don't know if you're using a hash map, a database, a counter, or a hash function internally.
- **Design Twitter:** The user calls `getNewsFeed(userId)`. They don't know if it's a merge of sorted lists, a priority queue, or a pre-computed cache.

#### Polymorphism
- **What:** Different classes responding to the same method signature in different ways.
- **Runtime polymorphism (method overriding):** A `User` interface could have `VIPUser` and `RegularUser` implementations with different behavior for `getTransactionLimit()`.
- **Compile-time polymorphism (method overloading):** Multiple `transfer()` methods with different parameter sets.

#### Inheritance
- **What:** A class derives properties and behavior from a parent class.
- **When to use:** "Is-A" relationship. A `SavingsAccount` IS-A `BankAccount`.
- **When NOT to use:** "Has-A" relationship should use composition. A `Bank` HAS accounts — it should contain a list of accounts, not extend an account.
- **Favor composition over inheritance** — this is a fundamental OOD principle.

### 2. Class Design Strategy

#### Identifying Classes
- **Noun Analysis:** Read the problem. Every significant noun is a potential class: Bank, Account, User, Tweet, Feed, URL.
- **Responsibility Assignment:** Each class should have exactly one reason to change (Single Responsibility Principle).

#### Identifying Methods
- **Verb Analysis:** Every action described in the problem is a potential method: deposit, withdraw, transfer, postTweet, follow, encode, decode.

#### Identifying Fields
- **State Analysis:** What data does each class need to remember? Bank needs accounts. Twitter needs users, tweets, follow relationships.

### 3. Interface Design
- **Define contracts:** An interface declares *what* a class must do, not *how*.
- **TinyURL Codec interface:** Must expose `encode(String longUrl)` and `decode(String shortUrl)`.
- **Program to interfaces, not implementations:** Declare variables as `Map`, not `HashMap`. This allows changing the implementation without changing client code.

### 4. SOLID Principles

| Principle | Meaning | Application |
|-----------|---------|-------------|
| **S** — Single Responsibility | A class should have only one reason to change | Bank class handles bank operations; Account class handles account-level operations. Don't combine them. |
| **O** — Open/Closed | Open for extension, closed for modification | Add new account types by creating new subclasses, not by modifying the existing Account class. |
| **L** — Liskov Substitution | Subclasses should be usable in place of their parent class | If `transfer()` works with `Account`, it should work identically with `SavingsAccount` or `CheckingAccount`. |
| **I** — Interface Segregation | Don't force classes to implement methods they don't use | Separate `Readable` and `Writable` interfaces instead of one large `FileOperations` interface. |
| **D** — Dependency Inversion | Depend on abstractions, not concretions | Bank should depend on an `AccountRepository` interface, not a specific `MySQLAccountStore`. |

### 5. HashMap Usage Patterns

#### Pattern A: Direct Lookup Table
- Map account number → account object (Bank)
- Map short URL → long URL (TinyURL)
- O(1) average lookup, insertion, deletion

#### Pattern B: Adjacency List / Relationship Mapping
- Map userId → Set of followeeIds (Twitter)
- Map userId → List of Tweets (Twitter)
- Models one-to-many and many-to-many relationships

#### Pattern C: Counter / Frequency Map
- Map character → count (common in string problems)
- Foundation for many algorithmic problems

#### Pattern D: Bidirectional Mapping
- Map long URL → short URL AND short URL → long URL (TinyURL)
- Two maps maintained in sync

### 6. Designing Scalable Systems

#### Simple Bank System — Design Thinking
- **State:** Array or HashMap of accounts with balances
- **Validation:** Every operation must validate: Does the account exist? Is there sufficient balance? Is the amount positive?
- **Atomicity:** A transfer is TWO operations (withdraw + deposit). If withdraw succeeds but deposit fails, the system is in an inconsistent state. Think about transactional integrity.
- **Thread Safety (advanced):** What if two threads transfer from the same account simultaneously?

#### Design Twitter — Design Thinking
- **Core entities:** User, Tweet (with timestamp)
- **Relationships:** User follows User (many-to-many)
- **News Feed:** The hardest part. Merge the most recent tweets from all followees. This is a "merge K sorted lists" problem — use a priority queue (max-heap) ordered by timestamp.
- **Edge cases:** A user's own tweets appear in their feed. Unfollowing removes future tweets from the feed but the tweet still exists. Cannot follow/unfollow yourself.

#### Encode/Decode TinyURL — Design Thinking
- **Approach 1: Counter-based.** Maintain a global counter. Each new URL gets the next integer, converted to base-62 (a-z, A-Z, 0-9) for a short code.
- **Approach 2: Hashing.** Hash the long URL to produce a short code. Handle collisions.
- **Approach 3: Random key.** Generate a random 6-character string. Check for collisions. Retry if collision occurs.
- **Tradeoff:** Counter is predictable (security issue) but collision-free. Hashing can collide. Random is unpredictable but must verify uniqueness.

### 7. Handling State
- **Mutable state** must be managed carefully. Every public method that modifies state should validate inputs and maintain invariants.
- **Initialization:** Constructors set up the initial state. Bank constructor creates accounts with initial balances. Twitter constructor initializes empty data structures.
- **State transitions:** Document valid state transitions. An account's balance can increase (deposit) or decrease (withdraw), but never go below zero.

### 8. Object Relationships
- **Association:** A Bank *has* Accounts (one-to-many)
- **Dependency:** A Transfer *uses* two Accounts
- **Aggregation:** Twitter *has* Users, but Users exist independently of Twitter
- **Composition:** A Tweet *belongs to* a User and doesn't exist without one

### 9. Real-World Modeling
- OOP design problems test your ability to map a real-world domain into classes, methods, and relationships
- The key skill: **identifying the right level of abstraction** — not too granular, not too coarse
- Ask: "What are the ENTITIES? What are the ACTIONS? What are the RELATIONSHIPS? What are the CONSTRAINTS?"

---

## 🧠 Patterns & Thinking Models

### Pattern 1: Entity-Relationship Modeling
- Identify entities (nouns) → classes
- Identify actions (verbs) → methods
- Identify relationships (has-a, is-a, uses-a) → composition, inheritance, dependency
- **Thinking Model:** "If I were building this for a real product, what objects would I create?"

### Pattern 2: HashMap as the Core Data Structure
- Almost every design problem in interviews relies heavily on HashMaps
- The key question is: "What do I need to look up quickly?"
- **Thinking Model:** "What queries will the system receive, and what data structure gives O(1) for those queries?"

### Pattern 3: Priority Queue for Ordered Retrieval
- Design Twitter's `getNewsFeed()` requires merging and ordering
- A max-heap by timestamp gives you the most recent tweets efficiently
- **Thinking Model:** "Do I need the 'top K' or 'most recent K' of something? Use a heap."

### Pattern 4: Input Validation as the First Step
- Every public method should validate inputs before processing
- Return false / throw exception for invalid inputs
- **Thinking Model:** "What could go wrong? Account doesn't exist? Amount is negative? Insufficient balance?"

---

## 📊 Data Structures Used

| Data Structure | Where Used | Why |
|---------------|-----------|-----|
| **HashMap<Integer, Long>** | Bank System | Account ID → balance mapping |
| **HashMap<Integer, Set<Integer>>** | Design Twitter | User → followees |
| **HashMap<Integer, List<Tweet>>** | Design Twitter | User → their tweets |
| **PriorityQueue (Max-Heap)** | Design Twitter | Merge K most recent tweets |
| **HashMap<String, String>** | TinyURL | Short ↔ Long URL mapping |
| **Array** | Bank System (alternative) | Index-based account access |
| **LinkedList / List** | Design Twitter | Ordered tweet storage per user |

---

## ⚙️ Algorithms Involved

| Algorithm | Problem | Notes |
|-----------|---------|-------|
| HashMap CRUD | All three problems | Insert, lookup, update, delete in O(1) avg |
| Merge K Sorted Lists | Design Twitter (getNewsFeed) | Use priority queue to merge tweet streams |
| Hashing / Encoding | TinyURL | Convert between representations |
| Base Conversion | TinyURL (counter approach) | Convert integer to base-62 string |

---

## ⏱ Time & Space Complexity Patterns

| Operation | Time | Space |
|-----------|------|-------|
| Bank: deposit/withdraw/transfer | O(1) | O(n) for n accounts |
| Twitter: postTweet | O(1) | O(total tweets) |
| Twitter: getNewsFeed | O(K log K) where K = followees × tweets | O(K) for heap |
| Twitter: follow/unfollow | O(1) | O(users × followees) |
| TinyURL: encode | O(1) amortized | O(n) for n URLs |
| TinyURL: decode | O(1) | Already stored |

---

## ⚠️ Common Mistakes

### OOP Mistakes
- **God class:** Putting everything in one class instead of separating concerns
- **Public fields:** Exposing internal state directly instead of through methods
- **Ignoring edge cases in validation:** Not checking for null, negative amounts, non-existent accounts
- **Mixing responsibilities:** Bank class shouldn't handle printing or UI logic

### Bank System Mistakes
- **Integer overflow:** Account balances should be `long`, not `int`
- **Not validating account existence** before performing operations
- **Not checking sufficient funds** before withdrawal/transfer
- **1-indexed accounts:** The problem often uses 1-indexed accounts but arrays are 0-indexed

### Twitter Mistakes
- **Forgetting self-tweets in feed:** A user sees their own tweets in their news feed
- **Following/unfollowing self:** Users shouldn't be able to follow themselves
- **Tweet ordering:** Tweets must be returned in reverse chronological order
- **Not limiting feed size:** The feed typically returns only the 10 most recent tweets

### TinyURL Mistakes
- **Collision handling:** If two different long URLs hash to the same short URL, you have a collision
- **Not maintaining bidirectional mapping:** Need to check if a long URL was already encoded to avoid generating multiple short URLs for the same long URL
- **Using predictable encoding:** Sequential counters are guessable — security concern

---

## 🔁 How Problems Connect to Each Other

```
┌────────────────────────────────────────────────────┐
│              DESIGN PROBLEM CONNECTIONS              │
│                                                     │
│  Simple Bank System                                 │
│    ├── HashMap for state management                 │
│    ├── Validation patterns                          │
│    └── Encapsulation + Single Responsibility        │
│                                                     │
│  Design Twitter                                     │
│    ├── HashMap for relationships (follow graph)     │
│    ├── Priority Queue for feed (merge K sorted)     │
│    ├── Object relationships (User has Tweets)       │
│    └── Multiple data structures coordinated         │
│                                                     │
│  Encode/Decode TinyURL                              │
│    ├── HashMap for bidirectional mapping             │
│    ├── Abstraction (hide encoding strategy)          │
│    └── Interface design (codec contract)             │
│                                                     │
│  COMMON THREAD: HashMap is the backbone of all      │
│  three problems. Design = choosing the right maps.  │
└────────────────────────────────────────────────────┘
```

- **Bank → Twitter:** Both manage entities with IDs. Bank maps accountId → balance; Twitter maps userId → data. The pattern of "ID-based lookup" is identical.
- **Twitter → TinyURL:** Both require generating unique identifiers. Twitter generates tweetIds; TinyURL generates short codes.
- **All three problems** test the ability to maintain consistent state across multiple operations.

---

## 🚀 Advanced Insights

1. **Design Twitter is a System Design Gateway:** The `getNewsFeed()` method is essentially a simplified version of the "Fan-out on read" vs "Fan-out on write" debate in real-world system design. Understanding this connection prepares you for system design interviews.

2. **TinyURL and Hash Functions:** Understanding collision resolution (open addressing, chaining) and hash distribution quality is fundamental to computer science. TinyURL is a gentle introduction to distributed systems concepts like URL shortening services (think Bitly architecture).

3. **Defensive Programming:** All three problems reward defensive coding — checking preconditions, validating inputs, handling edge cases. This is not just about passing test cases; it's about writing production-quality code.

4. **The Power of Choosing the Right Data Structure:** Design Twitter can be solved poorly (brute force merge) or elegantly (heap-based merge). The algorithm quality is directly determined by the data structure choice.

5. **Immutable vs. Mutable Design:** Consider whether tweets should be mutable. In Twitter's design, tweets are immutable once posted (you can delete but not edit — historically). This design choice simplifies concurrency and caching.

---
---

# 📅 WEEK 4 — Linked Lists, Stacks, Queues, Graphs & Advanced Patterns

## Problems Covered

| # | Problem | Category |
|---|---------|----------|
| 1 | Merge Two Sorted Lists | Linked List |
| 2 | Remove Linked List Elements | Linked List |
| 3 | Middle of Linked List | Linked List |
| 4 | Palindrome Linked List | Linked List |
| 5 | Intersection of Two Linked Lists | Linked List |
| 6 | Rotate List | Linked List |
| 7 | Baseball Game | Stack |
| 8 | Trapping Rain Water | Monotonic Stack |
| 9 | Decode String | Stack |
| 10 | Number of Students Unable to Eat Lunch | Queue |
| 11 | 01 Matrix | BFS / Graph |
| 12 | Shortest Subarray with Sum at Least K | Deque / Prefix Sum |

---

## 📌 Core Topics Covered

### 1. Linked List Fundamentals

#### What Makes Linked Lists Different from Arrays
- **No random access:** You cannot jump to index i in O(1). You must traverse from head.
- **Dynamic size:** No need to pre-allocate. Insertion/deletion at a known position is O(1) (pointer manipulation only).
- **Node structure:** Each node contains data + a pointer to the next node (singly linked) or both next and prev (doubly linked).
- **Memory:** Nodes are scattered in memory (not contiguous), which means poor cache locality compared to arrays.

#### The Dummy Node Technique
- **What:** Create a fake node before the actual head: `dummy.next = head`
- **Why:** Eliminates special-case handling for the head node. When the head itself might be removed (Remove Linked List Elements) or when you're building a new list (Merge Two Sorted Lists), a dummy node simplifies the logic enormously.
- **Pattern:** Create dummy → operate → return `dummy.next`

#### Slow/Fast Pointer (Floyd's Technique)
- **Middle of Linked List:** Slow pointer moves 1 step, fast pointer moves 2 steps. When fast reaches the end, slow is at the middle.
- **Why it works:** Fast covers the list at twice the speed. When fast has traversed the full list, slow has traversed exactly half.
- **Cycle Detection (extension):** If a cycle exists, fast and slow will eventually meet inside the cycle.
- **Palindrome Linked List:** Use slow/fast to find the middle, reverse the second half, then compare the two halves node by node.

#### Linked List Reversal
- **In-place reversal:** Maintain three pointers: `prev`, `curr`, `next`. At each step: save next, point curr.next to prev, advance prev and curr.
- **Palindrome check requires reversal:** Reverse the second half, compare with the first half.
- **Partial reversal:** Sometimes you only reverse a sublist (e.g., between positions m and n).

#### Intersection of Two Linked Lists
- **Core Insight:** If two lists intersect, they share a common tail. The length difference is the key.
- **Two-pointer technique:** Pointer A starts at headA, pointer B starts at headB. When A reaches the end, redirect to headB. When B reaches the end, redirect to headA. They will meet at the intersection (or both reach null if no intersection).
- **Why it works:** After switching, both pointers traverse the same total distance: lengthA + lengthB. The length difference is absorbed by the switch.

#### Rotate List
- **Core Insight:** Rotation by k is equivalent to making the (n-k)th node the new tail and the (n-k+1)th node the new head.
- **Key step:** Connect the old tail to the old head (forming a cycle), then break the cycle at the right position.
- **Edge case:** k can be larger than n. Always compute k % n first.

### 2. Stack-Based Problems

#### Stack Fundamentals
- **LIFO:** Last In, First Out
- **Operations:** push (add to top), pop (remove from top), peek (view top), isEmpty
- **When to use:** When you need to process elements in reverse order, match pairs, or track "most recent" state.

#### Baseball Game — Direct Stack Application
- A sequence of operations modifies scores. "+" sums the last two, "D" doubles the last, "C" removes the last.
- The stack naturally tracks the "most recent" scores. Each operation queries or modifies the top of the stack.

#### Decode String — Nested Stack Application
- Input like "3[a2[c]]" decodes to "accaccacc"
- **Key insight:** Brackets can be nested. A stack naturally handles nesting.
- **What goes on the stack:** The current string and the current repeat count, pushed when entering a '['. Popped and assembled when encountering ']'.
- **Mental model:** Each '[' pushes a new "context" onto the stack. Each ']' pops and resolves one level of nesting.

#### Trapping Rain Water — Monotonic Stack Approach
- **Monotonic decreasing stack:** Maintains indices of bars in decreasing height order.
- **When you encounter a bar taller than the stack top:** The top of the stack is a "valley floor." Pop it. The trapped water above that bar is bounded by the current bar and the new stack top.
- **Why monotonic stack works:** It efficiently finds the nearest taller element on both sides, which defines the water boundaries.

### 3. Queue Patterns

#### Queue Fundamentals
- **FIFO:** First In, First Out
- **Operations:** offer/enqueue (add to back), poll/dequeue (remove from front), peek (view front), isEmpty
- **When to use:** Processing elements in order, BFS, simulation problems.

#### Number of Students Unable to Eat Lunch
- **Simulation problem:** Students are in a queue. If the front student doesn't want the top sandwich, they go to the back. If no one wants the top sandwich, stop.
- **Key insight:** If every remaining student in the queue doesn't want the current sandwich, we're done. One complete cycle through the queue without anyone eating = termination.
- **The queue data structure naturally models the circular behavior of students going to the back of the line.

### 4. Monotonic Stack (Deep Dive)

#### What is a Monotonic Stack?
- A stack that maintains its elements in strictly increasing or decreasing order
- Before pushing a new element, pop all elements that violate the monotonic property
- This gives you, for free, the "nearest greater/smaller element" relationship

#### Monotonic Decreasing Stack (used in Trapping Rain Water)
- Stack maintains elements in decreasing order (bottom to top)
- When a new element is larger than the top, pop — the popped element has found its "next greater element" (the new element being pushed)
- Applications: trapping rain water, largest rectangle in histogram, daily temperatures

#### Monotonic Increasing Stack
- Stack maintains elements in increasing order
- When a new element is smaller than the top, pop — the popped element has found its "next smaller element"
- Applications: stock span, next greater element problems

### 5. BFS (Breadth-First Search)

#### Core Concept
- **Level-by-level exploration:** BFS visits all nodes at distance d before visiting any node at distance d+1.
- **Data structure:** Queue-based. Add starting node(s) to the queue. While the queue is not empty, dequeue a node, process it, and enqueue all unvisited neighbors.
- **Shortest path guarantee:** In unweighted graphs (or grids), BFS finds the shortest path from source to any reachable node.

#### 01 Matrix
- **Problem:** Find the distance of each cell to the nearest 0.
- **Multi-source BFS:** Instead of running BFS from each 1 cell (expensive), start BFS simultaneously from ALL 0 cells. Add all 0 cells to the queue initially (distance = 0). Then expand outward level by level. The first time you reach a 1 cell, that's its minimum distance.
- **Why multi-source:** Single-source BFS from each 0 is redundant. Multi-source BFS processes the entire grid in one pass.
- **Grid BFS specifics:** Four directions (up, down, left, right). Check bounds. Use a visited matrix or modify the grid in-place.

### 6. Prefix Sum + Deque

#### Shortest Subarray with Sum at Least K
- **This is the hardest problem in the entire 4-week set.**
- **Why it's hard:** Combines prefix sums with a monotonic deque. The array can contain negative numbers, which invalidates simpler sliding window approaches.
- **Prefix sum foundation:** Compute prefix[i] = sum of first i elements. Subarray sum from j to i = prefix[i] - prefix[j].
- **The goal:** Find the shortest subarray where prefix[i] - prefix[j] >= K.
- **Why deque:** Maintain a deque of indices where prefix values are in increasing order. This allows:
  1. **Remove from front:** If prefix[i] - prefix[deque.front] >= K, we've found a valid subarray. Record its length and pop the front (any future i will only give a longer subarray with this j).
  2. **Remove from back:** If prefix[i] <= prefix[deque.back], the back is useless — a future index will prefer i over deque.back because i gives a smaller prefix (larger difference) AND a shorter subarray.
- **This is a monotonic deque pattern:** increasing order of prefix values, used to efficiently find the optimal starting index.

### 7. Sliding Window (Conceptual Connection)
- Shortest Subarray with Sum at Least K is related to the sliding window technique, but the presence of negative numbers means the window can't just expand/contract greedily.
- **Standard sliding window (all positive):** Expand right end to grow, shrink left end to reduce. Works because adding elements always increases the sum.
- **With negatives:** The monotonicity is broken. The deque-based approach is the generalization that handles this.

### 8. Graph Traversal Concepts
- **01 Matrix is a graph problem in disguise:** Each cell is a node, adjacent cells are edges, all edges have weight 1.
- **BFS on grids:** The grid IS the graph. 4-directional adjacency defines the edges.
- **Distance calculation:** BFS level = distance from source(s).
- **Visited tracking:** Essential to avoid infinite loops. Mark cells as visited when they are enqueued (not when they are processed — this is a common BFS bug).

### 9. Memory Handling in Linked Structures
- **In languages with garbage collection (Java):** When you remove a node, set its pointers to null to allow GC. Though not strictly necessary, it's good practice and shows awareness.
- **Linked list operations create/destroy node references:** When reversing a list, you're not moving data — you're rewiring pointers. The nodes stay in memory; only the `.next` references change.
- **Side effects:** Palindrome check by reversing the second half MODIFIES the original list. If you need to preserve the original, reverse it back after checking.

---

## 🧠 Patterns & Thinking Models

### Pattern 1: Slow/Fast Pointer
- Find middle: slow (1 step), fast (2 steps)
- Detect cycle: same speeds, they meet if cycle exists
- Find cycle start: reset one pointer to head, move both at speed 1
- **Thinking Model:** "Do I need to find a position that's a fraction of the list length without knowing the length?"

### Pattern 2: Dummy Node
- Simplifies head manipulation
- Use whenever the head might change or when building a new list
- **Thinking Model:** "Will the head of my result list be unclear until I process the input? Use a dummy."

### Pattern 3: In-Place Reversal
- Three pointers: prev, curr, next_temp
- Iterate through the list, reversing each pointer
- **Thinking Model:** "Do I need to traverse backwards in a singly linked list? Reverse it first."

### Pattern 4: Stack for Matching / Nesting
- Parentheses matching, bracket decoding, expression evaluation
- Each opening delimiter pushes context; each closing delimiter pops and resolves
- **Thinking Model:** "Does this problem involve nested or paired structures?"

### Pattern 5: Monotonic Stack for Nearest Greater/Smaller
- Maintain sorted order in the stack
- Pop elements when the monotonic property is violated — the popped element's "answer" is the current element
- **Thinking Model:** "Do I need the nearest larger/smaller element for each position?"

### Pattern 6: Multi-Source BFS
- Initialize BFS with ALL source nodes in the queue
- Expands outward uniformly from all sources simultaneously
- Finds shortest distance from ANY source
- **Thinking Model:** "Do I need the shortest distance from a SET of sources, not just one?"

### Pattern 7: Monotonic Deque for Sliding Window Optimization
- Maintains candidates in sorted order
- Efficiently removes suboptimal candidates from both ends
- **Thinking Model:** "Is this a sliding window problem where I need to track min/max or optimal starting points efficiently?"

### Pattern 8: Queue for Simulation
- Real-world processes that follow first-come-first-served can be modeled with queues
- **Thinking Model:** "Is the problem simulating a real-world line or process?"

---

## 📊 Data Structures Used

| Data Structure | Where Used | Why |
|---------------|-----------|-----|
| **Singly Linked List** | Merge, Remove, Middle, Palindrome, Intersection, Rotate | Core data structure under study |
| **Dummy Node** | Merge Two Sorted Lists, Remove Elements | Simplifies head handling |
| **Stack** | Baseball Game, Decode String, Trapping Rain Water | LIFO processing, nesting |
| **Queue** | Students Unable to Eat, BFS (01 Matrix) | FIFO processing, level-order traversal |
| **Deque (Double-Ended Queue)** | Shortest Subarray with Sum at Least K | Remove from both ends efficiently |
| **Monotonic Stack** | Trapping Rain Water | Next greater element pattern |
| **Monotonic Deque** | Shortest Subarray | Sliding window min/max |
| **Prefix Sum Array** | Shortest Subarray | O(1) subarray sum queries |
| **2D Grid as Graph** | 01 Matrix | Implicit graph, BFS traversal |
| **Boolean/Visited Matrix** | 01 Matrix | Track visited cells in BFS |

---

## ⚙️ Algorithms Involved

| Algorithm | Problem(s) | Time | Space |
|-----------|-----------|------|-------|
| Linked List Merge (Two-Pointer) | Merge Two Sorted Lists | O(n + m) | O(1) |
| Linked List Traversal + Deletion | Remove Linked List Elements | O(n) | O(1) |
| Slow/Fast Pointer | Middle of Linked List | O(n) | O(1) |
| Reverse Linked List + Compare | Palindrome Linked List | O(n) | O(1) |
| Two-Pointer Length Equalization | Intersection of Two Linked Lists | O(n + m) | O(1) |
| Linked List Rotation (Cycle + Break) | Rotate List | O(n) | O(1) |
| Stack Simulation | Baseball Game | O(n) | O(n) |
| Monotonic Stack | Trapping Rain Water | O(n) | O(n) |
| Stack-based Decoding | Decode String | O(n × max_k) | O(n) |
| Queue Simulation | Students Unable to Eat | O(n²) worst | O(n) |
| Multi-Source BFS | 01 Matrix | O(m × n) | O(m × n) |
| Prefix Sum + Monotonic Deque | Shortest Subarray ≥ K | O(n) | O(n) |

---

## ⏱ Time & Space Complexity Patterns

| Problem | Time | Space | Key Insight |
|---------|------|-------|-------------|
| Merge Two Sorted Lists | O(n + m) | O(1) | Just rewire pointers |
| Remove Linked List Elements | O(n) | O(1) | Single pass with dummy |
| Middle of Linked List | O(n) | O(1) | One pass with two pointers |
| Palindrome Linked List | O(n) | O(1) | Find mid + reverse + compare |
| Intersection of Two Lists | O(n + m) | O(1) | Length equalization trick |
| Rotate List | O(n) | O(1) | Cycle + break, k % n |
| Baseball Game | O(n) | O(n) | One op per token |
| Trapping Rain Water | O(n) | O(n) stack / O(1) two-ptr | Multiple approaches |
| Decode String | O(output length) | O(output length) | Stack of contexts |
| Students Unable to Eat | O(n²) worst | O(n) | Simulation termination |
| 01 Matrix | O(m × n) | O(m × n) | Each cell processed once |
| Shortest Subarray ≥ K | O(n) | O(n) | Each index enters/leaves deque once |

**Themes:**
- **Linked list problems are almost always O(n) time, O(1) space.** The whole point of linked list problems is operating with minimal extra space by manipulating pointers.
- **Stack/Queue problems are O(n) time, O(n) space.** The stack/queue itself is the extra space.
- **BFS on grids is O(m × n).** Every cell is processed exactly once.
- **Monotonic stack/deque achieves amortized O(n):** Each element enters and leaves at most once.

---

## ⚠️ Common Mistakes

### Linked List Mistakes
- **Losing the head reference:** If you advance the head pointer without saving it first, you've lost the list. This is why dummy nodes are essential.
- **Not handling empty lists:** If head is null, your code should handle it gracefully.
- **Null pointer exceptions:** Always check `node != null` before accessing `node.next`.
- **Cycle creation:** When rotating, you intentionally create a cycle. **Forgetting to break it** results in an infinite loop.
- **Off-by-one in slow/fast pointer:** For even-length lists, which "middle" node does the slow pointer land on? It matters for palindrome checking — you need to be consistent.
- **Not restoring the list after reversal:** Palindrome check reverses half the list. If the problem (or a later test) expects the original list, you must reverse it back.

### Stack Mistakes
- **Accessing top of empty stack:** Always check isEmpty() before pop() or peek().
- **Decode String — incorrect nesting management:** Each '[' must push BOTH the current string and the current multiplier. Missing one leads to incorrect assembly.
- **Trapping Rain Water — monotonic stack direction:** The stack should be monotonically decreasing by height. If you use increasing, the logic inverts and is usually wrong.

### Queue Mistakes
- **Students Unable to Eat — termination condition:** The simulation ends when a complete rotation happens without any student eating. Not when the queue is empty (it might never empty).
- **BFS — marking visited at wrong time:** Mark a cell as visited when ENQUEUING, not when DEQUEUING. If you mark when dequeuing, a cell can be enqueued multiple times, causing TLE and incorrect results.

### BFS Mistakes (01 Matrix)
- **Starting BFS from 1 cells instead of 0 cells:** Multi-source BFS from 0 cells is O(m × n). Running BFS from each 1 cell separately is O(m × n × number_of_1s) — far worse.
- **Not initializing distances correctly:** Set distance of 0 cells to 0 and 1 cells to infinity (or -1) initially.
- **Forgetting boundary checks:** Before accessing grid[r][c], verify 0 ≤ r < rows and 0 ≤ c < cols.

### Shortest Subarray ≥ K Mistakes
- **Thinking it's a simple sliding window:** Negative numbers break the sliding window invariant. You MUST use the monotonic deque approach.
- **Deque operations order:** First, remove satisfied subarrays from the front. Then, remove suboptimal prefixes from the back. Then, add the current index.
- **Off-by-one with prefix sums:** The prefix array has n+1 elements (prefix[0] = 0). Indexing errors here are common.

---

## 🔁 How Problems Connect to Each Other

```
┌─────────────────────────────────────────────────┐
│           LINKED LIST PROGRESSION                │
│                                                  │
│  Merge Two Sorted Lists       (Two-pointer)      │
│       ↓ (uses dummy node)                        │
│  Remove Linked List Elements  (Traversal+Delete) │
│       ↓ (uses dummy node)                        │
│  Middle of Linked List        (Slow/Fast)        │
│       ↓ (slow/fast finds middle)                 │
│  Palindrome Linked List       (Mid + Reverse)    │
│       ↓ (intersection uses two-pointer variant)  │
│  Intersection of Two Lists    (Length equalize)   │
│       ↓ (rotation forms cycle + breaks it)       │
│  Rotate List                  (Cycle + Break)    │
│                                                  │
│  Each problem BUILDS on skills from the previous │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐  
│           STACK PROGRESSION                      │
│                                                  │
│  Baseball Game        (Basic stack ops)           │
│       ↓                                          │
│  Decode String        (Stack for nesting)         │
│       ↓                                          │
│  Trapping Rain Water  (Monotonic stack)           │
│                                                  │
│  Simple → Nested → Advanced monotonic             │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│           BFS + QUEUE CLUSTER                    │
│                                                  │
│  Students Unable to Eat    (Queue simulation)    │
│       ↓ (queue → BFS uses queue)                 │
│  01 Matrix                 (Multi-source BFS)    │
│                                                  │
│  Simple queue → Graph traversal with queue        │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│           PREFIX SUM CHAIN                       │
│  (Spanning Weeks 2 and 4)                        │
│                                                  │
│  Running Sum (Week 2) → Foundation               │
│       ↓                                          │
│  Shortest Subarray ≥ K (Week 4)                  │
│       → Prefix Sum + Monotonic Deque             │
│                                                  │
│  The simplest prefix sum leads to the hardest    │
│  problem in the entire 4-week set.               │
└─────────────────────────────────────────────────┘

CROSS-WEEK CONNECTIONS:
• Valid Palindrome (Week 1) → Palindrome Linked List (Week 4)
  Same concept, different data structure

• Trapping Rain Water (Week 2 two-pointer) → Trapping Rain Water (Week 4 stack)
  Same problem, different approach

• Backtracking recursion (Week 1) → BFS uses similar "explore all paths" thinking (Week 4)
  DFS vs BFS — two sides of the same coin
```

---

## 🚀 Advanced Insights

1. **The Two-Pointer Technique Spans All Data Structures:** In Week 1 (strings), Week 2 (arrays), and Week 4 (linked lists), two-pointer appears in different forms. The underlying principle — reducing search space by moving pointers intelligently — is universal.

2. **Monotonic Stack/Deque as Amortized O(n):** The key insight is that each element enters and exits the stack/deque exactly once across the entire algorithm. Even though individual operations may seem expensive, the TOTAL work across all operations is O(n).

3. **BFS vs. DFS Trade-offs:**
   - BFS: Shortest path guarantee, uses more memory (stores entire level), implemented with queue
   - DFS: No shortest path guarantee (for unweighted), uses less memory (stack depth), implemented with stack or recursion
   - For **distance problems on unweighted graphs, BFS is always the choice.**

4. **Palindrome Linked List is a Synthesis Problem:** It combines three techniques: slow/fast pointer (to find the middle), linked list reversal (to reverse the second half), and comparison (to verify the palindrome). This is how interview problems test multiple skills simultaneously.

5. **Shortest Subarray with Sum at Least K is the Hardest Problem Here:** It requires understanding prefix sums, monotonic deques, and why simpler sliding window fails with negative numbers. Being able to explain WHY the deque works (not just what it does) demonstrates true understanding.

6. **The "Two Passes" Pattern in Linked Lists:** Many linked list problems use two passes — one to gather information (length, find middle, detect intersection), and a second to act on that information. This is because random access is unavailable.

---
---

# 🔥 FULL SKILL TREE THIS TEST COVERS

```
                        ┌──────────────────┐
                        │    FOUNDATIONS     │
                        └────────┬─────────┘
                                 │
            ┌────────────────────┼────────────────────┐
            ▼                    ▼                    ▼
    ┌───────────────┐  ┌─────────────────┐  ┌──────────────────┐
    │  MATHEMATICS   │  │  DATA STRUCTURES │  │   ALGORITHMIC    │
    │                │  │                  │  │   PARADIGMS      │
    │ • Modular Arith│  │ • Array          │  │                  │
    │ • Prime Factors│  │ • Linked List    │  │ • Brute Force    │
    │ • Digital Root │  │ • Stack          │  │ • Divide & Conquer│
    │ • Exponentiation│ │ • Queue/Deque   │  │ • Greedy         │
    │ • Bit Manip    │  │ • Heap          │  │ • Recursion      │
    │ • Combinatorics│  │ • HashMap       │  │ • Backtracking   │
    │ • Catalan Nums │  │ • Matrix (2D)   │  │ • Dynamic Prog   │
    └───────┬───────┘  │ • Graph (Grid)   │  │ • BFS / DFS      │
            │          └────────┬─────────┘  │ • Binary Search  │
            │                   │            │ • Sorting        │
            │                   │            │ • Two Pointers   │
            │                   │            │ • Sliding Window │
            │                   │            │ • Monotonic Stack│
            │                   │            │ • Prefix Sum     │
            │                   │            └────────┬─────────┘
            │                   │                     │
            └───────────────────┼─────────────────────┘
                                │
                        ┌───────▼──────────┐
                        │  DESIGN & OOP     │
                        │                   │
                        │ • Encapsulation   │
                        │ • Abstraction     │
                        │ • Polymorphism    │
                        │ • Inheritance     │
                        │ • SOLID Principles│
                        │ • Class Design    │
                        │ • Interface Design│
                        │ • State Mgmt      │
                        │ • Composition     │
                        └───────┬──────────┘
                                │
                        ┌───────▼──────────┐
                        │  META-SKILLS      │
                        │                   │
                        │ • Pattern Recog   │
                        │ • Complexity Anal │
                        │ • Edge Case Think │
                        │ • Optimization    │
                        │ • Communication   │
                        └──────────────────┘
```

---

# 📚 PREREQUISITE KNOWLEDGE MAP

## Must Know Before Starting

### For Week 1:
- Basic recursion (base case, recursive case)
- Multiplication, division, modulo operations
- What a call stack is
- Basic string operations
- Understanding of exponential growth

### For Week 2:
- Array indexing (0-based)
- Nested loops for matrix traversal
- Understanding of sorted arrays
- Basic inequality reasoning (for two-pointer problems)
- What logarithms are (for binary search complexity)

### For Week 3:
- Java class syntax (fields, methods, constructors)
- Access modifiers (public, private, protected)
- HashMap/HashSet usage in Java
- Basic understanding of interfaces and abstract classes
- Concept of a "contract" in programming

### For Week 4:
- Pointer/reference concepts (what `null` means)
- How memory allocation works for objects
- Queue and Stack interfaces in Java
- 2D array traversal (for grid BFS)
- Concept of a "graph" (nodes and edges)

### Universal Prerequisites:
- Big-O notation (what O(n), O(n²), O(log n), O(n log n) mean)
- Basic Java syntax (loops, conditionals, method signatures)
- Ability to trace through code mentally
- Understanding of recursion vs iteration

---

# 🧠 PATTERN MASTERY CHECKLIST

Check off each pattern as you become comfortable explaining and applying it:

### Mathematical Patterns
- [ ] Closed-form mathematical solutions (Add Digits, Power of Two)
- [ ] Prime factorization analysis (Trailing Zeroes)
- [ ] Binary exponentiation / fast power (Pow(x, n))
- [ ] Bit manipulation for power-of-two checks

### Recursion & Backtracking Patterns
- [ ] Base case + recursive case identification
- [ ] Memoization to eliminate overlapping subproblems
- [ ] Choose → Explore → Un-choose backtracking template
- [ ] Pruning invalid branches early
- [ ] Generating combinations vs. permutations

### Array & String Patterns
- [ ] Prefix sum construction and range queries
- [ ] Two-pointer convergence (opposite ends moving inward)
- [ ] Two-pointer read-write (in-place modification)
- [ ] Sliding window (expand/contract)
- [ ] Matrix traversal (row, column, diagonal, spiral)
- [ ] Matrix transpose index relationship

### Binary Search Patterns
- [ ] Standard binary search for exact match
- [ ] Bisect-left (first occurrence / insertion point)
- [ ] Bisect-right (last occurrence)
- [ ] Binary search on rotated arrays
- [ ] Binary search on a boolean predicate

### Sorting & Selection Patterns
- [ ] Merge sort (divide, sort, merge)
- [ ] Quicksort and pivot selection
- [ ] Quickselect for Kth element in O(n) average
- [ ] Counting sort for bounded ranges
- [ ] Sort-first then greedy scan (Merge Intervals)

### Linked List Patterns
- [ ] Dummy node technique
- [ ] Slow/fast pointer for middle finding
- [ ] In-place linked list reversal
- [ ] Two-pointer for intersection detection
- [ ] Cycle formation and breaking (rotation)
- [ ] Two-pass pattern (gather info, then act)

### Stack & Queue Patterns
- [ ] Stack for simulation (Baseball Game)
- [ ] Stack for nested structure decoding (Decode String)
- [ ] Monotonic decreasing stack (Trapping Rain Water)
- [ ] Monotonic increasing stack (Next Greater Element pattern)
- [ ] Queue for process simulation
- [ ] Monotonic deque for sliding window optimization

### Graph & BFS Patterns
- [ ] BFS with queue for shortest path in unweighted graph
- [ ] Multi-source BFS (01 Matrix)
- [ ] Grid as implicit graph (4-directional adjacency)
- [ ] Visited array to prevent revisiting

### OOP & Design Patterns
- [ ] Encapsulation with private fields + public methods
- [ ] Interface-based design
- [ ] SOLID principles applied correctly
- [ ] HashMap as the core of state management
- [ ] Priority Queue for ordered retrieval
- [ ] Defensive programming with input validation

---

# 🏁 WHAT LEVEL THIS TEST IS

## Overall Assessment: **Intermediate** (with Advanced elements)

| Aspect | Level | Justification |
|--------|-------|---------------|
| Math problems (Week 1) | Beginner–Intermediate | Mostly formula-based, standard patterns |
| Backtracking (Week 1) | Intermediate | Template-based but requires tree thinking |
| Array/Two-Pointer (Week 2) | Intermediate | Trapping Rain Water is a hard problem |
| Binary Search (Week 2) | Intermediate | Rotated array and boundary searches |
| Sorting/Selection (Week 2) | Intermediate | Quickselect is conceptually tricky |
| OOP Design (Week 3) | Intermediate | Design Twitter is a medium-hard design problem |
| Linked Lists (Week 4) | Intermediate | Palindrome LL combines multiple techniques |
| Stack problems (Week 4) | Intermediate | Decode String nesting is moderately complex |
| BFS / Graph (Week 4) | Intermediate | Multi-source BFS is a standard intermediate concept |
| Shortest Subarray ≥ K (Week 4) | **Advanced** | Combines prefix sum + monotonic deque |
| Trapping Rain Water (Weeks 2&4) | **Advanced** | Multiple approaches, deep understanding required |

### Summary:
- **60% Intermediate problems** — core data structures and algorithms applied correctly
- **20% Beginner problems** — warmup / foundation building
- **20% Advanced problems** — requiring synthesis of multiple concepts

### This test prepares you for:
- LeetCode Easy and Medium confidently
- Select LeetCode Hard problems
- Coding interview rounds at mid-level tech companies
- Data structure and algorithm course final exams

---

# 🎯 HOW TO REVISE ALL 4 WEEKS IN 5 DAYS

## Day 1: Mathematics + Recursion + Backtracking (Week 1)

### Morning (2 hours)
- Review all math formulas: trailing zeroes, digital root, power of two bit trick, fast exponentiation
- Practice deriving each formula from first principles — don't just memorize
- Write down the recursion template: base case, recursive case

### Afternoon (2 hours)
- Review the backtracking template: Choose → Explore → Un-choose
- Draw the recursion tree for Combination Sum, Generate Parentheses, and Letter Combinations on paper
- Identify the branching factor and constraints for each
- Review the time complexity of each (Catalan numbers for parentheses)

### Evening (1 hour)
- Review two-pointer for palindrome
- Connect palindrome string to palindrome linked list (preview Week 4)
- Flash-card the O(1) closed-form solutions

---

## Day 2: Arrays + Binary Search + Matrix (Week 2, Part 1)

### Morning (2 hours)
- Master the binary search template with all its variants
- Practice on paper: standard search, bisect-left, bisect-right, rotated array
- Memorize: `lo + (hi - lo) / 2` to avoid overflow
- Know when to use `lo <= hi` vs `lo < hi` and the corresponding update rules

### Afternoon (2 hours)
- Review two-pointer problems: Container With Most Water, Trapping Rain Water, Remove Duplicates
- Understand WHY you move the shorter pointer in Container
- Draw the Trapping Rain Water diagram and trace through both two-pointer and stack approaches
- Review prefix sum concept (Running Sum)

### Evening (1 hour)
- Review matrix problems: diagonal traversal, transpose, row sums
- Quick review of string matching concepts (KMP)

---

## Day 3: Sorting + Selection + Intervals (Week 2, Part 2) + OOP Concepts (Week 3)

### Morning (2 hours)
- Review Merge Sort, Quick Sort, Heap Sort — know the properties of each (stable?, in-place?, worst case?)
- Understand Quickselect: how it achieves O(n) average for Kth element
- Review counting sort for bounded ranges
- Review Merge Intervals: sort → greedy merge

### Afternoon (2 hours)
- Deep-dive on OOP: write out the four principles with examples
- Review SOLID principles — one sentence per principle
- Think through the design of Bank System, Twitter, TinyURL: what classes, what methods, what data structures
- Review HashMap usage patterns: direct lookup, adjacency list, bidirectional mapping

### Evening (1 hour)
- Practice explaining Design Twitter's getNewsFeed as a merge-K-sorted-lists problem
- Review TinyURL encoding strategies: counter vs hash vs random
- Know the tradeoffs of each

---

## Day 4: Linked Lists + Stacks + Queues (Week 4, Part 1)

### Morning (2 hours)
- Practice linked list operations on paper: traversal, insertion, deletion, reversal
- Master the dummy node technique
- Trace through slow/fast pointer for middle finding on lists of even and odd length
- Trace through the palindrome linked list algorithm step by step

### Afternoon (2 hours)
- Review intersection detection algorithm (two-pointer with switch)
- Review rotate list (cycle + break)
- Review stack problems: Baseball Game (direct stack), Decode String (nested stack)
- Trace through Decode String example: "3[a2[c]]"

### Evening (1 hour)
- Review monotonic stack for Trapping Rain Water
- Compare with the two-pointer approach from Week 2
- Know both approaches cold

---

## Day 5: BFS + Advanced Topics + Full Integration

### Morning (2 hours)
- Master BFS template: queue-based, level-by-level
- Understand multi-source BFS for 01 Matrix
- Review: mark visited on ENQUEUE, not on DEQUEUE — know WHY
- Review queue simulation (Students Unable to Eat)

### Afternoon (2 hours)
- Deep-dive on Shortest Subarray with Sum at Least K
- Trace through the prefix sum + monotonic deque algorithm on a small example
- Understand why simple sliding window fails with negative numbers
- Understand why both ends of the deque are pruned

### Evening (1 hour)
- Full integration review: go through the Pattern Mastery Checklist
- For each unchecked pattern, write a one-sentence explanation
- Review the cross-week connections: palindrome string→LL, prefix sum→shortest subarray, two-pointer across all data structures
- Review common mistakes for each data structure

---

### Daily Review Technique
For each problem, be able to answer these 5 questions:
1. **What is the core data structure/algorithm?**
2. **What is the time and space complexity?**
3. **What is the key insight that makes the solution work?**
4. **What is the most common mistake?**
5. **What other problems use the same pattern?**

---

# 🧩 PATTERN RECOGNITION CHEAT SHEET

## Quick Classification: Given a Problem, What Pattern to Use?

| **If you see...** | **Think...** | **Pattern** |
|-------------------|-------------|-------------|
| "Find in a sorted array" | Binary search | Bisect-left/right |
| "Minimum/maximum subarray of length/sum" | Sliding window or two pointers | Expand/shrink window |
| "All possible combinations/permutations" | Backtracking | Choose → Explore → Un-choose |
| "Shortest path in unweighted graph/grid" | BFS | Queue-based level traversal |
| "Overlapping subproblems" | DP / Memoization | Cache results |
| "In-place array modification" | Two pointers (read-write) | Fast/slow pointer |
| "Linked list middle/cycle" | Slow/fast pointer | Floyd's technique |
| "Nested brackets/parentheses" | Stack | Push on open, pop on close |
| "Next greater/smaller element" | Monotonic stack | Maintain sorted order |
| "Design a system with operations" | OOP + HashMap | Classes + maps for state |
| "Kth largest/smallest" | Heap or Quickselect | Min-heap of size K |
| "Merge intervals/sorted lists" | Sort + sweep / merge | Sort then linear scan |
| "Subarray sum" | Prefix sum | prefix[i] - prefix[j] |
| "Distance in a grid from multiple sources" | Multi-source BFS | All sources in initial queue |
| "Power/factorial/digits of a number" | Math formula | Look for closed-form |
| "Palindrome" | Two pointers (converge) | Compare from outside in |
| "Pairs that satisfy a condition" | Two pointers or HashMap | Sort + two-pointer or hash lookup |
| "Trapping water / histogram" | Monotonic stack or two pointers | Track boundaries left and right |
| "Decode/evaluate/process expression" | Stack | Context push/pop |
| "Sliding window with negatives" | Monotonic deque + prefix sum | Deque maintains increasing prefix |

---

## Complexity Cheat Sheet

| Pattern | Typical Time | Typical Space |
|---------|-------------|---------------|
| Hash lookup | O(1) | O(n) |
| Binary search | O(log n) | O(1) |
| Two pointers | O(n) | O(1) |
| Sliding window | O(n) | O(1) - O(k) |
| Prefix sum build | O(n) | O(n) |
| Prefix sum query | O(1) | — |
| BFS on grid | O(m × n) | O(m × n) |
| BFS on graph | O(V + E) | O(V) |
| Sorting | O(n log n) | O(n) merge / O(log n) quick |
| Quickselect | O(n) avg | O(1) |
| Heap operations | O(log n) per op | O(k) for size-k heap |
| Backtracking | Exponential | O(depth) |
| Monotonic stack | O(n) amortized | O(n) |
| Merge K sorted | O(n log k) | O(k) |

---

## The 7 Universal Questions for Any Problem

1. **What are the inputs and outputs?** (Types, ranges, constraints)
2. **What's the brute force?** (Always start here — what's the obvious solution?)
3. **Where's the waste?** (What work is the brute force repeating?)
4. **What data structure eliminates that waste?** (Hashmap? Heap? Stack? Sorted structure?)
5. **What algorithm pattern fits?** (Two-pointer? Binary search? BFS? DP?)
6. **What are the edge cases?** (Empty input? Single element? All same? Max/min values? Overflow?)
7. **What's the complexity?** (Time and space — verify it meets the problem's constraints)

---

> *"The difference between a 30-minute solve and a 3-minute solve is pattern recognition. Study patterns, not problems."*

---

*End of DSA Conceptual Guide*
