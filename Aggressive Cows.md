## 01. Aggressive Cows

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/aggressive-cows/1)

### Problem Description

**Task:** Given an integer array arr[], which denotes the positions of stalls. All the positions are distinct. There are k aggressive cows.Assign the cows to the stalls such that the minimum distance between any two cows is maximized.Examples:Input: arr[] = [1, 2, 4, 8, 9], k = 3

#### Examples

##### Example 1

- **Output:**
```text
4
```
- **Explanation:** The first cow can be placed at arr[0], the second at arr[1], and the third at arr[4]. In this arrangement, the minimum distance between any two cows is 4 (between arr[1] and arr[4]), which is the maximum possible among all valid arrangements.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log m)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C)

- **Submitted:** 2026-10-24 18:37:52
- **Status:** Correct
- **Marks:** 4

```c
int compare(const void *a, const void *b) {
    int x = *(const int *)a;
    int y = *(const int *)b;
    return (x > y) - (x < y);
}

int aggressiveCows(int *arr, int n, int k) {
    // code here
    qsort(arr, n, sizeof(int), compare);

    int low = 1;
    int high = arr[n - 1] - arr[0];

    int max = 0;

    while (low<=high){
        int mid = low+(high-low)/2;

        if (valid(arr, n, k, mid)) {
            max = mid;
            low = mid+1;
        }else{
            high = mid-1;
        }
    }
    return max;
}

int valid(int *arr, int n, int k, int gap) {
    int cows = 1;
    int last = arr[0];
    for(int i=1;i<n;i++){
        if(arr[i] - last >= gap){
            cows++;
            last = arr[i];
        }
        if(cows>=k) return 1;
    }
    return 0;
}
```

*Generated on: 10/24/2026, 6:39:53 PM*