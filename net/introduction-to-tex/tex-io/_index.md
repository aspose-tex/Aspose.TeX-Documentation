---
title: TeX I/O
type: docs
weight: 12
url: /net/tex-io/
---

## **TeX file**

Technically, any file can be a TeX file. It doesn't even need to have the *.tex* extension. A TeX engine reads the input byte by byte trying to recognize commands known to it (i.e., those that are in its internal state). It simply reports errors about unrecognized commands and/or requests corrections on the terminal (if it's running in an [interactive mode](/tex/net/tex-io/#tex-interaction-modes)). But if you expect to see something like a nicely typeset document, the input should follow TeX syntax and, ideally, contain only commands known to the engine.

## **TeX input**

A TeX job runs on an explicitly specified TeX file. So, we include this file in the input of a certain TeX job. In addition, TeX has four primitives related to auxiliary input:
 * `\input<file name>` requires a file name and starts processing that file as soon as processing of the containing file reaches the `\input` command. Once the end of the auxiliary file is reached, processing returns to the file containing the `\input` command.
 * `\openin<4-bit-number>=<file name>` also requires a file name, but it just opens a file and maps it to a number from 0 to 15.
 * `\read<number> to <control sequence>` requires the number that a file is mapped to, and reads a line from it at a time so that `<control sequence>` corresponds to the list of tokens read.
 * `\closein<4-bit-number>` closes the file mapped to the number.

The files whose names are passed to `\input` and `\openin` commands are also included in the TeX input, and we will call them *auxiliary input* files or *dependencies*, while the file specified for the job we will call the *main input* file.

The four commands may occur either in the main input file or in an auxiliary input file. But beware of circular dependencies.

When running in an [interactive mode](/tex/net/tex-io/#tex-interaction-modes), in case of any error, the TeX engine requests a correction on the terminal. At this point, you may want to replace the erroneous command with a new one. And this will be another and the last way to provide input to TeX that we will call the *terminal input*.

## **TeX output**

As we mentioned [above](/tex/net/tex-io/#tex-input), a TeX job runs on an explicitly specified file. The file may not contain any data to typeset. There may be only control sequences that produce no characters to type. But normally it WILL contain such data, so that we will get a file in the target format which should contain our typeset text (or whatever else allowed by the engine and format, if they are extended to fit extra features of a certain target format). The file will have the same name as the file specified as the input. We will call this file the *main output* file. As we mentioned [above](/tex/net/aspose-tex-and-object-tex/#object-tex), for the original TeX, this will be a file in DVI format. We will call the name of both input and output files without extension the *job name*.

In addition, TeX has three primitives related to auxiliary output:
 * `\openout<4-bit-number>=<file name>` requires a file name, opens a file and maps it to a number from 0 to 15.
 * `\write<number>{token list}` requires the number that a file is mapped to, and writes the `token list` to the file.
 * `\closeout<4-bit-number>` closes the file mapped to the number.
 
The files whose names are passed to the `\openout` commands are also included in the TeX output, and we will call them *auxiliary output* files.

As the TeX engine runs through the input, it may output some debug information to the *log*, or *trascript*, file. We will include this file in the TeX output.

Simultaneously with writing to the log file, the TeX engine may output less detailed information to the terminal. And this is the last way the TeX engine writes the output that we will call the *terminal output*.

## **TeX interaction modes**

A TeX job may be running in one of four interaction modes at any given time. These modes are switched by the following TeX primitives:
 * `\batchmode`. The engine omits all stops and omits terminal output, and thus doesn't require the terminal for either input or output.
 * `\nonstopmode`. The engine omits all stops and thus requires the terminal only for output.
 * `\scrollmode`. The engine omits error stops and requires the terminal for both input and output.
 * `\errorstopmode`. The engine stops at every opportunity to interact.

Aspose.TeX allows us to specify the interaction mode as a TeX job option when its object is being created. This mode will be set in the internal state of the engine immediately after loading TeX format (if any format is supposed to be loaded at all), and will be switched to another mode as soon as the engine encounters one of the four commands. The default value of this option will preserve the interaction mode defined by the TeX format. When no format is loaded, the interaction mode is the same as set by the `\errorstopmode` command.