---
layout: post
title: "iOS development tips"
---

## Basics

1. Model-View-Controller is a design pattern in iOS.

2. Unlike in Android Studio, the Interface Builder is not a graphical representation of code. A storyboard file is an archive of object instances.

3. Outlets are references to objects: `@IBOutlet var questionLabel: UILabel!` (IB means interface builder.)

4. Actions: `@IBAction func showNextQuestion(_ sender: UIButton) {}`

5. Use `genstrings foo.swift` to generate the Localizable.strings file.

## References

* [iOS Programming: The Big Nerd Ranch Guide](https://www.amazon.com/iOS-Programming-Ranch-Guide-Guides/dp/0134682335/ref=sr_1_2?keywords=ios+programming&qid=1564912891&s=gateway&sr=8-2)
