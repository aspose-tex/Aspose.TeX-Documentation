---
title: Other TeX conversion output formats | C++
linktitle: Other TeX formats
type: docs
weight: 18
url: /cpp/other-tex-formats/
description: Conversion functionality of Aspose.TeX API solution for C++ allows converting LaTeX files as well as your own custom TeX files. Here are some code examples.
---

It's highly unlikely that you will currently want to convert a TeX file written in any other format than LaTeX. But this is possible if you are studying the TeX language and/or internals for some reason. Anyway, **Aspose.TeX for C++** allows you to convert files written in Plain TeX format. It also allows you to create custom formats and typeset documents designed in these formats.

We will start with creating a custom format.

## **Creating a custom format**

Let's remember that the format file is a binary dump of the TeX engine's internal state.

```C++
// Create typesetting options for no format on ObjectTeX engine extension.
System::SharedPtr<TeXOptions> options = TeXOptions::ConsoleAppOptions(TeXConfig::get_ObjectIniTeX());
// Specify a file system working directory for input.
options->set_InputWorkingDirectory(System::MakeObject<InputFileSystemDirectory>(RunExamples::InputDirectory));
// Specify a file system working directory for output.
options->set_OutputWorkingDirectory(System::MakeObject<OutputFileSystemDirectory>(RunExamples::OutputDirectory));
    
// Run format creation.
Aspose::TeX::TeXJob::CreateFormat(u"customtex", options);
    
// For further output to look write.
options->get_TerminalOut()->get_Writer()->WriteLine();
```
As you can see, the code is similar to the code for converting a TeX file. But there are a few differences.

First, here we use the [TeXConfig.ObjectIniTeX](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_config#aefa7bbdf2ed28d6499f2dc5d5ad2ca3e) job configuration. This is a special configuration that leaves the engine's state "virgin", i.e., the internal parameters have their default values, and the set of control sequences coincides with the set of primitives. In our example, the set of primitives is extended in the sense mentioned [here](/tex/net/aspose-tex-and-object-tex/#object-tex).

Next, we set up the input and output working directories as usual. The input working directory needs to contain the main format source file and all its dependencies.

And the second key difference is the way we run the job. This time we use the static [CreateFormat()](https://apireference.aspose.com/tex/net/aspose.tex/texjob/methods/createformat) method, which together with the options takes the name of the main source file, that must be the same as the format name.

## **Typesetting a TeX file in your custom format**

Now that we have our own TeX format, we want to typeset a TeX file written in this format. Here is the code:

```C++
// Create typesetting options for a custom format on ObjectTeX engine extension.
System::SharedPtr<TeXOptions> options = TeXOptions::ConsoleAppOptions(TeXConfig::ObjectTeX(formatProvider));
options->set_JobName(u"typeset-with-custom-format");
// Specify the input working directory.
options->set_InputWorkingDirectory(wd);
// Specify a file system working directory for output.
options->set_OutputWorkingDirectory(System::MakeObject<OutputFileSystemDirectory>(RunExamples::OutputDirectory));
            
// Run typesetting.
System::MakeObject<Aspose::TeX::TeXJob>(System::MakeObject<System::IO::MemoryStream>(System::Text::Encoding::get_ASCII()->GetBytes(u"Congratulations! You have successfully typeset this text with your own TeX format!\\end")), System::MakeObject<XpsDevice>(), options)->Run();
            
// For further output to look write.
options->get_TerminalOut()->get_Writer()->WriteLine();
```
Obviously, we have to specify the format somehow. First of all, we need to create an instance of the [FormatProvider](https://apireference.aspose.com/tex/cpp/class/aspose.te_x.resource_providers.format_provider) class. Then, in options constructor, we use the [TeXConfig.ObjectTeX()](https://apireference.aspose.com/tex/cpp/class/aspose.te_x.te_x_config#aefa7bbdf2ed28d6499f2dc5d5ad2ca3e) configuration, which takes our format provider as an argument and loads the format on top of the "virgin" state of the engine.

The rest of the code should be familiar to you. It uses the features discussed earlier in this [guide](/tex/cpp/conversion/).

## **Typesetting a TeX file in Plain TeX format**

If we throw away the format provider from the code just demonstrated, the engine will load the default format, which is [Object TeX](/tex/net/aspose-tex-and-object-tex/) in its fourth sense. Thus, if you have a TeX file written in Plain TeX format, this way you may convert it to any supported target format.