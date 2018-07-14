---
layout: post
title:  "Dart's simple solution to one source of programming tedium"
description: "Dart has a simple shorthand that keeps your short function declarations clean and easy to read."
date:   2018-06-17 13:24:09 -0700
tags:
  - "shorthands"
  - "language features"
  - "shorthands"
  - "fat arrows"
---

Although we developers like to think of ourselves as craftsmen, artists, and deep-thinking problem-solvers, the truth is that any software engineer's job involves a fair bit of tedium.  Whether you're working on web, server, mobile, or game development, it's inescapable.  From time to time, you're going to run into code that is monotonous, frustrating, and downright *boring* to deal with.  Some of this problem may be inherent to computer science, but often it stems from a lack of forethought in the tools and processes we use to build software.

One of my favorite things about [Dart](https://www.dartlang.org/) is that it does so much to counteract the cumbersome aspects of the programming process.  The authors of the language have clearly put a great deal of thought into every detail of its syntax in order to maximize developer productivity.  One important way that they accomplish this is by providing simple shortcuts developers can take to avoid the most lackluster parts of writing code.  Individually these shorthands and strategies may not seem like much, but taken together they make developing in Dart downright *fun*.

## One way most languages become tiresome

Have you ever written a function or two that looked something like these?

```javascript
// ...

function hasGizmo(xIndex, yIndex) {
  return gizmoRows[yIndex][xIndex] != null;
}

function applyOffset(baseAmount) {
  return offset + baseAmount;
}

function whisper(phrase) {
  print(phrase.toLowerCase());
}

function findMatches(criterion) {
  return [];
}

function canCatchWombat(wombat) {
  return true;
}

// ...
```

The thing these functions all have in common is that they're *one-liners*.  You might be tempted to move the curly braces onto the same line for the sake of saving space.

```javascript
function canCatchWombat(wombat) {return true;}
```

That's arguably better--as long as it doesn't violate any style conventions you may be operating under.  Still, it doesn't read particularly clearly, especially with the `return` keyword taking up so much space and interrupting the expression of your intent.  The `;}` at the end also looks particularly awkward.

## Dart's handy solution: fat arrows

Fortunately, Dart lets you do this:

```dart
bool hasGizmo(int xIndex, int yIndex) => gizmoRows[yIndex][xIndex] != null;

num applyOffset(num baseAmount) => offset + baseAmount;

void whisper(String phrase) => print(phrase.toLowerCase());

List findMatches(String criterion) => [];

bool canCatchWombat(Wombat wombat) => true;
```

It might take you a few minutes to become acclimated to this shorter way of expressing your thoughts, but by the time you've written an entire program using this shorthand, you'll never want to go back.

The `=>` syntax only works with functions containing a single expression, but if you think about it, anything longer would be more clearly written on multiple lines anyway.  And in typical situations where the compiler can figure out what types are expected but where brevity may be important--for example, when you're defining a short closure--you can omit the type annotations altogether.

```dart
addWombatHandler((wombat) => true);
```

Look how sleek that is!  Dart gets its syntax out of your way so that you can focus on what's important: the actual intent of your program.  It's amazing how much such a simple feature on the language level can improve the readability of your program's code.

## Example code

If you're interested in seeing some of the *fat arrow* syntax in action, I threw together a silly example program which you can see and mess around with [here](/a-silly-example-of-darts-fat-arrow-syntax).
