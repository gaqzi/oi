---
tags: [rich-hickey, adr, go, testify, mockery, rob-pike]
---
First Decision
====================

Starting development isn't just cracking up your favorite editor and start slinging code. Whether intentional or not there are decisions to make, And it's good if others can understand _why_ decisions were made at some point in time. 

I like [ADRs](https://adr.github.io/) (Any Decision Records) for keeping track of the decisions, the why, and the options considered. So let's start with the [first decisions I made](../decisions/0001-use-go-with-testify-assertions-and-mockery-mocks.md):

1. Programming language: Go
2. Test assertion library: [Testify](https://github.com/stretchr/testify)
3. Mocking library: [mockery](https://github.com/vektra/mockery)

I'm targeting Go developers, so language is obvious, but I think it's nice to indicate _why_ I picked the libraries I did. And it's purely because of familiarity and nothing else. Which is as good an option as any, just be aware of it. This makes development _easier_ for me and on a team we may have different experiences and what is easy for you is not for someone else.

## An aside on easy vs simple

[Rich Hickey](https://en.wikipedia.org/wiki/Rich_Hickey), of Clojure game, gave a talk title [Simple Made Easy](https://www.youtube.com/watch?v=LKtk3HCgTa8) where he clarified what the words `easy` and `simple` mean:

Easy is _relative_:
- Near, at hand (on our hard drive, in our tool set, IDE, brew install, go get…)
- Near to our understanding/skill set (familiar)
- Near our capabilities (done it before etc.)

Simple is in design and requires vigilance, sensibilities, and care. It's about reducing entanglements and working with abstractions that make _talking_ and _working_ on the problem simpler.

A lot of constructs we use are not _easy_ at a glance but when we've learned them they enable us, and we don't think about them anymore. Are they all inherently simple? No, some are really complicated. But some great ones are simple. 

I think [Rob Pike's][rob-pike], of Go fame, [option type] is a good example of something that's simple but for most people not easy. And after getting over how it works immensely powerful, and you'll see it all over in Go code. These are closures which allow access to private attributes, it's wild! 

Watch the talk, this short description is hopefully enough to get you interested, Rich makes the point fantastically. And good luck on not going on a Rich Hickey keynote bender! :)

[rob-pike]: https://en.wikipedia.org/wiki/Rob_Pike
[option type]: https://commandcenter.blogspot.com/2014/01/self-referential-functions-and-design.html
