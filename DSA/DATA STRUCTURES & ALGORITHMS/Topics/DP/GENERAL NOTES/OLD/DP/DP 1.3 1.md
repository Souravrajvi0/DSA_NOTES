Q→[https://cses.fi/problemset/task/1637/](https://cses.fi/problemset/task/1637/)

  

```C++
// memoization wala answer
\#include <iostream>
\#include<vector>
using namespace std;

vector<int> ext(int n){
    vector<int>rs;
    while(n>0){
        if(n%10!=0)  rs.push_back(n%10);
        n=n/10;
    }
    return rs;
}
vector<int>dp;

int f(int n){
    if(n==0)return 0;
    if(n<=9)return 1;
    if(dp[n]!=-1)return dp[n];

    vector<int>r=ext(n);
    int min=INT32_MAX;
    for(int i=0;i<r.size();i++){
       if(min>f(n-r[i])){
        min=f(n-r[i]);
       }
    }
    return dp[n]=1+min;
}
int main()
{
    int n;
    cin>>n;
    dp.clear();
    dp.resize(1000005,-1);
    cout<<f(n)<<"\n";
    return 0;
    
}
```

→Recursive solution ko iterative solution mein convert karne k liye recursive relation par focus karo and also focus karo order par

  

  

Q→2[https://cses.fi/problemset/task/1634](https://cses.fi/problemset/task/1634)

```C++
\#include <iostream>
\#include<vector>
\#include <algorithm> 
using namespace std;
vector<int>dp;
int help(int x,vector<int>&coins){
    if(x==0)return 0;
    if(x<0)return -1;
    if(dp[x]!=-2)return dp[x];
     
 int res=INT32_MAX;
 for(int i=0;i<coins.size();i++){
    if(x-coins[i]<0)continue;
 int subproblem=help(x-coins[i],coins);
 if(subproblem!=-1){
    res=min(res,subproblem+1);
 }
 
 }
 if(res==INT32_MAX)return dp[x]=-1;
 return dp[x]=res;

}

int main()
{
    int n,x;
    cin>>n>>x;
    vector<int>coins(n);
    for(int i=0;i<n;i++){
        cin>>coins[i];
    }
    dp.clear();
    dp.resize(1000005,-2);
    cout<<help(x,coins);
    return 0;
}
```

Q→3[https://cses.fi/problemset/task/1633](https://cses.fi/problemset/task/1633)

DOUBT

Q→4 [https://leetcode.com/problems/number-of-dice-rolls-with-target-sum/description/](https://leetcode.com/problems/number-of-dice-rolls-with-target-sum/description/)

![image 46.png](../../../../../../../Images/image%2046.png)

→State of Dp here can be find out that there are two variables Changing so 2d dp

→

  

  

Q→5 [https://www.spoj.com/problems/MCOINS/](https://www.spoj.com/problems/MCOINS/)