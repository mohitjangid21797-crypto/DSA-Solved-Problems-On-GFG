## 01. Kth Largest in BST

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/kth-largest-element-in-bst/1)

### Problem Description

**Task:** Given the root of a Binary Search Tree (BST) and an integer k, find the k-th largest element in the BST without modifying its structure.Examples:Input: root = [4, 2, 9], k = 2

#### Examples

##### Example 1

- **Output:**
```text
2Explanation: The 3rd largest element is 2.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(height of BST)

### Accepted Solutions (3)

#### Solution 1 (C++)

- **Submitted:** 2026-10-08 19:27:01
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of a Binary Tree Node
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
  void Kthmaximum(Node *root , int &k , int &ans)
  {
      if(root==NULL)
      return;
      Kthmaximum(root->right , k , ans);
      if(k==0)
      return;
      ans = min(ans , root->data);
      k--;
      Kthmaximum(root->left , k , ans);
  }
    int kthLargest(Node *root, int k) {
        // code here
        int ans = INT_MAX;
        Kthmaximum(root , k, ans);
        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-08 19:26:39
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of a Binary Tree Node
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
  void Kthmaximum(Node *root , int &k , int &ans)
  {
      if(root==NULL)
      return;
      Kthmaximum(root->right , k , ans);
      if(k==0)
      return;
      ans = min(ans , root->data);
      k--;
      Kthmaximum(root->left , k , ans);
  }
    int kthLargest(Node *root, int k) {
        // code here
        int ans = INT_MAX;
        Kthmaximum(root , k, ans);
        return ans;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-08 19:25:57
- **Status:** Correct
- **Marks:** 2

```cpp
/* Structure of a Binary Tree Node
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
  void Kthmaximum(Node *root , int &k , int &ans)
  {
      if(root==NULL)
      return;
      Kthmaximum(root->right , k , ans);
      k--;
      if(k==0)
      {
          ans = root->data;
      }
      if(k<=0)
      return;
      Kthmaximum(root->left , k , ans);
  }
    int kthLargest(Node *root, int k) {
        // code here
        int ans = INT_MAX;
        Kthmaximum(root , k, ans);
        return ans;
    }
};
```

*Generated on: 10/8/2026, 7:27:20 PM*