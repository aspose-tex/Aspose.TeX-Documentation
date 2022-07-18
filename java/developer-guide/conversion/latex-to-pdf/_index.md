---
title: LaTeX to PDF | Java
linktitle: LaTeX to PDF
type: docs
weight: 11
url: /java/latex-to-pdf/
keywords: latex to pdf, latex pdf, convert latex to pdf
description: To convert TeX to PDF using Aspose.TeX API solution for Java learn this article to see that describes how to do this and the code examples.
lastmod: "2021-10-14"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---

## **How to convert LaTeX to PDF**

Let's take a closer look at the Java code providing the simplest way to convert LaTeX to PDF format.

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-LaTeXToPdf-Simplest.java" >}}

So, the first thing we need to do (sometimes not the very first, as we will find out later) is to create an instance of the [TeXOptions](https://reference.aspose.com/tex/java/com.aspose.tex/TeXOptions) class. The only static method that does this is [consoleAppOptions()](https://reference.aspose.com/tex/java/com.aspose.tex/TeXOptions#consoleAppOptions-com.aspose.tex.TeXConfig-), so let's not bother with the meaning of its name. The method takes an [instance](https://reference.aspose.com/tex/java/com.aspose.tex/TeXConfig#objectLaTeX--) of the [TeXConfig](https://reference.aspose.com/tex/java/com.aspose.tex/TeXConfig) class, which is exactly suitable for converting a [LaTeX file](/tex/net/latex-io/#latex-file). This configuration instructs the Object TeX engine to load the Object LaTeX format and to be ready to accept the LaTeX file. Object LaTeX format is actually just the [LaTeX](/tex/net/what-is-latex/) format, except that it uses [Object TeX](/tex/net/aspose-tex-and-object-tex/#object-tex) specific primitives to set up the page metrics.

The first of the required options is [OutputWorkingDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getOutputWorkingDirectory--) which defines the space, or area, where the TeX output will be written. [Here](/tex/java/aspose-tex-output/) are the details about the output directory concept in **Aspose.TeX for Java**. In this example we use the [OutputFileSystemDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/OutputFileSystemDirectory) class, which allows us to write the output to the specified directory, or folder.

The second option is a [SaveOptions](https://reference.aspose.com/tex/java/com.aspose.tex.rendering/SaveOptions) class instance which will control the transformation of the [object model](/tex/net/aspose-tex-and-object-tex/#why-the-new-tex-is-object) to the target format. Since we are converting LaTeX to PDF, it's the [PdfSaveOptions](https://reference.aspose.com/tex/java/com.aspose.tex.rendering/PdfSaveOptions) class instance.

Then we need to create an instance of the [TeXJob](https://reference.aspose.com/tex/java/com.aspose.tex/TeXJob) class. Wanting to convert a LaTeX file stored in the file system, we use [this](https://reference.aspose.com/tex/java/com.aspose.tex/TeXJob#TeXJob-java.lang.String-com.aspose.tex.rendering.Device-com.aspose.tex.TeXOptions-) version of the constructor. We should specify the full path to the file. Otherwise, the engine will look for it in the current directory (which is defined [here](https://docs.oracle.com/javase/7/docs/api/java/io/File.html)) and most likely will not find it. Nevertheless, we may omit the extension if our file has the *.tex* one. The engine will append it automatically. The second argument of the constructor is a [Device](https://reference.aspose.com/tex/java/com.aspose.tex.rendering/Device) class instance. Since we are converting LaTeX to PDF, it's an [PdfDevice](https://reference.aspose.com/tex/java/com.aspose.tex.rendering/PdfDevice) class instance. As the last argument, we pass the recently prepared conversion options.

All that we have to do now is to [run](https://reference.aspose.com/tex/java/com.aspose.tex/TeXJob#run--) the job.

Regardless of whether the run was successful or not, the first result that we'll see will be the terminal output. In case of success, it looks something like this:

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
Output written on hello-world.pdf (1 page).
Transcript written on hello-world.log.
```

We will find other products of the engine's run in the folder that we specified as the output directory. Those will be the transcript (.log) file and, **Voila!**, the main output PDF file.

## **An alternative way to write main output PDF file**

There's another constructor of the [PdfDevice](https://reference.aspose.com/tex/java/com.aspose.tex.rendering/PdfDevice#PdfDevice-java.io.OutputStream-) class, which lets us get the resulting PDF file in an alternative way.

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-LaTeXToPdf-Alternative.java" >}}

The *any-name.pdf* file in the specified directory will be our main output PDF file. At the same time, unlike [image output](/tex/java/latex-to-png/#an-alternative-way-to-write-main-output-png-files), we will not find any PDF files in the output directory defined by the conversion options. Exception: *any-name.pdf* is located (by its path) in the same file system directory that is assigned to [OutputWorkingDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getOutputWorkingDirectory--) option using [OutputFileSystemDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/OutputFileSystemDirectory).

## **About input options**

In case our main input file requires dependencies, for example, packages, that are not included in the basic LaTeX system and supported packages, we MUST set the [RequiredInputDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getRequiredInputDirectory--) option the similar way we set the [OutputWorkingDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getOutputWorkingDirectory--) option and put the dependencies in that directory. Dependecies may be arbitrarily organized in subdirectories. In case we have our own files to include along the typesetting process, say external graphics files, we MUST also set the [InputWorkingDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getInputWorkingDirectory--) using the path to the location where those files are collected. We may also place the main input file somewhere inside the input directory and specify the relative path in the `run()` method (or specify no path at all if the main input file is in the root). [Here](/tex/java/aspose-tex-input/) are the details about the input directory concept in **Aspose.TeX for Java** and provided implementations.

Other TeX job options are discussed [here](/tex/java/other-options/).

**You may also check out the free LaTeX-to-PDF conversion [web app](https://products.aspose.app/tex/conversion/latex-to-pdf) built based on [Aspose.TeX for .NET](https://products.aspose.com/tex/net/) API. [Here](https://products.aspose.com/tex/java/) is the Java version page.**