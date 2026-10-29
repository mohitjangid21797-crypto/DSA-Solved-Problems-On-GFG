## 01. The most ever easiest C++ solution || Just 6 lines

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/flatten-binary-tree-to-linked-list/1)

### Problem Description

**Task:** Given the root of a binary tree, flatten the tree into a Linked list:
The linked list should use the same Node class where the right child pointer points to the next node in the list and the left child pointer is always null.
The linked list nodes should be in the same order as a preorder traversal of the binary tree.

#### Examples

##### Example 1

- **Input:**
```text
root[] = [1, 2, 5, 3, 4, 6]
```
- **Output:**
```text
[1, 2, 3, 4, 5, 6] Explanation: After flattening, the tree looks like: 1 \ 2 \ 3 \ 4 \ 5 \ 6Here, left of each node points to NULL and right contains the next node in preorder.The inorder traversal of this flattened tree is 1 2 3 4 5 6.
```

##### Example 2

- **Input:**
```text
root[] = [1, 3, 4, 2, 5]
```
- **Output:**
```text
[1, 3, 4, 2, 5]
```
- **Explanation:** After flattening, the tree looks like: 1 \ 3 \ 4 \ 2 \ 5 Here, left of each node points to NULL and right contains the next node in preorder.The inorder traversal of this flattened tree is 1 3 4 2 5.

#### Constraints

- **1.** `1 <= number of nodes in binary tree <= 10⁵`
- **2.** `1 <= data of nodes <= 105`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (4)

#### Solution 1 (C++)

- **Submitted:** 2026-10-05 18:29:08
- **Status:** Correct
- **Marks:** 0

```cpp
/* Binary Tree Node Structure
class Node {
public:
    int data;
    Node* left;
    Node* right;

    Node(int data) {
        this->data = data;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
    void flatten(Node* root) {
        // code here
        while(root)
        {
            if(!root->left)
        {
            root = root->right;
        }
        else
        {
            Node *curr = root->left;
            while(curr->right)
            {
                curr = curr->right;
            }
            curr->right = root->right;
            root->right = root->left;
            root->left = NULL;
            root = root->right;
        }
        }
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-05 18:28:52
- **Status:** Correct
- **Marks:** 0

```cpp
/* Binary Tree Node Structure
class Node {
public:
    int data;
    Node* left;
    Node* right;

    Node(int data) {
        this->data = data;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
    void flatten(Node* root) {
        // code here
        while(root)
        {
            if(!root->left)
        {
            root = root->right;
        }
        else
        {
            Node *curr = root->left;
            while(curr->right)
            {
                curr = curr->right;
            }
            curr->right = root->right;
            root->right = root->left;
            root->left = NULL;
            root = root->right;
        }
        }
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-08-27 10:03:04
- **Status:** Correct
- **Marks:** 0

```cpp
/* Binary Tree Node Structure
class Node {
public:
    int key;
    Node* left;
    Node* right;

    Node(int key) {
        this->key = key;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
    void flatten(Node* root) {
      while(root)
      {
          if(!root->left)
          {
              root = root->right;
          }
          else
          {
              Node *curr = root->left;
              while(curr->right)
              curr = curr->right;
              curr->right = root->right;
              root->right = root->left;
              root->left = NULL;
              root = root->right;
          }
      }
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-08-25 10:12:27
- **Status:** Correct
- **Marks:** 4

```cpp
/* Binary Tree Node Structure
class Node {
public:
    int key;
    Node* left;
    Node* right;

    Node(int key) {
        this->key = key;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
    void flatten(Node* root) {
        // code here
        while (root)
        {
            if(!root->left)
            {
                root = root->right;
            }
            else
            {
                Node *curr = root->left;
                while (curr->right)
                {
                    curr = curr->right;
                }
                curr->right = root->right;
                root->right = root->left;
                root->left = NULL;
                root = root->right;
            }
        }
    }
};
```

*Generated on: 10/5/2026, 6:29:31 PM*