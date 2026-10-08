## 01. Sum of k smallest in BST

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sum-of-k-smallest-elements-in-bst3029/1)

### Problem Description

**Task:** Given a Binary Search Tree, find sum of k smallest nodes in it. You may assume that k is always smaller than or equal to size of the tree.Examples:Input: k = 3

#### Examples

##### Example 1

- **Output:**
```text
22
```
- **Explanation:** The sum of two smallest elements is 4+5 = 9

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log k)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-08 16:30:31
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of a Tree Node
class Node {
    int data;
    Node* right;
    Node* left;
    Node(int x){
        data = x;
        right = nullptr;
        left = nullptr;
    }
}; */

class Solution {
  public:
  void ksmallest(Node *root , vector<int>&arr)
  {
      if(root==NULL)
      return;
      ksmallest(root->left , arr);
      arr.push_back(root->data);
      ksmallest(root->right , arr);
  }
    int sum(Node* root, int k) {
        // code here
        vector<int>ans;
        ksmallest(root , ans);
        int sum = 0;
        for(int i = 0 ; i<=k-1 ; i++)
        {
            sum+=ans[i];
        }
        return sum;
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-08 16:30:21
- **Status:** Correct
- **Marks:** 2

```cpp
/* Structure of a Tree Node
class Node {
    int data;
    Node* right;
    Node* left;
    Node(int x){
        data = x;
        right = nullptr;
        left = nullptr;
    }
}; */

class Solution {
  public:
  void ksmallest(Node *root , vector<int>&arr)
  {
      if(root==NULL)
      return;
      ksmallest(root->left , arr);
      arr.push_back(root->data);
      ksmallest(root->right , arr);
  }
    int sum(Node* root, int k) {
        // code here
        vector<int>ans;
        ksmallest(root , ans);
        int sum = 0;
        for(int i = 0 ; i<=k-1 ; i++)
        {
            sum+=ans[i];
        }
        return sum;
        
    }
};
```

*Generated on: 10/8/2026, 4:30:53 PM*