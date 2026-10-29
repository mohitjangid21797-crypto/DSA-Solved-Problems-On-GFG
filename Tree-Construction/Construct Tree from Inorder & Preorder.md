## 01. Construct Tree from Inorder & Preorder

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/construct-tree-1/1)

### Problem Description

**Task:** Given two arrays representing the inorder and preorder traversals of a binary tree, construct the binary tree and return its root.

> **Note:** The inorder and preorder traversals contain unique values, and every value present in the preorder traversal is also found in the inorder traversal.

#### Examples

##### Example 1

- **Input:**
```text
inorder[] = [3, 1, 4, 0, 5, 2], preorder[] = [0, 1, 3, 4, 2, 5]
```
- **Output:**
```text
[0, 1, 2, 3, 4, 5]
```
- **Explanation:** The tree will look like

##### Example 2

- **Input:**
```text
inorder[] = [2, 5, 4, 1, 3], preorder[] = [1, 4, 5, 2, 3]
```
- **Output:**
```text
[1, 4, 3, 5, N, N, N, 2]Explanation: The tree will look like
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (3)

#### Solution 1 (C++)

- **Submitted:** 2026-10-04 15:53:05
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of a Tree Node
class Node {
public:
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  // To find position of element in inorder array:
  int find(vector<int>&inorder , int start , int end , int target)
  {
      for(int i = start ; i<=end ; i++)
      {
          if(inorder[i]==target)
          return i;
      }
      return -1;
  }
  Node *Tree(vector<int>&preorder , vector<int>&inorder , int instart , int inend , int index)
  {
      if(instart>inend)
      return NULL;
      Node *root = new Node(preorder[index]);
      int pos = find(inorder , instart ,inend , preorder[index]);
      root->left = Tree(preorder , inorder , instart , pos-1 , index+1);
      root->right = Tree(preorder , inorder , pos+1 , inend , index+pos-instart+1);
      return root;
  }
  
    Node *buildTree(vector<int> &inorder, vector<int> &preorder) {
        // code here
        Node *root = Tree(preorder , inorder , 0 , preorder.size()-1 , 0);
        return root;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-04 15:52:52
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of a Tree Node
class Node {
public:
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  // To find position of element in inorder array:
  int find(vector<int>&inorder , int start , int end , int target)
  {
      for(int i = start ; i<=end ; i++)
      {
          if(inorder[i]==target)
          return i;
      }
      return -1;
  }
  Node *Tree(vector<int>&preorder , vector<int>&inorder , int instart , int inend , int index)
  {
      if(instart>inend)
      return NULL;
      Node *root = new Node(preorder[index]);
      int pos = find(inorder , instart ,inend , preorder[index]);
      root->left = Tree(preorder , inorder , instart , pos-1 , index+1);
      root->right = Tree(preorder , inorder , pos+1 , inend , index+pos-instart+1);
      return root;
  }
  
    Node *buildTree(vector<int> &inorder, vector<int> &preorder) {
        // code here
        Node *root = Tree(preorder , inorder , 0 , preorder.size()-1 , 0);
        return root;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-08-23 15:16:37
- **Status:** Correct
- **Marks:** 4

```cpp
/* Structure of a Tree Node
class Node {
public:
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  int find(vector<int>&inorder , int start , int end ,int target )
  {
      for(int i = start ; i<=end ; i++)
      {
          if(inorder[i]==target)
          return i;
      }
      return -1;
      
  }
  Node *createBT(vector<int>&inorder , vector<int>&preorder , int Instart , int Inend , int index)
  {
      if(Instart>Inend)
      return NULL;
      Node *root = new Node(preorder[index]);
      int pos = find(inorder , Instart , Inend , preorder[index]);
      root->left = createBT(inorder , preorder , Instart , pos-1 , index+1);
      root->right = createBT(inorder , preorder , pos+1 , Inend , index + (pos-Instart)+1);
      return root;
  }
    Node *buildTree(vector<int> &inorder, vector<int> &preorder) {
        // code here
        int Instart = 0,  Inend = inorder.size()-1 , index = 0;
        Node *root = createBT(inorder , preorder , Instart , Inend , index);
        return root;
    }
};
```

*Generated on: 10/4/2026, 3:53:22 PM*