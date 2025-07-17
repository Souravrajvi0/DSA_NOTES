Recursion is a programming technique where a function calls itself directly or indirectly to solve a problem. It involves breaking down a problem into smaller, more manageable sub-problems, each of which is a smaller instance of the original problem.

### Key Concepts in Recursion:

1. **Base Case:** The simplest case that can be solved without further recursion. It prevents infinite recursion by providing a condition under which the function stops calling itself.
2. **Recursive Case:** **The part of the function that reduces the problem size and makes a recursive call to itself**.
3. **Call Stack:** Recursion relies on the call stack to keep track of function calls. Each recursive call adds a new layer to the stack, and when the base case is reached, the function calls start returning, unwinding the stack.

### Example: Factorial Calculation

A classic example of recursion is the calculation of the factorial of a number n:

n!=n×(n−1)×(n−2)×⋯×1

```C++
int factorial(int n) {
if (n == 0) {  // Base Case
 return 1;
}  
return n * factorial(n - 1);
}
```
![DP 1.1-20241226085638704.webp](../../../../../../Images/DP%201.1-20241226085638704.webp)

Yahan Par Subproblems bari bari calculate horahi hai! toh yeh Main problem hai!!
Even In recursion we have a space complexity of O(n) which in turn is of Call stack space.
TC BHI O(2^N) TYPE AARAHI HAI!
![DP 1.1-20241226085954967.webp](../../../../../../Images/DP%201.1-20241226085954967.webp)

### Multiple Recursive Calls and Overlapping Subproblems

In general, **Whenever you have multiple recursive calls within a recursive function, you risk overlapping subproblems if those recursive calls can lead to the same computations being performed more than once.**
- You **don't always need more than one recursive call** to apply DP.
- If the problem involves **overlapping subproblems** (even with one recursive call), **DP** can help by storing solutions to avoid redundant calculations.

### Dynamic Programming (DP)

Dynamic Programming is an optimization technique used to solve problems that can be broken down into smaller, overlapping subproblems. Unlike simple recursion, which may repeatedly solve the same subproblems, DP stores the results of these subproblems and reuses them, thus reducing the time complexity.

In recursion, especially when dealing with problems that involve overlapping subproblems, dynamic programming (DP) can be an effective technique to optimize the solution

![DP 1.1-20241226090030831.webp](../../../../../../Images/DP%201.1-20241226090030831.webp)


### 1. **Top-Down Approach (Memoization+Recursion):**

**Concept:** This approach involves solving the problem recursively and storing the results of subproblems to avoid redundant calculations.  
BASICALLY YAHAN PAR HUMEIN KOI BHI VALUE MILTI HAI USE MEIN STORE KAR LUNGA DP ARRAY K ANDAR!!

**How it works:**

1. Start with the original problem and break it down into smaller subproblems.
2. Solve each subproblem recursively, storing the results in a table (usually a dictionary or array).
3. If a subproblem has already been solved (i.e., it’s in the table), return the stored result instead of recalculating it.
4. The recursion continues until the base case is reached.

![image 3 16.png](../../../../../../Images/image%203%2016.png)

![image 4 14.png](../../../../../../Images/image%204%2014.png)
### 2. **Bottom-Up Approach (Tabulation/Iterative):**

**Concept:** This approach involves solving all subproblems first and then using their results to build up the solution to the original problem.  

- In this approach, you start by solving the smallest subproblems (like F(0)and F(1)), then iteratively compute larger subproblems until you reach the desired F(n).
  
**How it works:**

1. Define a table (usually an array) to store the results of subproblems.
2. Start by solving the smallest subproblems (usually the base cases) and store their results in the table.
3. Use the results of the smaller subproblems to solve larger subproblems, filling up the table as you go.
4. The last entry in the table will contain the solution to the original problem.

![image 5 12.png](../../../../../../Images/image%205%2012.png)

*This is The best approach in terms of complexity Since yahan par recursive stack mein bhi kuch nahi aya! 

---

Q1→[https://leetcode.com/problems/min-cost-climbing-stairs/](https://leetcode.com/problems/min-cost-climbing-stairs/)

![image 6 12.png](../../../../../../Images/image%206%2012.png)

→Yahan mujhe cost ko minimize karna hai toh zaruri nahi hai ki main shortest path hi luon

→Yahan Greedy lagane ka koi fayda nahi hoga kyonki greedy mein kya hoga , Kisi point par main aya and uske bad maine dekha agle dono options mein kam cost kiski hai toh in that case fir hoga ye ki kuch ghlat path aa jaega→ 10/15→ 10 choose kiya and then Fir 15 choose kiya toh total cost agya 25.

jabki agar main pehle 15 par gya hota toh in that case mere hota total cost 15 hi

![image 7 11.png](../../../../../../Images/image%207%2011.png)

```C++
// recursive solution
class Solution {
public:

    int findmin(int sum,vector<int>& cost,int i){
        if(i>=cost.size())return sum;
         
         int sum1=findmin(sum+cost[i],cost,i+1);
         int sum2=findmin(sum+cost[i],cost,i+2);
         return min(sum1,sum2);
 }

int minCostClimbingStairs(vector<int>& cost) {
        
        return min (findmin(0,cost,0),findmin(0,cost,1));
        }
};
// problem hai TLE KI yahan toh recursion se DP par jane ka idea dimag mein ata hai
```

![image 8 11.png](../../../../../../Images/image%208%2011.png)

SO THE THING IS →KISI BHI RECURSIVE SOLUTION PAR DP KAISE LAGAUNGA??????

DP ARRAY KA USE KRTE HAIN→ KAISE ?? HAR STAIR PAR ANE KA EK MINIUM COST HOTA HAI USEE HI SAVE KARLO DP ARRAY MEIN

  

→dp[i]=min cost upto till now for that particular step

→So in the case of using Dp array what i need to make sure is that i understand the significance of the DP array.Jaise yahan par ye Min cost of that step ko batayega.

→When we are trying to go from 0→n in a recursive solution then we are trying to implement the memoization we should go for The other direction from n→0 // Thoda convernient hojata hai

→MEMOIZATION METHOD

```C++
class Solution {
public:

    int findmin(vector<int>& cost,int i,vector<int>& dp){
        if(i>=cost.size())return 0;// we return 0 kyonki upar ane k bad we don't have anything to return
        if(dp[i]!=-1)return dp[i];

        int sumofchoice1=cost[i]+findmin(cost,i+1,dp);
        int sumofchoice2=cost[i]+findmin(cost,i+2,dp);
        dp[i]=min(sumofchoice1,sumofchoice2);
        return dp[i];
 }

int minCostClimbingStairs(vector<int>& cost) {
        vector<int> dp(cost.size(),-1);
        return min (findmin(cost,0,dp),findmin(cost,1,dp));
        }
};
//Yahan flow hai upar ka mtlb niche se upar jare hain!
What if I want to go from upar se niche in that case base case mein change aa jayega
```

Now we go upar se niche

  

```C++
   class Solution {
public:
int findmin(vector<int>& cost, int i, vector<int>& dp) {
if (i == 0) return cost[0]; // Base case for the first step
if (i == 1) return cost[1]; // Base case for the second step
//   if(i==0||i==1)return cost[i];
if (dp[i] != -1) return dp[i]; // Return the memoized result if already computed
    // Recursive case: compute the minimum cost from this step
    int sumofchoice1 = cost[i] + findmin(cost, i - 1, dp);
    int sumofchoice2 = cost[i] + findmin(cost, i - 2, dp);

    dp[i] = min(sumofchoice1, sumofchoice2); // Memoize the result
    return dp[i];
}

int minCostClimbingStairs(vector<int>& cost) {
    int n = cost.size();
    vector<int> dp(n, -1); // Initialize the dp array with -1

    // Calculate the minimum cost to reach the top by starting from the last or second-to-last step
    return min(findmin(cost, n - 1, dp), findmin(cost, n - 2, dp));
}
```

→ TABULATION

```C++
class Solution {
public:
    int minCostClimbingStairs(vector<int>& cost) {
        int n=cost.size();
        for(int i=2;i<n;i++){
         cost[i]+=min(cost[i-1],cost[i-2]);
         }
        return min(cost[n-1],cost[n-2]);
        
    }
};
```

// Tabulation wala code better rahega kyonki Easy code with better complexity

---

Q2→[https://leetcode.com/problems/unique-paths/description/](https://leetcode.com/problems/unique-paths/description/)

  

![image 9 10.png](../../../../../../Images/image%209%2010.png)

```C++
// BASIC RECURSION CODE
class Solution {
public:
   int Tpaths(int i,int j,int m,int n){

    if(i==m-1&&j==n-1)return 1;
    if (i >= m || j >= n) return 0;

    int rightPaths = Tpaths(i, j + 1, m, n);
    int downPaths = Tpaths(i + 1, j, m, n);

    // Return the total number of paths from this position
    return rightPaths + downPaths;
}
int uniquePaths(int m, int n) {
        return Tpaths(0,0,m,n);
    }
};
```

```C++
// DP WITH MEMOIZATION
class Solution {
public:
   int Tpaths(int i,int j,int m,int n,vector<vector<int>>& dp){
    if(i==m-1&&j==n-1)return 1;
    if (i >= m || j >= n) return 0;
    if(dp[i][j]!=-1)return dp[i][j];
    
    int rightPaths = Tpaths(i, j + 1, m, n,dp);
    int downPaths = Tpaths(i + 1, j, m, n,dp);
    return dp[i][j]=rightPaths + downPaths;
}
int uniquePaths(int m, int n) {
    vector<vector<int>> dp(m, vector<int>(n, -1));
    return Tpaths(0,0,m,n,dp);
    }
};
```

**TABULATION MEIN HAMARI THINKING ALAG REHTI HAI**

```C++
class Solution {
public:
    int uniquePaths(int m, int n) {
        int dp[m][n];
         for(int i=0;i<m;i++){
          for(int j=0;j<n;j++){
            if(i==0||j==0){
                dp[i][j]=1;
            }else{
                dp[i][j]=dp[i-1][j]+dp[i][j-1];
            }
             }
}

     return dp[m-1][n-1];

    }
};
// DP SOCHNE KA TRIKA HI BADAL DEGI MERA
```

---

Q3→ [https://leetcode.com/problems/unique-paths-ii/description/](https://leetcode.com/problems/unique-paths-ii/description/)

  

  

Q4→[https://leetcode.com/problems/n-th-tribonacci-number/description/](https://leetcode.com/problems/n-th-tribonacci-number/description/)