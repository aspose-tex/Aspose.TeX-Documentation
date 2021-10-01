---
title: LaTeX math formulas rendering
type: docs
weight: 10
url: /net/latex-math-formula-rendering/
---

The API reference section related to this topic is [here](https://apireference.aspose.com/tex/net/aspose.tex.features). In fact, the easiest way to demonstrate the LaTeX math formula rendering feature is to start with the example. Here it is:

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Features-LaTeXMathRendering.cs" >}}

Let's get to the details. First of all, we create a [rendering options](https://apireference.aspose.com/tex/net/aspose.tex.features/mathrendereroptions) instance, similar to the TeX/LaTeX typesetting. We do it here simultaneously specifying the output image resolution.

Next, we specify the preamble. The default preamble is:
```tex
\usepackage{amsmath}
\usepackage{amsfonts}
\usepackage{amssymb}
```
which provides slightly more advanced math formula support than basic LaTeX. You can, for example, add the `color` package if you want to use your own highlightening in the formula, as we showed in the code example.

Then we instruct the renderer to scale the output by 300%.

Next two options define the foreground and background colors. Those parts of the formula that are not covered ("colored") by the custom highlightening will be displayed in the `TextColor` color.

The next line of the example doesn't make much sense. It just demonstrates that you can direct the log output to some stream.

And the last option `ShowTerminal` allows you to toggle writing the terminal output to the console.

The method that actually performs the rendering is [MathRenderer.Render()](https://apireference.aspose.com/tex/net/aspose.tex.features/mathrenderer/methods/render). It returns the size of the formula in points as an output argument. To use this size later we declare the variable in the next line.

The stream where the image is to be written is taken by the method as the second argument. We create the stream next.

And finally, we call the `MathRenderer.Render()` method itself, passing options as the third argument. The LaTeX code of the formula is passed as a string through the first argument.

The last lines of the example print two artifacts of math formula rendering - the size of the formula and the brief error report (in case there were errors).

This is the most general use case for LaTeX math formula rendering.

**You may also check out the free [web app](https://products.aspose.app/tex/mathrenderer) built based on the feature implemented within [Aspose.TeX API](https://products.aspose.com/tex/net/).**