
The idea is pretty cool, and lets you do $a^b$ in $O(\log_{2}b)$ time.

So say you want to do something like 4^9.
So here 4 is your base, and 9 is your exponent.

The idea is to scale your base to match the current bit value of the exponent, and then multiply that to your result in case the current bit of the exponent is set.

So in this case:
I initially have `result = 1`, `base = 4`, `exponent = 9`

Now you are looking at the LSB of your exponent `1001`.
WOOT, it's 1. Multiply the result with the current base.
`result*=base`

Now scale the base for the next exponent bit.
`base = base * base`, So it's basically $4^2$ now.

Also `exponent = exponent >> 1`

Now again look at the LSB of your exponent `100`
Womp Womp, your computed base cannot be multiplied right now to the `result`, try again next time.
`exponent = exponent >> 1`
DONT FORGET TO SCALE YOUR BASE FOR THE NEXT EXPONENT
`base = base * base` So it's now $4^4$, which makes sense cause you'd be looking at the third bit from the right next.

Now again look at the LSB of your exponent `10`
Womp Womp, your computed base cannot be multiplied right now to the `result`, try again next time.
`exponent = exponent >> 1`
DONT FORGET TO SCALE YOUR BASE FOR THE NEXT EXPONENT
`base = base * base` So it's now $4^8$, which makes sense cause you'd be looking at the fourth from the right next.

Now again look at the LSB of your exponent `1`
WOOT, your computed base CAN be multiplied right now to the `result`.
`exponent = exponent >> 1`
`result*= result*base` = `4^1 * 4^8`
DONT FORGET TO SCALE YOUR BASE FOR THE NEXT EXPONENT 
`base = base * base` So it's now $4^16$, which makes sense cause you'd be looking at the fifth from the right next.

Oops you're out of exponent bits, and your answer is $4^9$ in $O(log_2(exponent))$ time!
Hurray!

Here's some python code that implements this, it's fast!
```python
import time
def fast_expo(base, expo, mod):
    result = 1
    base %= mod

    while expo > 0:
        if expo & 1:
            result = (result * base) % mod

        base = (base * base) % mod
        expo >>= 1

    return result


mod = 123456789

start = time.perf_counter()
ans = fast_expo(27, 1000000000, mod)
end = time.perf_counter()

print("time taken:", end-start)
print(ans)
```