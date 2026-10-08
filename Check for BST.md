## 01. Check for BST

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/check-for-bst/1)

### Problem Description

**Task:** Given a binary tree, check whether it is a Binary Search Tree (BST) or not. A binary tree is considered a BST if it satisfies the following properties:All nodes in the left subtree of a node have values less than the node's value.All nodes in the right subtree of a node have values greater than the node's value.Both the left and right subtrees are also Binary Search Trees.Return true if the given binary tree is a BST; otherwise, return false.Examples:Input: root = [2, 1, 3, N, N, N, 5]

#### Examples

##### Example 1

- **Output:**
```text
false
```
- **Explanation:** The node with data 9 present in the right subtree has lesser key value than root node 10.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(h)

### Accepted Solutions (4)

#### Solution 1 (C++)

- **Submitted:** 2026-10-08 15:21:33
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
}; */

class Solution {
  public:
 bool checkBST(Node *root , int &prev)
 {
     if(root==NULL)
     return 1;
     bool l = checkBST(root->left , prev);
     if(l==0)
     return 0;
     if(root->data<=prev)
     return 0;
     prev = root->data;
     return checkBST(root->right , prev);
     
 }
    bool isBST(Node* root) {
        int prev = INT_MIN;
        return checkBST(root, prev);
    }
    
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-08 15:21:21
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
}; */

class Solution {
  public:
 bool checkBST(Node *root , int &prev)
 {
     if(root==NULL)
     return 1;
     bool l = checkBST(root->left , prev);
     if(l==0)
     return 0;
     if(root->data<=prev)
     return 0;
     prev = root->data;
     return checkBST(root->right , prev);
     
 }
    bool isBST(Node* root) {
        int prev = INT_MIN;
        return checkBST(root, prev);
    }
    
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-08 15:16:29
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
}; */

class Solution {
  public:
  void Inorder(Node *root , vector<int>&arr)
  {
      if(root==NULL)
      return;
      Inorder(root->left , arr);
      arr.push_back(root->data);
      Inorder(root->right , arr);
  }
    bool isBST(Node* root) {
     vector<int>ans;
     Inorder(root , ans);
     for(int i = 0 ; i<ans.size()-1 ; i++)
    {
        if(ans[i]>=ans[i+1])
        {
            return 0;
        }
    }
    return 1;
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-10-08 15:16:12
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
}; */

class Solution {
  public:
  void Inorder(Node *root , vector<int>&arr)
  {
      if(root==NULL)
      return;
      Inorder(root->left , arr);
      arr.push_back(root->data);
      Inorder(root->right , arr);
  }
    bool isBST(Node* root) {
     vector<int>ans;
     Inorder(root , ans);
     for(int i = 0 ; i<ans.size()-1 ; i++)
    {
        if(ans[i]>=ans[i+1])
        {
            return 0;
        }
    }
    return 1;
    }
};
```

*Generated on: 10/8/2026, 3:21:53 PM*