## 01. Merge k Sorted Arrays

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/merge-k-sorted-arrays/1)

### Problem Description

**Task:** Given a 2D matrix mat[][] of size n x m. Each row in the matrix is sorted in non-decreasing order, merge all the rows and return a single sorted array that contains all the elements of the matrix.

#### Examples

##### Example 1

- **Input:**
```text
mat[][] = [[1, 3, 5, 7], [2, 4, 6, 8], [0, 9, 10, 11]]Output: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
```
- **Explanation:** Merging all elements from the 3 sorted arrays and sorting them results in: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11].

##### Example 2

- **Input:**
```text
mat[][] = [[1, 2, 3, 4], [2, 2, 3, 4], [5, 5, 6, 6], [7, 8, 9, 9]]Output: [1, 2, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 8, 9, 9]
```
- **Explanation:** Merging all elements from the 4 sorted arrays and sorting them results in:[1, 2, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 8, 9, 9]

#### Constraints

- **1.** `1 ≤ n * m ≤ 10⁵⁰ ≤ mat[i][j] ≤ 10⁶`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(k*log(n)), k = total no. of elementsAuxiliary Space: O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-11 17:53:48
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    vector<int> mergeArrays(vector<vector<int>> &arr) {
        // Code here
        vector<pair<int , pair<int , int>>>v;
        for(int i = 0 ; i<arr.size() ; i++)
        {
            v.push_back(make_pair(arr[i][0] , make_pair(i , 0)));
        }
        priority_queue<pair<int , pair<int , int>> , vector<pair<int , pair<int , int>>> ,greater<pair<int , pair<int , int>>>>p(v.begin() , v.end());
        pair<int , pair<int , int>>Element;
        int i  , j;
        vector<int>ans;
        while(!p.empty())
        {
            Element = p.top();
            p.pop();
            int x = Element.first;
            i = Element.second.first;
            j = Element.second.second;
            ans.push_back(x);
            if(j+1<arr[0].size())
            p.push(make_pair(arr[i][j+1] , make_pair(i , j+1)));
        }
        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-11 17:53:35
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    vector<int> mergeArrays(vector<vector<int>> &arr) {
        // Code here
        vector<pair<int , pair<int , int>>>v;
        for(int i = 0 ; i<arr.size() ; i++)
        {
            v.push_back(make_pair(arr[i][0] , make_pair(i , 0)));
        }
        priority_queue<pair<int , pair<int , int>> , vector<pair<int , pair<int , int>>> ,greater<pair<int , pair<int , int>>>>p(v.begin() , v.end());
        pair<int , pair<int , int>>Element;
        int i  , j;
        vector<int>ans;
        while(!p.empty())
        {
            Element = p.top();
            p.pop();
            int x = Element.first;
            i = Element.second.first;
            j = Element.second.second;
            ans.push_back(x);
            if(j+1<arr[0].size())
            p.push(make_pair(arr[i][j+1] , make_pair(i , j+1)));
        }
        return ans;
    }
};
```

*Generated on: 11/11/2026, 6:08:32 PM*