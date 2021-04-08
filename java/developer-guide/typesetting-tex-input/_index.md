---
title: Typesetting TeX input
type: docs
weight: 10
url: /java/typesetting-tex-input/
---
## **Typesetting TeX input**
Typesetting of TeX input runs by a single call of one of [com.aspose.tex.TeX.typeset(...);](https://apireference.aspose.com/tex/java/com.aspose.tex/TeX) methods. The way typesetting will be performed is defined by a [TeXOptions](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions) class instance passed as the argument. Also, all three methods accept a [Device](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/Device) class instance which defines the output format. Two methods allow passing main TeX file as a stream or by a file name specification. The third one will prompt a file name online, i.e., from the console or whatever [IInputTerminal](https://apireference.aspose.com/tex/java/com.aspose.tex/IInputTerminal) implementation you specify in options as input terminal.

### **Typesetting options**
[TeXOptions](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions) class provides the [factory method](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#consoleAppOptions-com.aspose.tex.TeXConfig-) that returns the [TeXOptions](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions) instance with properties set to default values. Namely, the [input terminal](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getTerminalIn--) property is set to be an [InputConsoleTerminal](https://apireference.aspose.com/tex/java/com.aspose.tex/InputConsoleTerminal) class instance, the [output terminal](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getTerminalOut--) is set to be an [OuputConsoleTerminal](https://apireference.aspose.com/tex/java/com.aspose.tex/OutputConsoleTerminal) class instance, and [save options](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getSaveOptions--) are set to be an [XpsSaveOptions](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/XpsSaveOptions) class options instance as XPS is supposed to be default output format.

Below, we will take a look at some examples on various use cases to make understanding easier.

### **Reading TeX input from a file system directory, writing output to a file system directory, setting up XPS as a destination format, and writing terminal output to the console**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-FileSystemInputOutputAndXpsOutput-TakeInputFromFileSystem-WriteOutputToFileSystem-WriteTerminalOutputToConsole.java" >}}

Here, the first thing we see is that the *consoleAppOptions()* factory method accepts *TeXConfig.objectTeX()* wich means that typesetting will run on a TeX engine extension called **Object TeX**. This extension contains auxiliary primitives to be capable of outputting to graphic formats. The default format is supposed to be **plain TeX** plus **Object TeX**'s page size set to those of A4 paper sheets and content origin dimensions set to 1 inch for both horizontal and vertical.

Next, we see that **TeXOption's** [input working directory](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getInputWorkingDirectory--) property is set be an [InputFileSystemDirectory](https://apireference.aspose.com/tex/java/com.aspose.tex/InputFileSystemDirectory) class instance defined by an absolute path of the directory that's supposed to be used for input.

The similar way, the [output working directory](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getOutputWorkingDirectory--) property is set be an [OutputFileSystemDirectory](https://apireference.aspose.com/tex/java/com.aspose.tex/OutputFileSystemDirectory) class instance defined by an absolute path of the directory that's supposed to be used for output.

Then the [output terminal](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getTerminalOut--) property is unnecessarily set to its default (as we mentioned above) value.

Then, having it commented out, we show how terminal output can be written to memory, e.g., for complete suppression.

Next line is where the TeX engine (we mean TeX engine extension hereafter) comes to life. It reads *hello-world.tex* file from the [input working directory](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getInputWorkingDirectory--) and writes output XPS file and transcript file to the [OutputWorkingDirectory](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getOutputWorkingDirectory--). To specify the output format, we use an [XpsDevice](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/XpsDevice) instance.

The last line is added to make further console output appear on a new line.

### **Overriding the job name and writing terminal output to a file**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-OverridenJobNameAndTerminalOutputWrittenToDisc-OverrideJobName-WriteTerminalOutputToFileSystem.java" >}}

This example is similar to the previous one. The first difference is that on the second line we specify so called job name which is one of important TeX's parameters. Having the [job name](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getJobName--) property initialized, the engine will take this name as a base for the output file, transcript file (log) and terminal output file in case the former one is being written to a file.

The second difference is that on the fifth line we specify the terminal output to be written to a file in the [input working directory](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getInputWorkingDirectory--).

### **Writing typeset XPS file to an external stream**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-TypesetXpsWrittenToExternalStream-WriteOutputXpsToExternalStream.java" >}}

The new feature we use here is the instantiation of [XpsDevice](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/XpsDevice) using a stream object. In this case the output XPS file will be written to this stream, and the rest of output will be routed to the [output working directory](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getOutputWorkingDirectory--) (except probably terminal output which can be routed separately).

### **Reading TeX input from a ZIP archive, writing output to a ZIP archive, setting up PDF as a destination format**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-ZipFileInputOuputAndPdfOutput-TakeInputFromZip-WriteOutputToZip.java" >}}

Here the whole example is enclosed in two *try ... finally* clauses for two streams - an input stream on a ZIP archive that is supposed to be the TeX input source, and an output stream on a ZIP archive that is supposed to be the output destination.

The [input working directory](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getInputWorkingDirectory--) and [output working directory](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getOutputWorkingDirectory--) are set to be instances of [InputZipDirectory](https://apireference.aspose.com/tex/java/com.aspose.tex/InputZipDirectory) and [OutputZipDirectory](https://apireference.aspose.com/tex/java/com.aspose.tex/OutputZipDirectory), respectively. Note that you can specify a subdirectory inside the input ZIP archive. If input files are located in the root, then pass an empty string to the [constructor](https://apireference.aspose.com/tex/java/com.aspose.tex/InputZipDirectory#InputZipDirectory-java.io.InputStream-java.lang.String-).

In this example we use [PdfDevice](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/PdfDevice) to specify that the output format must be PDF. To use this device we must set [save options](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getSaveOptions--) to be a [PdfSaveOptions](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/PdfSaveOptions) class instance. This class has some properties for fine tuning of PDF output. To get familiar with these properties and their values, please refer to [com.aspose.tex.rendering](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/package-frame) package documentation.

And the last line is necessary to finalize the output ZIP archive.

### **Writing terminal output to ZIP archive**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-OverridenJobNameAndTerminalOutputWrittenToZip-WriteTerminalOutputToZip.java" >}}

By assignment of the [output terminal](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getTerminalOut--) property we force terminal output to be written to a file in the output ZIP archive.

### **Writing typeset PDF file to an external stream**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-TypesetPdfWrittenToExternalStream-WriteOutputPdfToExternalStream.java" >}}

Here we instantiate [PdfDevice](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/PdfDevice) class using a stream object, so that output PDF file will be written to this stream. In this case stream will pass output to a file on your disk. There's also a commented option **2)** which will let you write the output PDF to a file in the [output working directory](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getOutputWorkingDirectory--), i.e., in the output ZIP archive.

### **Reading main TeX file as a stream, reading terminal input, setting up an image format as a destination format**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-StreamInputImageOutputAndTerminalInput-TakeMainInputFromStream-AuxFromFileSystem-TakeTerminalInputFromConsole-AlternativeImagesStorage.java" >}}

This example demonstrates the usage of the version of [typeset(...);](https://apireference.aspose.com/tex/java/com.aspose.tex/TeX#typeset-java.io.InputStream-com.aspose.tex.rendering.Device-com.aspose.tex.TeXOptions-) method that accepts main TeX file as a stream. All other auxiliary input files will be taken from 
the [input working directory](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getInputWorkingDirectory--).

Here we wanted to retrieve the typesetting result as a set of PNG images (pages). To do so, we passed an instance of [ImageDevice](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/ImageDevice) and set [save options](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getSaveOptions--) property to be a [PngSaveOptions](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/PngSaveOptions) class instance. To learn more about other implementations of [ImageSaveOptions](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/ImageSaveOptions) please refer to [com.aspose.tex.rendering](https://apireference.aspose.com/tex/java/com.aspose.tex.rendering/package-frame) package reference.

The last line shows the alternative way to retrieve output images from a page-by-page array of byte arrays.


