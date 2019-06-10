# Coding Practice for Placement #6
### Problem Statement: Given an array of integers and a range N, find the number of duplicates present. 

##### Follow-up Question 1: Do this in constant space.
---
This problem is quite simple were it not for the follow up question. Normally, you can do this by counting the frequency of each element and if it is >= 2, printing it. But this apprach requires extra O(n) space. 

Since we were given the range, we can avoid the extra space using it. We can use index of an array to represent the numbers and mark the element as negative whose index is the element present. The algorithm is as follows:
```
Itereate the array and check for sign of A[abs(A[i])] ;
  if positive then
     make it negative by   A[abs(A[i])]=-A[abs(A[i])];
  else  // i.e., A[abs(A[i])] is negative
     element is a repetition
```
One more approach for this is as follows:
```
Traverse the given array. Go to index arr[i]%n and increment its value by n.
Now traverse the array again and print all those indexes i for which arr[i]/n is greater than 1.

/*Note: you will print the index i, not the element stored at i*/
```
