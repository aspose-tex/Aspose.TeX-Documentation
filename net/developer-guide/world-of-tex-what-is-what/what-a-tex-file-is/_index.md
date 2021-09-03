---
title: 1.3. What a TeX file is
type: docs
weight: 10
url: /net/what-a-tex-file-is/
---

Technically, any file can be a TeX file. It doesn't even need to have the *.tex* extension. A TeX engine reads the input byte by byte trying to recognize commands known to it (i.e., those that are in its internal state). It simply reports errors about unrecognized commands and/or requests corrections on the terminal (if it's running in an [interactive mode](/tex/net/tex-interaction-modes/)). But if we expect to see something like a nicely typeset document, the input should follow TeX syntax and, ideally, contain only commands known to the engine.