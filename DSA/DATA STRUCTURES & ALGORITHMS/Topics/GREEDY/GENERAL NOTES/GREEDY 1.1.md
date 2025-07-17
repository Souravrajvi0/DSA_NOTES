# **Algorithmic Paradigms**

## Brute Force

To find a solution to a problem find all the ways or explore the possibilities and then take The way which gives you the best result.

![image 36.png](../../../../../Images/image%2036.png)

  

## Dynamic Programming

It’s an optimization on brute force, Since in brute force We tend to repeatedly calculate subproblems. So That’s we tend to store to store the answer of a particular subproblem and then We don’t have to compute it again and again. We just save ourself from re solving the problem again

  

## Divide And Conquer

Here we divide our problem in smaller sub problems and or keep on dividing em until we find the minute problems whose solutions we already know or Solve em individual subproblems(since we know em) and by those we get the solution of the bigger problem

Ex→ Merge sort ,Quick Sort, Binary Search

**THIS IS DIFERENT FROM RECURSION**
Take Example of Recursion of Fibonacci Number
![image 1 14.png](../../../../../Images/image%201%2014.png)

==**This Recursion is related more to brute force Recursion , Kyonki yahan par problem ka repetition hai, Divide and conquer mein problem ka repetition nahi dekhte**==

### DIFERRENCE BETWEEN DIVIDE AND CONQUER AND BRUTE FORCE

### 1. **Approach to Problem-Solving**:

- **Brute Force**:
    - Brute force is a straightforward approach where every possible option or combination is tried to find the solution. When applied recursively, it doesn’t necessarily optimize the problem structure.
    - It often involves solving the same subproblem multiple times without reducing the problem size in an optimal way.
    - Example: In recursive solutions to the Fibonacci sequence using brute force, the same subproblems like calculating `fib(n-1)` and `fib(n-2)` are solved multiple times.

- **Divide and Conquer**:
    - This is a more structured approach where the problem is divided into independent, smaller subproblems that are recursively solved. These subproblems are often disjoint, so no subproblem is repeated unnecessarily.
    - Divide and Conquer ensures that once a subproblem is solved, its result is reused, avoiding the inefficiency of recomputing it multiple times.
    - Example: Merge Sort divides the array into halves, recursively sorts each half, and then merges the results, avoiding re computation of the same data.

### 2. **Overlapping Subproblems**:

- **Brute Force**:
    - Recursion in brute force can lead to solving the same subproblem multiple times. For example, in the Fibonacci sequence, both `fib(n-1)` and `fib(n-2)` involve multiple redundant calculations of `fib(n-3)`, `fib(n-4)`, etc.
    - This lack of optimization leads to exponential time complexity in many brute-force recursive algorithms.
- **Divide and Conquer**:
    - In Divide and Conquer, subproblems are typically independent, meaning that no subproblem is repeated. Once a subproblem is solved, its result is reused or combined with others.
    - This leads to much better performance in terms of time complexity compared to brute-force recursion.

### 3. **Time Complexity**:

- **Brute Force**:
    - Recursive brute-force solutions often have higher time complexity because they don't avoid recomputation and may explore all possible combinations of a solution space. For example, the brute force recursive Fibonacci sequence solution has a time complexity of O(2^n).
- **Divide and Conquer**:
    - Divide and Conquer solutions generally have more optimal time complexity. They divide the problem into subproblems, solve each subproblem independently, and combine their results. For example, Merge Sort has a time complexity of O(n log n).

### 4. **Optimal Substructure**:

- **Brute Force**:
    - Brute force does not necessarily exploit optimal substructure (i.e., solving subproblems optimally to build up a solution to the original problem).
- **Divide and Conquer**:
    - Divide and Conquer takes advantage of the optimal substructure property, meaning that the solution to the problem is built from the optimal solutions of its subproblems. This characteristic leads to more efficient algorithms.

### 5. **Example: Fibonacci Sequence**:

- **Brute Force Recursive Solution**:
    
    - Each recursive call may lead to recomputation of the same values repeatedly. For example, `fib(n-1)` and `fib(n-2)` will both call `fib(n-3)`, leading to a lot of overlap in recursive calls. This results in exponential time complexity.
    
    ```Python
    pythonCopy code
    def fib(n):
        if n <= 1:
            return n
        return fib(n-1) + fib(n-2)
    
    ```
    
    - **Time Complexity**: O(2^n)
- **Divide and Conquer** (Dynamic Programming with Memoization):
    
    - Memoization or caching is used to store the results of subproblems so they are not recomputed, ensuring that each subproblem is solved only once.
    
    ```Python
    pythonCopy code
    def fib(n, memo={}):
        if n <= 1:
            return n
        if n not in memo:
            memo[n] = fib(n-1, memo) + fib(n-2, memo)
        return memo[n]
    
    ```
    
    - **Time Complexity**: O(n)

### 6. **Example: Sorting Algorithms**:

- **Brute Force**:
    - **Selection Sort**, where the array is scanned repeatedly to select the next element in order, is an example of brute force. It has a time complexity of O(n²) because every element is compared against others repeatedly.
- **Divide and Conquer**:
    - **Merge Sort** is a classic example of a divide-and-conquer algorithm. The array is recursively divided in half, sorted independently, and then merged. Its time complexity is O(n log n), which is much more efficient than brute force sorting algorithms.

### 7. **Conceptual Difference**:

- **Recursion**:
    - A method of solving problems where a function calls itself to solve smaller instances of the same problem.
    - It doesn't necessarily have a specific structure or pattern for breaking down the problem.
    - Any problem can be recursive if the function repeatedly calls itself with a smaller input until a base case is reached.
- **Divide and Conquer**:
    - A specific algorithmic paradigm that involves dividing the problem into two or more independent subproblems of similar type, solving them recursively, and combining their results to solve the original problem.
    - It consists of three steps:
        1. **Divide**: Split the problem into subproblems.
        2. **Conquer**: Solve each subproblem (often recursively).
        3. **Combine**: Merge the solutions of the subproblems to get the solution to the original problem.
    - Examples of Divide and Conquer algorithms include Merge Sort, Quick Sort, and Binary Search.

### 8. **Problem Structure**:

- **Recursion**: Doesn’t always require dividing the problem into independent subproblems; the recursive call can act on a smaller part of the input without division.
    - Example: Calculating the factorial of a number (`n! = n * (n-1)!`) is recursive but not divide and conquer.
- **Divide and Conquer**: Specifically emphasizes dividing the problem into smaller independent subproblems that can be solved individually and then recombining them.
    - Example: Merge Sort breaks an array into halves, sorts each half recursively, and then merges the sorted halves.

### 9. **Combining Results**:

- **Recursion**: Some recursive problems don't involve combining sub-solutions (e.g., factorial or Fibonacci sequence).
- **Divide and Conquer**: Always involves combining results from subproblems (e.g., in Merge Sort, the results from sorting two halves are combined to form the final sorted array).

  

## GREEDY ALGORITHMS

Yahan humein saari posibillities explore krne ki jarurat nahi hai

YAHAN HUM **LOCAL OPTIMISATION** KI TRAF DEKHTE HAIN

Example:

![image 2 12.png](../../../../../Images/image%202%2012.png)

A se b jana hai and 5 paths and unmein constraints hai toh in that case wo path lo jismein least amount of resistance ho

![image 3 10.png](../../../../../Images/image%203%2010.png)

Agar Humare starting mein panch tarike hain se pehla Step le skte ho then in that case hum 5 tariko ko immediately Judge karenege

# PATTERN 1

Q→[https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/submissions/1380690902/](https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/submissions/1380690902/)

MY APPROACH

```C++
 int largestSumAfterKNegations(vector<int>& nums, int k) {
        while(k>0){
           pair<int,int>min=make_pair(nums[0],0);
          for(int i=1;i<nums.size();i++){
             if(min.first>nums[i]){
                 min.first=nums[i];
                 min.second=i;
             }
            }
          nums[min.second]*=-1;
          k--;
        }
        int sum=0;
        for(int i=0;i<nums.size();i++){
            sum+=nums[i];
        }
        return sum;
```

Since Choices toh yahan bhi hongi but har ek choice mein sabse better wali main choose kar lunga and aage badh jaunga  
Which Means GREEDY MEIN CHOICES HONGI HUMEIN BAS UNHE OPTIMISE KARNA HAI  

**→GENERALLY GREEDY K QUESTION MEIN OPTIMALITY KI PROBLEM MILEGI KI BEST SUM KYA HAI YA MAX SUM KYA HAI→ KYONKI YAHAN GREEDY LAGANE SE KUCH FARAK NAHI PADEGA ANSWER PAR, SINCE IN CASE AGAR DIYA HO MAX SUM NKALNA HAI TOH HAR BAR JO SABSE BADA ELEMENT HAI WO CHOOSE KAR LO.**

BRUTE FORCE

![image 4 9.png](../../../../../Images/image%204%209.png)

![image 5 8.png](../../../../../Images/image%205%208.png)

YAHAN AGAR DEKHA JAYE NA BRUTE FORCE KI JARURAT THI NI,ASSUME SARE NUMBER POSTIVE HAIN TOH IN THAT CASE IT KINDA MAKES SENSE NA KI WE ONLY JUST NEGATE THE SMALLEST ELEMENT . TOH BAR BAR USS ELEMENT PAR NEGATE KRTE RAHO

  

![image 6 8.png](../../../../../Images/image%206%208.png)

### **→LOCAL OPTIMISATION OBSERVATION PAR HOTA HAI**

### →GREEDY K QUESTION K SATH EK CHIZ REHTI HAI YE TOH TUM UNHE MATHEMATICALLY PROVE KARO YA INTUTIVELY PROVE KARO

### →SO YAHAN SARI POSSIBILTIES KO EXPLORE KRNE KI JARURAT NAHI HAI

### **→GREEDY IS ALL ABOUT LOCAL OPTIMUM**

### **→ KAI BAR MAIN KAHIN GREEDY LAGUNGA WO GHALAT ANSWER DETA HAI SINCE WE LOOK FOR LOCAL OPTIMISATION AND SAHI NAHI HOTA HAI**

![image 7 7.png](../../../../../Images/image%207%207.png)

**→ Ache test case se hum apni greedy approach ko test kar skte hain and find out if that works on it**

```C++
int largestSumAfterKNegations(vector<int>& nums, int k) {
        priority_queue<int,vector<int>,greater<int>>minhp(nums.begin(),nums.end());
       int sum=0;
       for(int i=0;i<nums.size();i++)sum+=nums[i];
       while(k--){
          int el=minhp.top();
          if(el==0)break;
          minhp.pop();
          sum-=el;
          minhp.push(-el);
          sum+=(-el);
        }
        return sum;

    }
```

![image 8 7.png](../../../../../Images/image%208%207.png)

→GREEDY KI 50/60 % problems mein Sorting ya priorty queue lag raha hota hai, Kyonki humein ek certain element chahiye hota hai na local optimisation k liye that comes through some sort of order and order k liye liye sorting ya Priority queue hi better option hai

→AGAR SOLUTION MEIN IF AND BUTS AARE HAI NA THEN GREEDY MIGHT NOT BE THE RIGHT APPROACH FOR YOUR PROBLEM

---

**FRACTIONAL KNAPSACK**

[https://www.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card](https://www.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card) (REVISE)

MY APPROACH→ APPROACH SAHI HAI CODE BHI SAHI SA HAI BUT ERROR AEGA PQ KI VJAH SE

```C++
 double fractionalKnapsack(int w, Item arr[], int n) {
// Your code here
priority_queue<double,pair<int,int>>maxhp;// YE ERROR DEGA
for(int i=0;i<n;i++){
Item temp=arr[i];
double valpg=(double)temp.value/temp.weight;
int value=temp.value;
int weight=temp.weight;
maxhp.push({valpg,{value,weight}});
}
    double maxval=0.0;
    while(!maxhp.empty()&&w>0){
     pair<double,pair<int,int>>p=maxhp.top();
    int itemWeight = p.second.second;
    int itemValue = p.second.first;
    double valuePerUnitWeight = p.first;
    if (w >= itemWeight) {
        w -= itemWeight;
        maxval += itemValue;
    } else {

        maxval += w * valuePerUnitWeight;
        w = 0;
    }


    }
    return maxval;
}
```

**→STL JO HOTA HAI NA PRIORITY QUEUE KA USMEIN, AGAR SIGNATURE CHANGE KAROGE TOH NAYA COMPARATOR ADD KARNA PADEGA**

Q→[https://leetcode.com/problems/maximum-units-on-a-truck/description/](https://leetcode.com/problems/maximum-units-on-a-truck/description/)

MY APPROACH, kitna chutiya code hai mera

```C++
int maximumUnits(vector<vector<int>>& b, int ts) {
        priority_queue<pair<int,int>>maxhp;
        for(int i=0;i<b.size();i++){
           int numb=b[i][0];
           int numu=b[i][1];
           maxhp.push({numu,numb});
        }
        int max=0;
        while(ts--&& !maxhp.empty()){
        pair<int,int>p=maxhp.top();
        if(p.second==1){
            max+=p.first;
            maxhp.pop();
        }else{
        max+=p.first;
        maxhp.pop();
        maxhp.push({p.first,p.second-1});
        }
     }
      return max;
        
    }
```

```C++
   int maximumUnits(vector<vector<int>>& boxTypes, int truckSize) {
        priority_queue<pair<int,int>> maxhp;
        for(const auto& b : boxTypes) {
            maxhp.push({b[1], b[0]});  // {units per box, number of boxes}
        }
        
        int totalUnits = 0;
        while (truckSize > 0 && !maxhp.empty()) {
            auto [unitsPerBox, numBoxes] = maxhp.top();
            maxhp.pop();
            
            int boxesToAdd = min(numBoxes, truckSize);
            totalUnits += boxesToAdd * unitsPerBox;
            truckSize -= boxesToAdd;
        }
        
        return totalUnits;
    }
    // ye approach better hai
```

![image 9 6.png](../../../../../Images/image%209%206.png)

SANKET SIR KI APPROACH

[https://leetcode.com/problems/boats-to-save-people/description/](https://leetcode.com/problems/boats-to-save-people/description/)

MY APPROACH BHAYANKAR CHUTIYA

```C++
 bool sendtwo(vector<int>& people, int limit,int &size){
        int low =0;
        int high=people.size()-1;
        pair<int,int>p={-1,-1};
        while(low<high&&high>=0&&low<people.size()){
            if(people[low]==-1){
                low++;
                continue;
            }
            if(people[high]==-1){
                high--;
                continue;
            }
          int weight=people[low]+people[high];
          if(weight<limit){
            p.first=low;
            p.second=high;
            low++;
          }else if(weight>limit){
            high--;
          }else if(weight==limit){
              people[low]=-1;
              people [high]=-1;
              size-=2;
              return true;
          }
        }
         if (p.first != -1 && p.second != -1 && people[p.first] + people[p.second] <= limit) {
            people[p.first] = -1;
            people[p.second] = -1;
            size -= 2;
            return true;
        }
      
        return false;
       }
       
    
    int numRescueBoats(vector<int>& people, int limit) {
        sort(people.begin(), people.end());

        int size=people.size();
        int boat=0;
        while(size!=0&&size>0&&sendtwo(people,limit,size)){
         boat+=1;
        }
        for(int i=0;i<people.size();i++){
            if(people[i]!=-1){
                boat++;
            }
        }
        return boat;
}
```

SIR APPROACH

```C++
 int numRescueBoats(vector<int>& people, int limit) {
         int ans = 0;
        sort(people.begin() , people.end());
        int left = 0 , right = people.size() - 1;
        while(left <= right){
            if(people[left] + people[right] <= limit){
                ans ++;
                left++;
                right--;
            } else {
                ans ++;
                right--;
            }
        }
        return ans;
    }
```

# PATTERN 2

NOW THERE’S THIS ANOTHER FLAVOUR OF GREEDY→ SIRF YEHI KARA TOH KYA HOGA

Q→[https://www.geeksforgeeks.org/problems/maximum-product-subset-of-an-array/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card](https://www.geeksforgeeks.org/problems/maximum-product-subset-of-an-array/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card)

Pure cases bna le karna hota hai

  

  

[https://www.geeksforgeeks.org/problems/minimum-cost-to-cut-a-board-into-squares/1](https://www.geeksforgeeks.org/problems/minimum-cost-to-cut-a-board-into-squares/1)(REVISE)

  

  

[https://leetcode.com/problems/construct-string-with-repeat-limit/description/](https://leetcode.com/problems/construct-string-with-repeat-limit/description/)