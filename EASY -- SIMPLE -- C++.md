## 01. EASY || SIMPLE || C++

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/burning-tree/1)

### Problem Description

**Task:** Given the root of a binary tree and a target node, find the minimum time required to burn the entire tree if the target node is set on fire. In one second, the fire spreads from a node to its left child, right child, and parent.Note: The tree contains unique values.Examples : Input: root = [1, 2, 3, 4, 5, 6, 7], target = 2

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** Initially 2 is set to fire at 0 sec At 1 sec: Nodes 4, 5, 1 catches fire.At 2 sec: Node 3 catches fire.At 3 sec: Nodes 6, 7 catches fire.It takes 3s to burn the complete tree.Input: root = [1, 2, 3, 4, 5, N, 7, 8, N, N, 10], target = 10Output: 5Explanation: Initially 10 is set to fire at 0 sec At 1 sec: Node 5 catches fire. At 2 sec: Node 2 catches fire. At 3 sec: Nodes 1 and 4 catches fire. At 4 sec: Node 3 and 8 catches fire. At 5 sec: Node 7 catches fire. It takes 5s to burn the complete tree.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (3)

#### Solution 1 (C++)

- **Submitted:** 2026-10-06 12:28:12
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of binary tree Node
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
  // Calculate the height of target node :
  int Height(Node *root)
  {
      if(root==NULL)
      return 0;
      return 1 + max(Height(root->left) , Height(root->right));
  }
  int burnTree(Node *root, int target , int &timer , int &height)
  {
      // 1. if root does not exist
      if(root==NULL)
      return 0;
          if(root->data==target)
          {
              height = Height(root)-1;
              return -1;
          }
          int left = burnTree(root->left , target , timer , height);
          int right = burnTree(root->right , target , timer , height);
          if(left<0)
          {
              timer = max(timer , abs(left)+right);
              return left-1;
          }
          if(right<0)
          {
              timer = max(timer , abs(right) + left);
              return right-1;
          }
          return 1 + max(left , right);
  }
    int minTime(Node* root, int target) {
        // code here
        int timer = 0, height = 0;
        burnTree(root , target , timer , height);
        return max(timer , height);
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-06 12:26:51
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of binary tree Node
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
  // Calculate the height of target node :
  int Height(Node *root)
  {
      if(root==NULL)
      return 0;
      return 1 + max(Height(root->left) , Height(root->right));
  }
  int burnTree(Node *root, int target , int &timer , int &height)
  {
      // 1. if root does not exist
      if(root==NULL)
      return 0;
          if(root->data==target)
          {
              height = Height(root)-1;
              return -1;
          }
          int left = burnTree(root->left , target , timer , height);
          int right = burnTree(root->right , target , timer , height);
          if(left<0)
          {
              timer = max(timer , abs(left)+right);
              return left-1;
          }
          if(right<0)
          {
              timer = max(timer , abs(right) + left);
              return right-1;
          }
          return 1 + max(left , right);
  }
    int minTime(Node* root, int target) {
        // code here
        int timer = 0, height = 0;
        burnTree(root , target , timer , height);
        return max(timer , height);
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-06 12:26:31
- **Status:** Correct
- **Marks:** 8

```cpp
/* Structure of binary tree Node
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
  // Calculate the height of target node :
  int Height(Node *root)
  {
      if(root==NULL)
      return 0;
      return 1 + max(Height(root->left) , Height(root->right));
  }
  int burnTree(Node *root, int target , int &timer , int &height)
  {
      // 1. if root does not exist
      if(root==NULL)
      return 0;
          if(root->data==target)
          {
              height = Height(root)-1;
              return -1;
          }
          int left = burnTree(root->left , target , timer , height);
          int right = burnTree(root->right , target , timer , height);
          if(left<0)
          {
              timer = max(timer , abs(left)+right);
              return left-1;
          }
          if(right<0)
          {
              timer = max(timer , abs(right) + left);
              return right-1;
          }
          return 1 + max(left , right);
  }
    int minTime(Node* root, int target) {
        // code here
        int timer = 0, height = 0;
        burnTree(root , target , timer , height);
        return max(timer , height);
    }
};
```

*Generated on: 10/6/2026, 12:28:33 PM*