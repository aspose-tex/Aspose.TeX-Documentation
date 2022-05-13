---
title: Other target conversion formats | Java
linktitle: Other target formats
type: docs
weight: 12
url: /java/other-target-formats/
description: Conversion functionality of Aspose.TeX API solution for Java lets convert LaTeX files to a number of other raster image formats. Here are some code examples.
---

## **Image formats**

**Aspose.TeX for Java** also allows us to convert LaTeX files to a number of other raster image formats. Just in case. All these conversions are performed in the similar way as converting [LaTeX to PNG](/tex/java/latex-to-png/) using the [ImageDevice](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/ImageDevice). The only difference is in the type of the [SaveOptions](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getSaveOptions--) property in the conversion options.

We won't go into details just because there aren't actually any details.

### **How to convert LaTeX to JPEG**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-LaTeXToJpeg.java" >}}

**You may also check out the free LaTeX-to-JPEG conversion [web app](https://products.aspose.app/tex/conversion/latex-to-jpg) built based on [Aspose.TeX for .NET](https://products.aspose.com/tex/net/) API. [Here](https://products.aspose.com/tex/java/) is the Java version page.**

### **How to convert LaTeX to TIFF**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-LaTeXToTiff.java" >}}

**You may also check out the free LaTeX-to-TIFF conversion [web app](https://products.aspose.app/tex/conversion/latex-to-tiff) built based on [Aspose.TeX for .NET](https://products.aspose.com/tex/net/) API. [Here](https://products.aspose.com/tex/java/) is the Java version page.**

### **How to convert LaTeX to BMP**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-LaTeXToBmp.java" >}}

**You may also check out the free LaTeX-to-BMP conversion [web app](https://products.aspose.app/tex/conversion/latex-to-bmp) built based on [Aspose.TeX for .NET](https://products.aspose.com/tex/net/) API. [Here](https://products.aspose.com/tex/java/) is the Java version page.**

## **How to convert LaTeX to XPS**

Another target format is [XPS](https://en.wikipedia.org/wiki/Open_XML_Paper_Specification). The conversion to XPS is just as simple, except that in addition to the [SaveOptions](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getSaveOptions--), we have to use an instance of the [XpsDevice](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/XpsDevice) class.

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-LaTeXToXps-Simplest.java" >}}

### **An alternative way to write main output XPS file**

There's another constructor of the [XpsDevice](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/XpsDevice#XpsDevice-java.io.OutputStream-) class, which allows us to get the resulting XPS file in an alternative way.

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-LaTeXToXps-Alternative.java" >}}

The effect is the same as we get [here](/tex/java/latex-to-pdf/#an-alternative-way-to-write-main-output-pdf-file).

**You may also check out the free LaTeX-to-XPS conversion [web app](https://products.aspose.app/tex/conversion/latex-to-xps) built based on [Aspose.TeX for .NET](https://products.aspose.com/tex/net/) API. [Here](https://products.aspose.com/tex/java/) is the Java version page.**