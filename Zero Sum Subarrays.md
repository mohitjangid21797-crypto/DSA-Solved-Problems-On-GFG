## 01. Zero Sum Subarrays

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/zero-sum-subarrays1825/1)

### Problem Description

**Task:** You are given an array arr[] of integers. Find the total count of subarrays with their sum equal to 0.Examples:Input: arr[] = [0, 0, 5, 5, 0, 0]

#### Examples

##### Example 1

- **Output:**
```text
4
```
- **Explanation:** The 4 subarrays are [-1, -3, 4], [-2, 2], [2, 4, 6, -12], and [-1, -3, 4, -2, 2]

##### Example 2

- **Input:**
```text
arr[] = [0]
```
- **Output:**
```text
1
```
- **Explanation:** The only subarray is [0].Constraints: 1 <= n <= 10⁶-10⁹ <= arr[ i ] <= 10⁹

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-13 17:41:08
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int findSubarray(vector<int> &arr) {
        // code here
       vector<int>prefix(arr.size());
    prefix[0] = arr[0];
    for (int i = 1; i <arr.size(); i++)
    {
        prefix[i] = prefix[i-1] + arr[i];
    }
    int total = 0;
    unordered_map<int  , int> m;
    m[0] = 1;
    for (int i = 0; i < prefix.size(); i++)
    {
        if(m[prefix[i]]==0)
        m[prefix[i]] = 1;
        else
        {
            total+=m[prefix[i]];
            m[prefix[i]]++;
        }
    }
    return total;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-13 17:40:56
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int findSubarray(vector<int> &arr) {
        // code here
       vector<int>prefix(arr.size());
    prefix[0] = arr[0];
    for (int i = 1; i <arr.size(); i++)
    {
        prefix[i] = prefix[i-1] + arr[i];
    }
    int total = 0;
    unordered_map<int  , int> m;
    m[0] = 1;
    for (int i = 0; i < prefix.size(); i++)
    {
        if(m[prefix[i]]==0)
        m[prefix[i]] = 1;
        else
        {
            total+=m[prefix[i]];
            m[prefix[i]]++;
        }
    }
    return total;
    }
};
```

*Generated on: 11/13/2026, 5:55:53 PM*