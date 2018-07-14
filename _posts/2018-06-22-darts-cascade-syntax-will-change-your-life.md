---
layout: post
title:  "Dart's cascade syntax will change your life"
description: "Dart offers a powerful programming shorthand called cascades that saves you time and keeps your code clean."
date:   2018-06-22 11:09:02 -0700
tags:
  - "language features"
  - "shorthands"
  - "cascades"
  - "code examples"
---

If you've been working with code for a while--in any language--no doubt you've run into a situation like this:

```dart
var alertBox = new AlertBox();
alertBox.title = "What is your favorite animal?";
alertBox.style = AlertBoxStyle.bold;
alertBox.addOption("Iguana");
alertBox.addOption("Capybara");
alertBox.addOption("Trout");
alertBox.addOption("Goldfinch");
alertBox.addOption("Other");
alertBox.x = 250.0;
alertBox.y = 120.5;
alertBox.show();
```

Notice how many times I've repeated the name `alertBox` in that snippet.  Isn't repeated code one of the deadly sins of software development?  I know a repeated variable name isn't quite the same as repeated functionality, but it still gets in the way, adds to your cognitive load, and limits your flexibility when you need to refactor.  Surely there must be some cleaner way it could be written.

## Problematic in most languages

Perhaps we can make a *few* improvements by changing the `AlertBox` class.  We could implement an `addOptions` method that accepts an array of option strings.  That would eliminate a few repetitions.  We might also be able to add arguments to the constructor to set certain properties there.  And maybe we could make the `x` and `y` properties into a single `Vector2`, so that we can set the coordinates with a single call.  But all this is assuming that `AlertBox` is a class we're writing ourselves.  If we don't have the ability to change it, we're out of luck.  Even if we do, there may be other factors limiting our ability to rewrite it.  And all these changes only mitigate the problem of name repetition; they won't completely eliminate it.

On top of everything else, let's not forget that reorganizing a class requires a fair amount of work.  We shouldn't let that stop us from improving our code, but we also need to be realistic about the costs of refactoring: time, energy, and the possibility of introducing bugs.  The truth of the matter is that sometimes repeating a variable name ten times in a row really is the most straightforward way to accomplish a given task.  If only there were a way to eliminate the repetitions without touching the class's code.  I can imagine one, but it would have to be built into the language...

## Clean cascades in Dart

*Tada!*  In Dart, you can write the above snippet (functionally equivalent) like this:

```dart
var alertBox = new AlertBox()
  ..title = "What is your favorite animal?"
  ..style = AlertBoxStyle.bold
  ..addOption("Iguana")
  ..addOption("Capybara")
  ..addOption("Trout")
  ..addOption("Goldfinch")
  ..addOption("Other")
  ..x = 250.0
  ..y = 120.5
  ..show();
```

This construction is known as a *cascade*.  If you don't need to reference the `AlertBox` afterwards, you can even omit `var alertBox =` and begin your cascade with `new AlertBox()`.  But let's say you *do* need to keep it in a variable.  And let's say you decide later that you want to change the name of the variable to differentiate it from other `AlertBox`es.  With a cascade, you can make that change by touching a single variable name on a single line of code.  The result is code that is easier to read and *much* easier to refactor.  It's a programmer's dream come true!

## Give cascades a try

I'll bet you can't wait to try cascades out for yourself.  Here's a quick example program I wrote with an arbitrarily intricate `Sentence` class I made up.  Of course, this isn't meant to be instructive code; it merely demonstrates the power of the cascade syntax.  Notice how I'm making property assignments and regular function calls within the same cascade.  Pretty neat, huh?

Go ahead and mess around with the code.  Try building your own sentences and reordering the various effects using cascades.  It's easy to see how cascades are perfect for working with any sort of class that requires a fair amount of configuration, such as widgets in a UI.

<iframe src="https://dartpad.dartlang.org/embed-dart.html?id=08bf6e427d07a2c3b1acfb0647cf17ef&amp;horizontalRatio=80&amp;verticalRatio=60" width="100%" height="500px" style="border: 1px solid #ccc;">
</iframe>



<!-- That makes your code more flexible, and easier to refactor. -->
