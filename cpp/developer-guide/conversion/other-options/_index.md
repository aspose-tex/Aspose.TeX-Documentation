---
title: Other managing TeX options | C++
linktitle: Other options
type: docs
weight: 17
url: /cpp/other-options/
description: Conversion functionality of Aspose.TeX API solution for C++ lets set the initial interaction mode in which the engine starts. Here are some code examples.
---

## **How to set the interaction mode**

As we mentioned [here](/tex/net/tex-io/#tex-interaction-modes), **Aspose.TeX for C++** lets us set the initial interaction mode in which the engine starts. Here's how we do it:

```C++
// Create conversion options instance.
...
// Set the interaction mode.
options->set_Interaction(Interaction::NonstopMode);
```

## **How to set the job name**

When we pass the main input file as a file name, we get output files with the same name, although with another extensions. The TeX engine calls the input file's name the *job name* and uses it for output files, except in cases when auxilliary files with explicitly specified other names are written. When we pass the main input file as a [stream](/tex/cpp/other-ways-of-main-input/#providing-the-main-input-file-as-a-stream), the TeX engine uses the default job name, which is *texput*.
In both cases, we can override the job name by assigning the appropriate conversion option.

```C++
// Create conversion options instance.
...
// Set the job name.
options->set_JobName(u"my-job-name");
```
## **How to repeat the job**

As we have mentioned [above](/tex/net/latex-io/#latex-input) regarding labels and references, there are cases when we would like to run the same job twice. Here is how it can be done:

```C++
// Create conversion options instance.
...
// Set the job name.
options->set_Repeat(true);
```