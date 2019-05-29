# Coding Practice for Placements 1

### Problem Statement: Given an array of numbers and a number k, return whether whether any 2 numbers from the array add up to K. For example, given [10, 3, 2, 7] and K=12, return yes since 10+2=12. If K would have been 11, return no.

#### Follow-Up question:     Do this in one pass, ie, in O(n).
#### Follow-Up question 2:   Explain how the used data-structure is implemented/stored in C++/Java/python
#### Follow-Up question 3:   Time Complexities of various operations of the used data structures
---
First, you must clear all the doubts regarding the question before proceeding, like for example, if k=6, will the function return yes since 3+3=6 etc. The very basic approach for this question will be to use two loops, checking for each pair if the sum is equivalent to K. Pseudo code for this will be


`Note: The solutions provided are pseudo codes. You will need to implement them using sytax of language of your choice`
```
function(arr[], k){
  for(i=0; i<arr.length;i++){                     //this loop selects an element
    for(int j=i+1;j<arr.length;j++){              // this loop creates its pair with all other numbers. if interviewer tells to
      if(arr[i]+arr[j]==k)                        // include the (3,3) pair, start from j=0        
        return "yes";                             // we can return yes since we found our pair
    }
  }
  return "no";                                   // since yes wasnt returned, no pair mus be equal to k
}
```

For the follow up question, think in this way. Since `arr[i]+arr[j]==k` we can find if `k-arr[i]` is present in the array. If we iterate through array again, we wont be able to do this in O(n). Hence we will be using Map data structure as we can search for an element it it in O(1) time. We can use Set too, but if duplicate elements are present, we wont be able to differentiate.
```
function(arr[], k){
  for(int i=0;i<n;i++){                                     // loop for filling the map
    if(map.contains(arr[i]))                                // if duplicates are present
      map.put(arr[i], map.get(arr[i])++);                   // fetch the count, and increase it.
    else
      map.put(arr[i],1);                                    // set the count for element to be 1
  }
  for(int i=0;i<n;i++){                                     // Select each element
    if(map.contains(k-arr[i])){                             // If map contains k-element, we found the pair
       if(k-arr[i]==arr[i]){                                // This is the corner case. It will be explained later. Not needed if (3,3) is counted
          if(map.get(k-arr[i])>1)
            return "yes";
          else continue;
       }
      return "yes";                                         // since we found the pair, return yes
    }
  }
  return "no";                                              // since we didnt find the pair, return no
}
```

The corner case for this problem is that in the array `[10,3,2,7]` and `K=6` if we dont store the count, k-3 will return 3 which will be present in the map. Hence if this is the case, we should see if 3 occurs in the array more than once by storing its count.

For the next two follow up questions, use internet :D

[You may find this useful for questions regarding hashmaps](https://javarevisited.blogspot.com/2011/02/how-hashmap-works-in-java.html)
