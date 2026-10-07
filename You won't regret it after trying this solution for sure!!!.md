## 01. You won't regret it after trying this solution for sure!!!

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/delete-a-node-from-bst/1)

### Problem Description

**Task:** Given a binary search tree and a node value x. Delete the node with the given value x from the tree. If no node with value x exists, then do not make any change.
Return the root of the tree after deleting the node with value x.

> **Note:** You may return any valid BST after deleting the specified node. The driver code will print true if the resulting tree is a valid BST after deletion, and false otherwise.

#### Examples

##### Example 1

- **Input:**
```text
root = [2, 1, 3], x = 12
```
- **Output:**
```text
true
```
- **Explanation:** In the given input there is no node with value 12, so the tree will remain same.

##### Example 2

- **Input:**
```text
root = [1, N, 2, N, 8, 5, 11, 4, 7, 9, 12], x = 11
```
- **Output:**
```text
trueExplanation: In the given input, one of the possible tree after deleting 11 will be
```

##### Example 3

- **Input:**
```text
root = [2, 1, 3], x = 3Output: [2, 1]Explanation: In the given input, only possible tree after deleting 3 will be
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(Height of the BST)
- **Expected Auxiliary Space Complexity:** O(Height of the BST)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-07 17:59:09
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of a Binary Search Tree node
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
}; */

class Solution {
  public:
    Node* delNode(Node* root, int x) {
        // code here
        // If root does not exist : 
        if(root==NULL)
        {
            return NULL;
        }
        // If root does not exist :
        else
        {
            // x is less than root->data
            if(x<root->data)
            {
                root->left = delNode(root->left , x);
                return root;
            }
            // x is greater than root->data
            else if(x>root->data)
            {
                root->right = delNode(root->right , x);
                return root;
            }
            // x is equal to root->data
            else
            {
                // 1. x is leaf node :
                if(!root->left&&!root->right)
                {
                    delete root;
                    return NULL;
                }
                // 2. x is node having exactly one child either left child or left child:
                else if(!root->right)
                {
                    Node *temp = root->left;
                    delete root;
                    return temp;
                }
                else if(!root->left)
                {
                    Node *temp = root->right;
                    delete root;
                    return temp;
                }
                // 3 . x is having both left and right child:
                else
                {
                    Node *parent = root;
                    Node *child = root->left;
                    // finding maximum element in left subtree:
                    while(child->right)
                    {
                        parent = child;
                        child = child->right;
                    }
                    if(parent!=root)
                    {
                        parent->right = child->left;
                        child->left = root->left;
                        child->right = root->right;
                        delete root;
                        return child;
                    }
                    else
                    {
                       child->right = root->right;
                       delete root;
                       return child;
                    }
                }
            }
        }
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-07 17:58:52
- **Status:** Correct
- **Marks:** 4

```cpp
/* Structure of a Binary Search Tree node
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
}; */

class Solution {
  public:
    Node* delNode(Node* root, int x) {
        // code here
        // If root does not exist : 
        if(root==NULL)
        {
            return NULL;
        }
        // If root does not exist :
        else
        {
            // x is less than root->data
            if(x<root->data)
            {
                root->left = delNode(root->left , x);
                return root;
            }
            // x is greater than root->data
            else if(x>root->data)
            {
                root->right = delNode(root->right , x);
                return root;
            }
            // x is equal to root->data
            else
            {
                // 1. x is leaf node :
                if(!root->left&&!root->right)
                {
                    delete root;
                    return NULL;
                }
                // 2. x is node having exactly one child either left child or left child:
                else if(!root->right)
                {
                    Node *temp = root->left;
                    delete root;
                    return temp;
                }
                else if(!root->left)
                {
                    Node *temp = root->right;
                    delete root;
                    return temp;
                }
                // 3 . x is having both left and right child:
                else
                {
                    Node *parent = root;
                    Node *child = root->left;
                    // finding maximum element in left subtree:
                    while(child->right)
                    {
                        parent = child;
                        child = child->right;
                    }
                    if(parent!=root)
                    {
                        parent->right = child->left;
                        child->left = root->left;
                        child->right = root->right;
                        delete root;
                        return child;
                    }
                    else
                    {
                       child->right = root->right;
                       delete root;
                       return child;
                    }
                }
            }
        }
    }
};
```

*Generated on: 10/7/2026, 5:59:30 PM*