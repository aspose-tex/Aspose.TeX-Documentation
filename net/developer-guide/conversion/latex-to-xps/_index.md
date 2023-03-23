---
title: LaTeX to XPS | .NET
linktitle: LaTeX to XPS
type: docs
weight: 12
url: /net/latex-to-xps/
aliases: /net/other-target-formats/
description: Conversion functionality of Aspose.TeX API solution for .NET lets convert LaTeX files to XPS format. Here are some code examples.
lastmod: "2023-03-23"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---

Another target format is [**XPS**](https://en.wikipedia.org/wiki/Open_XML_Paper_Specification). An **XPS** file is physically a ZIP package that contains paginated content of a document, along with the metadata required for proper display by specific viewers (such as Windows XPS Viewer) and printing. All data in a package is represented by files. Some of them are binary and contain resources such as images, fonts, and ICC profiles. Others are XML files in various specific schemas. The latter include files that contain the document data itself. Document data consists of a set of files - each file contains data for an individual page of the document. Such files consist of a single page element and a tree of child elements - *Canvas*, *Path* and *Glyphs*. *Canvas* is a grouping element that can contain other *Canvases*, *Paths* and *Glyphs*. It serves to control the appearance of all child elements as a group. *Path* elements are used to define vector graphics paths. And *Glyphs* elements are used to define textual content. All three elements have properties to define various aspects of appearance.

There is the [**Aspose.Page**](https://products.aspose.com/page/) library that provides an API for manipulating XPS documents, as well as converting them to PDF and raster image formats.

## **How to convert LaTeX to XPS**

The LaTeX to XPS conversion is just as simple as the [conversion to raster image formats](/tex/net/latex-to-image/), except that the [SaveOptions](https://reference.aspose.com/tex/net/aspose.tex/texoptions/saveoptions/) MUST be set to an [XpsSaveOptions](https://reference.aspose.com/tex/net/aspose.tex.presentation.xps/xpssaveoptions/) class instance (by default or explicitly), and the device MUST be changed to an instance of the [XpsDevice](https://reference.aspose.com/tex/net/aspose.tex.presentation.xps/xpsdevice/) class.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToXps-Simplest.cs" >}}

### **An alternative way to write main output XPS file**

There's another constructor of the [XpsDevice](https://reference.aspose.com/tex/net/aspose.tex.presentation.xps/xpsdevice/xpsdevice/) class, which lets us get the resulting XPS file in an alternative way.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToXps-Alternative.cs" >}}

The effect is the same as we get [here](/tex/net/latex-to-pdf/#an-alternative-way-to-write-main-output-pdf-file).

**You may also check out the free LaTeX-to-XPS conversion [web app](https://products.aspose.app/tex/conversion/latex-to-xps) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**