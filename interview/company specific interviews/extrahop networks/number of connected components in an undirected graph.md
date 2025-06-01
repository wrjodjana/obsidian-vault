
>[!question]
>Given an undirected graph with n nodes, count the number of connected component
>You will be given an integer n representing total number of nodes and an array of edges
>where `edges[i] = [x, y]` representing that node x and y are connected
>Return an integer representing the number of connected components within the graph
>
>Example 1:
>Input n = 4, edges = `[[0, 1],[1,2],[2,3]]`
>Output: 1
>All nodes connected, so there is only 1 component
>
>Example 2:
>Input n = 4, edges = `[[0,1],[2,3]]`
>Output: 2
>0 1 are connected, and 2 3 are connected, so 2 components
****


Answer:
```Python
def countComponents(n, edges):
	graph = defaultdict(list)
	for x, y in edges:
		graph[x].append(y)
		graph[y].append(x)

	q = deque()
	visited = set()

	def bfs(root):
		q.append(root)
		visited.add(root)

		while q:
			node = q.popleft()
			for neighbor in graph[node]:
				if neighbor not in visited:
					q.append(neighbor)
					visited.add(neighbor)
	components = 0
	for i in range(n):
		if i not in visited:
			bfs(i)
			components += 1
	
```

