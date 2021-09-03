---
title: 1.7. What is LaTeX?
type: docs
weight: 10
url: /net/what-is-latex/
---

So, LaTeX. What is it?

LaTeX is the TeX format, in short.

LaTeX (*LAH-tekh or LAY-tekh*, often stylized as LATEX) is a software system for document preparation that was originally written in the early 1980s by [Leslie Lamport](https://en.wikipedia.org/wiki/Leslie_Lamport) at [SRI International](https://en.wikipedia.org/wiki/SRI_International). This is what [Wikipedia](https://en.wikipedia.org/wiki/LaTeX) tells.

## **What is LaTeX file?**
If we have a [TeX file](/tex/net/what-a-tex-file-is/) that is written using macros (primitives are allowed, nevertheless) and internal parameters values of the LaTeX format, then we will call this file a *LaTeX file*. These files MUST have the following structure:

```tex
\documentclass{<a document class>}
% Preamble
...
\begin{document}
% Document body
...
\end{document}
```
where `<a document class>` is a name of a document class which is an [input TeX file](https://en.wikibooks.org/wiki/LaTeX/Document_Structure#Document_classes) that defines the appearence of the output document's pages and macros that are most suitable for a certain type of document.

To be honest, you can insert primitive control sequences before `\documentclass{}`, like `\nonstopmode`, etc. But each LaTeX macro checks whether it is located in a proper part of a file.