## 01. Min Cost to Connect Ropes

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-cost-of-ropes-1587115620/1)

### Problem Description

**Task:** Given an array, arr[] of rope lengths, connect all ropes into a single rope with the minimum total cost. The cost to connect two ropes is the sum of their lengths. Return the minimum possible cost.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [4, 3, 2, 6]
```
- **Output:**
```text
29
```
- **Explanation:** First connect 2 and 3 to get [4, 5, 6] with a cost of 5, then connect 4 and 5 to get [9, 6] with a cost of 9, and finally connect 9 and 6 to get one rope with a cost of 15, giving a total minimum cost of 29. Any other order, such as connecting 4 and 6 first, results in a higher total cost of 38.

##### Example 2

- **Input:**
```text
arr[] = [4, 2, 7, 6, 9]
```
- **Output:**
```text
62
```
- **Explanation:** First, connect ropes 4 and 2, which makes the array [6, 7, 6, 9]. Cost of this operation 4 + 2 = 6. Next, add ropes 6 and 6, which results in [12, 7, 9]. Cost of this operation 6 + 6 = 12. Then, add 7 and 9, which makes the array [12,16]. Cost of this operation 7 + 9 = 16. And finally, add these two which gives [28]. Hence, the total cost is 6 + 12 + 16 + 28 = 62.

##### Example 3

- **Input:**
```text
arr[] = [10]
```
- **Output:**
```text
0Explanation: Since there is only one rope, no connections are needed, so the cost is 0.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-23 16:56:58
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int minCost(vector<int>& arr) {
        // code here
        priority_queue<int , vector<int> , greater<int>>p;
        int cost = 0;
        for(int i = 0 ; i<arr.size() ; i++)
        p.push(arr[i]);
        
        while(p.size()>1)
        {
            int min1 = p.top();
            p.pop();
            int min2 = p.top();
            p.pop();
            int x = min1 + min2;
            cost+=x;
            p.push(x);
        }
        return cost;
    }
};
```

*Generated on: 10/23/2026, 4:57:42 PM*