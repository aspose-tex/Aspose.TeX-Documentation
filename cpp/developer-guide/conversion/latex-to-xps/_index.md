---
title: LaTeX to XPS | C++
linktitle: LaTeX to XPS
type: docs
weight: 12
url: /cpp/latex-to-xps/
description: Conversion functionality of Aspose.TeX API solution for C++ lets convert LaTeX files to teh XPS format. Here are some code examples.
lastmod: "2023-03-23"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---

Another target format supported by **Aspose.TeX** is [**XPS**](https://en.wikipedia.org/wiki/Open_XML_Paper_Specification). An **XPS** file is actually a ZIP package that contains paginated content of a document, together with the metadata required for proper display by specific viewers (such as Windows XPS Viewer) and printing. All data in a package is represented by files. Some of them are binary and contain resources such as images, fonts, and ICC profiles. Others are XML files in various specific schemas. The latter include files that contain the document data itself. Document data consists of a set of files - each file contains data for an individual page of the document. Such files consist of a single page element and a tree of child elements - *Canvas*, *Path* and *Glyphs*. *Canvas* is a grouping element that can contain other *Canvases*, *Paths* and *Glyphs*. Its mission is to control the appearance of all child elements as a group. *Path* elements are used to define vector graphics paths. And *Glyphs* elements are used to define textual content. All three elements have properties to define various aspects of appearance.

## **How to convert LaTeX to XPS**

The conversion to XPS is just as simple as the [conversion to raster image formats](/tex/cpp/latex-to-image/), except that in addition to the [SaveOptions](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#ad9ff9be81f8d554a507dd48ec1c583f7), we have to change the device to an instance of the [XpsDevice](https://reference.aspose.com/tex/cpp/class/aspose.te_x.presentation.xps.xps_device) class.

```C++
...
// Initialize the options for saving in Xps format.
options->set_SaveOptions(System::MakeObject<XpsSaveOptions>());

System::MakeObject<Aspose::TeX::TeXJob>(u"hello-world.ltx", System::MakeObject<XpsDevice>(), options)->Run();
```

### **An alternative way to write main output XPS file**

There's another constructor of the [XpsDevice](https://reference.aspose.com/tex/cpp/class/aspose.te_x.presentation.xps.xps_device#aa24d2c38c5d134d90782b27ba090116a) class, which lets us get the resulting XPS file in an alternative way.

```C++
    // Create the stream to write the XPS file to.
    {
        System::SharedPtr<System::IO::Stream> xpsStream = System::IO::File::Open(System::IO::Path::Combine(RunExamples::OutputDirectory, u"any-name.xps"), System::IO::FileMode::Create);
        // Clearing resources under 'using' statement
        System::Details::DisposeGuard<1> __dispose_guard_0({ xpsStream});
        // ------------------------------------------
        
        try
        {
            // Create conversion options for Object LaTeX format on Object TeX engine extension.
            System::SharedPtr<TeXOptions> options = TeXOptions::ConsoleAppOptions(TeXConfig::get_ObjectLaTeX());
            // Specify the file system working directory for the output.
            options->set_OutputWorkingDirectory(System::MakeObject<OutputFileSystemDirectory>(RunExamples::OutputDirectory));
            // Initialize the options for saving in XPS format.
            options->set_SaveOptions(System::MakeObject<XpsSaveOptions>());
            // Default value.
            // Run LaTeX to XPS conversion.
            System::MakeObject<TeXJob>(System::IO::Path::Combine(RunExamples::InputDirectory, u"hello-world.ltx"), System::MakeObject<XpsDevice>(xpsStream), options)->Run();
        }
        catch(...)
        {
            __dispose_guard_0.SetCurrentException(std::current_exception());
        }
    }
```

The effect is the same as we get [here](/tex/cpp/latex-to-pdf/#an-alternative-way-to-write-main-output-pdf-file).

**You may also check out the free LaTeX-to-XPS conversion [web app](https://products.aspose.app/tex/conversion/latex-to-xps) built based on [Aspose.TeX for .NET](https://products.aspose.com/tex/net/) API. [Here](https://products.aspose.com/tex/cpp/) is the C++ version page.**