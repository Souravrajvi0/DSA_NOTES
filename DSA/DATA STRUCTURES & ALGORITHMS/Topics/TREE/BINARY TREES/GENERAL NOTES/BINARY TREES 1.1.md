##### Base case for binary trees:

In most recursive functions that traverse or manipulate binary trees, the base case checks if the current node is `NULL`. If the node is `NULL`, the recursion should stop, as this indicates either a leaf node or an empty subtree.

**Generic trees**: In some types of generic trees (with variable numbers of children), recursive traversal often involves iterating over a list or vector of children. The recursive call is made for each child, and the recursion naturally stops when there are no more children. Depending on the implementation, an explicit base case might not always be necessary.



![image 42.png](../../../../../../Images/image%2042.png)

```Plain
What is Tree?
```

Tree is a type of a non-linear Data Structure. In this a single node can be connected to multiple nodes..

This hierarchical structure of tree is used in Computer Science as an abstract data type for various applications like data storage, search & sort algorithms.

![image 1 19.png](../../../../../../Images/image%201%2019.png)

**Basic Term's :-**

```Plain
1. Node
2. Root
3. Children
4. Parent
5. Siblings
6. Ancestor
7. Descendant
8. Leaf
```

1. Node :- which hold's data 
2. Root :- Where tree start OR top node
3. Children :- it is a node of a parent node. E.g :- (2) is a child of node (1)
4. Parent :- E.g (1) is parent of node (2) & node (3)
5. Siblings :- whose parent is same. E.g (4) & (5) are sibling's because there parent is same i.e. (2)
6. Ancestor :- Going up from a child or leaf
7. Descendant :- Going down from top root
8. Leaf :- is that who don't have any child's E.g (4) & (5) & (6) & (7) are leaf node

```Plain
Now, What is Binary Tree?
A tree is called binary tree if every node has zero, one or two children.

We can visualize a binary tree as consisting of root node, left child & right child.
```

![image 2 17.png](../../../../../../Images/image%202%2017.png)

![image 3 15.png](../../../../../../Images/image%203%2015.png)

![image 4 13.png](../../../../../../Images/image%204%2013.png)

![image 5 11.png](../../../../../../Images/image%205%2011.png)





![image 7 10.png](../../../../../../Images/image%207%2010.png)

⇒Ye thoda linkedlist jaisa feel deta hai since Har Node se ek hi node connected hoga

![image 8 10.png](../../../../../../Images/image%208%2010.png)

```C++
DataType *pointerName;
```

Here's a breakdown:

1. `**DataType**`: This is the type of data that the pointer will point to. For example, if you are dealing with a binary tree of integers, the data type would be `int`. If you are working with nodes of a binary tree, the data type would be `TreeNode`.
2. : This is the asterisk symbol that denotes that the variable is a pointer. It indicates that the variable will store the address of an object of the type specified.
3. `**pointerName**`: This is the name you give to your pointer variable.

---

## TRAVERSAL TECHNIQUES

#### So, there are two traversal technique:-

  

## DFS - Depth First Search

Let's understand DFS traversal

### Time Complexity

For all three traversals (pre-order, in-order, and post-order), the time complexity is:

- **O(n)**

### Space Complexity

Space complexity can vary depending on the traversal method and whether the traversal is implemented recursively or iteratively.

### 1. **Recursive Traversal**

In recursive implementations, space complexity is mainly determined by the depth of the recursion stack.

**Space Complexity**: O(h), where `h` is the height of the tree. In the worst case (a skewed tree), `h` could be `n` (the number of nodes), so the space complexity in that scenario could be O(n). In a balanced binary tree, the height `h` would be log(n), making the space complexity O(log n).  
  
  

### 2. **Iterative Traversal**

**Space Complexity**: O(n), because in the worst case, the stack used to hold nodes can grow to the size of the tree (e.g., when nodes are pushed onto the stack but not yet processed).  
  
  

### **InOrder Traversal (left root right)**

First go to left from the root once you reach the left leaf null, add that into your result then traverse it right and so on.

From the above tree the traverse we get is :-

```Plain
4 2 5   1   6 3 7
```

![image 9 9.png](../../../../../../Images/image%209%209.png)

RECURSIVE CODE

```C++
void helper(TreeNode*node,vector<int>&nodes){
      if(node==NULL)return;
      helper(node->left,nodes);
      nodes.push_back(node->val);
      helper(node->right,nodes);
    }
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int>nodes;
        helper(root,nodes);
        return nodes;
    }
```

INTERATIVE CODE

Since we're using a stack in recursive code We can use a stack in iterative code as well right!
Before diving into the iterative approach, it's helpful to understand the recursive approach, as the iterative method essentially mimics the function call stack.
The key idea behind iterative inorder traversal is to **mimic** the recursive process without using the function call stack. We do this by maintaining a stack explicitly

```c++

vector<int> inorderTraversal(TreeNode* root) {
    vector<int>ans;
    if(root == NULL) return ans;
    stack<TreeNode*>st;
    TreeNode*cur = root;
    while(!st.empty()||cur!=NULL){
     
     while(cur){
        st.push(cur);
        cur = cur->left;
     }
      
    cur=st.top();
    ans.push_back(cur->val);
    st.pop();

    cur=cur->right;
    }
    return ans;
    }
```


We Need Both Conditions

### **What Happens If We Only Use `while(!st.empty())`?**

If we omit `cur != NULL` and use only `while(!st.empty())`, we might terminate the loop prematurely in cases where:

- The stack becomes empty after popping a node, but the `cur` pointer is still pointing to a valid node (e.g., the right child of a node we just processed).
- Example:
    - Suppose the stack is empty after processing the left subtree of the root, and `cur` points to the root's right subtree. The loop will terminate without exploring the right subtree, causing an incomplete traversal.

![BINARY TREES 1.1-20250104114901794.webp](../../../../../../Images/BINARY%20TREES%201.1-20250104114901794.webp)


**Time Complexity: O(N)**

**Space Complexity: O(N)=O(Height of the Tree)**

### **PreOrder Traversal (root left right)**

First add to the root then go to left from the root once you reach the left leaf null, then traverse it right and so on.

From the above tree the traverse we get is :-

```Plain
1 2 4   5   3 6 7
```

  

![image 10 8.png](../../../../../../Images/image%2010%208.png)

RECURSIVE SOLUTION→

```C++
 void helper(TreeNode*node,vector<int>&nodes){
      if(node==NULL)return;
      nodes.push_back(node->val);
      helper(node->left,nodes);
      helper(node->right,nodes);
    }

   vector<int> preorderTraversal(TreeNode* root) {
        // pre root left right
        vector<int>nodes;
        helper(root,nodes);
        return nodes;
        }
```

ITERATIVE CODE⇒

**Time Complexity: O(N)**

**Space Complexity: O(N)=O(Height of the Tree)**

```C++
vector<int> preorderTraversal(TreeNode* root) {
         vector<int>res;
         if(root==NULL)return res;
         stack<TreeNode*>st;
         st.push(root);
         while(!st.empty()){
           TreeNode*temp=st.top();
           st.pop();
           res.push_back(temp->val);
       if(temp->right!=NULL)st.push(temp->right);  // RIGHT PEHLE ISLIYE KYONKU LEFT UPAR 
       if(temp->left!=NULL)st.push(temp->left);  // CHAHITE MUJHE PEHLE AND STACK IS LIFO
        }
        return res;
    }
```

  

  

### **PostOrder Traversal (left right root)**

First go to left from the root once you reach the left leaf null, then traverse it right and once you reach the null of right now add that value into our result.

From the above tree the traverse we get is :-

```Plain
4 5 2   6   7 3 1
```

![image 11 7.png](../../../../../../Images/image%2011%207.png)

RECURSIVE

```C++
void helper(TreeNode*node,vector<int>&nodes){
      if(node==NULL)return;
      helper(node->left,nodes);
      helper(node->right,nodes);
      nodes.push_back(node->val);
    }
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int>nodes;
        helper(root,nodes);
        return nodes;
    }
```

ITERATIVE-



USING 2 STACKS
![BINARY TREES 1.1-20250104130033334.webp](../../../../../../Images/BINARY%20TREES%201.1-20250104130033334.webp)

```c++
vector<int> postorderTraversal(TreeNode* root) {
    vector<int>ans;
    if(!root)return ans;

    stack<TreeNode*>s1,s2;

    s1.push(root);
    while(!s1.empty()){
      TreeNode*temp=s1.top();
      s1.pop();
      s2.push(temp);
      if(temp->left)s1.push(temp->left);
      if(temp->right)s1.push(temp->right);
    }

    while(!s2.empty()){
    ans.push_back(s2.top()->val);
    s2.pop();
    }
    return ans;
    }
```

  USING 1 STACK
```c++
 vector<int> postorderTraversal(TreeNode* root) {

    vector<int>ans;
    if(!root)return ans;
    stack<TreeNode*>st;
    TreeNode* cur = root;
    TreeNode* prev=NULL;
    

    while(cur != NULL|| !st.empty()){
     
     while(cur){
        st.push(cur);
        cur=cur->left;
        }

      cur=st.top();
     if(cur->right == NULL || cur->right == prev){
      st.pop();
      ans.push_back(cur->val);
      prev = cur;
      cur = NULL;
     }else{
        cur = cur->right;
     }
    }
    return ans;
    }
```


  2ND APPROACH ITERATIVE
```c++

```

## BFS  -Breadth First Search/Level Order Traversal 

![image 12 7.png](../../../../../../Images/image%2012%207.png)

```C++
vector<vector<int>> levelOrder(TreeNode* root) {
       vector<vector<int>> levelOrder(TreeNode* root) {
         if (!root) return {};// YE MAT BHULNA BHAI
        queue<TreeNode*>q;
        q.push(root);
        vector<vector<int>>ans;
        while(!q.empty()){
            vector<int>level;
            int levelSize=q.size();

            for(int i=0;i<levelSize;i++){
                TreeNode*temp=q.front();
                q.pop();
                if(temp->left!=NULL)q.push(temp->left);
                if(temp->right!=NULL)q.push(temp->right);
                level.push_back(temp->val);
            }
           if(!level.empty()) ans.push_back(level);
        }
        return ans;
    }
```

We can also write Level Order traversal with just one while loop

```c++
void levelOrderTraversal(Node* root) {
    if (root == nullptr) return;

    queue<Node*> q;
    q.push(root);

    while (!q.empty()) {
        Node* current = q.front();
        q.pop();
        cout << current->data << " ";

        if (current->left) q.push(current->left);
        if (current->right) q.push(current->right);
    }
}
```

Time Complexity: O()
Space Complexity: O()

ORDER TOH ABHI BHI SAME HI RAHEGA! BUT HUM USE NAHI KAR PAENGE!
### Why Use a `for` Loop Inside the `while`?

1. **Group by Levels**: If you want to group nodes by levels or perform level-specific operations, the `for` loop is helpful because it processes all nodes of the current level before moving to the next.
2. **Modular Code**: It's easier to manage and extend level-specific logic (e.g., summing values at a level, checking if a level is a palindrome, etc.).