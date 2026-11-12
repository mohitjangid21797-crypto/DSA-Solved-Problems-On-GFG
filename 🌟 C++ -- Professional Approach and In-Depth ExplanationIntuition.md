## 01. 🌟 C++ || Professional Approach and In-Depth ExplanationIntuition

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/tree-from-postorder-and-inorder/1)

### Problem Description

**Task:** Given two arrays representing the inorder and postorder traversals of a binary tree, your task is to construct the binary tree and return its root.

> **Note:** The inorder and postorder traversals contain unique values, and every value present in the postorder traversal is also found in the inorder traversal.

#### Examples

##### Example 1

- **Input:**
```text
inorder[] = [4, 8, 2, 5, 1, 6, 3, 7], postorder[] = [8, 4, 5, 2, 6, 7, 3, 1]
```
- **Output:**
```text
[1, 2, 3, 4, 5, 6, 7, N, 8]
```
- **Explanation:** For the given inorder and postorder traversal of tree the resultant binary tree will be:

##### Example 2

- **Input:**
```text
inorder[] = [9, 5, 2, 3, 4], postorder[] = [5, 9, 3, 4, 2]
```
- **Output:**
```text
[2, 9, 4, N, 5, 3]
```
- **Explanation:** The resultant binary tree will be:

#### Constraints

- **1.** `1 ≤ number of nodes ≤ 10³⁰ ≤ inorder[i], postorder[i] ≤ 10⁶`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (3)

#### Solution 1 (C++)

- **Submitted:** 2026-10-04 17:01:27
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of binary tree node
class Node {
  public:
    int data;
    Node* left;
    Node* right;
    Node(int x) {
        data = x;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  int find(vector<int>&inorder , int start  , int end , int target)
  {
      for(int i = start ; i<=end ; i++)
      {
          if(inorder[i]==target)
          return i;
      }
      return -1;
  }
  Node *Tree(vector<int>&postorder , vector<int>&inorder , int instart  , int inend , int index)
  {
      if(instart>inend)
      return NULL;
      Node *root = new Node(postorder[index]);
      int pos = find(inorder , instart , inend , postorder[index]);
      root->right = Tree(postorder , inorder , pos+1 , inend , index+1);
      root->left = Tree(postorder , inorder , instart , pos-1 , index + inend-pos+1);
      return root;
  }
    Node *buildTree(vector<int> &inorder, vector<int> &postorder) {
        // code here
        int start = 0 , end = postorder.size()-1;
            while(start<=end)
            {
                swap(postorder[start] , postorder[end]);
                start++;
                end--;
            }
        Node *root = Tree(postorder , inorder , 0 , postorder.size()-1 , 0);
        return root;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-04 17:00:14
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of binary tree node
class Node {
  public:
    int data;
    Node* left;
    Node* right;
    Node(int x) {
        data = x;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  int find(vector<int>&inorder , int start  , int end , int target)
  {
      for(int i = start ; i<=end ; i++)
      {
          if(inorder[i]==target)
          return i;
      }
      return -1;
  }
  Node *Tree(vector<int>&postorder , vector<int>&inorder , int instart  , int inend , int index)
  {
      if(instart>inend)
      return NULL;
      Node *root = new Node(postorder[index]);
      int pos = find(inorder , instart , inend , postorder[index]);
      root->right = Tree(postorder , inorder , pos+1 , inend , index+1);
      root->left = Tree(postorder , inorder , instart , pos-1 , index + inend-pos+1);
      return root;
  }
    Node *buildTree(vector<int> &inorder, vector<int> &postorder) {
        // code here
        int start = 0 , end = postorder.size()-1;
            while(start<=end)
            {
                swap(postorder[start] , postorder[end]);
                start++;
                end--;
            }
        Node *root = Tree(postorder , inorder , 0 , postorder.size()-1 , 0);
        return root;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-04 16:59:48
- **Status:** Correct
- **Marks:** 4

```cpp
/* Structure of binary tree node
class Node {
  public:
    int data;
    Node* left;
    Node* right;
    Node(int x) {
        data = x;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  int find(vector<int>&inorder , int start  , int end , int target)
  {
      for(int i = start ; i<=end ; i++)
      {
          if(inorder[i]==target)
          return i;
      }
      return -1;
  }
  Node *Tree(vector<int>&postorder , vector<int>&inorder , int instart  , int inend , int index)
  {
      if(instart>inend)
      return NULL;
      Node *root = new Node(postorder[index]);
      int pos = find(inorder , instart , inend , postorder[index]);
      root->right = Tree(postorder , inorder , pos+1 , inend , index+1);
      root->left = Tree(postorder , inorder , instart , pos-1 , index + inend-pos+1);
      return root;
  }
    Node *buildTree(vector<int> &inorder, vector<int> &postorder) {
        // code here
        int start = 0 , end = postorder.size()-1;
            while(start<=end)
            {
                swap(postorder[start] , postorder[end]);
                start++;
                end--;
            }
        Node *root = Tree(postorder , inorder , 0 , postorder.size()-1 , 0);
        return root;
    }
};
```

*Generated on: 10/4/2026, 5:26:43 PM*