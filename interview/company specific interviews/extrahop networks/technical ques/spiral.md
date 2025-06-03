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
- 
