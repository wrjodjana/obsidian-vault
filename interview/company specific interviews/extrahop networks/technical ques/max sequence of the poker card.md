>[!question]
>Given a list of cards where each card has a suit ("H", "C", "D", "S") and rank ("1-10", "J", "Q", "K") we need to select the maximum number of cards such that each subsequent card picked has either the same suit (shape) or the same rank as the previous selected card.

**Questions:**
- If not said anything about joker, ask what happens to jokers?
- Can the same card appear multiple times, or just once?

**Approach:**
- Try every possible starting card, for each card find all the cards with the same suit/rank that hasn't been used yet
- Recursively explore each valid next card and continue the sequence from there
- Use dfs with backtracking meaning to fully explore one path, then backtrack by putting the card down and trying other possibilities
- Keep track of longest sequence found across all starting points and all paths


**Code:**
```Python
def maxSeq(cards):
	parsed_cards = []
	for card in cards:
		suit = card[0]
		rank = card[1:]
		parsed_cards.append((suit, rank))

	def valid(card1, card2):
		return card1[0] == card2[0] or card1[1] == card2[1]

	def dfs(last_idx, visited):
	
		max_length = 1
		for i in range(n):
			if i in visited:
				continue
			if valid(parsed_cards[last_idx], parsed_cards[i]):
				visited.add(i)
				length = 1 + dfs(i, visited)
				max_length = max(max_length, length)
				visited.remove(i)
		
		return max_length

	n = len(parsed_cards)
	res = 0
	visited = set()
	for i in range(n):
		visited.add(i)
		length = dfs(i, visited)
		visited.remove(i)
		res = max(res, length)

	return res
```

**Time/Space Complexity**
- Time Complexity: $O(n!)$ since the worst case is we explore all permutations of the card
- Space Complexity: $O(n)$ due to recursion stack depth and set storage

**Extension 1:** What if we must include a heart (at least two or three cards)?
```Python
def maxSeq(cards):
	parsed_cards = []
	for card in cards:
		suit = card[0]
		rank = card[1:]
		parsed_cards.append((suit, rank))

	def valid(card1, card2):
		return card1[0] == card2[0] or card1[1] == card2[1]

	def dfs(last_idx, visited):
	
		max_length = 1
		for i in range(n):
			if i in visited:
				continue

				if valid(parsed_cards[last_idx], parsed_cards[i]):
					visited.add(i)
					length = 1 + dfs(i, visited)
					max_length = max(max_length, length)
					visited.remove(i)
		
		return max_length

	n = len(parsed_cards)
	res = 0
	visited = set()
	for i in range(n):
		if parsed_cards[i][0] == "H":
			visited.add(i)
			length = dfs(i, visited)
			visited.remove(i)
			res = max(res, length)

	return res
```