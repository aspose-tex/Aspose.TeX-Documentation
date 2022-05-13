---
title: Aspose.TeX and Object TeX
type: docs
weight: 11
url: /net/aspose-tex-and-object-tex/
description: TeX is an input and output format of this API solution so here we go with explaining the Object TeX and how it is transformed into a target format.
---
## **Object TeX**
Now let's consider the output format.

The original TeX was capable of outputting files in *DVI* (DeVice Independent) format only. It happened that the DVI format doesn't define metrics of a media on which a file is going to be printed --- the page size and the position of the upper-left corner of the entire page content. Once we decide to make the TeX engine capable of outputting files, say, in PDF format, we need to define such metrics. Thus, we need to include new primitives into original TeX engine's set. And this would be an extension of the engine itself.

That's what *Object* TeX is. Again, **on the one hand, it's a programming language with VirTeX's set of primitives, expanded with new primitives imposed by new output requirements. On the other hand, it's an extended TeX engine that understands new primitives as well. And, on the third hand, Object TeX is a new typesetting system in whole.**

There's the fourth hand. The Object TeX format is also a format based on Plain TeX that contains definitions that involve new primitives, e.g., assign default values to media metrics.

## **Aspose.TeX**
And Aspose.TeX is just an API to the Object TeX system.

## **Why the new TeX is Object?**
So why did we use "Object" in the name of the system? The reason is that the actual output of the Object TeX engine is not a file in the output format, but some intermediate *object* model, which is then transformed into a target format.