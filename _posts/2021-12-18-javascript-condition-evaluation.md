---
layout: post
title: Rules to keep in mind while using if statement in javascript
tags:
  - javascript
---
## Evaluation of different data types in javascript

* `Objects` evaluate to `true`
* `Undefined` evaluates to `false`
* `Null` evaluates to `false`
* `Booleans` evaluate to the value of the boolean
* `Numbers` evaluate to `false` if `+0, -0, or NaN`, otherwise `true`
* `Strings` evaluate to `false` if an empty string `''`, otherwise `true`
* `Arrays` (whether empty or not ex: `[] or [0]`) evaluates to `true` as array is an object

## Prefer strict comparison over loose comparison

  It is better to use strict comparison(===) over loose comparison(==) as the strict comparison does not do any coercion.

  <u>Coercion</u>: Coercion in javascript refers to the process of automatic or implicit conversion of values from one data type to another.


## References

[Airbnb style guide](https://github.com/airbnb/javascript#:~:text=and%20!%3D.%20eslint%3A%20eqeqeq-,15.2,-Conditional%20statements%20such) \
[Comparison in javascript](https://www.sitepoint.com/javascript-truthy-falsy/)