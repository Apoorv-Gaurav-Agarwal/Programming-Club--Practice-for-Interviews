# Coding Practice for Placements 5

### You are provided with an unending stream of sorted integers like 1,1,1,1,2,2,2,3,4,5,11,12,12,12,12,12,12,12,12,12,12...
### You don't know the length of this stream. Your task is to find an integer in this stream and print its position(any one of the position). There can be unending number of duplicates.

##### Follow-up Question 1: Better complexity than O(n)
##### Follow-up Question 2: What will change in your code if negative numbers are present.
##### Follow-up Question 3: Return the number of duplicates of the given number. Example- In the above stream, if number is 2, you have to return 3.

#### Bonus: Given a bag consisting of 15 white marbles and 13 black marbles and a heap of infinite black and white marbles outside. Every time you need to pick 2 marbles. If both marbles are of same color, then put back a white marble and if the marbles are of different colors then put back a black marble in the bag. Answer the following:
##### How many marble/s will be left in the bag when you cannot further continue this process?
##### What will the color of only marble left in the bag when the process cannot be continued further?
---
The brute force approach for this problem will be performing a linear search for finding the number.

Since the stream of integers is sorted, we can perform binary search. The only problem will be we dont know the size of the stream. We can address this problem
by modifying it a little. Let low be pointing to 1st element and high pointing to 2nd element of array. Now compare key with high index element,
```
-> If it is greater than high index element then copy high index in low index and double the high index.
-> If it is smaller, then apply binary search on high and low indices found.
```
Hence, for finding the correct range to apply binary search, we will take O(log n) time and for finding the element, we will take O(log n). Our overall complexity will be 2*O(log n) or simply O(log n). The pseudo code for the following: 
```
function search(int arr[], int tofind){
  int l = 0, h = 1; 
  int val = arr[0]; 
  // Find h to do binary search 
  while (val < tofind){ 
    l = h;     // store previous high 
    //check that 2*h doesn't exceeds array  
    //length to prevent ArrayOutOfBoundException 
    if(2*h < arr.length-1) h = 2*h;              
    else  h = arr.length-1; 
    val = arr[h]; // update new val 
    } 
  //Now we know the range where we can perform binary search
  /*Code for binary Search here using l and h as found above*/
```

In case of negative numbers being present, the approach won't change since you will be starting with the smallest number. The question is generally asked to confuse the interviewer as he may answer "We need to change the lower part as we changed the higher part of the array."
For the last follow up question, you can modify binary search a little to find the range.

#### Puzzle

The answer to the puzzle is that only one marble will be left at the end which will be black.

Since marbles can only be taken out in pairs and you started off with an odd number of black. There is always going to be one black left over that you'll keep putting back in the box until it's left on its own.

If you still need help, suppose you take out all the black marbles first in pairs. Bag will contain 21 white and 1 black marble. Now white + black combination
will remove the white marble and white + white combination will also remove the white marble. You won't be able to remove black marble. Same will happen if you remove all white marbles first.
