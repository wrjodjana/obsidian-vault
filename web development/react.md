**Getting started with react**

Rendering the `<h1>` element but in React

```js
const app = document.getElementById("app")
const root = ReactDOM.createRoot("app")
root.render(<h1>Develop. Preview. Ship.</h1>)
```

How it works:
1. Add the `ReactDOM.createRoot` method to target a specific DOM element and create a root to display react components in
2. Add the `root.render()` method to render the react code to your DOM

**JSX**
- Syntax extension for JavaScript that allows you to describe your UI in a familiar HTML syntax
- However, browsers don't understand JSX so you need **Babel** as a JavaScript compiler

**Components**

