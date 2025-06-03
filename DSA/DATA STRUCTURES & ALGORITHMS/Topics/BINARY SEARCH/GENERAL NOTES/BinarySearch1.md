The Problem Doesn't Necessarily have to be array related! **IT CAN BE USED ANYWHERE!! WHERE THE SEARCH SPACE IS SORTED!!!**
Think About how you search in a dictionary!!

Binary Search is an efficient algorithm used to find an element in a **sorted array**. It works by repeatedly dividing the search interval in half. If the value of the search key is **less than** the item in the middle, the search continues in the **left half**, otherwise in the **right half**.

### 🔍 How Binary Search Works

1. Start with two pointers: `low = 0` and `high = n - 1` (start and end of the array).
    
2. Calculate the middle index: `mid = low + (high - low) / 2`
    
3. Compare the middle element with the target:
    
    - If `arr[mid] == target`, return `mid`.
        
    - If `arr[mid] < target`, search in the right half: `low = mid + 1`.
        
    - If `arr[mid] > target`, search in the left half: `high = mid - 1`.
        
4. Repeat until `low > high`.

### ✅ C++ Implementation of Binary Search

**ITERATIVE** 
```c++
int binarySearch(int arr[], int n, int target) {
    int low = 0, high = n - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2; // To avoid overflow

        if (arr[mid] == target)
            return mid;
        else if (arr[mid] < target)
            low = mid + 1;
        else
            high = mid - 1;
    }

    return -1; // Not found
}
```

Time Complexity: O(logN)
Space Complexity: O(1)

SO BASICALLY YAHAN PAR GAME HAI SEARCH SPACE KO ADHA KARNE KA!! AUR DIVIDE KARNE KA SINCE WITH THE HELP OF THE MONOTONUS WAY OF CHANGE IN VALUES!!
SEARCH SPACE PAR KAM KARTE HAIN HUM YAHAN!
**RECURSIVE** 

```c++
int bsRecursive(int low, int high, int target, vector<int>& nums) {
    if (low > high) return -1;

    int mid = low + (high - low) / 2; // Prevents potential overflow
    if (nums[mid] == target) return mid;

    if (nums[mid] < target)
        return bsRecursive(mid + 1, high, target, nums);
    else
        return bsRecursive(low, mid - 1, target, nums);
}

int search(vector<int>& nums, int target) {
    return bsRecursive(0, nums.size() - 1, target, nums);
}
```

Time Complexity: O(logN)
Space Complexity: O(log N)
