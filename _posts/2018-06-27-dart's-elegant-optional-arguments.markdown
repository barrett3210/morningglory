---
title: "Dart's elegant optional arguments"
layout: post
date: 2018-06-27 15:31:43
description: "Dart's unique system for optional parameters gives developers a new kind of flexibility."
tags:
  - "language features"
  - "optional arguments"
  - "optional parameters"
  - "code examples"
---

Almost all modern programming languages include the concept of *optional arguments*.  The idea is pretty easy to understand.  Every function has a list of zero or more *arguments* (also called *parameters*) that serve as the function's input values.  When you call a function, you supply values for these arguments.  Many arguments are *required*, meaning that you must supply their values in order to call the function.  *Optional arguments*, however, can be omitted.  When you don't specify a value for an optional argument, a default value is used.

## A look at parameters in other C-based languages

In most C-based languages, optional arguments must come at the end of a function call.  For example, take a look at this snippet of JavaScript (as of ES6):

```javascript
// Define a function.
function jsFunction(a, b, c = 7) {
  // ...
}

// Call the function without specifying a value for `c`.
jsFunction(1, 2);

// Call the function with `42` for the value of `c`.
jsFunction(1, 2, 42);
```

Here we've defined a function with two required arguments and one optional argument.  The first time `jsFunction` gets called, we didn't pass in anything for `c`, so the default value of `7` will be used.  The second time we decided to provide the value `42` instead.  Neat!

This system works fine, but it has a few drawbacks.  Optional arguments in JavaScript must come at the end of a function signature.  So what happens if you have a function with several optional arguments and you want to specify one of them, but none of the arguments that come before it?

```javascript
// You can't specify a value for `f` without providing values for `c`, `d`, and `e` as well.
longerJSFunction(a, b, c = 7, d = true, e = 999, f = "funky") {
  // ...
}
```

Well--you may be out of luck.  In JavaScript it is possible to pass in the value `undefined` for arguments you don't want to specify, but in practice this looks pretty clunky:

```javascript
// This is what you'd have to do to use the default values for `c`, `d`, and `e`
// while still specifying a value for `f`.
longerJSFunction(9, 10, undefined, undefined, undefined, "wicked");
```

One or two uses of `undefined` is easy enough to manage, but it's very easy to lose track of which value goes to which argument.  Even worse, the value `undefined` is only subtly distinct from the value `null`, and trying to track down which one means what in which context will probably have you scouring StackOverflow.

## Parameters in Objective-C

Objective-C (the classic language of iOS and macOS development) has its own unique style for calling functions.  Let's take a look.

Here's how you might declare a function in Objective-C:

```objc
- (void)playSound:(NSString *)filename;
```

And here's how you'd call that function:
```objc
[self playSound:@"beep.wav"];
```

This syntax is nice because it reads like a sentence in English.  The purpose of each argument is clearly stated immediately before the value that gets passed in, so you're not likely to lose track of which value goes with which argument.

Still, Objective-C has its downsides, namely verbosity.  It's notoriously difficult to write a concise program in Objective-C.  I'm from the camp of developers that values code clarity highly above code concision, but even I have to admit that spelling out the name of each argument every single time I make a function call can be exhausting.  Modern IDEs give you a little help by typing the names of each argument automatically, but formatting and traversing all that text is still a pain.

Another downside of Objective-C's function syntax is that optional arguments aren't possible--at least not in the same sense.  You can sort of create optional arguments by defining multiple variants of the same method:

```objc
- (void)playSound:(NSString *)filename;
- (void)playSound:(NSString *)filename withPitch:(double)frequency;
- (void)playSound:(NSString *)filename withPitch:(double)frequency looping:(BOOL)looping;
```

Defining a separate variant for each additional argument is a ton of busywork, and it makes refactoring a pain.  And since each argument has a name attached to it, you might expect that Objective-C would let you list the arguments in any order.  *It doesn't*.

## The best of both worlds

The creators of Dart have clearly given a lot of thought to its syntax.  In the simplest case--calling functions with no optional arguments--Dart's syntax resembles JavaScript's.

```dart
// Define a function in Dart.
void dartFunction(num a, num b) {
  // ...
}

// Call a function in Dart.
dartFunction(1, 2);
```

But when you get into optional arguments, you're presented with a choice.  Should you use **positial** arguments or **named** arguments?

### Optional positional arguments

Dart's optional positional arguments also work similarly to JavaScript's.

```dart
// Define a function in Dart with four optional positional arguments
void example(num a, num b, [num c = 7, bool d = true, int e = 999, String f = "funky"]) {
  // ...
}
```

Calling optional positional arguments is also pretty similar.  You can omit optional positional arguments simply by leaving them off of the end of the function call.
```dart
// Call the function and specify values for all positional arguments.
example(9, 10, 11.3, false, 555, "wicked");

// Call the function again, but this time use the default value for `f`.
example(9, 10, 11.3, false, 555);
```

Accordingly, optional positional arguments in Dart have most of the same advantages and disadvantages as they do in JavaScript.  The only improvement is that there's no `undefined` value in Dart--only `null`--so you won't run into any tricky-to-parse discrepancies.  Of course this also means that there's no workaround to skip over arguments you don't want to specify.  If you want to specify the last argument in a series of positional arguments, you must specify the entire series.  And you might expect that to be a problem.  It's a good thing there are also optional *named* arguments.

### Optional named arguments

Here's how you define optional named arguments in Dart.

```dart
// Define a function in Dart with four optional named arguments.
void example(num a, num b, {num c = 7, bool d = true, int e = 999, String f = "funky"}) {
  // ..
}
```

And here's how you call them.
```dart
// Call the function and specify values for all named arguments.
example(9, 10, c: 11.3, d: false, e: 555, f: "wicked");
```

Interesting.  It's almost like a syntactic mix of JavaScript and Objective-C.


But it gets much better!  What if you only want to specify *some* of the optional named arguments?

```dart
// Call the function again and specify values only for `c` and `d`.
example(9, 10, c: 11.3, d: false);

// Call the function again, this time only specifying a value for `f`
example(9, 19, f: "amazing!");
```

Did you catch what just happened there?  Optional named arguments let you pick and choose which arguments to specify and which to omit on an individual basis.  But Dart even takes things a step further.  You can specify optional named arguments in *any order*.

```dart
// In Dart, these two calls are both valid and functionally equivalent:
example(9, 10, c: 11.3, f: "fantastic!");
example(9, 10, f: "fantastic!", c: 11.3);
```

## Power to the programmers

As you can see, Dart gives developers a great deal of freedom when deciding the best way to express their code.  Named optional arguments provide a built-in way of labeling values, ensuring that you'll never lose track of the meaning behind an argument.  On the other hand, positional optional arguments read quickly and save space, as they blend in alongside any required arguments in your function calls.  I prefer named optional arguments for most applications, but there are certainly cases where the brevity of positional optional arguments is more intuitive.

## Both styles in action

Here's a quick example program that demonstrates the two different styles of optional arguments.  Try playing around with them so you can get a sense of which argument style works best for which situations.  Just one word of warning before you begin: once you've experienced the flexibility of Dart's syntax, every other language you've ever used may feel limited by comparison.

<iframe src="https://dartpad.dartlang.org/embed-dart.html?id=29bce9ad7fdc57de65d802bf493f0346&amp;horizontalRatio=80&amp;verticalRatio=60" width="100%" height="500px" style="border: 1px solid #ccc;">
</iframe>
