## 01. MOST OPTIMAL APPROACH IN T.C = O(N) & S.C = O(H) -----> class Solution {public: LNode* find(LNode* c,LNode* d){ LNode* f = c; if(c == d){ return c; } LNode* g = c; while(g != d && g->next != d){ f = f->next; g = g->next->next; } return f; } TNode* solve(LNode* &a1,LNode* &a2){ if(a1 == a2){ return NULL; } LNode* mid = find(a1,a2); TNode* newNode = new TNode(mid->data); newNode->left = solve(a1,mid); newNode->right = solve(mid->next,a2); return newNode; } TNode *sortedListToBST(LNode *head) { TNode* temp = NULL; LNode* a1 = head; LNode* a2 = NULL; return solve(a1,a2); }};

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sorted-list-to-bst/1)

### Problem Description

**Task:** Given a singly linked list whose elements are sorted in ascending order, construct a height-balanced Binary Search Tree (BST) containing the same elements as the linked list. A height-balanced BST is defined as a binary tree in which the depth difference between the left and right subtrees of every node is at most 1.It is guaranteed that the linked list does not contain duplicate values.The middle element would always be the root. In case of even elements, pick the root as second mid as root.You need to return root of the tree, the preorder traversal is printed by the driver code to test your result.Examples:Input: Linked List: 1- > 2- > 3- > 4- > 5- > 6- > 7Output: 4 2 1 3 6 5 7Explanation: The BST formed using elements of the linked list is shown below. Hence, the preorder traversal of the tree is 4 2 1 3 6 5 7.

#### Examples

##### Example 1

- **Input:**
```text
Linked List : 1- > 2- > 3 Output: 2 1 3Explanation: The BST formed using elements of the linked list is - Hence, the preorder traversal of this tree is 2 1 3.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-13 14:39:42
- **Status:** Correct
- **Marks:** 0

```cpp
/* structure of Linked List Node
class LNode {
public:
    int data;
    LNode* next;

    LNode(int x) {
        data = x;
        next = nullptr;
    }
};

// Tree Node
class TNode {
public:
    int data;
    TNode* left;
    TNode* right;

    TNode(int x) {
        data = x;
        left = right = nullptr;
    }
};*/

class Solution {
  public:
  TNode *buildBST(vector<int>&arr , int start , int end)
  {
      if(start>end)
      return NULL;
      int mid = start + (end-start+1)/2;
      TNode *temp = new TNode(arr[mid]);
      temp->left = buildBST(arr , start , mid-1);
      temp->right = buildBST(arr , mid+1 , end);
      return temp;
  }
    TNode *sortedListToBST(LNode *head) {
        // code here
        vector<int>arr;
        LNode *temp = head;
        while(temp)
        {
            arr.push_back(temp->data);
            temp = temp->next;
        }
        int start = 0 , end = arr.size()-1;
        return buildBST(arr , start , end);
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-13 14:39:29
- **Status:** Correct
- **Marks:** 8

```cpp
/* structure of Linked List Node
class LNode {
public:
    int data;
    LNode* next;

    LNode(int x) {
        data = x;
        next = nullptr;
    }
};

// Tree Node
class TNode {
public:
    int data;
    TNode* left;
    TNode* right;

    TNode(int x) {
        data = x;
        left = right = nullptr;
    }
};*/

class Solution {
  public:
  TNode *buildBST(vector<int>&arr , int start , int end)
  {
      if(start>end)
      return NULL;
      int mid = start + (end-start+1)/2;
      TNode *temp = new TNode(arr[mid]);
      temp->left = buildBST(arr , start , mid-1);
      temp->right = buildBST(arr , mid+1 , end);
      return temp;
  }
    TNode *sortedListToBST(LNode *head) {
        // code here
        vector<int>arr;
        LNode *temp = head;
        while(temp)
        {
            arr.push_back(temp->data);
            temp = temp->next;
        }
        int start = 0 , end = arr.size()-1;
        return buildBST(arr , start , end);
    }
};
```

*Generated on: 10/13/2026, 2:40:03 PM*