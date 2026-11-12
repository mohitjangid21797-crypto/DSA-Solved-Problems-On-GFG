## 01. Easiest Solution in C++ Using Priority Queue | Beginner Friendly

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/kth-largest-element-in-a-stream2220/1)

### Problem Description

**Task:** Given an input stream arr[] and a number k. Find the K^th largest element (not K^th largest unique element) after insertion of each element in the stream. If the K^th largest element doesn't exist, then answer will be -1 for that insertion. Return a list of same size as arr[] where each element represents the Kth largest value after the corresponding insertion.Examples :Input: arr[] = [1, 2, 3, 4, 5, 6], k = 4

#### Examples

##### Example 1

- **Output:**
```text
[-1, 2, 2, 3, 3] After 3, the steam is [3]. Tthe 2nd largest does not exist. Output is -1.After 2, the stream is [3, 2]. The 2nd largest is 2.After 1, the stream is [3, 2, 1]. The 2nd largest is 2.After 3, the stream is [3, 2, 1, 3]. The 2nd largest is 3.After 3, the stream is [3, 2, 1, 3, 3]. The 2nd largest is 3.Constraints:1 ≤ k ≤ n ≤ 10⁵¹ ≤ arr[i] ≤ 10⁵
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n * log(k))
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-26 17:43:02
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    vector<int> kthLargest(vector<int>& arr, int k) {
        // code here
         vector<int>ans;
         priority_queue<int , vector<int> , greater<int>>p;
         for(int i = 1 ; i<=k-1 ; i++)
         {
             ans.push_back(-1);
         }
         for(int i = 0 ; i<k ; i++)
         {
             p.push(arr[i]);
         }
         ans.push_back(p.top());
         for(int i = k ; i<arr.size() ; i++)
         {
             if(arr[i]>p.top())
             {
                 p.pop();
                 p.push(arr[i]);
             }
             ans.push_back(p.top());
             
         }
         
         
         return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-26 17:42:04
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    vector<int> kthLargest(vector<int>& arr, int k) {
        // code here
         vector<int>ans;
         priority_queue<int , vector<int> , greater<int>>p;
         for(int i = 1 ; i<=k-1 ; i++)
         {
             ans.push_back(-1);
         }
         for(int i = 0 ; i<k ; i++)
         {
             p.push(arr[i]);
         }
         ans.push_back(p.top());
         for(int i = k ; i<arr.size() ; i++)
         {
             if(arr[i]>p.top())
             {
                 p.pop();
                 p.push(arr[i]);
             }
             ans.push_back(p.top());
             
         }
         
         
         return ans;
    }
};
```

*Generated on: 10/26/2026, 5:43:24 PM*