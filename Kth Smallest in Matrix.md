## 01. Kth Smallest in Matrix

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/kth-element-in-matrix/1)

### Problem Description

**Task:** Given a square matrix mat[][], where each row and column is sorted in non-decreasing order. Find the kth smallest element in the matrix.Examples:Input: mat[][] = [[16, 28, 60, 64], [22, 41, 63, 91], [27, 50, 87, 93], [36, 78, 87, 94]], k = 3

#### Examples

##### Example 1

- **Output:**
```text
30
```
- **Explanation:** 30 is the 7^th smallest element.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n × log(max(mat) - min(mat)))
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-03 17:12:49
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int kthSmallest(vector<vector<int>> &p, int k) {
        // code here
        vector<pair<int , pair<int , int >>>p1;
            for(int i = 0 ; i<p[0].size() ; i++)
            {
                p1.push_back(make_pair(p[i][0], make_pair(i, 0)));
            }
            priority_queue<pair<int , pair<int , int >>, vector<pair<int , pair<int , int >>>, greater<pair<int , pair<int , int >>>> pq(p1.begin() , p1.end());
           pair<int , pair<int , int >>Element;
           int ans;
           int i , j;
           while (k--)
           {
            Element = pq.top();
            pq.pop();
            ans = Element.first;
            i = Element.second.first;
            j = Element.second.second;
            if(j+1<p.size())
            {
                pq.push(make_pair(p[i][j+1], make_pair(i, j+1)));
            }
           }
           return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-03 17:12:33
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int kthSmallest(vector<vector<int>> &p, int k) {
        // code here
        vector<pair<int , pair<int , int >>>p1;
            for(int i = 0 ; i<p[0].size() ; i++)
            {
                p1.push_back(make_pair(p[i][0], make_pair(i, 0)));
            }
            priority_queue<pair<int , pair<int , int >>, vector<pair<int , pair<int , int >>>, greater<pair<int , pair<int , int >>>> pq(p1.begin() , p1.end());
           pair<int , pair<int , int >>Element;
           int ans;
           int i , j;
           while (k--)
           {
            Element = pq.top();
            pq.pop();
            ans = Element.first;
            i = Element.second.first;
            j = Element.second.second;
            if(j+1<p.size())
            {
                pq.push(make_pair(p[i][j+1], make_pair(i, j+1)));
            }
           }
           return ans;
    }
};
```

*Generated on: 11/3/2026, 5:13:00 PM*