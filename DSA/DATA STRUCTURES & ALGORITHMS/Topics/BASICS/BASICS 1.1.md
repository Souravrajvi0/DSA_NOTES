  

![54E5DD7D-8BD7-4E82-95F5-6A7BCA644EC1.png](../../../../Images/54E5DD7D-8BD7-4E82-95F5-6A7BCA644EC1.png)

![793BD24B-BBFE-49FF-AD0E-9A7145852203.png](../../../../Images/793BD24B-BBFE-49FF-AD0E-9A7145852203.png)

![FCE31046-B2CF-4268-8A63-6B46E934836B.png](../../../../Images/FCE31046-B2CF-4268-8A63-6B46E934836B.png)

![B1CDC504-864E-48D3-AAF0-47600F0AD5FC.png](../../../../Images/B1CDC504-864E-48D3-AAF0-47600F0AD5FC.png)

![F768A3A5-A3D0-4E15-8D0D-32FC80F52013.png](../../../../Images/F768A3A5-A3D0-4E15-8D0D-32FC80F52013.png)

![40FD73BF-5506-4BE7-959E-F3605051D5C0.png](../../../../Images/40FD73BF-5506-4BE7-959E-F3605051D5C0.png)

![4482D197-CE42-43C8-86D6-FBB6166945C8.png](../../../../Images/4482D197-CE42-43C8-86D6-FBB6166945C8.png)

```C++
std::vector<int> numbers = {1, 2, 3, 4, 5};

// Using reference - can modify original elements
for (auto &num : numbers) {
    num *= 2;  // This will actually change the values in 'numbers'
}

// Without reference - only modifies copies
for (auto num : numbers) {
    num *= 2;  // This does not affect the original 'numbers' vector
}
```

→`long long x` or `long long int x` - they are interchangeable.  
  


- No negative numbers: `unsigned long long` cannot represent negative values.
- Larger positive range: It can represent twice the range of positive numbers compared to `long long`.
- Different overflow behavior: Overflow wraps around differently than with signed types.
- For `long long x`:  
      
    In decimal, this is:  
    - Minimum value: -2^63
    - Maximum value: 2^63 - 1
    - Minimum: -9,223,372,036,854,775,808
    - Maximum: 9,223,372,036,854,775,807
- For `unsigned long long x`:  
      
    In decimal, this is:  
    - Minimum value: 0
    - Maximum value: 2^64 - 1
    - Minimum: 0
    - Maximum: 18,446,744,073,709,551,615

→ALWAYS USE LONG DOUBLE for float values

![1C66545A-2A00-4DD9-AEFE-7987BBEBCB3F.png](../../../../Images/1C66545A-2A00-4DD9-AEFE-7987BBEBCB3F.png)

![1DFB68D3-8248-4647-AF2D-12430EE4412D.png](../../../../Images/1DFB68D3-8248-4647-AF2D-12430EE4412D.png)

# \#include<bits/stdc++.h>

![49FD83F7-B732-45D5-B64F-3CD7F7799681.png](../../../../Images/49FD83F7-B732-45D5-B64F-3CD7F7799681.png)

![90D93164-479C-4478-BDF0-69D663FD3AC7.png](../../../../Images/90D93164-479C-4478-BDF0-69D663FD3AC7.png)

![57BBA604-76E1-442B-82A8-EA0D8475F5A8.png](../../../../Images/57BBA604-76E1-442B-82A8-EA0D8475F5A8.png)

  

  

```C++
\#include <bits/stdc++.h>
using namespace std;

\#define endl '\n'
\#define int long long

const int MOD = 1e9 + 7;
const int INF = LLONG_MAX/2;

signed main() {
    ios::sync_with_stdio(false);cin.tie(NULL);

    int tc; cin >> tc;
    while (tc--) {
        // Your code logic here
    }

    return 0;
}
```