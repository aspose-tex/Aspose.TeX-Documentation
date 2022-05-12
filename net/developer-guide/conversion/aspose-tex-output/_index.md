---
title: Aspose.TeX's output interface | .NET
linktitle: Aspose.TeX's output interface
type: docs
weight: 15
url: /net/aspose-tex-output/
---

Please, refer to **Aspose.TeX for .NET** [API reference](https://apireference.aspose.com/tex/net/aspose.tex.io) for formal definitions of I/O implementation.

## **The concept of the output directory**
Since I/O primitives of the TeX language can only deal with file names, Aspose.TeX defines a directory as a mapping between names and bulks of data. The bulks of data are supposed to be files, or streams, or arrays, or whatever else. The API allows us to specify the input and output working directories separately. It provides the general [IOutputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex.io/ioutputworkingdirectory) interface for the output, which the user can implement for their own purposes. It also provides it's own implementations, which will be discussed below. The interface extends [IInputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex.io/iinputworkingdirectory), since the engine may first create and write a file, and then read it back. The interface's own method [GetOutputFile()](https://apireference.aspose.com/tex/net/aspose.tex.io/ioutputworkingdirectory/methods/getoutputfile) returns the stream to write to, as opposed to the stream to read returned by [GetFile()](https://apireference.aspose.com/tex/net/aspose.tex.io/iinputworkingdirectory/methods/getfile).

### **Writing file output to the disk file system**

As we mentioned [above](/tex/net/latex-to-png/), the most common value for the [OutputDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/outputworkingdirectory) would likely be an instance of the [OutputFileSystemDirectory](https://apireference.aspose.com/tex/net/aspose.tex.io/outputfilesystemdirectory) class.

Here's how we would set it:

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-OutputFileSystemDirectory.cs" >}}

This use case is quite simple, so there's no need to focus on it anymore.

### **Writing file output to a ZIP archive**

We can also create a file (or stream) and let the TeX engine use it as a ZIP archive to store the output files. Here it is:

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-OutputZipDirectory.cs" >}}

First, we create an output stream for the ZIP file. Then, after creating the conversion options, we set the [OutputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/outputworkingdirectory) option to be an instance of the [OutputZipDirectory](https://apireference.aspose.com/tex/net/aspose.tex.io/outputzipdirectory) class.

## **The concept of the output terminal**

There's another important part of the output --- the terminal output. As for this one, **Aspose.TeX for .NET** defines the general [IOutputTerminal](https://apireference.aspose.com/tex/net/aspose.tex.io/ioutputterminal) interface having only one property that returns a [TextWriter](https://docs.microsoft.com/en-us/dotnet/api/system.io.textwriter) implementation instance. Provided implementations are dicussed below.

### **Writing terminal output to the console**

To do this, we need to set the [TerminalOut](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/terminalout) option to be an instance of the [OutputConsoleTerminal](https://apireference.aspose.com/tex/net/aspose.tex.io/outputconsoleterminal) class.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-OutputConsoleTerminal.cs" >}}

Again, this is the default value of the option, so there's no real need to specify it. Due to this, this section serves only demonstration purposes.

### **Writing terminal output to file**

Unlike the input terminal, **Aspose.TeX for .NET** provides an implementation of the [IOutputTerminal](https://apireference.aspose.com/tex/net/aspose.tex.io/ioutputterminal), which allows us to write the terminal output to a file in some output directory.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-OutputFileTerminal.cs" >}} 

Here we ask the TeX engine to write the terminal output to the file with the name [<job_name>](/tex/net/tex-io/#tex-output).trm, which will be stored in the same output directory that we specified for rest of the output. But this is not necessary. We might as well pass any other instance of any implementation of [IOutputTerminal](https://apireference.aspose.com/tex/net/aspose.tex.io/ioutputterminal) to the constructor.