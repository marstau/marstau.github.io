---
layout: post
title: Override controls override and final
category: 游戏技术
tags: Ｃ／Ｃ＋＋
keywords: 
description: 
---

Override controls: override {#override}
---------------------------

No special keyword or annotation is needed for a function in a derived
class to override a function in a base class. For example:

        struct B {
            virtual void f();
            virtual void g() const;
            virtual void h(char);
            void k();   // not virtual
        };

        struct D : B {
            void f();   // overrides B::f()
            void g();   // doesn't override B::g() (wrong type)
            virtual void h(char);   // overrides B::h()
            void k();   // doesn't override B::k() (B::k() is not virtual)
        };

This can cause confusion (what did the programmer mean?), and problems
if a compiler doesn't warn against suspicious code. For example,

-   Did the programmer mean to override **B::g()**? (almost certainly
    yes).
-   Did the programming mean to override **B::h(char)**? (probably not
    because of the redundant explicit **virtual**).
-   Did the programmer mean to override **B::k()**? (probably, but
    that's not possible).

To allow the programmer to be more explicit about overriding, we now
have the "contextual keyword" **override**:

        struct D : B {
            void f() override;  // OK: overrides B::f()
            void g() override;  // error: wrong type
            virtual void h(char);   // overrides B::h(); likely warning
            void k() override;  // error: B::k() is not virtual
        };

A declaration marked **override** is only valid if there is a function
to override. The problem with **h()** is not guaranteed to be caught
(because it is not an error according to the language definition) but it
is easily diagnosed.

**override** is only a *contextual* keyword, so you can still use it as
an identifier:

    int override = 7;   // not recommended

See also:

-   Standard: 10 Derived classes [class.derived] [9]
-   Standard: 10.3 Virtual functions [class.virtual]
-   [N3234==11-0004] Ville Voutilainen: [Remove explicit from
    class-head](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/).
-   [N3151==10-0141] Ville Voutilainen: [Keywords for override
    control](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3151.html).
    Earlier, more elaborate design.
-   [N3163==10-0153] Herb Sutter: [Override Control Using Contextual
    Keywords](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3163.pdf).
    Alternative earlier more elaborate design.
-   [N2852==09-0042] V. Voutilainen, A. Meredith, J. Maurer, and C.
    Uzdavinis: [Explicit Virtual
    Overrides](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2852.html).
    Earlier design based on [attributes](#attributes).
-   [N1827==05-0087] C. Uzdavinis and A. Meredith: [An Explicit Override
    Syntax for
    C++](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1827.htm).
    The original proposal.

------------------------------------------------------------------------

Override controls: final {#final}
------------------------

Sometimes, a programmer wants to prevent a virtual function from being
overridden. This can be achieved by adding the specifier **final**. For
example:

        struct B {
            virtual void f() const final;   // do not override
            virtual void g();
        };

        struct D : B {
            void f() const;     // error: D::f attempts to override final B::f
            void g();       // OK
        };

There are legitimate reasons for wanting to prevent overriding, but I'm
afraid that most examples I have been shown to demonstrate the need for
**final** have been based on mistaken assumptions on how expensive
**virtual** functions are (usually based on experience with other
languages). So, if you feel the urge to add a **final** specifier,
please double check that the reason is logical: Would semantic errors be
likely if someone defined a class that overwrote that virtual function?
Adding **final** closes the possibility of a future user of the class
might provide a better implementation of the function for some class you
haven't thought of. If you don't want to keep that option open, why did
you define the function to be **virtual** in the first place? Most
reasonable answers to that question that I have encountered have been
along the lines: This is a fundamental function in a framework that the
framework builders needed to override but isn't safe for general users
to override. My bias is to be suspicious towards such claims.

If it is performance (inlining) you want or you simply never want to
override, it is typically better not to define a function to be
**virtual** in the first place. This is not Java.

**final** is only a *contextual* keyword, so you can still use it as an
identifier:

    int final = 7;  // not recommended

See also:

-   Standard: 10 Derived classes [class.derived] [9]
-   Standard: 10.3 Virtual functions [class.virtual]







