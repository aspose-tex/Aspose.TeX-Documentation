---
title: LaTeX to image | .NET
linktitle: LaTeX to image
type: docs
weight: 10
url: /net/latex-to-image/
aliases: /net/latex-to-png/
keywords: latex to png, latex png, latex to image, latex image, latex to jpg, latex jpg, latex to jpeg, latex jpeg, latex to tiff, latex tiff, latex to bmp, latex bmp
description: To convert TeX to image formats using Aspose.TeX API solution for .NET learn this article to see that describes how to do this and the code examples.
lastmod: "2023-03-23"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---

**Aspose.TeX for .NET** allows us to convert LaTeX files to a number of raster image formats.

## **How to convert LaTeX to PNG**

Let's take a detailed look at the code in C# providing the simplest way to convert LaTeX to PNG format.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToPng-Simplest.cs" >}}

So, the first thing we need to do (well, sometimes not the very first) is to create an instance of the [TeXOptions](https://reference.aspose.com/tex/net/aspose.tex/texoptions/) class. The only static method that does this is [ConsoleAppOptions()](https://reference.aspose.com/tex/net/aspose.tex/texoptions/consoleappoptions/), so let's not be puzzled by the meaning of its name. The method takes the [ObjectLaTeX instance](https://reference.aspose.com/tex/net/aspose.tex/texconfig/objectlatex/) of the [TeXConfig](https://reference.aspose.com/tex/net/aspose.tex/texconfig/) class, which is exactly suitable for converting a [LaTeX file](/tex/net/latex-io/#latex-file). This configuration tells the Object TeX engine to load the Object LaTeX format and to be ready to accept the LaTeX file. Object LaTeX format is actually just the [LaTeX](/tex/net/what-is-latex/) format, except that it uses [Object TeX](/tex/net/aspose-tex-and-object-tex/#object-tex) specific primitives to set up the page metrics.

The first of the required options is [OutputWorkingDirectory](https://reference.aspose.com/tex/net/aspose.tex/texoptions/outputworkingdirectory/) which defines the space, or area, where the TeX output will be written. [Here](/tex/net/aspose-tex-output/) are the details about the output directory concept in **Aspose.TeX for .NET**. In this example we use the [OutputFileSystemDirectory](https://reference.aspose.com/tex/net/aspose.tex.io/outputfilesystemdirectory/) class, which lets us write the output to the specified directory, or folder.

The second option is a [SaveOptions](https://reference.aspose.com/tex/net/aspose.tex.presentation/saveoptions/) class instance which will control the transformation of the [object model](/tex/net/aspose-tex-and-object-tex/#why-the-new-tex-is-object) to the target format. Since we are converting LaTeX to PNG, it's the [PngSaveOptions](https://reference.aspose.com/tex/net/aspose.tex.presentation.image/pngsaveoptions/) class instance, which lets us specify the resolution of the output images.

Then we need to create an instance of the [TeXJob](https://reference.aspose.com/tex/net/aspose.tex/texjob/) class. Wanting to convert a LaTeX file stored in the file system, we use [this](https://reference.aspose.com/tex/net/aspose.tex/texjob/texjob/) version of the constructor. We need to specify the full path to the file. Otherwise, the engine will look for it in the current directory (which is [CurrentDirectory](https://docs.microsoft.com/en-us/dotnet/api/system.environment.currentdirectory)) and most likely will not find it. Nevertheless, the *.tex* extension may be omitted. The engine will append it automatically. The second argument of the constructor is a [Device](https://reference.aspose.com/tex/net/aspose.tex.presentation/device/) class instance. Since we are converting LaTeX to PNG, it's an [ImageDevice](https://reference.aspose.com/tex/net/aspose.tex.presentation.image/imagedevice/) class instance, and this is common to all supported image formats. As the last argument, we pass the recently prepared conversion options.

All that's left to do now is to [run](https://reference.aspose.com/tex/net/aspose.tex/texjob/run/) the job.

Regardless of whether the run was successful or not, the first result that we'll see will be the terminal output. If the run was successful, it will look something like this:

```text
This is ObjectTeX, Version 3.1415926-1.0 (Aspose.TeX 21.8)
entering extended mode

(<input_directory>\hello-world.ltx
LaTeX2e <2011/06/27>
(article.cls
Document Class: article 2007/10/19 v1.4h Standard LaTeX document class
(size10.clo))
No file hello-world.aux.
[1]
(<output_directory>\hello-world.aux) )
Output written on hello-world.png (1 page).
Transcript written on hello-world.log.
```

We will find other "fruits" of the engine's labor in the folder that we specified as the output directory. Those will be the transcript file and, **here it is!**, the main output PNG image file(s).

## **An alternative way to write main output PNG file(s)**

There is another way to get image data as an array of byte arrays, each array in the second dimension represents image data for a separate page.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToPng-Alternative.cs" >}}

The *"page-n.png"* file(s) will be written to any path we specify. Unlike [PDF output](/tex/net/latex-to-pdf/#an-alternative-way-to-write-main-output-pdf-file), they will duplicate the output PNG files written to the output directory.

## **About input options**

In case our main input file requires dependencies, for example, packages, that are not included in the basic LaTeX system and supported packages, we MUST set the [RequiredInputDirectory](https://reference.aspose.com/tex/net/aspose.tex/texoptions/requiredinputdirectory/) option the similar way we set the [OutputWorkingDirectory](https://reference.aspose.com/tex/net/aspose.tex/texoptions/outputworkingdirectory/) option and put the dependencies in that directory. Dependecies may be arbitrarily organized in subdirectories. In case we have our own files to include along the typesetting process, say external graphics files, we MUST also set the [InputWorkingDirectory](https://reference.aspose.com/tex/net/aspose.tex/texoptions/inputworkingdirectory/) using the path to the location where those files are collected. We can also place the main input file somewhere inside the input directory and specify the relative path in the `run()` method (or specify no path at all if the main input file is in the root). [Here](/tex/net/aspose-tex-input/) are the details about the input directory concept in **Aspose.TeX for .NET** and provided implementations.

Other TeX job options are discussed [here](/tex/net/other-options/).

**You may also check out the free LaTeX-to-PNG conversion [web app](https://products.aspose.app/tex/conversion/latex-to-png) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**

Below, we discuss the LaTeX conversion to other supported raster image formats without sinking deep into details as there are actually no details. The only difference is in the type of the [SaveOptions](https://reference.aspose.com/tex/net/aspose.tex/texoptions/saveoptions/) property in the conversion options.

## **How to convert LaTeX to JPG**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToJpeg.cs" >}}

**You may also check out the free LaTeX-to-JPG conversion [web app](https://products.aspose.app/tex/conversion/latex-to-jpg) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**

## **How to convert LaTeX to TIFF**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToTiff.cs" >}}

**You may also check out the free LaTeX-to-TIFF conversion [web app](https://products.aspose.app/tex/conversion/latex-to-tiff) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**

## **How to convert LaTeX to BMP**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-LaTeXToBmp.cs" >}}

**You may also check out the free LaTeX-to-BMP conversion [web app](https://products.aspose.app/tex/conversion/latex-to-bmp) built based on [Aspose.TeX for .NET API](https://products.aspose.com/tex/net/).**