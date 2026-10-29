## 01. Diagonal Tree Traversal

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/diagonal-traversal-of-binary-tree/1)

### Problem Description

**Task:** Given a Binary Tree, return the diagonal traversal of the binary tree.Consider imaginary lines passing between the nodes of the binary tree. All nodes lying on the same diagonal belong to the same diagonal group.Return a single list containing all the nodes in diagonal order, starting from the topmost diagonal and moving to the next diagonals.If nodes from the left and right subtrees belong to the same diagonal, the nodes from the left subtree must be included before the nodes from the right subtree.Examples :Input : root = [8, 3, 10, 1, 6, N, 14, N, N, 4, 7, 13]Output : [8, 10, 14, 3, 6, 7, 13, 1, 4]

#### Examples

##### Example 1

- **Explanation:** Diagonal Traversal of binary tree : 8 10 14 3 6 7 13 1 4Input: root = [1, 2, N, 3, N]Output: [1, 2, 3]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (4)

#### Solution 1 (C++)

- **Submitted:** 2026-10-05 11:17:40
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of binary tree node
class Node {
public:
    int data;
    Node* left;
    Node* right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};*/

class Solution {
  public:
  void find(Node *root , int &l , int pos)
  {
      if(root==NULL)
      return ;
      l = max(l,pos);
      find(root->left ,l , pos+1);
      find(root->right  , l , pos);
  }
  void fillvalues(Node *root , vector<vector<int>>&arr , int l)
  {
      if(root==NULL)
      return ;
      arr[l].push_back(root->data);
      fillvalues(root->left , arr , l+1);
      fillvalues(root->right , arr , l);
  }
    vector<int> diagonal(Node *root) {
        // code here
        int l = 0 ;
        find(root , l , 0);
        vector<vector<int>>arr(l+1);
        l = 0;
        fillvalues(root , arr , l);
        vector<int>ans;
        for(int i = 0 ; i<arr.size() ; i++)
        {
            for(int j = 0 ; j<arr[i].size() ; j++)
            ans.push_back(arr[i][j]);
        }
        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-05 11:16:52
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of binary tree node
class Node {
public:
    int data;
    Node* left;
    Node* right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};*/

class Solution {
  public:
  void find(Node *root , int &l , int pos)
  {
      if(root==NULL)
      return ;
      l = max(l,pos);
      find(root->left ,l , pos+1);
      find(root->right  , l , pos);
  }
  void fillvalues(Node *root , vector<vector<int>>&arr , int l)
  {
      if(root==NULL)
      return ;
      arr[l].push_back(root->data);
      fillvalues(root->left , arr , l+1);
      fillvalues(root->right , arr , l);
  }
    vector<int> diagonal(Node *root) {
        // code here
        int l = 0 ;
        find(root , l , 0);
        vector<vector<int>>arr(l+1);
        l = 0;
        fillvalues(root , arr , l);
        vector<int>ans;
        for(int i = 0 ; i<arr.size() ; i++)
        {
            for(int j = 0 ; j<arr[i].size() ; j++)
            ans.push_back(arr[i][j]);
        }
        return ans;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-08-24 12:13:10
- **Status:** Correct
- **Marks:** 0

```cpp
/* A binary tree node
struct Node
{
    int data;
    Node* left, * right;
}; */

class Solution {
  public:
  void find(Node *root , int &l , int pos)
  {
      if(root==NULL)
      return ;
      l = max(l,pos);
      find(root->left,l,pos+1);
      find(root->right,l,pos);
  }
  void fillelement(Node *root , vector<vector<int>>&arr , int pos)
  {
      if(root==NULL)
      return ;
      arr[pos].push_back(root->data);

      fillelement(root->left,arr,pos+1);
      fillelement(root->right,arr,pos);
  }
  vector<vector<int>>diagonalTraversal(Node *root)
  {
      int l = 0;
      find(root , l , 0);
      vector<vector<int>>ans(l+1);
      fillelement(root , ans ,0);
      return ans;
  }
  vector<int> diagonal(Node *root) {
      vector<vector<int>>ans = diagonalTraversal(root);
      vector<int>ans1;
      for(int i = 0 ; i<ans.size() ; i++)
      {
          for(int j = 0 ; j<ans[i].size() ; j++)
          ans1.push_back(ans[i][j]);
      }
      return ans1;
     
        
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-08-24 09:42:02
- **Status:** Correct
- **Marks:** 4

```cpp
/* A binary tree node
struct Node
{
    int data;
    Node* left, * right;
}; */

class Solution {
  public:
  void find(Node *root , int &l , int pos)
  {
      if(root==NULL)
      return ;
      l = max(l , pos);
      find(root->left , l , pos+1);
      find(root->right , l , pos);
  }
  void fill(Node *root , vector<vector<int>>&arr, int l)
  {
      if(root==NULL)
      return;
      arr[l].push_back(root->data);
      fill(root->left , arr , l+1);
      fill(root->right , arr  , l);
  }
    vector<int> diagonal(Node *root) {
        // code here
        int l = 0; 
        find(root , l , 0);
        vector<vector<int>>diagonalelement(l+1);
        fill(root , diagonalelement , 0);
        vector<int>ans;
        for(int i = 0 ; i<diagonalelement.size() ; i++)
        {
            for(int j = 0 ; j<diagonalelement[i].size() ;j++)
            ans.push_back(diagonalelement[i][j]);
        }
        return ans;
        
    }
};
```

*Generated on: 10/5/2026, 11:17:59 AM*