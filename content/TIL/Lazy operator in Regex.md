---
tags:
  - TIL
  - debugging
  - regex
date: 27 Mar 2026
---

Here's a basic example of what I was trying to do today.
```bash
echo "good gourd guard" | grep -Po "g.+d"
```

The end goal was to get three matches, namely `good`, `gourd` and `guard`.
However, this regular expression returned the whole string as a match, that is `good gourd guard`.

So 
```bash
❯ echo "good gourd guard" | grep -Po "g.+d"  
good gourd guard
```

This is where the lazy operator (?) comes in.
By default the matching is greedy, meaning the regex engine tries to gobble up everything it can into a single match.
Whereas, by adding the `?` lazy operator, you can switch the behavior, so it takes the minimum amount of characters required to form a valid match.

So
```bash
❯ echo "good gourd guard" | grep -Po "g.+?d"  
good  
gourd  
guard
```
Gives  the expected three matches.

> [!info]  
> The usual `-E` flag uses Extended Regular Expressions (POSIX), which **does not support lazy quantifiers**. Which is why I had to use `-P` which denotes Perl-Compatible Regular Expressions that does seem to support it.


