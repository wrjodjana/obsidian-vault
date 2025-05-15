

**DOM** **(Document-Object Model)**
- object representation of the HTML elements
- acts as a bridge between your code and the user interface and has a tree-like structure with parent and child elements

![[Pasted image 20250515113553.png]]

**Updating UI with JavaScript**

HTML Code:
```html
<html>
	<body>
		<div id="app"> </div>
		<script type="text/javascript">
		</script>
	</body>
</html>
```


Under Script:
```js
const app = document.getElementById("app");
const header = document.createElement("h1");
const text = 'Develop. Preview. Ship.';
const headerContent = document.createTextNode(text);
app.appendChild(header)
```

Explanation:
1. Select div element with "app" id
2. Create a new h1 element
3. Create a new text node for the h1 element
4. Append the text to the h1 element
5. Place h1 element inside div

However this shit is so bad because how tf r u writing all that for just an `<h1>` element

**Imperative vs Declarative Programming**

Imperative programming is when you write the steps for how the user interface should be updated w