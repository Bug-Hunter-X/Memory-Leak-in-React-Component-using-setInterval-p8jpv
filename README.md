# React setInterval Memory Leak
This repository demonstrates a common bug in React: a memory leak caused by using `setInterval` within a `useEffect` hook without proper cleanup.

The `bug.js` file shows the problematic code. The `bugSolution.js` file provides the corrected version.

## Bug
The bug lies in the `useEffect` hook of `MyComponent`.  `setInterval` starts a timer that increments the count every second. However, there's no mechanism to stop this timer when the component unmounts.  This leads to a memory leak and continues to update the count even after the component is no longer visible.

## Solution
The solution involves using the return value of `useEffect` to add a cleanup function. This function clears the interval when the component unmounts, preventing the memory leak.