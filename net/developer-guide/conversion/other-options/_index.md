---
title: Other options
type: docs
weight: 17
url: /net/other-options/
---

## **How to set the interaction mode**

As we mentioned [here](/tex/net/tex-io/#tex-interaction-modes), **Aspose.TeX for .NET** lets us set the initial interaction mode in which the engine starts. Here's how we do it:

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-InteractionMode.cs" >}}

## **How to set the job name**

When we pass the main input file as a file name, we get output files with the same name, although with another extensions. The TeX engine calls the input file's name the *job name* and uses it for output files, except in cases when auxilliary files with explicitly specified other names are written. When we pass the main input file as a [stream](/tex/net/other-ways-of-main-input/#providing-the-main-input-file-as-a-stream), the TeX engine uses the default job name, which is *texput*.
In both cases, we can override the job name by assigning the appropriate conversion option.

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-JobName.cs" >}}

## **How to repeat the job**

As we have mentioned [above](/tex/net/latex-io/#latex-input) regarding labels and references, there are cases when we would like to run the same job twice. Here is how it can be done:

{{< gist "aspose-com-gists" "76c7e5770ac8b3f6d409f6ec60f02030" "Aspose.TeX.Examples-Conversion-Repeat.cs" >}}