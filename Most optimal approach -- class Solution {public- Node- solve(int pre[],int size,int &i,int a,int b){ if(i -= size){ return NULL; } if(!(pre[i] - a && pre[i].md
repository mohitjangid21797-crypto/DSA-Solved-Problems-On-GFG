## 01. Most optimal approach :- class Solution {public: Node* solve(int pre[],int size,int &i,int a,int b){ if(i >= size){ return NULL; } if(!(pre[i] > a && pre[i] < b)){ return NULL; } Node* newNode = (Node*)malloc( sizeof( Node ) ); newNode->data = pre[i++]; if(newNode->data > a && newNode->data < b){ newNode->left = solve(pre,size,i,a,newNode->data); newNode->right = solve(pre,size,i,newNode->data,b); return newNode; } } Node* Bst(int pre[], int size) { int i = 0; return solve(pre,size,i,INT_MIN,INT_MAX); }};

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/preorder-to-postorder4423/1)

### Problem Description

**Task:** Given an array pre[] representing the preorder traversal of a Binary Search Tree. Construct the corresponding BST and return its root.

> **Note:** All node values are distinct.

#### Examples

##### Example 1

- **Input:**
```text
pre[] = [40, 30, 35, 80, 100]
```
- **Output:**
```text
[40, 30, 80, N, 35, N, 100]
```
- **Explanation:** The corresponding BST is:

##### Example 2

- **Input:**
```text
pre[] = [10, 5, 1, 7, 40, 50]
```
- **Output:**
```text
[10, 5, 40, 1, 7, N, 50]Explanation: The corresponding BST is:
```

#### Constraints

- **1.** `1 ≤ n ≤ 10³, n is the size of pre1 ≤ pre[i] ≤ 10⁴`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(h)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-09 18:26:15
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of a Tree Node
class Node {
  public:
    int data;
    Node *left, *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
  Node *BST(vector<int>&arr ,int &index , int lower , int upper)
  {
      if(index==arr.size()||arr[index]<lower||arr[index]>upper)
      return NULL;
      Node *temp = new Node(arr[index++]);
      temp->left = BST(arr , index , lower , temp->data);
      temp->right = BST(arr , index , temp->data , upper);
      return temp;
  }
    Node* preToBST(vector<int>& pre) {
        int index = 0;
        int lower = INT_MIN;
        int upper = INT_MAX;
        Node *root = BST(pre , index , lower , upper);
        return root;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-09 18:26:03
- **Status:** Correct
- **Marks:** 4

```cpp
/* Structure of a Tree Node
class Node {
  public:
    int data;
    Node *left, *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
  Node *BST(vector<int>&arr ,int &index , int lower , int upper)
  {
      if(index==arr.size()||arr[index]<lower||arr[index]>upper)
      return NULL;
      Node *temp = new Node(arr[index++]);
      temp->left = BST(arr , index , lower , temp->data);
      temp->right = BST(arr , index , temp->data , upper);
      return temp;
  }
    Node* preToBST(vector<int>& pre) {
        int index = 0;
        int lower = INT_MIN;
        int upper = INT_MAX;
        Node *root = BST(pre , index , lower , upper);
        return root;
    }
};
```

*Generated on: 10/9/2026, 6:26:34 PM*