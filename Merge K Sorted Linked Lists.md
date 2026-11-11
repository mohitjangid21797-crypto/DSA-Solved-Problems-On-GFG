## 01. Merge K Sorted Linked Lists

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/merge-k-sorted-linked-lists/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=bottom_sticky_on_article)

### Problem Description

**Task:** Given an array arr[] of n sorted linked lists of different sizes. Your task is to merge all these lists into a single sorted linked list and return the head of the merged list.Examples:Input:

#### Examples

##### Example 1

- **Output:**
```text
1 - > 2 - > 3 - > 4 - > 7 - > 8 - > 9Explanation: The arr[] has 3 sorted linked list of size 3, 3, 1.1st list: 1 - > 3 - > 72nd list: 2 - > 4 - > 83rd list: 9The merged list will be: Input: Output: 1 - > 3 - > 4 - > 5 - > 6 - > 8Explanation: The arr[] has 3 sorted linked list of size 2, 1, 3.1st list: 1 - > 32nd list: 83rd list: 4 - > 5 - > 6The merged list will be:
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (5)

#### Solution 1 (C++)

- **Submitted:** 2026-11-11 17:01:28
- **Status:** Correct
- **Marks:** 0

```cpp
/* Linked List Node Structure
class Node {
  public:
    int data;
    Node* next;
    Node(int x){
        data = x;
        next = nullptr;
    }
};
*/
class Compare
{
    public:
    bool operator()(Node*a , Node *b)
    {
        return a->data > b->data;
    }
};

class Solution {
  public:
    Node* mergeKLists(vector<Node*>& arr) {
        // code here
        priority_queue<Node* , vector<Node*> , Compare>p(arr.begin() , arr.end());
        
        Node *root = NULL;
        Node *temp = NULL;
        while(!p.empty())
        {
            Node *temp1 = p.top();
            if(root==NULL)
            {
                root= p.top();
                temp = root;
            }
            else
            {
                temp->next = p.top();
                temp = temp->next;
            }
            p.pop();
            if(temp1->next)
            p.push(temp1->next);
        }
        return root;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-11 16:44:12
- **Status:** Correct
- **Marks:** 0

```cpp
/* Linked List Node Structure
class Node {
  public:
    int data;
    Node* next;
    Node(int x){
        data = x;
        next = nullptr;
    }
};
*/
class Compare
{
    public:
    bool operator()(Node*a , Node *b)
    {
        return a->data > b->data;
    }
};

class Solution {
  public:
    Node* mergeKLists(vector<Node*>& arr) {
        // code here
        priority_queue<Node* , vector<Node*> , Compare>p;
        for(int i = 0 ; i<arr.size() ; i++)
        p.push(arr[i]);
        
        Node *root = NULL;
        Node *temp = NULL;
        while(!p.empty())
        {
            Node *temp1 = p.top();
            if(root==NULL)
            {
                root= p.top();
                temp = root;
            }
            else
            {
                temp->next = p.top();
                temp = temp->next;
            }
            p.pop();
            if(temp1->next)
            p.push(temp1->next);
        }
        return root;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-11-11 16:42:59
- **Status:** Correct
- **Marks:** 0

```cpp
/* Linked List Node Structure
class Node {
  public:
    int data;
    Node* next;
    Node(int x){
        data = x;
        next = nullptr;
    }
};
*/
class Compare
{
    public:
    bool operator()(Node*a , Node *b)
    {
        return a->data > b->data;
    }
};

class Solution {
  public:
    Node* mergeKLists(vector<Node*>& arr) {
        // code here
        priority_queue<Node* , vector<Node*> , Compare>p;
        for(int i = 0 ; i<arr.size() ; i++)
        p.push(arr[i]);
        
        Node *root = NULL;
        Node *temp = NULL;
        while(!p.empty())
        {
            Node *temp1 = p.top();
            if(root==NULL)
            {
                root= p.top();
                temp = root;
            }
            else
            {
                temp->next = p.top();
                temp = temp->next;
            }
            p.pop();
            if(temp1->next)
            p.push(temp1->next);
        }
        return root;
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-07-02 21:42:29
- **Status:** Correct
- **Marks:** 0

```cpp
/*
class Node {
  public:
    int data;
    Node* next;

    Node(int x){
        data = x;
        next = NULL;
    }
};
*/

class Solution {
  public:
  Node *merge(Node *curr1 , Node *curr2)
  {
      Node *head3 = new Node(0) , *tail = head3;
      while(curr1&&curr2)
      {
          if(curr1->data<=curr2->data)
          {
              tail->next = curr1;
              tail = tail->next;
              curr1 = curr1->next;
              tail->next = NULL;
          }
          else
          {
              tail->next = curr2;
              tail = tail->next;
              curr2 = curr2->next;
              tail->next = NULL;
          }
      }
      if(curr1)
      tail->next = curr1;
      else
      tail->next = curr2;
      tail = head3;
      head3 = head3->next;
      delete tail;
      return head3;
  }
  void mergesort(vector<Node*>&arr , int start , int end)
  {
      if(start>=end)
      return ;
      int mid = start + (end-start)/2;
      // left array
      mergesort(arr , start , mid);
      // right array
      mergesort(arr , mid+1 , end);
      // merge the sorted list:
      arr[start] = merge(arr[start] , arr[mid+1]);
  }
Node* mergeKLists(vector<Node*>& arr) {
      mergesort(arr , 0 , arr.size()-1);
      return arr[0];
        
    }
};
```

#### Solution 5 (C++)

- **Submitted:** 2026-07-02 21:24:17
- **Status:** Correct
- **Marks:** 0

```cpp
/*
class Node {
  public:
    int data;
    Node* next;

    Node(int x){
        data = x;
        next = NULL;
    }
};
*/

class Solution {
  public:
  Node *merge(Node *curr1 , Node *curr2)
  {
      Node *head3 = new Node(0);
      Node *tail = head3;
      while(curr1&&curr2)
      {
          if(curr1->data<=curr2->data)
          {
              tail->next = curr1;
              tail = tail->next;
              curr1 = curr1->next;
              tail->next = NULL;
          }
          else
          {
              tail->next = curr2;
              tail = tail->next;
              curr2 = curr2->next;
              tail->next = NULL;
          }
      }
      if(curr1)
      tail->next = curr1;
      else
      tail->next = curr2;
      tail = head3;
      head3 = head3->next;
      delete tail;
      return head3;
  }
Node* mergeKLists(vector<Node*>& arr) {
         Node *head = NULL;
         for(int i = 0 ; i<arr.size() ; i++)
         {
             head = merge(head , arr[i]);
         }
         return head;
        
    }
};
```

*Generated on: 11/11/2026, 5:16:49 PM*