---
title: "Dart's constructor syntax in action"
layout: post
date: 2018-07-10 11:56:04
description: "A quick example to demonstrate the efficiency of Dart's constructor syntax"
tags:
  - "language features"
  - "shorthands"
  - "minimal boilerplate"
  - "code examples"
---

In my [last post](/how-dart-cuts-away-boilerplate-code), I showcased Dart's efficient constructor syntax for assigning parameters to instance variables.  Today I'm giving you some short example code to work with so you can see just how quickly you can build out a new class in Dart.

## Constructors in most languages

In object oriented languages, there's a very common pattern in many object constructors.  Any time a constructor accepts an argument, there's a good chance that argument will immediately be assigned to an instance variable.  Take this example from Java.

```java
public Circle(float radius, float x, float y) {
  this.radius = radius;
  this.x = x;
  this.y = y;
}
```

## Constructors in Dart

By comparison, Dart gets out of your way.

```dart
Circle(this.radius, this.x, this.y);
```

That's super concise, but every bit as clear to read.  Notice that I didn't even provide a function body!  Since I've already defined types for `radius`, `x`, and `y` when I declared them as instance variables, there's no need to repeat type information here either.

Of course, if you need to do any work in your constructor beyond simple assignments, that's also possible.

```dart
Circle(this.radius, this.x, this.y) {
  var area = pi * pow(radius, 2.0);
  print("Created new Circle with area of $area");
}
```

## Example code

Give it a try for yourself!  Try changing the `City` class to add new instance variables.  Assign them directly in the constructor definition with the `this.instanceVariable` syntax.

<iframe src="https://dartpad.dartlang.org/embed-dart.html?id=3946ab2083f0023991d391d571f9e995&amp;horizontalRatio=80&amp;verticalRatio=60" width="100%" height="500px" style="border: 1px solid #ccc;">
</iframe>
