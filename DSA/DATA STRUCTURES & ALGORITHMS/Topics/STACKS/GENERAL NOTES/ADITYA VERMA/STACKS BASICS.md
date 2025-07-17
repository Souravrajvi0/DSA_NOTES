![STACKS BASIC-20241110093455641.webp](../../../../../../Images/STACKS%20BASIC-20241110093455641.webp)


![STACKS BASIC-20241110093506348.webp](../../../../../../Images/STACKS%20BASIC-20241110093506348.webp)


![STACKS BASIC-20241110093642943.webp](../../../../../../Images/STACKS%20BASIC-20241110093642943.webp)

→JABH STACK K SAWALO KO DEKHO TOH INHI OPERATIONS K BASIS PAR SOLVE KARNE KI KOSHISH KARO SINCE INKI TC → O(1) hoti hai

![STACKS BASIC-20241110093721786.webp](../../../../../../Images/STACKS%20BASIC-20241110093721786.webp)


 STACK KA FLOW VISUALIZE HOJATA HAI,BUT WHAT IF MUJHE STACK K BICH MEIN SE KOI ELEMENT UDANA HAI?? In that case mujhe ek extra Data structure ki zarurat padegi
![STACKS BASIC-20241110093746132.webp](../../../../../../Images/STACKS%20BASIC-20241110093746132.webp)


THEN WHY SHOULD WE USE STACK?? AND WHAT IS THE USE OF IT?
- **STACK KA SIZE UNLIMITED HOTA HAI**
- **STACK PROVIDES DISCIPLINE**
- **STACK PROVIDES INTUTION**

STACK MANTRA:
## LAST IN FIRST OUT
## FIRST IN LAST OUT

## HEADER FILE FOR STACK

```c++
#include <iostream>
#include<stack>
using namespace std;

```



```c++
#include <iostream>
#include<stack>
using namespace std;

int main()
{
    stack<int>st;
    st.push(2);
    st.push(3);
    st.push(4);
    cout<<st.top()<<endl;
    cout<<st;-> //isse error aega since pura stack aese print nahi hota hai c++ mein java mein hota hai
    return 0;
}

```



![STACKS BASIC-20241110094348435.webp](../../../../../../Images/STACKS%20BASIC-20241110094348435.webp)


![STACKS BASIC-20241110094422033.webp](../../../../../../Images/STACKS%20BASIC-20241110094422033.webp)


![STACKS BASIC-20241110094455233.webp](../../../../../../Images/STACKS%20BASIC-20241110094455233.webp)

→ Ek stack se nikalte vaqt dusre temporary stack mein daldo but elements reverse order mein aa jayenge
→Fir uss temporary se vapis original mein daldo toh order bhi preserve hojayega

![STACKS BASIC-20241110094534303.webp](../../../../../../Images/STACKS%20BASIC-20241110094534303.webp)

![STACKS BASIC-20241110094550997.webp](../../../../../../Images/STACKS%20BASIC-20241110094550997.webp)

![STACKS BASIC-20241110094628125.webp](../../../../../../Images/STACKS%20BASIC-20241110094628125.webp)


**USE OF ARRAY/VECTOR WITH STACK**

→SINCE STACK K BICH MEIN ELEMENT STORE KRANE K LIYE ELEMENTS UDANE HI PADENGE, TOH koi nahi elements kahin store karwa lenge kya dikkat hai

![STACKS BASIC-20241110094659351.webp](../../../../../../Images/STACKS%20BASIC-20241110094659351.webp)

**→REVERSE STACK RECURSIVELY**

![STACKS BASIC-20241110094745172.webp](../../../../../../Images/STACKS%20BASIC-20241110094745172.webp)


![STACKS BASIC-20241110094807716.webp](../../../../../../Images/STACKS%20BASIC-20241110094807716.webp)


https://www.geeksforgeeks.org/problems/reverse-a-stack/1

**BRO YE PUSH ELEMENT AT BOTTOM WALE CONCEPT KA USE HOTA HAI**

Ye Fir se try karna // ACHA SWAL HAI


```c++
void ib(stack<int>&st,int x){
vector<int>v;
while(!st.empty()){
v.push_back(st.top());
st.pop();
}
st.push(x);
for(int i=v.size()-1;i>=0;i--){
st.push(v[i]);
}
}
void Reverse(stack<int> &st){
    if(st.size()==1)return;
    int top=st.top();
    st.pop();
    Reverse(st);
    ib(st,top);
}


```

![STACKS BASIC-20241110094926315.webp](../../../../../../Images/STACKS%20BASIC-20241110094926315.webp)

### **STACK IMPLEMENTAION (REVISE)**

→IMPLEMENT STACK USING ARRAY

→IMPLEMENT STACK USING VECTOR

→IMPLEMENT STACK USING LL