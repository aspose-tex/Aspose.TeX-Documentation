---
title: Other target conversion formats | .NET
linktitle: Other target formats
type: docs
weight: 12
url: /net/other-target-formats/
---

## **Image formats**

**Aspose.TeX for .NET** also allows us to convert LaTeX files to a number of other raster image formats. Just in case. All these conversions are performed in the similar way as converting [LaTeX to PNG](/tex/net/latex-to-png/) using the [ImageDevice](https://apireference.aspose.com/tex/net/aspose.tex.presentation.image/imagedevice). The only difference is in the type of the [SaveOptions](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/saveoptions) property in the conversion options.

We will not sink deep into details just because there are actually no details.

### **How to convert LaTeX to JPEG**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToJpeg.cs" >}}

**You may also check out the free LaTeX-to-JPEG conversion [web app](https://products.aspose.app/tex/conversion/latex-to-jpg) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**

### **How to convert LaTeX to TIFF**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToTiff.cs" >}}

**You may also check out the free LaTeX-to-TIFF conversion [web app](https://products.aspose.app/tex/conversion/latex-to-tiff) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**

### **How to convert LaTeX to BMP**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToBmp.cs" >}}

**You may also check out the free LaTeX-to-BMP conversion [web app](https://products.aspose.app/tex/conversion/latex-to-bmp) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**

## **How to convert LaTeX to XPS**

Another target format is [XPS](https://en.wikipedia.org/wiki/Open_XML_Paper_Specification). The conversion to XPS is just as simple, except that in addition to the [SaveOptions](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/saveoptions), we have to change the device to an instance of the [XpsDevice](https://apireference.aspose.com/tex/net/aspose.tex.presentation.xps/xpsdevice) class.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToXps-Simplest.cs" >}}

### **An alternative way to write main output XPS file**

There's another constructor of the [XpsDevice](https://apireference.aspose.com/tex/net/aspose.tex.presentation.xps/xpsdevice/constructors/2) class, which lets us get the resulting XPS file in an alternative way.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToXps-Alternative.cs" >}}

The effect is the same as we get [here](/tex/net/latex-to-pdf/#an-alternative-way-to-write-main-output-pdf-file).

**You may also check out the free LaTeX-to-XPS conversion [web app](https://products.aspose.app/tex/conversion/latex-to-xps) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**