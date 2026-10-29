## 01. JAVA SOLUTION

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/avl-tree-insertion/1)

### Problem Description

**Task:** Given the root of a AVL Tree and an integer key, insert the key into the given AVL Tree such that the tree remains a valid AVL Tree after the insertion. The task is to return the root of the updated AVL Tree after inserting the given key.
The given tree is initially a valid AVL Tree.
The key does not already exist in the tree.

#### Examples

##### Example 1

- **Input:**
```text
root = [4, 2, 6, N, N, N, 8], key = 10Output: Explanation: After inserting 10 in the given tree, it will become Now, the balance factor of node 6 becomes -2, which violates the AVL property.Perform a left rotation on node 6 & we get
```

##### Example 2

- **Input:**
```text
root = [20, 9, 25, 1, 15], key = 13Output: Explanation: After inserting 13 in the given tree, it will becomeNow, the balanced factor of node 20 becomes +2, which violates the AVL property.Perform a left rotation on node 9 & perform a right rotation on 20, we get
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log n)
- **Expected Auxiliary Space Complexity:** O(log n)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-10-15 18:16:44
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of AVL Tree Node
class Node {
public:
    int data;
    int height;
    Node *left, *right;
    Node(int x) {
        data = x;
        height = 1;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
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
      Node*top = root;
      Node *middle = root->left;
      Node *middleright = middle->right;
      middle->right = top;
      top->left = middleright;
      top->height = 1 + max(Height(top->left) , Height(top->right));
      middle->height = 1 + max(Height(middle->left) , Height(middle->right));
      return middle;

  }
  Node *leftRotation(Node *root)
  {
      Node *top = root;
      Node *middle = root->right;
      Node* middleleft = middle->left;
      middle->left = top;
      top->right = middleleft;
      top->height = 1 + max(Height(top->left) , Height(top->right));
      middle->height = 1 + max(Height(middle->left) , Height(middle->right));
      return middle;
  }

    Node* insertToAVL(Node* root, int key) {
        // code here
        if(!root)
      {
          Node *temp = new Node(key);
          return temp;
      }
      else
      {
          // key<root->data--> move left
          if(key<root->data)
          {
              root->left = insertToAVL(root->left , key);
          }
          // key>root->data--> move right
          else if(key>root->data)
          {
              root->right = insertToAVL(root->right , key);
          }
          // key==root->data --> return
          else
          return root;

          // Calculate Height
          root->height = 1 + max(Height(root->left) , Height(root->right));

          // Calculate Balance:
          int balance = getBalance(root);

          // Check balance:
          // 1. Balance>1 and key<root->left->data  ==> LL
          if(balance>1&&key<root->left->data)
          {
              return rightRotation(root);
          }
          // 2. Balance<1 and key>root->right->data ==> RR
          else if(balance<-1 && key>root->right->data)
          {
              return leftRotation(root);
          }
          // 3. Balance>1 and key>root->left->data  ==> LR
          else if(balance>1 && key>root->left->data)
          {
              root->left = leftRotation(root->left);
              return rightRotation(root);
          }
          // 4. Balance<1 and key<root->right->data ==> RL
          else if(balance<-1&&key<root->right->data)
          {
              root->right = rightRotation(root->right);
              return leftRotation(root);
          }
          else
          return root;   
      }
        
        
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-15 18:16:27
- **Status:** Correct
- **Marks:** 8

```cpp
/* Structure of AVL Tree Node
class Node {
public:
    int data;
    int height;
    Node *left, *right;
    Node(int x) {
        data = x;
        height = 1;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
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
      Node*top = root;
      Node *middle = root->left;
      Node *middleright = middle->right;
      middle->right = top;
      top->left = middleright;
      top->height = 1 + max(Height(top->left) , Height(top->right));
      middle->height = 1 + max(Height(middle->left) , Height(middle->right));
      return middle;

  }
  Node *leftRotation(Node *root)
  {
      Node *top = root;
      Node *middle = root->right;
      Node* middleleft = middle->left;
      middle->left = top;
      top->right = middleleft;
      top->height = 1 + max(Height(top->left) , Height(top->right));
      middle->height = 1 + max(Height(middle->left) , Height(middle->right));
      return middle;
  }

    Node* insertToAVL(Node* root, int key) {
        // code here
        if(!root)
      {
          Node *temp = new Node(key);
          return temp;
      }
      else
      {
          // key<root->data--> move left
          if(key<root->data)
          {
              root->left = insertToAVL(root->left , key);
          }
          // key>root->data--> move right
          else if(key>root->data)
          {
              root->right = insertToAVL(root->right , key);
          }
          // key==root->data --> return
          else
          return root;

          // Calculate Height
          root->height = 1 + max(Height(root->left) , Height(root->right));

          // Calculate Balance:
          int balance = getBalance(root);

          // Check balance:
          // 1. Balance>1 and key<root->left->data  ==> LL
          if(balance>1&&key<root->left->data)
          {
              return rightRotation(root);
          }
          // 2. Balance<1 and key>root->right->data ==> RR
          else if(balance<-1 && key>root->right->data)
          {
              return leftRotation(root);
          }
          // 3. Balance>1 and key>root->left->data  ==> LR
          else if(balance>1 && key>root->left->data)
          {
              root->left = leftRotation(root->left);
              return rightRotation(root);
          }
          // 4. Balance<1 and key<root->right->data ==> RL
          else if(balance<-1&&key<root->right->data)
          {
              root->right = rightRotation(root->right);
              return leftRotation(root);
          }
          else
          return root;   
      }
        
        
    }
};
```

*Generated on: 10/15/2026, 6:17:05 PM*