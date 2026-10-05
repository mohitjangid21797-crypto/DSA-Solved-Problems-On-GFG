## 01. Tree Boundary Traversal

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1)

### Problem Description

**Task:** Given a root of a Binary Tree, return its boundary traversal in the following order:
Left Boundary: Nodes from the root to the leftmost non-leaf node, preferring the left child over the right and excluding leaves.
Leaf Nodes: All leaf nodes from left to right, covering every leaf in the tree.
Reverse Right Boundary: Nodes from the root to the rightmost non-leaf node, preferring the right child over the left, excluding leaves, and added in reverse order.

> **Note:** The root is included once, leaves are added separately to avoid repetition, and the right boundary follows traversal preference not the path from the rightmost leaf.

#### Examples

##### Example 1

- **Input:**
```text
root = [1, 2, 3, 4, 5, 6, 7, N, N, 8, 9, N, N, N, N]
```
- **Output:**
```text
[1, 2, 4, 8, 9, 6, 7, 3]
```

##### Example 2

- **Input:**
```text
root = [1, N, 2, N, 3, N, 4, N, N]
```
- **Output:**
```text
[1, 4, 3, 2]
```
- **Explanation:** Left boundary: [1] (as there is no left subtree) Leaf nodes: [4] Right boundary: [3, 2] (in reverse order) Final traversal: [1, 4, 3, 2]

#### Constraints

- **1.** `1 ≤ number of nodes ≤ 10⁵¹ ≤ node- > data ≤ 10⁵`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(h)

### Accepted Solutions (5)

#### Solution 1 (C++)

- **Submitted:** 2026-10-05 15:15:41
- **Status:** Correct
- **Marks:** 0

```cpp
/* Node Structure
class Node {
  public:
    int data;
    Node* left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  void leftsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return;
      ans.push_back(root->data);
      if(root->left)
      {
          leftsubtree(root->left , ans);
      }
      else
      {
          leftsubtree(root->right , ans);
      }
  }
  void leaves(Node *root , vector<int>&ans)
  {
      if(root==NULL)
      return ;
      if(root->left==NULL&&root->right==NULL)
      ans.push_back(root->data);
      leaves(root->left , ans);
      leaves(root->right , ans);
  }
  void rightsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return ;
      if(root->right)
      {
          rightsubtree(root->right , ans);
      }
      else
      {
          rightsubtree(root->left , ans);
      }
      ans.push_back(root->data);
  }
    vector<int> boundaryTraversal(Node *root) {
        // code here
        vector<int>ans;
        if(root->left!=NULL||root->right!=NULL)
        ans.push_back(root->data);
        leftsubtree(root->left , ans);
        leaves(root , ans);
        rightsubtree(root->right , ans);
        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-05 15:14:15
- **Status:** Correct
- **Marks:** 0

```cpp
/* Node Structure
class Node {
  public:
    int data;
    Node* left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  void leftsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return;
      ans.push_back(root->data);
      if(root->left)
      {
          leftsubtree(root->left , ans);
      }
      else
      {
          leftsubtree(root->right , ans);
      }
  }
  void leaves(Node *root , vector<int>&ans)
  {
      if(root==NULL)
      return ;
      if(root->left==NULL&&root->right==NULL)
      ans.push_back(root->data);
      leaves(root->left , ans);
      leaves(root->right , ans);
  }
  void rightsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return ;
      if(root->right)
      {
          rightsubtree(root->right , ans);
      }
      else
      {
          rightsubtree(root->left , ans);
      }
      ans.push_back(root->data);
  }
    vector<int> boundaryTraversal(Node *root) {
        // code here
        vector<int>ans;
        if(root->left!=NULL||root->right!=NULL)
        ans.push_back(root->data);
        leftsubtree(root->left , ans);
        leaves(root , ans);
        rightsubtree(root->right , ans);
        return ans;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-05 15:12:59
- **Status:** Correct
- **Marks:** 0

```cpp
/* Node Structure
class Node {
  public:
    int data;
    Node* left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  void leftsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return;
      ans.push_back(root->data);
      if(root->left)
      {
          leftsubtree(root->left , ans);
      }
      else
      {
          leftsubtree(root->right , ans);
      }
  }
  void leaves(Node *root , vector<int>&ans)
  {
      if(root==NULL)
      return ;
      if(root->left==NULL&&root->right==NULL)
      ans.push_back(root->data);
      leaves(root->left , ans);
      leaves(root->right , ans);
  }
  void rightsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return ;
      if(root->right)
      {
          rightsubtree(root->right , ans);
      }
      else
      {
          rightsubtree(root->left , ans);
      }
      ans.push_back(root->data);
  }
    vector<int> boundaryTraversal(Node *root) {
        // code here
        vector<int>ans;
        if(root->left!=NULL||root->right!=NULL)
        ans.push_back(root->data);
        leftsubtree(root->left , ans);
        leaves(root , ans);
        rightsubtree(root->right , ans);
        return ans;
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-10-05 15:11:26
- **Status:** Correct
- **Marks:** 0

```cpp
/* Node Structure
class Node {
  public:
    int data;
    Node* left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  void leftsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return;
      ans.push_back(root->data);
      if(root->left)
      {
          leftsubtree(root->left , ans);
      }
      else
      {
          leftsubtree(root->right , ans);
      }
  }
  void leaves(Node *root , vector<int>&ans)
  {
      if(root==NULL)
      return ;
      if(root->left==NULL&&root->right==NULL)
      ans.push_back(root->data);
      leaves(root->left , ans);
      leaves(root->right , ans);
  }
  void rightsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return ;
      if(root->right)
      {
          rightsubtree(root->right , ans);
      }
      else
      {
          rightsubtree(root->left , ans);
      }
      ans.push_back(root->data);
  }
    vector<int> boundaryTraversal(Node *root) {
        // code here
        vector<int>ans;
        if(root->left!=NULL||root->right!=NULL)
        ans.push_back(root->data);
        leftsubtree(root->left , ans);
        leaves(root , ans);
        rightsubtree(root->right , ans);
        return ans;
    }
};
```

#### Solution 5 (C++)

- **Submitted:** 2026-08-24 12:43:18
- **Status:** Correct
- **Marks:** 0

```cpp
/* Node Structure
class Node {
  public:
    int data;
    Node* left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  void leftsub(Node *root , vector<int>&ans)
  {
      if(root==NULL||(!root->left&&!root->right))
      return;
      ans.push_back(root->data);
      if(root->left)
      leftsub(root->left , ans);
      else
      leftsub(root->right , ans);
  }
  void rightsub(Node *root , vector<int>&ans)
  {
      if(root==NULL||(!root->left&&!root->right))
      return;
      if(root->right)
      rightsub(root->right , ans);
      else
      rightsub(root->left , ans);
      ans.push_back(root->data);
  }
  void leaf(Node *root , vector<int>&ans)
  {
      if(!root)
      return ;
      if(!root->left&&!root->right)
      {
          ans.push_back(root->data);
          return ;
      }
      leaf(root->left , ans);
      leaf(root->right , ans);
  }
  
    vector<int> boundaryTraversal(Node *root) {
      vector<int>ans;
      ans.push_back(root->data);
      // leftsubtree:
      leftsub(root->left , ans);
      // leaf Nodes;
      if(root->left||root->right)
      leaf(root , ans);
      // rightsubtree:
      rightsub(root->right , ans);
      return ans; 
        
        
    }
};
```

*Generated on: 10/5/2026, 3:16:14 PM*