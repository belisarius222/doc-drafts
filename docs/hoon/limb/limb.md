---
navhome: /docs/
next: true
sort: 1
title: Limb
---

# Limb

`[%limb p=(each @ud [p=@ud q=@tas])]`: attribute of subject.

### Produces

If `p` matches `[%& p=@ud]`, slot `p.p` of the subject.

If `p` matches `[%| p=@ud q=@tas]`, the `p`th match for `q`,
using the search traverse below.

### Syntax

Irregular: `+15` is slot `15`, `[%& 15]`.

Irregular: `.` is slot `1`, the whole subject.

Irregular: `&4` is slot `30`, the 4th element of a tuple
with at least 5 elements.

Irregular: `|4` is slot `31`, the elements that follow `&4`. 

Irregular: `foobar` is `[%| 0 %foobar]`.

Irregular: `^^^foobar` is `[%| 3 %foobar]`.

Irregular: `+<-` is "take the tail, then take the head of
that, then the head of that." `+` and `>` mean "tail" while
`-` and `<` mean "head." This limb syntax starts on `+` or `-`
and alternates for readability. 

### Traverse

The search traverse takes a name `q` and a *skip count* `p`.

The search product may be an *arm* or a *leg*.  A *leg* is a
subtree of the subject.  An arm defines a Nock formula and a
subject leg to compute the result.  Logically, a limb is an
attribute -- computation or subtree, "synthesized" or "natural"
-- of the subject.

We search the subject type headfirst, depth-first, and pre-order.
If we descend to a `%face` type whose label matches the limb
symbol, the descent address is a leg.   The type is the type
beneath the label.  But if the `%face` label differs, the search
skips this whole subtree.

If we descend into a `%core` type in which the limb symbol is an
arm, we produce that arm.  If the limb symbol is not bound, we
descend into the payload (data) of the core.

If the skip count `p` is nonzero, we pretend our first `p`
matches are actually mismatches.  This lets the programmer "look
through" an overriding label.  No label anywhere is inaccessible.

### Examples

The Dojo prompt gives you a subject with a decent namespace.
Try

```
~zod:dojo> now
~2016.4.25..01.39.59..a0f0
```

You can also add variables to the subject, then use them.  (Note
that `=variable value` is not Hoon (language) syntax; it's Dojo
(shell) syntax.)

```
~zod:dojo> =foo %bar
~zod:dojo> foo
%bar
```
