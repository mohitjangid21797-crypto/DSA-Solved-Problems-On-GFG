## 01. BST with Dead End

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/check-whether-bst-contains-dead-end/1)

### Problem Description

**Task:** Given a root of Binary Search Tree (BST) containing unique positive integers greater than 0. Find if the BST contains a dead end. A dead end is a leaf node in the BST such that no new node can be inserted in the BST at or below this node while maintaining the BST property and the constraint that all node values must be > 0.

#### Examples

##### Example 1

- **Input:**
```text
root[] = [8, 5, 9, 2, 7, N, N, 1]Output: true
```
- **Explanation:** Node 1 is a Dead End. We can neither insert 0 as only positives are allowed nor insert 3 (because 3 cannot be inserted as left of 2)

##### Example 2

- **Input:**
```text
root[] = [8, 7, 10, 2, N, 9, 13]Output: true
```
- **Explanation:** Node 9 is a Dead End in the given BST.

#### Constraints

- **1.** `1 ≤ number of nodes ≤ 3000¹ ≤ node- > data ≤ 10⁵^`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(h)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-12 17:34:44
- **Status:** Correct
- **Marks:** 0

```cpp
/* Tree Node structure
class Node
{
    int data;
    struct Node *left;
    struct Node *right;

    Node(int x){
        data = x;
        left = right = nullptr;
    }
};*/

class Solution {
  public:
  bool checkDeadEnd(Node *root , int lower , int upper)
  {
      if(root==NULL)
      return 0;
      if(!root->left&&!root->right)
      {
          if((root->data)-lower==1&&upper-root->data==1)
          return 1;
          else
          return 0;
      }
      return checkDeadEnd(root->left , lower , root->data)||checkDeadEnd(root->right , root->data , upper);
  }
    bool isDeadEnd(Node *root) {
        // Code here
        int lower = 0;
        int upper = INT_MAX;
        return checkDeadEnd(root , lower , upper);
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-12 17:34:32
- **Status:** Correct
- **Marks:** 4

```cpp
/* Tree Node structure
class Node
{
    int data;
    struct Node *left;
    struct Node *right;

    Node(int x){
        data = x;
        left = right = nullptr;
    }
};*/

class Solution {
  public:
  bool checkDeadEnd(Node *root , int lower , int upper)
  {
      if(root==NULL)
      return 0;
      if(!root->left&&!root->right)
      {
          if((root->data)-lower==1&&upper-root->data==1)
          return 1;
          else
          return 0;
      }
      return checkDeadEnd(root->left , lower , root->data)||checkDeadEnd(root->right , root->data , upper);
  }
    bool isDeadEnd(Node *root) {
        // Code here
        int lower = 0;
        int upper = INT_MAX;
        return checkDeadEnd(root , lower , upper);
        
    }
};
```

*Generated on: 10/12/2026, 5:35:04 PM*