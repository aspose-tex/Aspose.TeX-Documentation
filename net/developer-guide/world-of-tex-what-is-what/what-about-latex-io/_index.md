---
title: 1.8. What about LaTeX I/O?
type: docs
weight: 10
url: /net/what-about-latex-io/
---

There are a few thing worth noting about TeX [input](/tex/net/what-is-tex-input/) and [output](/tex/net/what-is-tex-output/) in the context of working with LaTeX files.

## **LaTeX output.**
A typical LaTeX job creates an auxiliary output file with the [job name](/tex/net/what-is-tex-output/) as its name and extension *.aux*. This file usually contains reference data that the engine collects along the job run, if you, say, set labels for math formulas (equations) and then refer to them somewhere in the text. In case you don't use anything of this kind, this file contains only the `\relax` control sequence (which is one of the TeX primitives). So don't be surprised.

Although `\openout`, `\write` and `\closeout` primitives are not forbidden, packages are the most suitable place for them. Therefore you should better use them in your own custom packages if you're developing them.

Other parts of the output are arbitrary, also follow the general [TeX output](/tex/net/what-is-tex-output/) concept and depend on what exactly your TeX file (program) is supposed to do, what packages (see below) you are using, etc.

## **LaTeX input.**
The aforementioned *.aux* file is a mandatory part of LaTeX input at the same time. Algorithmically, LaTeX can't accomplish those reference-related tasks within a single run, so the same job must be run twice --- the first time to collect data, the second time to use those data. Many LaTeX-based software systems run LaTeX jobs twice automatically. Spoiler: There is an [option](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/repeat) in Aspose.TeX API that lets you control this behavior.

Another mandatory part is a [document class](/tex/net/what-is-latex/#what-is-latex-file). The document class file, in turn, may implicitly depend on other files, which are thus included in the LaTeX input as well.

If you want to use features beyond the scope of the basic LaTeX and its document classes but supported by a certain TeX engine implementation, then you typically use a package, which you must notify the engine about in the preamble. A *LaTeX package* is a file, or a group of files assembled under one name, that provides such features. To notify the engine, you use the `\usepackage` command with the package name and omittable options, if the package defines any.

For example,
```tex
\usepackage[a6paper,landscape]{geometry}
```
Although `\input`, `\openin`, `\read` and `\closein` primitives are not forbidden, packages are the most suitable place for them. Therefore you should better use them in your own custom packages if you're developing them.

Other parts of the input are arbitrary, also follow the general [TeX input](/tex/net/what-is-tex-output/) concept and depend on what exactly your TeX file (program) is supposed to do, what packages you are using, etc.