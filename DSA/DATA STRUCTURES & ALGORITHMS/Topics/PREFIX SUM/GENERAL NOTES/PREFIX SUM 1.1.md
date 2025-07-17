# PREFIX SUM

→The **prefix sum algorithm** is a technique to efficiently compute the sum of elements in a subarray or range of an array.

→It precomputes cumulative sums to answer sum queries in constant time after an initial linear time preprocessing step.

Problem:

Given an array `arr[]` of size `n`, you want to efficiently compute the sum of elements from index `l` to `r` (inclusive), multiple times.

Without prefix sums, for each query, you would need to compute the sum manually, which takes O(n) for each query making TC N * N. With prefix sums, you can preprocess the array in O(n) and answer each sum query in O(1).

### Steps:

1. **Build the prefix sum array**:
    
    The prefix sum array `prefix[]` is an array where each element `prefix[i]` contains the sum of all elements from `arr[0]` to `arr[i]`.
    
    Mathematically:
    
    ```C++
    prefix[0] = arr[0]// Pehla hum khud se dalte hain
    prefix[i] = prefix[i-1] + arr[i]  (for i > 0)
    ```
    
2. **Answer sum queries**:

To get the sum of elements from index `l` to `r`, you can calculate it using the prefix sum array as:

```C++

sum(l, r) = prefix[r] - prefix[l-1]  (if l > 0)
sum(l, r) = prefix[r]  (if l == 0)
```

### Time Complexity:

- Preprocessing (computing the prefix sum array): O(n)
- Querying the sum of any subarray: O(1)

### Applications:

- Solving range sum problems efficiently.
- Multi-dimensional prefix sums can be used for 2D range queries (e.g., in grids).
- It’s often used in competitive programming when there are multiple range sum queries.

Code→

```C++
// Function to compute the prefix sum array
vector<int> computePrefixSum(const vector<int>& arr) {
int n = arr.size();
vector<int> prefix(n);
// Initialize the first element
prefix[0] = arr[0];
// Compute the prefix sum for the rest of the elements
for (int i = 1; i < n; i++) {
    prefix[i] = prefix[i - 1] + arr[i];
}
return prefix;
}

// Function to get the sum of elements from index l to r
int rangeSum(int l, int r, const vector<int>& prefix) {
if (l == 0) {
return prefix[r];
} else {
return prefix[r] - prefix[l - 1];
}
}
```

  

# SUFFIX SUM

### Suffix Sum Algorithm

The **suffix sum** is similar to the prefix sum, but instead of summing elements from the start of the array to a given index, you sum elements from a given index to the end of the array. It’s useful when you need to compute the sum of elements starting from some index `i` to the last element.

  

### Problem:

Given an array `arr[]` of size `n`, you want to efficiently compute the sum of elements from index `i` to the end (index `n-1`), multiple times.

### Steps:

1. **Build the suffix sum array**:
    
    The suffix sum array `suffix[]` is an array where each element `suffix[i]` contains the sum of all elements from `arr[i]` to `arr[n-1]`.
    
    Mathematically:
    
    ```CSS
    suffix[n-1] = arr[n-1]
    suffix[i] = suffix[i+1] + arr[i]  (for i < n-1) Since i is decreasing here
    ```
    
2. **Answer sum queries**:
    
    To get the sum of elements from index `i` to the end, you simply return `suffix[i]`.
    

### Example:

Let’s work through an example:

```C++

arr = [2, 4, 6, 8, 10]

```

### Step 1: Compute the suffix sum array

```CSS

suffix[4] = arr[4] = 10
suffix[3] = suffix[4] + arr[3] = 10 + 8 = 18
suffix[2] = suffix[3] + arr[2] = 18 + 6 = 24
suffix[1] = suffix[2] + arr[1] = 24 + 4 = 28
suffix[0] = suffix[1] + arr[0] = 28 + 2 = 30

```

So the suffix array will be:

```CSS

suffix = [30, 28, 24, 18, 10]
```

### Step 2: Query the sum of a subarray

To find the sum of elements from index `2` to the end:

```Scss

sum(2) = suffix[2] = 24
```

CODING IMPLEMENATION

```C++
vector<int> computeSuffixSum(const vector<int>& arr) {
    int n = arr.size();
    vector<int> suffix(n);
    
    // Initialize the last element
    suffix[n - 1] = arr[n - 1];
    
    // Compute the suffix sum for the rest of the elements
    for (int i = n - 2; i >= 0; i- -) {
        suffix[i] = suffix[i + 1] + arr[i];
    }
    
    return suffix;
}

// Function to get the sum of elements from index i to the end
int suffixSum(int i, const vector<int>& suffix) {
    return suffix[i];
}
```

  

**⇒Suffix sums are used in problems where you need to sum elements from the right part of an array multiple times.**

**⇒Useful in competitive programming for range queries, problems involving sliding windows, and more.**

### Key Differences:

|   |   |   |
|---|---|---|
|Aspect|**Prefix Sum**|**Suffix Sum**|
|**Definition**|The sum of elements from the start of the array (index `0`) to a given index `i`.|The sum of elements from a given index `i` to the end of the array (index `n-1`).|
|**Computation**|The sum at each index `i` is: `prefix[i] = arr[0] + arr[1] + ... + arr[i]`.|The sum at each index `i` is: `suffix[i] = arr[i] + arr[i+1] + ... + arr[n-1]`.|
|**Array Build**|Starts at index `0` and moves forward to the end.|Starts at the last index (`n-1`) and moves backward to the start.|
|**Usage**|Efficiently calculates the sum of any subarray from index `0` to `i` or between two indices (e.g., `sum(l, r)`).|Efficiently calculates the sum of elements from index `i` to the end of the array.|
|**Query Example**|To find the sum of elements between `l` and `r`, use: `prefix[r] - prefix[l-1]`.|To find the sum of elements from `i` to the end, use: `suffix[i]`.|
|**Initialization**|`prefix[0] = arr[0]`, `prefix[i] = prefix[i-1] + arr[i]` for `i > 0`.|`suffix[n-1] = arr[n-1]`, `suffix[i] = suffix[i+1] + arr[i]` for `i < n-1`.|
|**Typical Problem Use**|When you need to compute the sum of elements in the left part of the array or between any two indices.|When you need to compute the sum of elements in the right part of the array starting from a given index.|
|**Example Problem**|Find the sum of elements between indices `l` and `r`.|Find the sum of elements starting from index `i` to the end of the array.|

QUESTIONS

[https://leetcode.com/problems/running-sum-of-1d-array/description/](https://leetcode.com/problems/running-sum-of-1d-array/description/)

```C++
vector<int> runningSum(vector<int>& nums) {
      for(int i=1;i<nums.size();i++){
            nums[i]=nums[i-1]+nums[i];
        }
        return nums;
    }
```

  

[https://leetcode.com/problems/product-of-array-except-self/description/](https://leetcode.com/problems/product-of-array-except-self/description/)(REVISE)

MY CODE→

```C++
vector<int> productExceptSelf(vector<int>& nums) {
       int n=nums.size();
       vector<int>pf(n);
        pf[0]=nums[0];
        for(int i=1;i<n;i++){
            pf[i]=pf[i-1]*nums[i];
        }
        vector<int>sf(n);
       sf[n-1]=nums[n-1];
       for(int i=n-2;i>=0;i--){
        sf[i]=nums[i]*sf[i+1];
       }
       vector<int>res;
       res.push_back(sf[1]);
       for(int i=1;i<n-1;i++){
        res.push_back(pf[i-1]*sf[i+1]);
       }
     res.push_back(pf[n-2]);
       return res;
 }
```

![image 51.png](../../../../../Images/image%2051.png)

TC→O(3N)

SC→O(3N)

  

OPTIMISE KARNA BAKI HAI ISKO

  

  

  

  

[https://leetcode.com/problems/subarray-sum-equals-k/description/](https://leetcode.com/problems/subarray-sum-equals-k/description/)

YE SAWAL SLIDING WINDOW KA NAHI HAI BALKI PREFIX SUM KA HAI

  

  

  

[https://leetcode.com/problems/minimum-penalty-for-a-shop/description/](https://leetcode.com/problems/minimum-penalty-for-a-shop/description/)

  

  

[https://leetcode.com/problems/reducing-dishes/description/](https://leetcode.com/problems/reducing-dishes/description/)

  

```C++
int maxSatisfaction(vector<int>& s) {
        sort(s.begin(),s.end());
        int n=s.size();
        vector<int>sf(n);
        sf[n-1]=s[n-1];
        for(int i=n-2;i>=0;i--){
            sf[i]=sf[i+1]+s[i];
        }
        int time=1;
        int liketimec=0;
       for(int i=0;i<n;i++){
        if(sf[i]<0)continue;
        liketimec+=time*s[i];
        time++;
        }
        return liketimec;
        
    }
```

![image 1 26.png](../../../../../Images/image%201%2026.png)

![image 2 24.png](../../../../../Images/image%202%2024.png)


[https://leetcode.com/discuss/study-guide/5119937/Prefix-Sum-Problems](https://leetcode.com/discuss/study-guide/5119937/Prefix-Sum-Problems)

