Lets start with a problem Question! 
LC 3008
You are given a **0-indexed** string `s`, a string `a`, a string `b`, and an integer `k`.

An index `i` is **beautiful** if:

- `0 <= i <= s.length - a.length`
- `s[i..(i + a.length - 1)] == a`
- There exists an index `j` such that:
    - `0 <= j <= s.length - b.length`
    - `s[j..(j + b.length - 1)] == b`
    - `|j - i| <= k`

Return _the array that contains beautiful indices in **sorted order from smallest to largest**_.

BRUTE FORCE ISMEIN TLE AEGA

```c++
 vector<int> beautifulIndices(string s, string a, string b, int k) {

       vector<int>ai;
       size_t pos=s.find(a);

       while(pos != string ::npos){
        ai.push_back(int(pos));
        pos=s.find(a,pos+1);
       }

       vector<int>bi;
       pos=s.find(b);

       while(pos != string ::npos){
        bi.push_back(int(pos));
        pos=s.find(b,pos+1);
       }
      vector<int>ans;
    int i = 0, j = 0;
   for (int i = 0; i < ai.size(); i++) {
    for (int j = 0; j < bi.size(); j++) {
        if (abs(bi[j] - ai[i]) <= k) {
            ans.push_back(ai[i]);
            break;
        }
    }
    }
      return ans;
    }
```

Time Complexity: O()
Space Complexity: O()


HOW TO GET BETTER SOLUTION THAN THIS NOW???

#                                                                                      KMP 

