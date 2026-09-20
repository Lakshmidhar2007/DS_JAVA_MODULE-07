# Ex9 Finding the Longest Length of Nested Set in a Permutation Array

## DATE: 20/09/2026

## AIM:

To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.

## Algorithm

1. Read the permutation array from the user.
2. Start from each index and follow the sequence using `nums[current]`.
3. Keep track of visited elements to stop when a duplicate element occurs.
4. Count the number of elements visited for each starting index.
5. Compare all counts and print the maximum length.

## Program:

```java
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: LAKSHMIDHAR N
RegisterNumber:  212224230138
*/

import java.util.*;

public class Main {

    static int arrayNesting(int[] nums) {
        int maxLength = 0;

        for (int i = 0; i < nums.length; i++) {
            boolean[] visited = new boolean[nums.length];
            int current = i;
            int count = 0;

            while (!visited[current]) {
                visited[current] = true;
                current = nums[current];
                count++;
            }

            maxLength = Math.max(maxLength, count);
        }

        return maxLength;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] nums = new int[n];

        for (int i = 0; i < n; i++)
            nums[i] = sc.nextInt();

        System.out.println(arrayNesting(nums));
    }
}
```

## Output:

<img width="440" height="150" alt="image" src="https://github.com/user-attachments/assets/77515f5c-8ff8-4b42-bce3-09b9a56b8eef" />


## Result:

The program successfully computes the longest length of the nested set s[k] for the given permutation array.
