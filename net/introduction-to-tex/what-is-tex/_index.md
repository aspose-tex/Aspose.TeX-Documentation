---
title: What is TeX?
type: docs
weight: 10
url: /net/what-is-tex/
keywords: what is tex
description: This page briefly answers the question "What is TeX?"
lastmod: "2021-10-14"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---
## **What TeX is NOT**
TeX is definitely not a format at all.

## **What IS TeX?**
So what IS TeX? Well, that is the question, as Hamlet[^1] said. Let's try to answer it as simply as possible.
Imagine that we have a programming language consisting of two elementary commands (called *control sequences*), or *primitives*, `\a` and `\b`. And in this language we can write programs for documents (books, articles, etc.) typesetting. Let's call this language **(L1)**. In order for these programs to be executed in a certain way, we have a certain engine that interprets the commands of this language.

Now let's assume that when writing a typesetting program for some document, we found that the subsequence `\a \b \a` occurs quite frequently. And also assume that in our language there is another primitive `\def`, which allows us to define subroutines, or macros. Let's call this language **(L2)**. Under these circumstances, we can define the macro `\def\c{\a \b \a}` at the beginning of the program and replace each occurrence of the subsequence with `\c` both for better readability and reduction.

Now, if we want to typeset another document, in the program of which this subsequence of commands also occurs frequently, we will have to define this macro again. But let's assume that our engine is capable of loading the `\c` macro into its internal state, and then saving that state as a binary file (a *dump*), which will then be automatically loaded ("on top" of the **(L2)** language command set) before processing the typesetting programs of each document in which the macro `\c` is required. We will call the set of primitives extended by the `\c` macro a *format*. Thus, our format is a *macro extension* of low-level primitive language **(L2)**.

The engine also contains a number of internal registers, or *internal parameters*, which can be accessed using control sequences. In addition to macro definitions, a format may contain initialization expressions for these parameters.

It happened that <a href="https://en.wikipedia.org/wiki/Donald_Knuth" target=_blank rel="nofollow">Donald E. Knuth</a>, defined a language similar to **(L2)**, but with a much wider set of primitives, which he called TeX. He also created an engine that understood (and still does) TeX language. He also called it TeX.

Happily, these weren't the only things he did. He also proposed the macro extension, or format, he called *Plain* TeX, which made writing programs more convenient. The initial set of TeX's primitives is sometimes called VirTeX ("Vir" for "virgin"), and, formally, is also a format, when considered along with defaults of internal parameters.

**So, on the one hand, TeX IS a programming language. And on the other hand, it IS an interpreter engine that understands this language. And, on the third hand, TeX is a more general concept meaning a typesetting system in whole.**

The only thing left to note here is that, in fact, the characters of the very text being typeset are also commands that force the TeX engine to type corresponding characters (taking into account the current input encoding) using the current font settings (which, in turn, are controllable by control sequences). Thus, when defining macros, we can use characters as well.

We hope that from now on the question "What is TeX?" no longer exists in your mind.

[^1]: The character in W. Shakespeare's "The Tragical Historie of Hamlet, Prince of Denmarke".
