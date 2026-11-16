## 01. Smallest Range in K Lists

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/find-smallest-range-containing-elements-from-k-lists/1)

### Problem Description

**Task:** Given a 2d integer array mat[][], where each row is sorted in ascending order. Find the smallest range [l, r] that includes at least one element from each row. If more than one such ranges are found, return the first one.Note: If there are two possible ranges [a, b] and [c, d] with the same size, choose the one with the smaller starting value, i.e., consider [a, b] if a < c.Examples:Input: mat[][] = [[4, 7, 9, 12, 15], [0, 8, 10, 14, 20], [6, 12, 16, 30, 50]]

#### Examples

##### Example 1

- **Output:**
```text
[4, 20]Explanation: Smallest range is formed by number 4 from the first list, 7 from second list and 20 from the third list.Constraints:1 ≤ n, k ≤ 5000 ≤ mat[i][j] ≤ 105
```
- **Explanation:** Smallest range is formed by number 7 from the first list, 8 from second list and 6 from the third list.Input: mat[][] = [[2, 4], [1, 7], [20, 40]]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n * k * log k)
- **Expected Auxiliary Space Complexity:** O(k)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-16 20:06:36
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    vector<int> findSmallestRange(vector<vector<int>>& mat) {
        // Code here
        int maximum = INT_MIN , minimum;
        vector<pair<int , pair<int , int>>>v;
        for(int i = 0 ; i<mat.size() ; i++)
        {
            v.push_back(make_pair(mat[i][0] , make_pair(i,0)));
            maximum = max(maximum , mat[i][0]);
        }
        
        priority_queue<pair<int , pair<int , int>> , vector<pair<int , pair<int , int>>> , greater<pair<int , pair<int , int>>>>p(v.begin() , v.end());
        minimum = p.top().first;
        vector<int>ans(2);
        ans[0] = minimum;
        ans[1] = maximum;
        pair<int , pair<int , int>>Element;
        int i , j;
        while(p.size()==mat.size())
        {
            Element = p.top();
            p.pop();
            i = Element.second.first;
            j = Element.second.second;
            if(j+1<mat[i].size())
            {
                p.push(make_pair(mat[i][j+1] , make_pair(i,j+1)));
                minimum =p.top().first;
                maximum = max(maximum , mat[i][j+1]);
            }
            if(maximum-minimum<ans[1]-ans[0])
            {
                ans[0] = minimum;
                ans[1] = maximum;
            }
        }
        return ans;
        
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-16 20:06:19
- **Status:** Correct
- **Marks:** 8

```cpp
class Solution {
  public:
    vector<int> findSmallestRange(vector<vector<int>>& mat) {
        // Code here
        int maximum = INT_MIN , minimum;
        vector<pair<int , pair<int , int>>>v;
        for(int i = 0 ; i<mat.size() ; i++)
        {
            v.push_back(make_pair(mat[i][0] , make_pair(i,0)));
            maximum = max(maximum , mat[i][0]);
        }
        
        priority_queue<pair<int , pair<int , int>> , vector<pair<int , pair<int , int>>> , greater<pair<int , pair<int , int>>>>p(v.begin() , v.end());
        minimum = p.top().first;
        vector<int>ans(2);
        ans[0] = minimum;
        ans[1] = maximum;
        pair<int , pair<int , int>>Element;
        int i , j;
        while(p.size()==mat.size())
        {
            Element = p.top();
            p.pop();
            i = Element.second.first;
            j = Element.second.second;
            if(j+1<mat[i].size())
            {
                p.push(make_pair(mat[i][j+1] , make_pair(i,j+1)));
                minimum =p.top().first;
                maximum = max(maximum , mat[i][j+1]);
            }
            if(maximum-minimum<ans[1]-ans[0])
            {
                ans[0] = minimum;
                ans[1] = maximum;
            }
        }
        return ans;
        
        
    }
};
```

*Generated on: 11/16/2026, 8:21:13 PM*