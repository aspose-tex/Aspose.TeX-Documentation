---
title: Other managing TeX options | Java
linktitle: Other options
type: docs
weight: 17
url: /java/other-options/
description: Conversion functionality of Aspose.TeX API solution for Java lets set the initial interaction mode in which the engine starts. Here are some code examples.
---

## **How to set the interaction mode**

As we mentioned [here](/tex/net/tex-io/#tex-interaction-modes), **Aspose.TeX for Java** allows us to set the initial interaction mode in which the engine starts. Here's how we do it:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-InteractionMode.java" >}}

## **How to set the job name**

When we pass the main input file as a file name, we get output files with the same name, although with another extensions. The TeX engine calls the input file's name the *job name* and uses it for output files, except in cases when auxilliary files with explicitly specified other names are written. When we pass the main input file as a [stream](/tex/java/other-ways-of-main-input/#providing-the-main-input-file-as-a-stream), the TeX engine uses the default job name, which is *texput*.
In both cases, we can override the job name by assigning the appropriate conversion option.

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-JobName.java" >}}

## **How to "stop time"**

LaTeX has a feature to automatically generate a title from some definitions in the preamble. This title normally contains the current date. We may wish to freeze the date in some desired value. Here's how it can be done:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-DateTime.java" >}}

## **How to ignore missing packages**

We may want to convert a LaTeX file that references some packages that are not supported by the Aspose.TeX for .NET library. In this case, the TeX engine will will halt with an error when trying to load such a package. To avoid this, we can use the following option:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-IgnoreMissingPackages.java" >}}

## **How to avoid building ligatures**

Normally, the TeX engine builds ligatures for certain pairs of characters if the font provides data required to do so. We can instruct the engine to skip ligature building with the following code:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-NoLigatures.java" >}}

## **How to repeat the job**

As we have mentioned [above](/tex/net/latex-io/#latex-input) regarding labels and references, there are cases when we may want to run the same job twice. Here is how it can be done:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-Repeat.java" >}}

## **How to turn math formulas to raster images**

Sometimes we may need to have math formulas as raster images rather then typed in fonts. The following option can serve for this purpose:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-RasterizeFormulas.java" >}}

## **How to turn graphics to raster images**

The ObjectTeX engine alows us to include graphic files in raster formats (PNG and JPG) as wel as PS(EPS) and XPS(OXPS) formats. The last two formats usually contain vector elements and texts. To have them rasterized and included as solid images, we can use the following option:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-RasterizeIncludedGraphics.java" >}}

## **How to subset fonts**

In case we want to reduce the size of the output file, we can resort to font subsetting, wich means that the fonts in the output document will only contain data about the glyphs that are used in the document. Here's how we can solve this:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-SubsetFonts.java" >}}