---
layout: post
title: Rendering the Great Outdoors/Fast Occlusion Culling for Outdoor Environments
category: 游戏技术
tags: DirectX
keywords: 
description: 
---

**July 17, 2002**

From :
<http://www.gamasutra.com/view/feature/2979/rendering_the_great_outdoors_fast_.php>

Rendering engines used in today’s game titles utilize various techniques
for **hidden surface removal (HSR),** different techniques being
suitable for different game genres. For example, action games played in
closed-in locations such as rooms, caves, and tunnels need an engine
allowing fast rendering of a few hundred polygons, a high frame rate,
and a high level of details to impress players. Conversely, a game that
is taking place outdoors requires quite a different approach. Let’s
discuss appropriate approaches for the latter. Not too long ago, games
ran in software mode only, without the help of 3D accelerators. With the
CPU doing all the work, engines rendered as few pixels as possible,
typically with BSP-based scenes and BSP rendering.

**Moving Games Outdoors**

With the advent of 3D accelerators and the invention of the depth-buffer
(or Z-buffer), the strict sorting of polygons slowly faded out of
engines, and software engineers started trying out different techniques.
Game designers wanted to move their worlds outdoors, and new graphics
hardware made such designs possible. As graphics hardware power
increases, however, so do requirements for game content and high-quality
graphics, creating room to waste processing power with inefficient usage
of computing resources. Let’s discuss one technique for hidden surface
removal usable in 3D engines, developed while creating some of the games
I’ve worked on. The technique, utilizing object occlusion, is for
outdoor rendering. The fundamental entities working for us will be
so-called occluders, and we’ll come to them soon.

**The Scene Hierarchy Tree**

One of the first steps toward optimized rendering is keeping objects in
a scene organized. Most commercial modeling packages and 3D engines use
a scene hierarchy, and for good reason: used smartly, it allows for fast
rejection of entire hierar-chy branches based on bounding volume tests,
and may also accelerate collision testing. A scene hierarchy tree is a
collection of objects (visuals as well as nonvisuals) in an organized
fashion. In a tree structure, a scene has its root object, which may
have children objects linked to it, and these child objects may have
other objects linked to them. The objects may be visuals (characters,
terrain, items in the game), as well as nonvisual objects (such as
3D-positioned lights, sounds, dummies, and other helper objects).

**Balancing the Tree**

When creating the hierarchy tree in a commercial 3D graphics package or
in-game editor, keep the tree balanced. For example, by linking all your
objects to the root level, you lose the benefits of having a hierarchy,
because all your objects are in a single list and any processing will
just treat them as an array. Grouping objects logically is a big step
forward. Hierarchical object linking is usually based on some logical
assumptions. For preprocessing purposes, keep multiple adjacent objects
together, linked to one parent object. Object linking is also done for
other purposes, such as inheriting the parent’s position, rotation, and
scale. This is achieved by using matrices and matrix concatenation.

**Bounding Volumes**

A bounding volume is a simple geometrical object roughly representing
the volume of a real object’s geometry. It’s as small as possible while
still enclosing all vertices of the object. The most suitable geometric
objects for bounding volumes are spheres and boxes. For the techniques
presented in this article, I recommend using both types and defining a
structure representing the bounding volume:

 

> struct S\_bounding\_volume{<span
> class="Apple-converted-space"> </span>\
>  struct{<span class="Apple-converted-space"> </span>\
>  struct{<span class="Apple-converted-space"> </span>\
>  float x,y,z;<span class="Apple-converted-space"> </span>\
>  }min,max;<span class="Apple-converted-space"> </span>\
>  }box;\
>  struct{<span class="Apple-converted-space"> </span>\
>  struct{<span class="Apple-converted-space"> </span>\
>  float x,y,z;\
>  }pos;<span class="Apple-converted-space"> </span>\
>  float radius;\
>  }sphere;\
>  };

 

You’re probably already using an HSR technique utilizing bounding boxes
or spheres, so why use a combination of both? The answer is simple:
speed. While bounding spheres allow for very fast collision detection
using a simple distance test, the volume it encloses is often much
greater than the actual object it represents (Figure 2). Too often,
then, we consider an object to be on-screen when none of its vertices
actually would be.

<div>

![](http://www.gamasutra.com/redesign/images/corner_top_left.gif)

</div>

\
 ![](http://www.gamasutra.com/features/20020717/fig_02.gif)

![](http://www.gamasutra.com/redesign/images/corner_top_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_left.gif)

****Figure 2: Visual object with bounding box and sphere. Notice that
the sphere is a bit larger than the box.****

On the other hand, a bounding box is a closer match to the shape of an
object, but tests with boxes are slower. Usually we do a two-pass
collision/intersection test, using a bounding sphere in a first pass and
oriented bounding box (OBB) in the second pass. Because the first test
rejects most invisible or non-clipped objects, the chances that a second
test will never be executed are high. At the same time, performing the
bounding box test yields more accurate results, leading to fewer objects
being rendered.

This mixed bounding volume is also suitable for other pur-poses, such as
collision detection or physics.

**Node Volumes**

Every visual object in a scene hierarchy should have an associated
bounding volume, so that with just a few math operations, we’re able to
say if each object is visible or not. As I mentioned previously, it
wouldn’t be very efficient to test all the scene objects in each
rendered frame. For example, in a racing game with 20 cars, you’d end up
testing all the vehicle’s objects (wheels, doors, driver, driver’s
fingers, and on and on) 20 times, which could easily make for upwards of
25 objects on each car multiplied by 20 cars. Why perform 25 tests when
a single test for each car can accomplish the same result?

<div class="adBox"
style="position:relative;text-align:left;padding-bottom:10px;widows:2;text-transform:none;background-color:#fafafa;text-indent:0px;padding-left:10px;font:12px/15.6px Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:right;letter-spacing:normal;color:#000000;clear:right;word-spacing:0px;padding-top:20px;left:10px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

<div id="adheader">

\
\
  

</div>

<div id="imu_ad">

</div>

</div>

With complex models or models used in a scene multiple times, finding a
way to skip the processing of an entire model or models if they’re out
of view would be highly desirable. For this reason, we’ll introduce a
node bounding volume. This is the same bounding structure defined above,
but it doesn’t enclose vertices; rather it encloses all bounding volumes
of a group of objects, the child objects of the node (objects, models,
and so on).

**Building and Maintaining Volumes**

Assuming you have static geometry, calculating a visual object’s extent
is done once before starting rendering. The bounding box is axis-aligned
(AABB) in the local coordinates of an object, defined by two extreme
points of the box. Anytime a bounding box is used in computations, it
must be transformed into world coordinates using the object’s
transformation matrix, and thus changed to an oriented bounding box.
Because OBBs cannot be specified by just two corner points, we’ll need
to extract the two corner points of the AABB into the eight corner
points of the OBB, and transform all these points to world coordinates
with the object’s transformation matrix (the same one that will be used
to transform the object’s vertices to world coordinates). The bounding
sphere is also in local coordinates, and must be transformed (position)
and scaled (radius) to world coordinates before being used in
computations.

The situation with node bounding volumes is a bit more difficult.
Because the position of objects may change in real time, this bounding
volume must be computed at run time whenever any object in the group
moves. The best method is a lazy evaluation programming technique — in
other words, computing the value when it’s needed. You may implement a
system of invalidation of a node’s bounding volume when the child’s
matrix changes due to position, rotation, or scale. This system is
harder to implement and debug, but it’s critical for fast 3D culling,
both rendering and collision testing.

By measurements I’ve made in our 3D system, the dynamic bounding volume
update takes no more than 1 to 2 percent of total CPU time when the game
is running.

**Convex Hull Computation**

Because it’s very easy to detect collision against it, a convex hull is
another basic geometry object used in occlusion testing. During
occlusion testing, we’ll detect a collision of a 3D point with a hull
and a sphere with a hull. Since we must detect how the bounding volume
of an object collides with viewing volumes (screen frustum and occlusion
frustum), hidden-surface removal has much in common with collision
detection.

A hull is defined as a set of planes that forms the hull, with their
normals pointing away from the hull. Any point in space is a part of the
hull if it lies behind all the planes forming the hull. For our
purposes, we’ll also use an open hull, which is a hull that represents
an open 3D volume.

All the information we need to compute the convex hull is a set of 3D
points. During the computation, we’ll remove redundant points, which are
inside the hull and do not lie on the skeleton of the hull. We’ll also
need to compute the edge faces of the convex hull; these faces are not
necessarily triangles, as they are in 3D meshes.

We’ll utilize planes of these edge faces for our occlusion computations:
for example, a fast check of whether a 3D point is inside of a convex
hull. If a point in space is behind all the edge faces of the hull
(assuming the planes’ normals point out from the hull), then it is
inside of the hull (Listing 1).

 

> bool IsPointInHull(const S\_vector &v,const vector<span
> class="Apple-converted-space"> </span>\
>  &planes){<span class="Apple-converted-space"> </span>\
> \
>  for(int i =planes.size();i —;){\
>  float d =v.DistanceToPlane(planes [i]);\
>  if(d \>=0.0f)<span class="Apple-converted-space"> </span>\
>  return false;<span class="Apple-converted-space"> </span>\
>  } return true;\
>  }

 

 

> **Listing 1: Checks if a 3D point is inside a convex hull. A convex
> hull is defined as a set of planes with normals pointing away from the
> hull. This function uses the S\_vector class for a 3D point, the
> S\_plane class for a plane in 3D space, and a member function S\_vec-
> tor::DistanceToPlane(const S\_plane&) const that determines the
> distance from a 3D point to a plane.**

 

Several algorithms exist for computing a convex hull from a set of
points. Some commonly used ones include incremental, **gift-wrapping,
divide-and-conquer, and quick-hull.** There is a nice Java applet
demonstrating techniques of building convex hulls that is a good
starting point for choosing and implementing the algorithm. It is
available (with kind permission of its author)
at[www.cse.unsw.edu.au/\~lambert/java/3d/hull.html](http://www.cse.unsw.edu.au/~lambert/java/3d/hull.html).

<span style="background-color:#ffe500;">Speaking from my own experience,
writing code for building convex hulls is quite a difficult task. Even
when you implement the code properly, you’ll encounter problems with
float-rounding errors (using doubles won’t solve anything).</span><span
style="background-color:#ffe500;"> Regardless of which algorithm you
choose, with some point sets you’ll end up with hulls that are invalid
after final validity checks are per-formed. Having multiple points
placed close together on a plane is a common source of problems</span>.

After I struggled for months with code that computed it wrong, then
spending another month writing my own convex-hull computation code, I
finally switched to **Qhull**, a freeware package that utilizes the
quick-hull algorithm. It’s available at<span
class="Apple-converted-space"> </span>[www.geom.umn.edu/software/qhull](http://www.geom.umn.edu/software/qhull).

Although the QHull library is a robust, platform-independent package
that can do many additional tasks, we will only be needing it to compute
the convex hull using our structures. It handles rounding problems by
joggling points; if computation fails, it shifts points randomly by a
small value and recomputes until it gets a proper hull.

If you decide to use this or any other available package, be prepared to
spend a day or two reading its documentation and writing code to call
it; you’ll save a month otherwise spent writing and debugging your own
system.

The final result we need after computation is a set of filtered points
that form a skeleton of the hull, and a set of faces. Following is an
example of what we get (faces are kept as indices in the point set):

 

> struct S\_vector{<span class="Apple-converted-space"> </span>\
>  float x,y,z;\
>  }; struct S\_face{\
>  int num\_points;<span class="Apple-converted-space"> </span>\
>  unsigned short \*indices;\
>  };

 

Now we use the help of C++ STL vector class for storing our vertices and
faces:

 

> std::vectorhull\_points;<span class="Apple-converted-space"> </span>\
>  std::vectorhull\_faces;

 

Note that when inserting into vector , a copy constructor of the class
being inserted is called. Make sure you have implemented a copy
constructor of S\_face so that memory for indices is properly allocated
and freed.

 

**The View Frustum**

A viewing frustum is a 3D volume. For practical reasons, we can treat it
as a convex hull, simplifying further computa-tions. The viewing frustum
is typically a cut pyramid (if a projection transformation is used) or a
cube (if an orthogonal transformation is used). This article assumes
that projection transformation is used, and many times the camera’s
position will form one of the points of the frustum’s hull.

<div class="adBox"
style="position:relative;text-align:left;padding-bottom:10px;widows:2;text-transform:none;background-color:#fafafa;text-indent:0px;padding-left:10px;font:12px/15.6px Verdana, Arial, Helvetica, sans-serif;white-space:normal;orphans:2;float:right;letter-spacing:normal;color:#000000;clear:right;word-spacing:0px;padding-top:20px;left:10px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">

<div id="adheader">

\
\
  

</div>

<div id="imu_ad">

</div>

</div>

**Making Sense of Occluders**

Occluders in the real world may be thought of as objects which occlude
(or obstruct) your view of other objects behind them (Figure 3). Take an
example of an occluder — a building, a hill, or a car — all these things
occlude your view to objects physically located behind them. Transparent
or translucent objects are not good view occluders, because as light
rays pass through the material, so we’ll ignore transparent objects as
occluders in 3D rendering.

Objects in the real world consist of atoms and molecules, and pretty
much every atom can either be occluded by another atom or not (in which
case a viewer can see it). In computer graphics, however, objects are
built from vertices and polygons, and these vertices and polygons are
usually grouped into primitives, which are rendered together in order to
achieve good graphics throughput. Our task consists of rejecting as many
of these primitives as possible in the early (preprocessing) phase of
our pipeline, without affecting the viewer’s experience by rejecting
objects that should be rendered.

\

<div>

![](http://www.gamasutra.com/redesign/images/corner_top_left.gif)

</div>

\
 ![](http://www.gamasutra.com/features/20020717/fig_03.gif)

![](http://www.gamasutra.com/redesign/images/corner_top_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_left.gif)

****Figure 3: An example of occlusion in the real world. The house
occludes the view onto the tree; the shaded area represents the volume
that the viewer cannot see.****

\

In practice, this means finding which objects are fully occluded by
other objects and rejecting these occluded objects from any further
processing. A solid object, sufficiently big to be worth the additional
computations associated with occlusion testing, is an ideal occluder.

In an ideal 3D engine, we could detect occlusion of even the smallest
primitive behind any object in a scene. In reality, however, we must
find some algorithm that allows fast detection of occlusion for a
sufficient number of potentially visible primitives. For that reason,
we’ll simplify the occlusion volumes to convex hulls.

Convex hulls allow for sufficient approximation of a 3D object in most
cases. When it is not possible to represent the shape of an object with
a convex hull, you can use more hulls to accomplish the task. The
occlusion hull doesn’t need to copy the exact shape of visual object it
works with. In many cases, an occluder may consist of many fewer faces
than the visual primitive itself, roughly copying the shape of the
visual (Figures 4 and 5). The rule to keep in mind here is that an
occluder’s shape shouldn’t be bigger than the shape of visuals it
represents; otherwise your engine will end up rejecting primitives that
should be rendered, resulting in an ugly graphical artifact.

\

<div>

![](http://www.gamasutra.com/redesign/images/corner_top_left.gif)

</div>

\
 ![](http://files.note.sdo.com/XbPJ4~kd5GbywE01400hmc) 

\

![](http://www.gamasutra.com/redesign/images/corner_top_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_left.gif)

****Figure 4:<span class="Apple-converted-space"> </span>**A house,
suitable for occluding other objects in 3D scene.\
** **Figure 5: The occluder object (drawn in green wire-frame),
representing the simplified shape of the house.\
**

\

**** 

**The Occluder ’s Place in the Pipeline**

In determining HSR, <span style="background-color:#337fe5;">occluders
should be processed first</span>. Because the position of a camera
(viewer) changes constantly in 3D games, so does the occlusion frustum,
the 3D volume cast by the occluder. Our task is to compute the occlusion
volume at the beginning of rendering from a particular camera view. (If
you render multiple views in a single frame, a mirror for example, this
step must be done for each rendered view.) After this preprocessing
step, you should collect all occluders on the screen, against which
you’ll test other potentially visible primitives. Some optimization
tips: Minimize the number of occluders you include in the test list,
done by determining if a particular occluder is occluded by another
occluder. Figure 6 shows this possibility. Also, don’t consider
occluders that may potentially hide only a small amount of primitives.
You should reject occluders that occupy a small area of screen space.

\

<div>

![](http://www.gamasutra.com/redesign/images/corner_top_left.gif)

</div>

\
 ![](http://www.gamasutra.com/features/20020717/fig_06.gif)

![](http://www.gamasutra.com/redesign/images/corner_top_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_left.gif)

****Figure 6:<span class="Apple-converted-space"> </span>**Image showing
an occluder hidden by another occluder. Any\
 visual occluded by the occluder B is also occluded by occluder A, so
we\
 include only occluder A in our list of occluders we test against.**

\

Once we have a list of on-screen occluders, we can move on to the next
preprocessing step: <span style="background-color:#337fe5;">traversing
the scene hierarchy tree and using the list of occluders to check if a
particular object is visible.</span>

**Building Occlusion Volumes**

Let’s have a closer look at the information needed in order to detect
whether an object is occluded. Looking closer at the occlusion volume,
we see that occlusion volume is actually another kind of convex hull,
expanded from the viewpoint into infinity. The occlusion volume is built
from all of the occluder’s polygons facing the camera, and from contour
edges (as seen from the camera) expanded away from the camera (Figure
7).

\

<div>

![](http://www.gamasutra.com/redesign/images/corner_top_left.gif)

</div>

\
 ![](http://www.gamasutra.com/features/20020717/fig_07.gif)

![](http://www.gamasutra.com/redesign/images/corner_top_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_left.gif)

****Figure 7:<span class="Apple-converted-space"> </span>**An Oocclusion
frustum built from an occluder, using current\
 viewer position.**

\

Actually, this volume is open — there’s no back plane that would cap the
volume — because the occluder hides everything behind it into infinity.
And any plane we save will speed up further computations.

To build contours(外形) from a convex hull, we use a simple algorithm
utilizing the fact that each edge in a convex hull connects exactly two
faces.(每条边连接两个面) The algorithm is this:

1.  Iterate through all polygons, and detect whether a polygon faces the
    viewer. (To detect whether a polygon faces the viewer, use the dot
    product of the polygon’s normal and direction to any of the
    polygon’s vertices. When this is less than 0, the polygon faces the
    viewer.)
2.  If the polygon faces viewer, do the following for all its edges: If
    the edge is already in the edge list, remove the edge from the list.
    Otherwise, add the edge into the list.

After this, we should have collected all the edges forming the
occluder’s contour, as seen from the viewer’s position. Once you’ve got
it, it’s time to build the occlusion frustum itself, as shown in Figure
7 (note that this figure shows a 2D view of the situation). The frustum
is a set of planes defining a volume being occluded. The property of
this occlusion volume is that any point lying behind all planes of this
volume is inside of the volume, and thus is occluded. So in order to
define an occlusion volume, we just need a set of planes forming the
occlusion volume.

Looking closer, we can see that the frustum is made of all of the
occluder’s polygons facing the viewer, and from new planes made of edges
and the viewer’s position. So we will do the following:

1.  Add planes of all facing polygons of the occluder.
2.  Construct planes from two points of each edge and the viewer’s
    position.

If you’ve gotten this far and it’s all working for you, there’s one
useful optimization to implement at this point. It lies in minimizing
the number of facing planes (which will speed up intersection
detection). You may achieve this by collapsing all the facing planes
into a single plane, with a normal made of the weighted sum of all the
facing planes. Each participating normal is weighted by the area of its
polygon. Finally, the length of the computed normal is made unit-length.
The d part of this plane is computed using the farthest contour point.
Occlusion testing will work well without this optimization, but
implementing it will speed up further computations without loss of
accuracy.

 

**Detecting Occlusion**

To detect if an object is occluded, we will utilize the object’s
bounding volume. To find out if the object is inside of the occlusion
frustum, we’ll make a simple test to check if its bounding sphere is
inside of the frustum. Figure 8 shows possible situations that may
arise. Here we see that only sphere C passed the test and is fully
occluded. Listing 3 shows the function that may be used for such a
computation. This process detects whether a bounding sphere is occluded.
It’s fast, but not as accurate as detection using bounding boxes. With
this technique, some objects may be detected as visible after the
bounding sphere test succeeds, but their bounding box is still fully
occluded, so we would end up rendering them even though they’re fully
occluded. Figure 9 illustrates this possibility.

Detecting if the bounding box is inside the occlusion frus-tum is
another very simple task: detect if all eight corner points of the
bounding box are inside of the frustum (Listing 2). Note that we use
oriented bounding boxes in world coor-dinates, so we must transform
local AABBs to world OBBs (as explained previously). If any vertex is
outside of the volume, the box is not occluded. This test can take eight
times more dot products than the sphere test, so it is less efficient.
Ideally you would use it only when you detect that the center of the
bounding sphere is inside the occlusion frustum but the sphere is still
not occluded. This minimizes the chances of wasting time checking
box-versus-frustum collision, at the same time getting more accurate
occlusion tests, resulting in fewer objects being rendered.

\

<div>

![](http://www.gamasutra.com/redesign/images/corner_top_left.gif)

</div>

\
 ![](http://www.gamasutra.com/features/20020717/fig_08.gif)\
\

![](http://www.gamasutra.com/redesign/images/corner_top_right.gif)

<div>

![](http://www.gamasutra.com/features/20020717/fig_09.gif)

</div>

![](http://www.gamasutra.com/redesign/images/corner_bottom_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_left.gif)

**Figure 8: Sphere A is outside of at least one plane. Sphere B is
inside all planes, but its radius is greater than the distance from one
of the planes. Sphere C is behind all planes and a sufficient distance
from all planes.\
 Figure 9. A case when the bounding sphere is not fully occluded but\
 the bounding box is, thus the object should not be rendered.**

\

 

\

+--------------------------------------+--------------------------------------+
| bool AreAllVerticesInVF(const vector | bool IsSphereInFrustum(const         |
| &planes, const\                      | vector&planes,\                      |
|  S\_vector \*verts,int num\_verts){\ |  const S\_vector &sphere\_pos,float  |
| \                                    | sphere\_radius,bool &clip){\         |
|  for(int i =0;i<span                 | \                                    |
| class="Apple-converted-space"> </spa |  clip =false;\                       |
| n>\                                  |  for(int i =planes.size();i —;){\    |
|  for(int j =planes.size();j —;){\    |  float d =planes [i                  |
|  float d =planes [j ].d +planes [j   | ].normal.Dot(sphere\_pos)+planes [i  |
| ].normal.Dot(verts [i ]);\           | ].d;\                                |
|  if(d \>=0.0f)\                      |  if(d \>=sphere\_radius)\            |
|  return false;\                      |  return false;\                      |
|  }\                                  |  if(d \>=-sphere\_radius)\           |
|  }\                                  |  clip =true;\                        |
|  return true;\                       |  }\                                  |
|  }                                   |  return true;\                       |
|                                      |  }                                   |
+--------------------------------------+--------------------------------------+
| **Listing 2: Detects if a set of all | **Listing 3: Detects if a sphere is  |
| points is inside of the viewing      | inside the frustum (convex hull).    |
| frustum. This is just a variation of | Notice that this function also       |
| Listing 1, checking multiple points  | computes clipping flag, which is set |
| instead of one.**                    | whenever a sphere collides with one  |
|                                      | hull’s plane (that is, it is neither |
|                                      | fully inside nor fully outside of    |
|                                      | the volume).**                       |
+--------------------------------------+--------------------------------------+

\

**Editing Support**

Computing the occlusion volume and detecting whether an object is
occluded is half of the work that needs to be done. Another task is
finding a way to edit occluders comfortably in an evolving 3D scene
during development. It may be done in several ways; I’ll discuss some of
them here.

Editing occlusion volumes in a modeling package.This is a convenient way
of starting with occluders quickly and testing functionality. You may
use 3DS Max, Maya, or whatever modeling program you prefer, to build an
occluder skeleton from vertices and faces and import that into your
engine.

Integrating an occluder editor into your game editor.This is a harder
way to do it, but it’s preferable over editing in a modeling package.
The geometry inside occluders may change, and occluders must match
geometry in order to be effective, so an “edit and see” approach is the
best bet here.

Because an occluder is simply a convex hull, once you’ve implemented and
tuned your convex hull code, you can call it with a set of points and
you’ve got it.

Figures 10 shows occlusion techniques in a real game project, including
numbers about rendered triangles. Note that the terrain is specially
modeled so that occlusion is efficient; it contains high hills that are
suitable for occluding objects behind them. But the areas of possibility
for occluder utilization are much wider: cities with plenty of
buildings, fences (solid, not transparent), and so on.

\

<div>

![](http://www.gamasutra.com/redesign/images/corner_top_left.gif)

</div>

\
 ![](http://www.gamasutra.com/features/20020717/fig_10.gif)

![](http://www.gamasutra.com/redesign/images/corner_top_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_right.gif)

![](http://www.gamasutra.com/redesign/images/corner_bottom_left.gif)

**Figure 1 The original in-game screenshot, the same screenshot in
wireframe mode, with 7,000 triangles rendered at 50fps, and with
cclusion is switched off. The number of rendered triangles rose to
17,300, the frame rate dropped to 20 frames per second.**

\

 

Finally, fine-tune editing support by visually displaying occluders in
edit mode while designing your missions or modi-fying the occluder’s
shape in the editor.

**Take It Outside**

This article provides some insight into rendering possibilities for
outdoor scenes, and shows some new directions for optimizations. The
model described here has worked — and continues to work — for games I
have been working on (used with other HSR techniques, such as sectors
and portals) and has undergone many changes to get to this point. As we
continue to improve our methods for rendering all kinds of environments
in games, soon there will be no boundaries as to what kinds of worlds we
can provide players.







