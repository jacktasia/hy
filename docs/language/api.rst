=================
Hy (the language)
=================


.. warning::
    This is incomplete; please consider contributing to the documentation
    effort.


Theory of Hy
============

Hy maintains, over everything else, 100% compatibility in both directions
with Python it's self. All Hy code follows a few simple rules. Memorize
this, it's going to come in handy.

These rules help make sure code is idiomatic and interface-able in both
languages.


  * Symbols in earmufs will be translated to the uppercased version of that
    string. For example, `*foo*` will become `FOO`.

  * UTF-8 entities will be encoded using
    `punycode <http://en.wikipedia.org/wiki/Punycode>`_ and prefixed with
    `__hy_`. For instance, `⚘` will become `__hy_w7h`, and `♥` will become
    `__hy_g6h`.

  * Symbols that contain dashes will have them replaced with underscores. For
    example, `render-template` will become `render_template`.


Builtins
========

Hy features a number special forms that are used to help generate
correct Python AST. The following are "special" forms, which may have
behavior that's slightly unexpected in some situations.

do / progn
----------

the `do` or `progn` forms can be used in full code branches. What that means
is basically `(do)` and `(progn)` can only be used where a Python expression
can be used. These forms don't actually allow you to break Pythonic internals
such as `lambda` or `list-comp`, where you can only have one expression.