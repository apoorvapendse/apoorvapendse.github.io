We very recently switched from a "reset" button to an "undo mistakes" button and the mechanism was pretty interesting.

**How the original reset worked:**
After every turn in LynRummy, we created a "snapshot" of the game state, which is just a giant serialized string containing the state of the Game, such as the player who was playing, the state of the Deck, the state of the board, etc.

A player pressing "Reset" would then deserialize this snapshot and load it in our Game data structure, followed by re-rendering all the DOM elements, which are basically the board/bookcase and the player hand.

The old version was introduced in [this commit](https://github.com/showell/LynRummy/commit/04e6c2b35b2598981c57fafc11a049a7647ee740)
Where the main crux was:
```ts
reset_moves_in_current_turn(): void {
    Object.assign(this, Game.deserialize(this.snapshot));
}
```

This however, isn't the most ideal from a player's perspective. The most helpful "reset" would be an "undo" move that takes them to the last clean state of the board.