# Coding Practice for Placements 4

### Problem Statement: Given a string, return the longest consecutive character and its length. For example, in string "AABCDDEBBBEA", return "B 3" since B occurs max for 3 consecutive times

#### Follow-Up question:     Do this in one pass, ie, in O(n).
#### Follow-Up question 2:   Do this without using additional space.
---
To start this problem, you can ask interviewer questions like "What will be returned if string is empty?", "Will all the characters be uppercase" etc. Here, we will assume empty strings wont be present and all characters are uppercase.

For solving the problem, it is effective to first think of the brute force method and make it efficient step by step. The brute force solution will comprise of checking each consecutive character using 2 for loops. 

The efficient approach will be to maintain pointers while moving through the string once. Hence, we will store only the info we require to process. This approach will satisfy both of the follow up questions.

```
function(char[] str){
  int curr=0, max=0, i;
  char max_char='';
  for(i=0;i<str.length-1;i++){
			if(str[i]==str[i+1])
        curr++;
			else{
				if(max<curr){
          max=curr;
          max_char=str[i];
          }
				curr=1;
			}
		}
  }
```
