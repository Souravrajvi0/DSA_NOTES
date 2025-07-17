INKI HEADER FILES INCLUDE KARNA MAT BHULNA ya fir # include<bits/stdc++.h> add kardena

## **UNORDERED SET**

![image 50.png](../../../../../Images/image%2050.png)

### **UNORDERED SET IN C++**

- An Unordered_set is similar to set data structure and it **won't allow duplicate keys.**
- But the keys are **not sorted** by any order ( **No order** ) and hence we can't except the ordering of elements.
- Implemented using Hash Tables
- Faster in insertion / removal / find than set in average case i.e TC - O(1). ( worst case TC - O(n))
- There is no concept of index here!

### _**Declaring unordered_set**_

_Syntax_

```C++
 unordered_set< data_type > st;
```

_Examples_

```C++
unordered_set<int> s; //  unordered_set of int's
unordered_set<string> s; //  unordered_set of strings
unordered_set<pair<int, int>> s; //  unordered_set of pairs
unordered_set<vector<int>> s; //  unordered_set of vectors
//Note : Similar syntax for char long long int float double long double and some other data types include user defined data types.

```

![image 1 25.png](../../../../../Images/image%201%2025.png)

→ Elements added are totally floating around  in random order!


### _**Accessing unordered_set elements**_

Since it won't provide indexing **we can not directly access any element.** ,The below is the way to traverse the unordered_set.

```C++
for( auto x : s ){ 
	cout << x << " " ;  // prints each key in ascending order
}
```

WE USE **FOR EACH LOOP** here:

```C++
  unordered_set<int>s;// declaration same as vector or stack or queue
    s.insert(1);
    s.insert(2);
    s.insert(3);
    s.insert(4);
    s.insert(5);
    s.insert(5); //ye ekbar hi jayega do bar nahi jayega
    s.size(); // size abhi bhi 5 hi rahega  
    s.erase(2);// 2 delete hogya set se 
 for(int i:s){
        cout<<i<<endl;
    }
```

→ **SET UNIQUE ELEMENTS KO HI STORE KARTA HAI**
→In case If I'm trying to insert the same element again and again it'll just be added once!
  Searching an Element inside a set might feel a little weird because it's as usual as in other Data Structures! 

**FIND**
- **If the element is found:** It returns an iterator pointing to the element.
- **If the element is not found:** It returns `end()`, which is an iterator pointing past the last element in the container.

```C++
int main()
{
 unordered_set<int>s;
    s.insert(1);
    s.insert(2);
    int target=2;
    if(s.find(target)!=s.end()){  // iska mtlb target exists krta hai
                                  
    }
    if(s.find(target)==s.end(){  // in this case target doesn't exist
    }
    
   
}
```

![image 2 23.png](../../../../../Images/image%202%2023.png)

![image 3 19.png](../../../../../Images/image%203%2019.png)

Questions:
Count Number of Distinct Integers After Reverse Operations(Done)
Find Maximum Number of String Pairs(Mid)




## **UNOREDERED MAPS (Hash)**

#### **When to Use Maps**

- To **store the frequency** of specific elements.
- To handle **key-value pairs** efficiently.

---

### **Types of Maps**

1. **`unordered_map<>`**:
    
    - Keys are **not sorted**.
    - **Insertion, deletion, and lookup** have an average time complexity of **O(1)**.
    - Best choice when order of keys doesn't matter.
2. **`map<>`**:
    
    - Keys are stored in **sorted order**.
    - **Insertion, deletion, and lookup** take **O(log n)** due to the underlying balanced binary search tree.
    - Use this when you need keys to remain sorted.
    - In an **ordered map (`std::map`)**, the elements are **arranged in ascending order of the keys** by default.

#### **Key Point**:

- Use **`map<>`** if sorted order is needed.
- Use **`unordered_map<>`** for faster operations when order is irrelevant.


### **`unordered_map` Syntax**

```c++
unordered_map<int, int> q1;
unordered_map<int, vector<int>> q2;
unordered_map<int, vector<vector<string>>> q3;
unordered_map<char, pair<int, char>> q4;
unordered_map<string, int> q5;

```

### **Inserting Keys and Values**

You can insert keys and their associated values in the following ways:

1. **Using `insert`**: `q.insert(make_pair(3, 7));`
2. **Using `[]` Operator**:
```c++
q[3] = 7;
cout << q.at(3);  // Outputs: 7

```
**Key Points**:

- `q.at(key)`: Throws an error if the key doesn't exist.
- `q[key]`: Inserts the key with a default value (0 for integers) if it doesn't exist.
- To check if a key exists, use `q.count(key)` before accessing it.




### **Handling Duplicate Keys**

If a key already exists, assigning a new value to it will overwrite the previous value:
```c++
unordered_map<int, int> q;
q[3] = 7;
q[3] = 10;

cout << q[3] << endl;  // Output: 10

```

If you want to associate multiple values with the same key, use a `vector`:

```c++
unordered_map<int, vector<int>> q;
q[3].push_back(7);
q[3].push_back(10);
// q[3] now holds a vector: {7, 10}

```

### **Checking If a Key Exists**

1. **Using `count()`**:
```c++

if (q.count(ourkey) > 0) {
    cout << "Key exists" << endl;
} else {
    cout << "Key does not exist" << endl;
}
```

- `q.count(key)`: Returns `1` if the key exists, `0` otherwise.

2. **Using `find()`**:
```c++
unordered_map<int, int>::iterator it = q.find(ourkey);
if (it == q.end()) {
    cout << "Key does not exist" << endl;
} else {
    cout << it->first << " -> " << it->second << endl;
}

```
![MAPS &SETS 1.1-20241122091753756.webp](../../../../../Images/MAPS%20&SETS%201.1-20241122091753756.webp)

### **Key Notes**

1. **Default Value Behavior**:
    
    - Accessing a non-existent key using `q[key]` inserts it with a default value (e.g., `0` for integers).
    - Use `q.count(key)` or `q.find(key)` to avoid unintentional insertion.
2. **Performance**:
    
    - Average time complexity for insertions, deletions, and lookups is **O(1)** due to hashing.
    - Worst case: **O(n)** if there are hash collisions.


### BEWARE

```C++
map<int,int> m;
cout << m[3] << endl;
```

This seems innocent enough right? Well, in C++, things often works in ways you wouldn't expect. In this particular code we just wanted to print out map element with key 3, which we didn't create, so you would expect it would throw some kind of exception, but this is totally okay for compilers, they will initiliaze map[3] = 0, so by printing out non-existent element from out map, we essentially created that element

  

## **PAIR**

```C++
#include <utility>  // Required for pair

int main() {
// Creating a pair
pair<int, string> p1(1, "Hello"); // Kuch bhi do skte hain 
// Accessing elements
cout<<p1<<endl;  // direct print krne se error aega
cout << "First: " << p1.first << "\\n";  // Output: First: 1
cout << "Second: " << p1.second << "\\n"; // Output: Second: Hello

// Using make_pair for creation
auto p2 = make_pair(2, "World");

// Accessing elements
cout << "First: " << p2.first << "\\n";  // Output: First: 2
cout << "Second: " << p2.second << "\\n"; // Output: Second: World

return 0;
}
```

⇒ Unordered map hamesha pair ko recieve karta hai
⇒key,value pair ki baat horahi hai yaahan
⇒Hashmap and hashset mein kind of unlimited size hota hai
![image 5 15.png](../../../../../Images/image%205%2015.png)
![image 6 15.png](../../../../../Images/image%206%2015.png)
![image 7 14.png](../../../../../Images/image%207%2014.png)

insert karne ka better tarika then a key value pair
![image 8 14.png](../../../../../Images/image%208%2014.png)

![image 9 13.png](../../../../../Images/image%209%2013.png)











  QUESTIONS:
 VALID ANAGRAM
 TWO SUM
 UNIQUE NUMBER OF OCCURENCES 



  

