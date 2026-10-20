## 01. Max Sum Subarray of Size K

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1)

### Problem Description

**Task:** Given an array of integers arr[] and a number k. Return the maximum sum of a subarray of size k.Note: A subarray is a contiguous part of any given array.Examples:Input: arr[] = [100, 200, 300, 400], k = 2

#### Examples

##### Example 1

- **Output:**
```text
400
```
- **Explanation:** arr_3 = 400, which is maximum.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-20 08:14:50
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int maxSubarraySum(vector<int>& arr, int k) {
        // code here
        int left = 0;
        int right = left+k-1;
        int n = arr.size();
        
        int maxSum = 0;
        int curSum = 0;
        
        for(int i = left;i<=right;i++){
            curSum += arr[i];
        }
        
        while(right < n && left < n){
            
            if(curSum > maxSum){
                maxSum = curSum;
            }
    
            curSum -= arr[left];
            left++;
            right++;
            curSum += arr[right];
            
        }
        return maxSum;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-20 08:14:34
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    int maxSubarraySum(vector<int>& arr, int k) {
        // code here
        int left = 0;
        int right = left+k-1;
        int n = arr.size();
        
        int maxSum = 0;
        int curSum = 0;
        
        for(int i = left;i<=right;i++){
            curSum += arr[i];
        }
        
        while(right < n && left < n){
            
            if(curSum > maxSum){
                maxSum = curSum;
            }
    
            curSum -= arr[left];
            left++;
            right++;
            curSum += arr[right];
            
        }
        return maxSum;
    }
};
```

*Generated on: 10/20/2026, 8:21:59 AM*