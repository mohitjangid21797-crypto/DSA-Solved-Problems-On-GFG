## 01. AVL Tree Deletion

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/avl-tree-deletion/1)

### Problem Description

**Task:** Given the root of an AVL tree and an integer key, delete the given key from the AVL tree and return the root of the modified tree.
After deleting the node, ensure that the tree continues to satisfy the properties of an AVL tree by performing the necessary rotations.

#### Examples

##### Example 1

- **Input:**
```text
root = [4, 2, 6, 1, 3, 5, 7], key = 4
```
- **Output:**
```text
Explanation: The node with value 4 has two children. To delete such a node, replace it with its inorder successor, which is 5 (the smallest node in the right subtree). Then, delete the original node 5 from the right subtree. After deletion, the tree remains balanced, so no rotations are required. The resulting AVL tree is shown above.
```

##### Example 2

- **Input:**
```text
root = [9, 5, 10, 2, 6, N, 12, 1, 3], key = 10Output:Explanation: Delete node 10 and replace it with its only child 12. After deletion, node 9 becomes unbalanced with a balance factor of +2. Since the balance factor of its left child 5 is +1 (i.e., non-negative), it is an LL case. Therefore, perform a right rotation on node 9 to restore the AVL property.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log n)
- **Expected Auxiliary Space Complexity:** O(log n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-16 17:26:03
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of AVL Tree Node
class Node {
  public:
    int data, height;
    Node *left, *right;

    Node(int x) {
        data = x;
        height = 1;
        left = right = nullptr;
    }
}; */

int Height(Node *root)
{
    if(root==NULL)
    return 0;
    return root->height;
}

int getBalance(Node *root)
{
    return Height(root->left) - Height(root->right);
}

Node *rightRotation(Node *root)
{
    Node *top = root;
    Node *middle = root->left;
    Node  *middleright = middle->right;
    middle->right = top;
    top->left = middleright;
    top->height = 1 + max(Height(top->left) ,Height(top->right));
    middle->height = 1 + max(Height(middle->left) , Height(middle->right));
    return middle;
}
Node *leftRotation(Node *root)
{
    Node *top = root;
    Node *middle = root->right;
    Node *middleleft = middle->left;
    middle->left = top;
    top->right = middleleft;
    top->height = 1 + max(Height(top->left) ,Height(top->right));
    middle->height = 1 + max(Height(middle->left) , Height(middle->right));
    return middle;
}
class Solution {
    public:
    Node* deleteNode(Node* root, int key) {
        // code here
        // if root does not exist
        if(root==NULL)
        return NULL;
        // if root exist
        else
        {
            // find that node:
            // if key<root->data then move left
            if(key<root->data)
                root->left = deleteNode(root->left , key);
            // if key>root->data then move right
            else if(key>root->data)
                root->right = deleteNode(root->right , key);
            // if key==root->data the start deleting the node
            else
            {
                // Now check type node which has to be deleted
                // 1. if node is leaf then delete directly
                if(root->left==NULL&&root->right==NULL)
                {
                    delete root;
                    return NULL;
                }
                // 2. if node is having excatly one child either left or right
                else if(root->left&&root->right==NULL)
                {
                    Node *temp = root->left;
                    delete root;
                    return temp;
                }
                else if(root->right&&root->left==NULL)
                {
                    Node *temp = root->right;
                    delete root;
                    return temp;
                }
                // 3 . if node have both child
                else
                {
                    // first find maximum element from left subtree or minimum element from right subtree
                    // then replace it with node which has to be deleted then delete it
                   Node *curr = root->left;
                   while(curr->right)
                   curr = curr->right;
                   root->data = curr->data;
                   root->left = deleteNode(root->left , curr->data);
                   
                }
            }
                    // after deleting the nodes update their height
                    root->height = 1 + max(Height(root->left) , Height(root->right));
                    // then check nodes are balance or not
                    int balance = getBalance(root);
                    // Now check unbalancing occurs left side or right side:
                    // if unbalancing occurs left side:
                    if(balance>1)
                    {
                        if(getBalance(root->left)<0)
                        {
                            // LR
                            root->left = leftRotation(root->left);
                            return rightRotation(root);
                        }
                        else
                        {
                            //LL
                            return rightRotation(root);
                        }
                    }
                    // unbalancing occurs on right side
                    else if(balance<-1)
                    {
                        if(getBalance(root->right)>0)
                        {
                            //RL
                            root->right = rightRotation(root->right);
                            return leftRotation(root);
                        }
                        else
                        {
                            // RR
                            return leftRotation(root);
                        }
                    }
                    else
                    return root;
            }
                
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-16 17:25:49
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of AVL Tree Node
class Node {
  public:
    int data, height;
    Node *left, *right;

    Node(int x) {
        data = x;
        height = 1;
        left = right = nullptr;
    }
}; */

int Height(Node *root)
{
    if(root==NULL)
    return 0;
    return root->height;
}

int getBalance(Node *root)
{
    return Height(root->left) - Height(root->right);
}

Node *rightRotation(Node *root)
{
    Node *top = root;
    Node *middle = root->left;
    Node  *middleright = middle->right;
    middle->right = top;
    top->left = middleright;
    top->height = 1 + max(Height(top->left) ,Height(top->right));
    middle->height = 1 + max(Height(middle->left) , Height(middle->right));
    return middle;
}
Node *leftRotation(Node *root)
{
    Node *top = root;
    Node *middle = root->right;
    Node *middleleft = middle->left;
    middle->left = top;
    top->right = middleleft;
    top->height = 1 + max(Height(top->left) ,Height(top->right));
    middle->height = 1 + max(Height(middle->left) , Height(middle->right));
    return middle;
}
class Solution {
    public:
    Node* deleteNode(Node* root, int key) {
        // code here
        // if root does not exist
        if(root==NULL)
        return NULL;
        // if root exist
        else
        {
            // find that node:
            // if key<root->data then move left
            if(key<root->data)
                root->left = deleteNode(root->left , key);
            // if key>root->data then move right
            else if(key>root->data)
                root->right = deleteNode(root->right , key);
            // if key==root->data the start deleting the node
            else
            {
                // Now check type node which has to be deleted
                // 1. if node is leaf then delete directly
                if(root->left==NULL&&root->right==NULL)
                {
                    delete root;
                    return NULL;
                }
                // 2. if node is having excatly one child either left or right
                else if(root->left&&root->right==NULL)
                {
                    Node *temp = root->left;
                    delete root;
                    return temp;
                }
                else if(root->right&&root->left==NULL)
                {
                    Node *temp = root->right;
                    delete root;
                    return temp;
                }
                // 3 . if node have both child
                else
                {
                    // first find maximum element from left subtree or minimum element from right subtree
                    // then replace it with node which has to be deleted then delete it
                   Node *curr = root->left;
                   while(curr->right)
                   curr = curr->right;
                   root->data = curr->data;
                   root->left = deleteNode(root->left , curr->data);
                   
                }
            }
                    // after deleting the nodes update their height
                    root->height = 1 + max(Height(root->left) , Height(root->right));
                    // then check nodes are balance or not
                    int balance = getBalance(root);
                    // Now check unbalancing occurs left side or right side:
                    // if unbalancing occurs left side:
                    if(balance>1)
                    {
                        if(getBalance(root->left)<0)
                        {
                            // LR
                            root->left = leftRotation(root->left);
                            return rightRotation(root);
                        }
                        else
                        {
                            //LL
                            return rightRotation(root);
                        }
                    }
                    // unbalancing occurs on right side
                    else if(balance<-1)
                    {
                        if(getBalance(root->right)>0)
                        {
                            //RL
                            root->right = rightRotation(root->right);
                            return leftRotation(root);
                        }
                        else
                        {
                            // RR
                            return leftRotation(root);
                        }
                    }
                    else
                    return root;
            }
                
    }
};
```

*Generated on: 10/16/2026, 5:26:25 PM*