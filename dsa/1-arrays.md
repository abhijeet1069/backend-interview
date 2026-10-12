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

- [ ] 7. Merge Sorted Array — LC 88
- [ ] 8. Move Zeroes — LC 283
- [ ] 9. Remove Duplicates from Sorted Array — LC 26
- [ ] 10. Remove Element — LC 27
- [ ] 11. Squares of a Sorted Array — LC 977
- [ ] 12. 3Sum — LC 15
- [ ] 13. Container With Most Water — LC 11
- [ ] 14. Trapping Rain Water — LC 42
- [ ] 15. Sort Colors — LC 75
- [ ] 16. Rotate Array — LC 189
- [ ] 17. Majority Element — LC 169