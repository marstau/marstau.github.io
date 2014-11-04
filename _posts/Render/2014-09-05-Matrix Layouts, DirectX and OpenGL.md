---
layout: post
title: Matrix Layouts, DirectX and OpenGL
category: 游戏技术
tags: Game　Engine
keywords: Matrix,Math
description: 
---
When reading about computer graphics, you invariably run into the mention of the Matrix datatype. Typically, this is a 4x4 matrix of floating-point values, used to perform affine transforms for graphics (scaling, rotation, translation, sometimes shearing).
However, there are at least two different conventions for how to apply matrices to the vectors (vertices and normals) that make up the building blocks of 3D graphics. A vertex is extended to a 4- vector by tacking on a "1" (this allows translation to work); a normal is extended to a 4-vector by tacking on a "0" (this means that only the non-translation part will apply). So far, so good. But is that 4-vector a row vector, or a column vector? (And it gets even better when the matrix is stored in memory).
Consider the two cases:

      m11 m12 m13 m14    x

      m21 m22 m23 m24    y

      m31 m32 m33 m34    z

      m41 m42 m43 m44    1
    
_Case 1: column vector on the right_



                  m11 m12 m13 m14

                  m21 m22 m23 m24
     x y z 1
                  m31 m32 m33 m34

                  m41 m42 m43 m44
    
_Case 2: row vector on the left_


In the first case, column vectors on the right, the translation of the operation lives in matrix elements m14, m24 and m34. However, in the second case, the translation lives in elements m41, m42 and m43. Thus, when you see a matrix written out, you have to take a while to consider in which orientation you're supposed to be reading it. Sadly, papers and documentation that writes about matrices seldom consider that there are these two conventions, and tend to just assume that you know which one you mean.
 
**Traditional mathematicians, and OpenGL, tends to prefer colum vectors. Meanwhile**, certain other legacies of computer graphics, as well as DirectX, tend to prefer row vectors, on the left. The confusion gets even more complete when you start talking about "pre-multiplying" and "post-multiplying" matrices. Pre-multiplying may mean multiplying it on the left (if you're the row vector type), or it may mean multiplying it on the right (if you're the OpenGL type) -- if by "pre" you mean that the pre-multiplied operation happens before the target matrix operation. If instead you mean, with pre-multplying, that the matrix you're pre-multiplying goes on the left, then it means that it happens afterward in the OpenGL notation, but it still means that it happens before in the DirectX notation.
Confused yet?
So, then we come to storing matrices in memory. Of course there's two ways to store matrices -- they could be stored in the order m11 m12 m13 m14 m21 ..., or they could be stored in the order m11 m21 m31 m41 m12 ... The first version is called "row major" because you can view it as storing one row at a time. The second version is called "column major" because you can view it as storing one column at a time.
So, if you're given a matrix as an array of floats in memory, or as a sequence of floats on a web page, you need to know both which vector convention is assumed for the matrix, AND the storage format used for the matrix. However, as luck would have it, an error in one, will cancel out an error in the other. A row-major matrix intended for row vectors will work, as-is in memory, just as well for a column vector if you just assume it's stored in column-major order.
And, guess what? OpenGL assumes colum major matrices; DirectX assumes row major matrices. This means that the translation, in a matrix seen as a float array, will always go in elements at index 12, 13 and 14 in a matrix in memory (where index is in the range 0..15), be it OpenGL or DirectX. These locations map to m41, m42 and m43 in the DirectX conventions, and to m14, m24, m34 in the OpenGL conventions. Whew! You may actually have something wrong in your code, but because you've mis-understood the convention, an additional interpretation error negates the first mistake, and it all works out.
##Left- and Right-handed matrices
There's this persistent rumor that there are "left-handed" and "right-handed" matrices. That's not true. In a left-handed coordinate system, a rotation of the X vector +90 degrees around Z axis projects to the Y vector. In a right-handed coordinate system, a rotation of the X vector +90 degrees around the Z axis projects to the Y vector. The math is the same; the matrix is the same. The only difference is the interpretation of the data once you get it out -- larger Z means closer to the viewer in a Y-up, X-right right-handed coordinate system, but further into the screen in a left-handed coordinate system. If your matrix attempts to some-how do something different for left- and right-handed uses, it will either end up rotating in the opposite direction of what you'd expect, or it will end up mirroring your entire geometry. If you have right-handed data, and want to display it in a left-handed coordinate system, that's what you want, but you should express that as an explicit mirror matrix that either negates one row (or column :-), or flips two rows (or columns) of the identity matrix.



