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
	1. Instead of moving one step at a time, the spiral follows a pattern where we move multiple steps in each direction
	2. Spiral moves in segments, 1 East, 1 North, 2 West, 2 South, 3 East, 3 North etc.
	3. Each direction has a specific number of steps before we turning and the number of steps increases in pairs: directions that are opposite of each other share the same step count
	4. Logic:
		1. Start with 1 step east, then we know how many steps we need to take in each direction before turning
		2. Instead of taking individual steps, calculate how many steps we take in the current direction, if we have enough steps remaining, we can move the entire segment length at once
		3. If there's not enough steps left to complete segment in current direction, we take only the remaining steps and stop
		4. After completing full segment, rotate to the next direction. Every time we complete two directions (East -> North or West -> South), we increase segment length for next pair of directions
3. Time/Space Complexity:
	1. Time Complexity: $O(\sqrt s)$ because the spiral completes roughly $\sqrt s$ full cycles before reaching $s$ steps since each cycle covers an increasing number of steps
	2. Space Complexity: $O(1)$ since no additional data structures are used and only using constant variables to track position, direction


Extensions:

Instead of assuming that you start at (0, 0) facing East, modify your function to // also accept an starting x coordinate, y coordinate, and direction

```Python
def spiral(s, start_x, start_y, start_direction):
	if s == 0:
		return (start_x, start_y)

	directions = [(1, 0), (0, 1), (-1, 0), (0, -1)]

	x, y = start_x, start_y
	direction = start_direction % 4
	steps_left = s

	steps_curr_direction = (start_direction // 2) + 1

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

	return (x, y)
```

```Python
def steps_to_pos(final_x, final_y):
	if final_x == 0 and final_y == 0:
		return 0

	directions = [(1, 0), (0, 1), (-1, 0), (0, -1)]

	x, y = 0, 0
	directions = 0
	steps_taken = 0
	steps_curr_direction = 1

	while True:
		dx, dy = directions[direction]

		if dx != 0:
			if dy == 0 and final_y == y:
				steps_needed = abs(final_x - x)
				if dx > 0:
					if final_x >= x and steps_needed <= steps_curr_direction:
						return steps_taken + steps_needed
				else:
					if final_x <= x and steps_needed <= steps_curr_direction:
						return steps_taken + steps_needed
		else:
			if dx == 0 and final_x == x:
				steps_needed = abs(final_y - y)
				if dy > 0:
					if final_y >= y and steps_needed <= steps_curr_direction:
						return steps_taken + steps_needed
				else:
					if final_y <= 
```






