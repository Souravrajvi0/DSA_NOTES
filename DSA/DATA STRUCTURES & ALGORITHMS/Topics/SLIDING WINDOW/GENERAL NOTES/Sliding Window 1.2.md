  

  

![image 11.png](../../../../../Images/image%2011.png)

![image 1 4.png](../../../../../Images/image%201%204.png)

![image 2 4.png](../../../../../Images/image%202%204.png)

[https://leetcode.com/problems/subarray-sum-equals-k/description/](https://leetcode.com/problems/subarray-sum-equals-k/description/)

Will the discussed approach work with negative numbers in the array?  
A. No.  
Because let's say in the given array [4,1,1,1,2,3,5] when we found the sum within the window to be greater than the desired value 5 (i=0, j=2 -> [4,1,1]), we started reducing the size of the window by doing i++. Here we assumed that once the sum of elements within the window becomes greater than 5 then increasing the window size will just add to the sum and hence we will not attain the sum 5 again. This is true when all the element are positive and hence reducing the window size by doing i++ makes sense. But this might not be true if array also contains negative numbers. Consider the array [4,1,1,-2,1,5], here we would have found the sum to be greater than 5 for i=0, j=2 and if we would have now started reducing the window size by doing i++, we would have missed the potential subarray (i=0, j=4).  
In short, the discussed approach will not work with array having negative numbers.  

[https://www.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card](https://www.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card)(Revise)

YAHAN SLIDING WINDOW NAHI LAGEGI DHYAN RAKHNA MERE BHAI

```C++
 int maxLen(vector<int>& arr, int n) {
        // Your code here
        unordered_map<int,int>sum;
        int cursum=0;
        int maxl=0;
        for(int i=0;i<n;i++){
            cursum+=arr[i];
            if(cursum==0){
                maxl=i+1;
            }else if (sum.count(cursum)==0){
                sum[cursum]=i;
            }else{
            
            int idx=sum[cursum];
            int l=i-idx;
            if(l>maxl){
                maxl=l;
            }
          }
            
        }
        return maxl;
    }
```

  

[https://www.geeksforgeeks.org/problems/longest-k-unique-characters-substring0853/1](https://www.geeksforgeeks.org/problems/longest-k-unique-characters-substring0853/1)

MY CODE →

Chutiya code likha hai maine

```C++
int longestKSubstr(string s, int k) {
    // your code here
    unordered_map<char,int>mp;
    int i=0;
    int j=0;
    int maxl=-1;
    int l=0;
    int n=s.length();
    int count=0;
    while(j<n){
       if(mp[s[j]]==0)count++;
        mp[s[j]]++;
        l++;
        if(count<k){
            j++;
        }else if(count==k){
            maxl=max(maxl,l);
            j++;
        }else if(count>k){
            while(count>k){
                mp[s[i]]--;
                if(mp[s[i]]==0){
                    count--;
                    }
                i++;
                l--;
            }
            if(count==k){
                maxl=max(maxl,l);
            }
            j++;
       }
    }
    return maxl;
    }
```

IN ANY VARIABLE LENTH SLIDING WINDOW PROBLEM I THERE ARE TWO THINGS I NEED TO UNDERSTAND

1. Condition kya hai
2. Condition ko mathematically represent bhi karna aana chahiye

→so in this question mein conditon ye hai ki number of unique characters in the sliding window should be equal to K

```C++
  int longestKSubstr(string s, int k) {
    // your code here
    unordered_map<char,int>map;
    int i=0;
    int j=0;
    int n=s.length();
    int maxl=-1;
    while(j<n){
        map[s[j]]++;
        
        if(map.size()<k){
            j++;
        }else if(map.size()==k){
            maxl=max(maxl,j-i+1);
            j++;
        }else if(map.size()>k){
            
            while(map.size()>k){
                map[s[i]]--;
                if(map[s[i]]==0)map.erase(s[i]);
                i++;
                }
                if(map.size()==k){
                    maxl=max(maxl,j-i+1);
                }
           j++;
        }
    }
        return maxl;
    }
```

[https://leetcode.com/problems/longest-substring-without-repeating-characters/description/](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

```C++
 int lengthOfLongestSubstring(string s) {
        int i=0;
        int j=0;
        int count=0;
        int maxl=0;
        int n=s.length();
        unordered_map<char,int>mp;
        while(j<n){
        mp[s[j]]++;
        if(mp[s[j]]>1)count++;
        if(count==0){
            maxl=max(maxl,j-i+1);
            j++;
        }else if(count!=0){
          while(count!=0){
            mp[s[i]]--;
            if(mp[s[i]]==1)count--;
            i++;
          }
          if(count==0){
            maxl=max(maxl,j-i+1);
          }
          j++;
      }
   }
    return maxl; 
    }
```

[https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/)

(REVISE)

  

[https://leetcode.com/problems/fruit-into-baskets/description/](https://leetcode.com/problems/fruit-into-baskets/description/)

  

[https://leetcode.com/problems/minimum-window-substring/description/](https://leetcode.com/problems/minimum-window-substring/description/)