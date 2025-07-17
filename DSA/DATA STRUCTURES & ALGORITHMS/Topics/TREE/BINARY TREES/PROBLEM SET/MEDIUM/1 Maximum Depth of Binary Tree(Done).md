---
difficulty: EASY
date_started: 2025-01-04
last_reviewed: 
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**:
**CONCEPT:** [](.md)

PROBLEM LINK:https://leetcode.com/problems/maximum-depth-of-binary-tree/description/
## Problem Statement
> Copy the problem statement here for quick reference.
> Given the `root` of a binary tree, return _its maximum depth_.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg)

**Input:** root = [3,9,20,null,null,15,7]
**Output:** 3

**Example 2:**

**Input:** root = [1,null,2]
**Output:** 2

**Constraints:**

- The number of nodes in the tree is in the range `[0, 104]`.
- `-100 <= Node.val <= 100`

## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - SINCE TREE TRAVERSAL HAI DONO TRIKE SE HO SAKTE HAI DFS AND BFS AS WELL!
   - DFS approach easy hoti hai!

2. **Approach Options**:
   - Describe any alternative approaches you considered.

   DFS
   ```c++
int maxDepth(TreeNode* root) {
        if(root == NULL) return 0;
        int lefth = maxDepth(root->left);
        int righth = maxDepth(root->right);
        return max(lefth,righth)+1;
    }
```

  BFS
```c++
 int maxDepth(TreeNode* root) {
        if(!root)return 0;
        queue<TreeNode*>q;
        q.push(root);
        int height = 0;
        while(!q.empty()){
            int levelSize = q.size();
            
            for( int i = 0; i<levelSize ; i++){
                TreeNode*temp=q.front();
                q.pop();
                if(temp->left)q.push(temp->left);
                if(temp->right)q.push(temp->right);
            }
            height++;
        }
        return height;
    }
```

3. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - DONO HI APPRAOCH SAHI HAI!

## Code (C++)
```cpp
// C++ solution goes here
```

## Complexity Analysis
- **Time Complexity**: 
- **Space Complexity**: 

## Edge Cases
List any edge cases you considered, such as:
- Empty input
- Very large input
- Special cases (e.g., minimum/maximum values)

## Mistakes / Lessons Learned
Document any mistakes you made while solving, along with the solutions.
Write down any new techniques or patterns that you discovered while working on this problem.

## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.