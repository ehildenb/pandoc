Partial Support
===============

Goal:
:   Add writer `--to code` which will write non-code blocks as Markdown with
    comments specified by option `--comment-prefix[=CSTRING]`. For now do not
    filter based on codeblock type at all.

Current:
:   Can specify `-to code{.CODE}`, where `CODE` can be one of
    `["hs", "maude", "k", "c", "c++", "sh", "py"]`, and it will write codeblocks
    labeled with the given `CODE` using the appropriate comment-prefix for the
    remainder of the document. The comments are rendered with the `markdown`
    writer with line-wraps preserved.

Unsupported
===========

Goal:
:   Better syntax than `--to code{.CODE}` for specifying the correct code
    writer.

Goal:
:   Support custom comment prefixes when writing code-files so that users have a
    fallback when their language is not supported by `pandoc`.

    Add option `--comment-prefix[=CSTRING]` which allows specifying how comments
    should be rendered. The comments will be rendered with the `markdown` writer
    for now (before being prefixed with `CSTRING`).

Goal:
:   Specify a different writer than `markdown` for writing comment blocks in.

    Add option `--comment-writer` which takes the internal writer to use for
    codeblocks. Defaults to `markdown` writer if not supplied (so that it
    specializes to case above). Perhaps only support a subset of the available
    pandoc writers (eg. the non-binary format ones).

Out of Scope
============

Goal:
:   Add codeblock selection ability with option
    `--code-selector[=CODE-SELECTOR]` (this is option that the `--to code`
    writer uses). `CODE-SELECTOR` is any CSS class-based selector which can be
    applied over the document.

    Generalize `--code-selector` to `--css-selector`, which works on *any* CSS
    class-labaled elements in the AST. Perhaps this is implemented as a filter.
