## 01. Lowest Common Ancestor in a BST

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/lowest-common-ancestor-in-a-bst/1)

### Problem Description

**Task:** Given a Binary Search Tree (BST) with unique node values and two nodes n1 and n2 (n1 ! = n2), find their Lowest Common Ancestor (LCA).
The Lowest Common Ancestor (LCA) of two nodes is defined as the deepest node in the tree that has both n1 and n2 as descendants, where a node can be a descendant of itself.

#### Examples

##### Example 1

- **Input:**
```text
root = [5, 4, 6, 3, N, N, 7, N, N, N, 8], n1- > data = 7, n2- > data = 8 Output: 7Explanation: 7 is the lowest node that has both 7 and 8 as descendants.
```

##### Example 2

- **Input:**
```text
root = [20, 8, 22, 4, 12, N, N, N, N, 10, 14], n1- > data = 8, n2- > data = 14 Output: 8Explanation: 8 is the lowest node that has both 8 and 14 as descendants.
```

##### Example 3

- **Input:**
```text
root = [2, 1, 3], n1- > data = 1, n2- > data = 3
```
- **Output:**
```text
2Explanation: 2 is the lowest node that has both 1 and 3 as descendants.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(h)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-12 16:26:00
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
};
*/

class Solution {
  public:
    Node* findLCA(Node* root, Node* n1, Node* n2) {
        // code here
        if(root==NULL)
        return NULL;
        if(root->data>n1->data&&root->data>n2->data)
        return findLCA(root->left , n1, n2);
        else if(root->data<n1->data&&root->data<n2->data)
        return findLCA(root->right , n1 , n2);
        else
        return root;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-12 16:25:52
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
};
*/

class Solution {
  public:
    Node* findLCA(Node* root, Node* n1, Node* n2) {
        // code here
        if(root==NULL)
        return NULL;
        if(root->data>n1->data&&root->data>n2->data)
        return findLCA(root->left , n1, n2);
        else if(root->data<n1->data&&root->data<n2->data)
        return findLCA(root->right , n1 , n2);
        else
        return root;
    }
};
```

*Generated on: 10/12/2026, 4:26:21 PM*