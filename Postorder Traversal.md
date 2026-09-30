## 01. Postorder Traversal

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/postorder-traversal/1)

### Problem Description

**Task:** Given the root of a Binary Tree, return its Postorder Traversal.

> **Note:** A postorder traversal first visits the left child (including its entire subtree), then visits the right child (including its entire subtree), and finally visits the node itself.

#### Examples

##### Example 1

- **Input:**
```text
root = [19, 10, 8, 11, 13]
```
- **Output:**
```text
[11, 13, 10, 8, 19]Explanation: The postorder traversal of the given binary tree is [11, 13, 10, 8, 19].
```

##### Example 2

- **Input:**
```text
root = [11, 15, N, 7]
```
- **Output:**
```text
[7, 15, 11]Explanation: The postorder traversal of the given binary tree is [7, 15, 11].
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (5)

#### Solution 1 (C++)

- **Submitted:** 2026-09-30 18:29:00
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Binary Tree Node
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
    vector<int> postOrder(Node* root) {
      stack<Node*>st;
      vector<int>ans;
      st.push(root);
      while(!st.empty())
      {
          Node *temp = st.top();
          st.pop();
          ans.push_back(temp->data);
          if(temp->left)
          st.push(temp->left);
          if(temp->right)
          st.push(temp->right);
      }
      int start = 0 , end = ans.size()-1;
      while(start<=end)
      {
          swap(ans[start] , ans[end]);
          start++;
          end--;
      }
      return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-09-30 18:14:03
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Binary Tree Node
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
    vector<int> postOrder(Node* root) {
      stack<Node*>st;
      vector<int>ans;
      st.push(root);
      while(!st.empty())
      {
          Node *temp = st.top();
          st.pop();
          ans.push_back(temp->data);
          if(temp->left)
          st.push(temp->left);
          if(temp->right)
          st.push(temp->right);
      }
      int start = 0 , end = ans.size()-1;
      while(start<=end)
      {
          swap(ans[start] , ans[end]);
          start++;
          end--;
      }
      return ans;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-08-27 09:36:12
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Binary Tree Node
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
    vector<int> postOrder(Node* root) {
       vector<int>ans;
            while (root)
            {
               if(!root->right)
               {
                ans.push_back(root->data);
                root = root->left;
               }
               else
               {
                Node *curr = root->right;
                while (curr->left&&curr->left!=root)
                {
                   curr = curr->left;
                }
                if(curr->left==NULL)
                {
                    ans.push_back(root->data);
                    curr->left = root;
                    root = root->right;
                }
                else if(curr->left==root)
                {
                    curr->left = NULL;
                    root = root->left;
                }

               }
            }
            int start = 0 , end = ans.size()-1;
            while(start<=end)
            {
                swap(ans[start] , ans[end]);
                start++;
                end--;
            }
            return ans;
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-08-25 09:39:58
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Binary Tree Node
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
    vector<int> postOrder(Node* root) {
       vector<int>ans;
           while(root)
           {
           // Root ka left exist nhi krta hai:
           if(!root->right)
           {
               ans.push_back(root->data);
               root= root->left;
           }
           // Agar exist krta hai to :
           else
           {
             // Create a Pointer curr and move it right till curr->right Null nhi hota ya equal to root nhi ho jata
             Node *curr = root->right;
             while (curr->left&&curr->left!=root)
             {
               curr = curr->left;
             }
             // If curr->right ==NULL means it is not traversed:
             if(curr->left==NULL)
             {
               ans.push_back(root->data);
               curr->left = root;
               root = root->right;
             }
             // If curr->right==root which means link exist and if link exist which means it is traversed:
             else
             {
                curr->left= NULL;
                root = root->left;
             }
       }
       }
       int start = 0 , end = ans.size()-1;
       while (start<=end)
       {
           swap(ans[start],ans[end]);
           start++;
           end--;
       }
       return ans;
    }
};
```

#### Solution 5 (C++)

- **Submitted:** 2026-08-17 16:08:56
- **Status:** Correct
- **Marks:** 2

```cpp
/* Structure of Binary Tree Node
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
  void Postorder(Node *root , vector<int>&arr)
  {
      if(root==NULL)
      return;
      Postorder(root->left , arr);
      Postorder(root->right,arr);
      arr.push_back(root->data);
  }
    vector<int> postOrder(Node* root) {
        // code here
        vector<int>ans;
        Postorder(root , ans);
        return ans;
    }
};
```

*Generated on: 9/30/2026, 6:29:16 PM*