# LEETCODE-TREES-2641
### Steps of the Algorithm

1. **DFS to Compute Level Sums:**
   The `dfs` method computes the sum of node values for each level of the tree. It does this recursively:
   - If the current node is null, return immediately.
   - If the current depth (or level) is new, it adds a zero to the `levelSums` list to start summing up values for that level.
   - It then adds the node's value to the current level's sum and recursively processes the left and right children.

2. **Replacement of Node Values:**
   The `replace` method is a recursive function that creates a new tree where each node's value is replaced by the sum of its cousins’ values at the same level:
   - It computes the **next level cousins sum** for a node by subtracting the node's children's values from the total sum of node values at the next level.
   - It then recursively processes the left and right subtrees, creating new nodes with the computed cousin sum for the corresponding children.

### Dry Run of Example

Let's dry run the solution for a small binary tree:
```
    1
   / \
  2   3
```

#### Step 1: Compute the `levelSums` using DFS
- `levelSums` starts as an empty list.
- At root (level 0), the sum becomes `[1]`.
- At level 1, after visiting both children (2 and 3), the sum becomes `[1, 5]`.

#### Step 2: Replace the node values
- At level 0, there's no cousin, so the root node remains `0`.
- At level 1, the sum of node values is `5`. The cousin sum for both children is calculated as:
  - For node 2: `5 - 3 = 2` (so replace 2 with 3).
  - For node 3: `5 - 2 = 3` (so replace 3 with 2).

The new tree becomes:
```
    0
   / \
  3   2
```

### Complexity Analysis

- **Time Complexity:**
  - The DFS runs in O(n) to calculate the level sums, where `n` is the number of nodes in the tree.
  - The replacement function also runs in O(n), as it traverses each node once to replace values.
  - So the overall time complexity is O(n).

- **Space Complexity:**
  - The space complexity is O(h), where `h` is the height of the tree, due to the recursive call stack and the `levelSums` list that stores sums for each level (which can have at most `h` levels).

### Conclusion
This solution efficiently replaces each node's value in a binary tree with the sum of its cousins' values using a two-pass DFS approach.
