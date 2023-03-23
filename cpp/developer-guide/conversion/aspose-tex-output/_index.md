---
title: Aspose.TeX's output interface | C++
linktitle: Aspose.TeX's output interface
type: docs
weight: 16
url: /cpp/aspose-tex-output/
description: Conversion functionality of Aspose.TeX API solution for C++ with TeX, as an output format is explained here with the code examples.
---

Please, refer to **Aspose.TeX for C++** [API reference](https://reference.aspose.com/tex/cpp/namespace/aspose.te_x.i_o) for formal definitions of I/O implementation.

## **The concept of the output directory**
Since I/O primitives of the TeX language can only deal with file names, Aspose.TeX defines a directory as a mapping between names and bulks of data. The bulks of data are supposed to be files, or streams, or arrays, or whatever else. The API allows us to specify the input and output working directories separately. It provides the general [IOutputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.i_output_working_directory) interface for the output, which the user can implement for their own purposes. It also provides it's own implementations, which will be discussed below. The interface extends [IInputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.i_input_working_directory), since the engine may first create and write a file, and then read it back. The interface's own method [GetOutputFile()](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.i_output_working_directory#a53f4d029e1d19f0ecf87ae82b39b6697) returns the stream to write to, as opposed to the stream to read returned by [GetFile()](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.i_input_working_directory#adc0d6f35f9a0c426ba010779d90b5cd6).

### **Writing file output to the disk file system**

As we mentioned [above](/tex/cpp/latex-to-png/), the most common value for the [OutputDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#aa4f4ea6dab7db5ba1b40800495f16f63) would likely be an instance of the [OutputFileSystemDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.output_file_system_directory) class.

Here's how we would set it:

```C++
// Create conversion options instance.
...
// Specify a file system working directory for the output.
options->set_OutputWorkingDirectory(System::MakeObject<OutputFileSystemDirectory>(RunExamples::OutputDirectory));

```
This use case is quite simple, so there's no need to focus on it anymore.

### **Writing file output to a ZIP archive**

We can also create a file (or stream) and let the TeX engine use it as a ZIP archive to store the output files. Here it is:

```C++
    // Open the stream for the ZIP archive that will serve as the output working directory.
    System::SharedPtr<System::IO::Stream> outZipStream = System::IO::File::Open(System::IO::Path::Combine(RunExamples::OutputDirectory, u"zip-pdf-out.zip"), System::IO::FileMode::Create);

    // Create conversion options instance.
    ...
    // Specify a ZIP archive working directory for the output.
    options->set_OutputWorkingDirectory(System::MakeObject<OutputZipDirectory>(outZipStream));
```

First, we create an output stream for the ZIP file. Then, after creating the conversion options, we set the [OutputWorkingDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#aa4f4ea6dab7db5ba1b40800495f16f63) option to be an instance of the [OutputZipDirectory](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.output_zip_directory) class.

## **The concept of the output terminal**

There's another important part of the output --- the terminal output. As for this one, **Aspose.TeX for C++** defines the general [IOutputTerminal](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.i_output_terminal) interface having only one property that returns a [TextWriter](https://reference.aspose.com/tex/cpp/class/system.i_o.text_writer) implementation instance. Provided implementations are dicussed below.

### **Writing terminal output to the console**

To do this, we need to set the [TerminalOut](https://reference.aspose.com/tex/cpp/class/aspose.te_x.te_x_options#ad6ed0e8818801ed0ce2d5fdd1eeac51f) option to be an instance of the [OutputConsoleTerminal](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.output_console_terminal) class.

```C++
// Create conversion options instance.
...
// Specify the console as the output terminal.
options->set_TerminalOut(System::MakeObject<OutputConsoleTerminal>()); // Default. No need to specify.

```

Again, this is the default value of the option, so there's no real need to specify it. Due to this, this section serves only demonstration purposes.

### **Writing terminal output to file**

Unlike the input terminal, **Aspose.TeX for C++** provides an implementation of the [IOutputTerminal](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.i_output_terminal), which allows us to write the terminal output to a file in some output directory.

```C++
// Create conversion options instance.
...
// Specify that the terminal output must be written to a file in the output working directory.
// The file name is <job_name>.trm.
options->set_TerminalOut(System::MakeObject<OutputFileTerminal>(options->get_OutputWorkingDirectory()));

```
Here we ask the TeX engine to write the terminal output to the file with the name [<job_name>](/tex/net/tex-io/#tex-output).trm, which will be stored in the same output directory that we specified for rest of the output. But this is not necessary. We might as well pass any other instance of any implementation of [IOutputTerminal](https://reference.aspose.com/tex/cpp/class/aspose.te_x.i_o.i_output_terminal) to the constructor.