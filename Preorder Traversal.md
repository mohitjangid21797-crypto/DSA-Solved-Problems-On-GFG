## 01. Preorder Traversal

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/preorder-traversal/1)

### Problem Description

**Task:** Given the root of a binary tree, return its preorder traversal. A preorder traversal first visits the node, then visits the left child (including its entire subtree), and finally visits the right child (including its entire subtree).

#### Examples

##### Example 1

- **Input:**
```text
root = [1, 4, N, 4, 2]
```
- **Output:**
```text
[1, 4, 4, 2]Explanation: The preorder traversal of the given binary tree is [1, 4, 4, 2]
```

##### Example 2

- **Input:**
```text
root = [6, 3, 2, N, 1, 2, N]
```
- **Output:**
```text
[6, 3, 1, 2, 2] Explanation: The preorder traversal of the given binary tree is [6, 3, 1, 2, 2]
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (5)

#### Solution 1 (C++)

- **Submitted:** 2026-09-30 18:06:49
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Tree Node
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
};*/

class Solution {
  public:
    vector<int> preOrder(Node* root) {
       vector<int>ans;
       stack<Node*>st;
       st.push(root);
       while(!st.empty())
       {
           Node *temp = st.top();
           st.pop();
           ans.push_back(temp->data);
           if(temp->right)
           st.push(temp->right);
           if(temp->left)
           st.push(temp->left);
       }
       return ans;
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-09-28 21:56:58
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Tree Node
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
};*/

class Solution {
  public:
    vector<int> preOrder(Node* root) {
       vector<int>ans;
            while (root)
            {
                if(!root->left)
                {
                    ans.push_back(root->data);
                    root = root->right;
                }
                else
                {
                    Node *curr = root->left;
                    while(curr->right&&curr->right!=root)
                    {
                        curr = curr->right;
                    }
                    if(curr->right==NULL)
                    {
                        ans.push_back(root->data);
                        curr->right = root;
                        root = root->left;
                    }
                    else if(curr->right==root)
                    {
                        curr->right = NULL;
                        root = root->right;
                    }
                }
            }
            return ans;  // code here
        
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-09-28 21:54:07
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Tree Node
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
};*/

class Solution {
  public:
    vector<int> preOrder(Node* root) {
       vector<int>ans;
            while (root)
            {
                if(!root->left)
                {
                    ans.push_back(root->data);
                    root = root->right;
                }
                else
                {
                    Node *curr = root->left;
                    while(curr->right&&curr->right!=root)
                    {
                        curr = curr->right;
                    }
                    if(curr->right==NULL)
                    {
                        ans.push_back(root->data);
                        curr->right = root;
                        root = root->left;
                    }
                    else if(curr->right==root)
                    {
                        curr->right = NULL;
                        root = root->right;
                    }
                }
            }
            return ans;  // code here
        
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-08-27 09:34:06
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Tree Node
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
};*/

class Solution {
  public:
    vector<int> preOrder(Node* root) {
       vector<int>ans;
            while (root)
            {
                if(!root->left)
                {
                    ans.push_back(root->data);
                    root = root->right;
                }
                else
                {
                    Node *curr = root->left;
                    while(curr->right&&curr->right!=root)
                    {
                        curr = curr->right;
                    }
                    if(curr->right==NULL)
                    {
                        ans.push_back(root->data);
                        curr->right = root;
                        root = root->left;
                    }
                    else if(curr->right==root)
                    {
                        curr->right = NULL;
                        root = root->right;
                    }
                }
            }
            return ans;  // code here
        
    }
};
```

#### Solution 5 (C++)

- **Submitted:** 2026-08-25 09:23:26
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Tree Node
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
};*/

class Solution {
  public:
    vector<int> preOrder(Node* root) {
        // code here
        vector<int>ans;
            while(root)
            {
            // Root ka left exist nhi krta hai:
            if(!root->left)
            {
                ans.push_back(root->data);
                root= root->right;
            }
            // Agar exist krta hai to :
            else
            {
              // Create a Pointer curr and move it right till curr->right Null nhi hota ya equal to root nhi ho jata
              Node *curr = root->left;
              while (curr->right&&curr->right!=root)
              {
                curr = curr->right;
              }
              // If curr->right ==NULL means it is not traversed:
              if(curr->right==NULL)
              {
                ans.push_back(root->data);
                curr->right = root;
                root = root->left;
              }
              // If curr->right==root which means link exist and if link exist which means it is traversed:
              else
              {
                 curr->right= NULL;
                 root = root->right;
              }

            }
        }
            return ans;
    }
};
```

*Generated on: 9/30/2026, 6:27:31 PM*