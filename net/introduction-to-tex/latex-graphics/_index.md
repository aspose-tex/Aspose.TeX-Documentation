---
title: LaTeX graphics | \includegraphics command
linktitle: LaTeX graphics
type: docs
weight: 18	
url: /net/latex-graphics/
description: The inclusion of graphics in TeX is a matter worth mentioning. When talking about it, the first thing that comes to mind is the `\includegraphics` command.
lastmod: "2021-10-14"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---

## **LaTeX graphics**

Actually, there are two aspects of LaTeX graphics that are worth mentioning:
 * vector graphics described directly by means of LaTeX/TeX commands and,
 * inclusion of external graphics described by means of external formats, like EPS, PDF or raster PNG and PDF.
The former one has limited support in the original LaTeX and its packages. It is implemented with help of TeX vertical and horizontal rules. That's because the original LaTeX is based on the original TeX engine, which typsets the input creating files in *DVI* format, which is not suitable for describing either lines and curves or binary raster image data. But engines that are able to output to graphics-supporting formats (like pdfTeX to PDF) can also deal with graphics using format-dependent packages or package features. The latter graphics are not supported in basic LaTeX for the same reason. We will discuss graphics inclusion features below.

## **The LaTeX `graphics` package and `\includegraphics` command**

When talking about LaTeX graphics inclusion, the first thing that comes to mind is the `\includegraphics` command. It is defined in the `graphics` package, which you should mention in the preamble to enable its features.
```tex
\usepackage{graphics}
```

If your typesetting system is not configured to use, say, pdfTeX by default, you should specify the appropriate option that will force the package to use the required `driver` file:
```tex
\usepackage[pdftex]{graphics}
```
A `driver` file is a part of a package that implements the interface between package commands and format-dependent low-level TeX extension primitives. Aspose.TeX's LaTeX graphics support is configured to use its own driver, so you don't need to specify the driver option.

Now, the simplest way to include, say, a PNG image is to type:
```tex
\includegraphics{sample-image.png}
```
where `sample-image.png` is the name of the file you want to include. You may even ommit the extension. The `graphics` package contains the list of definitions of supported formats. When looking for a file, it traverses that list and includes the first matching file found.

You can also specify the full file name using an absolute or relative path:
```tex
\includegraphics{d:/sample-image.png} % absolute path
\includegraphics{./sample-image.png} % relative to the current directory
\includegraphics{../img/sample-image.png} % relative to the directory containing the current one
```

Another way to specify the graphics files location(s) is to define a list of alternative paths using `\graphicspath` command before calling `\includegraphics`:
```tex
\graphicspath{{d:/img}{c:/img}{d:/work/img}}
```

### Scaling the graphics

LaTeX `graphics` package provides commands for manipulating the content. So you can scale the included graphics (in fact, anything described by TeX/LaTeX code) as follows:
```tex
\scalebox{.5}{\includegraphics{sample-image.png}} % scales both width and height by 0.5
\scalebox{.5}[1.5]{\includegraphics{sample-image.png}} % scales the width and height by 0.5 and 1.5 respectively
```

### Resizing the graphics

It's similar to scaling, but you specify the required size instead of a scaling factor(s):
```tex
\resizebox{10mm}{!}{\includegraphics{sample-image.png}} % changes the width to 10mm preserving the proprtions
\resizebox{20mm}{10mm}{\includegraphics{sample-image.png}} % changes both width and height independently
```

### Rotating the graphics

```tex
\rotatebox{25}{\includegraphics{sample-image.png}} % rotates the image by 25 degrees counterclockwise
```

## The LaTeX `graphicx` package

The LaTeX `graphicx` package provides the `key=value` interface to content transformations. To enable its features, you should mention it in the preamble:
```tex
\usepackage{graphicx}
\usepackage[pdftex]{graphicx} % with the driver option
```

You can combine any of the following options, but keep in mind that the order is important.

### Graphics viewport
```tex
\includegraphics[viewport=10 10 280 220]{sample-image.png} % sets the viewport with the lower left corner
                                                           % at the point (10, 10) (coinsides with (0, 0)
                                                           % of the box) and dimensions 280x220pt
\includegraphics[viewport=10 10 250 220,clip]{sample-image.png} % the same, but the image is clipped by the viewport
```

### Scaling graphics

```tex
\includegraphics[scale=.5]{sample-image.png} % scales both width and height by 0.5
```

### Resizing graphics

```tex
\includegraphics[width=15mm]{sample-image.png} % changes the width to 10mm preserving the proprtions
height=15mm,width=25mm]{sample-image.png} % changes both width and height independently
```

### Rotating graphics

```tex
\includegraphics[angle=10]{sample-image.png} % rotates the image by 10 degrees counterclockwise
```

To learn more about the `graphics` package bundle features, see the documentation [here](https://ctan.org/pkg/graphics) and
[here](http://mirrors.ctan.org/macros/latex/required/graphics/graphics.pdf).

**You may also check out the free conversion [web app](https://products.aspose.app/tex/conversion/latex/) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**