---
title: LaTeX math formulas rendering | C++
linktitle: LaTeX math formulas rendering
type: docs
weight: 10
url: /cpp/latex-math-formula-rendering/
description: Aspose.TeX API solution for C++ LaTeX math formulas rendering is described in this article. Here you will find code examples of the functionality.
lastmod: "2021-10-14"
sitemap:
    changefreq: "weekly"
    priority: 0.8
---

The API reference section related to this topic is [here](https://reference.aspose.com/tex/cpp/namespace/aspose.te_x.features). In fact, the easiest way to demonstrate the LaTeX math formula rendering feature is to start with the example. Here it is:

```C++
    // Create rendering options 
    System::SharedPtr<PngMathRendererOptions> options = System::MakeObject<PngMathRendererOptions>();
    // Sspecify the image resolution 150 dpi
    options->set_Resolution(150);
    // Specify the preamble.
    options->set_Preamble(u"\\usepackage{amsmath}\r\n\\usepackage{amsfonts}\r\n\\usepackage{amssymb}\r\n\\usepackage{color}");
    // Specify the scaling factor 300%.
    options->set_Scale(3000);
    // Specify the foreground color.
    options->set_TextColor(System::Drawing::Color::get_Black());
    // Specify the background color.
    options->set_BackgroundColor(System::Drawing::Color::get_White());
    // Specify the output stream for the log file.
    options->set_LogStream(System::MakeObject<System::IO::MemoryStream>());
    // Specify whether to show the terminal output on the console or not.
    options->set_ShowTerminal(true);
    
    // The variable in which the dimensions of the resulting image will be written.
    System::Drawing::SizeF size;
    // Create the output stream for the formula image.
    {
        System::SharedPtr<System::IO::Stream> stream = System::IO::File::Open(System::IO::Path::Combine(RunExamples::OutputDirectory, u"math-formula.png"), System::IO::FileMode::Create);
        // Clearing resources under 'using' statement
        System::Details::DisposeGuard<1> __dispose_guard_0({ stream});
        // ------------------------------------------
        try
        {
            System::MakeObject<Features::PngMathRenderer>()->Render(u"\\begin{equation*}\r\ne^x = x^{\\color{red}0} + x^{\\color{red}1} + \\frac{x^{\\color{red}2}}{2} + \\frac{x^{\\color{red}3}}{6} + \\cdots = \\sum_{n\\geq 0} \\frac{x^{\\color{red}n}}{n!}\r\n\\end{equation*}", stream, options, size);
        }
        catch(...)
        {
            __dispose_guard_0.SetCurrentException(std::current_exception());
        }
    }
    
    // Show other results.
    System::Console::get_Out()->WriteLine(options->get_ErrorReport());
    System::Console::get_Out()->WriteLine();
    System::Console::get_Out()->WriteLine(System::String(u"Size: ") + size);

```

Let's get to the details. First of all, we create a [rendering options](https://reference.aspose.com/tex/cpp/class/aspose.te_x.features.math_renderer_options) instance, similar to the TeX/LaTeX typesetting. We do it here simultaneously specifying the output image resolution.

Next, we specify the preamble. The default preamble is:
```tex
\usepackage{amsmath}
\usepackage{amsfonts}
\usepackage{amssymb}
```
which provides slightly more advanced math formula support than basic LaTeX. You can, for example, add the `color` package if you want to use your own highlighting in the formula, as we showed in the code example.

Then we instruct the renderer to scale the output by 300%.

Next two options define the foreground and background colors. Those parts of the formula that are not covered ("colored") by the custom highlighting will be displayed in the `TextColor` color.

The next line of the example doesn't make much sense. It just demonstrates that you can direct the log output to some stream.

And the last option `ShowTerminal` allows you to toggle writing the terminal output to the console.

The method that actually performs the rendering is [MathRenderer.Render()](https://reference.aspose.com/tex/cpp/class/aspose.te_x.features.math_renderer#aed31aae98b36b5367b680389b9c36acc). It returns the size of the formula in points as an output argument. To use this size later we declare the variable in the next line.

The stream where the image is to be written is taken by the method as the second argument. We create the stream next.

And finally, we call the `MathRenderer.Render()` method itself, passing options as the third argument. The LaTeX code of the formula is passed as a string through the first argument.

The last lines of the example print two artifacts of math formula rendering - the size of the formula and the brief error report (in case there were errors).

This is the most general use case for LaTeX math formula rendering.

**You may also check out the free [web app](https://products.aspose.app/tex/mathrenderer) built based on the feature implemented within [Aspose.TeX for C++ API](https://products.aspose.com/tex/cpp/).**