# Math and Number Theory

## Java primtive types and sizes

* int
    * size - 32 bits
    * Value Range -  -2,147,483,648 to 2,147,483,647 (-2^31 to 2^31-1)
    * Default value -  0

* long
    * size - 64 bits
    * Value Range -  -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 (-2^63 to 2^63-1)
    * Default value -  0L

* float
    * size - 32 bits
    * Value Range -  6-7 digits of precision
    * Default value -  0.0f

* double
    * size - 64 bits
    * Value Range -  15-17 digits of precision
    * Default value -  0.0fd

* char
    * size - 16 bits
    * Value Range -  0 - 65,535 (\u0000 to \uffff)
    * Default value -  \u0000

## Fast exponentation

```java
/*
Fast exponentiation (binary exponentiation) is an algorithm to calculate powers efficiently.

a^n = (a^(a/2))^2 ; if n is even
a^n = a*(a^(n-1/2))^2 ; if n is odd

This reduces number of operations from O(n) to O(log n)
 * **/
public class FastExponentiation {
	public long pow(long base, int exp) {
		long result = 1;
		while(exp > 0) {
			if(exp%2 == 1)
				result *= base;
			base*=base;
			exp /= 2;
		}
		return result;
	}
}
```

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