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

- **Submitted:** 2026-10-05 15:58:44
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
            if(root->left==NULL)
        {
            ans.push_back(root->data);
            root = root->right;
        }
        else
        {
            Node *curr = root->left;
            while(curr->right!=NULL&&curr->right!=root)
            {
                curr = curr->right;
            }
            if(curr->right==NULL)
            {
                curr->right = root;
                ans.push_back(root->data);
                root = root->left;
            }
            else if(curr->right==root)
            {
                curr->right = NULL;
                root = root->right;
            }
        }
        }
        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-05 15:58:25
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
            if(root->left==NULL)
        {
            ans.push_back(root->data);
            root = root->right;
        }
        else
        {
            Node *curr = root->left;
            while(curr->right!=NULL&&curr->right!=root)
            {
                curr = curr->right;
            }
            if(curr->right==NULL)
            {
                curr->right = root;
                ans.push_back(root->data);
                root = root->left;
            }
            else if(curr->right==root)
            {
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

- **Submitted:** 2026-09-30 18:27:29
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

#### Solution 4 (C++)

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

#### Solution 5 (C++)

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

*Generated on: 10/5/2026, 3:59:37 PM*