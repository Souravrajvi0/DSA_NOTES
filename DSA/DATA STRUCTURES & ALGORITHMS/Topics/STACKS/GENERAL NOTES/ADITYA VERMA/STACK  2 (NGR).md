![image 17.png](../../../../../../Images/image%2017.png)


HOW TO IDENTIFY KI YE STACK KA HI QUESTION HAI!

![image 1 9.png](../../../../../../Images/image%201%209.png)

→ ARRAY K SWALO MEIN STACK KA IDEA ANA CHAHIYE DIMAG MEIN

→YA FIR BRUTE FORCE HAI O(N^2) ki and usmein bhi variable dependency hai toh stack ka sawal hai

![image 2 7.png](../../../../../../Images/image%202%207.png)

## PATTERN 1 -NEXT GREATEST TO RIGHT

Q→[https://leetcode.com/problems/next-greater-element-i/](https://leetcode.com/problems/next-greater-element-i/)(ISKO NEXT GREATER TO RIGHT BHI BOLTE HAIN

BRUTE FORCE

```C++
vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        vector<int>res;
        for(int i=0;i<nums1.size();i++){
           int num=nums1[i];
           bool found=false;
           int nge=-1;
          for(int j=0;j<nums2.size();j++){
           if(nums2[j]==nums1[i]){
            found =true;
           }
           if(found&&nums2[j]>nums1[i]){
            nge=nums2[j];
            break;
           }
         }
          res.push_back(nge);
       }
     return res;
    }
```

→TC=O(N^M)

Now isse better kar sakte hain kya???

![image 3 5.png](../../../../../../Images/image%203%205.png)

![image 4 5.png](../../../../../../Images/image%204%205.png)

```C++
vector<long long> nextLargerElement(vector<long long> arr, int n){
// Your code here
vector<long long> res;
stack<long long>st;
for(int i=n-1;i>=0;i--){
while(!st.empty()){
if(st.top()>arr[i]){
res.push_back(st.top());
break;
}else{
st.pop();
}
}
if(st.size()==0)res.push_back(-1);
st.push(arr[i]);
}
reverse(res.begin(),res.end());
return res;
}
```

Q→ Nearest greater to left

```C++
int main()
{
    int arr[]={1,3,2,5};
    stack<int>st;
    vector<int>res;
    for(int i=0;i<4;i++){
     while(!st.empty()&&st.top()<arr[i]){
        st.pop();
     }
    (st.empty()) ? res.push_back(-1) : res.push_back(st.top());
     st.push(arr[i]);
    }
    for(int i=0;i<res.size();i++){
        cout<<res[i]<<" ";
    }
    
    return 0;
}
```

Q→[https://www.geeksforgeeks.org/problems/smallest-number-on-left3403/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card](https://www.geeksforgeeks.org/problems/smallest-number-on-left3403/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card)

  

```C++
vector<int> leftSmaller(int n, int a[]){
// code here
vector<int>res;
stack<int>st;
for(int i=0;i<n;i++){
while(!st.empty()&&st.top()>=a[i]){
st.pop();
}
(st.size()==0)?res.push_back(-1):res.push_back(st.top());
st.push(a[i]);
}
return res;
}
```

Q→ **Nearest Smaller to Right(SAME SA HI HAI)**

  

Q→[https://www.geeksforgeeks.org/problems/stock-span-problem-1587115621/1](https://www.geeksforgeeks.org/problems/stock-span-problem-1587115621/1)

BRUTE FORCE (N^2)

```C++
vector <int> calculateSpan(int price[], int n)
{
// Your code here
vector<int>res;
for(int i=0;i<n;i++){
int count=1;
for(int j=i-1;j>=0;j--){
if(price[j]>price[i]){
break;
}
count++;
}
res.push_back(count);
}
return res;
}
```

Ab optimise karna hai using stack

→Ye smjha aaraha hai ki assuming koi general i, toh usse pehle wale sare elements se compare hogi uss particular arr[i] ki value and jaise hi koi value jada ai since consecutive pucha hai toh count tut jaega

  

```C++
 public:
//Function to calculate the span of stockâ€™s price for all n days.
vector <int> calculateSpan(int price[], int n)
{
// Your code here
stack<pair<int,int>>st;
vector<int>res;
for(int i=0;i<n;i++){
   while(!st.empty()&&st.top().first<=price[i]){
    st.pop();
    }
    if(st.size()==0){
        res.push_back(i+1);
    }else{
        int idx=st.top().second;
        res.push_back(i-idx);

    }

st.push({price[i],i});
}
return res;
}
```

→ yahan dekhna na ye hai since we need to find the number of smallest consecutive behind the current,Why don’t we find the next greatest on the left

→ Sawal ko dekhne ka nazariya bhi matter karta hai

![image 5 4.png](../../../../../../Images/image%205%204.png)

→In case agar greatest on the left nahi mila mtlb abhi tak sabse bada ye hi hai

→ then we store idx+1

And if we find the the greatest on the left kisi index se toh indexes ka difference hi hmara answer hojayega

→

![image 6 4.png](../../../../../../Images/image%206%204.png)

Q→[https://leetcode.com/problems/online-stock-span/description/](https://leetcode.com/problems/online-stock-span/description/)

  

Q→[https://leetcode.com/problems/largest-rectangle-in-histogram/description/](https://leetcode.com/problems/largest-rectangle-in-histogram/description/)

  

Q→[https://leetcode.com/problems/maximal-rectangle/description/](https://leetcode.com/problems/maximal-rectangle/description/)

  

Q→[https://leetcode.com/problems/trapping-rain-water/description/](https://leetcode.com/problems/trapping-rain-water/description/)

  

Q→[https://leetcode.com/problems/min-stack/description/](https://leetcode.com/problems/min-stack/description/)