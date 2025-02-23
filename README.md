# JavaScript Closure Issue in setTimeout Loop

This repository demonstrates a common JavaScript closure issue that arises when using `setTimeout` within a loop.  The expected behavior is to print numbers 0-9 sequentially after a one-second delay. However, due to the way closures work, the loop completes before the `setTimeout` callbacks execute, resulting in all callbacks logging the final value of `i` (which is 10). 

## Bug Description

The problem lies in the way the `setTimeout` callbacks capture the variable `i`.  They don't capture the value of `i` at the time of their creation; instead, they capture a reference to the variable `i`. By the time the `setTimeout` callbacks finally execute, the loop has already finished, and `i` is 10.

## Solution

The solution involves creating a new scope for each iteration of the loop using an immediately invoked function expression (IIFE) or a `let` variable inside the loop.