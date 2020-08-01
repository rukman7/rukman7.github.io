---
layout: post
title: Regular expressions basics
tags:
  - regular expressions
---
### Anchors
`^a` - Maches anything that starts after a.\
`$b` - Matches anything that ends with b.

### Ranges
* Ranges are described in square brackets `[]`
* Using `^` inside range bracets negates the character that follows.
	- Example: `[^7]` - Match everything except the number 7.
* `[A-Z]` - Matches characters that are one among A through Z. 
  - Example: `[A-Za-z]`

### Boundaries
* `\s` - Whitespace 
  - Example: `\sstark` -> Matches tony stark.
* `\b` - Word boundary
  - Example: 
    - `\bstark` -> Matches tony stark & tony-stark but not tonystark.
	- `\brobinhood\b` -> Matches robinhood but not robin or hood.
* Uppercase `\s` & `\b` negates its properties.

### Quantifiers
* Quantifiers specify how many of the previous characters are allowed.
* `b*` -> Matches b 0 or more times.
* `b?` -> Matches b 0 or once only(optional)
* `b+`  -> Matches one or more occurence of b.
* `b{3}` -> Matches exactly 3 occurences.
  - Example: uuu

* `.` -> Match any single character.
	
* Use `\` backslash to escape meta characters.
	
* `^$` - Matches empty lines.