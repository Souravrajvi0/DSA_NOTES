Q1→[https://leetcode.com/problems/house-robber/](https://leetcode.com/problems/house-robber/)

Jabh buhut sari posssiblities ki bat ho na tabh recursion ka idea toh ana hi chahiye

![image 45.png](../../../../../../../Images/image%2045.png)

![image 1 22.png](../../../../../../../Images/image%201%2022.png)

![image 2 20.png](../../../../../../../Images/image%202%2020.png)

→REPEATING SUBPROBLEM DIKH RAHI HAI,ARRAY TOH SAME HAI HAR JAGAH BUT INDEX KI VALUE JO HAI NA VO CHANGE HO RAHI HAI

→ **STATE OF THE DYNAMIC PROGRAMMING**

![image 3 17.png](../../../../../../../Images/image%203%2017.png)

→JO BHI SET OF PARAMETRES K CHANGE HONE SE SUBPROBLEM CHANGE HOJATI HAI VOHI STATE HAI ya jis variable se subproblem uniquely identify hojaye

→Koi bhi subproblem ko indentify karne k liye jo bhi parametres use horahe hain wo sare milkar STATE OF THE DP BNATE HAIN.

→ CHOTI SUBPROBLEM KE OPTIMAL ANSWER KO USE KRKE AGAR MAIN BADI PROBLEM KA ANSWER NIKAL SAKTA HUON TOH IN THAT CASE OPTIMAL SUB STRUCTURE EXIST KARTA HAI

→DP LAG SAKTI HAI KYON? **optimal Sub structure** hai and **overlapping subproblem** hai

- Now Let’s Find out the Recursive solution for this code

  

```C++
// sanket sir ka code hai ye 
 class Solution {
public:
int f(vector<int>& arr, int i) {
if (i == arr.size() - 1) return arr[i]; // single house // ya i>=arr.size() return0  ye bhi kar skte hain
if (i == arr.size() - 2) return max(arr[i], arr[i + 1]); // 2 houses
    return max(arr[i] + f(arr, i + 2), f(arr, i + 1));
}

int rob(vector<int>& nums) {
    return f(nums, 0);
}
};
```

TLE AGYA NOW WE GO FOR DP

HOW TO GO FROM RECURSIVE RELATION TO DP?

Sabse pehle find the state of the DP(kitne parametres ka use karke Ek subproblem uniquely identify hoti hai)

BUT KYON? Well ye subproblems hi toh hai jinko humko bari bari call hoti hai.Toh Agar kisi subproblem ka answer mujhe pehle milgya tha toh usko main store karna chahta huon!

But uske liye mujhe pata hona chahiye na ye answer konsi subproblem ka hai!so Jis bhi subproblem ka answer hai uske corresponding main usko store karunga

![image 4 15.png](../../../../../../../Images/image%204%2015.png)

![image 5 13.png](../../../../../../../Images/image%205%2013.png)

![image 6 13.png](../../../../../../../Images/image%206%2013.png)

  

![image 7 12.png](../../../../../../../Images/image%207%2012.png)

→If **STATE OF THE DP** can be identified using This number of variables

- 1 variable →1 dimensional DP
- 2 variable→2 dimensional DP
- 3 variable→3 dimensional DP

→So we use a DP array initialized with -1(depending on the problem-INT_MAX,INT_MIN bhi use ho skta hai) then with time onwards if we find That in the DP array there is still a -1 in that ith index that subproblem is not yet computed

→But what if dp[i]≠-1 then ith state is already computed then just reuse it

→ AND THE DP ARRAY MOSTLY DONE BY CP in 99% is a global array or vector

![image 8 12.png](../../../../../../../Images/image%208%2012.png)

![image 9 11.png](../../../../../../../Images/image%209%2011.png)

→

![image 10 9.png](../../../../../../../Images/image%2010%209.png)

![image 11 8.png](../../../../../../../Images/image%2011%208.png)

Dp vector ka size maximum se upar bna lo kuch koi constant thoda sa Nums.size() se

```C++
// memoization wala solution
class Solution {
public:
    int maxs(vector<int>&nums,int i,vector <int>&dp){
    if(i==nums.size()-1)return nums[i];
    if(i==nums.size()-2)return max(nums[i],nums[i+1]);
    if(dp[i]!=-1)return dp[i];
    
    return dp[i]= max(nums[i]+maxs(nums,i+2,dp),maxs(nums,i+1,dp));
 }
    int rob(vector<int>& nums) {
        vector <int> dp(nums.size(),-1);
        return maxs(nums,0,dp);
        
    }
};
```

→ TOP Down mein kai stack overflow hoskta hai kyonki Recursion hota hai yahan

→ Now in Bottom up mein aesa koi fayda ata hai nahi issee unless memory constraint ho buhut jada

**Bottom up ko kaise dekhna hai???????????????**

Agar Tumhare pass recursive solution read hai, Then Recursion kya krta hai ki konse order mein solution build hone chahiye je recursion khud pata laga leti hai

→In iterative solution mein hhumein dhyan rakhna hota hai humein kis order mein chizon ko build krna chahiye ki bada wale ka answer aajaye

→ Toh in bottom up approach mein ye dekho ki konsi konsi Choti subproblems pehle se padi honi chahiye jiska use karke ek badi problem solve hojaye

→Ki ekbar recursive solution ban jaye fir uske bad mein ordering define kar pauon ki mera final answer ban jaye

→BOTTOM UP KEHTA HAI KISI BHI SUBPROBLEM KO BNANE K LIYE USSE CHOTI SUBPROBLEM KO PEHLE BNA DUNGA  
→SABSE CHOTI SUBPROBLEM SE START KARUNGA FIR UNSE BADI PROBLEMS BANAUNGA FIR USEE BADI SUBPROBLEMS BNAUNGA LIKE INN FIBONACCI  

→ YEHI ORDER HOTA HAI ,JIS ORDER MEIN SOLUTION BUILD KARNA HAI

![image 12 8.png](../../../../../../../Images/image%2012%208.png)

![image 13 7.png](../../../../../../../Images/image%2013%207.png)

→ since Base case toh pehle hi pata the toh unhi se build up karenge bottom up ka

```C++
  int rob(vector<int>& nums) {
        if(nums.size()==1)return nums[0];// corner case
        vector <int> dp(nums.size());
        dp[nums.size()-1]=nums[nums.size()-1];
        dp[nums.size()-2]=max(nums[nums.size()-1],nums[nums.size()-2]);

        for(int i=nums.size()-3;i>=0;i--){
            dp[i]=max(dp[i+1],nums[i]+dp[i+2]);
        }
        return dp[0];
        
    }
```

→ NOW SIR KA SOLUTION

  

```C++
class Solution {
public:
vector<int> dp;// VECTOR KO GLOBAL BNAYA HAI
// RECURSIVE SOLUTION HAI SIR KA YE
int f(vector<int>& arr, int i) {
    if (i == arr.size() - 1) return arr[i]; // single house
    if (i == arr.size() - 2) return max(arr[i], arr[i + 1]); // 2 houses

    return max(arr[i] + f(arr, i + 2), 0 + f(arr, i + 1));
}

// TOP DOWN 
int ftd(vector<int>& arr, int i) {
    if (i == arr.size() - 1) return arr[i]; // single house
    if (i == arr.size() - 2) return max(arr[i], arr[i + 1]); // 2 houses

    if (dp[i] != -1) return dp[i]; // ith state already computed

    // if dp[i] was -1 so let's compute ith state for the first
    return dp[i] = max(arr[i] + ftd(arr, i + 2), 0 + ftd(arr, i + 1));
}
//BOTTOM DOWN
int fbu(vector<int>& arr) {
    int n = arr.size();
    if (n == 1) return arr[0];
    dp.clear();
    dp.resize(n);

    // base case
    dp[n - 1] = arr[n - 1];
    dp[n - 2] = max(arr[n - 1], arr[n - 2]);

    for (int i = n - 3; i >= 0; i--) // order
        dp[i] = max(arr[i] + dp[i + 2], 0 + dp[i + 1]);

    return dp[0];
}

int rob(vector<int>& nums) {
    dp.clear();
    dp.resize(105, -1);
    // return f(nums, 0);
    return fbu(nums);
}
};
```

![image 14 7.png](../../../../../../../Images/image%2014%207.png)

→isko ulta bhi dekh sakte hain

→ ye pattern wale swal fibonacci wale problem se inspired hai

→And in Bottom up mein space optimisation bhi ho sakta hai kaise well? ab ek kam kro ki ek array ki jagah 3 variable le lo

  

---

**Problem Statement:**

SAME PROBLEM ON LC→[https://leetcode.com/problems/integer-replacement/](https://leetcode.com/problems/integer-replacement/)  
Given a number  
`n`, you can perform any of the following operations on it some number of times:

1. **Reduce** `**n**` **to** `**n - 1**`.
2. **If** `**n**` **is divisible by 2, reduce** `**n**` **to** `**n / 2**`.
3. **If** `**n**` **is divisible by 3, reduce** `**n**` **to** `**n / 3**`.

  

**Objective:**  
Find out the minimum number of steps required to reduce  
`n` to 1

![image 15 7.png](../../../../../../../Images/image%2015%207.png)

![image 16 6.png](../../../../../../../Images/image%2016%206.png)

GREEDY NAHI LAGEGA YAHAN

→DP KOI ALGORITHM NAHI HAI YE EK OPTIMISATION TECHNIQUE HAI , JUST EK TECHNIQUE HAI

→ APNE BRUTE FORCE SOLUTION KO OPTIMSATION KR SKTE Ho

→PEHLE BRUTE FORCE SOLUTION NIKALO AND US PAR DP LAGANE KA TRY KARO

→

![image 17 6.png](../../../../../../../Images/image%2017%206.png)

→ 1st type ye hai ki example→ Count the number of ways

→ 2nd Type ye hai ki example→get the maxmisation of this or minmisation of this