![image-1725985519476.jpg7029535620694811530.jpg](../../../../../Images/image-1725985519476.jpg7029535620694811530.jpg)

![image-1725992324638.jpg1369065165535004504.jpg](../../../../../Images/image-1725992324638.jpg1369065165535004504.jpg)

**YAHAN BASICALLY PASSES HOTE HAIN**

```C++
void bubbleSort(int arr[], int n) {
        // Your code here
        for(int i=1;i<n;i++){  // since i know n-1 passes honge pass 1->n-1
           bool sorted=true;   // Har bar check kar raha huon ki is pass mein agar kuch change
            for(int j=0;j<n-i;j++){ // nahi hua toh mtlb array sort ho chuka hai
                if(arr[j]>arr[j+1]){
                   swap(arr[j],arr[j+1]);
                   sorted=false;
                }
            }
            if(sorted)break;
        }
    }
```

![image 12.png](../../../../../Images/image%2012.png)

![image 1 5.png](../../../../../Images/image%201%205.png)

![image 2 5.png](../../../../../Images/image%202%205.png)

![image 3 3.png](../../../../../Images/image%203%203.png)

![image 4 3.png](../../../../../Images/image%204%203.png)

TOTAL NUMBER OF OPERATIONS IN BUBBLE SORT IS N(N-1)/2;