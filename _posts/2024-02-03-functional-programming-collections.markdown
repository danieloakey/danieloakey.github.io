---
layout: post
title:  "Want to spread functional programming? Don’t forget the collections"
date:   2024-02-03 08:02:00 +0000
categories: fp
---
The benefits of functional programming are often not well communicated, in my opinion. I love this quote from a [paper entitled 'Why Functional Programming Matters'](https://www.cs.kent.ac.uk/people/staff/dat/miranda/whyfp90.pdf):

> The functional programmer sounds rather like a mediæval monk, denying himself the pleasures of life in the hope that it will
make him virtuous. To those more interested in material benefits, these "advantages" are totally unconvincing.

The paper goes on to explore what, for me, is the most obvious advantage of programming in a functional style, the ability to build up a program by composing lots of smaller transformations on data. Composition is pretty much the only way we can build large systems successfully.

If you can look beyond manipulating collections with traditional for-loops and variable assignments, it becomes easier to combine the Lego blocks of map, filter, reduce, etc. into more complex functions. In eschewing explicit control of execution, you’re now free to focus on what needs computing, not how it should be done.

By and large, most mainstream programming languages have come round to these ideas and have duly adopted map, filter et al. in some form (sometimes using more friendly terminology!). Just as every language in the 90s wanted to be object oriented, the languages of today want to be at least a little functional.

What’s missing, however, are good immutable data structures. It’s a small benefit to transform a collection within a single method or class, but a much greater benefit to extend that technique across a whole system. If you’re passing around an immutable list, you have a guarantee that no part of the code base can make changes to the original. This makes it simpler to work with and more safely parallelised.

The Java [Stream library](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html) is an example of falling short. If you attempt to reuse a `Stream`, you get an `IllegalStateException`. The only way to use the library is to end the chain of transformations by collecting into the usual `List`/`Array`/etc. -- so you're back to copying and passing mutable collections.

We need principled, efficient implementations of immutable lists, vectors, sets, maps and more. Thanks to persistent data structures, immutability can be enjoyed without major memory or performance overheads. Languages like Scala and Clojure have had these since their inceptions.

My ideal collections library would also allow for fast conversion between mutable and immutable data, as found in Scala. That would give programmers the ability to drop back into procedural code whenever simplicity or performance demanded it -- near enough the best of both worlds.

There are already some excellent immutable collection libraries out there for lots of platforms. Here's [an example for Ruby](https://github.com/hamstergem/hamster). With more interest and education they can become powerful tools in developers’ toolkits. Functional programming is already "winning" by stealth, immutable collections might be the next step.
