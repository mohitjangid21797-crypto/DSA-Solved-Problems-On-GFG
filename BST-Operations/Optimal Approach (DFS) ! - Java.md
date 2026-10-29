## 01. Optimal Approach (DFS) ! - Java

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/print-bst-elements-in-given-range/1)

### Problem Description

**Task:** Given the root of a Binary Search Tree (BST) and two integers low and high, return all node values that lie in the inclusive range [low, high] in ascending order.

#### Examples

##### Example 1

- **Input:**
```text
root = [17, 4, 18, 2, 9, N, N], l = 4, h = 17 Output: [4, 9, 17]Explanation: The BST nodes whose values lie in the range [4, 17] are 4, 9, and 17. Hence the result is returned as [4, 9, 17].
```

##### Example 2

- **Input:**
```text
root = [16, 7, 20, 1, 10, N, N], l = 13, h = 23 Output: [16, 20]Explanation: The nodes in the range [13, 23] are 16 and 20. Hence the result is returned as [16, 20].
```

#### Constraints

- **1.** `1 ≤ Number of nodes ≤ 10⁵¹ ≤ l ≤ h ≤ 10⁶`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(height of the tree)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-12 17:00:33
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of tree Node
class Node {
public:
    int data;
    Node *left;
    Node *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};*/
class Solution {
  public:
  void printBST(Node *root , int low , int high , vector<int>&ans)
  {
      if(root==NULL)
      return ;
      if(root->data>low&&root->data>high)
      printBST(root->left , low , high , ans);
      else if(root->data<low&&root->data<high)
      printBST(root->right , low , high , ans);
      else
      {
          printBST(root->left , low , high , ans);
          ans.push_back(root->data);
          printBST(root->right , low , high , ans);
      }
  }
    vector<int> nodesInRange(Node *root, int low, int high) {
        // code here
        vector<int>ans;
        printBST(root , low , high , ans);
        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-12 17:00:21
- **Status:** Correct
- **Marks:** 2

```cpp
/* Structure of tree Node
class Node {
public:
    int data;
    Node *left;
    Node *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};*/
class Solution {
  public:
  void printBST(Node *root , int low , int high , vector<int>&ans)
  {
      if(root==NULL)
      return ;
      if(root->data>low&&root->data>high)
      printBST(root->left , low , high , ans);
      else if(root->data<low&&root->data<high)
      printBST(root->right , low , high , ans);
      else
      {
          printBST(root->left , low , high , ans);
          ans.push_back(root->data);
          printBST(root->right , low , high , ans);
      }
  }
    vector<int> nodesInRange(Node *root, int low, int high) {
        // code here
        vector<int>ans;
        printBST(root , low , high , ans);
        return ans;
    }
};
```

*Generated on: 10/12/2026, 5:00:53 PM*