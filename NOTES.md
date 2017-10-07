PR 1: Code Writers (Agnostic about Code Type)
=============================================

-   Add option `--comment-prefix[=CSTRING]` which allows specifying how comments
    should be rendered. The comments will be rendered with the `markdown` writer
    for now (before being prefixed with `CSTRING`).

-   Add writer `--to code` which will write non-code blocks as Markdown with
    comments specified by option `--comment-prefix[=CSTRING]`. For now do not
    filter based on codeblock type at all.

PR 2: Code Writers (Internal CSS Selector for Code Type)
========================================================

-   Add option `--comment-writer` which takes the internal writer to use for
    codeblocks. Defaults to `markdown` writer if not supplied (so that it
    specializes to case above). Perhaps only support a subset of the available
    pandoc writers (eg. the non-binary format ones).

-   Add codeblock selection ability with option
    `--code-selector[=CODE-SELECTOR]` (this is option that the `--to code`
    writer uses). If `--code-selector` is not added to the command line,
    defaults internally to `*`, which specializes to the case above (all
    code-blocks taken). Initially only support `.CLASS-NAME` where `CLASS-NAME`
    is the class associated with the codeblocks. If supplied multiple times on
    command line, semantics is OR?

-   Add code-block specific writers which will expand out to use the above added
    `--code-class` and `--comment-prefix` options. For example, `--to code-bash`
    (syntax up for debate) would expand to
    `--to code --code-class=bash --comment-prefix='#   '`.

PR 3: CSS Selector based Tangler
================================

-   Add CSS Selector parser as dependency to `pandoc`.

-   Generalize `--code-selector` above to read any CSS-selector string for
    picking codeblocks. Specializes naturally to case above.

-   Add `--filter-selector[=FILTER-SELECTOR]` (name up for debate) option which
    allows selecting any block with `Attr` based on CSS selector
    `FILTER-SELECTOR`. Note that this is *not* a writer option, but a generic
    AST transformation.
