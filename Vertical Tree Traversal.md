## 01. Vertical Tree Traversal

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/print-a-binary-tree-in-vertical-order/1)

### Problem Description

**Task:** Given the root of a Binary Tree, find the vertical traversal of the tree starting from the leftmost level to the rightmost level.

> **Note:** If there are multiple nodes passing through a vertical line, then they should be printed as they appear in level order traversal of the tree.

#### Examples

##### Example 1

- **Input:**
```text
root = [1, 2, 3, 4, 5, 6, 7, N, N, N, 8, N, 9, N, 10, 11, N]
```
- **Output:**
```text
[[4], [2], [1, 5, 6, 11], [3, 8, 9], [7], [10]]
```
- **Explanation:** The below image shows the horizontal distances used to print vertical traversal starting from the leftmost level to the rightmost level.

##### Example 2

- **Input:**
```text
root = [1, 2, 3, 4, 5, N, 6]
```
- **Output:**
```text
[[4], [2], [1, 5], [3], [6]]Explanation: From left to right the vertical order will be [[4], [2], [1, 5], [3], [6]]
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (4)

#### Solution 1 (C++)

- **Submitted:** 2026-10-04 19:01:21
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
  void position(Node *root , int &l , int &r , int pos)
  {
      if(root==NULL)
      return;
      l = min(l , pos);
      r = max(r , pos);
      position(root->left , l , r , pos-1);
      position(root->right , l , r , pos+1);
  }
  
    vector<vector<int>> verticalOrder(Node *root) {
        // code here
        int l = 0 , r = 0 , pos = 0;
        position(root , l , r , pos);
        vector<vector<int>>positive(r+1);
        vector<vector<int>>negative(abs(l)+1);
        vector<vector<int>>ans;
        queue<Node *>q;
        queue<int>index;
        pos = 0;
        q.push(root);
        index.push(pos);
        while(!q.empty())
        {
            Node *temp = q.front();
            q.pop();
            int pos = index.front();
            index.pop();
            if(pos>=0)
            {
                positive[pos].push_back(temp->data);
            }
            else if(pos<0)
            {
                negative[abs(pos)].push_back(temp->data);
            }
            if(temp->left)
            {
                q.push(temp->left);
                index.push(pos-1);
            }
            if(temp->right)
            {
                q.push(temp->right);
                index.push(pos+1);
            }
        }
        for(int i = negative.size()-1 ; i>=1 ; i--)
        ans.push_back(negative[i]);
        for(int i = 0 ; i<positive.size() ; i++)
        ans.push_back(positive[i]);
        return ans;
        
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-04 19:01:06
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
  void position(Node *root , int &l , int &r , int pos)
  {
      if(root==NULL)
      return;
      l = min(l , pos);
      r = max(r , pos);
      position(root->left , l , r , pos-1);
      position(root->right , l , r , pos+1);
  }
  
    vector<vector<int>> verticalOrder(Node *root) {
        // code here
        int l = 0 , r = 0 , pos = 0;
        position(root , l , r , pos);
        vector<vector<int>>positive(r+1);
        vector<vector<int>>negative(abs(l)+1);
        vector<vector<int>>ans;
        queue<Node *>q;
        queue<int>index;
        pos = 0;
        q.push(root);
        index.push(pos);
        while(!q.empty())
        {
            Node *temp = q.front();
            q.pop();
            int pos = index.front();
            index.pop();
            if(pos>=0)
            {
                positive[pos].push_back(temp->data);
            }
            else if(pos<0)
            {
                negative[abs(pos)].push_back(temp->data);
            }
            if(temp->left)
            {
                q.push(temp->left);
                index.push(pos-1);
            }
            if(temp->right)
            {
                q.push(temp->right);
                index.push(pos+1);
            }
        }
        for(int i = negative.size()-1 ; i>=1 ; i--)
        ans.push_back(negative[i]);
        for(int i = 0 ; i<positive.size() ; i++)
        ans.push_back(positive[i]);
        return ans;
        
        
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-08-24 11:48:58
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
  // Find leftmost and rightmost position :
  void find(Node *root , int &l , int &r , int pos)
  {
      if(root==NULL)
      return ;
      l = min(l , pos);
      r = max(r , pos);
      find(root->left , l,r,pos-1);
      find(root->right , l,r,pos+1);
  }

  // Create two 2d array +ve and -ve position , return ans;
  vector<vector<int>>verticalTraversal(Node *root)
  {
      int l = 0 , r = 0;
      find(root , l,r,0);
      vector<vector<int>>positive(r+1);
      vector<vector<int>>negative(abs(l)+1);
      // Level order traversal :
      queue<Node*>q;
      queue<int>index;
      q.push(root);
      index.push(0);
      while (!q.empty())
      {
          Node *temp = q.front();
          q.pop();
          int pos = index.front();
          index.pop();
          if(pos>=0)
          {
              positive[pos].push_back(temp->data);
          }
          else
          {
              negative[abs(pos)].push_back(temp->data);
          }
          if(temp->left)
          {
              q.push(temp->left);
              index.push(pos-1);
          }
          if(temp->right)
          {
              q.push(temp->right);
              index.push(pos+1);

          }
      }
      vector<vector<int>>ans;
      for(int i = negative.size()-1 ; i>0 ; i--)
      {
          ans.push_back(negative[i]);
      }
      for(int i = 0 ; i<positive.size();i++)
      {
          ans.push_back(positive[i]);
      }
      return ans;
  }
 
    vector<vector<int>> verticalOrder(Node *root) {
        return verticalTraversal(root);
        
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-08-24 08:47:18
- **Status:** Correct
- **Marks:** 4

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
  void find(Node *root , int &l , int &r , int pos)
  {
      if(root==NULL)
      return;
      l = min(l,pos);
      r = max(r , pos);
      find(root->left , l,r,pos-1);
      find(root->right , l,r,pos+1);
  }
 
    vector<vector<int>> verticalOrder(Node *root) {
        // code here
        int l = 0 , r = 0;
            find(root , l , r , 0);
            vector<vector<int>>positive(r+1);
            vector<vector<int>>negative(abs(l)+1);
            queue<Node*>q;
            queue<int>index;
            q.push(root);
            index.push(0);
            while (!q.empty())
            {
                Node *temp = q.front();
                q.pop();
                int pos = index.front();
                index.pop();
                if(pos>=0)
                {
                    positive[pos].push_back(temp->data);
                }
                else
                {
                    negative[abs(pos)].push_back(temp->data);
                }
                if(temp->left)
                {
                    q.push(temp->left);
                    index.push((pos-1));
                }
                if(temp->right)
                {
                    q.push(temp->right);
                    index.push(pos+1);
                }
            }
            vector<vector<int>>ans;
            for (int i = negative.size()-1; i>0; i--)
            {
              ans.push_back(negative[i]);

            }
            for (int i = 0; i<=positive.size()-1; i++)
            {
              ans.push_back(positive[i]);

            }
            return ans;
            
        
    }
};
```

*Generated on: 10/4/2026, 7:01:42 PM*