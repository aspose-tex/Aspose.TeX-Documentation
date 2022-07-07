---
title: Aspose.TeX's input interface | C++
linktitle: Aspose.TeX's input interface
type: docs
weight: 14
url: /cpp/aspose-tex-input/
description: Conversion functionality of Aspose.TeX API solution for C++ with TeX, as an input format is explained here with the code examples.
---

Please, refer to **Aspose.TeX for C++** [API reference](https://reference.aspose.com/tex/cpp/namespace/aspose.te_x.i_o) for formal definitions of I/O implementation.

## **The concept of the input directory**
Since I/O primitives of the TeX language can only deal with file names, **Aspose.TeX for C++** defines a directory as a mapping between names and bulks of data. The bulks of data are supposed to be files, or streams, or arrays, or whatever else. The API allows us to specify the input and output working directories separately. It provides the general [IInputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.i_input_working_directory) interface, which the user can implement for their own purposes. It also provides its own implementations, which will be discussed below. The interface defines the [GetFile()](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.i_input_working_directory#adc0d6f35f9a0c426ba010779d90b5cd6) method, which returns the data stream and determines the full name of the file, while taking some, hypothetically different, name as the first agrument, which, in fact, is the mapping key.

### **Getting file input from the disk file system**

Here's how we would do it:

```C++
// Create conversion options instance.
...
// Specify a file system working directory for input.
options->set_InputWorkingDirectory(System::MakeObject<InputFileSystemDirectory>(RunExamples::InputDirectory));

```

This use case is quite simple, so there's no need to focus on it anymore.

### **Getting file input from a ZIP archive**

We can also put the input files in a ZIP archive and consider it an input directory. In this case, we should proceed as follows:

```C++
    // Open a stream on a ZIP archive that will serve as the input working directory.
    System::SharedPtr<System::IO::Stream> inZipStream = System::IO::File::Open(System::IO::Path::Combine(RunExamples::InputDirectory, u"zip-in.zip"), System::IO::FileMode::Open);

    // Create conversion options instance.
    ...
    // Specify a ZIP archive working directory for input.
    options->set_InputWorkingDirectory(System::MakeObject<InputZipDirectory>(inZipStream, u"in"));
```

First, we create the stream containing the ZIP file. Then, after creating the conversion options, we set the [InputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#a7c6f19c427b6cf0f07de087995293c2e) option to be an instance of the [InputZipDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.input_zip_directory) class. The second argument of the constructor is the base path inside the archive. If we want the entire archive to be an input directory, we should pass the empty string. 

## **The concept of the input terminal**

Now it's time to remember that there is also the terminal input. As for this one, **Aspose.TeX for C++** defines the general [IInputTerminal](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.i_input_terminal) interface having only one property that returns a  [TextReader](https://reference.aspose.com/tex/cpp/class/system.i_o.text_reader) implementation instance. Provided implementations are dicussed below.

### **Getting terminal input from the console**

To do this, we need to set the [TerminalIn](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#accef67ee56635f27198fce16af16195c) option to be an instance of the [InputConsoleTerminal](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.input_console_terminal) class.

```C++
// Create conversion options instance.
...
// Specify the console as the input terminal.
options->set_TerminalIn(System::MakeObject<InputConsoleTerminal>()); // Default. Not necessary to specify.

```

But, to tell you the truth, this is the default value of the option, so there's no real need to specify it. :-) Due to this fact, and as long as there are no other implementations, this section serves only demonstration purposes.

Theoretically, if we have an interactive TeX file (or script) with predictable behavior, we may want to implement a version of the input terminal which would contain a complementary script for responding to the TeX engine's requests. Try your hand when you have time!