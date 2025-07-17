![90C46223-AF22-4F8D-BB29-36E213AC0794.png](../../../../../../Images/90C46223-AF22-4F8D-BB29-36E213AC0794.png)

-  L<N<R is mostly with no duplicates!
-  Everything on the left should be lesser than the node's value and everything on the right should be greater than the node's value!

-  If duplicates exist We’d have to take the Equal Marks! like L< = N< = R
- How to integrate these nodes well what you can do is either add a node to the tree or like just keep a counter variable in the node like if 8 comes twice (8,2)


→BST mein Right wale part mein sare nodes bade honge root se and left wale sare chote honge root se!

→ SO TO BE BST , ON EVERY NODE THE BST PROPERTY SHOULD BE FOLLOWED MEANING THAT HAR SUBTREE SHOULD BE A BST ONLY THEN YOU CAN SAY THE WHOLE TREE IS A BST!


## **WHY BST??**
Height of the BST is generally  log2(N)

## **SEARCH IN A BST**






In a **Binary Search Tree (BST)**:

- The **maximum value** will always be found in the **rightmost node** of the tree because, by definition, all values in the right subtree are greater than the current node.
- The **minimum value** will always be found in the **leftmost node** of the tree because all values in the left subtree are smaller than the current node.

  

![image-1727757533127.jpg232251271030702680.jpg](../../../../../../Images/image-1727757533127.jpg232251271030702680.jpg)

### SEARCH IN BST

[https://www.geeksforgeeks.org/problems/search-a-node-in-bst/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card](https://www.geeksforgeeks.org/problems/search-a-node-in-bst/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card)

RECURSIVE
```c++
TreeNode* searchBST(TreeNode* root, int val) {
        if(!root) return NULL;
        if(root->val == val){
            return root;
        } else if(root->val > val){
             return searchBST(root->left,val);
        }else{
            return searchBST(root->right,val);
        }
    }
```

Time Complexity: O(N)
Space Complexity: O(log2N)

ITERATIVELY EASY HOTA HAI!
TC: log2(N) ati hai!
```C++
bool search(Node* root, int x) {
    // Your code here
    while(root && root->data!=x){
        root = (root->data>x) ? root->left : root->right;
    }
    if(root)return true;
    return false;
}

```



In a **Binary Search Tree (BST)**, the snippet `while(root && root->val != val)` works perfectly for searching because of the specific properties of a BST:

1. **Ordered structure**:
    
    - In a BST, the left child of a node always contains values smaller than the node, and the right child contains values larger than the node. This order allows you to discard one half of the tree at each step based on whether the value you're searching for is less than or greater than the current node's value.
    - You can efficiently "narrow down" your search by following the structure of the tree, moving either left or right as appropriate, just like in binary search.
    
    Hence, this iterative approach works for a **BST** because it leverages the fact that you know where to search next: either the left or right subtree, depending on the comparison.
    

### Why this doesn't work for a generic **Binary Tree**:

A **Binary Tree**, on the other hand, does **not** have the ordering properties of a BST. In a generic binary tree:

- The left and right children can have any arbitrary value, without any relationship to the parent node.
- There's no guarantee that smaller values will be on the left and larger values on the right.

Time Complexity!

- **BST:** Takes advantage of ordering, providing better performance on average (O(log N)).
- **BT:** Has no ordering, leading to linear time complexity (O(N)) in the worst case for all searches.

  

**Binary Search Tree (BST)** can become a **skewed tree**.

### What is a Skewed Tree?

A **skewed tree** is a type of binary tree in which all the nodes have only one child, either on the left or the right. There are two types of skewed trees:

- **Left-Skewed Tree:** Each node has only a left child.
- **Right-Skewed Tree:** Each node has only a right child.

### How Can a BST Become Skewed?

A BST can become **skewed** if the values are inserted in either increasing or decreasing order.

1. **Right-Skewed BST:**
    
    - If the elements are inserted in **increasing order**, each new element is greater than the previous one. As a result, all elements will be inserted as right children, leading to a **right-skewed tree**.
    
    Example of inserting elements in increasing order:
    
    ```YAML
    
    Insert: 1, 2, 3, 4, 5
    Resulting BST:
        1
<br/>
          2
<br/>
            3
<br/>
              4
<br/>
                5
    
    ```
    
2. **Left-Skewed BST:**
    
    - If the elements are inserted in **decreasing order**, each new element is smaller than the previous one. As a result, all elements will be inserted as left children, leading to a **left-skewed tree**.
    
    Example of inserting elements in decreasing order:
    
    ```YAML
    
    Insert: 5, 4, 3, 2, 1
    Resulting BST:
        5
       /
      4
     /
    3
    ```
    

**WELL IN THIS CASE EVE SEARCHING IN BST WILL ALSO COME UNDER O(N)**

**FIND MIN AND MAX VALUE IN A TREE**
https://www.geeksforgeeks.org/problems/minimum-element-in-bst/1

## **MIN**
```c++
 int minValue(Node* root) {
        // Code here
        while(root->left!=NULL){
            root=root->left;
        }
        return root->data;
    }
```
Time Complexity: O(log2N)
Space Complexity: O(1)

## **MAX** 
```c++
 int maxValue(Node* root) {
        // Code here
        while(root->right!=NULL){
            root=root->right;
        }
        return root->data;
    }
```

Time Complexity: O(log2N)
Space Complexity: O(1)


**Ceil(X) is a number that is either equal to X or is immediately greater than X.**
[https://www.geeksforgeeks.org/problems/implementing-ceil-in-bst/1](https://www.geeksforgeeks.org/problems/implementing-ceil-in-bst/1)

```C++
int findCeil(Node* root, int i) {
    if (root == NULL) return -1;

    // Your code here
    int ceil=-1;
    while(root){
        if(root->data>=i){
            ceil=root->data;
            root=root->left;
        }
        root=root->right;
    }
    return ceil;
}
```

[https://www.geeksforgeeks.org/problems/floor-in-bst/1](https://www.geeksforgeeks.org/problems/floor-in-bst/1)

```C++
int floor(Node* root, int x) {
        // Code here
        int floor=-1;
        if(!root)return floor;
        while(root){
            if(root->data <= x){
                floor=root->data;
                root=root->right;
            }
            root=root->left;
        }
        return floor;
    }
```

[https://leetcode.com/problems/insert-into-a-binary-search-tree/description/](https://leetcode.com/problems/insert-into-a-binary-search-tree/description/)

![67B41148-2269-4721-9F79-33557777A29D.png](../../../../../../Images/67B41148-2269-4721-9F79-33557777A29D.png)

Ismein 5 insert karna hai!

```C++
       4
      / \
     2   7
    / \  /
   1   3 5
```

```C++
       4
      / \
     2   5
    / \   \
   1   3   7
```

![D60A1109-EFDA-472A-9F44-557ED0BFA5AD.png](../../../../../../Images/D60A1109-EFDA-472A-9F44-557ED0BFA5AD.png)

![0B2F2A52-E91A-47DF-903E-5F455EF9800B.png](../../../../../../Images/0B2F2A52-E91A-47DF-903E-5F455EF9800B.png)

### 1. **Recursive Approach** (First Code):

```C++
cpp
Copy code
TreeNode* insertIntoBST(TreeNode* root, int val) {
    if (root == NULL) return new TreeNode(val);

    if (root->val > val) {
        root->left = insertIntoBST(root->left, val);
    } else {
        root->right = insertIntoBST(root->right, val);
    }
    return root;
}
```

### 2. **Iterative Approach** (Second Code):

```C++
cpp
Copy code
TreeNode* insertIntoBST(TreeNode* root, int val) {
    if (root == NULL) return new TreeNode(val);
    TreeNode* temp = root;
    while (temp) {
        if (temp->val > val) {
            if (temp->left) {
                temp = temp->left;
            } else {
                temp->left = new TreeNode(val);
                break;
            }
        } else {
            if (temp->right) {
                temp = temp->right;
            } else {
                temp->right = new TreeNode(val);
                break;
            }
        }
    }
    return root;
}
```

### 3. **Iterative Approach with** `**prev**` **Pointer** (Third Code):

```C++
cpp
Copy code
TreeNode* insertIntoBST(TreeNode* root, int val) {
    TreeNode* t = new TreeNode(val);
    if (root == NULL) return t;
    TreeNode* temp = root;
    TreeNode* prev = NULL;
    while (temp != NULL) {
        prev = temp;
        if (temp->val > val) {
            temp = temp->left;
        } else {
            temp = temp->right;
        }
    }
    if (prev->val > val) {
        prev->left = t;
    } else {
        prev->right = t;
    }
    return root;
}
```

### Comparison:

- **First Code (Recursive)**: Simple and clean, but recursion may cause issues with deep trees (stack overflow).
- **Second Code (Iterative)**: Avoids recursion but uses a loop to traverse. It's slightly more verbose but safer in terms of memory (no stack overflow).
- **Third Code (Iterative with** `**prev**`**)**: This method is a variation of the iterative approach but uses a `prev` pointer to track the parent node, offering flexibility in handling more complex scenarios. However, it's a bit more complicated than the second version.

  

[https://leetcode.com/problems/delete-node-in-a-bst/](https://leetcode.com/problems/delete-node-in-a-bst/)(REVISE)

Now even deleting a node can also result in various Types of Trees not just one!

![52315E8F-2A65-464C-98A5-2C4919A35D72.png](../../../../../../Images/52315E8F-2A65-464C-98A5-2C4919A35D72.png)

![7E0D5115-65D3-471F-8FE9-150C7BFEDB42.png](../../../../../../Images/7E0D5115-65D3-471F-8FE9-150C7BFEDB42.png)

![5CB5653F-D0DE-4448-951A-70F27790F402.png](../../../../../../Images/5CB5653F-D0DE-4448-951A-70F27790F402.png)

EDGE CASES HONGE LEKIN

![image-1727766898810.jpg2017990684525843416.jpg](../../../../../../Images/image-1727766898810.jpg2017990684525843416.jpg)

![image-1727766914152.jpg8383956231864046636.jpg](../../../../../../Images/image-1727766914152.jpg8383956231864046636.jpg)