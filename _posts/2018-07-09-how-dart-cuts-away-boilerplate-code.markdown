---
title: "How Dart cuts away boilerplate code"
layout: post
date: 2018-07-09 10:14:30
description: "Dart is designed to maximize your productivity by removing as much boilerplate code as possible."
tags:
  - "language features"
  - "shorthands"
  - "minimal boilerplate"
  - "saving time"
  - "easy refactoring"
---

When you think of the process of creating software, what image comes to mind?  If you've never actually written a substantial program before, you'd be forgiven for assuming it to be a fairly linear series of steps.  Perhaps it begins with an architect, who draws up specific plans for every aspect of the program.  Then it might be up to a team of developers to convert those plans into code.  The developers would probably need to communicate with one another to decide on which conventions to use, but as long as they stick to the architect's plan, development should be pretty straightforward.

If you're a software engineer yourself, no doubt this notion is striking you as laughably naïve.  The truth is that software engineering is never so well *contained*.  To be sure, planning is important, but plans inevitably shift.  Sometimes they shift from day to day; other times from minute to minute.  That's because it's impossible to understand precisely how a program will function until you actually try to implement it.  Software engineering is a constant struggle to make code accommodate new cases that were utterly inconceivable until they popped up *this morning*.  That's not to mention fixing bugs, adding features, or maintaining code over time and across changing teams.

What does all this mean for programmers?  It means that code needs to change--*a lot*.

## Malleability is key

The trouble with changing code is that it's costly, in terms of both time and effort.  The creators of [Dart](https://www.dartlang.org/) clearly know this, and they've designed their language to be as malleable as possible.  They've gone to great lengths to eliminate one of the most expensive aspects of changing software: boilerplate.  The more boilerplate you have to type when refactoring, the less likely you are to refactor.  When you're writing a program in Dart, you'll discover that you're spending less of your time reading, re-reading, and re-typing the same constructs again and again.  With these trivialities out of the way, your time is freed up to focus on the actual problems you're trying to solve.  In other words, Dart maximizes productivity by keeping the cost of change to a minimum.

## Embracing change

How about some examples?  Let's look at a few syntax features that help make refactoring in Dart practically painless.

### Parameter assignment in constructors

In object oriented languages, there's a very common pattern in many object constructors.  Any time a constructor accepts an argument, there's a good chance that argument will immediately be assigned to an instance variable.  Dart gives you a handy `this` shortcut when you're defining your constructors so that you don't need to type out `instanceVariable = argument;` every single time you accept one of these arguments.

```dart
Planet(this.name, this.mass, this.radius, this.orbitalPeriod);
```

Since all that this constructor does is assign arguments to instance variables, I didn't even have to define a method body!  Of course you could if you had extra work to do in the constructor.  But talk about a time saver!

*Update: Check out some example code [here](/dart's-constructor-syntax-in-action)!*

### Redirecting constructors

Sometimes a constructor's only purpose is to call another one of the class's constructors with specific arguments.  Dart doesn't make you write out a function body just for this purpose.  Instead you can use a redirecting constructor.

```dart
class Grid {
  int width;
  int height;

  Grid(this.width, this.height);

  Grid.tall(int height) : this(1, height);
  Grid.flat(int width) : this(width, 1);
}
```

### Fat arrows

I've already written a [post](/darts-simple-solution-to-one-source-of-programming-tedium) or [two](/a-silly-example-of-darts-fat-arrow-syntax) on Dart's *fat arrow* syntax.  It's a simple way to avoid typing (and more importantly, *reading*) the `return` keyword all over the place.

```dart
bool isEmpty => length == 0;
```

While this shorthand might not seem like such a big deal at first, the mental load it eliminates when you're refactoring becomes invaluable in the long run.

### Cascades

Another favorite feature of mine that I've [already covered elsewhere](/darts-cascade-syntax-will-change-your-life) is Dart's cascade syntax.  Cascades let you avoid repeating the same variable name line after line as you'd have to in most languages.  With all that repetition out of the way, it's much easier to focus on (and alter) the actual intent of your code.

```dart
var widget = new Widget()
  ..title = "Main widget"
  ..alignment = WidgetAlignment.centered
  ..width = 380.0
  ..height = 200.0
  ..color = new Color(1.0, 0.0, 1.0)
  ..addChildWidget(new SomeSubWidget())
  ..addChildWidget(new AlternateSubWidget())
  ..alignContents();
```

### Built in accessor methods

Accessor methods (*getters* and *setters*) are a language level feature in Dart.  Getters and setters are automatically defined for properties when you declare them, so you don't have to spend hours adding them (or *removing* them when you realize they're unused).  No more trivial `instanceVariable = assignedValue` methods cluttering up your classes.  If you need to define a formula for a getter or add extra functionality to a getter or setter, it couldn't be easier!

```dart
num get circumference => 2.0 * pi * radius;

set diameter(num value) => radius = value * 0.5;
```

### Classes, interfaces, and mixins

Inheritance is a staple of most object oriented languages.  It's also an important way to avoid code repetition and thereby save time--at least in theory.  Unfortunately, inheritance in many languages can also be a source of great confusion.  Different languages offer different schemes, some more convoluted than others (I'm looking at you, multiple inheritance).  Many languages offer concepts such as interfaces, abstract classes, and mixins.  All of these are powerful tools, but unfortunately it can be difficult to decide exactly which one to use for which purpose, particularly before you've actually implemented any of your class hierarchy.

Dart relies on single inheritance, arguably the simplest of inheritance schemes.  It does offer interfaces, abstract classes, and mixins as well, but with an important overhaul.  To define a class, of course, you use the `class` keyword.  To define an interface, you *also* use the `class` keyword.  To define a mixin, you **also** use the `class` keyword.  This distinction means that you don't always need to have the entire picture of how your class hierarchy will work before you can start building it out.  You might start implementing one set of methods as a class, but then learn that they make more sense as an interface or a mixin.  In Dart, restructuring functionality to fit a new model is a piece of cake.  Dart's concept of *implicit interfaces* means you can shift members freely from one structure to another.  Don't preoccupy yourself with the correct label for everything up front.  Boldly declare fields and methods in whichever class they fit best for now.  Rest assured that you'll be able to move them with ease later if needed.

## Hello, Dart.  Hello productivity!

The features I've outlined are just a few of the most effective boilerplate eliminators in Dart's arsenal.  In day-to-day use, you'll notice a plethora of fine touches and time-savers that I haven't listed here.  With all that boilerplate out of the way, you'll be able to focus on what's important: solving problems and shipping code quickly.  To get started with Dart, head over to the language's official [Language Tour](https://www.dartlang.org/guides/language/language-tour).  For more in-depth information on Dart, be sure to check out some of my [other articles](/archives).  Happy coding!
