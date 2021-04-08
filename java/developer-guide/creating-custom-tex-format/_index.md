---
title: Creating a custom TeX format
type: docs
weight: 10
url: /java/creating-custom-tex-format/
---
## **Creating a custom TeX format**

Suppose you want to have a number of documents designed in a similar way. To do so, you may introduce necessary definitions inside each TeX file. But to create your own TeX format would be a wiser approach.

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-CreateCustomTeXFormatFile.java" >}}

On the first line we again create a [TeXOptions](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions) class instance. This time we pass the *TeXConfig.objectIniTeX()* value. This is the same as the *TeXConfig.objectTeX()* except that the **plain TeX** format is not loaded and **Object TeX**'s page metrics are not initialized, which lets you create your format from scratch.

Input and output are specified to be read/written from/to disk.

All the rest is done by the fourth line which runs format creation. The binary TeX format file will be written accordingly to you output working directory specification.

## **Typesetting with a custom format**

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-TypesetWithCustomTeXFormat.java" >}}

Here we create [TeXOptions](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXOptions) class instance providing the *TeXConfig.objectTeX()* defined by a format provider. The format provider itself is defined by an input working directory and a format name.

The rest of the example must be familiar to you if you have already looked through [Typesetting TeX input](/tex/java/typesetting-tex-input/) section.
