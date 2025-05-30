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

```jsx
function Header() {
	return (<h1>Develop. Preview. Ship.</h1>);
}
root.render(<Header />);
```

**Nesting Components**

```jsx
function HomePage() {
	return <div>
		<Header />
	</div>;
}
```

**Component Trees**

![[Pasted image 20250516064215.png]]

Since `HomePage` is now the top-level component, you can pass it to the `root.render()`

```jsx
const root = reactDOM.createRoot(app);
root.render(<HomePage />);
```

**Using props**

Image you wanted possible variations of a button or you don't know the information ahead of time because you're fetching external data, you use **props**

```jsx
function Header({ title }) {
	return <h1>title</h1>
}

function HomePage() {
	return (
		<div>
			<Header title="React" />
		</div>
	);
}
```
- Pass a custom `title` prop to the `Header` component and in `Header` accept `title` as its first function parameter
- You can use object destructuring by explicitly naming the values of the props, e.g. `title`

**Using variables in JSX**

Writing JavaScript directly inside JSX markup

```jsx
function Header({ title }) {
	return <h1>{title}</h1>;
}
```

Adding JavaScript expression inside curly braces:

1. Object property with dot notation
```jsx
function Header(props) {
	return <h1>{props.title}</h1>;
}
```

2. A template literal
```jsx
function Header({title}) {
	return <h1>('Cool ${title}')</h1>;
}
```

3. Returned value of function
```jsx
function createTitle(title) {
	if (title) {
		return title;
	} else {
		return 'Default title';
	}
}

function Header({ title }) {
	return <h1>createTitle(title)</h1>;
}
```

4. Ternary operators
```jsx
function Header(title) {
	return <h1>{title ? title : 'Default Title'}</h1>;
}
```


**Iterating through lists**

```jsx
function HomePage() {
	const names = ["Warren", "Bob", "James]

	return (
		<div>
			<Header title="Temporary Title" />
			<ul>
				{names.map((name) => (
					<li key={name}>{name}</li>
				))}
			</ul>
		</div>
	);
}
```
- Use the `array.map()` method to iterate over the array and use the arrow function to map a name to a list item
- We can use names for now since unique, but if they are not, you should use an item ID

**Listening to Events**

```jsx
<button onClick={}>Like</button>
```
- Event names are `camelCased`
- `onClick` is used when the user clicks a button, `onChange` works for input fields and `onSubmit` for forms

**Handling Events**

```jsx
function HandleClick() {
	like += 1;
}
<button onClick={HandleClick}>Like</button>
```
- Define a function to "handle" events whenever they are triggered

**State and Hooks**

Definition
- Hooks add additional logic such as a state to your components
- A state is any information in your UI that changes over time, usually triggered by user interaction

```jsx
function HomePage() {
	const [likes, setLikes] = React.useState(0)
}
```
- `useState()` returns an array and you can access and use those array values inside your components using array destructuring
- First item in the array is the state `value` and second item in the array is a function to update the `value` 
- In this case, the initial value of likes i `0`

Checking initial state is working by using state variable

```jsx
<button onClick={handleClick}>Like({likes})</button>
```

State updater function

```jsx
function handleClick() {
	setLikes(likes+1)
}
```