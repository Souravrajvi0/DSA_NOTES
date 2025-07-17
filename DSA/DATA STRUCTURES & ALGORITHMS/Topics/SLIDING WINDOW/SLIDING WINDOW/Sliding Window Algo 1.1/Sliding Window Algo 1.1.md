⇒Sliding window Helps in reducing the time complexity

The term **Sliding** in the ‘Sliding Window Algorithm’ comes from the operations we will be performing on the given array (aka window). We will only be moving forward and backward in this array with the help of two pointers called ‘**Start**’ and ‘**End’**. The elements between these two pointers will represent our contiguous window at any given point of time.

⇒By ‘**Start**’ and ‘**End**’ pointer we mean that we will have two integer variables with the same names in order to move forward and backward along the array using its index. ‘**Start**’ variable will mark the start index of our sliding window and ‘**End**’ variable will mark the end index of our sliding window.

⇒While solving a problem using this algorithm we will generally be moving both our pointers, their individual movement being governed by some constraints specific to the problem and the distance between them being constantly tracked so as to get the global minimum or maximum. This is generally going to be the pattern for most of the problems.

⇒ We can do some selective problems in O(n)

**The Sliding Window Technique** is a problem-solving technique that is used to

**1.Running Average:** Use a sliding window to efficiently calculate the average of a fixed-size window as new elements arrive in a stream of data.

**2.Formulating Adjacent Pairs:** Sliding windows are useful when you need to process adjacent pairs of elements in an ordered data structure, allowing you to easily access and operate on neighboring elements.

**3.Target Value Identification:** When you want to find a specific target value or combination of values in an array, a sliding window can help by adjusting the window size and efficiently searching for the desired value or subarrays that meet specific criteria.

**4.Longest/Shortest/Most Optimal Sequence:** Sliding windows are handy when you need to find the longest, shortest, or most optimal sequence that satisfies a given condition in a collection. By sliding a window through the collection and tracking relevant information within it, you can identify the desired sequence more efficiently than scanning the entire collection.

The main idea behind the sliding window technique is to convert **two nested loops into a single loop**. Usually, the technique helps us to reduce the time complexity from **O(n²) or O(n³) to O(n)**.

This is done by **maintaining a sliding window**, which is a **subarray of the original array** that is of a fixed size. The algorithm then iterates over the original array, updating the sliding window as it goes. This allows the algorithm to keep track of a contiguous sequence of elements in the original array, **without having to iterate over the entire array multiple times.**

  

- Sliding Window Technique is a popular method in algorithmic problems because of its high efficiency (mostly linear)
- It helps to avoid computing repetitive problems by computing only the new part that's introduced in the data set and discarding the one that moves out, usually 1 at a time.

**LAGANA KAHAN HAI????**

**⇒Sliding Window is very common in interviews and many questions that look like "(**_**Longest/Shortest/Number of**_**) (**_**Substrings/Subarrays**_**) with (**_**At most/Exactly**_**) K elements that fit (**_**some condition**_**)" have a common pattern. They are usually O(n).**

⇒

**How to Know, Where we use the Sliding Window?**

To know, Where we use the Sliding Window then we remember the following terms which is mentioned below:

Array, String, Sub Array, Sub String, Largest Sum, Maximum Sum, Minimum Sum

![image 2.png](../../../../../../Images/image%202.png)

⇒A **subarray** and a **substring** are both contiguous segments of an array or a string. Both must be contiguous, meaning there are no gaps in the sequence of elements or characters

⇒A **subsequence** in an array is a sequence that can be derived from the array by deleting some (or no) elements without changing the order of the remaining elements.

  

  

![image 1 2.png](../../../../../../Images/image%201%202.png)

**⇒ BRUTE FORCE**

→ TC⇒ O(N^2)

![image 2 2.png](../../../../../../Images/image%202%202.png)

**⇒ SLIDING WINDOW ALGORITHM**

![image 3.png](../../../../../../Images/image%203.png)

![image 4.png](../../../../../../Images/image%204.png)

  

![image 5.png](../../../../../../Images/image%205.png)

⇒ TC-O(N)

  

[https://leetcode.com/problems/grumpy-bookstore-owner/submissions/1377479304/](https://leetcode.com/problems/grumpy-bookstore-owner/submissions/1377479304/)

![image 6.png](../../../../../../Images/image%206.png)

![image 7.png](../../../../../../Images/image%207.png)

  

  

  

  

[https://www.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1](https://www.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1)

  

[https://leetcode.com/problems/minimum-size-subarray-sum/description/](https://leetcode.com/problems/minimum-size-subarray-sum/description/)

  

[https://leetcode.com/problems/max-consecutive-ones-iii/description/](https://leetcode.com/problems/max-consecutive-ones-iii/description/)

  

[https://leetcode.com/problems/longest-subarray-of-1s-after-deleting-one-element/description/](https://leetcode.com/problems/longest-subarray-of-1s-after-deleting-one-element/description/)

  

[https://leetcode.com/problems/subarray-product-less-than-k/description/](https://leetcode.com/problems/subarray-product-less-than-k/description/)

  

[https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/description/](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/description/)

  

[https://leetcode.com/problems/count-subarrays-with-score-less-than-k/description/](https://leetcode.com/problems/count-subarrays-with-score-less-than-k/description/)

  

[https://leetcode.com/problems/count-number-of-nice-subarrays/description/](https://leetcode.com/problems/count-number-of-nice-subarrays/description/)