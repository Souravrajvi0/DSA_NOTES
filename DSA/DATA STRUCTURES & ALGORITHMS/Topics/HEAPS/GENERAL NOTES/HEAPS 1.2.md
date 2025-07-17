## Representation

⇒JAISE STACK KO REPRESENT KARTE HAIN! WAISE HI HEAP KO KRTE HAIN!
- WITH SIZE K


![image 53.png](../../../../../Images/image%2053.png)

## HOW TO IDENTIFY HEAP QUESTIONS
LOOK FOR TWO KEYWORDS
K AND SMALLEST/LARGEST

![image 1 27.png](../../../../../Images/image%201%2027.png)

## WHICH HEAP TO CHOOSE?

![image 2 25.png](../../../../../Images/image%202%2025.png)

SIZE TOH K HI HOTA HAI HEAP KA!
## ⇒The Significance of K

HEAP K QUESTIONS MEIN EK SIMPLE SOLUTION  SAMAJH MEIN AEGA WO AEGA SORTING KA!!!
KI KUCH NA HO TOH SORTING KAR LO!

![image 3 20.png](../../../../../Images/image%203%2020.png)

⇒Sorting mein sabse achi complexity deta ha**i Merge Sort** so for that TC → O(nlogn)

⇒So when we use a heap of Size K the complexity comes down to nlogK

![image 4 18.png](../../../../../Images/image%204%2018.png)

![image 5 16.png](../../../../../Images/image%205%2016.png)

![image 6 16.png](../../../../../Images/image%206%2016.png)

![image 7 15.png](../../../../../Images/image%207%2015.png)



SMALLEST KTH KO AESE SOCHNA KI JABH SORTING HOGI IN SIZE OF ARRAY N THEN 
- IN THE SMALL ARAY OF SIZE K THE LAST ELEMENT IS GOING TO BE THE KTH SMALLEST ELEMENT IN THE WHOLE ARRAY 
- THE BIGGEST IN THE SMALL K ARRAY!
So When it is going to be the biggest in the smallest array k then we could use a max heap and if the size exceeds from K then we could just remove the top element! 
if Size becomes K+1 Then for sure the top element is not going to be our answer just like that we could traverse the whole array and adding elements in the heap!
And in the end Top element of the heap is going to be our answer!


![HEAPS 1.2-20250103101454441.webp](../../../../../Images/HEAPS%201.2-20250103101454441.webp)
### Max-Heap Using `priority_queue`

A **max-heap** is the default behavior of `priority_queue` in C++. The maximum element is always at the top.

**Max-Heap Declaration:**

```C++
 priority_queue<int> maxHeap;
```

**Min-Heap Declaration:**

```C++
 priority_queue<int, vector<int>, greater<int>> minHeap;
```

### Functions for `priority_queue`

Here are the commonly used functions available for `priority_queue` in C++:

```C++
priority_queue<int> maxHeap;
priority_queue<int, vector<int>, greater<int>> minHeap;
//  implement usinged using vector and greater is a comparator here!
//Why not just greater?
//If you write only greater, the compiler doesn't know what data type
// it should use for the comparison. Since greater is a generic template
// that can work with different types, you need to specify the type, 
//like greater<int>, to let the compiler know how to specialize it.
// toh fir ye chijein mine maxheap mein kyon nahi use ki??
// well vector<int> and less<int>(default comparator hai)
-------------------------------
maxHeap.push(10);  // Adds 10 to the max-heap
minHeap.push(5);   // Adds 5 to the min-heap

minHeap.top();
maxHeap.top();

-------------------------------
maxHeap.pop();  // Removes the maximum element from the max-heap
minHeap.pop();  // Removes the minimum element from the min-heap


------------------------------
if (maxHeap.empty()) {
    // Max-heap is empty        // goes for both
}
--------------------
 vector<int> vec = {10, 30, 20, 5, 7, 50};
    
    // Create a max-heap (default behavior) using the vector's values
priority_queue<int> maxHeap(vec.begin(), vec.end());
// same can be done fot the min heap also just put the vector iterators in it!

--------------------------------
int heapSize = maxHeap.size();  // Gets the number of elements in the max-heap


-------------------------------
WITH PAIR
priority_queue<pair<int, int>> maxHeap;
priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> minHeap;

minHeap.push(make_pair(10, 1));  // First element 10, second element 1

---------------------------------
\#define pip pair<int, int>

int main() {
    // Min-heap with pip (pair<int, int>)
    priority_queue<pip, vector<pip>, greater<pip>> minHeap;

    // Inserting pairs into the min-heap
    minHeap.push(make_pair(10, 1));  // First element 10, second element 1
```

```C++

priority_queue<int, vector<int>, greater<int>> minhp(nums.begin(), nums.end());

```

### Breakdown:

1. `priority_queue<int, vector<int>, greater<int>>`:
    - `**priority_queue<int>**`: This creates a priority queue of type `int`, but by default, `priority_queue` is a **max-heap**.
    - `**vector<int>**`: The underlying container to store the elements is a `vector<int>`. By default, a `priority_queue` uses `vector` as the container.
    - `**greater<int>**`: This is a comparison function (called a **comparator**) that ensures the priority queue behaves as a **min-heap**. Instead of the default **max-heap**, it now keeps the smallest element at the top.
2. `**minhp(nums.begin(), nums.end())**`:
    - `**nums.begin(), nums.end()**`: These are iterators to the beginning and the end of a container named `nums`. This will initialize the min-heap with all the elements in the `nums` container.
    - This constructor takes a range of elements (from `nums.begin()` to `nums.end()`) and inserts them into the priority queue.

  

Q→[https://www.geeksforgeeks.org/problems/kth-smallest-element5635/1](https://www.geeksforgeeks.org/problems/kth-smallest-element5635/1)

MY APPROACH

```C++
  // k : find kth smallest element and return using this function
    int kthSmallest(vector<int> &arr, int k) {
        // code here
        priority_queue<int>mh;
        
        for(int i=0;i<arr.size();i++){
            mh.push(arr[i]);
            if(mh.size()>k){    // MAIN HEAP KA SIZE K SE GREATER NAHI HONE DUNGA
                mh.pop();       // PEHLE MAT LIKH DENA YE IF CONDITION
            }
        }
        return mh.top();
        
    }
```

**→ In the array of size n the kth smallest will be the top of top/greatest of the array of size k**

→ **HEAP MEIN ELEMENT JARURI NAHI SORTED HO,BAS YE GURANTEE HOTI HAI KI TOP MAX/MIN HOGA**

ALTERNATIVE APPROACH

```C++
int findKthSmallest(vector<int>& arr, int k) {
    // Min-heap to store elements
    priority_queue<int, vector<int>, greater<int>> minHeap(arr.begin(), arr.end());

    // Pop k-1 elements from the min-heap
    for (int i = 1; i < k ; ++i) {
        minHeap.pop();  /// min heap mein sare elements dal do for k-1 pop kardo 
    }                   ///  ab top par kya bacha -> APNA ANSWER BHAI

    // The k-th smallest element is now at the top of the min-heap
    return minHeap.top();
}
```

  

[https://leetcode.com/problems/kth-largest-element-in-an-array/description/](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)

```C++
 int findKthLargest(vector<int>& nums, int k) {

     priority_queue<int,vector<int>,greater<int>>mp;
        for(int i=0;i<nums.size();i++){
            mp.push(nums[i]);
            if(mp.size()>k){
                mp.pop();
            }
        }
        return mp.top();
    }
```

→Ek tarike se main ye bhi keh skta huon ki heap jo // jaise min heap vo larger elements ko bachaega aur choto ki marega and vise versa for the Max heap

  

[https://www.geeksforgeeks.org/problems/kth-smallest-element5635/1](https://www.geeksforgeeks.org/problems/kth-smallest-element5635/1)

  

MY APPROACH

```C++
 vector <int> nearlySorted(int arr[], int num, int K){
        // Your code here
        vector<int>res;
        priority_queue<int,vector<int>,greater<int>>minh;
        for(int i=0;i<=K;i++){
            minh.push(arr[i]);
        }
        for(int i=K+1;i<num;i++){
            res.push_back(minh.top());
            minh.pop();
            minh.push(arr[i]);
        }
        while(!minh.empty()){
            res.push_back(minh.top());
            minh.pop();
        }
        return res;
    }
```