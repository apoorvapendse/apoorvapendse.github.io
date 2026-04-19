---
tags:
  - JavaScript
  - TIL
  - React
  - Redux
---
State management happens centrally, and state updates are immutable which lets you conveniently track history of the state of your application.

There's four/five main things:
- Dispatching actions (read below)
- Store (the central state of your application)
- Action (What UI interactions will dispatch to your store, so it can handle them)
- Reducers (What the store runs to update the state based on the actions dispatched)

The components that subscribe to certain parts of the store's state only re-render when that part changes.

> [!note]- Explanation  
> When you use the `useSelector` hook (or `connect` in older versions), Redux doesn't just re-render everything because the root state object changed. It follows this process:
>
>1. **Action Dispatched:** The reducer creates a **new** state object.
  >  
>2. **Notification:** Redux notifies all subscribers that "something changed."
  >  
>3. **The Selector Check:** Each component runs its selector function (e.g., `state => state.user`).
  >  
>4. **Reference Comparison:** The hook compares the **result** of that selector from the last render to the **new result** using `===`.

And then React Toolkit (RTK) introduces some nice abstractions, you break down your state  into slices, and can write code that appears to mutate the state, but actually doesn't, thanks to [Immer](https://immerjs.github.io/immer/).

Also, each slice exposes a single reducer, which acts like a wrapper reducer that wraps all those functions you define in the `reducers` list.


I like the idea that all state updates are immutable and you can "time travel", because you have the entire state history with you.

This sounds very similar to event sourcing, where you play your events to get to the current state, as my friend showell says, you basically get the ability to replay stuff "for free".
Actually it's in the other direction, but yeah.

The time travel concept sounds super powerful to me in terms of being able to debug stuff!