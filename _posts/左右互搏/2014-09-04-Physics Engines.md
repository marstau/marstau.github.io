---
layout: post
title: Physics Engines
category: 左右互搏
tags: Game　Engine
keywords: 
description: 
---

## [Havok ](http://www.havok.com)
* Collision Detection - including Continuous Physics™
* MOPP™ Technology - for compact representation of large collision meshes
* Dynamics and Constraint Solving
* Vehicle Dynamics
* Data Serialization and Art Tool Support
* Visual Debugger for in-game diagnostic feedback 

有不少游戏和软件都选择了他做物理引擎，比如HOLO3，失落星球，HL2， 细胞分裂，指环王Online ..etc现在Havok被Intel收购了，以后可能对Intel的CPU会有特别的优化。

## [AGEIA PhysX](http://www.ageia.com/)
* Massively Parallel Physics Architecture
* High-speed GDDR3 Memory Interface
* AGEIA Universal Continuous Collision Detection
* AGEIA Physical Smart Particle Technology
* AGEIA Complex Object Physics System
* AGEIA Scalable Terrain Fidelity
* AGEIA Dynamic Gaming Framework

因为特有的硬件卡(物理加速卡-PPU)支持，所以能处理大量的物理运算，其他几款暂时没得比。Unreal3，GameBryo，Reality Engine等多款商业引擎和游戏都使用了他。
## [Bullet](http://www.bulletphysics.com)
Open Source

* Multi Platform support
* Supports various shape types:
* Discrete Collision Detection for Rigid Body Simulation
* Single Queries:
* Sweep and Prune Broadphase
* Documentation and Support
* Auto generation of MSVC project files, comes with Jam build system 
* Bullet Collision Detection works with Bullet Dynamics, but there is also a sample integration with Open Dynamics Engine.
* Framework with 2 different Constraint Solvers
* Hinge, Point to Point Constraint, Twist Cone Constraint (ragdolls)
* Automatic de-activation (sleeping)
* Generic 6 Degree of Freedom Constraint , Motors, Limits
* LCP Warm starting of contact points
* Collada 1.4 Physics Import using FCollada and COLLADA-DOM
* Convex Decomposition Code

这款物理引擎的历史也比较久了，但似乎国内知道的ODE的人更多一些，这款物理引擎被Nvidia的开发人员所关注(Nvidia前些时候说过，要用GPU来实现物理加速，可能会最先在这款物理引擎上实现。)

## [ODE](http://www.ode.org/)
* Rigid bodies with arbitrary mass distribution.
* Joint types: ball-and-socket, hinge, slider (prismatic), hinge-2, fixed, angular motor, linear motor, universal.
* Collision primitives: sphere, box, cylinder, capsule, plane, ray, and triangular mesh, convex.
* Collision spaces: Quad tree, hash space, and simple.
* Simulation method: The equations of motion are derived from a Lagrange multiplier velocity based model due to Trinkle/Stewart and Anitescu/Potra.
* A first order integrator is being used. It's fast, but not accurate enough for quantitative engineering yet. Higher order integrators will come later.
* Choice of time stepping methods: either the standard \`\`big matrix'' method or the newer iterative QuickStep method can be used. 
* Contact and friction model: This is based on the Dantzig LCP solver described by Baraff, although ODE implements a faster approximation to the Coloumb friction model.
* Has a native C interface (even though ODE is mostly written in C++).
* Has a C++ interface built on top of the C one.
* Many unit tests, and more being written all the time.
* Platform specific optimizations.
## [TOKAMAK](http://www.tokamakphysics.com)
* Joints
* Friction
* Stacking
* Collision Detection
* Rigid Particle
* Breakage

这个物理引擎出现也比较早了，作者是日本人，其实日本的游戏也很发达的，能把技术共享出来，难得啊。（日文的技术网站还是很多的。）Tokamak是一个速度极快的物理引擎，基本上他只能被使用於Windows平台，但是速度上的优势让他佔有一席之地，当然这引擎也是免费提供的，Tokamak有被应用为Blitz3D的插件，所以您若是Blitz3D用户，可能见过其身影。

## [Newton](http://www.newtondynamics.com)
这款物理引擎名声可能不是很响，但是功能上绝对不差。比较出名的作品有：TV3D, Quest3D。这个物理引擎是跨Win32/Mac/Linux三个平台的，同时也有3DGameStudio插件，在速度和功能上很不错，你也可以找到大量范例，虽然没有开源，但广为使用，有兴趣的人，从这个开始是不错的选择，他也是OGRE游戏引擎的组件之一。(Tip:这款引擎支持Delphi;在后面这个非官方的Wiki上，有一套不错的教程: http://walaber.com/newtonwiki/index.php?title=MainPage )

## LiquidFun
谷歌发布的开源2D物理引擎

LiquidFun是一款执行受约束刚体模拟的物理引擎，它以Box2D为基础，并在其上添加了基于粒子的流体模拟。
## Reference
