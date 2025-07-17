→KAI BAR TUMHE YE REALIZE HOGA KI TUMHE PROBLEM MEIN RECURSION KI KOI JARURAT NAHI HAI.

→BUT KAI BAR PRE COMPUTATION WALA CONCEPT APPLY HORA HOTA HAI

→DP KA ESSENCE KAI BAR OPTIMAL STRUCTURE AND SUB PROBLEM STRUCTURES K ALAWA KAI BAR PRE COMPUTATION SE BHI ATA HAI

→Koi cheez hai jise tum pre compute karke rakh sakho

→Q=[https://www.hackerearth.com/practice/algorithms/dynamic-programming/introduction-to-dynamic-programming-1/practice-problems/algorithm/roy-and-coin-boxes-1/](https://www.hackerearth.com/practice/algorithms/dynamic-programming/introduction-to-dynamic-programming-1/practice-problems/algorithm/roy-and-coin-boxes-1/)(REVISIT)

2 APPROACH HAI ISMEIN DONO SOLVE KARNI HAI

![image 47.png](../../../../../../../Images/image%2047.png)

```C++
\#include <iostream>
\#include<vector>

using namespace std;

int main()
{
    
    int n;
    cin>>n;
     vector<int>f(n+1,0);
     int m;
     cin>>m;
     vector<int>l(n+1,0);
     vector<int>r(n+1,0);
     for(int i=1;i<=n+1;i++){
        int L,R;
        cin>>L>>R;
        l[L]++;
        r[R]++;
     }
     f[1]=l[1];
     for(int i=2;i<n+1;i++){
        f[i]=l[i]-r[i-1]+f[i-1];
     }
     vector <int>c(10000007,0);
     for(int i=1;i<=n;i++){
      int coins=f[i];
      c[coins]++;
     }
     for(int i=c.size()-2;i>0;i--){
        c[i]=c[i+1]+c[i];
     }
     int q;
     cin>>q;
     while(q--){
        int num;
        cin>>num;
        cout<<c[num]<<"\n";
    }
 
    
    return 0;
}
```