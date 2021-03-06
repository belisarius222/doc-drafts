---
navhome: /docs/
sort: 8
title: %_ "cencab"
---

# `%_ "cencab"`

`[%cncb p=wing q=(list (pair wing hoon))]`: take a wing with changes,
preserving type.

## Expands to

```
^+(p %=(p q))
```

## Syntax

Regular: *1-fixed*, then *jogging*.

## Discussion

`%_` ("cencab") is different from `%=` ("centis") because `%=` 
can change the type of a limb with mutations.

## Examples

```
~zod:dojo> =foo [p=42 q=6]
~zod:dojo> foo(p %bar)
[p=%bar q=6]
~zod:dojo> foo(p [55 99])
[p=[55 99] q=6]
~zod:dojo> %_(foo p %bar)
[p=7.496.034 99]
~zod:dojo> %_(foo p [55 99])
! nest-fail
```
