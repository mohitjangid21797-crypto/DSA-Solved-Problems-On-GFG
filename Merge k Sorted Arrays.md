## 01. Merge k Sorted Arrays

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/merge-k-sorted-arrays/1)

### Problem Description

**Task:** Given a 2D matrix mat[][] of size n x m. Each row in the matrix is sorted in non-decreasing order, merge all the rows and return a single sorted array that contains all the elements of the matrix.

#### Examples

##### Example 1

- **Input:**
```text
mat[][] = [[1, 3, 5, 7], [2, 4, 6, 8], [0, 9, 10, 11]]Output: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
```
- **Explanation:** Merging all elements from the 3 sorted arrays and sorting them results in: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11].

##### Example 2

- **Input:**
```text
mat[][] = [[1, 2, 3, 4], [2, 2, 3, 4], [5, 5, 6, 6], [7, 8, 9, 9]]Output: [1, 2, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 8, 9, 9]
```
- **Explanation:** Merging all elements from the 4 sorted arrays and sorting them results in:[1, 2, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 8, 9, 9]

#### Constraints

- **1.** `1 ≤ n * m ≤ 10⁵⁰ ≤ mat[i][j] ≤ 10⁶`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(k*log(n)), k = total no. of elementsAuxiliary Space: O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (4)

#### Solution 1 (C++)

- **Submitted:** 2026-11-16 19:30:52
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
  void Merge(vector<int>&arr , int start , int mid , int end)
  {
      if(start>end)
      return;
      int left = start , right = mid+1 , index = 0;
      vector<int>temp(end-start+1);
      while(left<=mid&&right<=end)
      {
          if(arr[left]<=arr[right])
          {
              temp[index] = arr[left];
              left++;
              index++;
          }
          else
          {
              temp[index] = arr[right];
              right++;
              index++;
          }
      }
      while(left<=mid)
      {
          temp[index] = arr[left];
          left++;
          index++;
      }
      while(right<=end)
      {
          temp[index] = arr[right];
          right++;
          index++;
      }
      index = 0;
      int x = start;
      while(x<=end)
      {
          arr[x] = temp[index];
          x++;
          index++;
      }
  }
  void mergeSort(vector<int>&arr , int start , int end , int portion , int k)
  {
      if(portion<=1)
      return;
      int mid = start + ((portion/2)*k) -1;
      mergeSort(arr ,start , mid , portion/2 , k);
      mergeSort(arr , mid+1 , end , portion-(portion/2) , k);
      Merge(arr , start , mid , end);
  }
        
    vector<int> mergeArrays(vector<vector<int>> &arr) {
       vector<int>v;
       for(int i = 0 ; i<arr.size() ; i++)
       {
           for(int j = 0 ; j<arr[i].size() ; j++)
           v.push_back(arr[i][j]);
       }
       mergeSort(v , 0 , v.size()-1 , arr.size() , arr[0].size());
       return v;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-16 19:30:40
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
  void Merge(vector<int>&arr , int start , int mid , int end)
  {
      if(start>end)
      return;
      int left = start , right = mid+1 , index = 0;
      vector<int>temp(end-start+1);
      while(left<=mid&&right<=end)
      {
          if(arr[left]<=arr[right])
          {
              temp[index] = arr[left];
              left++;
              index++;
          }
          else
          {
              temp[index] = arr[right];
              right++;
              index++;
          }
      }
      while(left<=mid)
      {
          temp[index] = arr[left];
          left++;
          index++;
      }
      while(right<=end)
      {
          temp[index] = arr[right];
          right++;
          index++;
      }
      index = 0;
      int x = start;
      while(x<=end)
      {
          arr[x] = temp[index];
          x++;
          index++;
      }
  }
  void mergeSort(vector<int>&arr , int start , int end , int portion , int k)
  {
      if(portion<=1)
      return;
      int mid = start + ((portion/2)*k) -1;
      mergeSort(arr ,start , mid , portion/2 , k);
      mergeSort(arr , mid+1 , end , portion-(portion/2) , k);
      Merge(arr , start , mid , end);
  }
        
    vector<int> mergeArrays(vector<vector<int>> &arr) {
       vector<int>v;
       for(int i = 0 ; i<arr.size() ; i++)
       {
           for(int j = 0 ; j<arr[i].size() ; j++)
           v.push_back(arr[i][j]);
       }
       mergeSort(v , 0 , v.size()-1 , arr.size() , arr[0].size());
       return v;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-11-16 19:21:48
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
  void Merge(vector<int>&arr , int start , int mid , int end)
  {
      if(start>end)
      return;
      int left = start , right = mid+1 , index = 0;
      vector<int>temp(end-start+1);
      while(left<=mid&&right<=end)
      {
          if(arr[left]<=arr[right])
          {
              temp[index] = arr[left];
              left++;
              index++;
          }
          else
          {
              temp[index] = arr[right];
              right++;
              index++;
          }
      }
      while(left<=mid)
      {
          temp[index] = arr[left];
          left++;
          index++;
      }
      while(right<=end)
      {
          temp[index] = arr[right];
          right++;
          index++;
      }
      index = 0;
      int x = start;
      while(x<=end)
      {
          arr[x] = temp[index];
          x++;
          index++;
      }
  }
  void mergeSort(vector<int>&arr , int start , int end , int portion , int k)
  {
      if(portion<=1)
      return;
      int mid = start + ((portion/2)*k) -1;
      mergeSort(arr ,start , mid , portion/2 , k);
      mergeSort(arr , mid+1 , end , portion-(portion/2) , k);
      Merge(arr , start , mid , end);
  }
        
    vector<int> mergeArrays(vector<vector<int>> &arr) {
       vector<int>v;
       for(int i = 0 ; i<arr.size() ; i++)
       {
           for(int j = 0 ; j<arr[i].size() ; j++)
           v.push_back(arr[i][j]);
       }
       mergeSort(v , 0 , v.size()-1 , arr.size() , arr[0].size());
       return v;
    }
};
```

#### Solution 4 (C++)

- **Submitted:** 2026-11-16 18:03:58
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
  public:
        
    vector<int> mergeArrays(vector<vector<int>> &arr) {
       vector<pair<int , pair<int , int>>>v;
       for(int i = 0 ; i<arr.size() ; i++)
       v.push_back(make_pair(arr[i][0] , make_pair(i,0)));
       
priority_queue<pair<int , pair<int , int>> , vector<pair<int , pair<int , int>>> ,  greater<pair<int , pair<int , int>>>>p(v.begin() , v.end());
   
   
   vector<int>ans;
   int i = 0 , j  = 0;
   pair<int , pair<int , int>>Element;
   while(!p.empty())
   {
       Element = p.top();
       p.pop();
       i = Element.second.first;
       j = Element.second.second;
       ans.push_back(Element.first);
       if(j+1<arr[i].size())
       {
           p.push(make_pair(arr[i][j+1] , make_pair(i, j+1)));
       }
   }
   return ans;
    }
};
```

*Generated on: 11/16/2026, 7:46:13 PM*