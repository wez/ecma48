# ECMA-48 in searchable, copy-n-pastable form

* [Browse the book online here](https://wezfurlong.org/ecma48/)

[ECMA-48](http://www.ecma-international.org/publications/standards/Ecma-048.htm) is
the freely available standard that defines *ANSI Escape Sequences*.  The text
in ECMA-48 is identical to the corresponding ANSI standard but is made freely
available via the ECMA website whereas the ANSI standard requires fees to access.

ECMA-48 was last revised in 1979 and the currently available digital representation
of the standard is a scan of a hard copy document from that time, and that makes
it difficult to search and link into.

I (@wez) took it upon myself to OCR and transcribe this document into markdown
to open things up a bit.  I need this documentation as part of my effort in
building terminal emulation software.

## Regenerating the built book

This book uses [mdBook](https://github.com/rust-lang/mdBook) to transform markdown
into a readable form.  To regenerate it:

```
$ cargo install mdbook
$ mdbook build --open
```

Then add the modified files into a commit and submit a pull request!
