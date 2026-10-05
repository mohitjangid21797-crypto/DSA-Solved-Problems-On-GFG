## 01. Tree Boundary Traversal

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1)

### Problem Description

**Task:** My SubmissionsRefresh Time (IST)StatusMarksLangTest CasesCode2026-10-05 15:12:59Correct0cpp1111 / 1111View2026-10-05 15:11:26Correct0cpp1111 / 1111View2026-10-05 15:07:46Wrong0cpp2 / 1111View2026-10-05 15:06:52Wrong0cpp2 / 1111View2026-10-05 15:04:32Wrong0cpp7 / 1111View2026-10-05 15:02:15Wrong0cpp2 / 1111View2026-08-24 12:43:18Correct0cpp1111 / 1111View2026-08-24 12:39:43Wrong0cpp11 / 1111View2026-08-24 10:36:57Correct4cpp1111 / 1111View2026-08-24 10:34:39Wrong0cpp0 / 1111View2026-08-24 10:31:29Wrong0cpp0 / 1111ViewDiscussions ( 759 Threads )Most Recent Commenting as Mohit SutharComment AnonymouslySubmit💡Discussion Guidelines×Please avoid posting complete solutions or full code in the comments.Ask questions, share hints, discuss approaches, or report any issues. Let's help everyone learn together.Anonymous_Geek1 month agoSep 04, 2026 10:18 (GMT +5:30)https://youtu.be/DkE1OsXuhj00ReplySanthosh Katta1 month agoSep 03, 2026 18:23 (GMT +5:30)class Solution { public: void left(Node* root, vector < int > &ans){
if(root = = nullptr) return ; if(root- > left = = nullptr && root- > right = = nullptr) return;
ans.push_back(root- > data); if(root- > left) left(root- > left,ans); else left(root- > right,ans);
} void leaf(Node* root, vector < int > &ans){ if(root = = nullptr) return ; if(root- > left = = nullptr && root- > right = = nullptr) { ans.push_back(root- > data); return; }
leaf(root- > left,ans); leaf(root- > right,ans); } void right(Node* root, vector < int > &ans){ if(root = = nullptr) return ; if(root- > left = = nullptr && root- > right = = nullptr) return;
if(root- > right) right(root- > right,ans); else right(root- > left,ans);
ans.push_back(root- > data); } vector < int > boundaryTraversal(Node *root) { vector < int > ans; if(root = = nullptr) return ans; if(root- > left = = nullptr && root- > right = = nullptr) { ans.push_back(root- > data); return ans; } ans.push_back(root- > data); left(root- > left,ans); leaf(root,ans); right(root- > right,ans);
return ans; }};0Reply(Show 1 Replies)Ronak Mulani1 month agoAug 20, 2026 16:32 (GMT +5:30)class Solution { void leftSide(Node root, ArrayList < Integer > ans){
if(root = = null || (root.left = = null && root.right = = null)){ return; }
ans.add(root.data);
if(root.left ! = null){ leftSide(root.left, ans); }else{ leftSide(root.right, ans); } } void leaves(Node root, ArrayList < Integer > ans){ if(root = = null){ return; } if(root.left = = null && root.right = = null){ ans.add(root.data); } leaves(root.left,ans); leaves(root.right,ans); } void rightSide(Node root, ArrayList < Integer > list){
if(root = = null || (root.left = = null && root.right = = null)){ return; }
list.add(root.data);
if(root.right ! = null){ rightSide(root.right, list); }else{ rightSide(root.left, list); } } public ArrayList < Integer > boundaryTraversal(Node root) { // code here ArrayList < Integer > ans = new ArrayList < > (); //added root element in ans ans.add(root.data); //left side excluding leaves leftSide(root.left,ans); //left nodes //if left or right not exiests if(root.left! = null || root.right! = null){ leaves(root,ans); } //right side reversely excluding leaves ArrayList < Integer > list = new ArrayList < > (); rightSide(root.right,list); Collections.reverse(list); for(int num : list){ ans.add(num); } return ans; }}0ReplyVishal TomaR2 months agoAug 03, 2026 11:55 (GMT +5:30)/* Node Structure
class Node {
public:
int data;
Node* left, *right;
Node(int val) {
data = val;
left = right = nullptr;
}
}; */
class Solution {
bool isleaf(Node * root) {
return !root- > left && !root- > right;
}
void left(Node * root, vector < int > &ans) {
Node *curr = root- > left;
while (curr) {
if (!isleaf(curr)) {
ans.push_back(curr- > data);
}
if (curr- > left) {
curr = curr- > left;
}
else {
curr = curr- > right;
}
}
}
void right(Node * root, vector < int > &ans) {
Node *curr = root- > right;
vector < int > temp;
while (curr) {
if (!isleaf(curr)) {
temp.push_back(curr- > data);
}
if (curr- > right) {
curr = curr- > right;
}
else {
curr = curr- > left;
}
}
for (int i = temp.size() - 1 ; i >= 0 ; i--) {
ans.push_back(temp[i]);
}
}
void leaf(Node* root, vector < int > &ans) {
if (!root)
return ;
if (isleaf(root)) {
ans.push_back(root- > data);
return ;
}
leaf(root- > left, ans);
leaf(root- > right, ans);
}
public:
vector < int > boundaryTraversal(Node *root) {
// code here
vector < int > ans;
if (!root)
return ans;
if (!isleaf(root))
ans.push_back(root- > data);
left(root, ans);
leaf(root, ans);
right(root, ans);
return ans;
}
};
CPP | 78% beats
0Reply(Show 1 Replies)nameless2 months agoJul 21, 2026 12:18 (GMT +5:30)python 3 solution class Solution: def isLeaf(self, root): return root.left is None and root.right is None def leftBoundary(self, root, ans): if root is None or self.isLeaf(root): return ans.append(root.data) if root.left: self.leftBoundary(root.left, ans) else: self.leftBoundary(root.right, ans) def addLeaves(self, root, ans): if root is None: return if self.isLeaf(root): ans.append(root.data) return self.addLeaves(root.left, ans) self.addLeaves(root.right, ans) def rightBoundary(self, root, ans): if root is None or self.isLeaf(root): return if root.right: self.rightBoundary(root.right, ans) else: self.rightBoundary(root.left, ans) ans.append(root.data) def boundaryTraversal(self, root): if root is None: return [] if self.isLeaf(root): return [root.data] ans = [root.data] self.leftBoundary(root.left, ans) self.addLeaves(root, ans) self.rightBoundary(root.right, ans) return ans0Replynameless2 months agoJul 21, 2026 12:15 (GMT +5:30)class Solution: def boundaryTraversal(self, root): return root.left is None and root.right is None
def leftBoundary(self, root, ans):
if root is None: return
if not self.isLeaf(root): ans.append(root.data)
if root.left: self.leftBoundary(root.left, ans) elif root.right: self.leftBoundary(root.right, ans)
# Add all leaf nodes def addLeaves(self, root, ans):
if root is None: return
if self.isLeaf(root): ans.append(root.data) return
self.addLeaves(root.left, ans) self.addLeaves(root.right, ans)
# Add Right Boundary in reverse def rightBoundary(self, root, ans):
if root is None: return
if root.right: self.rightBoundary(root.right, ans) elif root.left: self.rightBoundary(root.left, ans)
if not self.isLeaf(root): ans.append(root.data)
def boundaryTraversal(self, root):
if root is None: return []
if self.isLeaf(root): return [root.data]
ans = [root.data]
# Left Boundary (skip root) self.leftBoundary(root.left, ans)
# Leaf Nodes self.addLeaves(root, ans)
# Right Boundary (skip root) self.rightBoundary(root.right, ans)
return ans 0Replynameless2 months agoJul 21, 2026 12:15 (GMT +5:30)class Solution: def boundaryTraversal(self, root): return root.left is None and root.right is None
def leftBoundary(self, root, ans):
if root is None: return
if not self.isLeaf(root): ans.append(root.data)
if root.left: self.leftBoundary(root.left, ans) elif root.right: self.leftBoundary(root.right, ans)
# Add all leaf nodes def addLeaves(self, root, ans):
if root is None: return
if self.isLeaf(root): ans.append(root.data) return
self.addLeaves(root.left, ans) self.addLeaves(root.right, ans)
# Add Right Boundary in reverse def rightBoundary(self, root, ans):
if root is None: return
if root.right: self.rightBoundary(root.right, ans) elif root.left: self.rightBoundary(root.left, ans)
if not self.isLeaf(root): ans.append(root.data)
def boundaryTraversal(self, root):
if root is None: return []
if self.isLeaf(root): return [root.data]
ans = [root.data]
# Left Boundary (skip root) self.leftBoundary(root.left, ans)
# Leaf Nodes self.addLeaves(root, ans)
# Right Boundary (skip root) self.rightBoundary(root.right, ans)
return ans 0Replynameless2 months agoJul 21, 2026 12:15 (GMT +5:30)class Solution: def boundaryTraversal(self, root): return root.left is None and root.right is None
def leftBoundary(self, root, ans):
if root is None: return
if not self.isLeaf(root): ans.append(root.data)
if root.left: self.leftBoundary(root.left, ans) elif root.right: self.leftBoundary(root.right, ans)
# Add all leaf nodes def addLeaves(self, root, ans):
if root is None: return
if self.isLeaf(root): ans.append(root.data) return
self.addLeaves(root.left, ans) self.addLeaves(root.right, ans)
# Add Right Boundary in reverse def rightBoundary(self, root, ans):
if root is None: return
if root.right: self.rightBoundary(root.right, ans) elif root.left: self.rightBoundary(root.left, ans)
if not self.isLeaf(root): ans.append(root.data)
def boundaryTraversal(self, root):
if root is None: return []
if self.isLeaf(root): return [root.data]
ans = [root.data]
# Left Boundary (skip root) self.leftBoundary(root.left, ans)
# Leaf Nodes self.addLeaves(root, ans)
# Right Boundary (skip root) self.rightBoundary(root.right, ans)
return ans 0Replynameless2 months agoJul 21, 2026 12:15 (GMT +5:30)class Solution: def boundaryTraversal(self, root): return root.left is None and root.right is None
def leftBoundary(self, root, ans):
if root is None: return
if not self.isLeaf(root): ans.append(root.data)
if root.left: self.leftBoundary(root.left, ans) elif root.right: self.leftBoundary(root.right, ans)
# Add all leaf nodes def addLeaves(self, root, ans):
if root is None: return
if self.isLeaf(root): ans.append(root.data) return
self.addLeaves(root.left, ans) self.addLeaves(root.right, ans)
# Add Right Boundary in reverse def rightBoundary(self, root, ans):
if root is None: return
if root.right: self.rightBoundary(root.right, ans) elif root.left: self.rightBoundary(root.left, ans)
if not self.isLeaf(root): ans.append(root.data)
def boundaryTraversal(self, root):
if root is None: return []
if self.isLeaf(root): return [root.data]
ans = [root.data]
# Left Boundary (skip root) self.leftBoundary(root.left, ans)
# Leaf Nodes self.addLeaves(root, ans)
# Right Boundary (skip root) self.rightBoundary(root.right, ans)
return ans 0Reply

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** Not found
- **Expected Auxiliary Space Complexity:** Not found

### Accepted Solutions (4)

#### Solution 1 (C++)

- **Submitted:** 2026-10-05 15:12:59
- **Status:** Correct
- **Marks:** 0

```cpp
/* Node Structure
class Node {
  public:
    int data;
    Node* left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  void leftsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return;
      ans.push_back(root->data);
      if(root->left)
      {
          leftsubtree(root->left , ans);
      }
      else
      {
          leftsubtree(root->right , ans);
      }
  }
  void leaves(Node *root , vector<int>&ans)
  {
      if(root==NULL)
      return ;
      if(root->left==NULL&&root->right==NULL)
      ans.push_back(root->data);
      leaves(root->left , ans);
      leaves(root->right , ans);
  }
  void rightsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return ;
      if(root->right)
      {
          rightsubtree(root->right , ans);
      }
      else
      {
          rightsubtree(root->left , ans);
      }
      ans.push_back(root->data);
  }
    vector<int> boundaryTraversal(Node *root) {
        // code here
        vector<int>ans;
        if(root->left!=NULL||root->right!=NULL)
        ans.push_back(root->data);
        leftsubtree(root->left , ans);
        leaves(root , ans);
        rightsubtree(root->right , ans);
        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-05 15:11:26
- **Status:** Correct
- **Marks:** 0

```cpp
/* Node Structure
class Node {
  public:
    int data;
    Node* left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  void leftsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return;
      ans.push_back(root->data);
      if(root->left)
      {
          leftsubtree(root->left , ans);
      }
      else
      {
          leftsubtree(root->right , ans);
      }
  }
  void leaves(Node *root , vector<int>&ans)
  {
      if(root==NULL)
      return ;
      if(root->left==NULL&&root->right==NULL)
      ans.push_back(root->data);
      leaves(root->left , ans);
      leaves(root->right , ans);
  }
  void rightsubtree(Node *root , vector<int>&ans)
  {
      if(root==NULL||(root->left==NULL&&root->right==NULL))
      return ;
      if(root->right)
      {
          rightsubtree(root->right , ans);
      }
      else
      {
          rightsubtree(root->left , ans);
      }
      ans.push_back(root->data);
  }
    vector<int> boundaryTraversal(Node *root) {
        // code here
        vector<int>ans;
        if(root->left!=NULL||root->right!=NULL)
        ans.push_back(root->data);
        leftsubtree(root->left , ans);
        leaves(root , ans);
        rightsubtree(root->right , ans);
        return ans;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-08-24 12:43:18
- **Status:** Correct
- **Marks:** 0

```cpp
/* Node Structure
class Node {
  public:
    int data;
    Node* left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  void leftsub(Node *root , vector<int>&ans)
  {
      if(root==NULL||(!root->left&&!root->right))
      return;
      ans.push_back(root->data);
      if(root->left)
      leftsub(root->left , ans);
      else
      leftsub(root->right , ans);
  }
  void rightsub(Node *root , vector<int>&ans)
  {
      if(root==NULL||(!root->left&&!root->right))
      return;
      if(root->right)
      rightsub(root->right , ans);
      else
      rightsub(root->left , ans);
      ans.push_back(root->data);
  }
  void leaf(Node *root , vector<int>&ans)
  {
      if(!root)
      return ;
      if(!root->left&&!root->right)
      {
          ans.push_back(root->data);
          return ;
      }
      leaf(root->left , ans);
      leaf(root->right , ans);
  }
  
    vector<int> boundaryTraversal(Node *root) {
      vector<int>ans;
      ans.push_back(root->data);
      // leftsubtree:
      leftsub(root->left , ans);
      // leaf Nodes;
      if(root->left||root->right)
      leaf(root , ans);
      // rightsubtree:
      rightsub(root->right , ans);
      return ans; 
        
        
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-08-24 10:36:57
- **Status:** Correct
- **Marks:** 4

```cpp
/* Node Structure
class Node {
  public:
    int data;
    Node* left, *right;
    Node(int val) {
        data = val;
        left = right = nullptr;
    }
}; */

class Solution {
  public:
  void leftsub(Node *root , vector<int>&ans)
  {
      if(root==NULL||(!root->left&&!root->right))
      return;
      
      ans.push_back(root->data);
      if(root->left)
      leftsub(root->left , ans);
      else
      leftsub(root->right , ans);
  }
  void leaf(Node *root , vector<int>&ans)
  {
      if(!root)
      return;
      
      if(!root->left&&!root->right)
      {
          ans.push_back(root->data);
          return ;
      }
      leaf(root->left , ans);
      leaf(root->right , ans);
      
  }
   void rightsub(Node *root , vector<int>&ans)
  {
      if(root==NULL||(!root->left&&!root->right))
      return;
      
      if(root->right)
      rightsub(root->right , ans);
      else
      rightsub(root->left , ans);
      ans.push_back(root->data);
  }
    vector<int> boundaryTraversal(Node *root) {
        // code here
        vector<int>ans;
        ans.push_back(root->data);
        
        // left subtree:
        leftsub(root->left , ans);
        
        // leaf nodes:
        if(root->left || root->right)
        leaf(root , ans);
        
        rightsub(root->right , ans);
        return ans;
        
        
    }
};
```

*Generated on: 10/5/2026, 3:13:23 PM*