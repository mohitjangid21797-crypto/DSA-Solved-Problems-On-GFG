## 01. Sum of k Smallest in BST

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

### Accepted Solutions (5)

#### Solution 1 (C++)

- **Submitted:** 2026-10-09 10:21:48
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
  void kSmallestSum(Node *root , int &k , int &sum)
  {
      if(root==NULL)
      return ;
      kSmallestSum(root->left , k , sum);
      if(k==0)
      return;
      sum+=root->data;
      k--;
      kSmallestSum(root->right , k , sum);
  }
  
    int sum(Node* root, int k) {
        int sum = 0;
        kSmallestSum(root , k , sum);
        return sum;
        // code here
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-09 10:21:35
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
  void kSmallestSum(Node *root , int &k , int &sum)
  {
      if(root==NULL)
      return ;
      kSmallestSum(root->left , k , sum);
      if(k==0)
      return;
      sum+=root->data;
      k--;
      kSmallestSum(root->right , k , sum);
  }
  
    int sum(Node* root, int k) {
        int sum = 0;
        kSmallestSum(root , k , sum);
        return sum;
        // code here
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-08 16:40:07
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
  void ksmallest(Node *root , int &sum , int &k)
  {
      if(root==NULL)
      return ;
      ksmallest(root->left , sum , k);
      if(k==0)
      return;
      sum+=root->data;
      k--;
      ksmallest(root->right , sum  , k);
     
  }
    int sum(Node* root, int k) {
        // code here
        int sum = 0;
        ksmallest(root , sum , k);
        return sum;
        
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-10-08 16:39:49
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
  void ksmallest(Node *root , int &sum , int &k)
  {
      if(root==NULL)
      return ;
      ksmallest(root->left , sum , k);
      if(k==0)
      return;
      sum+=root->data;
      k--;
      ksmallest(root->right , sum  , k);
     
  }
    int sum(Node* root, int k) {
        // code here
        int sum = 0;
        ksmallest(root , sum , k);
        return sum;
        
    }
};
```

#### Solution 5 (C++)

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

*Generated on: 10/9/2026, 10:22:18 AM*