## Universal Problem-Solving Framework

### The UCCEE Method

- **Understand**: Read problem 2-3 times, identify inputs/outputs/constraints, spot edge cases
- **Clarify**: Ask about empty inputs, size limits, invalid case handling, expected return format
- **Code**: Start with brute force if needed, optimize incrementally, use clear variable names
- **Execute**: Test with given examples, create your own test cases, verify edge cases
- **Evaluate**: Analyze time/space complexity, identify optimization opportunities

### Pattern Recognition Checklist

- Two elements sum to target → Two Pointers or Hash Map
- Subarray with specific condition → Sliding Window
- Tree/graph traversal → DFS/BFS
- Shortest path → BFS or Dijkstra
- Optimization with choices → Dynamic Programming
- Generate all possibilities → Backtracking
- Top K elements → Heap
- Interval problems → Sorting + Greedy
- Cycle detection → Fast/Slow Pointers

---

## 1. Array and List Problems

### Two Pointers Strategy

- **When to use**: Sorted arrays, palindromes, pair problems, removing duplicates
- **Setup**: Place one pointer at start, one at end (or both at start for fast/slow)
- **Movement rules**: Move based on comparison results or specific conditions
- **Key insight**: Eliminates need for nested loops, reduces O(n²) to O(n)
- **Common patterns**: Target sum, container problems, removing elements

### Sliding Window Strategy

- **When to use**: Subarrays, substrings, consecutive elements, "maximum/minimum in window"
- **Fixed window**: Maintain constant window size, slide one position at a time
- **Variable window**: Expand when condition not met, contract when condition satisfied
- **Track**: Window sum, character frequencies, or relevant metrics
- **Key insight**: Avoid recalculating overlapping portions

### Fast and Slow Pointers

- **When to use**: Cycle detection, finding middle element, nth from end
- **Setup**: Both start at same position, fast moves 2x speed of slow
- **Cycle detection**: If they meet, cycle exists
- **Middle finding**: When fast reaches end, slow is at middle
- **Floyd's algorithm**: Used for cycle detection and finding cycle start

### Prefix Sum Technique

- **When to use**: Range sum queries, subarray sum problems
- **Setup**: Build cumulative sum array from original array
- **Range calculation**: sum(i,j) = prefix[j+1] - prefix[i]
- **Space trade-off**: O(n) extra space for O(1) query time

### Common Array Patterns

- **Kadane's algorithm**: Maximum subarray sum (track current and global max)
- **Dutch flag**: Three-way partitioning (low, mid, high pointers)
- **Boyer-Moore**: Majority element (candidate and counter approach)
- **Merge technique**: Combining sorted arrays or intervals

---

## 2. String Problems

### Character Frequency Strategy

- **When to use**: Anagrams, character counting, permutation problems
- **Tools**: Dictionary/Counter for frequency mapping
- **Pattern**: Build frequency map, then compare or manipulate
- **Optimization**: Use array of size 26 for lowercase letters only

### String Sliding Window

- **When to use**: Substring problems, character constraints, "contains all characters"
- **Setup**: Track character frequencies in current window
- **Expansion**: Add characters to window until condition met
- **Contraction**: Remove characters while maintaining condition
- **Template**: Similar to array sliding window but with character tracking

### Palindrome Strategies

- **Two pointers**: Start from ends, move inward while checking equality
- **Expand around center**: For each position, expand outward to find longest palindrome
- **Dynamic programming**: For complex palindrome substring/subsequence problems
- **Preprocessing**: Convert to lowercase, remove non-alphanumeric for real palindromes

### String Matching Patterns

- **Brute force**: Check every position (O(nm) time)
- **KMP algorithm**: Build failure function, avoid redundant comparisons
- **Rolling hash**: Use polynomial hashing for faster string comparison
- **Suffix arrays**: For multiple pattern matching

---

## 3. Linked List Problems

### Two Pointers in Linked Lists

- **Cycle detection**: Fast pointer moves 2 steps, slow moves 1 step
- **Finding middle**: When fast reaches end, slow is at middle
- **Nth from end**: Move first pointer n steps ahead, then move both until first reaches end
- **Intersection**: Use two pointers starting from different heads

### Linked List Reversal

- **Iterative approach**: Track prev, current, next pointers
- **Recursive approach**: Reverse rest of list, then fix current connections
- **Partial reversal**: Reverse only portion between given positions
- **Group reversal**: Reverse k nodes at a time

### Merge Operations

- **Two sorted lists**: Compare values, link smaller one, advance pointer
- **K sorted lists**: Use priority queue/heap for efficient merging
- **Sort linked list**: Use merge sort (divide at middle, merge sorted halves)

### Common Linked List Patterns

- **Dummy node**: Simplifies edge cases when head might change
- **Runner technique**: Use two pointers at different speeds
- **Stack simulation**: Use recursion or actual stack for LIFO operations

---

## 4. Tree Problems

### Tree Traversal Strategies

- **Inorder (Left-Root-Right)**: For BST, gives sorted order
- **Preorder (Root-Left-Right)**: For copying/serializing tree structure
- **Postorder (Left-Right-Root)**: For deletion, calculating sizes
- **Level order (BFS)**: For level-by-level processing, shortest path in trees

### DFS vs BFS Decision Making

- **Use DFS when**: Need to explore all paths, memory is limited, solution likely deep
- **Use BFS when**: Finding shortest path, solution likely near root, need level-by-level processing
- **Iterative vs Recursive**: Iterative uses explicit stack, recursive uses call stack

### Tree Path Problems

- **Root to leaf**: Use DFS with path tracking and backtracking
- **Any node to any node**: Consider each node as potential path center
- **Path sum problems**: Subtract target as you go deeper
- **Diameter/maximum path**: Use post-order traversal to get subtree information

### Binary Search Tree Operations

- **Search**: Compare with current node, go left if smaller, right if larger
- **Insert**: Find correct position, attach new node
- **Delete**: Handle three cases (no children, one child, two children)
- **Validation**: Ensure all nodes follow BST property with min/max bounds

### Tree Construction

- **From traversals**: Use preorder/postorder with inorder to rebuild tree
- **From array**: For complete binary trees, use index relationships
- **Serialization**: Convert tree to string and back

---

## 5. Graph Problems

### Graph Representation

- **Adjacency list**: Better for sparse graphs, easier to iterate neighbors
- **Adjacency matrix**: Better for dense graphs, O(1) edge lookup
- **Edge list**: Simple representation, good for algorithms like Kruskal's

### DFS Strategies

- **Use for**: Cycle detection, topological sort, strongly connected components
- **Implementation**: Recursive or iterative with stack
- **State tracking**: White (unvisited), Gray (visiting), Black (visited)
- **Applications**: Maze solving, finding all paths

### BFS Strategies

- **Use for**: Shortest path in unweighted graphs, level-by-level exploration
- **Implementation**: Queue-based iteration
- **Applications**: Minimum steps problems, social network distances

### Shortest Path Algorithms

- **Unweighted graphs**: BFS gives shortest path
- **Weighted graphs**: Dijkstra for single source, Floyd-Warshall for all pairs
- **Negative weights**: Bellman-Ford algorithm
- **Grid problems**: Treat as graph, use coordinates as nodes

### Cycle Detection

- **Undirected graphs**: Use DFS, check if visiting already visited node (not parent)
- **Directed graphs**: Use DFS with color coding (white/gray/black)
- **Union-Find**: Efficient for detecting cycles in undirected graphs

### Topological Sorting

- **Kahn's algorithm**: Use in-degree counting with queue
- **DFS approach**: Use post-order traversal, reverse the result
- **Applications**: Task scheduling, dependency resolution

---

## 6. Dynamic Programming

### DP Problem Recognition

- **Optimal substructure**: Solution can be built from optimal subsolutions
- **Overlapping subproblems**: Same subproblems solved multiple times
- **Keywords**: "Maximum/minimum", "count ways", "optimal", "best"

### Bottom-Up vs Top-Down

- **Bottom-up (tabulation)**: Build solution from smallest to largest subproblems
- **Top-down (memoization)**: Start with main problem, cache recursive results
- **Space optimization**: Often can reduce 2D DP to 1D by keeping only necessary rows

### Common DP Patterns

- **Linear DP**: Process elements one by one (Fibonacci, climbing stairs)
- **Grid DP**: 2D problems (unique paths, minimum path sum)
- **Interval DP**: Problems on ranges/intervals
- **Tree DP**: Dynamic programming on trees
- **Bitmask DP**: Use bits to represent states

### Knapsack Problem Variations

- **0/1 Knapsack**: Each item can be taken at most once
- **Unbounded Knapsack**: Unlimited quantities of each item
- **Multiple Knapsack**: Limited quantities of each item
- **Fractional Knapsack**: Can take fractions (use greedy approach)

### String DP Problems

- **Edit distance**: Transform one string to another with minimum operations
- **Longest common subsequence**: Find longest sequence common to both strings
- **String matching**: Count occurrences of pattern in text

---

## 7. Backtracking

### Backtracking Template

- **Choose**: Make a choice from available options
- **Explore**: Recursively explore the consequences
- **Unchoose**: Undo the choice (backtrack) before trying next option

### When to Use Backtracking

- **Generate all possibilities**: Permutations, combinations, subsets
- **Constraint satisfaction**: N-Queens, Sudoku solving
- **Path finding**: Finding all paths between two points
- **Optimization**: When you need to try all possibilities to find optimal

### Pruning Strategies

- **Early termination**: Stop exploring if current path can't lead to solution
- **Constraint checking**: Validate choices before making recursive calls
- **Memoization**: Cache results for repeated subproblems
- **Ordering**: Try most promising options first

### Common Backtracking Problems

- **Permutations**: Generate all arrangements of elements
- **Combinations**: Choose k elements from n elements
- **Subsets**: Generate all possible subsets (power set)
- **Word search**: Find word in 2D grid
- **N-Queens**: Place n queens on chessboard without conflicts

---

## 8. Sorting and Searching

### Binary Search Variations

- **Standard binary search**: Find exact element in sorted array
- **Find first occurrence**: Continue searching left even after finding target
- **Find last occurrence**: Continue searching right even after finding target
- **Search insert position**: Find where element should be inserted
- **Search in rotated array**: Identify which half is sorted first

### Binary Search Decision Framework

- **Use when**: Array is sorted or problem has monotonic property
- **Template variations**: Adjust loop condition and update logic based on problem
- **Common mistakes**: Integer overflow in mid calculation, infinite loops
- **Extension**: Binary search on answer space for optimization problems

### Sorting Algorithm Choice

- **Quick sort**: Average O(n log n), in-place, good for general purpose
- **Merge sort**: Guaranteed O(n log n), stable, good for linked lists
- **Heap sort**: O(n log n), in-place, good when memory is limited
- **Counting sort**: O(n + k), good when range of elements is small

### Searching Strategies

- **Linear search**: O(n), use when array is unsorted
- **Binary search**: O(log n), requires sorted array
- **Hash table**: O(1) average, good for exact match queries
- **Trie**: Good for prefix-based searches

---

## 9. Heap and Priority Queue

### Heap Usage Patterns

- **Top K elements**: Use min-heap of size K for largest K elements
- **Kth largest/smallest**: Use heap to maintain K elements
- **Median finding**: Use two heaps (max-heap for smaller half, min-heap for larger half)
- **Merge K sorted arrays**: Use heap to track current element from each array

### Priority Queue Applications

- **Dijkstra's algorithm**: Use min-heap for shortest distances
- **Huffman coding**: Build optimal encoding tree
- **Task scheduling**: Process tasks based on priority
- **Event simulation**: Process events in chronological order

---

## 10. Hash Tables and Sets

### Hash Table Strategies

- **Frequency counting**: Count occurrences of elements
- **Two sum variants**: Use hash to find complementary elements
- **Caching**: Store computed results to avoid recomputation
- **Grouping**: Group elements by some property (anagrams, etc.)

### Set Operations

- **Membership testing**: O(1) check if element exists
- **Duplicate removal**: Convert list to set and back
- **Intersection/Union**: Find common elements or combine sets
- **Difference**: Find elements in one set but not another

---

## Problem-Solving Time Management

### 45-Minute Interview Strategy

- **5 minutes**: Understand problem, ask clarifying questions
- **5 minutes**: Discuss approach, mention time/space complexity
- **25 minutes**: Code the solution
- **5 minutes**: Test with examples, discuss optimizations
- **5 minutes**: Handle follow-up questions

### Debugging Strategies

- **Trace through examples**: Walk through your code with given test cases
- **Check edge cases**: Empty inputs, single elements, boundary conditions
- **Review logic**: Ensure loop conditions, base cases, and updates are correct
- **Rubber duck debugging**: Explain your code line by line

### Optimization Mindset

- **Start simple**: Get working solution first, optimize later
- **Identify bottlenecks**: Which operations are repeated most often?
- **Space vs time trade-offs**: Can you use more memory to save time?
- **Algorithm choice**: Is there a fundamentally better approach?