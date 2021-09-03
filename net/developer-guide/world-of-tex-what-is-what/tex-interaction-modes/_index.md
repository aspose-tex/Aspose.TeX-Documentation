---
title: 1.6. TeX interaction modes
type: docs
weight: 10
url: /net/tex-interaction-modes/
---

A TeX job may be running in one of four interaction modes at any given time. These modes are switched by the following TeX primitives:
 * `\batchmode`. The engine omits all stops and omits terminal output, and thus doesn't require the terminal for either input or output.
 * `\nonstopmode`. The engine omits all stops and thus requires the terminal only for output.
 * `\scrollmode`. The engine omits error stops and requires the terminal for both input and output.
 * `\errorstopmode`. The engine stops at every opportunity to interact.

Aspose.TeX allows you to specify the interaction mode as a TeX job option when its object is being created. This mode will be set in the internal state of the engine immediately after loading TeX format (if any format is supposed to be loaded at all), and will be switched to another mode as soon as the engine encounters one of the four commands. The default value of this option will preserve the interaction mode defined by the TeX format. When no format is loaded, the interaction mode is the same as set by the `\errorstopmode` command.