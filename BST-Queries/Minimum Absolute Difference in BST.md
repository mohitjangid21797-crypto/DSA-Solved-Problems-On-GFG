## 01. Minimum Absolute Difference in BST

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-absolute-difference-in-bst-1665139652/1)

### Problem Description

**Task:** Given the root of a Binary Search Tree (BST) containing n (n > 1) nodes, find the minimum absolute difference between the values of any two different nodes in the tree.Return the minimum absolute difference.Examples:Input: root[] = [50, 30, 70, 20, N, 60, 80]Output: 10Explanation: There are no two nodes whose absolute difference is smaller than 10.Input: root[] = [60, 30, 90, 10]Output: 20Explanation: There are no two nodes whose absolute difference is smaller than 20.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(h)

### Accepted Solutions (4)

#### Solution 1 (C++)

- **Submitted:** 2026-10-08 16:09:27
- **Status:** Correct
- **Marks:** 0

```cpp
/* Binary Tree Node Structure
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
 void minDist(Node *root , int &prev , int&ans)
 {
     if(root==NULL)
     return;
     minDist(root->left , prev , ans);
     if(prev!=INT_MIN)
     ans = min(ans , root->data-prev);
     prev = root->data;
     minDist(root->right , prev , ans);
 }
    int absDiff(Node *root) {
       int prev = INT_MIN;
       int ans = INT_MAX;
       minDist(root , prev , ans);
       return ans;
      
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-08 16:09:04
- **Status:** Correct
- **Marks:** 0

```cpp
/* Binary Tree Node Structure
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
 void minDist(Node *root , int &prev , int&ans)
 {
     if(root==NULL)
     return;
     minDist(root->left , prev , ans);
     if(prev!=INT_MIN)
     ans = min(ans , root->data-prev);
     prev = root->data;
     minDist(root->right , prev , ans);
 }
    int absDiff(Node *root) {
       int prev = INT_MIN;
       int ans = INT_MAX;
       minDist(root , prev , ans);
       return ans;
      
        
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-08 15:40:44
- **Status:** Correct
- **Marks:** 0

```cpp
/* Binary Tree Node Structure
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
  void Inorder(Node *root , vector<int>&arr)
  {
      if(root==NULL)
      return;
      Inorder(root->left , arr);
      arr.push_back(root->data);
      Inorder(root->right , arr);
  }
    int absDiff(Node *root) {
       
       vector<int>ans;
       Inorder(root , ans);
       int minimum = INT_MAX;
       for(int i = 0 ; i<ans.size()-1 ; i++)
       {
           minimum = min(minimum , ans[i+1]-ans[i]);
       }
       return minimum;
        
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-10-08 15:40:31
- **Status:** Correct
- **Marks:** 4

```cpp
/* Binary Tree Node Structure
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
  void Inorder(Node *root , vector<int>&arr)
  {
      if(root==NULL)
      return;
      Inorder(root->left , arr);
      arr.push_back(root->data);
      Inorder(root->right , arr);
  }
    int absDiff(Node *root) {
       
       vector<int>ans;
       Inorder(root , ans);
       int minimum = INT_MAX;
       for(int i = 0 ; i<ans.size()-1 ; i++)
       {
           minimum = min(minimum , ans[i+1]-ans[i]);
       }
       return minimum;
        
    }
};
```

*Generated on: 10/8/2026, 4:09:49 PM*