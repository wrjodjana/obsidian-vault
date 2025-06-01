>[!question]
>It’s a nice afternoon, and you’re taking a walk in the park. You decide to walk in an outward,
>counter-clockwise spiral (shown below), starting facing East
>
>![[Screenshot 2025-06-01 at 1.34.48 AM.png | 200]]
>
>Given a number of steps s, calculate your position after s steps. Return the position as a 
>pair of coordinates (x, y) relative to your starting position (0, 0).
>Positive x represents East, Positive y represents North
>
>Example 1:
>Input: s = 0
>Output: (0, 0)
>
>Example 2:
>Input: s = 1
>Output: (1, 0)
>
>Example 3:
>Input: s = 2
>Output: (1, 1)

Answer:
```Python
def spiral(s):
	if s == 0:
		return (0, 0)

	directions = [(1, 0), (0, 1), (-1, 0), (0, -1)]
	
	x, y = 0, 0
	direction = 0
	steps_left = s
	steps_curr_direction = 1
	
	while steps_left > 0:
		steps = min(steps_left, steps_curr_direction)
		dx, dy = directions[direction]
		x += dx * steps
		y += dy * steps
		
		steps_left -= steps
		
		if steps == steps_curr_direction:
			direction = (direction + 1) % 4
			if direction % 2 == 0:
				steps_curr_direction += 1

	return (x,y)
```

Explanation:

1. Questions to ask:
	1. What should I return if s is negative?
	2. Are there any constraints on the maximum number of steps
2. Optimal Approach:
	1. Insights:
		1. 






