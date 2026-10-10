## 01. Easy-to-understand recursive solution🧐🧐🧐

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/array-to-bst4443/1)

### Problem Description

**Task:** Given a sorted array arr[]. Convert it into a Height Balanced Binary Search Tree (BST) and return the root of the BST.Height-balanced BST means a binary tree in which the depth of the left subtree and the right subtree of every node never differ by more than 1.Note: You can return any BST, the driver code will check the BST, and print true if it is a Height-balanced BST else print false.Examples :Input: arr[] = [10, 20, 30]

#### Examples

##### Example 1

- **Output:**
```text
true
```
- **Explanation:** One of the possible Height Balanced BST will be [9, 1, 23, N, 5, 14, 27]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-10 14:24:18
- **Status:** Correct
- **Marks:** 0

```cpp
/*
class Node {
  public:
    int data;
    Node* left;
    Node* right;

    Node(int val) {
        data = val;
        left = nullptr;
        right = nullptr;
    }
};
*/

class Solution {
  public:
  Node *BST(vector<int>&arr , int start , int end)
  {
      if(start>end)
      return NULL;
      int mid = start + (end-start)/2;
      Node *temp = new Node(arr[mid]);
      temp->left = BST(arr , start , mid-1);
      temp->right = BST(arr , mid+1 , end);
      return temp;
  }
 
  Node* sortedArrayToBST(vector<int>& arr) 
  {
      Node *root = BST(arr , 0 , arr.size()-1);
      return root;
      
  }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-10 14:24:08
- **Status:** Correct
- **Marks:** 4

```cpp
/*
class Node {
  public:
    int data;
    Node* left;
    Node* right;

    Node(int val) {
        data = val;
        left = nullptr;
        right = nullptr;
    }
};
*/

class Solution {
  public:
  Node *BST(vector<int>&arr , int start , int end)
  {
      if(start>end)
      return NULL;
      int mid = start + (end-start)/2;
      Node *temp = new Node(arr[mid]);
      temp->left = BST(arr , start , mid-1);
      temp->right = BST(arr , mid+1 , end);
      return temp;
  }
 
  Node* sortedArrayToBST(vector<int>& arr) 
  {
      Node *root = BST(arr , 0 , arr.size()-1);
      return root;
      
  }
};
```

*Generated on: 10/10/2026, 2:24:39 PM*