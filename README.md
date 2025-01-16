# React 19 useEffect Cleanup Function Returning True Causes Infinite Loop

This repository demonstrates a subtle bug in React 19 related to the `useEffect` hook's cleanup function.  The cleanup function unexpectedly returning `true` leads to an infinite loop. 

## Problem

A common pattern is to include a cleanup function in the `useEffect` hook to perform actions before the component unmounts or when dependencies change.   However, if this cleanup function returns `true` (instead of `undefined`), it causes unintended behavior by creating an infinite loop. This is because React interprets a truthy return value from the cleanup function as an indication that the component should continue to re-render. 

## Solution

The solution involves ensuring the cleanup function doesn't return any value (or returns undefined).  The cleanup function's purpose is to execute side effects to clean up resources; it shouldn't control re-rendering behavior.

## How to reproduce

1. Clone this repository.
2. Run `npm install` to install dependencies.
3. Run `npm start` to start the development server.
4. Observe the infinite loop in the console and the browser.