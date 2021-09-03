---
title: 1.4. What TeX input is
type: docs
weight: 10
url: /net/what-is-tex-input/
---

A TeX job runs on an explicitly specified file. So, we include this file in the input of a certain TeX job. In addition, TeX has four primitives related to auxiliary input:
 * `\input<file name>` requires a file name and starts processing that file as soon as processing of the containing file reaches the `\input` command. Once the end of the auxiliary file is reached, processing returns to the file containing the '\input' command.
 * `\openin<4-bit-number>=<file name>` also requires a file name, but it just opens a file and associates it with a number from 0 to 15.
 * `\read<number> to <control sequence>` requires the number that a file is associated with, and reads a line from it at a time so that `<control sequence>` corresponds to the list of tokens read.
 * `\closein<4-bit-number>` closes the file associated with the number.

The files whose names are passed to `\input` and `\openin` commands are also included in the TeX input, and we will call them *auxiliary input* files or *dependencies*, while the file specified for the job we will call the *main input* file.

The four commands may occur either in the main input file or in an auxiliary input file. But beware of circular dependencies.

When running in an [interactive mode](/tex/net/tex-interaction-modes/), in case of any error, the TeX engine requests a correction on the terminal. At this point, you may want to replace the erroneous command with a new one. And this will be another and the last way to provide input to TeX that we will call the *terminal input*.