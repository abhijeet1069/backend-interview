# Sliding Window

## Max Avg Subarray 1 - Sliding Window of fixed length

```java
/**
Find a contiguous subarray whose length is equal to k that has the maximum average value 
and return this value. 

Input: nums = [1,12,-5,-6,50,3], k = 4
Output: 12.75000
Explanation: Maximum average is (12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75
*/
public double findMaxAverage(int[] nums, int k) {
    //window of fixed size, just slide over the array
    //initial window size
    int currSum = 0;
    for(int i = 0;i < k; i++)
        currSum += nums[i];
    
    int maxSum = currSum;
    for(int l = 1, r = k; r < nums.length; l++,r++){
        currSum = currSum - nums[l-1] + nums[r]; //exclude the previous element and include the next element
        if(currSum > maxSum)
            maxSum = currSum;
        }
    // average is directly proportional to sum, so we optimized for sum
    return (double)maxSum/k;
    }
```

## Longest Substring Without Repeating Characters - Sliding window of variable size


```java
/**
 * Given a string s, find the length of the longest substring without duplicate characters.
 * 
 * Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3. Note that "bca" and "cab" are also 
correct answers.
*/

public int lengthOfLongestSubstring(String s) {
        int l = 0;
        int maxLen = 0;
        Set<Character> set = new HashSet<>();
        for(int r = 0; r < s.length(); r++){

            while(set.contains(s.charAt(r))){ // reduce the window
                set.remove(s.charAt(l));
                l++;
            }
            set.add(s.charAt(r)); //increasing the window can come after also
            maxLen = Math.max(maxLen, r-l+1);
        }
        return maxLen;
    }
```

## Longest Repeating Character Replacement


```java
/**
 * You are given a string s and an integer k. You can choose any character of the string and 
 * change it to any other uppercase English character. You can perform this operation at most 
 * k times.

Return the length of the longest substring containing the same letter you can get after 
performing the above operations.

Input: s = "ABAB", k = 2
Output: 4
Explanation: Replace the two 'A's with two 'B's or vice versa.
 * 
*/

public int characterReplacement(String s, int k) {
    int[] freq = new int[26];
    int l = 0, maxFreq = 0, maxLen = 0;
    for(int r = 0;r < s.length(); r++){
        char c = s.charAt(r);
        freq[c-'A']++;
        maxFreq = Math.max(maxFreq,freq[c-'A']);
        while((r-l+1) - maxFreq > k){
            freq[s.charAt(l)-'A']--;
            l++;
        }
        maxLen = Math.max(maxLen,r-l+1);
    }
    return maxLen;
}
```

## Permutation in String

```java
/**
 * Return true if one of s1's permutations is the substring of s2.
 * 
 * Input: s1 = "ab", s2 = "eidbaooo"
Output: true
Explanation: s2 contains one permutation of s1 ("ba").
*/

public boolean checkInclusion(String s1, String s2) {
        if (s1.length() > s2.length())
            return false;

        int[] s1Freq = new int[26];
        int[] s2Freq = new int[26];
        
        //build initial frequency
        for (int i = 0; i < s1.length(); i++) {
            s1Freq[s1.charAt(i) - 'a']++;
            s2Freq[s2.charAt(i) - 'a']++;
        }

        if (Arrays.equals(s1Freq, s2Freq))
            return true;

        for (int l = 0, r = s1.length(); r < s2.length(); l++, r++) {
            s2Freq[s2.charAt(l) - 'a']--;
            s2Freq[s2.charAt(r) - 'a']++;

            if (Arrays.equals(s1Freq, s2Freq))
                return true;
        }
        return false;
    }
```

## Minimum Size Subarray Sum

```java
/**
Given an array of positive integers nums and a positive integer target, return the minimal length of a subarray whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.

Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.

Input: target = 11, nums = [1,2,3,4,5]
Output: 3
Explanation: The subarray [3,4,5] has the minimal length under the problem constraint.
*/
public int minSubArrayLen(int target, int[] nums) {
        int sum = 0, l = 0;
        int minlen=Integer.MAX_VALUE;
        for(int r = 0; r < nums.length; r++){
            sum += nums[r];
            while(sum >= target){
                minlen=Math.min(minlen,r-l+1);
                sum -= nums[l];
                l++;
            }
        }
        if(minlen == Integer.MAX_VALUE)
            return 0;
        else
            return minlen;
    }
```