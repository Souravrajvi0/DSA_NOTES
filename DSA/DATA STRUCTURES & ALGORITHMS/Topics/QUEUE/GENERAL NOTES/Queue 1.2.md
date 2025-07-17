Q→[https://www.geeksforgeeks.org/problems/reverse-first-k-elements-of-queue/1](https://www.geeksforgeeks.org/problems/reverse-first-k-elements-of-queue/1)

```C++
// Function to reverse first k elements of a queue.
queue<int> modifyQueue(queue<int> q, int k) {
// add code here.
int n=q.size();
stack<int>st;
for(int i=1;i<=k;i++){
int x=q.front();
q.pop();
st.push(x);
}
while(!st.empty()){
q.push(st.top());
st.pop();
}
for(int i=1;i<=n-k;i++){
q.push(q.front());
q.pop();
}
return q;
}
```

Q→[https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/](https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/)(REPEAT)

```C++
int countStudents(vector<int>& st, vector<int>& sd) {
        queue<int>q;
        for(int i=0;i<st.size();i++){
            q.push(st[i]);
        }
        int i=0;
        int count=0;
        while(!q.empty()&&count!=q.size()){
       
        if(q.front()==sd[i]){
            q.pop();
            i++;
            count=0;
        }else{
          q.push(q.front());
          q.pop();
          count++;
        }
    }
        return q.size();
    }
```

Q→[https://leetcode.com/problems/implement-queue-using-stacks/description/](https://leetcode.com/problems/implement-queue-using-stacks/description/)

![image 32.png](../../../../../Images/image%2032.png)

JABH BHI TWO STACKS USE KARTE HAIN TABH TC EK POP/PUSH MEIN KISI KI BDHTI HI HAI

EK JAGAH COMPROMISE TOH HOGA HI

TWO APPRAOCHES BNEGI ISKI PUSH EFFICIENT AND POP EFFICIENT

```C++
 stack<int>s1;
   stack<int>s2;
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
   void reverse(stack<int> &st){
        if(st.size()==1)return;
        int top=st.top();
        st.pop();
        reverse(st);
        ib(st,top);
    }
    MyQueue() {
        
    }
    
    void push(int x) {
        s1.push(x);
        reverse(s1);
        s2=s1;
        reverse(s1);
    }
    
    int pop() {
       int top=s2.top();
       s2.pop();
       if(s2.size()!=0){
       reverse(s1);
       s1.pop();
       reverse(s1);
       }else{
        s1=s2;
       }
       return top;
    }
    
    int peek() {
       return s2.top();
        
    }
    
    bool empty() {
        if(s2.size()==0)return true;
        return false;
    }
};
```

Q→[https://www.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1](https://www.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1)

SLIDING WINDOW AND QUEUE KA PROBELM HAI YE SOLVE KAR DIYA SLIDING WINDOW K LIYE

Q→[https://leetcode.com/problems/sliding-window-maximum/description/](https://leetcode.com/problems/sliding-window-maximum/description/)

  

Q→[https://leetcode.com/problems/dota2-senate/description/](https://leetcode.com/problems/dota2-senate/description/)

  

Q→ Reorder Queue Using One Stack only

  

Q→[https://leetcode.com/problems/reveal-cards-in-increasing-order/description/](https://leetcode.com/problems/reveal-cards-in-increasing-order/description/)