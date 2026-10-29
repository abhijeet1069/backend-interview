# Foundations

## Time Complexity

Time complexity describes how an algorithm’s computational work grows with the input size.

It does not directly measure the actual time in seconds. Actual execution time depends on hardware, implementation, compiler optimizations, and other factors.

Common growth order:

* O(1) : Constant, Accessing arr[0]
* O(log n) : Logarithmic, Binary search
* O(n) : Linear, Traversing an array
* O(nlog n) : Linearithmic, Merge Sort 
* O(n^2) : Quadratic, Comparing every pair 
* O(n^3) : Cubic, Three nested loops 
* O(2^n) : Exponential, Recursive subset-generation algorithms 
* O(n!) : Factorial, Enumerating all permutations 

## Big-O notation — O(f(n))

Big-O describes an asymptotic upper bound on the growth of a function.

* Big-O is an upper bound, not necessarily a tight bound.
* It ignores constant factors and lower-order terms when describing asymptotic growth.
* In algorithm discussions, Big-O is often used to express worst-case complexity, 

## Big-Omega Notation — Ω(f(n))

Big-Omega describes an asymptotic lower bound on the growth of a function.

## Big-Theta Notation — Θ(f(n))

Big-Theta describes an asymptotically tight bound.



## Space Complexity

Space complexity describes how the memory requirements of an algorithm grow with input size.

It is important to distinguish between:

* Total space complexity: Memory used by the algorithm, including the input if the chosen 
    definition counts it.
* Auxiliary space complexity: Additional memory used by the algorithm, 
    excluding the input storage.

## Recursion

* A method calls itself to solve a smaller problem.
* Requires a reachable base case for termination.
* Recursive calls remain active until they return.
* Example: tree traversal, merge sort and backtracking.

## Iteration

* Repeats operations using loops.
* Often uses O(1) auxiliary space for simple traversals.
* Avoids recursive call-stack growth.

## Call Stack

* Tracks active method invocations.
* Follows LIFO: Last In, First Out.
* A method call creates a stack frame; returning removes it.
* Excessive stack usage can cause StackOverflowError.