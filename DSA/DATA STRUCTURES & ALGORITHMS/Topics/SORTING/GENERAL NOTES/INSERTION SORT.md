  

![image-1725998618988.jpg2790802854257938521.jpg](../../../../../Images/image-1725998618988.jpg2790802854257938521.jpg)

  

My Code→

```C++
 void insertionSort(int arr[], int n)
    {
        //code here
        for(int i=1;i<n;i++){
             for(int j=i;j>=1;j--){
                if(arr[j]<arr[j-1]){
                    int a=arr[j];
                    arr[j]=arr[j-1];
                    arr[j-1]=a;
                }else{
                    break;
                }
            }
        }
    }
```

BETTER CODE→

![image 14.png](../../../../../Images/image%2014.png)

![image 1 7.png](../../../../../Images/image%201%207.png)

**STABLE HOTA HAI YE**