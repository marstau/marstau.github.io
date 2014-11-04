---
layout: post
title: Steering Behaviors For Autonomous Charac
category: 游戏技术
tags: DirectX
keywords: 
description: 
---

<div
style="widows:2;text-transform:none;text-indent:0px;font:medium Simsun;white-space:normal;orphans:2;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"
align="center">

**Steering Behaviors For Autonomous Characters<span
class="Apple-converted-space"> </span>**\
 background and update<span class="Apple-converted-space"> </span>\
 by<span class="Apple-converted-space"> </span>[Craig
Reynolds](http://www.red3d.com/cwr/)<span
class="Apple-converted-space"> </span>\
\
 ![path following diagram](http://www.red3d.com/cwr/steer/pathfoll.gif)

</div>

\

**Abstract:**<span class="Apple-converted-space"> </span>This paper
presents solutions for one requirement of autonomous characters in
animation and games: the ability to navigate around their world in a
life-like and improvisational manner. These "steering behaviors" are
largely independent of the particulars of the character's means of
locomotion. Combinations of steering behaviors can be used to achieve
higher level goals (For example: get from here to there while avoiding
obstacles, follow this corridor, join that group of characters...) This
paper divides motion behavior into three levels. It will focus on the
middle level of steering behaviors, briefly describe the lower level of
locomotion, and touch lightly on the higher level of goal setting and
strategy.

------------------------------------------------------------------------

\

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  \
   Online version of the<span class="Apple-converted-space"> </span>[GDC](http://www.gdconf.com/)<span class="Apple-converted-space"> </span>1999 paper:<span class="Apple-converted-space"> </span>\
   **[Steering Behaviors For Autonomous Characters](http://www.red3d.com/cwr/papers/1999/gdc99steer.html)<span class="Apple-converted-space"> </span>**\
  \
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span
style="widows:2;text-transform:none;background-color:#c0c0c0;text-indent:0px;display:inline !important;font:medium Simsun;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"> </span>

  ---- -------------------------------------------------------------------------------------------------------------- ---- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -----
       [![OpenSteer Logo](http://opensteer.sourceforge.net/images/beta_90a.gif)](http://opensteer.sourceforge.net/)        [OpenSteer](http://opensteer.sourceforge.net/)<span class="Apple-converted-space"> </span>is a open source C++ implementation of these steering behaviors, currently a prototype at version 0.7. It includes an application to demonstrate some of the basic ideas. You can also use it to develop and tune your own steering behaviors.      
  ---- -------------------------------------------------------------------------------------------------------------- ---- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -----

\

------------------------------------------------------------------------

> Java-based animated diagrams of steering behaviors described in this
> paper:
>
> -   Simple behaviors for individuals and pairs:
>     -   [*Seek*<span class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>*Flee*](http://www.red3d.com/cwr/steer/SeekFlee.html)
>     -   [*Pursue*<span class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>*Evade*](http://www.red3d.com/cwr/steer/PursueEvade.html)
>     -   [*Wander*](http://www.red3d.com/cwr/steer/Wander.html)
>     -   [*Arrival*](http://www.red3d.com/cwr/steer/Arrival.html)
>     -   [*Obstacle
>         Avoidance*](http://www.red3d.com/cwr/steer/Obstacle.html)
>     -   [*Containment*](http://www.red3d.com/cwr/steer/Containment.html)
>     -   [*Wall Following*](http://www.red3d.com/cwr/steer/Wall.html)
>     -   [*Path
>         Following*](http://www.red3d.com/cwr/steer/PathFollow.html)
>     -   [*Flow Field
>         Following*](http://www.red3d.com/cwr/steer/FlowFollow.html)
> -   Combined behaviors and groups:
>     -   [*Crowd Path
>         Following*](http://www.red3d.com/cwr/steer/CrowdPath.html)
>     -   [*Leader
>         Following*](http://www.red3d.com/cwr/steer/LeaderFollow.html)
>     -   [*Unaligned Collision
>         Avoidance*](http://www.red3d.com/cwr/steer/Unaligned.html)
>     -   [*Queuing*](http://www.red3d.com/cwr/steer/Doorway.html)<span
>         class="Apple-converted-space"> </span>(at a doorway)
>     -   [*Flocking*](http://www.red3d.com/cwr/boids/)<span
>         class="Apple-converted-space"> </span>(combining:<span
>         class="Apple-converted-space"> </span>*separation, alignment,
>         cohesion*)
>
> Note that I cannot distribute the source code for these applets.
> Source code is available for<span
> class="Apple-converted-space"> </span>[OpenSteer](http://opensteer.sourceforge.net/)<span
> class="Apple-converted-space"> </span>which is a similar
> implementation in C++.

------------------------------------------------------------------------

> **Related online resources by other authors**<span
> class="Apple-converted-space"> </span>(sorry, still not particularly
> well arranged):
>
> -   **General steering behavior and related resources:**
>     -   Applets for<span
>         class="Apple-converted-space"> </span>[Swarm](http://www.ozemail.com.au/~dcrombie/project/applet.html),<span
>         class="Apple-converted-space"> </span>[Forming
>         Lines](http://www.ozemail.com.au/~dcrombie/project/applet3.html),<span
>         class="Apple-converted-space"> </span>[Predator](http://www.ozemail.com.au/~dcrombie/project/games.html)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Tag](http://www.ozemail.com.au/~dcrombie/project/games2.html).
>         From<span class="Apple-converted-space"> </span>[The
>         Examination and Exploration of Algorithms and Complex
>         Behaviour to Realistically Control Multiple Mobile
>         Robots](http://www.ozemail.com.au/~dcrombie/project/)<span
>         class="Apple-converted-space"> </span>by<span
>         class="Apple-converted-space"> </span>[Duncan
>         Crombie](http://www.ozemail.com.au/~dcrombie/).
>     -   [Behavior Library for Autonomous Character
>         Locomotion](http://www.atomicmedia.com/autonomous/)<span
>         class="Apple-converted-space"> </span>(demo and code) by<span
>         class="Apple-converted-space"> </span>[Clint
>         Hannaford](http://www.atomicmedia.com/demo/)<span
>         class="Apple-converted-space"> </span>of<span
>         class="Apple-converted-space"> </span>[Atomic
>         Media](http://www.atomicmedia.com/)<span
>         class="Apple-converted-space"> </span>written in Lingo(?) for
>         MacroMedia's<span
>         class="Apple-converted-space"> </span>[Shockwave](http://www.macromedia.com/software/shockwaveplayer/)<span
>         class="Apple-converted-space"> </span>player.
>     -   [steeringbehaviors.de](http://www.steeringbehaviors.de/)<span
>         class="Apple-converted-space"> </span>is devoted to issues of
>         steering behaviors, by Christian Schnellhammer and<span
>         class="Apple-converted-space"> </span>[Thomas
>         Feilkas](http://home.t-online.de/home/TFeilkas/), includes
>         applets and source code with documentation. See also this<span
>         class="Apple-converted-space"> </span>[report](http://home.t-online.de/home/TFeilkas/steeringbehaviors.pdf)<span
>         class="Apple-converted-space"> </span>(in German).
> -   **Simulating Pedestrians and Traffic:**
>     -   Steering Autonomous Driving Agents Through Intersections in
>         Virtual Urban Environments<span
>         class="Apple-converted-space"> </span>[[PDF](http://www.cs.uiowa.edu/~howang/pubs/steeringOnIntersection.pdf)]<span
>         class="Apple-converted-space"> </span>(2004)<span
>         class="Apple-converted-space"> </span>[<span
>         class="author"><span class="author">Hongling
>         Wang</span></span>](http://www.cs.uiowa.edu/~howang/),<span
>         class="Apple-converted-space"> </span>[Joseph
>         Kearney](http://www.cs.uiowa.edu/~kearney/)<span
>         class="Apple-converted-space"> </span>[James
>         Cremer](http://www.cs.uiowa.edu/~cremer/), and<span
>         class="Apple-converted-space"> </span>[Peter
>         Willemsen](http://www.cs.utah.edu/~willemsn/)<span
>         class="Apple-converted-space"> </span>(to appear in
>         proceedings of  International Conference on Modeling,
>         Simulation and Visualization Methods, Las Vegas, Nevada, June
>         2004)<span class="Apple-converted-space"> </span><span
>         class="new"
>         style="color:red;font-size:smaller;font-weight:bold;">[new]</span>
>     -   [Intuitive Crowd Behaviour in Dense Urban Environments using
>         Local
>         Laws](http://csdl.computer.org/comp/proceedings/tpcg/2003/1942/00/19420122abs.htm)<span
>         class="Apple-converted-space"> </span>[[PDF](http://www.cs.ucl.ac.uk/research/vr/Projects/Create/publications/EGUK2003Final.pdf)]<span
>         class="Apple-converted-space"> </span>(2003)<span
>         class="Apple-converted-space"> </span>[Celine
>         Loscos](http://www.cs.ucl.ac.uk/people/C.Loscos.html), David
>         Marchal,<span class="Apple-converted-space"> </span>[Alexandre
>         Meyer](http://www-evasion.imag.fr/Membres/Alexandre.Meyer/)<span
>         class="Apple-converted-space"> </span><span class="new"
>         style="color:red;font-size:smaller;font-weight:bold;">[new]</span>
>     -   [AI Madness: Using AI to Bring Open-City Racing to
>         Life](http://www.gamasutra.com/features/20010124/adzima_01.htm)<span
>         class="Apple-converted-space"> </span>(2001) by Joe Adzima,
>         describes "urban AI" for pedestrians and vehicles in a virtual
>         cityscape. These techniques were used in the commercial
>         games<span class="Apple-converted-space"> </span>*Midtown
>         Madness 2<span class="Apple-converted-space"> </span>*and<span
>         class="Apple-converted-space"> </span>*Midnight Club.*
>     -   [Simulating the Collision Avoidance Behavior of
>         Pedestrians](http://www.logos.t.u-tokyo.ac.jp/~franck/research.html)<span
>         class="Apple-converted-space"> </span>(2000) by<span
>         class="Apple-converted-space"> </span>[Franck
>         Feurtey](http://www.logos.t.u-tokyo.ac.jp/~franck/), this
>         Master's thesis describes a spacetime ("(x, y, t) space")
>         approach to 2d unaligned collision avoidance while minimizing
>         detours and speed variation.
>     -   [Generation of Ambient Traffic for Real-time Driving
>         Simulation](http://citeseer.org/bonakdarian98generation.html)<span
>         class="Apple-converted-space"> </span>(1998) by<span
>         class="Apple-converted-space"> </span>[Esmail
>         Bonakdarian](http://www.cs.mercer.edu/bonak/),<span
>         class="Apple-converted-space"> </span>[James
>         Cremer](http://www.cs.uiowa.edu/~cremer/),<span
>         class="Apple-converted-space"> </span>[Joseph
>         Kearney](http://www.cs.uiowa.edu/~kearney/)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Pete
>         Willemsen](http://www.cs.utah.edu/~willemsn/)<span
>         class="Apple-converted-space"> </span>describes "bit players"
>         to provide background traffic for virtual driving simulations.
>     -   Discrete Force Model for Pedestrian Motion (including<span
>         class="Apple-converted-space"> </span>[Lane Formation in a
>         Street](http://rcswww.urz.tu-dresden.de/~helbing/Pedestrians/Corridor.html),<span
>         class="Apple-converted-space"> </span>[Oscillation at a
>         Bottleneck](http://rcswww.urz.tu-dresden.de/~helbing/Pedestrians/Door.html)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Interactions at a
>         Crossing](http://rcswww.urz.tu-dresden.de/~helbing/Pedestrians/Crossing.html)),
>         Java applets by<span
>         class="Apple-converted-space"> </span>[Kai
>         Bolay](http://bolay.de/kai/english/)<span
>         class="Apple-converted-space"> </span>based on the work
>         of<span class="Apple-converted-space"> </span>[Dirk
>         Helbing](http://www.helbing.org/). See also these related
>         applets simulating:<span
>         class="Apple-converted-space"> </span>[multi-lane
>         traffic](http://rcswww.urz.tu-dresden.de/~helbing/RoadApplet/)and<span
>         class="Apple-converted-space"> </span>[single-lane
>         traffic](http://vwisb7.vkw.tu-dresden.de/~treiber/MicroApplet/index.html).
>     -   Cellular Automata Simulation of Pedestrians by<span
>         class="Apple-converted-space"> </span>[Victor
>         Blue](http://www.ulster.net/~vjblue/)<span
>         class="Apple-converted-space"> </span>including<span
>         class="Apple-converted-space"> </span>[Unidirectional and
>         Bi-directional Pedestrian
>         Flows](http://www.ulster.net/~vjblue/p2dir.html)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Cross-directional and
>         4-directional Pedestrian
>         Flows](http://www.ulster.net/~vjblue/p4dir.html).
> -   **Simulating emergency evacuation of human crowds:**
>     -   [Simulating Dynamical Features of Escape
>         Panic](http://angel.elte.hu/~panic/)<span
>         class="Apple-converted-space"> </span>(2000) by<span
>         class="Apple-converted-space"> </span>[Dirk
>         Helbing](http://www.helbing.org/),<span
>         class="Apple-converted-space"> </span>[Illes J.
>         Farkas](http://angel.elte.hu/~fij), and<span
>         class="Apple-converted-space"> </span>[Tamas
>         Vicsek](http://angel.elte.hu/~vicsek): an individual-based
>         model of panic evacuations of human crowds from rooms and
>         corridors.
>     -   Simulations of emergency evacuations at<span
>         class="Apple-converted-space"> </span>[Fire Safety Engineering
>         Group](http://fseg.gre.ac.uk/)<span
>         class="Apple-converted-space"> </span>at the University of
>         Greenwich.
>     -   [Crowd Dynamics Ltd.](http://www.crowddynamics.com/)<span
>         class="Apple-converted-space"> </span>G. Keith Still's
>         consulting company uses simulations of crowds to help plan
>         safe public spaces.
> -   **Learning and evolving steering controllers**
>     -   [Learning to Race: Experiments with a Simulated Race
>         Car](http://citeseer.org/pyeatt98learning.html)<span
>         class="Apple-converted-space"> </span>(1998) by<span
>         class="Apple-converted-space"> </span>[Larry D.
>         Pyeatt](http://www.cs.ttu.edu/~pyeatt/)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Adele E.
>         Howe](http://www.cs.colostate.edu/~howe/)<span
>         class="Apple-converted-space"> </span>uses reinforcement
>         learning to discover a reactive control system for a virtual
>         race car using the<span
>         class="Apple-converted-space"> </span>[Robot Automobile Racing
>         Simulator](http://rars.sourceforge.net/)<span
>         class="Apple-converted-space"> </span>(RARS). In addition to
>         driving around the track the controller also deals with
>         passing other cars and avoiding obstacles.
>     -   [Co-evolution of Pursuit and Evasion II: Simulation Methods
>         and Results](http://citeseer.org/cliff95coevolution.html)<span
>         class="Apple-converted-space"> </span>(1996) by<span
>         class="Apple-converted-space"> </span>[Dave
>         Cliff](http://www.ai.mit.edu/people/davec/davec.html)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Geoffrey F.
>         Miller](http://www.unm.edu/~psych/faculty/gmiller.html)
>     -   [Competition, Coevolution and the Game of
>         Tag](http://www.red3d.com/cwr/papers/1994/alife4.html), (1994)
>         by<span class="Apple-converted-space"> </span>[Craig
>         Reynolds](http://www.red3d.com/cwr/)<span
>         class="Apple-converted-space"> </span>[[CiteSeer](http://citeseer.ist.psu.edu/reynolds94competition.html)].
>     -   [Evolution of Corridor Following Behavior in a Noisy
>         World](http://www.red3d.com/cwr/papers/1994/sab94.html)<span
>         class="Apple-converted-space"> </span>(1994) by<span
>         class="Apple-converted-space"> </span>[Craig
>         Reynolds](http://www.red3d.com/cwr/)<span
>         class="Apple-converted-space"> </span>[[CiteSeer](http://citeseer.org/reynolds94evolution.html)].
>     -   [Co-Evolution of Pursuit and Evasion I: Biological and
>         Game-Theoretic
>         Foundations](http://cogslib.cogs.susx.ac.uk/csr_abs.php?csrp311)<span
>         class="Apple-converted-space"> </span>(1994) by<span
>         class="Apple-converted-space"> </span>[Geoffrey F.
>         Miller](http://www.unm.edu/~psych/faculty/gmiller.html)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Dave
>         Cliff](http://www.ai.mit.edu/people/davec/davec.html).\
> -   **Steering and path planning for games**
>     -   [Near Optimal Hierarchical
>         Path-Finding](http://www.jogd.com/Vol1issue1.html#Anchor-ABSTRACT-28253)<span
>         class="Apple-converted-space"> </span>(2004)<span
>         class="Apple-converted-space"> </span>[Adi
>         Botea](http://www.cs.ualberta.ca/~adib/),<span
>         class="Apple-converted-space"> </span>[Martin
>         Müller](http://www.cs.ualberta.ca/~mmueller/),<span
>         class="Apple-converted-space"> </span>[Jonathan
>         Schaeffer](http://www.cs.ualberta.ca/~jonathan/)<span
>         class="Apple-converted-space"> </span><span class="new"
>         style="color:red;font-size:smaller;font-weight:bold;">[new]</span>[](http://www.jogd.com/Vol1issue1.html#Anchor-ABSTRACT-28253)
>     -   [Efficient Navigation Mesh
>         Implementation](http://www.jogd.com/Vol1issue1.html#Anchor-ABSTRACT-30946)<span
>         class="Apple-converted-space"> </span>(2004) John C.
>         O’Neill<span class="Apple-converted-space"> </span><span
>         class="new"
>         style="color:red;font-size:smaller;font-weight:bold;">[new]</span>
>     -   [Ribbon Networks for Modeling Navigable Paths of Autonomous
>         Agents in Virtual Urban
>         Environments](http://csdl.computer.org/comp/proceedings/vr/2003/1882/00/18820079abs.htm)<span
>         class="Apple-converted-space"> </span>[[PDF](http://www.cs.utah.edu/~willemsn/pubs/vr2003_willemsen.pdf)]<span
>         class="Apple-converted-space"> </span>(2003)<span
>         class="Apple-converted-space"> </span>[Peter
>         Willemsen](http://www.cs.utah.edu/~willemsn/),<span
>         class="Apple-converted-space"> </span>[Joseph K.
>         Kearney](http://www.cs.uiowa.edu/~kearney/)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[<span
>         class="author"><span class="author">Hongling
>         Wang</span></span>](http://www.cs.uiowa.edu/~howang/)<span
>         class="Apple-converted-space"> </span><span class="new"
>         style="color:red;font-size:smaller;font-weight:bold;">[new]</span>
>     -   [Toward More Realistic
>         Pathfinding](http://www.gamasutra.com/features/20010314/pinter_pfv.htm)<span
>         class="Apple-converted-space"> </span>(2001) by Marco Pinter
>         describes extending A\* search on grid-based maps to enforce
>         constraints on turning radii.
>     -   [AI Madness: Using AI to Bring Open-City Racing to
>         Life](http://www.gamasutra.com/features/20010124/adzima_01.htm)<span
>         class="Apple-converted-space"> </span>(2001) by Joe Adzima,
>         describes "urban AI" for pedestrians and vehicles in a virtual
>         cityscape. These techniques were used in the commercial
>         games<span class="Apple-converted-space"> </span>*Midtown
>         Madness 2<span class="Apple-converted-space"> </span>*and<span
>         class="Apple-converted-space"> </span>*Midnight Club.*
>     -   [Formation-Based Pathfinding With Real-World
>         Vehicles](http://citeseer.org/vanverth00formationbased.html)<span
>         class="Apple-converted-space"> </span>(2000) by<span
>         class="Apple-converted-space"> </span>[Jim Van
>         Verth,](http://www.redstorm.com/corporate/bios/bio_vanverth.php)<span
>         class="Apple-converted-space"> </span>[Victor
>         Brueggemann](http://www.redstorm.com/games/force21/china/logs/engineering/brueggemann.html),
>         Jon Owen and Peter McMurry.  Extends steering behaviors to
>         include multi-vehicle formations and explores more specific
>         vehicle locomotion models.
>     -   [Coordinated Unit
>         Movement](http://www.gamasutra.com/features/19990122/movement_01.htm)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Implementing
>         Coordinated
>         Movement](http://www.gamasutra.com/features/19990129/implementing_01.htm)<span
>         class="Apple-converted-space"> </span>(1999) by<span
>         class="Apple-converted-space"> </span>[Dave C.
>         Pottinger](http://www.ensemblestudios.com/ourteam/pottinger.shtml)<span
>         class="Apple-converted-space"> </span>describes combining
>         strategic<span class="Apple-converted-space"> </span>*path
>         planning*with<span class="Apple-converted-space"> </span>*path
>         execution*<span class="Apple-converted-space"> </span>(similar
>         to steering behaviors) for single characters and groups.<span
>         class="Apple-converted-space"> </span>Site requires free
>         registration.
>     -   [Motion Planning Using Potential
>         Fields](http://www.gamedev.net/reference/articles/article1125.asp)<span
>         class="Apple-converted-space"> </span>(2000) by<span
>         class="Apple-converted-space"> </span>[Stefan
>         Baert](http://www.softline.be/StrategicAlliance/)<span
>         class="Apple-converted-space"> </span>starts from the
>         assumption that all<span
>         class="Apple-converted-space"> </span>*units*<span
>         class="Apple-converted-space"> </span>(game characters) are
>         the same size and move on a discrete grid, it discusses using
>         potential fields to address several issues in navigation,
>         while avoiding some of the typical shortcomings of potential
>         field techniques.
> -   **Models for the<span
>     class="Apple-converted-space"> </span>*locomotion<span
>     class="Apple-converted-space"> </span>*level of an autonomous
>     vehicle:**
>     -   [The Physics of Racing](http://www.miata.net/sport/Physics/)
>     -   [Car Physics for
>         Games](http://home.planet.nl/~monstrous/tutcar.html)
>     -   [Automobile Ride, Handling, and Suspension
>         Design...](http://www.rqriley.com/suspensn.html)
>     -   [Robot Automobile Racing
>         Simulator](http://rars.sourceforge.net/)<span
>         class="Apple-converted-space"> </span>(RARS)
> -   <span style="font-weight:bold;">Other topics:</span>
>     -   [Pursuit-evasion
>         games](http://satirist.org/learn-game/systems/pursue.html)<span
>         class="Apple-converted-space"> </span>from<span
>         class="Apple-converted-space"> </span>[Machine Learning in
>         Games](http://satirist.org/learn-game/)<span
>         class="Apple-converted-space"> </span>by<span
>         class="Apple-converted-space"> </span>[Jay
>         Scott](http://satirist.org/)
>     -   [Navigational
>         overview](http://www.red3d.com/breese/navigation.html)<span
>         class="Apple-converted-space"> </span>by Bjørn Reese
>     -   [Hunter-Prey](http://intell-lab.engi.cf.ac.uk/jan/hunter.htm),<span
>         class="Apple-converted-space"> </span>[Foraging](http://intell-lab.engi.cf.ac.uk/jan/foraging.htm)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Flocking](http://intell-lab.engi.cf.ac.uk/jan/flock.htm)<span
>         class="Apple-converted-space"> </span>strategies implemented
>         in the<span
>         class="Apple-converted-space"> </span>[VehicleGuide
>         2.0](http://intell-lab.engi.cf.ac.uk/jan/Vehicle.htm)<span
>         class="Apple-converted-space"> </span>system by<span
>         class="Apple-converted-space"> </span>[Jan
>         Beutler](http://intell-lab.engi.cf.ac.uk/jan/)
>     -   [Sensor Based Motion
>         Planning](http://robby.caltech.edu/~jwb/sensor.html)<span
>         class="Apple-converted-space"> </span>at the<span
>         class="Apple-converted-space"> </span>[Caltech Robotics
>         Group](http://robby.caltech.edu/)
>     -   [Robotic Experiments in Cricket
>         Phonotaxis](http://www.daimi.au.dk/~hhl/cricket.html)<span
>         class="Apple-converted-space"> </span>by<span
>         class="Apple-converted-space"> </span>[Henrik Hautop
>         Lund](http://www.daimi.au.dk/~hhl/index.html),<span
>         class="Apple-converted-space"> </span>[John
>         Hallam](http://www.dai.ed.ac.uk/daidb/staff/John_Hallam.html)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Barbara
>         Webb](http://www.psychology.nottingham.ac.uk/staff/Barbara.Webb/)
>     -   [Peter
>         Stone](http://www.cs.cmu.edu/~pstone/pstone-home-no-frames.html)'s
>         page on<span
>         class="Apple-converted-space"> </span>[RoboSoccer](http://www.cs.cmu.edu/~pstone/robosoccer.html)<span
>         class="Apple-converted-space"> </span>and his<span
>         class="Apple-converted-space"> </span>[papers](http://www.cs.cmu.edu/~pstone/pstone-papers.html).
>     -   [Procedural
>         Animation](http://www.accad.ohio-state.edu/~mlewis/VRML/Class/w8.html)<span
>         class="Apple-converted-space"> </span>controllers in the
>         materials for<span
>         class="Apple-converted-space"> </span>[Matthew
>         Lewis](http://www.accad.ohio-state.edu/~mlewis/)' VRML
>         course:<span class="Apple-converted-space"> </span>[Building
>         3D Virtual
>         Environments](http://www.accad.ohio-state.edu/~mlewis/VRML/Class/syl.html)
>     -   [Dynamically Simulated Characters in Virtual
>         Environments](http://www.cs.virginia.edu/~dbrogan/Research/VE/)<span
>         class="Apple-converted-space"> </span>(1997, 1998) by<span
>         class="Apple-converted-space"> </span>[Jessica K.
>         Hodgins](http://www-2.cs.cmu.edu/~jkh/),<span
>         class="Apple-converted-space"> </span>[David
>         Brogan](http://www.cs.virginia.edu/~dbrogan/)<span
>         class="Apple-converted-space"> </span>and<span
>         class="Apple-converted-space"> </span>[Ronald
>         Metoyer](http://www.cc.gatech.edu/grads/m/Ronald.Metoyer/).
>         Describes autonomous steering behaviors for robot "sheep" and
>         bicycle racers. The sheep are being herded into a pen by a
>         human user playing the part of a Border Collie. The cyclists
>         ride on the same VR race track as a human participant
>         providing both teammates and opponents. The full<span
>         class="Apple-converted-space"> </span>[CG&A
>         paper](http://www.cs.virginia.edu/~dbrogan/Papers/CGandA-ve.pdf)<span
>         class="Apple-converted-space"> </span>[PDF 0.4MB] is available
>         online.
>
> Sometimes I hear from people who want to use steering behaviors in
> their work but never studied the (relatively simple) math and physics
> concepts on which they are based. As starting points, here are some
> introductory tutorials that might be useful:
>
> -   [Vectors - Motion and Forces in Two
>     Dimensions](http://www.physicsclassroom.com/Class/vectors/vectoc.html)<span
>     class="Apple-converted-space"> </span>(from<span
>     class="Apple-converted-space"> </span>[The Physics
>     Classroom](http://www.physicsclassroom.com/))
> -   Interactive<span
>     class="Apple-converted-space"> </span>[vector](http://mathforum.org/~klotz/Vectors/index.html)<span
>     class="Apple-converted-space"> </span>tutorial<span
>     class="Apple-converted-space"> </span>(from<span
>     class="Apple-converted-space"> </span>[Math
>     Forum](http://mathforum.org/))
> -   [On-Line Geometric Modeling
>     Notes](http://graphics.cs.ucdavis.edu/CAGDNotes/CAGD-Notes.html)<span
>     class="Apple-converted-space"> </span>(from<span
>     class="Apple-converted-space"> </span>[UC Davis Visualization and
>     Graphics Research Group](http://graphics.cs.ucdavis.edu/))
> -   [Vectors in a Plane](http://www.ping.be/math/vectors.htm)<span
>     class="Apple-converted-space"> </span>and<span
>     class="Apple-converted-space"> </span>[Real Vector
>     Spaces](http://www.ping.be/math/vect.htm)<span
>     class="Apple-converted-space"> </span>(from<span
>     class="Apple-converted-space"> </span>[MATH-abundance](http://www.ping.be/math/))
> -   xxx<span class="Apple-converted-space"> </span><span class="new"
>     style="color:red;font-size:smaller;font-weight:bold;">[new]</span>

------------------------------------------------------------------------

\
\
 <span
style="widows:2;text-transform:none;background-color:#c0c0c0;text-indent:0px;display:inline !important;font:medium Simsun;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">Send
comments to<span class="Apple-converted-space"> </span></span>[Craig
Reynolds](http://www.red3d.com/cwr/)<span
style="widows:2;text-transform:none;background-color:#c0c0c0;text-indent:0px;display:inline !important;font:medium Simsun;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;"><span
class="Apple-converted-space"> </span>\<</span><cwr@red3d.com><span
style="widows:2;text-transform:none;background-color:#c0c0c0;text-indent:0px;display:inline !important;font:medium Simsun;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">\><span
class="Apple-converted-space"> </span></span>\
 <span
style="widows:2;text-transform:none;background-color:#c0c0c0;text-indent:0px;display:inline !important;font:medium Simsun;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">visitors
since September 5, 1997<span
class="Apple-converted-space"> </span></span>\
 <span
style="widows:2;text-transform:none;background-color:#c0c0c0;text-indent:0px;display:inline !important;font:medium Simsun;white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">Last
update: June 6, 2004</span>







