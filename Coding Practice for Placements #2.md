# Coding Practice for Placements 2

### Problem Statement: Find Nth last element of a linked list. For  example, in list 1->2->5->4->null 3rd last element is 2

#### Follow-Up question:     Do the same in a single iteration.
#### Follow-Up question 2:   Present Linked list as other data structures (stack, queue, tree, graph)
---

Since this question won't need any additional information to be provided, we can directly start with the solving procedure.
The Brute Force approach will be to first count the number of elements in the linked list and then determine the nth last element.

`Note: The solutions provided are pseudo codes. You will need to implement them using sytax of language of your choice`
```
function(list, n){                                // list represent the starting node. it will have value and next properties
  list1=list;                                     // making a temporary copy of the node
  count=1;
  while(list.next!=null){                         // loop till we reach the last node
    count++;                                      // counting the length of the list  
    list=list.next;                               
  }
  count=count-n;
  while(count-- > 0)                              // getting to the nth last element
    list1=list1.next;
  return list1.value;
}
```

For the follow up question, this is a very famous approach. We will use two pointers and increment them along the list at the same time. 
We will move one of the pointers n spaces ahead at the beginning, while the other pointer still points at the fist node. Now when incrementing both the pointers, when the second pointer reaches the end of the list, first pointer will be at nth last node
```
function(list, k){                                // list represent the starting node. it will have value and next properties
  list1=list;                                     // making a temporary copy of the node
  while(n-- > 0)                                  // moving one pointer n spaces ahead
    list=list.next;
  while(list.next!=null){                        // loop till we reach the last node
    list1=list1.next;                            // list1 will point to nth last node if list reaches end of node 
    list=list.next;                               
  }
  return list1.value;
}
```

For the next follow up question, you might be asked to implement stack, queue or tree using linked list. Insertion and deletion of nodes also can be asked as follow-up question.
Also, do search up turtle and hare algorithm for detection the loops in a linked list.
