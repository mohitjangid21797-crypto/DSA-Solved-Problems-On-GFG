## 01. Actually It's Easy -> Java Most Optimal Solution

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/fixed-two-nodes-of-a-bst/1)

### Problem Description

**Task:** Given the root of a Binary Search Tree (BST), where exactly two nodes have been swapped by mistake, restore the BST by swapping the values of the misplaced nodes. Return the root of the corrected BST.

> **Note:** It is guaranteed that exactly two nodes have been swapped, and restoring their values will make the tree a valid BST. The structure of the tree must remain unchanged.

#### Examples

##### Example 1

- **Input:**
```text
root = [10, 5, 8, 2, 20]
```
- **Output:**
```text
[10, 5, 20, 2, 8] Explanation: The nodes 20 and 8 were swapped.
```

##### Example 2

- **Input:**
```text
root = [5, 10, 20, 2, 8]
```
- **Output:**
```text
[10, 5, 20, 2, 8]
```
- **Explanation:** The nodes 10 and 5 were swapped.

#### Constraints

- **1.** `2 ≤ Number of nodes ≤ 10⁵¹ ≤ root[i] ≤ 10⁷`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(h)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-13 17:31:48
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
  void correctBSTFixingNodes(Node *root)
  {
      Node *first = NULL , *second = NULL;
      Node *last = NULL , *present = NULL;
      Node *curr  = NULL;
      while(root)
      {
          // root ka left exist nhi karta :
          if(root->left==NULL)
          {
              last = present;
              present = root;
              // if lats exist and check problem occur here
              if(last&&last->data>present->data)
              {
                  // if first time problem occurs means first is null;
                  if(first==NULL)
                  first = last;
                  second = present;
              }
              root = root->right;
          }
          // root ka left exist
          else
          {
              curr = root->left;
              while(curr->right&&curr->right!=root)
              {
                  curr = curr->right;
              }
              // check if link exist or not :
              // if link exist means left part is already traversed
              if(curr->right==root)
              {
                  curr->right = NULL;
                  last = present;
                  present = root;
                  if(last&&last->data>present->data)
                  {
                      // check problem occur firsttime or second time
                      // first is equal to null then problem occur first time else second time
                      if(first==NULL)
                      first = last;
                      second = present;
                  }
                  root = root->right;
              }
              // else link does not exist means left part is not traversed
              else if(curr->right==NULL)
              {
                  curr->right = root;
                  root= root->left;
              }
              
              
          }
      }
      int num = first->data;
      first->data = second->data;
      second->data = num;
  }
    Node* correctBST(Node* root) {
        // code here
        correctBSTFixingNodes(root);
        return root;
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-13 17:31:30
- **Status:** Correct
- **Marks:** 8

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
  void correctBSTFixingNodes(Node *root)
  {
      Node *first = NULL , *second = NULL;
      Node *last = NULL , *present = NULL;
      Node *curr  = NULL;
      while(root)
      {
          // root ka left exist nhi karta :
          if(root->left==NULL)
          {
              last = present;
              present = root;
              // if lats exist and check problem occur here
              if(last&&last->data>present->data)
              {
                  // if first time problem occurs means first is null;
                  if(first==NULL)
                  first = last;
                  second = present;
              }
              root = root->right;
          }
          // root ka left exist
          else
          {
              curr = root->left;
              while(curr->right&&curr->right!=root)
              {
                  curr = curr->right;
              }
              // check if link exist or not :
              // if link exist means left part is already traversed
              if(curr->right==root)
              {
                  curr->right = NULL;
                  last = present;
                  present = root;
                  if(last&&last->data>present->data)
                  {
                      // check problem occur firsttime or second time
                      // first is equal to null then problem occur first time else second time
                      if(first==NULL)
                      first = last;
                      second = present;
                  }
                  root = root->right;
              }
              // else link does not exist means left part is not traversed
              else if(curr->right==NULL)
              {
                  curr->right = root;
                  root= root->left;
              }
              
              
          }
      }
      int num = first->data;
      first->data = second->data;
      second->data = num;
  }
    Node* correctBST(Node* root) {
        // code here
        correctBSTFixingNodes(root);
        return root;
        
    }
};
```

*Generated on: 10/13/2026, 5:32:11 PM*