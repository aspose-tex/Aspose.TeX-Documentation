---
title: LaTeX Figure rendering | Java
linktitle: LaTeX figure rendering
type: docs
weight: 20
url: /java/latex-figure-rendering/
description: Aspose.TeX API solution for Java LaTeX fragment (figure) rendering is described in this article. Learn the code examples on how to use the functionality.
lastmod: "2023-02-28"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---

It may happen that you want to extract some content (a drawing, a writing, a plot, etc.) from a LaTeX file as a separately rendered piece, or a *"figure"*, regardless of its place on an output document page. An illustration for your publication on the Internet, for example, is the case. Our API can help you with the task. There are two available target formats - PNG and SVG. Just like in LaTeX math formula rendering. We must also note that **LaTeX figure rendering** is a generalization of [LaTeX math formula rendering](/tex/java/latex-math-formula-rendering).

## **How to render a LaTeX figure to PNG**

And as with formula rendering, we will start with an example. Here it is:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Features-PngLaTeXFigureRendering.java" >}}

First of all, we create a [rendering options](https://reference.aspose.com/tex/java/com.aspose.tex/PngFigureRendererOptions) instance. We do it here along with specifying the output image resolution.

Next, we specify the preamble. There's no default preamble for LaTeX figure rendering, so if you want, for instance, to render some graphics plotted using the `pict2e` LaTeX package, you need to specify it in the preamble:
```tex
\usepackage{pict2e}
```

Then we instruct the renderer to scale the output by 300%.

The next option defines the background color. Unlike with math formula rendering, we don't specify a foreground color since we assume that the colors are entirely under the control of the LaTeX code. In fact, so is the background color, so this is just a convenient option.

The next line of the example doesn't make much sense. It just demonstrates that you can direct the log output to some stream.

And the last option `ShowTerminal` allows you to toggle writing the terminal output to the console.

The method that actually performs the rendering is [FigureRenderer.render()](https://reference.aspose.com/tex/java/com.aspose.tex/FigureRenderer). It returns the size of the figure in points as an output argument. To use this size later we declare the variable in the next line.

The stream where the image is to be written is accepted by the method as the second argument. We create the stream next.

And finally, we call the `FigureRenderer.render()` method itself, passing options as the third argument. The LaTeX code of the figure is passed as the first argument.

The last lines of the example print two artifacts of figure rendering - the size of the figure and the brief error report (in case there are errors).

Here is the result of rendering.

[<img src="text-and-formula.png" title="LaTeX Figure rendering to PNG">](text-and-formula.png)

This is the most general use case for the **LaTeX figure rendering** feature.

## **How to render a LaTeX figure to SVG**

In much the same way, we can render a LaTeX figure to SVG format.

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Features-SvgLaTeXFigureRendering.java" >}}

The differences are:
 * We use [SvgFigureRendererOptions](https://reference.aspose.com/tex/java/com.aspose.tex/SvgFigureRendererOptions) class instead of [PngFigureRendererOptions](https://reference.aspose.com/tex/java/com.aspose.tex/PngFigureRendererOptions).
 * We don't specify the resolution.
 * We use [SvgFigureRenderer](https://reference.aspose.com/tex/java/com.aspose.tex/SvgFigureRenderer) class instead of [PngFigureRenderer](https://reference.aspose.com/tex/java/com.aspose.tex/PngFigureRenderer).
 
Here is the result:

[<img src="text-and-formula.svg" title="LaTeX Figure rendering to SVG">](text-and-formula.svg)