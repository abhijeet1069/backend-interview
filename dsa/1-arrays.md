## Arrays

I am noticing that Leetcode is all about finding patterns. And read questions in between
the lines. Purposefully, it will make you deviate. 

## 1. Two Sum — LC 1

```java
/**
 * You are given an array of integers nums and an integer target, return indices of the 
 * two numbers such that they add up to target.
 * 
 * Input: nums = [2,7,11,15], target = 9
   Output: [0,1]
   Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
**/
public int[] twoSum(int[] nums, int target) {
    Map<Integer,Integer> posMap = new HashMap<>();
    posMap.put(nums[0],0);
    for(int i = 1; i < nums.length; i++){
        int complement = target - nums[i];
        //this is the optimisation, its finding complement of already visited elements
        //not on complete array
        if(posMap.containsKey(complement)) 
            return new int[]{i,posMap.get(complement)};
            posMap.put(nums[i],i);
        }
        return new int[]{};
    }
```

## 2. Best Time to Buy and Sell Stock — LC 121

```java
/**
You are given an array prices where prices[i] is the price of a given 
stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and 
choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot 
achieve any profit, return 0.

Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
*/
public int maxProfit(int[] prices) {
    int buy = prices[0];
    int profit = 0;
    for(int i = 1; i < prices.length; i++){
        int sell = prices[i];
        //optmisation : reduce the buying cost and increase the profit
        //use sell as the pointer that traverses array
        profit = Math.max(profit,sell-buy);
        buy = Math.min(buy,prices[i]);
    }
    return profit;
}
```

## 3. Contains Duplicate — LC 217

First intuition is to use a HashMap and check count, but its a wrong abstraction. 
Used a HashSet and running time reduced to half. If you read carefully, this problem 
is essentially checking membership, but disguising itself as counting.

```java
/**
Given an integer array nums, return true if any value appears at least twice 
in the array, and return false if every element is distinct.
 
Input: nums = [1,2,3,1]
Output: true
   
Input: nums = [1,2,3,4]
Output: false

Explanation:
The element 1 occurs at the indices 0 and 3.
 * 
*/

public boolean containsDuplicate(int[] nums) {
    //optimisation is using HashSet, at first it feels its a HashMap question
    // but this is asking membership not count
    Set<Integer> set = new HashSet<>(); 
    for(int num : nums){
        if(set.contains(num))
            return true;
        set.add(num);
        }
    return false;
    }
```

## 4. Product of Array Except Self — LC 238

```java
/**
Given an integer array nums, return an array answer such that answer[i] is equal 
to the product of all the elements of nums except nums[i].

(hint->) The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

Input: nums = [1,2,3,4]
Output: [24,12,8,6]

Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
*/
public int[] productExceptSelf(int[] nums) {
        //no need of separate prefix[] and suffix[],
        // in one prod[] job can be done, as prefix calculated first then suffix
        int[] prod = new int[nums.length];
        prod[0] = 1;
        for(int i  = 1; i < nums.length; i++)
            prod[i] = prod[i-1]*nums[i-1]; //till here prod has prefix sum

        int suff = 1;
        for(int i = nums.length-1; i >= 0; i--){
            prod[i] *= suff;
            suff *= nums[i]; //no need of suff[] only single variable is enough
        }
        return prod;
    }
```
## 5. Maximum Subarray — LC 53

Kadane Algorithm - finds max subarray

```java
/**
 * Given an integer array nums, find the subarray with the largest sum, and 
 * return its sum.
 * 
Example 1:
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.
 * 
*/
public int maxSubArray(int[] nums) {
    int currSum = nums[0];
    int maxSum = nums[0];
    for(int i = 1; i < nums.length; i++){
        //at each stage we are asking to extend subarray, or to start a fresh one
        currSum = Math.max(currSum+nums[i],nums[i]);
        maxSum = Math.max(maxSum,currSum);
    }
    return maxSum;
    }
```

## 6. Maximum Product Subarray — LC 152

```java
/**
 * Given an integer array nums, find a subarray that has the largest product, and return the product.
 * 
 * Input: nums = [2,3,-2,4]
   Output: 6
   Explanation: [2,3] has the largest product 6.
*/
public int maxProduct(int[] nums) {
    int minProd = nums[0];
    int maxProd = nums[0];
    int result = nums[0];
    for(int i = 1; i < nums.length; i++){
        //property of negative numbers, flips the whole scene
        //make largest number to smallest and smallest to largest
        if(nums[i] < 0){
            int temp = maxProd;
            maxProd = minProd;
            minProd = temp;
        }
        maxProd = Math.max(maxProd*nums[i],nums[i]);
        minProd = Math.min(minProd*nums[i],nums[i]);
        result = Math.max(result,maxProd);
        }
        return result;
    }
```

## 7. Merge Sorted Array — LC 88

```java
/**
    * You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers
     * m and n, representing the number of elements in nums1 and nums2 respectively.
     *
     * The final sorted array should be stored inside nums1[]
     * 
     * Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
        Output: [1,2,2,3,5,6]
     */

    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int[] res = new int[m+n];
        int index = 0, i = 0, j = 0;
        while(i < m && j < n){ //run till the shorter array
            if(nums1[i] < nums2[j]){
                res[index] = nums1[i];
                i++;
            }
            else{
                res[index] = nums2[j];
                j++;
            }
            index++;
        }

        while (i < m){ //remaining first array
            res[index] = nums1[i];
            i++;
            index++;
        }

        while (j < n){ //remaining second array
            res[index] = nums2[j];
            j++;
            index++;
        }
        for(int k = 0;k < m+n; k++)
            nums1[k] = res[k];
    }
```

## 8. Move Zeroes — LC 283

```java
/**
Given an integer array nums, move all 0's to the end of it while maintaining the 
relative order of the non-zero elements. (in-place)

Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
*/

public void moveZeroes(int[] nums) {
        int j = 0;
        for(int i = 0;i < nums.length; i++){
            if(nums[i] != 0){
                nums[j] = nums[i];
                j++;
            }
        }
        //put remaining array to 0
        while(j < nums.length){
            nums[j] = 0;
            j++;
        }
    }
```

## 9. Remove Duplicates from Sorted Array — LC 26

```java
/**
Given an integer array nums sorted in non-decreasing order, remove the duplicates 
in-place such that each unique element appears only once. The relative order of the 
elements should be kept the same.
*/

public int removeDuplicates(int[] nums) {
        int index = 1;
        for(int i = 1;i < nums.length; i++){
            if(nums[i] != nums[index]){
                index++;
                nums[index] = nums[i];
            }
        }
        return index;
    }
```

## 10. Remove Element — LC 27

```java
/**
 * Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. 
 * The order of the elements may be changed. Then return the number of elements in nums which are
 *  not equal to val.
 * 
 * Input: nums = [3,2,2,3], val = 3
   Output: 2, nums = [2,2,_,_]
 * 
*/

public int removeElement(int[] nums, int val) {
    int usefulElementCount = 0;
    for(int i = 0; i < nums.length; i++){
        if(nums[i] != val){
            nums[usefulElementCount] = nums[i];
            usefulElementCount++;
        }
    }
        return usefulElementCount;
    }
```

### 11. Squares of a Sorted Array — LC 977

```java
/**
 * Given an integer array nums sorted in non-decreasing order, return an array of the squares of 
 * each number sorted in non-decreasing order.
 * 
 * Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
 * 
*/

public int[] sortedSquares(int[] nums) {
    int[] squares = new int[nums.length];
    int l = 0, r = nums.length-1;
    int index = nums.length-1;
    while(l <= r){
        if(Math.abs(nums[l]) > Math.abs(nums[r])){
            squares[index] = nums[l]*nums[l];
            l++;
        }
        else{
            squares[index] = nums[r]*nums[r];
            r--;
        }
        index--;
        }
        return squares;
    }

```

## 12. 3Sum — LC 15

```java

/**
 * Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] 
 * such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.

Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
 * 
*/

public List<List<Integer>> threeSum(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    Arrays.sort(nums);

    for(int i = 0;i < nums.length-2; i++){
        if(i > 0 && nums[i] == nums[i-1])
            continue;

        int left = i+1;
        int right = nums.length-1;

        while(left < right){
            int sum = nums[i] + nums[left] + nums[right];
            if(sum == 0){
                result.add(Arrays.asList(nums[i],nums[left],nums[right]));
                
                while(left < right && nums[left] == nums[left+1]) //skip duplicates
                    left++;
                
                while(left < right && nums[right] == nums[right-1])
                    right--;
                
                left++;
                right--;
                }

            else if(sum < 0)
                left++;
                
            else
                right--;
            }
        }
        return result;
    }

```

## 13. Container With Most Water — LC 11

```java
/**
 * You are given an integer array height of length n. There are n vertical lines drawn such 
 * that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container 
contains the most water.

Return the maximum amount of water a container can store.

Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, 
the max area of water (blue section) the container can contain is 49.
 * 
*/

public int maxArea(int[] height) {
    int l = 0, r = height.length-1, max_area = -1, curr_area = 0;
    while(l < r){
        if(height[l] <= height[r]){
            curr_area = (r-l)*height[l];
            l++;
        }
        else{
            curr_area = (r-l)*height[r];
            r--;
        }
        if(max_area < curr_area)
            max_area = curr_area;
        }
        return max_area;
    }
```

## 14. Trapping Rain Water — LC 42

```java
/**
Given n non-negative integers representing an elevation map where the width of each bar is 1, 
compute how much water it can trap after raining.

Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. 
In this case, 6 units of rain water (blue section) are being trapped.
*/

// For every position:

// 1. Find the tallest wall to its left.
// 2. Find the tallest wall to its right.
// 3. Calculate how much water that position traps.
// 4. Add it to the total.
public int trap(int[] height) {
    int[] l = new int[height.length];
    int max = height[0];
    for(int i = 1; i < height.length; i++){
        if(max > height[i])
            l[i] = max;
        else
             max = height[i];
        }

    int[] r = new int[height.length];
    max = height[height.length-1];
    for(int i = height.length-2; i >= 0; i--){
        if(max > height[i])
            r[i] = max;
        else
            max = height[i];
        }

        int[] res = new int[height.length];
        for(int i = 0;i < height.length; i++){
            //The water level at any position is determined by the shorter of the tallest 
            // walls on its left and right.
            int water = Math.min(l[i],r[i])-height[i];
            if(water < 0)
                res[i] = 0;
            else
                res[i] = water;
        }

        int sum = 0;
        for(int x : res)
            sum += x;

        return sum;
    }
```


## 15. Sort Colors — LC 75

```java
/**
 * You are given an array nums with n objects colored red, white, or blue, sort them in-place 
 * so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.

Input: nums = [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]

Explanation:
The array has two 0s, two 1s, and two 2s. Sorting them in-place places all 0s first,
then all 1s, then all 2s.
*/

public void sortColors(int[] nums) {
    int[] counts = new int[3];
    for(int num : nums)
        counts[num]++;

    int index = 0;
    for(int i = 0; i < 3; i++){
        for(int j = counts[i]; j > 0; j--){
            nums[index] = i;
            index++;
        }
    }
}
```

- [ ] 16. Rotate Array — LC 189
- [ ] 17. Majority Element — LC 169