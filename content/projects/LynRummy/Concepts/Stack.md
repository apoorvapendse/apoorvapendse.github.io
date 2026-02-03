A stack is a collection of cards.
Stacks can have various states which are broadly categorized into two states:
1. Clean state
	1. A stack with a clean state belongs to one of the following types:
		1. **Pure run**
			1. A pure run stack contains cards of the same suit in sequence. They can also wrap around the ACE.
			2. Here are a couple examples from the main page of [Lyn Rummy](https://showell.github.io/LynRummy) as of writing:
			3. ![[Pasted image 20260203172246.png]]
		2. **Same set**
			1. A stack containing cards 3 or at max 4 with the same value from **different** suits is said to be of this type.
			2. Note how a same set stack can only have 4 cards at max, which is because of a special rule we like to call "No Dups!"; you cannot have cards from the same suit for a same set type of stack.
			3. Here are some examples for valid same set stacks:![[Pasted image 20260203173603.png]]
			4. An invalid same set case because of duplicates:![[Pasted image 20260203172646.png]]
		3. **Alternate run/ RED-BLACK run**
			1. A stack with an alternate run is same as a pure run but with cards belonging to suits of alternating color.
			2. ![[Pasted image 20260203173430.png]]