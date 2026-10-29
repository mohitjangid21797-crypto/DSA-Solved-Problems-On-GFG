## 01. Optimal Solution | Java | TC : O(m+n) | SC : O(h1+h2)

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/merge-two-bst-s/1)

### Problem Description

**Task:** Given the roots r1 and r2 of two Binary Search Trees (BSTs), merge the elements of both trees into a single sorted array and return it. The returned array should contain all the elements from both BSTs, including duplicate values if they are present.Examples: Input: r1 = [3, 1, 5], r2 = [4, 2, 6]Output: [1, 2, 3, 4, 5, 6]

#### Examples

##### Example 1

- **Explanation:** After merging and sorting the two BST we get [0, 1, 2, 3, 5, 8, 10].

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n + m)
- **Expected Auxiliary Space Complexity:** O(n + m)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-13 15:00:34
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
  void Inorder(Node *root , vector<int>&arr)
  {
      if(root==NULL)
      return;
      Inorder(root->left , arr);
      arr.push_back(root->data);
      Inorder(root->right , arr);
  }
    vector<int> merge(Node *r1, Node *r2) {
        // code here
        vector<int>arr1 , arr2;
       Inorder(r1 , arr1);
       Inorder(r2 , arr2);
       vector<int>ans;
       int first  = 0 , second = 0;
       while(first<arr1.size()&&second<arr2.size())
       {
           if(arr1[first]<=arr2[second])
           {
               ans.push_back(arr1[first]);
               first++;
           }
           else
           {
               ans.push_back(arr2[second]);
               second++;
           }
       }
       while(first<arr1.size())
       {
           ans.push_back(arr1[first]);
           first++;
       }
       while(second<arr2.size())
       {
           ans.push_back(arr2[second]);
           second++;
       }
       return ans;
       
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-13 15:00:24
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
  void Inorder(Node *root , vector<int>&arr)
  {
      if(root==NULL)
      return;
      Inorder(root->left , arr);
      arr.push_back(root->data);
      Inorder(root->right , arr);
  }
    vector<int> merge(Node *r1, Node *r2) {
        // code here
        vector<int>arr1 , arr2;
       Inorder(r1 , arr1);
       Inorder(r2 , arr2);
       vector<int>ans;
       int first  = 0 , second = 0;
       while(first<arr1.size()&&second<arr2.size())
       {
           if(arr1[first]<=arr2[second])
           {
               ans.push_back(arr1[first]);
               first++;
           }
           else
           {
               ans.push_back(arr2[second]);
               second++;
           }
       }
       while(first<arr1.size())
       {
           ans.push_back(arr1[first]);
           first++;
       }
       while(second<arr2.size())
       {
           ans.push_back(arr2[second]);
           second++;
       }
       return ans;
       
    }
};
```

*Generated on: 10/13/2026, 3:00:53 PM*