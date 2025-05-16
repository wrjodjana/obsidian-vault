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

In React, components are functions. Inside the `script` tag, create new function `header`

```js
function Header() {
	return (<h1>Develop. Preview. Ship.</h1>);
}
root.render(<Header />);
```

**Nesting Components**

```js
function HomePage() {
	return <div>
		<Header />
	</div>;
}
```

**Component Trees**

![[Pasted image 20250516064215.png]]

Since `HomePage` is now the top-level component, you can pass it to the `root.render()`

```js
const root = reactDOM.createRoot(app);
root.render(<HomePage />);
```

**Using props**

Image you wanted possible variations of a button or you don't know the information ahead of time because you're fetching external data, you use **props**

```js
function HomePage() {
	return (
		<div>
			<Header title="React">
			
	)
}
```