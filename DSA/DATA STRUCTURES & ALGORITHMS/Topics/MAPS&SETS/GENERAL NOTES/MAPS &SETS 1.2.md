## 1.  **Ordered Set**

- `\#include <set>`

Implemented as a balanced binary tree.
The elements in a `set` are automatically sorted in ascending order.  
**Access**: accessing elements in a `set` takes logarithmic time, `O(log n)`.
**Unique Elements**: A `std::set` contains only unique elements, meaning no duplicates are allowed  
  

## 2. **Ordered Map**:

- `\#include <map>`
A `map` is a balanced binary tree (typically a Red-Black Tree) where elements are stored as key-value pairs.
**Order**: The elements in a `std::map` are automatically sorted by the key in ascending order. In case the keys are strings they are sorted in lexicographical order
**Access**: You can access elements by their key in logarithmic time, `O(log n)`.
**Unique Keys**: Each key in a `std::map` is unique, meaning you can't have two elements with the same key  



  
  

Q1→[https://leetcode.com/problems/finding-3-digit-even-numbers/description/](https://leetcode.com/problems/finding-3-digit-even-numbers/description/)