---
layout: post
title: Why is lower_bound called lower_bound in C++
---

I just recently started to understand why `lower_bound` is called `lower_bound`
and `upper_bound` is called `upper_bound`. I will explain this in this article.

First, let's do a quick recap of the definitions of these two functions. The
function `lower_bound` is defined as "Returns an iterator pointing to the first
element in the range [first,last) which does not compare less than *val*" (See
[API reference](http://www.cplusplus.com/reference/algorithm/lower_bound/)). The
function `upper_bound` is defined as "Returns an iterator pointing to the first
element in the range [first,last) which compares greater than *val*" (See [API
reference](http://www.cplusplus.com/reference/algorithm/upper_bound/)).

![An illustration of lower_bound and
upper_bound](https://github.com/ttang235/ttang235.github.io/raw/master/images/lower_upper_bound_illustration.png)

In essence, lower_bound and upper_bound are both doing binary search. But why do
we need two functions for one algorithm?

The reason is simple: we have two boundaries for a given value and a sorted
array, as illustrated in the picture.

Formally, given a sorted array, and a value `val` you want to search for, the
array typically can be partitioned into 3 parts: `< val`, `== val`, and `> val`,
as illustrated in the picture above.

For binary search, the most important positions are the two boundaries, and from
the picture, it's obvious that one bound is *lower*, while the other is *upper*.
So I think that's why they're named as `lower_bound` and `upper_bound`.

When I initially came across these two functions, I often thought of the math
concept `lower bound` and `upper bound` (see
[wiki](https://en.wikipedia.org/wiki/Upper_and_lower_bounds)). Then I had a
question in mind: the returned iterator points to a lower bound? A lower bound
of what?

So the answer to this question is: lower_bound can be seen as a lower bound of
the `== val` part, and upper_bound can be seen as an upper bound of the `== val`
part. Now it makes sense, even in a mathematical sense.
