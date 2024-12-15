# React useEffect Infinite Loop Bug

This repository demonstrates a common error in React's `useEffect` hook: creating an infinite loop by incorrectly specifying the dependency array.

The `bug.js` file contains the buggy code.  The `bugSolution.js` file provides the corrected version.

## Problem

The `useEffect` hook is designed to perform side effects after a component renders.  However, if the dependency array is not properly managed, it can lead to unintended behavior, such as an infinite loop.

In this example, the `count` state is updated within the `useEffect` hook, which causes the component to re-render.  Since `count` is included in the dependency array, this triggers another update, resulting in an infinite render loop. 

## Solution

The problem is solved by removing `count` from the dependency array if the effect doesn't need to be run on every state update. If the effect is only supposed to run once after mount, use an empty array `[]` as dependency.