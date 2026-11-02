# Math and Number Theory

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