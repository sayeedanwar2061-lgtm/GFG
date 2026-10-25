## 01. Array Leaders

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1)

### Problem Description

**Task:** You are given an array arr of positive integers. Your task is to find all the leaders in the array. An element is considered a leader if it is greater than or equal to all elements to its right. The rightmost element is always a leader.Examples:Input: arr = [16, 17, 4, 3, 5, 2]

#### Examples

##### Example 1

- **Output:**
```text
[17, 5, 2]
```
- **Explanation:** Note that there is nothing greater on the right side of 17, 5 and, 2.

##### Example 2

- **Input:**
```text
arr = [10, 4, 2, 4, 1]
```
- **Output:**
```text
[10, 4, 4, 1]Explanation: Note that both of the 4s are in output, as to be a leader an equal element is also allowed on the right. sideInput: arr = [5, 10, 20, 40]Output: [40]Explanation: When an array is sorted in increasing order, only the rightmost element is leader.Input: arr = [30, 10, 10, 5]Output: [30, 10, 10, 5]Explanation: When an array is sorted in non-increasing order, all elements are leaders.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-25 16:52:30
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    vector<int> leaders(vector<int>& arr) {
        stack<int> st;
        vector<int> ans;
        int n = arr.size();

        for (int i = n - 1; i >= 0; i--) {
            while (!st.empty() && st.top() <= arr[i]) {
                st.pop();
            }

            if (st.empty()) {
                ans.push_back(arr[i]);
            }

            st.push(arr[i]);
        }

        reverse(ans.begin(), ans.end());
        return ans;
    }
};
```

*Generated on: 10/25/2026, 4:52:50 PM*