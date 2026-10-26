## 01. class Solution { public static long sumBetweenTwoKth(long A[], long N, long K1, long K2) { // Your code goes here long sum=0; PriorityQueue<Long> pq=new PriorityQueue<>(Collections.reverseOrder()); for(long ele:A){ pq.add(ele); if(pq.size()>=K2){ pq.poll(); }} long count=K2-K1-1; while(count!=0){ sum=sum+pq.poll(); count--; } return sum; }}

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sum-of-elements-between-k1th-and-k2th-smallest-elements3133/1)

### Problem Description

**Task:** Given an array arr[] of positive integers and two integers k1 and k2, find the sum of all array elements whose values lie between the k1-th smallest and the k2-th smallest (both k1th and k2th smallest are not included) of the array.Examples :Input: arr[] = [20, 8, 22, 4, 12, 10, 14], k1 = 3, k2 = 6Output: 26Explanation: 3rd smallest is 10 and 6th smallest is 20. Sum of all between k1-th and k2-th is 12 + 14 = 26.Input: arr[] = [1, 2, 3, 4, 5], k1 = 1, k2 = 5Output: 9Explanation: 1st smallest is 1 and 5th smallest is 5. Sum of all between k1-th and k2-th is 2 + 3 + 4 = 9.Input: arr[] = [5, 6, 7], k1 = 2, k2 = 3Output: 0Explanation: The 2nd smallest is 6 and the 3rd smallest is 7. Since there are no strictly between 6 and 7, the required sum is 0.Constraints:2 ≤ arr.size() ≤ 10⁵¹ ≤ k1 < k2 ≤ arr.size()1 ≤ arr[i] ≤ 2 * 10⁴

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log k2 )
- **Expected Auxiliary Space Complexity:** O(k2)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-26 18:22:06
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int sumBetweenK1K2(vector<int>& arr, int k1, int k2) {
        // code here
        priority_queue<int>p1 , p2;
        for(int i = 0 ; i<k1 ; i++)
        p1.push(arr[i]);
        for(int i = k1 ; i<arr.size() ; i++)
        {
            if(arr[i]<p1.top())
            {
                p1.pop();
                p1.push(arr[i]);
            }
        }
        
        for(int i = 0 ; i<k2-1 ; i++)
        p2.push(arr[i]);
        for(int i = k2-1; i<arr.size() ; i++)
        {
            if(arr[i]<p2.top())
            {
                p2.pop();
                p2.push(arr[i]);
            }
        }
        int ans1 = 0 , ans2 = 0;
        while(!p1.empty())
        {
            ans1+=p1.top();
            p1.pop();
        }
        while(!p2.empty())
        {
            ans2+=p2.top();
            p2.pop();
        }
        
        return ans2-ans1;
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-26 18:21:57
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    int sumBetweenK1K2(vector<int>& arr, int k1, int k2) {
        // code here
        priority_queue<int>p1 , p2;
        for(int i = 0 ; i<k1 ; i++)
        p1.push(arr[i]);
        for(int i = k1 ; i<arr.size() ; i++)
        {
            if(arr[i]<p1.top())
            {
                p1.pop();
                p1.push(arr[i]);
            }
        }
        
        for(int i = 0 ; i<k2-1 ; i++)
        p2.push(arr[i]);
        for(int i = k2-1; i<arr.size() ; i++)
        {
            if(arr[i]<p2.top())
            {
                p2.pop();
                p2.push(arr[i]);
            }
        }
        int ans1 = 0 , ans2 = 0;
        while(!p1.empty())
        {
            ans1+=p1.top();
            p1.pop();
        }
        while(!p2.empty())
        {
            ans2+=p2.top();
            p2.pop();
        }
        
        return ans2-ans1;
        
    }
};
```

*Generated on: 10/26/2026, 6:22:27 PM*