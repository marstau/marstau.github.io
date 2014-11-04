---
layout: post
title: Bézier curve
category: 游戏技术
tags: Game　Engine
keywords: 
description: 
---

 {style="background-image:none;border-bottom:#aaaaaa 1px solid;padding-bottom:0.17em;widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;margin:0px 0px 0.6em;font:19px/19.2px sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;overflow:hidden;word-spacing:0px;padding-top:0.5em;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}

<span id="Examination_of_cases" class="mw-headline">References:
<http://en.wikipedia.org/wiki/B%C3%A9zier_curve></span>

<span class="mw-headline">Examination of cases</span>

A Bézier curve is defined by a set of<span
class="Apple-converted-space"> </span>*control points*<span
class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>through<span
class="Apple-converted-space"> </span>**P**~*n*~, where<span
class="Apple-converted-space"> </span>*n*<span
class="Apple-converted-space"> </span>is called its order (*n*<span
class="Apple-converted-space"> </span>= 1 for linear, 2 for quadratic,
etc.). The first and last control points are always the end points of
the curve; however, the intermediate control points (if any) generally
do not lie on the curve.

### <span class="editsection" style="float:right;margin-left:5px;font-size:13px;font-weight:normal;-webkit-user-select:none;">[[edit](http://en.wikipedia.org/w/index.php?title=B%C3%A9zier_curve&action=edit&section=6 "Edit section: Linear Bézier curves")]</span><span id="Linear_B.C3.A9zier_curves" class="mw-headline">Linear Bézier curves</span> {style="background-image:none;border-bottom-style:none;padding-bottom:0.17em;widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;margin:0px 0px 0.3em;font:bold 17px/19.2px sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;overflow:hidden;word-spacing:0px;padding-top:0.5em;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}

Given points<span class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>and<span
class="Apple-converted-space"> </span>**P**~1~, a linear Bézier curve is
simply a<span class="Apple-converted-space"> </span>[straight
line](http://en.wikipedia.org/wiki/Straight_line "Straight line")<span
class="Apple-converted-space"> </span>between those two points. The
curve is given by

![\\mathbf{B}(t)=\\mathbf{P}\_0 +
t(\\mathbf{P}\_1-\\mathbf{P}\_0)=(1-t)\\mathbf{P}\_0 + t\\mathbf{P}\_1
\\mbox{ , } t \\in
[0,1]](http://upload.wikimedia.org/math/a/d/9/ad90a6fecd5324dc32f75f0b19c2d684.png)

and is equivalent to<span class="Apple-converted-space"> </span>[linear
interpolation](http://en.wikipedia.org/wiki/Linear_interpolation "Linear interpolation").

### <span class="editsection" style="float:right;margin-left:5px;font-size:13px;font-weight:normal;-webkit-user-select:none;">[[edit](http://en.wikipedia.org/w/index.php?title=B%C3%A9zier_curve&action=edit&section=7 "Edit section: Quadratic Bézier curves")]</span><span id="Quadratic_B.C3.A9zier_curves" class="mw-headline">Quadratic Bézier curves</span> {style="background-image:none;border-bottom-style:none;padding-bottom:0.17em;widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;margin:0px 0px 0.3em;font:bold 17px/19.2px sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;overflow:hidden;word-spacing:0px;padding-top:0.5em;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}

A quadratic Bézier curve is the path traced by the function<span
class="Apple-converted-space"> </span>**B**(*t*), given points<span
class="Apple-converted-space"> </span>**P**~0~,<span
class="Apple-converted-space"> </span>**P**~1~, and<span
class="Apple-converted-space"> </span>**P**~2~,

![\\mathbf{B}(t) = (1 - t)[(1 - t) \\mathbf P\_0 + t \\mathbf P\_1] + t
[(1 - t) \\mathbf P\_1 + t \\mathbf P\_2] \\mbox{ , } t \\in
[0,1]](http://upload.wikimedia.org/math/0/9/d/09d743f944f43b8c8a3c8468cabdb072.png),

which can be interpreted as the linear interpolant of corresponding
points on the linear Bézier curves from<span
class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>to<span
class="Apple-converted-space"> </span>**P**~1~<span
class="Apple-converted-space"> </span>and from<span
class="Apple-converted-space"> </span>**P**~1~<span
class="Apple-converted-space"> </span>to<span
class="Apple-converted-space"> </span>**P**~2~<span
class="Apple-converted-space"> </span>respectively. Rearranging the
preceding equation yields:

![\\mathbf{B}(t) = (1 - t)\^{2}\\mathbf{P}\_0 + 2(1 -
t)t\\mathbf{P}\_1 + t\^{2}\\mathbf{P}\_2 \\mbox{ , } t \\in
[0,1].](http://upload.wikimedia.org/math/2/d/5/2d5e5d58562d8ec2c35f16df98d2b974.png)

The derivative of the Bézier curve with respect to<span
class="Apple-converted-space"> </span>*t*<span
class="Apple-converted-space"> </span>is

![\\mathbf{B}'(t) = 2 (1 - t) (\\mathbf{P}\_1 - \\mathbf{P}\_0) + 2 t
(\\mathbf{P}\_2 - \\mathbf{P}\_1)
\\,.](http://upload.wikimedia.org/math/e/0/2/e0288487bb9614866c5e8f722949a3ba.png)

from which it can be concluded that the tangents to the curve at<span
class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>and<span
class="Apple-converted-space"> </span>**P**~2~<span
class="Apple-converted-space"> </span>intersect at<span
class="Apple-converted-space"> </span>**P**~1~. As<span
class="Apple-converted-space"> </span>*t*<span
class="Apple-converted-space"> </span>increases from 0 to 1, the curve
departs from<span class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>in the direction of<span
class="Apple-converted-space"> </span>**P**~1~, then bends to arrive
at<span class="Apple-converted-space"> </span>**P**~2~<span
class="Apple-converted-space"> </span>in the direction from<span
class="Apple-converted-space"> </span>**P**~1~.

A quadratic Bézier curve is also a<span
class="Apple-converted-space"> </span>[parabolic](http://en.wikipedia.org/wiki/Parabola "Parabola")<span
class="Apple-converted-space"> </span>segment. As a parabola is a<span
class="Apple-converted-space"> </span>[conic
section](http://en.wikipedia.org/wiki/Conic_section "Conic section"),
some sources refer to quadratic Béziers as "conic
arcs".^[<span>[</span>2<span>]</span>](http://en.wikipedia.org/wiki/B%C3%A9zier_curve#cite_note-freetype-4)^

### <span class="editsection" style="float:right;margin-left:5px;font-size:13px;font-weight:normal;-webkit-user-select:none;">[[edit](http://en.wikipedia.org/w/index.php?title=B%C3%A9zier_curve&action=edit&section=8 "Edit section: Cubic Bézier curves")]</span><span id="Cubic_B.C3.A9zier_curves" class="mw-headline">Cubic Bézier curves</span> {style="background-image:none;border-bottom-style:none;padding-bottom:0.17em;widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;margin:0px 0px 0.3em;font:bold 17px/19.2px sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;overflow:hidden;word-spacing:0px;padding-top:0.5em;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}

Four points<span class="Apple-converted-space"> </span>**P**~0~,<span
class="Apple-converted-space"> </span>**P**~1~,<span
class="Apple-converted-space"> </span>**P**~2~<span
class="Apple-converted-space"> </span>and<span
class="Apple-converted-space"> </span>**P**~3~<span
class="Apple-converted-space"> </span>in the plane or in
higher-dimensional space define a cubic Bézier curve. The curve starts
at<span class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>going toward<span
class="Apple-converted-space"> </span>**P**~1~<span
class="Apple-converted-space"> </span>and arrives at<span
class="Apple-converted-space"> </span>**P**~3~<span
class="Apple-converted-space"> </span>coming from the direction of<span
class="Apple-converted-space"> </span>**P**~2~. Usually, it will not
pass through<span class="Apple-converted-space"> </span>**P**~1~<span
class="Apple-converted-space"> </span>or<span
class="Apple-converted-space"> </span>**P**~2~; these points are only
there to provide directional information. The distance between<span
class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>and<span
class="Apple-converted-space"> </span>**P**~1~<span
class="Apple-converted-space"> </span>determines "how long" the curve
moves into direction<span
class="Apple-converted-space"> </span>**P**~2~<span
class="Apple-converted-space"> </span>before turning towards<span
class="Apple-converted-space"> </span>**P**~3~.

Writing<span
class="Apple-converted-space"> </span>**B**~**P**~i~,**P**~j~,**P**~k~~(*t*)
for the quadratic Bézier curve defined by points<span
class="Apple-converted-space"> </span>**P**~i~,<span
class="Apple-converted-space"> </span>**P**~j~, and<span
class="Apple-converted-space"> </span>**P**~k~, the cubic Bézier curve
can be defined as a linear combination of two quadratic Bézier curves:

![\\mathbf{B}(t)=(1-t)\\mathbf{B}\_{\\mathbf P\_0,\\mathbf P\_1,\\mathbf
P\_2}(t) + t \\mathbf{B}\_{\\mathbf P\_1,\\mathbf P\_2,\\mathbf P\_3}(t)
\\mbox{ , } t \\in
[0,1].](http://upload.wikimedia.org/math/f/d/b/fdbeda5f0c7bbea16e80663c606ba863.png)

The explicit form of the curve is:

![\\mathbf{B}(t)=(1-t)\^3\\mathbf{P}\_0+3(1-t)\^2t\\mathbf{P}\_1+3(1-t)t\^2\\mathbf{P}\_2+t\^3\\mathbf{P}\_3
\\mbox{ , } t \\in
[0,1].](http://upload.wikimedia.org/math/5/7/6/5763bbda8a3420e33422c2dae2a5c13a.png)

For some choices of<span
class="Apple-converted-space"> </span>**P**~1~<span
class="Apple-converted-space"> </span>and<span
class="Apple-converted-space"> </span>**P**~2~<span
class="Apple-converted-space"> </span>the curve may intersect itself, or
contain a cusp.

### <span id="Terminology" class="mw-headline">Terminology</span> {style="background-image:none;border-bottom-style:none;padding-bottom:0.17em;widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;margin:0px 0px 0.3em;font:bold 17px/19.2px sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;overflow:hidden;word-spacing:0px;padding-top:0.5em;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}

Some terminology is associated with these parametric curves. We have

![\\mathbf{B}(t) = \\sum\_{i=0}\^n
\\mathbf{b}\_{i,n}(t)\\mathbf{P}\_i,\\quad
t\\in[0,1]](http://upload.wikimedia.org/math/f/0/3/f03e0da823da62ab676bd8291d280b7a.png)

where the polynomials

![\\mathbf{b}\_{i,n}(t) = {n\\choose i} t\^i (1-t)\^{n-i},\\quad
i=0,\\ldots
n](http://upload.wikimedia.org/math/5/f/3/5f3babb0b5f89c79094f8929b6db7868.png)

are known as<span class="Apple-converted-space"> </span>[Bernstein basis
polynomials](http://en.wikipedia.org/wiki/Bernstein_polynomial "Bernstein polynomial")<span
class="Apple-converted-space"> </span>of degree<span
class="Apple-converted-space"> </span>*n*.

Note that<span class="Apple-converted-space"> </span>*t*^0^ = 1,
(1 − *t*)^0^ = 1, and that the<span
class="Apple-converted-space"> </span>[binomial
coefficient](http://en.wikipedia.org/wiki/Binomial_coefficient "Binomial coefficient"),<span
class="Apple-converted-space"> </span>![\\scriptstyle {n \\choose
i}](http://upload.wikimedia.org/math/3/1/9/3197349f5acc1a0108fba95667bcecfd.png),
also expressed as<span
class="Apple-converted-space"> </span>![\^n{\\mathbf{C}}\_i
](http://upload.wikimedia.org/math/7/8/9/78963a9902a193f7f9553cee91b26e33.png)<span
class="Apple-converted-space"> </span>or<span
class="Apple-converted-space"> </span>![{\\mathbf{C}\_i}\^n
](http://upload.wikimedia.org/math/8/8/9/8893a70f26799a17e3cdb51f8d5fcf6a.png)<span
class="Apple-converted-space"> </span>is:

![{n \\choose i} =
\\frac{n!}{i!(n-i)!}.](http://upload.wikimedia.org/math/7/2/e/72e561208899d4bab8d96e328413d130.png)

The points<span class="Apple-converted-space"> </span>**P**~*i*~<span
class="Apple-converted-space"> </span>are called<span
class="Apple-converted-space"> </span>*control points*<span
class="Apple-converted-space"> </span>for the Bézier curve. The<span
class="Apple-converted-space"> </span>[polygon](http://en.wikipedia.org/wiki/Polygon "Polygon")<span
class="Apple-converted-space"> </span>formed by connecting the Bézier
points with<span
class="Apple-converted-space"> </span>[lines](http://en.wikipedia.org/wiki/Line_(mathematics) "Line (mathematics)"),
starting with<span class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>and finishing with<span
class="Apple-converted-space"> </span>**P**~*n*~, is called the<span
class="Apple-converted-space"> </span>*Bézier polygon*<span
class="Apple-converted-space"> </span>(or<span
class="Apple-converted-space"> </span>*control polygon*). The<span
class="Apple-converted-space"> </span>[convex
hull](http://en.wikipedia.org/wiki/Convex_hull "Convex hull")<span
class="Apple-converted-space"> </span>of the Bézier polygon contains the
Bézier curve.

 

### <span id="Linear_curves" class="mw-headline">Linear curves</span> {style="background-image:none;border-bottom-style:none;padding-bottom:0.17em;widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;margin:0px 0px 0.3em;font:bold 17px/19.2px sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;overflow:hidden;word-spacing:0px;padding-top:0.5em;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [![Animation of a linear Bézier curve, t in [0,1]](http://upload.wikimedia.org/wikipedia/commons/thumb/8/89/Bezier_1_big.gif/240px-Bezier_1_big.gif)](http://en.wikipedia.org/wiki/File:Bezier_1_big.gif "Animation of a linear Bézier curve, t in [0,1]")
  Animation of a linear Bézier curve,<span class="Apple-converted-space"> </span>*t*<span class="Apple-converted-space"> </span>in [0,1]
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The<span class="Apple-converted-space"> </span>*t*<span
class="Apple-converted-space"> </span>in the function for a linear
Bézier curve can be thought of as describing how far<span
class="Apple-converted-space"> </span>**B**(*t*) is from<span
class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>to**P**~1~. For example when<span
class="Apple-converted-space"> </span>*t=0.25*,<span
class="Apple-converted-space"> </span>**B**(*t*) is one quarter of the
way from point<span class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>to<span
class="Apple-converted-space"> </span>**P**~1~. As<span
class="Apple-converted-space"> </span>*t*<span
class="Apple-converted-space"> </span>varies from 0 to 1,**B**(*t*)
describes a straight line from<span
class="Apple-converted-space"> </span>**P**~0~<span
class="Apple-converted-space"> </span>to<span
class="Apple-converted-space"> </span>**P**~1~.

### <span class="editsection" style="float:right;margin-left:5px;font-size:13px;font-weight:normal;-webkit-user-select:none;">[[edit](http://en.wikipedia.org/w/index.php?title=B%C3%A9zier_curve&action=edit&section=16 "Edit section: Quadratic curves")]</span><span id="Quadratic_curves" class="mw-headline">Quadratic curves</span> {style="background-image:none;border-bottom-style:none;padding-bottom:0.17em;widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;margin:0px 0px 0.3em;font:bold 17px/19.2px sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;overflow:hidden;word-spacing:0px;padding-top:0.5em;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}

For quadratic Bézier curves one can construct intermediate points<span
class="Apple-converted-space"> </span>**Q**~0~<span
class="Apple-converted-space"> </span>and<span
class="Apple-converted-space"> </span>**Q**~1~<span
class="Apple-converted-space"> </span>such that as<span
class="Apple-converted-space"> </span>*t*<span
class="Apple-converted-space"> </span>varies from 0 to 1:

-   Point<span class="Apple-converted-space"> </span>**Q**~0~<span
    class="Apple-converted-space"> </span>varies from<span
    class="Apple-converted-space"> </span>**P**~0~<span
    class="Apple-converted-space"> </span>to<span
    class="Apple-converted-space"> </span>**P**~1~<span
    class="Apple-converted-space"> </span>and describes a linear Bézier
    curve.
-   Point<span class="Apple-converted-space"> </span>**Q**~1~<span
    class="Apple-converted-space"> </span>varies from<span
    class="Apple-converted-space"> </span>**P**~1~<span
    class="Apple-converted-space"> </span>to<span
    class="Apple-converted-space"> </span>**P**~2~<span
    class="Apple-converted-space"> </span>and describes a linear Bézier
    curve.
-   Point<span class="Apple-converted-space"> </span>**B**(*t*) varies
    from<span class="Apple-converted-space"> </span>**Q**~0~<span
    class="Apple-converted-space"> </span>to<span
    class="Apple-converted-space"> </span>**Q**~1~<span
    class="Apple-converted-space"> </span>and describes a quadratic
    Bézier curve.

  ------------------------ ------------------------ ------------------------
  [![Construction of a                              [![Animation of a
  quadratic Bézier                                  quadratic Bézier curve,
  curve](http://upload.wik                          t in
  imedia.org/wikipedia/com                          [0,1]](http://upload.wik
  mons/thumb/b/bf/Bezier_2                          imedia.org/wikipedia/com
  _big.png/240px-Bezier_2_                          mons/thumb/2/2d/Bezier_2
  big.png)](http://en.wiki                          _big.gif/240px-Bezier_2_
  pedia.org/wiki/File:Bezi                          big.gif)](http://en.wiki
  er_2_big.png "Constructi                          pedia.org/wiki/File:Bezi
  on of a quadratic Bézier                          er_2_big.gif "Animation 
   curve")                                          of a quadratic Bézier cu
                                                    rve, t in [0,1]")

  Construction of a                                 Animation of a quadratic
  quadratic Bézier curve                            Bézier curve,<span
                                                    class="Apple-converted-s
                                                    pace"> </span>*t*<span
                                                    class="Apple-converted-s
                                                    pace"> </span>in
                                                    [0,1]
  ------------------------ ------------------------ ------------------------

### <span class="editsection" style="float:right;margin-left:5px;font-size:13px;font-weight:normal;-webkit-user-select:none;">[[edit](http://en.wikipedia.org/w/index.php?title=B%C3%A9zier_curve&action=edit&section=17 "Edit section: Higher-order curves")]</span><span id="Higher-order_curves" class="mw-headline">Higher-order curves</span> {style="background-image:none;border-bottom-style:none;padding-bottom:0.17em;widows:2;text-transform:none;background-color:#ffffff;text-indent:0px;margin:0px 0px 0.3em;font:bold 17px/19.2px sans-serif;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;overflow:hidden;word-spacing:0px;padding-top:0.5em;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"}

For higher-order curves one needs correspondingly more intermediate
points. For cubic curves one can construct intermediate points<span
class="Apple-converted-space"> </span>**Q**~0~,<span
class="Apple-converted-space"> </span>**Q**~1~, and<span
class="Apple-converted-space"> </span>**Q**~2~that describe linear
Bézier curves, and points<span
class="Apple-converted-space"> </span>**R**~0~<span
class="Apple-converted-space"> </span>&<span
class="Apple-converted-space"> </span>**R**~1~<span
class="Apple-converted-space"> </span>that describe quadratic Bézier
curves:

  ------------------------ ------------------------ ------------------------
  [![Construction of a                              [![Animation of a cubic
  cubic Bézier                                      Bézier curve, t in
  curve](http://upload.wik                          [0,1]](http://upload.wik
  imedia.org/wikipedia/com                          imedia.org/wikipedia/com
  mons/thumb/c/c1/Bezier_3                          mons/thumb/f/ff/Bezier_3
  _big.png/240px-Bezier_3_                          _big.gif/240px-Bezier_3_
  big.png)](http://en.wiki                          big.gif)](http://en.wiki
  pedia.org/wiki/File:Bezi                          pedia.org/wiki/File:Bezi
  er_3_big.png "Constructi                          er_3_big.gif "Animation 
  on of a cubic Bézier cur                          of a cubic Bézier curve,
  ve")                                               t in [0,1]")

  Construction of a cubic                           Animation of a cubic
  Bézier curve                                      Bézier curve,<span
                                                    class="Apple-converted-s
                                                    pace"> </span>*t*<span
                                                    class="Apple-converted-s
                                                    pace"> </span>in
                                                    [0,1]
  ------------------------ ------------------------ ------------------------

For fourth-order curves one can construct intermediate points<span
class="Apple-converted-space"> </span>**Q**~0~,<span
class="Apple-converted-space"> </span>**Q**~1~,<span
class="Apple-converted-space"> </span>**Q**~2~<span
class="Apple-converted-space"> </span>&<span
class="Apple-converted-space"> </span>**Q**~3~<span
class="Apple-converted-space"> </span>that describe linear Bézier
curves, points<span class="Apple-converted-space"> </span>**R**~0~,<span
class="Apple-converted-space"> </span>**R**~1~<span
class="Apple-converted-space"> </span>&<span
class="Apple-converted-space"> </span>**R**~2~<span
class="Apple-converted-space"> </span>that describe quadratic Bézier
curves, and points<span
class="Apple-converted-space"> </span>**S**~0~<span
class="Apple-converted-space"> </span>&<span
class="Apple-converted-space"> </span>**S**~1~<span
class="Apple-converted-space"> </span>that describe cubic Bézier curves:

  ------------------------ ------------------------ ------------------------
  [![Construction of a                              [![Animation of a
  quartic Bézier                                    quartic Bézier curve, t
  curve](http://upload.wik                          in
  imedia.org/wikipedia/com                          [0,1]](http://upload.wik
  mons/thumb/3/33/Bezier_4                          imedia.org/wikipedia/com
  _big.png/240px-Bezier_4_                          mons/thumb/7/7d/Bezier_4
  big.png)](http://en.wiki                          _big.gif/240px-Bezier_4_
  pedia.org/wiki/File:Bezi                          big.gif)](http://en.wiki
  er_4_big.png "Constructi                          pedia.org/wiki/File:Bezi
  on of a quartic Bézier c                          er_4_big.gif "Animation 
  urve")                                            of a quartic Bézier curv
                                                    e, t in [0,1]")

  Construction of a                                 Animation of a quartic
  quartic Bézier curve                              Bézier curve,<span
                                                    class="Apple-converted-s
                                                    pace"> </span>*t*<span
                                                    class="Apple-converted-s
                                                    pace"> </span>in
                                                    [0,1]
  ------------------------ ------------------------ ------------------------

For fifth-order curves, one can construct similar intermediate points.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [![Animation of the construction of a fifth-order Bézier curve](http://upload.wikimedia.org/wikipedia/en/thumb/0/0b/BezierCurve.gif/240px-BezierCurve.gif)](http://en.wikipedia.org/wiki/File:BezierCurve.gif "Animation of the construction of a fifth-order Bézier curve")
  Animation of a fifth order Bézier curve,<span class="Apple-converted-space"> </span>*t*<span class="Apple-converted-space"> </span>in [0,1]
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

These representations rest on the process used in<span
class="Apple-converted-space"> </span>[De Casteljau's
algorithm](http://en.wikipedia.org/wiki/De_Casteljau%27s_algorithm "De Casteljau's algorithm")<span
class="Apple-converted-space"> </span>to calculate Bezier
curves.^[<span>[</span>3<span>]</span>](http://en.wikipedia.org/wiki/B%C3%A9zier_curve#cite_note-5)^

 

 






