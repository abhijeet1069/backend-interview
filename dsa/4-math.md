# Math and Number Theory

## Fast exponentation


## LC 412: Fizz Buzz

```java
/**
Given an integer n, return a string array answer (1-indexed) where:

answer[i] == "FizzBuzz" if i is divisible by 3 and 5.
answer[i] == "Fizz" if i is divisible by 3.
answer[i] == "Buzz" if i is divisible by 5.
answer[i] == i (as a string) if none of the above conditions are true.

Example 1:
Input: n = 3
Output: ["1","2","Fizz"]

Input: n = 15
Output: ["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]
*/

public List<String> fizzBuzz(int n) {
    List<String> list = new ArrayList<>();
    for(int i = 1; i <= n; i++){
        if(i%15 == 0) //this has to be priority 1, if it goes below, will never be executed
            list.add("FizzBuzz");
        else if(i%3 == 0)
            list.add("Fizz");
        else if(i%5 == 0)
            list.add("Buzz");
        else
            list.add(Integer.toString(i));
        }
    return list;
    }
```

## LC 7 : Reverse Integer

```java
/**
 * Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the 
 * value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).
 * 
Example 1:
Input: x = 123
Output: 321

Example 2:
Input: x = -123
Output: -321
 * 
*/

public int reverse(int num) {
    int reverse = 0;
    while(num != 0){
        int digit = num % 10;
        num /= 10;
        /**
        check if adding last digit causes overflow
        Integer.MAX_VALUE =  2147483647
        Integer.MIN_VALUE = -2147483648
        **/
        if (reverse > Integer.MAX_VALUE/10 ||
            (reverse == Integer.MAX_VALUE/10 && digit > 7))
                return 0;

        if (reverse < Integer.MIN_VALUE/10 ||
            (reverse == Integer.MIN_VALUE/10 && digit > 8))
                return 0;

        //this step increases the size of reverse so check before for overflow
        reverse = reverse*10 + digit; 
    }
    return reverse;
}
```

## LC 202: Happy Number

```java
/**
Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

Starting with any positive integer, replace the number by the sum of the squares of its digits.
Repeat the process until the number equals 1 (where it will stay), or it loops endlessly 
in a cycle which does not include 1.
Those numbers for which this process ends in 1 are happy.

Return true if n is a happy number, and false if not.

Example 1:
Input: n = 19
Output: true
Explanation:
1^2 + 9^2 = 82
8^2 + 2^2 = 68
6^2 + 8^2 = 100
1^2 + 0^2 + 0^2 = 1

Example 2:
Input: n = 2
Output: false
 * 
*/

public int reverse(int num) {
    int reverse = 0;
    while(num != 0){
        int digit = num % 10;
        num /= 10;
        /**
        check if adding last digit causes overflow
        Integer.MAX_VALUE =  2147483647
        Integer.MIN_VALUE = -2147483648
        **/
        if (reverse > Integer.MAX_VALUE/10 ||
            (reverse == Integer.MAX_VALUE/10 && digit > 7))
                return 0;

        if (reverse < Integer.MIN_VALUE/10 ||
            (reverse == Integer.MIN_VALUE/10 && digit > 8))
                return 0;

        //this step increases the size of reverse so check before for overflow
        reverse = reverse*10 + digit; 
    }
    return reverse;
}
```