### TOPIC [[binary trees]]

# Concept Name 
(Name it based on what it does - you can rename it later when you learn the formal term!)
KUCH SAWALO MEIN HEIGHT NIKALNE KA USAGE HOTA HAI! MTLB HEIGHT NIKAL LO FIR USS HEIGHT VALUE PAR KUCH OPERATIONS KAR SAKTE HAIN!

## What Problem Led Me to This Concept?
- First discovered in: Balanced Binary Tree
- Recognized pattern while: (what you were trying to do)
- Height ka use krna chah ra tha but sath mein question bhi solve horaha tha!


## What Does This Concept Do?
- Simple explanation in your own words

```c++
int maxDepth(TreeNode* root) {
        if(root == NULL) return 0;
        int lefth = maxDepth(root->left);
        int righth = maxDepth(root->right);
        return max(lefth,righth)+1;
    }


    bool isBalanced(TreeNode* root) {
     if(!root) return true;
     if(abs(maxDepth(root->left)-maxDepth(root->right))>1)return false;
     return isBalanced(root->left) && isBalanced(root->right);
        
    }
```

YAHAN HEIGHT HAR BAR NIKAL RAHA HUON WO CHUTIYA PANTI HAI! HAR POINT PAR!

BETTER WAY AESE

```c++
int maxDepth(TreeNode* root) {
        if(root == NULL) return 0;
        int lefth = maxDepth(root->left);
        if(lefth==-1)return -1;
        int righth = maxDepth(root->right);
        if (righth == -1) return -1;
        return (abs(lefth-righth)<=1)? max(lefth,righth)+1 : -1;
    }



    bool isBalanced(TreeNode* root) {
       return !(maxDepth(root) == -1);
    }
};
```



- Main purpose/goal
- AUR EXTRA CALLS LAGAE BINA EK BAR JABH HEIGHT FIND KI USS TIME HI USE KARLO! USKO KUCH EXTRA KRNE K LIYE!


- When to think of using this


## How to Apply This Concept?
1. Step 1 of using this concept
2. Step 2 of using this concept
3. Step 3 of using this concept

## Key Things to Remember
- Important point 1
- Important point 2
- Common mistakes to avoid

## Code Template
```c++
# Basic structure of how to implement this concept
# This is your template for future use


```


## Problems:
- [[1 Maximum Depth of Binary Tree(Done)]]
- [[2. Balanced Binary Tree(Done)]]
- [[3. Diameter of Binary Tree(Done)]]
- [[4. Binary Tree Maximum Path Sum(Imp)]]


