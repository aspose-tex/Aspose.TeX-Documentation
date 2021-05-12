---
title: Creating a custom TeX format
type: docs
weight: 10
url: /cpp/creating-custom-tex-format/
---
## **Creating a custom TeX format**

Suppose you want to have a number of documents designed in a similar way. To do so, you may introduce necessary definitions inside each TeX file. But to create your own TeX format would be a wiser approach.

{{< gist "aspose-com-gists" "d3eef38ac5b929503e8edee25e0873ce" "Aspose.TeX.Examples-CreateCustomTeXFormatFile.cpp" >}}

On the first line we again create a [TeXOptions](https://apireference.aspose.com/tex/cpp/aspose.tex/texoptions) class instance. This time we pass the *TeXConfig::get_ObjectIniTeX()* property value. This is the same as the *TeXConfig::ObjectTeX()* except that the **plain TeX** format is not loaded and **Object TeX**'s page metrics are not initialized, which lets you create your format from scratch.

Input and output are specified to be read/written from/to disk.

All the rest is done by the fourth line which runs format creation. The binary TeX format file will be written accordingly to you output working directory specification.

## **Typesetting with a custom format**

{{< gist "aspose-com-gists" "d3eef38ac5b929503e8edee25e0873ce" "Aspose.TeX.Examples-TypesetWithCustomTeXFormat.cpp" >}}

Here we create an [TeXOptions](https://apireference.aspose.com/tex/cpp/aspose.tex/texoptions) class instance providing the *TeXConfig::ObjectTeX()* defined by a format provider. The format provider itself is defined by an input working directory and a format name.

The rest of the example must be familiar to you if you have already looked through [Typesetting TeX input](/tex/cpp/typesetting-tex-input/) section.
