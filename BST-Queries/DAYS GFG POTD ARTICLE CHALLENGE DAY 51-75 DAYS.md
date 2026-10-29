## 01. 75 DAYS GFG POTD ARTICLE CHALLENGE DAY 51/75 DAYS

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/print-common-nodes-in-bst/1)

### Problem Description

**Task:** Given the roots r1 and r2 of two Binary Search Trees (BST), find all nodes that are present in both trees (the intersection of the two BSTs).
Return the common node values in sorted order.

#### Examples

##### Example 1

- **Input:**
```text
r1 = [5, 1, 10, 0, 4, 7, N, N, N, N, N, N, 9], r2 = [10, 7, 20, 4, 9, N, N] Output: [4, 7, 9, 10]Explanation: The values present in both BSTs are 4, 7, 9, and 10. Hence, the answer is [4, 7, 9, 10].
```

##### Example 2

- **Input:**
```text
r1 = [10, 2, 11, 1, 3, N, N], r2 = [2, 1, 3]Output: [1, 2, 3]Explanation: The values 1, 2, and 3 are present in both BSTs. Hence, the answer is [1, 2, 3].
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n1 + n2), where n1 and n2 are the number of nodes in r1 and r2 respectively.
- **Expected Auxiliary Space Complexity:** O(h1 + h2), where h1 and h2 are the heights of r1 and r2 respectively.

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-12 18:36:02
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of a Binary Search Tree node
class Node {
  public:
    int data;
    Node* left;
    Node* right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};*/

class Solution {
  public:
    vector<int> findCommon(Node* r1, Node* r2) {
        // code here
        vector<int>ans;
        stack<Node*>s1 , s2;
        while(r1)
        {
            s1.push(r1);
            r1 = r1->left;
        }
        while(r2)
        {
            s2.push(r2);
            r2 = r2->left;
        }
        while(!s1.empty()&&!s2.empty())
        {
            // both stack top element are equal :
            if(s1.top()->data==s2.top()->data)
            {
                ans.push_back(s1.top()->data);
                r1 = s1.top()->right;
                s1.pop();
                r2 = s2.top()->right;
                s2.pop();
            }
            // s1>s2
            else if(s1.top()->data>s2.top()->data)
            {
                r2 = s2.top()->right;
                s2.pop();
            }
            // s2>s1
            else
            {
                r1 = s1.top()->right;
                s1.pop();
            }
        while(r1)
        {
            s1.push(r1);
            r1 = r1->left;
        }
        while(r2)
        {
            s2.push(r2);
            r2 = r2->left;
        }
        
            
        }
        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-12 18:35:50
- **Status:** Correct
- **Marks:** 4

```cpp
/* Structure of a Binary Search Tree node
class Node {
  public:
    int data;
    Node* left;
    Node* right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};*/

class Solution {
  public:
    vector<int> findCommon(Node* r1, Node* r2) {
        // code here
        vector<int>ans;
        stack<Node*>s1 , s2;
        while(r1)
        {
            s1.push(r1);
            r1 = r1->left;
        }
        while(r2)
        {
            s2.push(r2);
            r2 = r2->left;
        }
        while(!s1.empty()&&!s2.empty())
        {
            // both stack top element are equal :
            if(s1.top()->data==s2.top()->data)
            {
                ans.push_back(s1.top()->data);
                r1 = s1.top()->right;
                s1.pop();
                r2 = s2.top()->right;
                s2.pop();
            }
            // s1>s2
            else if(s1.top()->data>s2.top()->data)
            {
                r2 = s2.top()->right;
                s2.pop();
            }
            // s2>s1
            else
            {
                r1 = s1.top()->right;
                s1.pop();
            }
        while(r1)
        {
            s1.push(r1);
            r1 = r1->left;
        }
        while(r2)
        {
            s2.push(r2);
            r2 = r2->left;
        }
        
            
        }
        return ans;
    }
};
```

*Generated on: 10/12/2026, 6:36:26 PM*