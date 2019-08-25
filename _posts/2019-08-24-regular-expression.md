---
layout: post
title:  "Regular Expression"
date:   2019-08-24 22:40:00 -0400
author: Yingjie Song
categories: COMP2801
---
# Regular expression #

"A [regular expression][wiki], regex or regexp (sometimes called a rational expression) is a sequence of characters that define a search pattern."

[wiki]: https://en.wikipedia.org/wiki/Regular_expression

Metacharacter|Description
--|--
^|Matches the **starting position** within the string.
.|Matches **any single character**.
[ ]|Matches a single character that **is contained** within the brackets. For example, [0-9] specifies a range which matches any digits from 0 to 9. See [character classes][wiki-character-classes].
[^ ]|Matches a single character that is **not contained** within the brackets.
$|Matches the **ending position** of the string.
( )|Matches a **marked subexpression**.
*|Matches the preceding element **zero or more** times.
?|Matches the preceding element **zero or one** time.
+|Matches the preceding element **one or more** times.
{n}|Matches the preceding element **exactly _n_** times.
{min,}|Matches the preceding element at **least _min_** times.
{min,max}|Matches the preceding element at **least _min_ and not more than _max_** times.
\||The **choice** operator matches either the expression before or the expression after the operator.

# Examples #

## Numeral ##

```
[+-]?(\d+(\.\d+)?|\.\d+)([eE][+-]?\d+)?
```

### Analysis ###

Sign `[+-]?`

Base `(\d+(\.\d+)?|\.\d+)`

Exponent `([eE][+-]?\d+)?`

Same as `[0-9]`, `\d` matches any digit. See [character classes][wiki-character-classes].

[wiki-character-classes]: https://en.wikipedia.org/wiki/Regular_expression#Character_classes

## Time ##

```
([0-1][0-9]|2[0-3])(:[0-5][0-9](:[0-5][0-9])?)?
```