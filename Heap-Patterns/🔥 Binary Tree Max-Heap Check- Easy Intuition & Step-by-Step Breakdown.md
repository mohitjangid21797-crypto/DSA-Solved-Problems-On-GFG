## 01. 🔥 Binary Tree Max-Heap Check: Easy Intuition & Step-by-Step Breakdown

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/is-binary-tree-heap/1)

### Problem Description

**Task:** You are given the root of a binary tree, and the task is to determine whether it satisfies the properties of a max-heap.A binary tree is considered a max-heap if it satisfies the following conditions:Completeness: Every level of the tree, except possibly the last, is completely filled, and all nodes are as far left as possible.Max-Heap Property: The value of each node is greater than or equal to the values of its children.Examples:Input: root = [97, 46, 37, 12, 3, 7, 31, 6, 9]

#### Examples

##### Example 1

- **Output:**
```text
true
```
- **Explanation:** The tree is complete and satisfies the max-heap property.

##### Example 2

- **Input:**
```text
root = [97, 46, 37, 12, 3, 7, 31, N, N, 2, 4] Output: falseExplanation: The tree is not complete and does not follow the Max-Heap Property, hence it is not a max-heap.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-27 16:31:36
- **Status:** Correct
- **Marks:** 0

```cpp
/*
class Node {
   public:
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
  int Count(Node *root)
  {
      if(root==NULL)
      return 0;
      return 1 + (Count(root->left) + Count(root->right));
  }
  bool checkCBT(Node *root , int index , int total_nodes)
  {
      if(root==NULL)
      return 1;
      if(index>=total_nodes)
      return 0;
      return checkCBT(root->left , 2*index+1 , total_nodes)&& checkCBT(root->right , 2*index+2 , total_nodes);
  }
  bool MaxHeap(Node *root)
  {
      // check if root->left exist :
      if(root->left)
      {
          // parent<leftchild --> return 0;
          if(root->data<root->left->data)
          return 0;
          // if parent>=left child the move left and from left side if parent<child -->then return 0
          if(!MaxHeap(root->left))
          return 0;
          // if from left side it gives 1 then go to right side
      }
      // check if root->right exist or not
      if(root->right)
      {
          if(root->data<root->right->data)
          return 0;
          return MaxHeap(root->right);
      }
      return 1;
  }
    bool isHeap(Node* root) {
        // code here
        // count the number of nodes 
        int count = Count(root);
        // check CBT or not:
        bool ans = checkCBT(root , 0 , count);
        // if does not follows CBT it will not maxHeap
        if(ans==0)
        return 0;
        // Now if it follows the CBT then check parent should be greater than its child
        return MaxHeap(root);
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-27 16:31:27
- **Status:** Correct
- **Marks:** 4

```cpp
/*
class Node {
   public:
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
  int Count(Node *root)
  {
      if(root==NULL)
      return 0;
      return 1 + (Count(root->left) + Count(root->right));
  }
  bool checkCBT(Node *root , int index , int total_nodes)
  {
      if(root==NULL)
      return 1;
      if(index>=total_nodes)
      return 0;
      return checkCBT(root->left , 2*index+1 , total_nodes)&& checkCBT(root->right , 2*index+2 , total_nodes);
  }
  bool MaxHeap(Node *root)
  {
      // check if root->left exist :
      if(root->left)
      {
          // parent<leftchild --> return 0;
          if(root->data<root->left->data)
          return 0;
          // if parent>=left child the move left and from left side if parent<child -->then return 0
          if(!MaxHeap(root->left))
          return 0;
          // if from left side it gives 1 then go to right side
      }
      // check if root->right exist or not
      if(root->right)
      {
          if(root->data<root->right->data)
          return 0;
          return MaxHeap(root->right);
      }
      return 1;
  }
    bool isHeap(Node* root) {
        // code here
        // count the number of nodes 
        int count = Count(root);
        // check CBT or not:
        bool ans = checkCBT(root , 0 , count);
        // if does not follows CBT it will not maxHeap
        if(ans==0)
        return 0;
        // Now if it follows the CBT then check parent should be greater than its child
        return MaxHeap(root);
    }
};
```

*Generated on: 10/27/2026, 4:31:57 PM*