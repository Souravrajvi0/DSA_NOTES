# **PATTERN 3→ LowestCommonSubsequence**

→JAISE KNAPSACK MEIN PICK AND NOT PICK KA GAME THA

→ VAISE HI YAHAN PAR MATCH AND NOT MATCH KA GAME HOGA

![image 49.png](../../../../../../../Images/image%2049.png)

  

[https://leetcode.com/problems/longest-common-subsequence/description/](https://leetcode.com/problems/longest-common-subsequence/description/)

SUBSEQUENCE MEIN ORDER MAIN MAINTAIN RAKHNA HOTA HAI

S1→ abcdgh

S2→abedfhr

LONGEST COMMON SUBSEQUENCE →abdh⇒4(size)

→Subsequence discontinous hoskta hai

LONGEST COMMON SUBSTRING⇒ ab⇒2

→Substring continous hota hai

  

BASE CASE?? Hamesha Smallest valid input/output sochhna hota hai

→Jabh dono string khali ho ya ek khali ho→ usmein longest css=0 hi hoga na

  

→ eb bat ye samaj ki recursion code input ko todta hai hamesha so it means ki recursion strings ko bhi todega so that choti substrings pass hogi bari bari

→NEXT PART HOTA HAI CHOICES KAISE DEFINE HONGI???

→Well Choices k liye kya karna hoga ki⇒ dono k ek common index se shuru karna hoga well usmein toh ya toh end se ya starting se

→

![image 1 24.png](../../../../../../../Images/image%201%2024.png)

→

![image 2 22.png](../../../../../../../Images/image%202%2022.png)

→TOP DOWN

```C++
  vector<vector<int>>dp;
    int help(string &text1, string &text2,int i,int j ){ // agar yahan bina call by refrence k 
    if(i<0||j<0)return 0;                                // bina TLE aega lol
    if(dp[i][j]!=-1)return dp[i][j];
    if(text1[i]==text2[j]){
        return dp[i][j]= 1+help(text1,text2,i-1,j-1);
     }
    return dp[i][j]= max(help(text1,text2,i,j-1), help(text1,text2,i-1,j));
   
}
    int longestCommonSubsequence(string text1, string text2) {
        dp.clear();
        dp.resize(1002,vector<int>(1002,-1));
        return help(text1, text2,text1.length()-1,text2.length()-1);
    }
```

→ BOTTOM UP

  

  

  

  

Q2→[https://www.geeksforgeeks.org/problems/print-all-lcs-sequences3413/1](https://www.geeksforgeeks.org/problems/print-all-lcs-sequences3413/1)