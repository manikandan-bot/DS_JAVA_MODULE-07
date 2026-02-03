# Ex9 Finding the Longest Length of Nested Set in a Permutation Array

## DATE: 

## AIM:
To write a program that finds the length of the longest set s[k] defined as  s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … }  
where the iteration stops before a duplicate element occurs. The task is to return the maximum size among all such sets.

## Algorithm
1. Start the program.  
2. Read the number of elements and the permutation array.  
3. Create a boolean `visited` array initialized to false.  
4. For each index `i` not yet visited, follow the chain `x = nums[x]`, marking visited elements and counting steps until revisiting; this gives the size of s[i].  
5. Track the maximum size encountered.  
6. Output the maximum size.  
7. Stop the program.

## Program:
```java
/*
Program to find the Longest Length of Nested Set in a Permutation Array

Developed by: MANIKANDAN T
RegisterNumber: 212224110037
*/

import java.util.*;
public class ArrayNestingMain {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine().trim();
        input = input.replace("nums =", "").replace("[", "").replace("]", "").trim();
        String[] parts = input.split(",");
        int[] nums = new int[parts.length];

        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }
        Solution sol = new Solution();
        int result = sol.arrayNesting(nums);
        System.out.println(result);
        sc.close();
    }
}
class Solution {
    public int arrayNesting(int[] nums) {
        int maxlen = 0;
        boolean[] visited = new boolean[nums.length];
        for (int i = 0; i < nums.length; i++) {
            if (!visited[i]) {
                int count = 0;
                int curr = i;
                while (!visited[curr]) {
                    visited[curr] = true;
                    curr = nums[curr];
                    count++;
                }
                maxlen = Math.max(maxlen, count);
            }
        }
        return maxlen;

    }
}
```
## OUTPUT
<img width="530" height="108" alt="image" src="https://github.com/user-attachments/assets/21bbfe63-b748-435a-b61e-30678a845de1" />


## RESULT
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
