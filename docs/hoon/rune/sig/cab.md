---
navhome: /docs/
next: true
sort: 5
title: ~_ "sigcab"
---

# `~_ "sigcab"`

`[%sgcb p=hoon q=hoon]`: user-formatted tracing printf.

## Expands to

`q`.

## Convention

Shows `p` in stacktrace if `q` crashes.

## Discussion

`p` must produce a `tank` (prettyprint source).

## Examples

```
~zod:dojo> ~_([%leaf "sample error message"] !!)
"sample error message"
ford: build failed

~zod:dojo> ~_  [%leaf "sample error message"] 
           !!
"sample error message"
ford: build failed
```
