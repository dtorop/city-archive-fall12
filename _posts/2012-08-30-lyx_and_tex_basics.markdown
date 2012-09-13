---
layout: class
title: LyX and TeX basics
---

## Tools

For Macintosh OS X:

* Download and install TeX. You can get the whole kit and kaboodle for OS X [here](http://www.tug.org/mactex/). If that is too much, [BasicTeX](http://www.tug.org/mactex/morepackages.html) may suffice.

* Download and install [LyX](http://www.lyx.org/Download#toc4)

## Creating documents

LyX is [WYSIWYM](https://en.wikipedia.org/wiki/WYSIWYM). This is a refreshing change.

When in doubt, go to the `Help` menu. `Information`, `Tutorial`, and `User's Guide` should be especially helpful.

You can create a new document via `File > New`. Type as needed, and take advantage of the toolbar buttons and tools in the `Insert` menu. On the left of the top toolbar, changing the paragraph style from `Standard` can do interesting things. `Document > Settings...` gives some overall control.

To preview the document, click the "eyeballs" icon on the left side of the second row of tools, or choose `View > View [PDF (pdflatex)]`. You can update this preview as needed via the refresh icon (just to the right of the "eyeballs").

You can save the document in LyX format via `File > Save`. Equally important, you can save it as a PDF, via `File > Export > PDF (pdflatex)`. Once you have a PDF, it's easy to print your document.

If, in `Document > Settings...`, you choose, under `Fonts` to `Use non-TeX fonts`, you get all the fonts that are on your computer, rather than the built-in TeX fonts. Once you use non-TeX fonts, to save the file as a PDF choose `File > Export > PDF (XeTeX)`.

Look at the underlying TeX markup via `View > View Source`. Watch the markup get created as you type and format.

If there are problems, try `View > View Messages`, and show me what's written there. This is especially helpful if there are errors creating a PDF. If you go to the `Settings` tab of mesages, choose `Selected` `Debug Messages`, then say `Yes` to `LaTeX generation/execution`, more helpful messages may appear.
