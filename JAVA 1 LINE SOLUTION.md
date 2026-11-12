## 01. JAVA 1 LINE SOLUTION

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/height-of-heap5025/1)

### Problem Description

**Task:** Given a Binary Heap of size n in an array arr[]. Write a program to calculate the height of the Heap.Note: Return 1 if the n is 1.Examples:Input: n = 6, arr[] = [1, 3, 6, 5, 9, 8]

#### Examples

##### Example 1

- **Output:**
```text
3 Explaination: The tree looks like following (2) / \ (3) (9) / \ / \ (5) (15) (10) (14) / \ (6) (12)
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-23 15:59:02
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
    int heapHeight(int n, int arr[]) {
        // code here
        if(n==1)
        return 1;
        else
        {
            int count = 0;
            while(n!=1)
            {
                n/=2;
                count++;
            }
            return count;
        }
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-23 15:58:48
- **Status:** Correct
- **Marks:** 1

```cpp
class Solution {
  public:
    int heapHeight(int n, int arr[]) {
        // code here
        if(n==1)
        return 1;
        else
        {
            int count = 0;
            while(n!=1)
            {
                n/=2;
                count++;
            }
            return count;
        }
    }
};
```

*Generated on: 10/23/2026, 3:59:21 PM*