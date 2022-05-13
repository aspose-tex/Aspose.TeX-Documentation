---
title: Other TeX conversion output formats | Java
linktitle: Other TeX formats
type: docs
weight: 18
url: /java/other-tex-formats/
description: Conversion functionality of Aspose.TeX API solution for Java allows converting LaTeX files as well as your own custom TeX files. Here are some code examples.
---

It's highly unlikely that you will currently want to convert a TeX file written in any other format than LaTeX. But this is possible if you are studying the TeX language and/or internals for some reason. Anyway, **Aspose.TeX for Java** allows you to convert files written in Plain TeX format. It also allows you to create custom formats and typeset documents designed in these formats.

We will start with creating a custom format.

## **Creating a custom format**

Let's remember that the format file is a binary dump of the TeX engine's internal state.

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-CreateCustomTeXFormatFile.java" >}}

As you can see, the code is similar to the code for converting a TeX file. But there are a few differences.

First, here we use the [TeXConfig.objectIniTeX()](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXConfig#objectIniTeX--) job configuration. This is a special configuration that leaves the engine's state "virgin", i.e., the internal parameters have their default values, and the set of control sequences coincides with the set of primitives. In our example, the set of primitives is extended in the sense mentioned [here](/tex/net/aspose-tex-and-object-tex/#object-tex).

Next, we set up the input and output working directories as usual. The input working directory needs to contain the main format source file and all its dependencies.

And the second key difference is the way we run the job. This time we use the static [createFormat()](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXJob#createFormat-java.lang.String-com.aspose.tex.TeXOptions-) method, which together with the options takes the name of the main source file, that must be the same as the format name.

## **Typesetting a TeX file in your custom format**

Now that we have our own TeX format, we want to typeset a TeX file written in this format. Here is the code:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-TypesetWithCustomTeXFormat.java" >}}

Obviously, we have to specify the format somehow. First of all, we need to create an instance of the [FormatProvider](https://apireference.aspose.com/tex/java/com.aspose.tex/FormatProvider) class. Then, in options constructor, we use the [TeXConfig.objectTeX()](https://apireference.aspose.com/tex/java/com.aspose.tex/TeXConfig#objectTeX--) configuration, which takes our format provider as an argument and loads the format on top of the "virgin" state of the engine.

The rest of the code should be familiar to you. It uses the features discussed earlier in this [guide](/tex/java/conversion/).

## **Typesetting a TeX file in Plain TeX format**

If we throw away the format provider from the code just demonstrated, the engine will load the default format, which is [Object TeX](/tex/net/aspose-tex-and-object-tex/) in its fourth sense. Thus, if you have a TeX file written in Plain TeX format, this way you may convert it to any supported target format.