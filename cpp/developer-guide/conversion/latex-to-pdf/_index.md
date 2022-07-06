---
title: LaTeX to PDF | C++
linktitle: LaTeX to PDF
type: docs
weight: 11
url: /cpp/latex-to-pdf/
keywords: latex to pdf, latex pdf, convert latex to pdf
description: To convert TeX to PDF using Aspose.TeX API solution for C++ learn this article to see that describes how to do this and the code examples.
lastmod: "2021-10-14"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---

## **How to convert LaTeX to PDF**

Let's take a detailed look at the code in C# providing the simplest way to convert LaTeX to PDF format.

{{< blocks/products/pf/agp/feature-section >}}
{{< app/tex/converter "C++ code example LaTeX to PNG conversion" LTX PDF>}}
    System::SharedPtr<TeXOptions> options = TeXOptions::ConsoleAppOptions(TeXConfig::ObjectLaTeX());

    options->set_OutputWorkingDirectory(System::MakeObject<OutputFileSystemDirectory>(RunExamples::OutputDirectory));

    options->set_SaveOptions(System::MakeObject<{{output camel}}SaveOptions>());

    System::MakeObject<Aspose::TeX::TeXJob>(u"{{inputFile}}", System::MakeObject<PdfDevice>(), options)->Run();
{{< /app/tex/converter >}}
{{< /blocks/products/pf/agp/feature-section>}}

So, the first thing we need to do (well, sometimes not the very first) is to create an instance of the [TeXOptions](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options) class. The only static method that does this is [ConsoleAppOptions()](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#ad8aec9c3ff198c9b1e0f36927c44179d), so let's not be puzzled by the meaning of its name. The method takes an [instance](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_config#a8ee52115ae06cd6e97151a456a4dd5ea) of the [TeXConfig](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_config/) class, which is exactly suitable for converting a [LaTeX file](/tex/net/latex-io/#latex-file). This configuration tells the Object TeX engine to load the Object LaTeX format and to be ready to accept the LaTeX file. Object LaTeX format is actually just the [LaTeX](/tex/net/what-is-latex/) format, except that it uses [Object TeX](/tex/net/aspose-tex-and-object-tex/#object-tex) specific primitives to set up the page metrics.

The first of the required options is [OutputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#aa4f4ea6dab7db5ba1b40800495f16f63) which defines the space, or area, where the TeX output will be written. [Here](/tex/cpp/aspose-tex-output/) are the details about the output directory concept in **Aspose.TeX for C++**. In this example we use the [OutputFileSystemDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.output_file_system_directory) class, which lets us write the output to the specified directory, or folder.

The second option is a [SaveOptions](https://apireference.aspose.com/tex/net/aspose.tex.presentation/saveoptions) class instance which will control the transformation of the [object model](/tex/net/aspose-tex-and-object-tex/#why-the-new-tex-is-object) to the target format. Since we are converting LaTeX to PDF, it's the [PdfSaveOptions](https://apireference.aspose.com/tex/net/aspose.tex.presentation.pdf/pdfsaveoptions) class instance.

Then we need to create an instance of the [TeXJob](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_job) class. Wanting to convert a LaTeX file stored in the file system, we use [this](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_job#a1c23c4138aca10b9cc6ae49d5cedc3db) version of the constructor. We must specify the full path to the file. Otherwise, the engine will look for it in the current directory (which is [CurrentDirectory](https://docs.microsoft.com/en-us/dotnet/api/system.environment.currentdirectory)) and most likely will not find it. Nevertheless, we may omit the extension if our file has the *.tex* one. The engine will append it automatically. The second argument of the constructor is a [Device](https://reference.aspose.com/tex/cpp/class/aspose.te_x.presentation.device) class instance. Since we are converting LaTeX to PDF, it's an [PdfDevice](https://apireference.aspose.com/tex/net/aspose.tex.presentation.pdf/pdfdevice) class instance. As the last argument, we pass the recently prepared conversion options.

All that's left to do now is to [run](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_job#a0bc7f8b329ea1f19cbba84bf2060f6fb) the job.

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

We will find other "fruits" of the engine's labor in the folder that we specified as the output directory. Those will be the transcript file and, **here it is!**, the main output PDF file.

## **An alternative way to write main output PDF file**

There's another constructor of the [PdfDevice](https://apireference.aspose.com/tex/net/aspose.tex.presentation.pdf/pdfdevice/constructors/2) class, which lets us get the resulting PDF file in an alternative way.

```C++
    // Create the stream to write the XPS file to.
    {
        System::SharedPtr<System::IO::Stream> pdfStream = System::IO::File::Open(System::IO::Path::Combine(RunExamples::OutputDirectory, u"any-name.pdf"), System::IO::FileMode::Create);
        // Clearing resources under 'using' statement
        System::Details::DisposeGuard<1> __dispose_guard_0({ pdfsStream});
        // ------------------------------------------
        
        try
        {
            // Create conversion options for Object LaTeX format on Object TeX engine extension.
            System::SharedPtr<TeXOptions> options = TeXOptions::ConsoleAppOptions(TeXConfig::get_ObjectLaTeX());
            // Specify the file system working directory for the output.
            options->set_OutputWorkingDirectory(System::MakeObject<OutputFileSystemDirectory>(RunExamples::OutputDirectory));
            // Initialize the options for saving in PDF format.
            options->set_SaveOptions(System::MakeObject<PdfSaveOptions>());
            // Default value.
            // Run LaTeX to XPS conversion.
            System::MakeObject<TeXJob>(System::IO::Path::Combine(RunExamples::InputDirectory, u"hello-world.ltx"), System::MakeObject<PdfDevice>(pdfStream), options)->Run();
        }
        catch(...)
        {
            __dispose_guard_0.SetCurrentException(std::current_exception());
        }
    }
```

The *any-name.pdf* file in the specified directory will be our main output PDF file. At the same time, unlike [image output](/tex/cpp/latex-to-png/#an-alternative-way-to-write-main-output-png-files), we will not find any PDF files in the output directory defined by the conversion options. Exception: *any-name.pdf* is located (by its path) in the same file system directory that is assigned to [OutputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#aa4f4ea6dab7db5ba1b40800495f16f63) option using [OutputFileSystemDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.output_file_system_directory).

## **About input options**

In case our main input file requires dependencies, for example, packages, that are not included in the basic LaTeX system and supported packages, we MUST set the [RequiredInputDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#a815cf18dc921a6ebeb6d2025e97ad003) option the similar way we set the [OutputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#aa4f4ea6dab7db5ba1b40800495f16f63) option and put the dependencies in that directory. Dependecies may be arbitrarily organized in subdirectories. In case we have our own files to include along the typesetting process, say external graphics files, we MUST also set the [InputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#a7c6f19c427b6cf0f07de087995293c2e) using the path to the location where those files are collected. We may also place the main input file somewhere inside the input directory and specify the relative path in the `run()` method (or specify no path at all if the main input file is in the root). [Here](/tex/cpp/aspose-tex-input/) are the details about the input directory concept in **Aspose.TeX for C++** and provided implementations.

Other TeX job options are discussed [here](/tex/cpp/other-options/).

**You may also check out the free LaTeX-to-PDF conversion [web app](https://products.aspose.app/tex/conversion/latex-to-pdf) built based on [Aspose.TeX for C++ API](https://products.aspose.com/tex/cpp/).**