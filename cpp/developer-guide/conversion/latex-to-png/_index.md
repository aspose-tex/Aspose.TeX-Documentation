---
title: LaTeX to PNG | C++
linktitle: LaTeX to PNG
type: docs
weight: 10
url: /cpp/latex-to-png/
keywords: latex to png, latex png
description: To convert TeX to PNG using Aspose.TeX API solution for C++ learn this article to see that describes how to do this and the code examples.
lastmod: "2021-10-14"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---

## **How to convert LaTeX to PNG**

Let's take a detailed look at the code in C# providing the simplest way to convert LaTeX to PNG format.

{{< blocks/products/pf/agp/feature-section >}}
{{< app/tex/converter "C++ code example LaTeX to PNG conversion" LTX PNG BMP JPEG TIFF>}}
    System::SharedPtr<TeXOptions> options = TeXOptions::ConsoleAppOptions(TeXConfig::ObjectLaTeX());

    options->set_OutputWorkingDirectory(System::MakeObject<OutputFileSystemDirectory>(RunExamples::OutputDirectory));

    options->set_SaveOptions(System::MakeObject<{{output camel}}SaveOptions>());

    System::MakeObject<Aspose::TeX::TeXJob>(u"{{inputFile}}", System::MakeObject<ImageDevice>(), options)->Run();
{{< /app/tex/converter >}}
{{< /blocks/products/pf/agp/feature-section>}}

So, the first thing we need to do (well, sometimes not the very first) is to create an instance of the [TeXOptions](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options) class. The only static method that does this is [ConsoleAppOptions()](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#ad8aec9c3ff198c9b1e0f36927c44179d), so let's not be puzzled by the meaning of its name. The method takes an [instance](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_config#a8ee52115ae06cd6e97151a456a4dd5ea) of the [TeXConfig](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_config/) class, which is exactly suitable for converting a [LaTeX file](/tex/net/latex-io/#latex-file). This configuration tells the Object TeX engine to load the Object LaTeX format and to be ready to accept the LaTeX file. Object LaTeX format is actually just the [LaTeX](/tex/net/what-is-latex/) format, except that it uses [Object TeX](/tex/net/aspose-tex-and-object-tex/#object-tex) specific primitives to set up the page metrics.

The first of the required options is [OutputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#aa4f4ea6dab7db5ba1b40800495f16f63) which defines the space, or area, where the TeX output will be written. [Here](/tex/cpp/aspose-tex-output/) are the details about the output directory concept in **Aspose.TeX for C++**. In this example we use the [OutputFileSystemDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.output_file_system_directory) class, which lets us write the output to the specified directory, or folder.

The second option is a [SaveOptions](https://apireference.aspose.com/tex/net/aspose.tex.presentation/saveoptions) class instance which will control the transformation of the [object model](/tex/net/aspose-tex-and-object-tex/#why-the-new-tex-is-object) to the target format. Since we are converting LaTeX to PNG, it's the [PngSaveOptions](https://apireference.aspose.com/tex/cpp/class/aspose.te_x.presentation.image.png_save_options) class instance, which lets us specify the resolution of the output images.

Then we need to create an instance of the [TeXJob](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_job) class. Wanting to convert a LaTeX file stored in the file system, we use [this](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_job#a1c23c4138aca10b9cc6ae49d5cedc3db) version of the constructor. We need to specify the full path to the file. Otherwise, the engine will look for it in the current directory (which is [CurrentDirectory](https://docs.microsoft.com/en-us/dotnet/api/system.environment.currentdirectory)) and most likely will not find it. Nevertheless, we may omit the extension if our file has the *.tex* one. The engine will append it automatically. The second argument of the constructor is a [Device](https://reference.aspose.com/tex/cpp/class/aspose.te_x.presentation.device) class instance. Since we are converting LaTeX to PNG, it's an [ImageDevice](https://apireference.aspose.com/tex/cpp/class/aspose.te_x.presentation.image.image_device) class (which is common to all supported image formats) instance. As the last argument, we pass the recently prepared conversion options.

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
Output written on hello-world.png (1 page).
Transcript written on hello-world.log.
```

We will find other "fruits" of the engine's labor in the folder that we specified as the output directory. Those will be the transcript file and, **here it is!**, the main output PNG image file(s).

## **An alternative way to write main output PNG file(s)**

There is another way to get image data as an array of byte arrays, each array in the second dimension represents image data for a separate page.

```C++
    // Create conversion options for Object LaTeX format on Object TeX engine extension.
    System::SharedPtr<TeXOptions> options = TeXOptions::ConsoleAppOptions(TeXConfig::get_ObjectLaTeX());
    // Specify the file system working directory for the output.
    options->set_OutputWorkingDirectory(System::MakeObject<OutputFileSystemDirectory>(RunExamples::OutputDirectory));
    // Initialize the options for saving in PNG format.
    options->set_SaveOptions(System::MakeObject<PngSaveOptions>());
    // Run LaTeX to PNG conversion.
    System::SharedPtr<ImageDevice> device = System::MakeObject<ImageDevice>();
    System::MakeObject<TeXJob>(System::IO::Path::Combine(RunExamples::InputDirectory, u"hello-world.ltx"), device, options)->Run();
    
    // Save pages file by file.
    for (int32_t i = 0; i < device->get_Result()->get_Length(); i++)
    {
        {
            System::SharedPtr<System::IO::Stream> fs = System::IO::File::Open(System::IO::Path::Combine(RunExamples::OutputDirectory, System::String(u"page-") + (i + 1) + u".png"), System::IO::FileMode::Create);
            // Clearing resources under 'using' statement
            System::Details::DisposeGuard<1> __dispose_guard_0({ fs});
            // ------------------------------------------
            
            try
            {
                fs->Write(device->get_Result()[i], 0, device->get_Result()[i]->get_Length());
            }
            catch(...)
            {
                __dispose_guard_0.SetCurrentException(std::current_exception());
            }
        }
    }
```
The *"page-n.png"* file(s) will be written to any path we specify. Unlike [PDF output](/tex/cpp/latex-to-pdf/#an-alternative-way-to-write-main-output-pdf-file), they will duplicate the output PNG files written to the output directory.

## **About input options**

In case our main input file requires dependencies, for example, packages, that are not included in the basic LaTeX system and supported packages, we MUST set the [RequiredInputDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#a815cf18dc921a6ebeb6d2025e97ad003) option the similar way we set the [OutputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#aa4f4ea6dab7db5ba1b40800495f16f63) option and put the dependencies in that directory. Dependecies may be arbitrarily organized in subdirectories. In case we have our own files to include along the typesetting process, say external graphics files, we MUST also set the [InputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#a7c6f19c427b6cf0f07de087995293c2e) using the path to the location where those files are collected. We may also place the main input file somewhere inside the input directory and specify the relative path in the `run()` method (or specify no path at all if the main input file is in the root). [Here](/tex/cpp/aspose-tex-input/) are the details about the input directory concept in **Aspose.TeX for C++** and provided implementations.

Other TeX job options are discussed [here](/tex/cpp/other-options/).

**You may also check out the free LaTeX-to-PNG conversion [web app](https://products.aspose.app/tex/conversion/latex-to-png) built based on [Aspose.TeX for C++ API](https://products.aspose.com/tex/cpp/).**