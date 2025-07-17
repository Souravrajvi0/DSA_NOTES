# **QUEUE IN C++**

- A queue is a linear data structure that follows the **FIFO (First In First Out)** principle i.e. elements that are added first will be removed first.
- It is defined inside `<queue>` header file (also available in `<bits/stdc++.h>`)

⇒`#inlcude<bits/stdc++.h>` Add krne se mostly sari standard header files add hojati hain uske bad kuch extra add krne ki jarurat nahi padti

=> `#include<queue>`  add Karna mat bhulna!

![image 18.png](../../../../../Images/image%2018.png)

### _**Visualize kaise Karni hai?**_

![Queue 1.1-20250102090852093.webp](../../../../../Images/Queue%201.1-20250102090852093.webp)

⇒ JAHAN SE PUSH HORAHA HAI POP USKI OPPOSITE DIRECTION SE HORAHA HAI

![image 2 8.png](../../../../../Images/image%202%208.png)

### _**Declaring a queue**_

_Syntax_

`queue< data_type > queue_name;`

_Examples_

```Plain
queue<int> q; // queue of int's
queue<string> q; // queue of strings
queue<pair<int, int>> q; // queue of pairs
queue<vector<int>> q; //queue of vectors
```

**Note :** Similar syntax for `char` `long long int` `float` `double` `long double` and some other data types include user defined data types.

### _**Important functions on queue**_

```Plain
q.push(ele); // pushes an element  'ele' into queue from end       TC - 𝓞(1)
q.pop(); // removes an element from front of the queue   TC - 𝓞(1)// Doubly eneded queue mein hum back se bhi remove kar sakte hain
q.front(); // returns the first element    TC - 𝓞(1)
q.back(); // returns the last element    TC - 𝓞(1)
q.size(); // returns the size of queue    TC - 𝓞(1)
q.empty(); // returns true if queue is empty else false    TC - 𝓞(1)
```

**Note :** The time complexity of all above inbuilt functions is constant - 𝓞(1)

### _**Accessing queue elements**_

Since it won't provide indexing **we can not directly access any element except first and last element.**

WHOLE QUEUE TRAVERSE KARNE K LIYE HUMEIN CHAHIYE KI HUM QUEUE SE ELMENT NIKALNE HI PADENGE AND KAHIN STORE BHI KARNE PADENGE
The below is the way to traverse the queue.

```Plain
while(!q.empty()){
	cout << q.front() << " ";
	q.pop();
}
```

### **Applications of Queues**

- Task Scheduling: Queues are used in task scheduling algorithms like Round Robin.
- Print Queue Management: Managing print jobs in computer systems.
- Message Queues: Communication between different parts of a system in a message-passing architecture.
- Breadth-First Search (BFS) in graph traversal algorithms.
- Handling requests in network protocols like TCP/IP.

![image 3 6.png](../../../../../Images/image%203%206.png)

A table comparing **Stack** and **Queue** with points that are essential to consider when solving DSA problems:

|   |   |   |
|---|---|---|
|**Point**|**Stack**|**Queue**|
|**Definition**|A linear data structure following **Last-In-First-Out (LIFO)** principle.|A linear data structure following **First-In-First-Out (FIFO)** principle.|
|**Basic Operations**|**Push** (add to top), **Pop** (remove from top), **Peek** (view top), **isEmpty**.|**Enqueue** (add to end), **Dequeue** (remove from front), **Peek** (view front), **isEmpty**.|
|**Access Pattern**|Access elements from the **top** only.|Access elements from the **front** only, while insertion is at the **rear**.|
|**Common Implementations**|Arrays, Linked Lists.|Arrays, Linked Lists, Circular Queues.|
|**Use Cases**|Undo operations, backtracking (e.g., Depth-First Search), expression parsing.|Task scheduling, handling requests (e.g., Breadth-First Search), process management.|
|**Time Complexity**|Push and Pop operations are **O(1)**; accessing elements may require **O(n)** in some cases.|Enqueue and Dequeue operations are **O(1)**; accessing elements may require **O(n)**.|
|**Memory Management**|Fixed or dynamic, depending on the implementation; generally stack-based memory allocation.|Fixed or dynamic, depending on the implementation; generally heap-based memory allocation.|
|**Types of Problems**|Problems involving **recursive** solutions, **reversing** data, or **backtracking**.|Problems involving **order processing**, **scheduling**, or **sequential access**.|
|**Variants**|Min Stack, Max Stack, Multi-Stack.|Circular Queue, Priority Queue, Deque (Double-Ended Queue).|
|**Edge Cases**|Stack overflow (when full), underflow (when empty).|Queue overflow (when full), underflow (when empty).|



### **DISPLAY ALL THE ELEMENTS OF QUEUE**

→Now Yahan Humein ek extra data Structure ki jarurat nahi padegi LIKE IN STACK

→ Hum jaise hi queue se nikalenge front se vaise print karwa k vapis queue mein push kardenge piche se

→Yhan jabh print karwa rahe hain tabh size pehle hi le liya kyonki size constant nahi hai toh uspar condition nahi lagegi**(DHYAN RAKHNA)**

![image 4 6.png](../../../../../Images/image%204%206.png)

  

→**NOW QUEUE AND STACK CAN BE USED TOGETHER TO SOLVE PROBLEMS**

→MTLB STACK KO TWO EXTRA STACKS LEKE REVERSE KAR SAKTE HAIN BUT QUEUE KO EXTRA QUEUE LEKAR REVERSE NAHI KAR SKTE SINCE DUSRI QUEUE MEIN JABH ELEMENTS DALENGE TABH BHI ELEMENTS KA ORDER SAME RAHEGA


![Queue 1.1-20250102091756546.webp](../../../../../Images/Queue%201.1-20250102091756546.webp)





![image 5 5.png](../../../../../Images/image%205%205.png)

![image 6 5.png](../../../../../Images/image%206%205.png)

→ **SINCE QUEUE MUJHE YE FACILITY DETI HAI KI MAIN PICHE SE  PUSH KAR SAKTA HUON TOH ISLIYE,KAI BAR MUJHE EXTRA QUEUE LENE KI JARURAT NAHI PADTI**

![image 7 4.png](../../../../../Images/image%207%204.png)

- BUT q.size() vo mat likhna since wo very problematic hai
- Aesa Kyon well ! Yahan par size change horaha hai queue ka toh ya toh pehle int n mein size save karlo

---

# IMPLEMENTATIONS

## **⇒ IMPLEMENTING USING ARRAY**

![image 8 4.png](../../../../../Images/image%208%204.png)

  

![image 9 3.png](../../../../../Images/image%209%203.png)

![image 10 3.png](../../../../../Images/image%2010%203.png)


Since b hamesha ek place age rehta hain toh b-f likhar 0 indexing ka effect hata dete haiin apne ap!

![image 11 3.png](../../../../../Images/image%2011%203.png)

![image 12 3.png](../../../../../Images/image%2012%203.png)

⇒Since back ek move karke aage hojata hai

![image 13 3.png](../../../../../Images/image%2013%203.png)

![image 14 3.png](../../../../../Images/image%2014%203.png)

Constructor⇒

![image 15 3.png](../../../../../Images/image%2015%203.png)

![image 16 2.png](../../../../../Images/image%2016%202.png)

## **⇒ IMPLEMENTING USING LINKED LIST(KAFFI ACHA AND CONVENIENT REHTA HAI)**

![image 17 2.png](../../../../../Images/image%2017%202.png)

![image 18 2.png](../../../../../Images/image%2018%202.png)

![image 19.png](../../../../../Images/image%2019.png)

→ SIZE MAINTAIN KARKE RAKHNA PADEGA MUJHE

![image 20.png](../../../../../Images/image%2020.png)

![image 21.png](../../../../../Images/image%2021.png)

![image 22.png](../../../../../Images/image%2022.png)

![image 23.png](../../../../../Images/image%2023.png)

![image 24.png](../../../../../Images/image%2024.png)

![image 25.png](../../../../../Images/image%2025.png)

# DEQUE

DOUBLY ENDED QUEUE

### Key Operations

1. **Push Front**: Insert an element at the front of the deque.
2. **Push Back**: Insert an element at the end of the deque.
3. **Pop Front**: Remove and return the element from the front of the deque.
4. **Pop Back**: Remove and return the element from the end of the deque.
5. **Front**: Access the element at the front without removing it.
6. **Back**: Access the element at the end without removing it.
7. **Size**: Get the number of elements in the deque.
8. **Empty**: Check if the deque is empty

![image 26.png](../../../../../Images/image%2026.png)

![image 27.png](../../../../../Images/image%2027.png)

![image 28.png](../../../../../Images/image%2028.png)

→So when we use a DLL linked list mein pop back toh easy hoga but but SLL mein humein (n-1) nodes travel karne padenge since piche kaise ja nahi sakta tail se


![image 29.png](../../../../../Images/image%2029.png)

⇒ DEQUE KA STL BHI USE KAR SAKTE HAIN

![image 30.png](../../../../../Images/image%2030.png)

# CIRCULAR QUEUE

![image 31.png](../../../../../Images/image%2031.png)

→F ko aage lekar aaojaoge

→ Size ko bhhi maintain karke rakhunga

Q→[https://leetcode.com/problems/design-circular-queue/description/](https://leetcode.com/problems/design-circular-queue/description/)

```C++
class MyCircularQueue {
public:
    int f;
    int b;
    vector<int>arr;
    int size;
    int cap;
    MyCircularQueue(int k) { // k is the capacity
      f=0;
      b=0;
      size=0;
      cap=k;
      vector<int>n(k);
      arr=n;
    }
    
    bool enQueue(int value) { 
        if(size==cap)return false;
        arr[b]=value;
        b++;
        if(b==cap)b=0;  // important
        size++;
        
        return true;
    }
    
    bool deQueue() {    // pop
         if(size<=0) return false;
         f++;
         if(f==cap)f=0;  // important
         size--;
         return true;
    }
    
    int Front() {
        if(size==0)return -1;
        return arr[f];
        
    }
    
    int Rear() {
        if(size==0)return -1;
        if(b==0)return arr[cap-1]; // important
        return arr[b-1];
        
    }
    
    bool isEmpty() {
        if(size==0)return true;
        else return false;
        
    }
    
    bool isFull() {
        if(size==cap)return true;
        else return false;
    }
};

```