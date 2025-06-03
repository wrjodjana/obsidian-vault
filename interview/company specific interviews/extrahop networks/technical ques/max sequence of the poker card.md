>[!question]
>Given a list of cards where each card has a suit ("H", "C", "D", "S") and rank ("1-10", "J", "Q", "K") we need to select the maximum number of cards such that each subsequent card picked has either the same suit (shape) or the same rank as the previous selected card.

**Questions:**
- If not said anything about joker, ask what happens to jokers?
- Can the same card appear multiple times, or just once?

**Approach:**
- Pick up one card, find a card with same suit/rank, then pick it up and recursively do this, until that path has been explored completely (backtracking) then put that card back down, repeat
- As I explore that path, keep note of the longest sequence so far


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
			
```