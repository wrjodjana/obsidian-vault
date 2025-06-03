>[!question]
>It’s a nice afternoon, and you’re taking a walk in the park. You decide to walk in an outward,
>counter-clockwise spiral (shown below), starting facing East!
>
>![[Screenshot 2025-06-03 at 11.43.04 AM.png|200]]
>
>Given a number of steps s, calculate your position after s steps. Return the position as a pair of coordinates (x, y) relative to your starting position (0, 0).
>Positive x represents East, Positive y represents North

**Questions**
- Is s always going to be non negative
- Any constraints on maximum number of steps?

**Approach**
- Go through the spiral, look at pattern (1 East, 1 North, 2 West, 2 South, 3 East, 3 North, 4 West, 4 South)
- Clearly see theres a pattern with the direction and also like the length we go each time
- So in our algorithm, we take into account the current direction, the current length everytime, and the number of steps we basically have left to complete the spiral

**Code:**
```Python
def spiral(steps):
	if steps == 0:
		return (0, 0)

	directions = [(1, 0),(0, 1), (-1, 0), (0, -1)]

	x, y = 0, 0
	curr_dir = 0
	curr_len = 1
	steps_left = steps

	while steps_left > 0:
		curr_steps = min(steps_left, curr_len)
		dx, dy = directions[curr_dir]
		x += (dx * curr_steps)
		y += (dy * curr_steps)
		steps_left -= curr_steps

		curr_dir = (curr_dir+1) % 4

		if curr_dir % 2 == 0:
			curr_len += 1

	return (x, y)
```

**Time/Space Complexity:**
- Time Complexity: $O(\sqrt n)$ because each iteration processes on segment, and these grow as the pattern, for n steps and k segments, we need $\frac{k^2}{2}$ or $k = \sqrt (2n)$ 
- Space Complexity: $O(1)$ since we're not using any additional data structure and the other variables are constant space

**Extension 1:** Instead of assuming that you start at (0, 0) facing East, modify your function to also accept an starting x coordinate, y coordinate, and direction

```Python

```
