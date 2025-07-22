So Um I’ll start with the basic algorithm first!

**→Sliding window** technique is a useful method for solving problems involving ==**subarrays or substrings**==, where you need to efficiently calculate results across overlapping segments of a larger array or string  
→It’s particularly handy when you want to optimize a solution that would otherwise involve recalculating results from scratch multiple times.  

##   
Sliding Window Concept:  

The idea is to maintain a "window" (a contiguous segment) of fixed or variable size that slides across the array or string. Instead of recomputing results from scratch every time the window moves, you update the results by removing the contribution of the element that leaves the window and adding the contribution of the new element that enters it.

  

## Types of Sliding Window:

1. **Fixed-size window**: This is when the size of the window remains constant, and the window slides one element at a time.
2. **Variable-size window**: In some problems, the size of the window changes dynamically based on certain conditions.

⇒While solving a problem using this algorithm we will generally be moving both our pointers, their individual movement being governed by some constraints specific to the problem and the distance between them being constantly tracked so as to get the global minimum or maximum. This is generally going to be the pattern for most of the problems.

⇒We can do some selective problems in O(n)

### **⇒The Sliding Window Technique** is a problem-solving technique that is used to

**1.Running Average:** Use a sliding window to efficiently calculate the average of a fixed-size window as new elements arrive in a stream of data.

**2.Formulating Adjacent Pairs:** Sliding windows are useful when you need to process adjacent pairs of elements in an ordered data structure, allowing you to easily access and operate on neighboring elements.

**3.Target Value Identification:** When you want to find a specific target value or combination of values in an array, a sliding window can help by adjusting the window size and efficiently searching for the desired value or subarrays that meet specific criteria.

**4.Longest/Shortest/Most Optimal Sequence:** Sliding windows are handy when you need to find the longest, shortest, or most optimal sequence that satisfies a given condition in a collection. By sliding a window through the collection and tracking relevant information within it, you can identify the desired sequence more efficiently than scanning the entire collection.

The main idea behind the sliding window technique is to convert **two nested loops into a single loop**. Usually, the technique helps us to reduce the time complexity from **O(n²) or O(n³) to O(n)**.

This is done by **maintaining a sliding window**, which is a **subarray of the original array** that is of a fixed size. The algorithm then iterates over the original array, updating the sliding window as it goes. This allows the algorithm to keep track of a contiguous sequence of elements in the original array, **without having to iterate over the entire array multiple times.**

  

**ADVANTAGES :**

- Sliding Window Technique is a popular method in algorithmic problems because of its high efficiency (mostly linear)
- It helps to avoid computing repetitive problems by computing only the new part that's introduced in the data set and discarding the one that moves out, usually 1 at a time.

## **LAGANA KAHAN HAI????**

**⇒Sliding Window is very common in interviews and many questions that look like "(**_**Longest/Shortest/Number of**_**) (**_**Substrings/Subarrays**_**) with (**_**At most/Exactly**_**) K elements that fit (**_**some condition**_**)" have a common pattern. They are usually O(n).**

# **FIXED SIZE**

![image 8.png](../../../../../Images/image%208.png)

![image 1 3.png](../../../../../Images/image%201%203.png)

![image 2 3.png](../../../../../Images/image%202%203.png)

![image 3 2.png](../../../../../Images/image%203%202.png)

![image 4 2.png](../../../../../Images/image%204%202.png)

**⇒ Window Size toh j-i+1 ho hoga na**

### [https://www.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1](https://www.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1)

```C++
   long maximumSumSubarray(int K, vector<int> &Arr , int N){
// code here
int i=0;   // dono ko 0 se hi start kiya hai
int j=0;
int maxs=INT_MIN;// depending upon the question
int sum=0;       // har window ka sum toh nikle ga na store kahan karenge?
while(j<N){      // since J hamesha aage rahega toh condition uspe lage gi
       sum+=Arr[j];  // yahan par window sum manage horaha hai
        if(j-i+1<K){  // if window size chota hai given size se toh window size bdhaya
            j++;  // window size bdahaya back ko elongate karke when i is fixed at 0
        }else if(j-i+1==K){  // size hit hogya 
            maxs=max(sum,maxs);  // Ab kam krne ka time agya // Kam kiya
            sum-=Arr[i];        //next window ki traf move karenge // kyonki next window
            i++;                // mein purane par jo arr[i] uski value nahi hogi
            j++;                // move to next i++ (window ka back aage badha)
                                // more to next j++( window ka front aage badha)
                                // since hum start mein hi add kar rahe hain arr[j] ko
                                // sum mein toh isliye yahan kuch nahi kiya
        }
    }
    return maxs;
}

```

[https://www.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1](https://www.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1)

MY APPROACH

```C++
 vector<long long int>res;
    long long int i=N-1;
    long long int j=N-1;  
    pair<long long int,long long int>neg;
    neg.first=INT_MAX;
    neg.second=-1;
    while(i>=0){   // main concept mera tha maine ulta sliding window lagaya hai yahan pe
        if(A[i]<0){
            neg.first=A[i];
            neg.second=i;
        }
        
        if(j-i+1<K){
             i--;
            
            
        }else if (j-i+1==K){
            (neg.first==INT_MAX)? (res.push_back(0)): (res.push_back(neg.first));
            
            i--;
            if(neg.second==j)neg.first=INT_MAX;  // agar last wala element remove kiya 
            j--;  // aur puri window mein vohi negative that in that case puri nayi window 
                 // koi negative aur nahi bachega // bina pair k value mein bakchodi hori thi
            }
    }
    reverse(res.begin(),res.end());
    return res;
```

  

ADITYA VERMA APPOACH

![image 5 2.png](../../../../../Images/image%205%202.png)

Total window bnti hai⇒ size-k+1

![image 6 2.png](../../../../../Images/image%206%202.png)

```C++
vector<long long> printFirstNegativeInteger(long long int A[],
                                             long long int N, long long int K) {
      int i=0;
      int j=0;
      vector<long long>res;
      queue<long long int>q;
      while(j<N){
          
          if(A[j]<0)q.push(A[j]);  // j calculation
          
          if(j-i+1<K){
              j++;
          }else if(j-i+1==K){
              (q.empty())?res.push_back(0):res.push_back(q.front()); // ans calculation
              
              if(!q.empty()&&q.front()==A[i])q.pop(); // i ki calculation
              
              
              i++;   // window slide kardo
              j++;
          }
          
    }
     return res;
 }
```

  

Q→[https://www.geeksforgeeks.org/problems/count-occurences-of-anagrams5839/1](https://www.geeksforgeeks.org/problems/count-occurences-of-anagrams5839/1)(REVISE)

MY APPROACH

```C++
int search(string pat, string txt) {
	    // code here
	    int k=pat.length();
	    int i=0;
	    int j=0;
	    int count=0;
	    unordered_map<char,int>m1;
	    for(int i=0;i<pat.length();i++){
	        m1[pat[i]]++;
	    }
	    unordered_map<char,int>m2;
      while(j<txt.length()){
	        m2[txt[j]]++;
	        
	        if(j-i+1<k){
	            j++;
	        }else if (j-i+1==k){
	            if(m2==m1)count++;
	            m2[txt[i]]--;
	            if(m2[txt[i]]==0)m2.erase(txt[i]);
	            i++;
	            j++;
	            }
	        
	        }
	        return count;
	}
```

⇒ SLIDING WINDOW K ANDAR EK BAR MAINE NOTICE KI KOI SYSTEM HAI JISMEIN KUCH EK PART ADD HORA HAI AND EK PART REMOVE HORAHA HAI

![image 7 2.png](../../../../../Images/image%207%202.png)

ADITYA VERMA APPROACH( 4/9/24 ko choda hai jabh revise kare toh ye swal karna fir se)

  

Q→[https://leetcode.com/problems/sliding-window-maximum/description/](https://leetcode.com/problems/sliding-window-maximum/description/)

Is sawal ki khasbat ye hai ki abhi tak wo jo element add ya remove horahe the unse order/configuration system ka change nahi hora tha but yahan hora hai

![image 8 2.png](../../../../../Images/image%208%202.png)

![image 9.png](../../../../../Images/image%209.png)

![image 10.png](../../../../../Images/image%2010.png)

  

```C++
vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        deque<int>dq;
        vector<int>res;
        int i=0;
        int j=0;
        int n=nums.size();
        int max=INT_MIN;
        while(j<n){
         while(!dq.empty()&&dq.back()<nums[j]){
                dq.pop_back();
              }
            dq.push_back(nums[j]);
            
          if(j-i+1<k){
            j++;
          }else if(j-i+1==k){
            res.push_back(dq.front());
            if(dq.front()==nums[i])dq.pop_front();
            i++;
            j++;
            }
        }
        return res;
    }
```

  

LEETCODE

[https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k/](https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k/)

[https://leetcode.com/problems/find-all-anagrams-in-a-string/solutions/92007/sliding-window-algorithm-template-to-solve-all-the-leetcode-substring-search-problem/](https://leetcode.com/problems/find-all-anagrams-in-a-string/solutions/92007/sliding-window-algorithm-template-to-solve-all-the-leetcode-substring-search-problem/)