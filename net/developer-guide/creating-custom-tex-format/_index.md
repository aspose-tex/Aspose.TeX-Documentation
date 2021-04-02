---
title: Creating a custom TeX format
type: docs
weight: 10
url: /net/creating-custom-tex-format/
---
## **Creating a custom TeX format**

Suppose you want to have a number of documents designed in a similar way. To do so, you may introduce necessary definitions inside each TeX file. But to create your own TeX format would be a wiser approach.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-CreateCustomTeXFormatFile.cs" >}}

On the first line we again create [TeXOptions](https://apireference.aspose.com/tex/net/aspose.tex/texoptions) class instance. This time we pass *TeXConfig.ObjectIniTeX* property value. This is the same is *TeXConfig.ObjectTeX()* except that **plain TeX** format is not loaded and **Object TeX**'s page metrics are not initialized, which lets you create your format from scratch.

Input and output are specified to be taken/retrieved from/to disc.

All the rest is done by the fourth line which runs format creation. The binary TeX format file will be written accordingly to you output working directory specification.

## **Typesetting with a custom format**

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-TypesetWithCustomTeXFormat.cs" >}}

Here we create [TeXOptions](https://apireference.aspose.com/tex/net/aspose.tex/texoptions) class instance providing *TeXConfig.ObjectTeX()* defined by a format provider. The format provider itself is defined by an input working directory and a format name.

The rest of the example must be familiar to you if you have already looked through [Typesetting TeX input](/tex/net/typesetting-tex-input/) section.
