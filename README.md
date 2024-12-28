# useEffect Hook Runs on Every Render Despite Empty Dependency Array

This repository demonstrates a common misconception about the `useEffect` hook in React.  Even with an empty dependency array, the effect might run more often than expected if the component's state is updated within the effect itself, causing unnecessary re-renders.

## Bug Description

The `useEffect` hook is designed to perform side effects after a component renders.  However, if the component's state is updated within the effect, and the effect has an empty dependency array, an unexpected infinite loop can occur. This is because updating state triggers a re-render, which in turn triggers the `useEffect` hook again, leading to a continuous cycle.

## How to Reproduce

1. Clone this repository.
2. Run `npm install` to install dependencies.
3. Run `npm start` to start the development server.
4. Observe the console logs indicating that the effect runs on every click, even though the dependency array is empty. 

## Solution

To fix this issue, you have to avoid updating the state that caused the re-render inside the useEffect hook.