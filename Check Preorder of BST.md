## 01. Check Preorder of BST

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/preorder-traversal-and-bst4006/1)

### Problem Description

**Task:** Given an array arr[ ] consisting of distinct integers, check if the given array can represent preorder traversal of a BST.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [2, 4, 3]
```
- **Output:**
```text
true Explaination: Given arr[] can represent preorder traversal of following BST:
```

##### Example 2

- **Input:**
```text
arr[] = [2, 4, 1]
```
- **Output:**
```text
false Explaination: Given arr[] cannot represent preorder traversal of a BST.
```

#### Constraints

- **1.** `1 ≤ arr.size() ≤ 10⁵⁰ ≤ arr[i] ≤ 10⁵`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (5)

#### Solution 1 (C++)

- **Submitted:** 2026-10-09 19:37:43
- **Status:** Correct
- **Marks:** 0

```cpp
class Node
{
    public:
    int data;
    Node *left , *right;
    Node(int x)
    {
        data = x;
        left = NULL;
        right = NULL;
    }
};
class Solution {
  public:
    bool canRepresentBST(vector<int> &ques) {
       stack<int>lower , upper;
           lower.push(INT_MIN);
           upper.push(INT_MAX);
           for(int i = 0 ; i<ques.size() ; i++)
           {
               if(ques[i]<lower.top())
               {
                 return 0;
               }
               while (ques[i]>upper.top())
               {
                  lower.pop();
                  upper.pop();
               }
               int left = lower.top();
               int right = upper.top();
               lower.pop();
               upper.pop();
               // right side :
               lower.push(ques[i]);
               upper.push(right);
               // left side:
               lower.push(left);
               upper.push(ques[i]);
           }
           return 1;
       
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-09 19:37:36
- **Status:** Correct
- **Marks:** 0

```cpp
class Node
{
    public:
    int data;
    Node *left , *right;
    Node(int x)
    {
        data = x;
        left = NULL;
        right = NULL;
    }
};
class Solution {
  public:
    bool canRepresentBST(vector<int> &ques) {
       stack<int>lower , upper;
           lower.push(INT_MIN);
           upper.push(INT_MAX);
           for(int i = 0 ; i<ques.size() ; i++)
           {
               if(ques[i]<lower.top())
               {
                 return 0;
               }
               while (ques[i]>upper.top())
               {
                  lower.pop();
                  upper.pop();
               }
               int left = lower.top();
               int right = upper.top();
               lower.pop();
               upper.pop();
               // right side :
               lower.push(ques[i]);
               upper.push(right);
               // left side:
               lower.push(left);
               upper.push(ques[i]);
           }
           return 1;
       
        
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-09 19:20:18
- **Status:** Correct
- **Marks:** 0

```cpp
class Node
{
    public:
    int data;
    Node *left , *right;
    Node(int x)
    {
        data = x;
        left = NULL;
        right = NULL;
    }
};
class Solution {
  public:
 Node *BST(vector<int>&arr , int &index , int lower , int upper)
 {
     if(index==arr.size()||arr[index]<lower || arr[index]>upper)
     return NULL;
     Node *temp = new Node(arr[index++]);
     temp->left = BST(arr , index , lower , temp->data);
     temp->right = BST(arr , index , temp->data ,  upper);
     return temp;
 }
    bool canRepresentBST(vector<int> &arr) {
        // code here
        int index = 0;
        int lower = INT_MIN;
        int upper = INT_MAX;
        BST(arr , index , lower , upper);
        if(index==arr.size())
        return 1;
        else
        return 0;
       
        
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-10-09 15:50:44
- **Status:** Correct
- **Marks:** 0

```cpp
class Node
{
    public:
    int data;
    Node *left , *right;
    Node(int x)
    {
        data = x;
        left = NULL;
        right = NULL;
    }
};
class Solution {
  public:
  Node *BST(vector<int>&arr , int &index , int lower , int upper)
  {
      if(index==arr.size()||arr[index]<lower||arr[index]>upper)
      return NULL;
      Node *temp = new Node(arr[index++]);
      temp->left = BST(arr , index , lower , temp->data);
      temp->right = BST(arr, index , temp->data , upper);
      return temp;
  }
    bool canRepresentBST(vector<int> &arr) {
        // code here
        int index = 0;
        int lower = INT_MIN;
        int upper = INT_MAX;
        Node *root = BST(arr , index , lower , upper);
        if(index==arr.size())
        return 1;
        else
        return 0;
        
    }
};
```

#### Solution 5 (C++)

- **Submitted:** 2026-10-09 15:50:32
- **Status:** Correct
- **Marks:** 4

```cpp
class Node
{
    public:
    int data;
    Node *left , *right;
    Node(int x)
    {
        data = x;
        left = NULL;
        right = NULL;
    }
};
class Solution {
  public:
  Node *BST(vector<int>&arr , int &index , int lower , int upper)
  {
      if(index==arr.size()||arr[index]<lower||arr[index]>upper)
      return NULL;
      Node *temp = new Node(arr[index++]);
      temp->left = BST(arr , index , lower , temp->data);
      temp->right = BST(arr, index , temp->data , upper);
      return temp;
  }
    bool canRepresentBST(vector<int> &arr) {
        // code here
        int index = 0;
        int lower = INT_MIN;
        int upper = INT_MAX;
        Node *root = BST(arr , index , lower , upper);
        if(index==arr.size())
        return 1;
        else
        return 0;
        
    }
};
```

*Generated on: 10/9/2026, 7:38:04 PM*