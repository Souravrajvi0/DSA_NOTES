# C++ Code Template

## Full Solution Template

```cpp
class Solution {
public:
    // Return type and function signature
    returnType functionName(parameters) {
        // Edge cases


        // Variables/Data structures needed


        // Main logic


        // Return result

    }
};
```

**⏱️ Complexity Analysis:**
| Complexity Type  | Value   | Explanation |
| ---------------- | ------- | ----------- |
| Time Complexity  | **O()** | [Why this complexity] |
| Space Complexity | **O()** | [Why this complexity] |

---

## Common C++ Snippets

### 1. Input/Output
```cpp
// Fast I/O
ios_base::sync_with_stdio(false);
cin.tie(NULL);

// Read single integer
int n;
cin >> n;

// Read array
vector<int> arr(n);
for(int i = 0; i < n; i++) {
    cin >> arr[i];
}

// Print result
cout << result << endl;
```

### 2. Vector Operations
```cpp
// Initialize
vector<int> v;                    // empty
vector<int> v(n);                 // size n, filled with 0
vector<int> v(n, value);          // size n, filled with value
vector<vector<int>> grid(n, vector<int>(m, 0)); // 2D

// Common operations
v.push_back(x);                   // add element
v.pop_back();                     // remove last
v.size();                         // get size
v.empty();                        // check if empty
v.clear();                        // clear all elements
reverse(v.begin(), v.end());      // reverse
sort(v.begin(), v.end());         // sort ascending
sort(v.begin(), v.end(), greater<int>()); // sort descending
```

### 3. String Operations
```cpp
string s = "hello";
s.length();                       // get length
s.substr(pos, len);              // substring
s.find(substr);                  // find substring (returns pos or string::npos)
s.push_back(ch);                 // add character
s.pop_back();                    // remove last character
reverse(s.begin(), s.end());     // reverse
```

### 4. Queue (BFS)
```cpp
#include <queue>

queue<int> q;
q.push(x);                       // enqueue
q.pop();                         // dequeue
q.front();                       // get front
q.empty();                       // check if empty
q.size();                        // get size
```

### 5. Stack (DFS)
```cpp
#include <stack>

stack<int> st;
st.push(x);                      // push
st.pop();                        // pop
st.top();                        // get top
st.empty();                      // check if empty
st.size();                       // get size
```

### 6. Priority Queue (Heap)
```cpp
#include <queue>

// Max heap (default)
priority_queue<int> maxHeap;
maxHeap.push(x);
maxHeap.top();                   // get max
maxHeap.pop();

// Min heap
priority_queue<int, vector<int>, greater<int>> minHeap;
minHeap.push(x);
minHeap.top();                   // get min
minHeap.pop();

// Custom comparator for pairs (min heap by second element)
auto cmp = [](pair<int,int> a, pair<int,int> b) { return a.second > b.second; };
priority_queue<pair<int,int>, vector<pair<int,int>>, decltype(cmp)> pq(cmp);
```

### 7. Map & Set
```cpp
#include <map>
#include <unordered_map>
#include <set>
#include <unordered_set>

// Map (ordered)
map<int, int> mp;
mp[key] = value;                 // insert/update
mp.count(key);                   // check if exists (0 or 1)
mp.erase(key);                   // remove

// Unordered Map (hash map - faster)
unordered_map<int, int> ump;
ump[key] = value;
ump.count(key);
ump.find(key) != ump.end();     // check if exists

// Set (ordered, unique)
set<int> s;
s.insert(x);
s.erase(x);
s.count(x);                      // check if exists

// Unordered Set (hash set - faster)
unordered_set<int> us;
us.insert(x);
us.erase(x);
us.count(x);
```

### 8. Pair & Tuple
```cpp
// Pair
pair<int, int> p = {1, 2};
p.first;                         // access first
p.second;                        // access second
make_pair(1, 2);

// Tuple (3+ elements)
tuple<int, int, int> t = {1, 2, 3};
get<0>(t);                       // access first element
```

### 9. Algorithms
```cpp
#include <algorithm>

// Sort
sort(arr.begin(), arr.end());                    // ascending
sort(arr.begin(), arr.end(), greater<int>());    // descending

// Binary Search (array must be sorted)
binary_search(arr.begin(), arr.end(), target);   // returns true/false
lower_bound(arr.begin(), arr.end(), target);     // iterator to first >= target
upper_bound(arr.begin(), arr.end(), target);     // iterator to first > target

// Min/Max
min(a, b);
max(a, b);
*min_element(arr.begin(), arr.end());            // min in array
*max_element(arr.begin(), arr.end());            // max in array

// Reverse
reverse(arr.begin(), arr.end());

// Count
count(arr.begin(), arr.end(), value);
```

### 10. Common Loops
```cpp
// For loop (index-based)
for(int i = 0; i < n; i++) {
    // code
}

// For-each loop (value)
for(int x : arr) {
    // x is copy
}

// For-each loop (reference)
for(int& x : arr) {
    // x is reference, can modify
}

// While loop
while(condition) {
    // code
}
```

### 11. Direction Arrays (Grid Problems)
```cpp
// 4 directions (up, right, down, left)
int dx[] = {-1, 0, 1, 0};
int dy[] = {0, 1, 0, -1};

// 8 directions (includes diagonals)
int dx[] = {-1, -1, -1, 0, 0, 1, 1, 1};
int dy[] = {-1, 0, 1, -1, 1, -1, 0, 1};

// Usage
for(int i = 0; i < 4; i++) {
    int nx = x + dx[i];
    int ny = y + dy[i];
    // check bounds and process
}
```

### 12. Graph Representation
```cpp
// Adjacency List (most common)
vector<vector<int>> adj(n);      // n nodes
adj[u].push_back(v);            // add edge u -> v

// For weighted graph
vector<vector<pair<int,int>>> adj(n); // {node, weight}
adj[u].push_back({v, weight});

// Adjacency Matrix
vector<vector<int>> adj(n, vector<int>(n, 0));
adj[u][v] = 1;                  // or weight
```

### 13. Common Math Operations
```cpp
#include <cmath>

abs(x);                          // absolute value
pow(base, exp);                  // power
sqrt(x);                         // square root
ceil(x);                         // ceiling
floor(x);                        // floor
min(a, b);                       // minimum
max(a, b);                       // maximum
gcd(a, b);                       // GCD (C++17)
```

### 14. Infinity Values
```cpp
int INF = 1e9;                   // 10^9 for int
int INF = INT_MAX;               // max int value
long long INF = 1e18;            // 10^18 for long long
long long INF = LLONG_MAX;       // max long long value
```

---

## Common Patterns Code

### Pattern 1: Two Pointer
```cpp
int left = 0, right = n - 1;
while(left < right) {
    // process
    if(condition) left++;
    else right--;
}
```

### Pattern 2: Sliding Window (Fixed Size)
```cpp
int windowSum = 0;
for(int i = 0; i < k; i++) {
    windowSum += arr[i];
}
int maxSum = windowSum;

for(int i = k; i < n; i++) {
    windowSum += arr[i] - arr[i - k];
    maxSum = max(maxSum, windowSum);
}
```

### Pattern 3: Sliding Window (Variable Size)
```cpp
int left = 0, right = 0;
while(right < n) {
    // expand window
    // add arr[right] to window

    while(windowInvalid) {
        // shrink window
        // remove arr[left] from window
        left++;
    }

    // update result
    right++;
}
```

### Pattern 4: BFS Template
```cpp
queue<int> q;
vector<int> visited(n, 0);
q.push(start);
visited[start] = 1;

while(!q.empty()) {
    int node = q.front();
    q.pop();

    for(int neighbor : adj[node]) {
        if(!visited[neighbor]) {
            visited[neighbor] = 1;
            q.push(neighbor);
        }
    }
}
```

### Pattern 5: DFS Template
```cpp
void dfs(int node, vector<vector<int>>& adj, vector<int>& visited) {
    visited[node] = 1;

    for(int neighbor : adj[node]) {
        if(!visited[neighbor]) {
            dfs(neighbor, adj, visited);
        }
    }
}
```

---

## Notes & Reminders

### Common Mistakes to Avoid
- [ ] Integer overflow (use `long long` when needed)
- [ ] Array bounds (check `i < n` not `i <= n`)
- [ ] Off-by-one errors
- [ ] Uninitialized variables
- [ ] Modifying container while iterating

### Performance Tips
- Use `unordered_map` instead of `map` for better performance (O(1) vs O(log n))
- Use `reserve()` for vectors if size is known
- Pass large objects by reference to avoid copying
- Use `emplace_back()` instead of `push_back()` for efficiency
