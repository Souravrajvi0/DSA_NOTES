MAIN FAYDA KYA HAI QUICK SORT KA??

**→Well Merge Sort ki space complexity is going to be equal to O(N) and The Space complexity of Quick Sort is going to be O(1)**

→

![image-1726729893341.jpg6193078550037899151.jpg](../../../../../Images/image-1726729893341.jpg6193078550037899151.jpg)

![image-1726729919748.jpg8455252153323545429.jpg](../../../../../Images/image-1726729919748.jpg8455252153323545429.jpg)

→ we’re not going to use Space here. We’re just going to use the concept of low and High Hee

→

![image-1726731030879.jpg2049468879309843679.jpg](../../../../../Images/image-1726731030879.jpg2049468879309843679.jpg)

![image-1726731062941.jpg7148845008270558462.jpg](../../../../../Images/image-1726731062941.jpg7148845008270558462.jpg)

→ PSEUDO CODE

![8C1D92E8-4A35-4C4C-8A99-A3AD5C5F791E.png](../../../../../Images/8C1D92E8-4A35-4C4C-8A99-A3AD5C5F791E.png)

### Purpose of the Partition Function

The `partition` function is used to rearrange the elements of the array so that all elements less than a chosen value (called the "pivot") are placed to its left, and all elements greater than the pivot are placed to its right. It then returns the index where the pivot element ends up after this rearrangement.

CODE→

```C++
int partition(vector<int> &arr, int low, int high) {
    int pivot = arr[low];
    int i = low;
    int j = high;

    while (i < j) {
        while (arr[i] <= pivot && i <= high - 1) {
            i++;
        }

        while (arr[j] > pivot && j >= low + 1) {
            j--;
        }
        if (i < j) swap(arr[i], arr[j]);
    }
    swap(arr[low], arr[j]);
    return j;
}

void qs(vector<int> &arr, int low, int high) {
    if (low < high) {
        int pIndex = partition(arr, low, high);
        qs(arr, low, pIndex - 1);
        qs(arr, pIndex + 1, high);
    }
}
```