
What do you think would this result in:
```
Python 3.10.12 (main, Jan 26 2026, 14:55:28) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from urllib.parse import urljoin
>>> urljoin("https://foo.com/v1", "authorize")
```

Or perhaps
```python3
>>> urljoin("https://foo.com/v1", "/authorize")
```

> [!note]- Click to see answer  
> `https://foo.com/authorize`!!!

The actual way to do this to get the desired `https://foo.com/v1/authorize`, would be:

```
>>> urljoin("https://foo.com/v1/", "authorize")
```

The reason behind this can be found in [this section](https://datatracker.ietf.org/doc/html/rfc3986#section-5.2.3) of RFC 3986.

Particularly this bit of the merging algorithm:

>return a string consisting of the reference's path component
appended to all but the last segment of the base URI's path (i.e.,
excluding any characters after the right-most "/" in the base URI
path, or excluding the entire base URI path if it does not contain
any "/" characters).


I seriously want my hour back!