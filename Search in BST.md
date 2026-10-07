## 01. Search in BST

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/search-a-node-in-bst/1)

### Problem Description

**Task:** Given a Binary Search Tree and a node value key, return true if the node with value key is present in the BST; otherwise, return false.

#### Examples

##### Example 1

- **Input:**
```text
root = [6, 2, 8, N, N, 7, 9], key = 8 Output: true
```
- **Explanation:** 8 is present in the BST as right child of root.

##### Example 2

- **Input:**
```text
root = [16, 12, 18, 10, N, 17, 19], key = 14 Output: falseExplanation: 14 is not present in the BST
```

#### Constraints

- **1.** `1 ≤ number of nodes ≤ 3*10⁴¹ ≤ node- > data, key ≤ 10⁹`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(h)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-07 12:02:10
- **Status:** Correct
- **Marks:** 0

```cpp
/* Definition for Node
class Node {
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
    bool search(Node* root, int key) {
        // code here
        if(root==NULL)
        return 0;
        if(root->data==key)
        return 1;
        if(root->data>key)
        {
            return search(root->left , key);
        }
        else
        {
            return search(root->right , key);
        }
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-07 12:01:59
- **Status:** Correct
- **Marks:** 2

```cpp
/* Definition for Node
class Node {
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
    bool search(Node* root, int key) {
        // code here
        if(root==NULL)
        return 0;
        if(root->data==key)
        return 1;
        if(root->data>key)
        {
            return search(root->left , key);
        }
        else
        {
            return search(root->right , key);
        }
    }
};
```

*Generated on: 10/7/2026, 12:02:47 PM*