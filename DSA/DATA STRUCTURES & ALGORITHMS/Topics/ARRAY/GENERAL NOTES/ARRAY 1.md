## **What is an Array?**

An array is a **fixed-size collection of elements** of the same type, stored in contiguous memory locations. Arrays allow efficient access to their elements using indices, starting from `0` to `n-1`.

## **Characteristics of Arrays**

1. **Fixed Size**: Once declared, the size of an array cannot be changed.
2. **Contiguous Memory**: All elements are stored in consecutive memory locations.
3. **Random Access**: You can directly access any element using its index in **O(1)** time.
4. **Homogeneous Elements**: All elements in the array must be of the same data type.

## **Syntax of Declaring Arrays**


```c++
data_type array_name[array_size];
int arr[5]; // Declares an integer array of size 5

```

### Initialization:


```c++
int arr[5] = {1, 2, 3, 4, 5}; // Initializes all elements
int arr[5] = {1, 2};          // Partially initializes: {1, 2, 0, 0, 0}
int arr[] = {1, 2, 3};        // Compiler determines size (3)
```

### Accessing Elements:


```c++
arr[0] = 10;       // Assign 10 to the first element
cout << arr[2];    // Print the third element

```


![ARRAY 1-20241223080853050.webp](../../../../../Images/ARRAY%201-20241223080853050.webp)

### LARGEST ELEMENT IN AN ARRAY

BRUTE FORCE: SORT AND RETURN ARR[N-1] (The last element)
OPTIMAL:
```c++
int largest(vector<int> &arr) {
        // code here
        int l=arr[0];
        for(int i=0;i<arr.size();i++){
            if(arr[i]>l){
                l=arr[i];
            }
        }
        return l;
    }
```
### Second Largest in an array

**BRUTE FORCE:** 
SORT AND RETURN SECOND LAST?? WON'T WORK - Since all the elements can be same right then!
![ARRAY 1-20241223083115119.webp](../../../../../Images/ARRAY%201-20241223083115119.webp)

Sure main yahan huon ki last element hi sabse bada hoga!!

```c++
int getSecondLargest(vector<int> &arr) {
        // Code Here
        sort(arr.begin(),arr.end());
        int sl=-1;
        for(int i=arr.size()-2;i>=0;i--){
            if(arr[i]!=arr[arr.size()-1]){
                sl=arr[i];
                break;
            }
        }
        return sl;
}
```

But this is NlogN +N approach!

**BETTER APPROACH:**
THIS APPROACH IS OF O(2N)
```c++
   int largest(vector<int> &arr) {
        // code here
       int l=arr[0];
       for(int i=0;i<arr.size();i++){
           if(arr[i]>l){
               l=arr[i];
           }
       }
       
       int sl=-1;
       for(int i=0;i<arr.size();i++){
           if(arr[i]>sl&&arr[i]<l){
               sl=arr[i];
           }
       }
       return sl;
    }

```

**OPTIMAL APPROACH:**

THIS APPROACH IS OF O(N)

```c++
 int getSecondLargest(vector<int> &arr) {
        // Code Here
      int l=arr[0];
      int sl=-1;
      for(int i=0;i<arr.size();i++){
          if(arr[i]>l){
              sl=l; // ye thoda bhulta huon main
              l=arr[i];
        }else if(arr[i]>sl&&arr[i]<l){
              sl=arr[i];
          }
      }
      return sl;
}

```

SO EK TARIKE SE MAINE 2 ROUNDS SE 1 ROUND PAR AGYA!!! WITH THE HELP OF USING ANE EXTRA VARIABLE
O(2N)-> O(N)


ISKE BAD YE SHIFTTING WALI QUESTION AA GAYE HAIN JISMEIN ARRAY KA KUCH PART SHIFT KARNA HOTA HAI!!

## LINEAR SEARCH 
![ARRAY 1-20241225175226573.webp](../../../../../Images/ARRAY%201-20241225175226573.webp)

First Occurrence k liye  direct return kardo, last Occurence k liye ulta chalu karo and All occurences k liye array rakh lo indexes ka!

