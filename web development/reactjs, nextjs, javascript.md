
**DOM**
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
const headerContent = document.
```