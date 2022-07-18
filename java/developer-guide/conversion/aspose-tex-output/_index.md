---
title: Aspose.TeX's output interface | Java
linktitle: Aspose.TeX's output interface
type: docs
weight: 15
url: /java/aspose-tex-output/
description: Conversion functionality of Aspose.TeX API solution for Java with TeX, as an output format is explained here with the code examples.
---

Please, refer to **Aspose.TeX for Java** [API reference](https://reference.aspose.com/tex/java/com.aspose.tex/package-frame) for formal definitions of I/O implementation.

## **The concept of the output directory**
Since I/O primitives of the TeX language can only deal with file names, Aspose.TeX defines a directory as a mapping between names and bulks of data. The bulks of data are supposed to be files, or streams, or arrays, or whatever else. The API allows us to specify the input and output working directories separately. It provides the general [IOutputWorkingDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/IOutputWorkingDirectory) interface for the output, which the user can implement for their own purposes. It also provides it's own implementations, which will be discussed below. The interface extends [IInputWorkingDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/IInputWorkingDirectory), since the engine may first create and write a file, and then read it back. The interface's own method [getOuputFile()](https://reference.aspose.com/tex/java/com.aspose.tex/IOutputWorkingDirectory#getOutputFile-java.lang.String-java.lang.String:A-) returns the stream to write to, as opposed to the stream to read returned by [getFile()](https://reference.aspose.com/tex/java/com.aspose.tex/IInputWorkingDirectory#getFile-java.lang.String-java.lang.String:A-boolean-).

### **Writing file output to the disk file system**

As we mentioned [above](/tex/java/latex-to-png/), the most common value for the [OutputWorkingDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getOutputWorkingDirectory--) would likely be an instance of the [OutputFileSystemDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/OutputFileSystemDirectory) class.

Here's how we would set it:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-OutputFileSystemDirectory.java" >}}

This use case is quite simple, so we won't dwell on it for a long time.

### **Writing file output to a ZIP archive**

We can also create a file (or stream) and let the TeX engine use it as a ZIP archive to store the output files. Here it is:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-OutputZipDirectory.java" >}}

First, we create an output stream for the ZIP file. Then, after creating the conversion options, we set the [OutputWorkingDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getOutputWorkingDirectory--) option to be an instance of the [OutputZipDirectory](https://reference.aspose.com/tex/java/com.aspose.tex/OutputZipDirectory) class.

## **The concept of the output terminal**

There's another important part of the output --- the terminal output. As for this one, **Aspose.TeX for Java** defines the general [IOutputTerminal](https://reference.aspose.com/tex/java/com.aspose.tex/IOutputTerminal) interface having two methods. One of them returns a [BufferedWriter](https://docs.oracle.com/javase/6/docs/api/java/io/BufferedWriter.html) instance. Another one returns an [OutputStream](https://docs.oracle.com/javase/6/docs/api/java/io/OutputStream.html) instance as the underlying stream. Provided implementations of the interface are dicussed below.

### **Writing terminal output to the console**

To do this, we need to set the [TerminalOut](https://reference.aspose.com/tex/java/com.aspose.tex/TeXOptions#getTerminalOut--) option to be an instance of the [OutputConsoleTerminal](https://reference.aspose.com/tex/java/com.aspose.tex/OutputConsoleTerminal) class.

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-OutputConsoleTerminal.java" >}}

Again, this is the default value of the option, so there's no real need to specify it. Due to this, this section serves only demonstration purposes.

### **Writing terminal output to file**

Unlike the input terminal, **Aspose.TeX for Java** provides an implementation of the [IOutputTerminal](https://reference.aspose.com/tex/java/com.aspose.tex/IOutputTerminal), which allows us to write the terminal output to a file in some output directory.

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-OutputFileTerminal.java" >}} 

Here we ask the TeX engine to write the terminal output to the file with the name [<job_name>](/tex/net/tex-io/#tex-output).trm, which will be stored in the same output directory that we specified for rest of the output. But this is not necessary. We might as well pass any other instance of any implementation of [IOutputTerminal](https://reference.aspose.com/tex/java/com.aspose.tex/IOutputTerminal) to the constructor.