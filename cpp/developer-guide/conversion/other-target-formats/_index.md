---
title: Other target conversion formats | C++
linktitle: Other target formats
type: docs
weight: 12
url: /cpp/other-target-formats/
description: Conversion functionality of Aspose.TeX API solution for C++ lets convert LaTeX files to a number of other raster image formats. Here are some code examples.
---

## **Image formats**

**Aspose.TeX for C++** also allows us to convert LaTeX files to a number of other raster image formats. Just in case. All these conversions are performed in the similar way as converting [LaTeX to PNG](/tex/cpp/latex-to-png/) using the [ImageDevice](https://reference.aspose.com/tex/cpp/class/aspose.te_x.presentation.image.image_device). The only difference is in the type of the [SaveOptions](https://reference.aspose.com/tex/net/aspose.tex/texoptions/properties/saveoptions) property in the conversion options.

We will not sink deep into details just because there are actually no details.

### **How to convert LaTeX to JPEG**

```C++
...
// Initialize the options for saving in JPEG format.
options->set_SaveOptions(System::MakeObject<JpegSaveOptions>());
```

**You may also check out the free LaTeX-to-JPEG conversion [web app](https://products.aspose.app/tex/conversion/latex-to-jpg) built based on [Aspose.TeX for C++ API](https://products.aspose.com/tex/cpp/).**

### **How to convert LaTeX to TIFF**

```C++
...
// Initialize the options for saving in TIFF format.
options->set_SaveOptions(System::MakeObject<TiffSaveOptions>());
```

**You may also check out the free LaTeX-to-TIFF conversion [web app](https://products.aspose.app/tex/conversion/latex-to-tiff) built based on [Aspose.TeX for C++ API](https://products.aspose.com/tex/cpp/).**

### **How to convert LaTeX to BMP**

```C++
...
// Initialize the options for saving in BMP format.
options->set_SaveOptions(System::MakeObject<BmpSaveOptions>());
```

**You may also check out the free LaTeX-to-BMP conversion [web app](https://products.aspose.app/tex/conversion/latex-to-bmp) built based on [Aspose.TeX for C++ API](https://products.aspose.com/tex/cpp/).**

## **How to convert LaTeX to XPS**

Another target format is [XPS](https://en.wikipedia.org/wiki/Open_XML_Paper_Specification). The conversion to XPS is just as simple, except that in addition to the [SaveOptions](https://reference.aspose.com/tex/net/aspose.tex/texoptions/properties/saveoptions), we have to change the device to an instance of the [XpsDevice](https://reference.aspose.com/tex/cpp/class/aspose.te_x.presentation.xps.xps_device) class.

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

**You may also check out the free LaTeX-to-XPS conversion [web app](https://products.aspose.app/tex/conversion/latex-to-xps) built based on [Aspose.TeX for C++ API](https://products.aspose.com/tex/cpp/).**