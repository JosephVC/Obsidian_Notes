---
---
Wierd Ghostscript error

When trying to run OCR, I often get the following error:
**Ghostscript 9.51 contains serious regressions and is not supported. Please upgrade to a newer version, or downgrade to the previous version.**

I know I've seen this before . .  .

Chocolatey is using Ghostscript 9.26, so I went to install that **and it didn't work**

What **did** work was installing Ghostscript 9.52 on my main system **and then** installing ghostscript (the Python library of the main Ghostscript library) via Poetry.
