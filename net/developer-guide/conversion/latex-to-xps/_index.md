---
title: LaTeX to XPS | .NET
linktitle: LaTeX to XPS
type: docs
weight: 12
url: /net/latex-to-xps/
description: Conversion functionality of Aspose.TeX API solution for .NET lets convert LaTeX files to XPS format. Here are some code examples.
---

## **How to convert LaTeX to XPS**

Another target format is [XPS](https://en.wikipedia.org/wiki/Open_XML_Paper_Specification). The LaTeX to XPS conversion is just as simple as [conversion to raster image formats](/tex/net/latex-to-image/), except that the [SaveOptions](https://reference.aspose.com/tex/net/aspose.tex/texoptions/saveoptions/) MUST be set to an [XpsSaveOptions](https://reference.aspose.com/tex/net/aspose.tex.presentation.xps/xpssaveoptions/) class instance (by default or explicitly), and the device MUST be changed to an instance of the [XpsDevice](https://reference.aspose.com/tex/net/aspose.tex.presentation.xps/xpsdevice/) class.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToXps-Simplest.cs" >}}

### **An alternative way to write a main output XPS file**

There's another constructor of the [XpsDevice](https://reference.aspose.com/tex/net/aspose.tex.presentation.xps/xpsdevice/xpsdevice/) class, which lets us get the resulting XPS file in an alternative way.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToXps-Alternative.cs" >}}

The effect is the same as we get [here](/tex/net/latex-to-pdf/#an-alternative-way-to-write-main-output-pdf-file).

**You may also check out the free LaTeX-to-XPS conversion [web app](https://products.aspose.app/tex/conversion/latex-to-xps) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**