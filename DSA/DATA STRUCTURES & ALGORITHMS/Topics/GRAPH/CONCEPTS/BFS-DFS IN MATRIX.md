## 🔁 Common Pattern: **Graph Traversal on 2D Grids**

You're essentially working with **grid-based problems**, and each of them represents a variation of **graph traversal**, where:

- Each **cell is treated like a node** in a graph.
    
- Movement is allowed in **4 directions (up/down/left/right)** or **8 directions (diagonals included)**.
    
- Traversal is done using **DFS or BFS** depending on what is asked.
    
- A `visited` array or some form of state change is used to prevent revisiting.
    

---

## 🔍 Let’s Analyze Problem-by-Problem

---

### **1. Flood Fill (DFS)**

> Replace all connected pixels of the same initial color (starting from `(sr, sc)`) with a new color.

- You're performing **DFS from a single point** (`(sr, sc)`).
    
- Replace all connected pixels of the **same initial color**.
    
- Movement: 4-directional.
    

🧠 **Key Idea:** _Single-source DFS traversal on a 2D matrix with a condition._

---

### **2. Rotting Oranges (Multi-source BFS)**

> Rotten oranges rot adjacent fresh oranges every minute. Find how many minutes to rot all.

- This is **multi-source BFS**.
    
- Start from all rotten oranges (`2`) simultaneously.
    
- Each level of BFS = 1 minute passing.
    
- Movement: 4-directional.
    

🧠 **Key Idea:** _BFS from multiple sources to track "spreading" behavior like infection or fire._

---

### **3. Count Islands (DFS on components)**

> Count how many connected groups of 'L' (land) are present.

- This is a **connected components in a grid** problem.
    
- Each group of `'L'` is an island.
    
- DFS is launched from any unvisited `'L'`.
    
- Movement: 8-directional (includes diagonals).
    

🧠 **Key Idea:** _DFS to find the number of connected components._

---

## 🔑 What Pattern Are You Practicing?

### ✅ Pattern Name: **"Graph on Grid" Traversals**

---

## 🎯 Concepts You’re Learning:

|Concept|Problem|Technique Used|
|---|---|---|
|Single-source DFS|Flood Fill|DFS|
|Multi-source BFS|Rotting Oranges|BFS (level-order)|
|DFS for connected components|Count Islands|DFS|
|Grid as a Graph|All|Map each (i,j) to a graph node|
|Movement via `dx/dy` arrays|All|Used to navigate 4 or 8 directions|
|Avoiding revisits|All|via `visited[][]` or state change|
|Component-wise traversal|Islands|Counting distinct groups|

---

## 🧠 Meta-Understanding:

You’re currently learning to:

- Recognize when a **2D matrix** can be treated as a **graph**.
    
- Decide between **DFS vs BFS**:
    
    - Use **DFS** when you want to explore full connected areas (like coloring or counting).
        
    - Use **BFS** when you need level-wise spreading or shortest paths.
        
- Use **`dx[] / dy[]`** arrays to simplify direction logic.
    
- Track visited states either through a `vis[][]` array or by modifying the matrix itself.
    

---

### 🌱 You're Building Muscle Memory For:

- Traversing and modifying 2D structures.
    
- Recognizing patterns like **flood fill**, **infection spread**, and **connected components**.
    
- Choosing the right traversal algorithm (DFS/BFS).
    
- Avoiding revisits and infinite loops.
    

---

## 🚀 Next Problems to Try in the Same Pattern:

|Problem|Technique|
|---|---|
|Number of Enclaves|DFS|
|Surrounded Regions|DFS/BFS|
|Pacific Atlantic Water Flow|Multi-source DFS|
|Word Search|Backtracking with DFS|
|Maze (shortest path)|BFS|
|Fire Spread|Multi-source BFS|

---

Sure! Here are the **next 5 problems** to strengthen your grip on grid-based DFS/BFS:

1. **Number of Enclaves**
    
2. **Surrounded Regions**
    
3. **Walls and Gates**
    
4. **Pacific Atlantic Water Flow**
    
5. **Shortest Path in Binary Matrix**