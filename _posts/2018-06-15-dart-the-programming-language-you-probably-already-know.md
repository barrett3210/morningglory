---
layout: post
title:  "Dart: the programming language you probably already know"
description: "Learning a new programming language doesn't have to be difficult.  If you know C, C++, Objective-C, C#, Java, or JavaScript, you already know most of Dart."
date:   2018-06-15 15:37:12 -0700
tags:
  - "learning programming languages"
  - "ease of learning"
  - "familiar languages"
---

If you're a developer or even just a casual coder, then no doubt you're already inundated with articles extolling the virtues of learning new technologies.  Leaders in the dev community love to say things like, "If you don't read 381 programming books a year and learn a new system every seven hours, then you're doing your company a disservice."

## Learn or perish

The thing is--*they're mostly right*.  In this modern world where computer science is constantly shifting, developers who fail to learn risk being left behind.  While the lofty goals set forth by many an engineering authority are hardly achievable, the sentiment behind them is well-intentioned and fully justified.  It's simply impossible to build software for the future with the tools of the past.  If you want to remain productive and effective as a developer, you must embrace change and actively absorb emerging practices, libraries, and languages.

## But learning is hard

Unfortunately, it can be pretty intimidating to dive into one of the trendy programming languages that have popped up recently.  A huge factor behind this is that the syntax of hip new languages tends to look nothing like that of their more traditional counterparts.  Languages like [Rust](https://www.rust-lang.org/), [Go](https://golang.org/), [Swift](https://developer.apple.com/swift/), and [Kotlin](https://kotlinlang.org/) are redefining the way we think about programming with novel constructs and methodologies that are arguably superior to the worn and tattered paradigms of the past.  And let's face it--languages such as C, C++, Objective-C, Java, and *especially JavaScript* have their fair share of complications and inefficiencies that modern languages are absolutely right to steer clear of.  Still, the foreign feel of these languages can make them uninviting to established developers, to say the least.

To illustrate my point, here's an example snippet of Go, admittedly taken out of context from the front page of the language's [website](https://play.golang.org/p/iN6HCp_e91p).  To the typical Java developer, it's certainly possible to decipher the general approach of this program, but it will take a good deal of digging to uncover the exact intent of each line.

```go
// The prime sieve: Daisy-chain Filter processes.
func main() {
	ch := make(chan int) // Create a new channel.
	go Generate(ch)      // Launch Generate goroutine.
	for i := 0; i < 10; i++ {
		prime := <-ch
		fmt.Println(prime)
		ch1 := make(chan int)
		go Filter(ch, ch1, prime)
		ch = ch1
	}
}
```

## Familiar, but fresh

This is where [Dart](https://www.dartlang.org/) comes in.  If you know any of the languages in the C family, you'll feel very much at home with Dart's syntax.  You'd be forgiven for mistaking Dart for JavaScript, Java, or C#.  At the heart of Dart are all the same fundamentals that were popularized by tried and true languages of the past, and they all work just as you'd expect.  That's not to say Dart doesn't innovate.  It offers a plethora of handy new features as well as some very effective shorthands, but somehow it manages to introduce them without alienating even the most impatient of programmers.

In fact, you can make pretty good ground in Dart just by pretending you're writing JavaScript.  You'll want to do some reading on [best practices](https://www.dartlang.org/guides/language/effective-dart) before you publish your code, but most of the elements that weren't broken in JavaScript are still valid in Dart.  The differences are slight enough that you'll be able to follow much of what's changed just by reading the compiler warnings in your IDE.

## Take Dart for a spin

So if you're searching for a new language to hack on this weekend, [give Dart a try](https://www.dartlang.org/guides/language/language-tour).  Rust, Go, Swift, and Kotlin are all outstanding languages with their own strengths that are well worth studying, but you'll need to invest a decent amount of time to get the most out of them.  In its domain Dart is every bit as powerful as those languages, and you'll be up and running with it in *hours*, not days.

<iframe src="https://dartpad.dartlang.org/embed-dart.html?id=b7f3e94d631f701fac2fd030ace2b2c4&amp;horizontalRatio=80&amp;verticalRatio=60" width="100%" height="500px" style="border: 1px solid #ccc;">
</iframe>
