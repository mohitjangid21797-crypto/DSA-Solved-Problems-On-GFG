## 01. Kth Largest

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/kth-largest-element5034/1)

### Problem Description

**Task:** Given an array arr[] and a number k. The task is to find the k^th largest element in the array.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [3, 5, 4, 2, 9], k = 3
```
- **Output:**
```text
4
```
- **Explanation:** Third largest element in the array is 4.

##### Example 2

- **Input:**
```text
arr[] = [4, 3, 7, 6, 5], k = 5
```
- **Output:**
```text
3
```
- **Explanation:** Fifth largest element in the array is 3.

#### Constraints

- **1.** `1 <= k <= arr.size <= 10⁶`
- **2.** `-10⁴ <= arr[i] <= 10⁴^`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log k)
- **Expected Auxiliary Space Complexity:** O(k)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-26 16:32:27
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int kthLargest(vector<int> &arr, int k) {
        // code here
        priority_queue<int , vector<int>, greater<int>>p;
        for(int i = 0 ; i<k ; i++)
        p.push(arr[i]);
        for(int i = k ; i<arr.size() ; i++)
        {
            if(arr[i]>p.top())
            {
                p.pop();
                p.push(arr[i]);
            }
        }
        return p.top();
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-26 16:32:15
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int kthLargest(vector<int> &arr, int k) {
        // code here
        priority_queue<int , vector<int>, greater<int>>p;
        for(int i = 0 ; i<k ; i++)
        p.push(arr[i]);
        for(int i = k ; i<arr.size() ; i++)
        {
            if(arr[i]>p.top())
            {
                p.pop();
                p.push(arr[i]);
            }
        }
        return p.top();
    }
};
```

*Generated on: 10/26/2026, 4:32:48 PM*