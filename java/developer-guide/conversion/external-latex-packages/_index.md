---
title: External LaTeX packages | Java
linktitle: External LaTeX packages
type: docs
weight: 19
url: /java/external-latex-packages/
description: Aspose.TeX API for Java allows the use of external packages, i.e. the ones that aren't included in the library itself like fancybox or pgfplots packages.
lastmod: "2023-03-23"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---

## **External LaTeX packages**

There is a number of [common LaTeX packages](/tex/net/embedded-packages/) included in the **Aspose.TeX** library for Java. So you don't have to take care about how to provide these packages to the library's TeX engine. But sometimes (maybe often) your LaTeX file may require a package beyond the "natively" supported "bundle" of packages. In this case, you can try to provide the required input, i.e. required package's source files, using the [setRequiredInputDirectory()](https://reference.aspose.com/tex/java/com.aspose.tex/texoptions/#setRequiredInputDirectory-com.aspose.tex.IInputWorkingDirectory-) method of the [TeXOptions](https://reference.aspose.com/tex/java/com.aspose.tex/texoptions/) class instance. We will see how this works with two examples.

### **Unpacked required input (`fancybox` package)**

Let's say we have the following simple LaTeX file, which is `required-input-fs.tex` from our [example solution](https://github.com/aspose-tex/Aspose.TeX-for-Java):

```tex
\documentclass{article}
\usepackage[a6paper,landscape]{geometry}
\usepackage{fancybox}
\begin{document}
Test: \fbox{
  \begin{Bitemize}[b]
  \item First item
  \item A second one\\ on two lines
  \item(2pt) A third with extra space
  \end{Bitemize}
}
\par\bigskip
Test: \fbox{
  \begin{Beqnarray}[t]
  y & = & x^2 \\
  a^2 + 2ab + b^2 & = & (a + b)^2 \\
  \int_0^\infty e^{-ax} dx & = & \frac{1}{a}
  \end{Beqnarray}
}
\end{document}
```

On the 3rd line, we see that the file requires the `fancybox` package, which is not "natively" supported. We also assume that we have the `fancybox` package source file. It is a simple package, so it really consists of just one file. We can place this file anywhere in our file system and specify the directory path as simply as follows:

```Java
options.setRequiredInputDirectory(new InputFileSystemDirectory("path-to-directory-where-fancybox.sty-located"));
```

After running a TeX job with this option (don't forget to adjust the other options as needed), we get the output document (i.e., a PNG image).

![](Conversion-RequiredInputFs.png)

Here is the complete source code for the example:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-RequiredInput-FileSystem.java" >}}

### **Archived required input (`pgfplots` package)**

Let's now assume that we have the following also quite simple LaTeX file, which is `required-input-zip.tex` from our example solution:
```tex
\documentclass{article}
\usepackage[margin=0.25in]{geometry}
\usepackage{pgfplots}
\pgfplotsset{width=10cm,compat=1.18}
\begin{document}

First example is 2D and 3D math expressions plotted side-by-side.

%Here begins the 2D plot
\begin{tikzpicture}
\begin{axis}
\addplot[color=red]{exp(x)};
\end{axis}
\end{tikzpicture}
%Here ends the 2D plot
\hskip 5pt
%Here begins the 3D plot
\begin{tikzpicture}
\begin{axis}
\addplot3[
    surf,
]
{exp(-x^2-y^2)*x};
\end{axis}
\end{tikzpicture}
%Here ends the 3D plot

\end{document}
```

On the 3rd line, we see that the file requires the `pgfplots` package, which is also not "natively" supported. Again, we assume that we have the `pgfplots` package source files. It's quite a large set of files that are divided between two locations if you find them in the installation directory of any LaTeX typesetting application. You can find `pgfplots` folder at both `\tex\generic` and `\tex\latex` folders. And the contents of both these folders must be provided as required input to the Aspose.TeX library. We want these source file to be packaged in a ZIP archive, so here is the archive's layout:

![](pgfplots-zip-layout.png)

And here is how we specify the access to these source files:

```Java
final Stream zipStream = File.Open("path-to-zip-with-pgfplots-sources"), FileMode.Open))
try {
    ...
    options.setRequiredInputDirectory(new InputZipDirectory(zipStream));
    ...
} finally {
    if (zipStream != null)
        zipStream.close();
}

```

After running a TeX job with this option, we get the output document:

![](Conversion-RequiredInputZip.png)

Here is the complete source code for the example:

{{< gist "aspose-com-gists" "67385c777283964d328086603f691ac9" "Aspose.TeX.Examples-Conversion-RequiredInput-Zip.java" >}}

> **_NOTE:_** The result was verified using the `pgfplots` package version 1.18.1. While the version of the `pfg` package included in the **Aspose.TeX** library is 3.1.9a.

### **Restrictions**

A package required by your LaTeX file may be developed under the `LaTeX3e` kernel. Such a package will most likely not work with the **Aspose.TeX** library since the latter is based on the `LaTeX2e` kernel.

Also, a package required by your LaTeX file may directly call device-dependent primitive commands that are not supported by the **Aspose.TeX** library's `Object TeX` engine. Such a package, unfortunately, will not work for sure.
