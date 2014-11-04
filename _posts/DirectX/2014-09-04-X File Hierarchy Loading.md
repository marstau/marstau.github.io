---
layout: post
title: X File Hierarchy Loading
category: 游戏技术
tags: DirectX
keywords: 
description: 
---

Introduction to X file loading {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; BACKGROUND-COLOR: #b7b4df; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 16pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}
------------------------------

This page describes how you can load mesh data in the x file format
maintaining a mesh hierarchy. If you are not interested in keeping the
hierarchy you can simply use the<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXLoadMeshFromX</span><span
class="Apple-converted-space"> </span>set of functions that are
described in the<span class="Apple-converted-space"> </span>[X File
Simple](http://www.toymaker.info/Games/html/load_x_simply.html)<span
class="Apple-converted-space"> </span>notes. However if you wish to
implement animation or skinning you will need to read on. These notes
are meant to be read in conjunction with the demo application.

Note that if you do not wish to implement this code I have written a
small library to do it for you. See the<span
class="Apple-converted-space"> </span>[XAnimator
page](http://www.toymaker.info/Games/html/xanimator.html).

Demo Application (with source code) {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; BACKGROUND-COLOR: #b7b4df; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 16pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}
-----------------------------------

![](http://files.note.sdo.com/XbPJ4~k4Pdp2wE0WA006s5)<span
style="COLOR: #ff0000"></span>

<span style="COLOR: #ff0000">New: updated August 2010<span
class="Apple-converted-space"> </span></span>to include some fixes I
discovered while creating<span
class="Apple-converted-space"> </span>[XAnimator](http://www.toymaker.info/Games/html/xanimator.html).
These include the ability to handle multiple skinned mesh and some bug
fixes

Updated demo code download:<span
class="Apple-converted-space"> </span>[XFileAnimationCode.rar](http://www.toymaker.info/Games/XFileAnimationCode.rar)

The demo has the following features

-   

-   Loads x files and maintains their hierarchy (press L to load)

-   

-   Handles animation and allows merging between animations.

-   

-   Handles skinning with software rendering.

The bouncy skinned model was created using 3DS Max. The process of
creating it and exporting it as a DirectX x file is described in more
detail here:<span class="Apple-converted-space"> </span>[Art
Creation](http://www.toymaker.info/Games/html/load_x_hierarchy.html#Art).The
demo has a couple of limitations: it does not load<span
class="Apple-converted-space"> </span>[effect files<span
class="Apple-converted-space"> </span>](http://www.toymaker.info/Games/html/effects_files.html)that
are referenced in the x file and it does not do hardware skinning (it
uses software skinning).

### Contents {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 12pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}

-   

-   [Hierarchy
    Concept](http://www.toymaker.info/Games/html/load_x_hierarchy.html#HierarchyConcept)

-   

-   [Loading the x
    file](http://www.toymaker.info/Games/html/load_x_hierarchy.html#Loadxfile)

-   

-   [Rendering the
    hierarchy](http://www.toymaker.info/Games/html/load_x_hierarchy.html#Rendering)

-   

-   [Animation](http://www.toymaker.info/Games/html/load_x_hierarchy.html#Animation)

-   

-   [Skinning](http://www.toymaker.info/Games/html/load_x_hierarchy.html#Skinning)

-   

-   [Art
    Creation](http://www.toymaker.info/Games/html/load_x_hierarchy.html#Art)

-   

-   [Final
    Words](http://www.toymaker.info/Games/html/load_x_hierarchy.html#Final)

-   

-   [Further
    Reading](http://www.toymaker.info/Games/html/load_x_hierarchy.html#FutherRead)

Hierarchy Concept {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; BACKGROUND-COLOR: #b7b4df; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 16pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}
-----------------

<span style="TEXT-DECORATION: underline">In order to animate our 3D
models we need to maintain a model hierarchy</span>. The hierarchy
consists of frames containing matrix and mesh data for different parts
of the model (when skinning these frames are seperate from the mesh and
known as bones).

E.g. if we had a 3D model of the human body it might be divided into
head, body, arms and legs. The body might be the top frame with <span
style="TEXT-DECORATION: underline">each part in frames below defining
their own matrix and mesh data</span>. <span
style="TEXT-DECORATION: underline">The frame matrix provides the offset
position and orientation from the body matrix.</span>

  -----------------------------------------------------------------------------------
  ![skeleton](http://www.toymaker.info/Games/assets/images/skeleton.jpg "skeleton")
  -----------------------------------------------------------------------------------

 

Ignoring the legs and head the hierarchy for the above may look like
this:

  -------------------------------------------------------------------------------------------------------------
  ![skeleton hierarchy](http://www.toymaker.info/Games/assets/images/frameHeirarchy.jpg "skeleton hierarchy")
  -------------------------------------------------------------------------------------------------------------

\

When rendering we start from the top and recursively travel down through
the hierarchy.<span style="COLOR: #e53333"> Each frame has an associated
matrix, so you can see that by altering the rotation of the left arm
frame all the upper and lower arm are also rotated</span>. Note: <span
style="TEXT-DECORATION: underline">in <span
style="COLOR: #e53333">skinning **frames** are called <span
style="COLOR: #e53333">**bones** </span></span>and there tends to be
just one mesh controlled by these bones.</span>

<span style="COLOR: #e53333">When the model is positioned in the 3D
world the first frame (known as the **root**) is transformed to the
correct position. Each part of the model is positioned based on the
frame matrix translating and rotating it from the frame above.</span> By
maintaining this structure we can animate parts of the model simply by
altering one frame matrix. <span style="COLOR: #e53333">We could name
frames in our 3D package and then use the names in our code to find the
correct frames to animate</span>. Alternatively we can create animation
in our 3D package and load it into our game and use the<span
class="Apple-converted-space"> </span>[D3DX](http://www.toymaker.info/Games/html/load_x_hierarchy.html#)<span
class="Apple-converted-space"> </span>helper functions to animate it.
This process is described in LINK below.

Loading the X File {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; BACKGROUND-COLOR: #b7b4df; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 16pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}
------------------

The main method for loading animation data, skin info and hierarchy
is<span class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">**D3DXLoadMeshHierarchyFromX**</span>.

*Note*: there is another similar function called<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXLoadSkinMeshFromXof</span><span
class="Apple-converted-space"> </span>which loads from a<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ID3DXFileData</span><span
class="Apple-converted-space"> </span>object. We could load the x file
data into our own formats and bypass the Direct3D functionality using
this object and the<span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ID3DXFileEnumObject</span>.
This method is not covered by these notes but if you interested there is
an article on Gamedev about this (see<span
class="Apple-converted-space"> </span>[further
reading](http://www.toymaker.info/Games/html/load_x_hierarchy.html#FutherRead)).

### The D3DXLoadMeshHierarchyFromX function {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 12pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}

<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">HRESULT
D3DXLoadMeshHierarchyFromX(<span class="Apple-converted-space"> </span>\
    LPCTSTR Filename,<span class="Apple-converted-space"> </span>\
    DWORD MeshOptions,\
    LPDIRECT3DDEVICE9 pDevice,\
    LPD3DXALLOCATEHIERARCHY pAlloc,\
    LPD3DXLOADUSERDATA pUserDataLoader,\
    LPD3DXFRAME\* ppFrameHeirarchy,\
    LPD3DXANIMATIONCONTROLLER\* ppAnimController );</span>

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">Filename</span><span
    class="Apple-converted-space"> </span>- the file name of the .x file
    to be loaded

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">MeshOptions</span><span
    class="Apple-converted-space"> </span>- various options can be
    specified here defining creation.

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">pDevice</span><span
    class="Apple-converted-space"> </span>- a D3D<span
    class="Apple-converted-space"> </span>[<span
    style="COLOR: #990000">Device</span>](http://www.toymaker.info/Games/html/load_x_hierarchy.html#)<span
    class="Apple-converted-space"> </span>pointer.

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">pAlloc</span><span
    class="Apple-converted-space"> </span>- allows you to specify a
    class that will handle the allocation of memory for all the frames
    and mesh data. More on this below.

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">pUserDataLoader</span><span
    class="Apple-converted-space"> </span>- as mentioned previously the
    .x file format is highly flexible using a template system to define
    data chunks. If you add your own templates you can specify a class
    here that knows how to load your specific data. If you do not use
    this then you can ignore it and set it to 0.

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ppFrameHeirarchy</span><span
    class="Apple-converted-space"> </span>- once loading complete this
    points to the top of the loaded frame hierarchy.

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ppAnimController</span><span
    class="Apple-converted-space"> </span>- once loading complete this
    points to an animation controller containing animation data loaded
    from the x file (if it has any). The
    [animation](http://www.toymaker.info/Games/html/load_x_hierarchy.html#Animation)<span
    class="Apple-converted-space"> </span>section describes this.

<span style="TEXT-DECORATION: underline">Before calling this function we
need to create a</span><span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">**ID3DXAllocateHierarchy**</span><span
class="Apple-converted-space">** **</span><span
style="TEXT-DECORATION: underline">derived class to handle the creation
of memory for our frame and mesh data. </span>This is where a lot of our
work will take place.<span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ID3DXAllocateHierarchy</span><span
class="Apple-converted-space"> </span>is an interface class that defines
the functions we must implement. We must implement the following
functions:

1.  

2.  <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">CreateFrame</span><span
    class="Apple-converted-space"> </span>- requests allocation of a
    frame object

3.  

4.  <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">CreateMeshContainer</span><span
    class="Apple-converted-space"> </span>- requests allocation of a
    mesh container object

5.  

6.  <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">DestroyFrame</span><span
    class="Apple-converted-space"> </span>- deallocation of frame object

7.  

8.  <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">DestroyMeshContainer</span><span
    class="Apple-converted-space"> </span>- deallocation of mesh
    container object

<span style="COLOR: #e53333">These will be called during the internal
processing of the x file carried out by the</span><span
class="Apple-converted-space" style="COLOR: #e53333"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #e53333; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXLoadMeshHierarchyFromX</span><span
class="Apple-converted-space" style="COLOR: #e53333"> </span><span
style="COLOR: #e53333">function. </span>The header for our class will
look like this:

<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">class
CMeshHeirarchy : public ID3DXAllocateHierarchy\
{\
public:\
    // The format of these interfaces is defined by
D3DXLoadMeshHierarchyFromX\
\
    // callback to create a D3DXFRAME derived object and initialize it\
    STDMETHOD( CreateFrame )( THIS\_ LPCSTR Name,
LPD3DXFRAME \*ppNewFrame );\
\
    // callback to create a D3DXMESHCONTAINER derived object and
initialise it\
    STDMETHOD( CreateMeshContainer )( THIS\_ LPCSTR Name, CONST
D3DXMESHDATA \*pMeshData,  CONST D3DXMATERIAL \* pMaterials, CONST
D3DXEFFECTINSTANCE \* pEffectInstances, DWORD NumMaterials, CONST
DWORD \* pAdjacency, LPD3DXSKININFO pSkinInfo, LPD3DXMESHCONTAINER \*
ppNewMeshContainer );\
\
   // callback to release a D3DXFRAME derived object\
   STDMETHOD( DestroyFrame )( THIS\_ LPD3DXFRAME pFrameToFree );\
\
   // callback to release a D3DXMESHCONTAINER derived object\
   STDMETHOD( DestroyMeshContainer )( THIS\_ LPD3DXMESHCONTAINER
pMeshContainerToFree );\
};</span>

The implementation of each of these functions is described below and can
be seen, in full, in the sample code.

### CreateFrame {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 12pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}

This function is called during processing of the .x file by the<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXLoadMeshHierarchyFromX</span><span
class="Apple-converted-space"> </span>call when a new frame is
encountered. If you look back at the
[diagram](http://www.toymaker.info/Games/html/load_x_hierarchy.html)<span
class="Apple-converted-space"> </span>above you can see that<span
style="TEXT-DECORATION: underline"> <span style="COLOR: #e53333">a frame
contains either other frames (children or siblings,which is accessed by
pFrameFirstChild or pFrameSibling) and / or the mesh data itself(stored
in pMeshContainer). </span></span>By maintaining this hierarchy we can
carry out animation and other functions on our mesh data.

<span style="COLOR: #e53333">This function is called with a frame name
and requires us to create a frame in memory. </span><span
style="COLOR: #e53333">This memory is returned to the caller via
the</span><span class="Apple-converted-space"
style="COLOR: #e53333"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #e53333; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ppNewFrame</span><span
class="Apple-converted-space" style="COLOR: #e53333"> </span><span
style="COLOR: #e53333">parameter. </span>Therefore we will need to look
at this frame structure in more detail.

**The D3DXFRAME Structure**

This is a structure provided by Direct3D to hold information for a frame
in our hierarchy. It contains all the basic data required:

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">LPSTR
    Name</span><span class="Apple-converted-space"> </span>- the frame
    name

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXMATRIX
    TransformationMatrix</span><span
    class="Apple-converted-space"> </span>- a transformation matrix that
    should be applied to this and child frames

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">LPD3DXMESHCONTAINER
    pMeshContainer</span><span class="Apple-converted-space"> </span>-
    if this frame has mesh data this will point to a container of mesh
    data.

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXFRAME \*pFrameSibling</span><span
    class="Apple-converted-space"> </span>- if this frame has a sibling
    this points to it

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXFRAME \*pFrameFirstChild</span><span
    class="Apple-converted-space"> </span>- if this frame has a child
    this points to it

When we come to render our mesh hierarchy we will traverse the frame
tree applying each frame transformation matrix and rendering our mesh
data. We will combine transformation matrix as we go down the hierarchy.
This allows us to, for example, move the top part of the arm and have
the lower part and hand and fingers all transform accordingly. It is
useful therefore to also maintain a combined transformation matrix per
frame (updated during our FrameMove function). This information is not
held in the frame structure but we can extend the structure ourselves
and add this bit of data:

<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">struct
D3DXFRAME\_DERIVED: public D3DXFRAME\
{\
    D3DXMATRIXA16 exCombinedTransformationMatrix;\
};</span>

You could of course add more data if required for a particular purpose.

*Note*: Direct3D provides a number of functions for working with frame
hierarchies like<span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXFrameDestroy</span>,\
<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXFrameFind</span>,<span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXFrameCalculateBoundingSphere</span><span
class="Apple-converted-space"> </span>etc.

### CreateMeshContainer {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 12pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}

This function is called during processing of the x file by the<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXLoadMeshHierarchyFromX</span><span
class="Apple-converted-space"> </span>call when mesh data is
encountered. This function is called with a large number of parameters:

<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">HRESULT
CreateMeshContainer(\
    LPCSTR Name,\
    const D3DXMESHDATA \*pMeshData,\
    const D3DXMATERIAL \*pMaterials,\
    const D3DXEFFECTINSTANCE \*pEffectInstances,\
    DWORD NumMaterials,\
    const DWORD \*pAdjacency,\
    LPD3DXSKININFO pSkinInfo,\
    LPD3DXMESHCONTAINER \*ppNewMeshContainer);</span>

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">Name</span><span
    class="Apple-converted-space"> </span>- name of the mesh

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">pMeshData</span><span
    class="Apple-converted-space"> </span>-  pointer to a mesh data
    structure containing details on this mesh

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">pMaterials</span><span
    class="Apple-converted-space"> </span>- an array of material
    structures describing the materials used by this mesh

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">pEffectInstances</span><span
    class="Apple-converted-space"> </span>- array of effect instance
    structures used by this mesh

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">NumMaterials</span><span
    class="Apple-converted-space"> </span>- number of materials in the
    mesh

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">pAdjacency</span><span
    class="Apple-converted-space"> </span>- array of adjacency
    information for the mesh

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">pSkinInfo</span><span
    class="Apple-converted-space"> </span>- if the mesh uses skinning
    this points to an<span class="Apple-converted-space"> </span><span
    class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ID3DXSkinInfo</span><span
    class="Apple-converted-space"> </span>object containing skinning
    data

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ppNewMeshContainer</span><span
    class="Apple-converted-space"> </span>- once we have created a mesh
    container we return the pointer via this parameter

All but the last parameter are input data defining the mesh. <span
style="COLOR: #e53333">Our function needs to take this data and create
and return a new mesh container structure. </span>This is a Direct3D
provided structure and is described below:

**The D3DXMESHCONTAINER structure**

This is a structure provided by D3D to hold information about a mesh in
our hierarchy. The data is:

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">LPSTR
    Name</span><span class="Apple-converted-space"> </span>- the mesh
    name

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXMESHDATA
    MeshData</span><span class="Apple-converted-space"> </span>- a
    structure containing the mesh triangle data itself in one of the
    D3DX mesh interface objects (<span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ID3DXMesh</span>,<span
    class="Apple-converted-space"> </span><span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ID3DXPMesh</span><span
    class="Apple-converted-space"> </span>or<span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ID3DXPatchMesh</span>)

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">LPD3DXMATERIAL
    pMaterials</span><span class="Apple-converted-space"> </span>- array
    of mesh materials (we will not use this) \*

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">LPD3DXEFFECTINSTANCE
    pEffects</span><span class="Apple-converted-space"> </span>- array
    of effect instances

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">DWORD
    NumMaterials</span><span class="Apple-converted-space"> </span>-
    number of materials

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">DWORD \*pAdjacency</span><span
    class="Apple-converted-space"> </span>- adjacency information

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">LPD3DXSKININFO
    pSkinInfo</span><span class="Apple-converted-space"> </span>-
    skinning information

-   

-   <span class="Code"
    style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXMESHCONTAINER \*pNextMeshContainer</span><span
    class="Apple-converted-space"> </span>- pointer to a sibling mesh
    structure

It is our responsibility to allocate and fill out this structure. It is
not as complex as it may look at first as a lot of this information can
be directly copied from the data that is passed to us.<span
class="Apple-converted-space" style="COLOR: #e53333"> </span>*<span
style="COLOR: #e53333">Note:</span>*<span class="Apple-converted-space"
style="COLOR: #e53333"> </span><span style="COLOR: #e53333">we must make
a copy of this data i.e. we must leave the caller data alone.</span>

<span style="COLOR: #ee33ee">MyView:so ga, each bone node container
multiply meshes, which is stored in D3DXMESHCONTAINER(it is a container
of meshes.), and each frame has a sibiling or child.</span>

As with the<span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXFRAME</span><span
class="Apple-converted-space"> </span>structure we can add more
information to this structure based on our application needs. We will
normally load any textures specified for this mesh and so the addition
of a texture pointer is useful. Other information commonly added
includes skinning data. The structure used in the demo is shown below:

<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">struct
D3DXMESHCONTAINER\_EXTENDED: public D3DXMESHCONTAINER\
{\
    IDirect3DTexture9\*\*  exTextures;  // Array of texture
pointers <span class="Apple-converted-space"> </span>\
    D3DMATERIAL9\*   exMaterials;      // Array of materials\
\
    // Skinned mesh variables\
    ID3DXMesh\*     exSkinMesh;           // The skin mesh\
    D3DXMATRIX\*    exBoneOffsets;        // The bone matrix Offsets\
    D3DXMATRIX\*\*   exFrameCombinedMatrixPointer; // Array of frame
matrix\
};</span>

The base<span class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXMESHCONTAINER</span><span
class="Apple-converted-space"> </span>has a<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">pMaterials</span><span
class="Apple-converted-space"> </span>member which is a<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXMATERIAL</span><span
class="Apple-converted-space"> </span>structure that contains a texture
filename and material data. It is easier to ignore this and instead
store the data in arrays of created textures and materials in our
derived structure (<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">exTextures</span><span
class="Apple-converted-space"> </span>and<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">exMaterials</span>).

The final three variables are for skinning purposes only and are
described in the section on<span
class="Apple-converted-space"> </span>[skinning](http://www.toymaker.info/Games/html/load_x_hierarchy.html#Skinning)<span
class="Apple-converted-space"> </span>below.

### DestroyFrame and DestroyMeshContainer {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 12pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}

These functions should deallocate the memory we created in the above two
functions. They are invoked when we destroy the frame hierarchy. This is
achieved using the<span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXFrameDestroy</span><span
class="Apple-converted-space"> </span>function. Look at the demo code
for the implementation.

Rendering the Hierarchy {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; BACKGROUND-COLOR: #b7b4df; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 16pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}
-----------------------

After loading the x file we have our hierarchy loaded in as a tree of
frames and mesh data (like the<span
class="Apple-converted-space"> </span>[diagram](http://www.toymaker.info/Games/html/load_x_hierarchy.html)).
<span style="TEXT-DECORATION: underline">We hold a pointer to the top of
our frame hierarchy</span> (returned from<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXLoadMeshHierarchyFromX</span><span
class="Apple-converted-space"> </span>in the<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ppFrameHeirarchy</span><span
class="Apple-converted-space"> \
</span>pointer). In addition, <span
style="TEXT-DECORATION: underline">if our x file contained animation, we
have a pointer to an animation controller </span>(returned from<span
class="Apple-converted-space"> \
</span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXLoadMeshHierarchyFromX</span><span
class="Apple-converted-space"> </span>in the<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ppAnimController</span><span
class="Apple-converted-space"> </span>pointer).

I will look first at how we can render this hierarchy without animation
or skinning. I will talk about animation and skinning later.

### Rendering the Hierarchy {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 12pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}

To render the model with a hierarchy involves traversing the hierarchy
maintaining matrix and rendering mesh as we encounter them. At regular
intervals the demo calls<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">CXFileEntity::UpdateFrameMatrices</span><span
class="Apple-converted-space"> </span>in order to calculate the combined
matrix for each frame in the hierarchy. This could be done in the render
function itself but later on we will also want to handle animation so we
keep this separate.

The function<span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">Render</span><span
class="Apple-converted-space"> </span>simply calls<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">DrawFrame</span><span
class="Apple-converted-space"> </span>with the topmost frame in the
hierarchy.<span class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">DrawFrame</span><span
class="Apple-converted-space"> </span>renders any mesh that it owns via
a call to <span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">DrawMeshContainer</span>.
Then if the frame has any siblings it recursively calls<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">DrawFrame</span><span
class="Apple-converted-space"> </span>with them (these calls will only
return once that branch has been completed) and then any child frames.

Animation {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; BACKGROUND-COLOR: #b7b4df; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 16pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}
---------

As already mentioned if we have a model hierarchy we can carry out
animation simply by altering a frame matrix. E.g. if we alter a shoulder
matrix then the rest of the arm below will be transformed as well.

The provided x file<span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">bones\_all.x</span><span
class="Apple-converted-space"> </span>contains a number of animation
sets that is worth viewing while understanding these notes.

In Direct3D animation is held in animation sets maintained by an
animation controller object. This is passed initially to our application
in the <span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXLoadMeshHierarchyFromX</span><span
class="Apple-converted-space"> </span>function (<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">m\_animController</span>).
This controller wraps a lot of the functionality required to carry out
animation.

In<span class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">FrameMove</span><span
class="Apple-converted-space"> </span>we tell the animation controller
what time it is by calling<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">AdvanceTime</span>.
This allows the controller to determine the matrices for each frame in
our hierarchy at that particular time. The frame controller will alter
the frame matrices (the<span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">TransformationMatrix</span><span
class="Apple-converted-space"> </span>held in the frame structure) and
when we update our frame hierarchy matrices during<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">UpdateFrameMatrices</span><span
class="Apple-converted-space"> </span>we use this new matrix to create
our combined frame matrix. The controller object carries out
interpolation of matrix between key frames for us.

We can change which animation set is active by calling the frame
controller<span class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">**SetTrackAnimationSet**</span><span
class="Apple-converted-space">** **</span>with the new animation set.
First of all we have to retrieve this set via a call to<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">GetAnimationSet</span>.

<span style="TEXT-DECORATION: underline">Switching between animations
abruptly would look wrong. Imagine our skeleton went from running to
dying  - the arms and legs etc, would suddenly change position.
</span><span style="COLOR: #e53333">So Direct3D provides a way of
interpolating into the new animation smoothly.</span>

<span style="COLOR: #e53333">This is achieved via the use of tracks.
</span>Our current track is running the original animation so we use a
second track for our new animation. We slowly fade out the effect of the
first animation and fade in the second. We do this by inserting keys
into the track using the animation controller functions. We can turn
tracks on and off, change the track speed and change how much that track
effects the animation (via a weighting value).

This process can be seen in the demo code<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">SetAnimationSet</span><span
class="Apple-converted-space"> </span>function. The speed with which the
transition between animations occurs is held in a global constant
variable:<span class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">kMoveTransitionTime</span>.
To understand how this process works try changing this value. Setting it
to a higher value will slow down the transition and help you to see what
is happening.

*Note*: the provided file<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">bones\_all.x</span><span
class="Apple-converted-space"> </span>has a number of animation sets
that were added using the **<span style="COLOR: #e53333">Mesh View
</span>**tool from the SDK<span style="TEXT-DECORATION: underline">. If
you have a number of .x files produced from an art package with the same
model but different animations you can combine them into one using the
Mesh View tool or do it programmatically using the animation
controller</span><span class="Apple-converted-space"><span
style="TEXT-DECORATION: underline"> </span>\
</span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal"><span
style="TEXT-DECORATION: underline">RegisterAnimationSet
</span></span><span style="TEXT-DECORATION: underline">unction.</span>

Skinning {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; BACKGROUND-COLOR: #b7b4df; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 16pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}
--------

### Introduction to Skinning {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 12pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}

Skinning takes data in a mesh-skeleton hierarchy and applies geometry
blending to transform the mesh vertices. Skinning uses a set of
interconnected bones (frames) that form a hierarchy as shown<span
class="Apple-converted-space"> </span>[above](http://www.toymaker.info/Games/html/load_x_hierarchy.html#diagram).
When bones are moved or rotated the mesh surface moves or rotates
accordingly (like skin does). The mesh surface is simply described with
vertices forming triangles and so skinning works by altering the vertex
position dependant on the bones attached to it. If you run the demo and
turn on wireframe mode you can see how the vertex positions are altered.

If you think about the skin on your elbow it is affected both by the
movement of the lower arm and the movement of the upper arm. Hence the
position of the elbow vertices depends on two inputs (bones). The
transformation of the vertices is calculated by combining a matrix from
the upper arm with the one from the lower arm. How much each matrix
affects each vertex is controlled by a blending weight.

*Advanced*: the actual geometry blending operation applies each bones
matrix to the vertices to create a number of differently positioned
vertices and then interpolates between them based on the blending
weight.

### Skinned Mesh Matrices {style="LINE-HEIGHT: normal; WIDOWS: 2; TEXT-TRANSFORM: none; FONT-VARIANT: normal; FONT-STYLE: normal; TEXT-INDENT: 0px; FONT-FAMILY: 'Times New Roman', Times, serif; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: #000000; FONT-SIZE: 12pt; WORD-SPACING: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"}

The skeleton is a hierarchical set of bones. Each bone has a matrix
which translates and rotates that bone relative to its parent (this is
just the same process as the frame hierarchy discussed above but the
mesh is normally separate to the hierarchy). Since the matrix are
relative to the parent rather than the character itself we say they are
defined in **<span style="COLOR: #009900">bone space</span>**<span
style="COLOR: #009900">. </span>We want to place the bones relative to
the character itself so must convert these matrices into **<span
style="COLOR: #009900">character space(角色空间) </span>**by combining
them with their parent matrix.

We add a variable to our extended mesh container structure for <span
style="TEXT-DECORATION: underline">this combined matrix
</span>(called<span class="Apple-converted-space"><span
style="TEXT-DECORATION: underline">  </span></span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal"><span
style="TEXT-DECORATION: underline">exFrameCombinedMatrixPointer</span></span><span
style="TEXT-DECORATION: underline">- one entry per bone</span>).  Since
we already maintain a combined matrix for each frame in the hierarchy
(<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">exCombinedTransformationMatrix</span>)
we do not need to duplicate it therefore our <span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">exFrameCombinedMatrixPointer</span><span
class="Apple-converted-space"> </span>is an array of pointers to the
correct frames'<span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">exCombinedTransformationMatrix</span>.
Finding the correct frame is carried out during<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">SetupBoneMatrices</span><span
class="Apple-converted-space"> </span>using the Direct3D<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXFrameFind</span><span
class="Apple-converted-space"> </span>function.

<span style="TEXT-DECORATION: underline">Combined Bone Matrix = Local
Bone Matrix \* Parent Combined Bone Matrix.</span>

There is one further matrix required when doing skinning and that
is<span style="TEXT-DECORATION: underline"> a matrix to connect the
bones to the mesh</span>, this is known as <span
style="TEXT-DECORATION: underline">a bone offset matrix</span>. We add
this to our structure as<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">exBoneOffsets</span>.
These are assigned during the<span class="Apple-converted-space">\
</span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">CMeshHierarchy::CreateMeshContainer</span><span
class="Apple-converted-space"> </span>function - one per bone. This
allows us to create our final matrix:

**Final Bone Matrix = Bone Offset Matrix \* Combined Bone Matrix**

This final matrix transforms the mesh into bone space then applies the
bone matrix to the mesh. This is calculated during the frame move
function and fed into the <span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">UpdateSkinnedMesh</span><span
class="Apple-converted-space"> </span>function.

*Note*: <span style="TEXT-DECORATION: underline">the amount each vertex
is affected by the bones is determined by a weighting. </span>This is
contained in the <span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">ID3DXSKININFO
</span>object and is automatically calculated into the equation for us
by the function<span class="Apple-converted-space"> </span><span
class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">UpdateSkinnedMesh</span>.

To summarise this rather complicated process: we have a mesh that needs
to be altered based on a skeleton hierarchy of bones (frames). Each bone
is positioned and oriented to its parent via a local bone matrix. We
store a pointer to the correct frames combined matrix in our mesh
container structure (<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">exFrameCombinedMatrixPointer</span>).
In order to wrap the mesh skin around the bones we use a bone offset
matrix. By combining these two matrices we can create a final matrix
that can be fed into the Direct3D<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">UpdateSkinnedMesh</span><span
class="Apple-converted-space"> </span>function. This function will alter
the mesh vertices based on the matrix and a set of weights to carry out
the actual skinning.

**Skinning Mesh Rendering**

There are a number of methods of carrying out skinning with Direct3D.
The demo code uses software skinning but there are other methods that
use hardware acceleration for greater speed. The Skinned Mesh sample
that comes with the DirectX SDK describes three other methods: Fixed
Function Non Indexed Skinning, Fixed Function Indexed Skinning and
Shader Based Skinning.

The software skinning method used by the demo is carried out in<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">FrameMove</span>.
The process is:

<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">/\*
Create the bone matrices that transform each bone from bone space into
character space (via exFrameCombinedMatrixPointer) and also wraps the
mesh around the bones using the bone offsets in exBoneOffsetsArray \*/\
\
for (UINT i = 0; i \< Bones; ++i)\
  
D3DXMatrixMultiply(&m\_boneMatrices[i],&pMesh-\>exBoneOffsets[i],</span>

<span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">                    pMesh-\>exFrameCombinedMatrixPointer[i]);\
\
void \*srcPtr;\
pMesh-\>MeshData.pMesh-\>LockVertexBuffer(D3DLOCK\_READONLY,
(void\*\*)&srcPtr);\
\
void \*destPtr;\
pMesh-\>exSkinMesh-\>LockVertexBuffer(0, (void\*\*)&destPtr);\
\
// Update the skinned mesh<span class="Apple-converted-space"> </span>\
pMesh-\>pSkinInfo-\>UpdateSkinnedMesh(m\_boneMatrices, NULL, srcPtr,
destPtr);\
\
// Unlock the meshes vertex buffers\
pMesh-\>exSkinMesh-\>UnlockVertexBuffer();\
pMesh-\>MeshData.pMesh-\>UnlockVertexBuffer();</span>

We lock the vertex buffer of our original unaltered mesh for read. We
also lock the vertex buffer of the destination mesh vertices to write
into (this is why we stored a copy of the mesh in our<span
class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">D3DXMESHCONTAINER\_EXTENDED</span><span
class="Apple-converted-space"> </span>structure. It was copied
during<span class="Apple-converted-space"> </span><span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">SetupBoneMatrices</span>).
We then call the Direct3D <span class="Code"
style="FONT-FAMILY: Fixedsys, monospace; COLOR: #000066; FONT-SIZE: 12pt; FONT-WEIGHT: normal">UpdateSkinnedMesh</span><span
class="Apple-converted-space"> </span>function which takes the
transformation matrices and our locked vertex buffers and carries out
the skinning. It does this by combining the matrix and a set of bone
weights to alter the position of the original vertices and write them
into the output buffer.

Locking vertex buffers is to be avoided as much as possible if we want
our graphic card to work at maximum speed. A lock can cause a stall in
the graphics processing leading to slow down. To avoid this there are a
number of methods that use the hardware to carry out the skinning
itself. As previously mentioned these methods are beyond the scope of
these notes (for the time being - I may add notes on them later) and if
you are interested I suggest you look at the skinned mesh sample that
comes with the DirectX SDK.







