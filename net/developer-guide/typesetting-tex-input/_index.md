---
title: Typesetting TeX input
type: docs
weight: 10
url: /net/typesetting-tex-input/
---
## **Typesetting TeX input**
Typesetting of TeX input runs by a single call of one of [Aspose.TeX.TeX.Typeset(...);](https://apireference.aspose.com/tex/net/aspose.tex/tex) methods. The way typesetting will be performed is defined by a [TeXOptions](https://apireference.aspose.com/tex/net/aspose.tex/texoptions) class instance passed as the argument. Also, all three methods accept a [Device](https://apireference.aspose.com/tex/net/aspose.tex.presentation/device) class instance which defines the output format. Two methods allow passing main TeX file as a stream or by a file name specification. The third one will prompt a file name online, i.e., from the console or whatever [IInputTerminal](https://apireference.aspose.com/tex/net/aspose.tex.io/iinputterminal) implementation you specify in options as input terminal.

### **Typesetting options**
[TeXOptions](https://apireference.aspose.com/tex/net/aspose.tex/texoptions) class provides the [factory method](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/methods/consoleappoptions) that returns the [TeXOptions](https://apireference.aspose.com/tex/net/aspose.tex/texoptions) instance with properties set to default values. Namely, the [TerminalIn](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/terminalin) property is set to be an [InputConsoleTerminal](https://apireference.aspose.com/tex/net/aspose.tex.io/inputconsoleterminal) class instance, the [TerminalOut](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/terminalout) is set to be a [OuputConsoleTerminal](https://apireference.aspose.com/tex/net/aspose.tex.io/outputconsoleterminal) class instance, and the [SaveOptions](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/saveoptions) is set to be an [XpsSaveOptions](https://apireference.aspose.com/tex/net/aspose.tex.presentation.xps/xpssaveoptions) class instance as XPS is supposed to be the default output format.

Below, we will take a look at some examples on various use cases to make understanding easier.

### **Reading TeX input from a file system directory, writing output to a file system directory, setting up XPS as a destination format, and writing terminal output to the console**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-FileSystemInputOutputAndXpsOutput-TakeInputFromFileSystem-WriteOutputToFileSystem-WriteTerminalOutputToConsole.cs" >}}

Here, the first thing we see is that the *ConsoleAppOptions()* factory method accepts *TeXConfig.ObjectTeX()* wich means that typesetting will run on the TeX engine extension called **Object TeX**. This extension contains auxiliary primitives to be capable of outputting to graphic formats. The default format is supposed to be the **plain TeX** plus **Object TeX**'s page size set to those of A4 paper sheets and content origin dimensions set to 1 inch for both horizontal and vertical.

Next, we see that **TeXOption's** [InputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/inputworkingdirectory) property is set be an [InputFileSystemDirectory](https://apireference.aspose.com/tex/net/aspose.tex.io/inputfilesystemdirectory) class instance defined by an absolute path of the directory that's supposed to be used for input.

The similar way, the [OutputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/outputworkingdirectory) property is set be an [OutputFileSystemDirectory](https://apireference.aspose.com/tex/net/aspose.tex.io/outputfilesystemdirectory) class instance defined by an absolute path of the directory that's supposed to be used for output.

Then the [TerminalOut](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/terminalout) property is unnecessarily set to its default (as we mentioned above) value.

Then, having it commented out, we show how terminal output can be written to memory, e.g., for complete suppression.

Next line is where the TeX engine (we mean TeX engine extension hereafter) comes to life. It reads *hello-world.tex* file from the [InputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/inputworkingdirectory) and writes output XPS file and transcript file to the [OutputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/outputworkingdirectory). To specify the output format, we use an [XpsDevice](https://apireference.aspose.com/tex/net/aspose.tex.presentation.xps/xpsdevice) instance.

The last line is added to make further console output appear on a new line.

### **Overriding the job name and writing terminal output to a file**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-OverridenJobNameAndTerminalOutputWrittenToDisc-OverrideJobName-WriteTerminalOutputToFileSystem.cs" >}}

This example is similar to the previous one. The first difference is that on the second line we specify so called job name which is one of important TeX's parameters. Having the [JobName](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/jobname) property initialized, the engine will take this name as a base for the output file, transcript file (log) and terminal output file in case the former one is being written to a file.

The second difference is that on the fifth line we specify the terminal output to be written to a file in [InputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/inputworkingdirectory).

### **Writing typeset XPS file to an external stream**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-TypesetXpsWrittenToExternalStream-WriteOutputXpsToExternalStream.cs" >}}

The new feature we use here is instantiation of [XpsDevice](https://apireference.aspose.com/tex/net/aspose.tex.presentation.xps/xpsdevice) using a stream object. In this case the output XPS file will be written to this stream, and the rest of output will be routed to the [OutputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/outputworkingdirectory) (except probably terminal output which can be routed separately).

### **Reading TeX input from a ZIP archive, writing output to a ZIP archive, setting up PDF as a destination format**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-ZipFileInputOuputAndPdfOutput-TakeInputFromZip-WriteOutputToZip.cs" >}}

Here the whole example is enclosed in two *using* clauses for two streams - an input stream on a ZIP archive that is supposed to be the TeX input source, and an output stream on a ZIP archive that is supposed to be the output destination.

The [InputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/inputworkingdirectory) and [OutputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/outputworkingdirectory) are set to be instances of [InputZipDirectory](https://apireference.aspose.com/tex/net/aspose.tex.io/inputzipdirectory) and [OutputZipDirectory](https://apireference.aspose.com/tex/net/aspose.tex.io/outputzipdirectory), respectively. Note that you can specify a subdirectory inside the input ZIP archive. If input files are located in the root, then pass an empty string to the [constructor](https://apireference.aspose.com/tex/net/aspose.tex.io/inputzipdirectory/constructors/main).

In this example we use [PdfDevice](https://apireference.aspose.com/tex/net/aspose.tex.presentation.pdf/pdfdevice) to specify that the output format must be PDF. To use this device, we must set the [SaveOptions](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/saveoptions) property to be a [PdfSaveOptions](https://apireference.aspose.com/tex/net/aspose.tex.presentation.pdf/pdfsaveoptions) class instance. This class has some properties for fine tuning of PDF output. To get familiar with these properties and their values, please refer to [Aspose.TeX.Presentation.Pdf](https://apireference.aspose.com/tex/net/aspose.tex.presentation.pdf) namespace documentation.

And the last line is necessary to finalize the output ZIP archive.

### **Writing terminal output to ZIP archive**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-OverridenJobNameAndTerminalOutputWrittenToZip-WriteTerminalOutputToZip.cs" >}}

By assignment of the [TerminalOut](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/terminalout) property we force terminal output to be written to a file in the output ZIP archive.

### **Writing typeset PDF file to an external stream**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-TypesetPdfWrittenToExternalStream-WriteOutputPdfToExternalStream.cs" >}}

Here we instantiate [PdfDevice](https://apireference.aspose.com/tex/net/aspose.tex.presentation.pdf/pdfdevice) class using a stream object, so that output PDF file will be written to this stream. In this case the stream will pass output to a file on your disk. There's also a commented option **2)** which will let you write the output PDF to a file in the [OutputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/outputworkingdirectory), i.e., in the output ZIP archive.

### **Reading main TeX file as a stream, reading terminal input, setting up an image format as a destination format**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-StreamInputImageOutputAndTerminalInput-TakeMainInputFromStream-AuxFromFileSystem-TakeTerminalInputFromConsole-AlternativeImagesStorage.cs" >}}

This example demonstrates the usage of the version of [Typeset(...);](https://apireference.aspose.com/tex/net/aspose.tex.tex/typeset/methods/1) method that accepts main TeX file as a stream. All other auxiliary input files will be taken from the
[InputWorkingDirectory](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/inputworkingdirectory).

Here we wanted to retrieve the typesetting result as a set of PNG images (pages). To do so, we passed an instance of [ImageDevice](https://apireference.aspose.com/tex/net/aspose.tex.presentation.image/imagedevice) and set the [SaveOptions](https://apireference.aspose.com/tex/net/aspose.tex/texoptions/properties/saveoptions) property to be a [PngSaveOptions](https://apireference.aspose.com/tex/net/aspose.tex.presentation.image/pngsaveoptions) class instance. To learn more about other implementations of [ImageSaveOptions](https://apireference.aspose.com/tex/net/aspose.tex.presentation.image/imagesaveoptions) please refer to [Aspose.TeX.Presentation.Image](https://apireference.aspose.com/tex/net/aspose.tex.presentation.image) namespace reference.

The last line shows the alternative way to retrieve output images from a page-by-page array of byte arrays.


