---
title: Aspose.TeX's input interface
type: docs
weight: 14
url: /net/aspose-tex-input/
---

Please, refer to **Aspose.TeX for .NET** [API reference](https://apireference.aspose.com/tex/net/aspose.tex.io) for formal definitions of I/O implementation.

## **The concept of the input directory**
Since I/O primitives of the TeX language can only deal with file names, **Aspose.TeX for .NET** defines a directory as a mapping between names and bulks of data. The bulks of data are supposed to be files, or streams, or arrays, or whatever else. The API allows us to specify the input and output working directories separately. It provides the general [IInputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex.io/iinputworkingdirectory) interface, which the user can implement for their own purposes. It also provides its own implementations, which will be discussed below. The interface defines the [GetFile()](https://apireference.aspose.com/tex/net/aspose.tex.io/iinputworkingdirectory/methods/getfile) method, which returns the data stream and determines the full name of the file, while taking some, hypothetically different, name as the first agrument, which, in fact, is the mapping key.

### **Getting file input from the disk file system**

Here's how we would do it:

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-InputFileSystemDirectory.cs" >}}

This use case is quite simple, so there's no need to focus on it anymore.

### **Getting file input from a ZIP archive**

We can also put the input files in a ZIP archive and consider it an input directory. In this case, we should proceed as follows:

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-InputZipDirectory.cs" >}}

First, we create the stream containing the ZIP file. Then, after creating the conversion options, we set the [InputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/inputworkingdirectory) option to be an instance of the [InputZipDirectory](https://apireference.aspose.com/tex/net/aspose.tex.io/inputzipdirectory) class. The second argument of the constructor is the base path inside the archive. If we want the entire archive to be an input directory, we should pass the empty string. 

## **The concept of the input terminal**

Now it's time to remember that there is also the terminal input. As for this one, **Aspose.TeX for .NET** defines the general [IInputTerminal](https://apireference.aspose.com/tex/net/aspose.tex.io/iinputterminal) interface having only one property that returns a  [TextReader](https://docs.microsoft.com/en-us/dotnet/api/system.io.textreader) implementation instance. Provided implementations are dicussed below.

### **Getting terminal input from the console**

To do this, we need to set the [TerminalIn](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/terminalin) option to be an instance of the [InputConsoleTerminal](https://apireference.aspose.com/tex/net/aspose.tex.io/inputconsoleterminal) class.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-InputConsoleTerminal.cs" >}}

But, to tell you the truth, this is the default value of the option, so there's no real need to specify it. :-) Due to this fact, and as long as there are no other implementations, this section serves only demonstration purposes.

Theoretically, if we have an interactive TeX file (or script) with predictable behavior, we may want to implement a version of the input terminal which would contain a complementary script for responding to the TeX engine's requests. Try your hand when you have time!