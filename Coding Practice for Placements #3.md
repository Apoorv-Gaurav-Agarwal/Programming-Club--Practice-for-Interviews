# Coding Practice for Placements 3

### Problem Statement : Find the nth number of the series. Series is a defined as sum of unique powers of 5 :                            5 , 25 , 30(5+25) , 125 , 130(125+5) , 150(125+25) , 155(125+25+5)...... 


#### Follow-Up question 1:   Use Constant Space  
#### Follow-Up question 2:   Expected Time Complexity is O(log n)
---

The first thing you should do upon receiving a problem from the interviewer is to ask question about the problem such as what is the range of n for determining whether it can be stored in int/long datatype or should we create something to store the very large number like BigInteger in java. Ask about the starting values of n

The brute force approach for this question is to stores all the power of 5  and then summing up all those power untill the n is not reached.

Store the starting cases, 5 and 25 here, when n is equal to 1 or 2. Now start two pointers, one starting from 5 and second to the value of the series encountered till now. Start adding the values of the pointers and increment the starting pointer to get the next element of the series, until the second pointer is reached. When we reach to the second pointer and nth element is not found , this means we need to enter a new power of 5 so as to proceed with the series.

`Here, after second element i.e. 25, first pointer is at position 5 and second pointer is at 25. We add them to get next value. Now, both pointers are at same position, we add next power ie 125 to the series and reset the first pointer to 5 and continue with this operation`

The pseudo code for this brute force approach is as follows: 

`Note: The solutions provided are pseudo codes. You will need to implement them using syntax of language of your choice`
```
array indexing is 1 based
function(n){
  arr={5,25} ; // initial values of the series in the array whose size in n
  curr=2; // maximum power of power encountered till now
  v=3;  // index o the next value of the series 
  i=1 , j=2 ; // initial pointers, one pointing to the starting of the array and second to the highest value of the series till now
  
  while(v<=n){
    if(i==j){
      curr++;   // to update maximum power of 5 next time
      arr[v] = power(5,curr);   // introduce new power of 5  
      j=v;   // current maximum value of 
      v++;    // update v as new value in the series is encounter
      i=1;  // update i to so as to start again start the series from 1
      
    }
    else{
     arr[v] = arr[i] + arr[j]; // next value of  the  series
     i++;  // update to next value
     v++; // update v as we have a new element in the series
    }
  }
  return arr[n];
}
```
---------------------------------------------------------------------------------------------------------------------------
### Method - 2
We can now look this question in a different way to improve the time complexity.
As the question suggest,numbers of the series can be expressed as sum of unique power of 5. Think how can we represent any number in a unique way.
We can have this intution by looking at the bit representation of the position of these numbers. 
The bit representation of every number is unique. Also the series proceed as a monotonically increasing sequence therefore 
we can somehow use bit representation. Like binary numbers, decimal representation of any binary number and can be 
seen as sum of unique powers of 2. Likewise we can represent the numbers of our series as unique power of 5.

Like 

Number     | Bit Representation |  Value                       |   Final Value
---------- | ------------------ | ---------------------------- | ----------------
  1        | 01                 | (1\*5^1)                     |        5
  2        | 10                 | (1\*5^2)+(0\*5^1)            |        25
  3        | 11                 | (1\*5^2)+(1\*5^1)            |        30
  4        | 100                | (1\*5^3)+(0\*5^2)+(0\*5^1)   |        125
  5        | 101                | (1\*5^3)+(0\*5^2)+(1\*5^1)   |        130
  
  
```
function(n){
  curr = 1;     
  result=0;       //  initial values of the result will be zero   
  while(n>0){
    curr = curr*5;    // update value of the 5  
    if(n&1==1)         // we need to update the result only if we get 1 at the ith bit position
        result += curr;     // update the result
    n>>=1;              // right shift the bits by 1 place
  }
  return result;    // return the final result
}
```

#### Happy Coding
