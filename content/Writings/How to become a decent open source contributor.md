---
title: How to become a decent open source contributor?
tags:
  - thoughts
  - advice
  - open-source
---
(This is still WIP)
After contributing to around half a dozen open source projects since the last couple years, I have a decent grasp on qualities that make a good and easy-to-work-with open source contributor.

Zulip's [How to be a successful contributor](https://zulip.readthedocs.io/en/latest/contributing/contributing.html#how-to-be-a-successful-contributor) is another great read on this topic.


Here are some of my learnings in no particular order:
### Get familiar with the org and its ways.
- The documentation is your best friend here. Some useful pointers would be:
	- Look at how maintainers prefer the commits to be written, do they use a rebase-based workflow or a merge-based workflow?
	- What are the best places to ask questions?
	- What is the way to get an issue assigned? 
	- What are the steps required to make your work reviewable?
	- Where can you report issues or propose an idea?
- The general aim as a new contributor should to become familiar with the traditional workflows and the way an organization "rolls".
- The bottom line is you have to act like you are already part of the project since day one.

### Save maintainer effort and time!
- As a new contributor, your goal must be to make your contributions as easy as possible to review and understand.
- This doesn't mean a copy pasting verbatim summary of the code changes you've introduced by just piping your diffs to an LLM (or much worse, generating both the diffs and the summary with the help of an LLM).
- You should instead specify the potential tradeoffs your approach might have, some spots you are unsure about or anything that could use extra attention or advice from an experienced reviewer.
- **The maintainers don't owe you anything, especially their valuable time they could've spent reviewing other useful work for the project. Always keep that in mind!**