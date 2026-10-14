## 01. Largest BST Subtree

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/largest-bst/1)

### Problem Description

**Task:** Given the root of a binary tree, find the size of the largest subtree that is also a Binary Search Tree (BST). A subtree is considered a BST if, for every node in the subtree:All nodes in its left subtree have values less than the node's value.All nodes in its right subtree have values greater than the node's value.The subtree contains no duplicate values.Return the number of nodes in the largest BST subtree.Note: The size of a subtree is the total number of nodes it contains.Examples :Input: root = [5, 2, 4, 1, 3]Output: 3Explanation:The following sub-tree is a BST of size 3Input: root = [6, 7, 3, N, 2, 2, 4]Output: 3Explanation: The following sub-tree is a BST of size 3:

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(h)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-14 21:23:23
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of a Binary Search Tree node
class Node {
public:
    int data;
    Node *left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};*/

class Box
{
    public:
    bool BST;
    int size;
    int max , min;
    Box(int data)
    {
        BST = 1;
        size = 1;
        min = data;
        max = data;
    }
};
class Solution {
  public:
  Box *largestBST(Node *root , int &totalsize)
  {
      // root does not exist:
      if(root==NULL)
      return 0;
      // root exist:
      //1. Node is leaf node
      if(root->left==NULL&&root->right==NULL)
      {
          Box *head = new Box(root->data);
          totalsize = max(totalsize , 1);
          return head;
      }
      // 2. Node having both left and right child
      else if(root->left&&root->right)
      {
          Box *lefthead = largestBST(root->left , totalsize);
          Box *righthead = largestBST(root->right , totalsize);
          // If satisfy BST conditions:
          if(lefthead->BST&&righthead->BST&&root->data>lefthead->max&&root->data<righthead->min)
          {
              Box *head = new Box(root->data);
              head->size = lefthead->size + righthead->size + 1;
              head->max = righthead->max;
              head->min = lefthead->min;
              totalsize = max(totalsize , head->size);
              return head;
          }
          // Not satisfy BST conditions:
          lefthead->BST = 0;
          return lefthead;
          
      }
      
      // 3. Node having only left child exist
      else if(root->left&&root->right==NULL)
      {
          Box *head = largestBST(root->left , totalsize);
          // satisfy BST conditions:
          if(head->BST&&root->data>head->max)
          {
              head->size+=1;
              head->max = root->data;
              totalsize = max(totalsize , head->size);
              return head;
          }
          // not satisfy BST conditions:
          else
          {
              head->BST = 0;
              return head;
          }
      }
      // 4 . Node having only right child exist
      else
      {
          Box *head = largestBST(root->right , totalsize);
          // satisfy BST conditions
          if(head->BST&&root->data<head->min)
          {
              head->size+=1;
              head->min = root->data;
              totalsize = max(totalsize , head->size);
              return head;
          }
          // not satisfy BST conditions:
          else
          {
              head->BST = 0;
              return head;
          }
          
      }
  }
    int largestBst(Node *root) {
        // code here
        int totalsize = 0;
        largestBST(root , totalsize);
        return totalsize;
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-14 21:23:02
- **Status:** Correct
- **Marks:** 4

```cpp
/* Structure of a Binary Search Tree node
class Node {
public:
    int data;
    Node *left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};*/

class Box
{
    public:
    bool BST;
    int size;
    int max , min;
    Box(int data)
    {
        BST = 1;
        size = 1;
        min = data;
        max = data;
    }
};
class Solution {
  public:
  Box *largestBST(Node *root , int &totalsize)
  {
      // root does not exist:
      if(root==NULL)
      return 0;
      // root exist:
      //1. Node is leaf node
      if(root->left==NULL&&root->right==NULL)
      {
          Box *head = new Box(root->data);
          totalsize = max(totalsize , 1);
          return head;
      }
      // 2. Node having both left and right child
      else if(root->left&&root->right)
      {
          Box *lefthead = largestBST(root->left , totalsize);
          Box *righthead = largestBST(root->right , totalsize);
          // If satisfy BST conditions:
          if(lefthead->BST&&righthead->BST&&root->data>lefthead->max&&root->data<righthead->min)
          {
              Box *head = new Box(root->data);
              head->size = lefthead->size + righthead->size + 1;
              head->max = righthead->max;
              head->min = lefthead->min;
              totalsize = max(totalsize , head->size);
              return head;
          }
          // Not satisfy BST conditions:
          lefthead->BST = 0;
          return lefthead;
          
      }
      
      // 3. Node having only left child exist
      else if(root->left&&root->right==NULL)
      {
          Box *head = largestBST(root->left , totalsize);
          // satisfy BST conditions:
          if(head->BST&&root->data>head->max)
          {
              head->size+=1;
              head->max = root->data;
              totalsize = max(totalsize , head->size);
              return head;
          }
          // not satisfy BST conditions:
          else
          {
              head->BST = 0;
              return head;
          }
      }
      // 4 . Node having only right child exist
      else
      {
          Box *head = largestBST(root->right , totalsize);
          // satisfy BST conditions
          if(head->BST&&root->data<head->min)
          {
              head->size+=1;
              head->min = root->data;
              totalsize = max(totalsize , head->size);
              return head;
          }
          // not satisfy BST conditions:
          else
          {
              head->BST = 0;
              return head;
          }
          
      }
  }
    int largestBst(Node *root) {
        // code here
        int totalsize = 0;
        largestBST(root , totalsize);
        return totalsize;
        
    }
};
```

*Generated on: 10/14/2026, 9:23:46 PM*