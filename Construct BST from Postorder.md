## 01. Construct BST from Postorder

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/construct-bst-from-post-order/1)

### Problem Description

**Task:** Given postorder traversal of a Binary Search Tree, you need to construct a BST from postorder traversal. The output will be inorder traversal of the constructed BST.

#### Examples

##### Example 1

- **Input:**
```text
post[] = [1, 7, 5, 50, 40, 10]
```
- **Output:**
```text
[1, 5, 7, 10, 40, 50] The BST for the given post order traversal is: Thus the inorder traversal of BST is: 1 5 7 10 40 50.
```

##### Example 2

- **Input:**
```text
post[] = [2, 1, 3, 5]
```
- **Output:**
```text
[1, 2, 3, 5] The BST for the given post order traversal is:
```

#### Constraints

- **1.** `1 ≤ n ≤ 10⁵ , n is the number of nodes in BST`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (4)

#### Solution 1 (C++)

- **Submitted:** 2026-10-09 18:58:52
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of tree node
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
  Node *BST(vector<int>&arr , int &index , int lower , int upper)
  {
      if(index==arr.size()||arr[index]<lower||arr[index]>upper)
      return NULL;
      Node *temp = new Node(arr[index++]);
      temp->right = BST(arr , index , temp->data  , upper);
      temp->left = BST(arr , index , lower , temp->data);
      return temp;
  }
  
    Node* constructTree(vector<int>& post) {
        // code here
        int index=0;
        int lower = INT_MIN;
        int upper = INT_MAX;
        int start = 0 , end = post.size()-1;
        while(start<=end)
        {
            swap(post[start] , post[end]);
            start++;
            end--;
        }
        Node *root = BST(post , index , lower , upper);
        return root;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-09 18:58:38
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of tree node
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
  Node *BST(vector<int>&arr , int &index , int lower , int upper)
  {
      if(index==arr.size()||arr[index]<lower||arr[index]>upper)
      return NULL;
      Node *temp = new Node(arr[index++]);
      temp->right = BST(arr , index , temp->data  , upper);
      temp->left = BST(arr , index , lower , temp->data);
      return temp;
  }
  
    Node* constructTree(vector<int>& post) {
        // code here
        int index=0;
        int lower = INT_MIN;
        int upper = INT_MAX;
        int start = 0 , end = post.size()-1;
        while(start<=end)
        {
            swap(post[start] , post[end]);
            start++;
            end--;
        }
        Node *root = BST(post , index , lower , upper);
        return root;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-09 15:19:13
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of tree node
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
  Node *BST(vector<int>&postorder , int &index , int lower , int upper)
  {
      if(index<0||lower>postorder[index]||upper<postorder[index])
      {
          return NULL;
      }
      Node *temp = new Node(postorder[index--]);
      temp->right = BST(postorder , index , temp->data , upper);
      temp->left = BST(postorder , index , lower , temp->data);
      return temp;
  }
    Node* constructTree(vector<int>& post) {
        // code here
        int index = post.size()-1;
        int lower = INT_MIN;
        int upper = INT_MAX;
        Node *root = BST(post , index , lower , upper);
        return root;
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-10-09 15:19:02
- **Status:** Correct
- **Marks:** 2

```cpp
/* Structure of tree node
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
  Node *BST(vector<int>&postorder , int &index , int lower , int upper)
  {
      if(index<0||lower>postorder[index]||upper<postorder[index])
      {
          return NULL;
      }
      Node *temp = new Node(postorder[index--]);
      temp->right = BST(postorder , index , temp->data , upper);
      temp->left = BST(postorder , index , lower , temp->data);
      return temp;
  }
    Node* constructTree(vector<int>& post) {
        // code here
        int index = post.size()-1;
        int lower = INT_MIN;
        int upper = INT_MAX;
        Node *root = BST(post , index , lower , upper);
        return root;
    }
};
```

*Generated on: 10/9/2026, 6:59:09 PM*