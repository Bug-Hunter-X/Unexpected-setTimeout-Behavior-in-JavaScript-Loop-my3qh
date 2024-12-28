# Unexpected setTimeout Behavior in JavaScript Loop

This repository demonstrates a common issue in JavaScript related to closures and the `setTimeout` function within loops.  The code appears to iterate and log numbers 0-9 with a one-second delay.  However, due to the asynchronous nature of `setTimeout` and how closures work, it logs the final value of `i` (which is 10) ten times.

## Bug Description

The problem lies in the closure created by the `setTimeout` callback. By the time `setTimeout` finally executes the callback function, the `for` loop has already completed, and `i` is equal to 10.  Therefore, the callback always logs the value of `i` as 10.

## Solution

The solution involves using an immediately invoked function expression (IIFE) to create a new scope for each iteration of the loop, effectively capturing the correct value of `i` for each callback.