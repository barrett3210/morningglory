---
layout: post
title:  "A fun example of Dart's fat arrow syntax"
description: "A fun example program that shows off Dart's fat arrow syntax."
date:   2018-06-19 15:57:32 -0700
tags:
  - "language features"
  - "shorthands"
  - "fat arrows"
  - "code examples"
---

The other day I gave you a [quick overview](/darts-simple-solution-to-one-source-of-programming-tedium) of Dart's *fat arrow* syntax.  Here's a fun example program I threw together that incorporates a whole bunch of `=>`s.  It's a program about a boat that docks at a port and picks up a random number of randomly-sized cargo boxes before continuing on its journey.

I wouldn't necessarily treat this code as *instructive*.  There are a few things in here I wouldn't normally condone.  For example, I always avoid ternary operations (`condition ? expressionA : expressionB`), since I feel regular `if`/`then` branching reads more clearly, particularly when any nesting is involved.  I'm only using a ternary operator here to show how compact *fat arrows* can make your code--in case that's the quality you want to optimize for.

<iframe src="https://dartpad.dartlang.org/embed-dart.html?id=7ef2b1d4a856b6fdfb6d1dec0f93537f&amp;horizontalRatio=80&amp;verticalRatio=60" width="100%" height="600px" style="border: 1px solid #ccc;">
</iframe>
