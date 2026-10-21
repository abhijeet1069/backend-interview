# Sliding Window

## Max Avg Subarray 1 - Sliding Window of fixed length

```java
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