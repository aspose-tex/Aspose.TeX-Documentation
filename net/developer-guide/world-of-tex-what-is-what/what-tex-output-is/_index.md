---
title: 1.5. What TeX output is
type: docs
weight: 10
url: /net/what-is-tex-output/
---

As we mentioned [above](/tex/net/what-is-tex-input/), a TeX job runs on an explicitly specified file. The file may not contain any data to typeset. There may be only control sequences that produce no characters to type. But normally it WILL contain such data, so that we will get a file in the target format which should contain our typeset text (or whatever else allowed by the a engine and format, if they are extended to fit extra features of a certain target format). The file will have the same name as the file specified as the input. We will call this file the *main output* file. As we mentioned [above](/tex/net/what-are-aspose-tex-and-object-tex/#what-is-object-tex), for the original TeX, this will be a file in DVI format. We will call the name of both input and output files without extension the *job name*.

In addition, TeX has three primitives related to auxiliary output:
 * `\openout<4-bit-number>=<file name>` requires a file name, opens a file and associates it with a number from 0 to 15.
 * `\write<number>{token list}` requires the number that a file is associated with, and writes the `token list` to the file.
 * `\closeout<4-bit-number>` closes the file associated with the number.
 
The files whose names are passed to the `\openout` commands are also included in the TeX output, and we will call them *auxiliary output* files.

As the TeX engine runs through the input, it may output some debug information to the *log*, or *trascript*, file. We will include this file in the TeX output.

Simultaneously with writing to the log file, the TeX engine may output the same or slightly different information to the terminal. And this is the last way the TeX engine writes the output that we will call the *terminal output*.