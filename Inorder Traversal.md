## 01. Inorder Traversal

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/inorder-traversal/1)

### Problem Description

**Task:** Given a root of a Binary Tree, your task is to return its Inorder Traversal.

> **Note:** An inorder traversal first visits the left child (including its entire subtree), then visits the node, and finally visits the right child (including its entire subtree).

#### Examples

##### Example 1

- **Input:**
```text
root = [1, 2, 3, 4, 5]
```
- **Output:**
```text
[4, 2, 5, 1, 3]Explanation: The inorder traversal of the given binary tree is [4, 2, 5, 1, 3].
```

##### Example 2

- **Input:**
```text
root = [8, 1, 5, N, 7, 10, 6, N, 10, 6]
```
- **Output:**
```text
[1, 7, 10, 8, 6, 10, 5, 6]Explanation: The inorder traversal of the given binary tree is [1, 7, 10, 8, 6, 10, 5, 6].
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (5)

#### Solution 1 (C++)

- **Submitted:** 2026-09-30 19:27:58
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
       vector<int> inOrder(Node* root) {
          vector<int>ans;
          stack<Node*>st1;
          stack<bool> visited;
          st1.push(root);
          visited.push(0);
          while(!st1.empty())
          {
              Node *temp = st1.top();
              st1.pop();
              bool flag = visited.top();
              visited.pop();
              if(flag==0)
              {
                  if(temp->right)
                  {
                      st1.push(temp->right);
                      visited.push(0);
                  }
                  st1.push(temp);
                  visited.push(1);
                  if(temp->left)
                  {
                      st1.push(temp->left);
                      visited.push(0);
                  }
              }
              else
              {
                  ans.push_back(temp->data);
              }
          }
          return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-09-30 18:24:42
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
       vector<int> inOrder(Node* root) {
           vector<int>ans;
                while (root)
                {
                    // root ka left agar exist nhi krta hai to :
                    if(!root->left)
                    {
                        ans.push_back(root->data);
                        root = root->right;
                    }
                    else
                    {
                        Node *curr = root->left;
                        // Pointer ko move krayga jab tak curr->right NULL ya root ka equal nhi ho jata:
                        while (curr->right&&curr->right!=root)
                        {
                            curr= curr->right;
                        }
                        // agar curr->right==NULL ho jata hai means that leftsubtree is not traversed:
                        if(curr->right==NULL)
                        {
                           curr->right = root;
                           root = root->left;
                        }
                        // agar curr->right==root means  leftsubtree is traversed:
                        else if(curr->right==root)
                        {
                            ans.push_back(root->data);
                            curr->right = NULL;
                            root = root->right;
                        } 
                    }
                }
                return ans;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-09-30 18:24:13
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
       vector<int> inOrder(Node* root) {
           vector<int>ans;
                while (root)
                {
                    // root ka left agar exist nhi krta hai to :
                    if(!root->left)
                    {
                        ans.push_back(root->data);
                        root = root->right;
                    }
                    else
                    {
                        Node *curr = root->left;
                        // Pointer ko move krayga jab tak curr->right NULL ya root ka equal nhi ho jata:
                        while (curr->right&&curr->right!=root)
                        {
                            curr= curr->right;
                        }
                        // agar curr->right==NULL ho jata hai means that leftsubtree is not traversed:
                        if(curr->right==NULL)
                        {
                           curr->right = root;
                           root = root->left;
                        }
                        // agar curr->right==root means  leftsubtree is traversed:
                        else if(curr->right==root)
                        {
                            ans.push_back(root->data);
                            curr->right = NULL;
                            root = root->right;
                        } 
                    }
                }
                return ans;
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-09-28 21:55:25
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
       vector<int> inOrder(Node* root) {
           vector<int>ans;
                while (root)
                {
                    // root ka left agar exist nhi krta hai to :
                    if(!root->left)
                    {
                        ans.push_back(root->data);
                        root = root->right;
                    }
                    else
                    {
                        Node *curr = root->left;
                        // Pointer ko move krayga jab tak curr->right NULL ya root ka equal nhi ho jata:
                        while (curr->right&&curr->right!=root)
                        {
                            curr= curr->right;
                        }
                        // agar curr->right==NULL ho jata hai means that leftsubtree is not traversed:
                        if(curr->right==NULL)
                        {
                           curr->right = root;
                           root = root->left;
                        }
                        // agar curr->right==root means  leftsubtree is traversed:
                        else if(curr->right==root)
                        {
                            ans.push_back(root->data);
                            curr->right = NULL;
                            root = root->right;
                        } 
                    }
                }
                return ans;
    }
};
```

#### Solution 5 (C++)

- **Submitted:** 2026-09-28 21:42:44
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
       vector<int> inOrder(Node* root) {
           vector<int>ans;
                while (root)
                {
                    // root ka left agar exist nhi krta hai to :
                    if(!root->left)
                    {
                        ans.push_back(root->data);
                        root = root->right;
                    }
                    else
                    {
                        Node *curr = root->left;
                        // Pointer ko move krayga jab tak curr->right NULL ya root ka equal nhi ho jata:
                        while (curr->right&&curr->right!=root)
                        {
                            curr= curr->right;
                        }
                        // agar curr->right==NULL ho jata hai means that leftsubtree is not traversed:
                        if(curr->right==NULL)
                        {
                           curr->right = root;
                           root = root->left;
                        }
                        // agar curr->right==root means  leftsubtree is traversed:
                        else if(curr->right==root)
                        {
                            ans.push_back(root->data);
                            curr->right = NULL;
                            root = root->right;
                        } 
                    }
                }
                return ans;
    }
};
```

*Generated on: 9/30/2026, 7:28:37 PM*